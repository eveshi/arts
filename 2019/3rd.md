2019 week3
### Algorithm
这周的题目：9. Palindrome Number [ https://leetcode.com/problems/reverse-integer/ ]
我的解法：
```
var isPalindrome = function(x) {
    if(x<0) return false;
    if(x<10) return true;
    let xCopy = x;
    let m = 0;
    while(xCopy > 0){
        m = xCopy%10 + m*10;
        xCopy = parseInt(xCopy/10)
    }
    if(x === m) return true;
    return false;
};
```
我的主要问题：
1. 还是不记得reverse只有array可以用。
2. 老把let写成const，还是不熟悉。

### Review
這週看的這篇[ https://blog.sessionstack.com/how-does-javascript-actually-work-part-1-b0bacc073cf ]，主要是js的一些基本原理，包括memory allocate，call stack的原理。我的收穫主要是關於stack的負載的問題，理解了報錯maximum call stack size exceeded是什麼意思。 

### Tip
普通的function的this是指向自己，但是arrow function的this是指向更上一層的。這也是為什麼我之前寫react的一些函數的時候，用this都發現沒用，因為我都是用的箭頭函數。

### Share
還是接著說上兩週說的關於知識架構的問題。就像大家所流傳的小黃鴨debug法一樣，要整理清晰出一個好的架構可能最好的就是要想給一個完全不懂的人要怎麼樣去上課是比較好的。於是我構想了一下，如果我要做一門課程的話，我第一節課應該是會簡單介紹html、css、js可以讓一個網頁跑起來的原理。（說著有點想真的做一門課出來。）
