# Number to Word

- [About](#about)
- [Code](#code)


## About
Number to Word is simple logic code to get a word of number sequence


## Code

These are the main functions that retrive the word

```javascript
function Once(num) {
    let single = ["", "One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine"];
    return single[num];
}
```
```javascript
function Tence(num) {
    let TeenNums = ["Ten", "Eleven", "Twelve", "Thirteen", "Fourteen", "Fifteen", "Sixteen", "Seventeen", "Eighteen", "Nineteen"];
    let Bignums = ["Twenty", "Thirty", "Forty", "Fifty", "Sixty", "Seventy", "Eighty", "Ninty"];

    if (num < 20) {
        return TeenNums[parseInt(num - 10)];
    }
    else {
        return num % 10 == 0 ? Bignums[parseInt(num / 10 - 2)] : Bignums[parseInt(num / 10 - 2)] + "-" + Once(parseInt(num % 10));
    }
}
```

```javascript
function Hundreds(num) {
    let ans = Once(parseInt(num / 100)) + " Hundred";
    if (num % 100 == 0) {
        return ans;
    }
    return ans + "en " + numberToWord(String(parseInt(num % 100)));
}
```
```javascript
function numberToWord(num) {

    switch (num.length) {

        case 1: return Once(parseInt(num));
        case 2: return Tence(parseInt(num));
        case 3: return Hundreds(parseInt(num));

        case 4: return Thousands(parseInt(num));
        case 5: return Thousands(parseInt(num));

        case 6: return Lakhs(parseInt(num));
        case 7: return Lakhs(parseInt(num));

        case 8: return Crores(parseInt(num));
        case 9: return Crores(parseInt(num));

        default: return HundredCrores(num);
    }

}
```
You can increase these functions functions as your Requirement
```javascript

function Thousands(num) {

    return numberToWord(String(parseInt(num / 1000))) + " Thousand " + numberToWord(String(parseInt(num % 1000)));
}
function Lakhs(num) {

    return numberToWord(String(parseInt(num / 100000))) + " Lakh " + numberToWord(String(parseInt(num % 100000)));
}
function Crores(num) {
    return numberToWord(String(parseInt(num / 10000000))) + " Crore " + numberToWord(String(parseInt(num % 10000000)));
}
function HundredCrores(num) {
    return numberToWord(String(parseInt(num / 10000000))) + " Crore " + numberToWord(String(parseInt(num % 10000000)));
}

```

