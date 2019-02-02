2019 week4
### Algorithm
这周的题目：13. Roman to Integer [ https://leetcode.com/problems/roman-to-integer/ ]
我的解法：
```
var romanToInt = function(s) {
    const chart = {
        "I": 1,
        "V": 5,
        "IV": 4,
        "X": 10,
        "IX": 9,
        "L": 50,
        "XL": 40,
        "C": 100,
        "XC": 90,
        "D": 500,
        "CD": 400,
        "M": 1000,
        "CM": 900
    }
    let num = 0;
    for(let i=0; i < s.length; i++){
        const dbs = s[i]+s[i+1]
        if(i===s.length - 1){
            num = num + chart[s[i]];
        }else if(chart[dbs]){
            num = num + chart[dbs]
            i = i + 1
            continue;
        }else{
            num = num + chart[s[i]]  
        }
    }
    return num;
};
```
我的主要问题：
1. 用了直接把特殊符号拿出来的办法，而实际上这让array要多进行一次内容提取，会拖慢速度
别人的解法：
```
var romanToInt = function(s) {
    
    s = s.split("");
    
    let integerValue = 0;
    let orderMax = 1;
    
    
    for (var i = s.length-1 ; i >=0; i--) {
        let romanLetter = s[i];
        
        orderValue = ordering[romanLetter]
        value =  key[romanLetter]
        
        if(orderValue >= orderMax){
            orderMax = orderValue;
            
        } else{
            value = value * (-1)
        }
        integerValue += value
    }
    return integerValue;
};



let key = {
    'I':1,
    'V':5,
    'X':10,
    'L':50,
    'C':100,
    'D':500,
    'M':1000
}
```
反思：
每次只提取一位。倒着来计算，这样就通过比大小的方式就可以计算了。

### Review
這週看的這篇[ https://www.rdegges.com/2018/please-stop-using-local-storage/ ]。在过去使用用户登录的时候，我都是照着别人的教程依葫芦画瓢存localstorage。localstorage也固然有容量大等优点。但是要深入理解用户登录的情况。为了保障用户安全，显然我们是不希望用户可以用不同浏览器登录时都可以保持登录状态，或者可以通过其他网站在localstorage拿到信息的。所以，在安全性来讲，可以在cookie设置httpOnly，以阻止client side拿到信息还是相对安全很多的。

### Tip
当我们在登陆的时候，所应该使用的是get或者query这样的请求吗？其实仔细思考这个过程，我们在比对参数之后，实际上要为用户create一个新的token返回，而不是单纯的给出一个已有数据供查阅。所以我们可以用的请求是post或者mutation才更为恰当。

### Share
在说自己弄懂某个语言之前，最好真的把document里面的所有案例看一遍，没懂的地方弄懂，不然真的没资格说这句话。就像我之前以为自己已经搞懂了graphql，真的写的时候才发现是一团糟，所有的细节都模棱两可。
