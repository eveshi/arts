## 2019 week1
### Algorithm
这周的题目：3. Longest Substring Without Repeating Characters
[https://leetcode.com/problems/longest-substring-without-repeating-characters/]

我的解法：
`var lengthOfLongestSubstring = function(s) {
    let length = 0
    const sLength = s.length
    let i = 0
    let longest = 0
    let strArray = []
    for(;i<s.length; i++){
        let flag = true
        let x=0
        let repeat = -1
        let comtemporaryArray = []
        for(;x<strArray.length;x++){
            if(strArray[x] == s[i]){
                flag = false
                repeat = x
            }
        }
        if(repeat == -1){
            length = length + 1
        }
        if(repeat > -1){
            for(let r = repeat+1;r<strArray.length; r++){
                comtemporaryArray.push(strArray[r])
            }
            strArray = [...comtemporaryArray]
            length = length - repeat
        }
        strArray.push(s[i])
        if(longest<length){
            longest = length
        }
    }
    return longest;
};
`
我遇到的问题：1. 我的算法复杂度是n方，所以是很慢的。2. 想法是把新的string记下来，然后等于是数新string的长度，但是好像很容易算错，因为数字太多，来来去去就晕了，所以试了很多遍。
别人的解法：
`
// 1
public class Solution {
    public int lengthOfLongestSubstring(String s) {
        int n = s.length();
        Set<Character> set = new HashSet<>();
        int ans = 0, i = 0, j = 0;
        while (i < n && j < n) {
            // try to extend the range [i, j]
            if (!set.contains(s.charAt(j))){
                set.add(s.charAt(j++));
                ans = Math.max(ans, j - i);
            }
            else {
                set.remove(s.charAt(i++));
            }
        }
        return ans;
    }
}

// 2
   public int lengthOfLongestSubstring(String s) {
        if (s.length()==0) return 0;
        HashMap<Character, Integer> map = new HashMap<Character, Integer>();
        int max=0;
        for (int i=0, j=0; i<s.length(); ++i){
            if (map.containsKey(s.charAt(i))){
                j = Math.max(j,map.get(s.charAt(i))+1);
            }
            map.put(s.charAt(i),i);
            max = Math.max(max,i-j+1);
        }
        return max;
    }
`
思考：这个是之前了解过的hashset，可以大大节省查找时间，而且可以直接用contain的函数来查找，而不是我用for来一个个比对
我优化后的解法：
`
var lengthOfLongestSubstring = function(s) {
    if(s.length == 0) return 0;
    let left_i = 0
    let right_i = 1
    let newStr = {[s[0]]:0}
    let length = 1
    for(;right_i<s.length;right_i++){
        if(newStr.hasOwnProperty(s[right_i])){
            const idx = newStr[s[right_i]]
            left_i = Math.max(left_i, idx+1) 
            // some kind of not understand
        }
        newStr[s[right_i]]=right_i
        length = Math.max(length, right_i-left_i+1)
    }
    return length
};
`
再反思：还应该注意的就是特殊情况，诸如输入长度为0。以及结果是否加1，因为长度要包含头尾，如果是相减，那么就一定要加一才会是总长度。

### Review
英文技术文章看了《浏览器的原理》[https://www.html5rocks.com/en/tutorials/internals/howbrowserswork/#Introduction]
对于一个前端工程师来说，浏览器是我们最常接触的开发工具了，但是我之前也是盲目使用，没有好好去思考背后的原理。比如为什么各个浏览器之间的代码不一定适配，我们写css要带的webkit到底是什么东西起什么作用。这篇文章很好的解答了我的疑惑。特别是关于dom节点和virtual dom节点的问题。之前写react，并没有搞清楚virtual到底可以怎么virtual。

### Tip
这周的tip其实是看极客时间的专栏《代码精进之路》学到的。因为编程完全自学，所以经常会有一些请教这个请教那个得出的野方法。关于条件运算符就是一例。因为有一次我朋友建议我使用条件运算符，我就在此后能用条件运算符的地方，都用运算符，觉得看起来简洁好看。但是实际上，很多时候条件运算符的道理绕来绕去，反而是把人绕晕了。我自己之前也出了很多因为看错条件引发的bug。所以，有的时候看起来简洁不代表真的简洁，我在以后的使用中也要多思考符号是否适合，而不是无脑使用。

### Share
这周想分享的是自学编程遇到一个瓶颈的问题。因为自学没有体系，东一下西一下，好像要写给什么是没有障碍可以写出来了，但是并没有真正的学会。我最近重新开始看webpack的官方文档，然后觉得对于自学的人来说，其实针对自己目前在学习的框架也好、语言也好，对着官方文档一句一句看懂，遇到所有不懂的都去查，可能是一个真正学会的好方法。
