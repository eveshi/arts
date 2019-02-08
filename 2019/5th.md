2019 week5 
### Algorithm
这周的题目：14. Longest Common Prefix [ https://leetcode.com/problems/longest-common-prefix/ ]
我的解法：
```
var longestCommonPrefix = function(strs) {
    let pre = '';
    let i = 0;
    if(!strs[0]){
        return '';
    }
    while(i<strs[0].length){
        const word = strs[0];
        let flag = true;
        for(let m = 1; m < strs.length; m++){
            if(!strs[m][i]){
                flag = false
            }
            if(strs[m][i] !== word[i]){
                flag = false
            }
        }
        if(flag === false){
            break;
        }
        pre = pre + word[i];
        i += 1;
    }
    return pre;
};
```
我的主要问题：
1. 复杂度n方，循环两次
别人的解法：
```
var longestCommonPrefix = function(strs) {
    if(!strs || !strs.length) return '';
    
    var minLen = Math.min(...strs.map(function(str) {
        return str.length;
    }));
    
    var prefix = strs.find(function(str) {
        return str.length === minLen;
    });
    
    for(var str of strs) {
        while(str.indexOf(prefix) !== 0) prefix = prefix.substring(0, minLen--);
    }
    
    return prefix;
};
```
反思：
1. 用了substring这个函数，不用像我循环取值。
2. 用indexof来search string。但是要搞清楚indexof的原理。
3. 理解math。min和find的用法。

### Review
这周看的[ https://blog.codinghorror.com/protecting-your-cookies-httponly/ ]。是讲httponly是干什么的。其实httponly就是说，本来我们的cookie是可以很容易被xxs等攻击，然后通过browser拿到的，就是document。cookie就可以拿到，但是采用httponly之后，就只有server才可以拿到这个信息。

### Tip
不是在react里面用cookie就要用react-cookie这个库，要看你的cookie是全局使用还是仅限于component。如果全局使用，则应该选择universal-cookie。

### Share
关于cs进修选校。其实看来看去，当然还是美国的学历最受认可最好，但是如果又要考虑移民，可能什么加拿大之类的又会更有优势。所以事实上，很多事情还是鱼和熊掌不能兼得。职业发展比较好的地方，竞争激烈，难以申请也难以留下来。安逸的地方，好申请的地方也必然会科技发展滞后一些。我还没想清楚要怎么样选择。感觉不选竞争激烈的地方拼一下会后悔吧。

