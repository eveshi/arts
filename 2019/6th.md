2019 week5 
### Algorithm
这周的题目：20. Valid Parentheses [ https://leetcode.com/problems/valid-parentheses/ ]
我的解法：
```
var isValid = function(s) {
    if(!s) return true;
    if(s.length%2 !== 0) return false;
    let newS = "";
    let i = 0;
    let flag = true;
    while(i<s.length){
        if(s[i] === "(" || s[i]==="{" || s[i]==="["){
            newS = newS += s[i];
        }else{
        if(s[i]===")"){
            if(newS.slice(-1) !== "("){
                flag = false;
                break;
            }
        }
        if(s[i]==="}"){
            if(newS.slice(-1) !== "{"){
                flag = false;
                break;
            }
        }
        if(s[i]==="]"){
            if(newS.slice(-1) !== "["){
                flag = false;
                break;
            }
        }
        newS = newS.slice(0,-1);
        }
        i++;
    }
    if(newS){
        flag = false
    }
    return flag;
};
```
我的主要问题：
1. 很冗长，而且容易写错
2. 对str的一些用法不熟练，比如slice其实很好用
别人的解法：
```
var isValid = function(s) {
    s = s.split('');
    let key = {
        '(' : ')',
        '{' : '}',
        '[' : ']'
    }
    let open = [];
    let close = '';
    for(var i = 0; i < s.length; i++){
        if(key.hasOwnProperty(s[i])){
            open.push(s[i]);
        } else {
            if(open.length === 0){
            return false;
            }
            if(key[open.pop()] !== s[i]){
                return false;
            }
        }
    }
    if(open.length > 0){
            return false;
    }
    return true;
};
```
反思：
1. 通过object的key和value的pair让我不用手动去比较，没那么重复

### Review
这周看的[ https://medium.com/commencis/what-is-service-worker-4f8dc478f0b9 ]。是讲service worker的原理。其实这么看起来service worker更像是一个在浏览器工作的管理员，它可能会参与一些cache的管理，push notification。在没有网络连接的时候帮你储存信息，到连接恢复就发出去。但它不参与任何前端显示的内容，和DOM没有任何关系。

### Tip
这周研究了一下html5广告的制作，实际上用google web designer是超级方便的，就像制作flash动画一样，几乎都不用使用编程的相关知识。不过在event里面，进行event自定义的时候，可以用基本的js来规定更多有趣的event。

### Share
今天想要分享的是背单词的内容。我现在开始一种新的额背单词的方法，就是不去记忆单词本身的意义，而是把单词放到句子中来背句子。因为我自己是一个很难记东西的人，那么有了一个背诵的场景，似乎让我记忆更深刻了，而且一个句子里面可能有好几个不懂得单词和句型用法，就等于一起学习了。当然这也不适用于需要短期记忆大量单词的人，比较适合像我这样慢慢背，一天背几个的人。


