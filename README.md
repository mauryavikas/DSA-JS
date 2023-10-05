# String Manupulation  
1. How do you reverse a given string in place?
    ```
    function reverseString(str){
        return str.split(" ").reverse().join(" "); 
    }
    console.log(reverseString(" hello im vikas maurya"));
    //o/p-> maurya vikas im hello
    ```
1. How do you print duplicate characters from a string?
1. How do you find duplicate characters in a given string?
1. How to remove the duplicate character from String?
1. How to find the maximum occurring character in given String?
1. How do you count the occurrence of a given character in a string?

    ```
    function DuplicateChar(str){
        let charArray= new Array(26).fill(0);
        // convert string to character array 
        let stringChar= str.toLowerCase().replaceAll(" ","").split("");
        stringChar.forEach((element,index) => {
            let charIndex= (element.charCodeAt()-"a".charCodeAt());
            charArray[charIndex]++;
        });

        charArray.forEach((element,index)=>{
            if(element>0){
                let charIndex= "a".charCodeAt()+index
                console.log(`char: ${String.fromCharCode(charIndex)} repeted ${element} times`)
            }
        });
    }
    DuplicateChar("hello i am vikas from karnataka.");
    // O/P->
    // char: a repeted 6 times
    // char: e repeted 1 times
    // char: f repeted 1 times
    // char: h repeted 1 times
    // char: i repeted 2 times
    // char: k repeted 3 times
    // char: l repeted 2 times
    // char: m repeted 2 times
    // char: n repeted 1 times
    // char: o repeted 2 times
    // char: r repeted 2 times
    // char: s repeted 1 times
    // char: t repeted 1 times
    // char: v repeted 1 times
    ```
1. How do you print the first non-repeated character from a string?


1. How do you check if two strings are anagrams of each other?
    ```
        // m1 : sort and compare nlogN , spaceO(1)
        function anagrams(str1, str2) {
            let charStr1 = str1.split("");
            let charStr2 = str2.split("");
            if (charStr1.length != charStr2.length) {
                return false;
            }
            charStr1.sort();
            charStr2.sort();

            for (let i = 0; i < charStr1.length; i++) {
                if (charStr1[i] != charStr2[i]) {
                    return false;
                }
            }
            return true;
        }
        console.log(anagrams("%h%", "%h%")) // o/p-> true 

        // m2 count and compare , t:O(n) S:O(n)
        function anagrams(str1, str2) {
            let NO_OF_CHARS = 256;
            let count1 = new Array(NO_OF_CHARS).fill(0);
            let count2 = new Array(NO_OF_CHARS).fill(0);
            let charStr1 = str1.split("");
            let charStr2 = str2.split("");
            if (charStr1.length != charStr2.length) {
                return false;
            }
            for (i = 0; i < str1.length; i++) {
                count1[str1[i].charCodeAt(0)]++;
                count2[str1[i].charCodeAt(0)]++;
            }

            for (let i = 0; i < charStr1.length; i++) {
                if (count1[i] != count2[i]) {
                    return false;
                }
            }
            return true;
        }
        console.log(anagrams("%h%", "%h%")) // o/p-> true
    ```
1. How can a given string be reversed using recursion?
    ```
        function reverse(strArr,index){
        if(index==strArr.length) return "";
        return reverse(strArr,index+1) +" "+strArr[index];
    }

    function StringReverse(str){
        let StrArr=str.split(" ");
        return reverse(StrArr,0);
    }


    console.log(StringReverse("hello vikas how are you doing"));
    ```


1. capitalize first world in the give string
    ```
    function capitalFirstWord(str){
    let strArr=str.split(" ");
    strArr.forEach((element, index)=>{
    strArr[index]=element.charAt(0).toUpperCase()+element.substring(1)
    });
    return strArr.join(" ");
    }

    console.log(capitalFirstWord("hello vikas how are you doing"));
    ```

1. How do you check if a string contains only digits?
    ```
    function isDigits(str){
    let strArr= str.replaceAll(" ","").split("");
    return strArr.every((ch)=>{
        const d = ch.charCodeAt();
        if(d<45 || d>57){
            return false;
        }
        return true;
    })
    }

    console.log(isDigits("vikas")) // false
    console.log(isDigits("9632.2 234567")) // true
    ```
    or use regular expression 

1. How do you count a number of vowels and consonants in a given string?
    ```
    function vowelsAndConsonants(str){
        const result ={ vowels:0, consonant:0};
        const vowels=['a','e','i','o','u'];

        for(let ch of str){
            if(vowels.includes(ch.toLowerCase())){
                result.vowels++;
            }else{
                result.consonant++;
            }
        }

        return result;
    }

    console.log(vowelsAndConsonants("hi my name is vikas")); //{ vowels: 6, consonant: 13 }
    ```
1. How do you reverse words in a given sentence without using any library method?
1. How can a given word be reversed using recursion?
    ```
    function reverseWord(word){
    if(word.length==0){
        return "";
    }
    return reverseWord(word.substring(1))+word.charAt(0);
    }

    console.log(reverseWord("vikas")); //o/p=>sakiv
    ```
1. How do you check if two strings are a rotation of each other?
    ```
        function isRotational(s1,s2){
        if(s1.length!=s2.length) return false ;
        const temp=s1+s1;
        return temp.includes(s2)
    }
    console.log(isRotational("HELLO","LOHEL"))// true
    console.log(isRotational("HELLO","LOEHL"))// false
    ```
1. How do you check if a given string is a palindrome?
    ```
    function isPalindrome(s1,s2){
    if(s1.length!=s2.length)return false;
    return s1.split("").reverse().join("")==s2;
    }
    console.log(isPalindrome("vikas","askiv"));// false
    console.log(isPalindrome("vikas","sakiv"));// true
    ```
1. How do you find all the permutations of a string?
    ```
        function swap(str,i,j){
            let charArr=str.split("");
            let temp=charArr[i];
            charArr[i]=charArr[j];
            charArr[j]=temp;
            return charArr.join("");
        }

        function permutation(str,k,l){
        if(k==l){
            console.log(str);
            return;
        }

        for(let j=k; j<l;j++){
            str=swap(str,k,j);
            permutation(str,k+1,l)
            // backtracking
            str=swap(str,k,j);
        }

        }

        permutation("abc",0,3);
    ```
1. How do you find the length of the longest substring without repeating characters?
1. Given string str, How do you find the longest palindromic substring in str?
1. How to convert a byte array to String?
    ```
    const decoder = new TextDecoder('UTF-8');

    const toString = (bytes) => {
        const array = new Uint8Array(bytes);
        return decoder.decode(array);
    };

    // Usage example:
    const bytes = [83, 111, 109, 101, 32, 116, 101, 120, 116, 32, 104, 101, 114, 101, 46, 46, 46];
    const string = toString(bytes);

    console.log(string);//Some text here...
    ```
1. How do you remove a given character from String?
    ```
    let str=" hello vikas how you doing"
    str=str.replaceAll("o","");
    console.log(str);// hell vikas hw yu ding
    ```
1. Given an array of strings, find the most frequent word in a given array, I mean, the string that appears the most in the array. In the case of a tie, ​the string that is the smallest (lexicographically) ​is printed.