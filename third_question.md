# 将所有数字用字符替换

给你一个下标从 0 开始的字符串 s ，它的**偶数**下标处为小写英文字母，**奇数**下标处为数字。

定义一个函数`shift(c, x)`，其中`c`是一个字符且`x`是一个数字，函数返回字母表中`c`后面第`x`个字符。

-比方说`shift('a', 5) = 'f'`和`shift('x', 0) = 'x'`。
对于每个**奇数**下标`i`，你需要将数字`s[i]`用`shift(s[i-1], s[i])`替换。

请你替换所有数字以后，将字符串`s`返回。题目**保证**`shift(s[i-1], s[i])`不会超过`'z'`。

## 示例 1：

>### 输入：
>s = "a1c1e1"
>### 输出：
>"abcdef"
>### 解释：
>- s[1] -> shift('a',1) = 'b'
>- s[3] -> shift('b',1) = 'd'
>- s[5] -> shift('c',1) = 'f'

## 示例 2：

>### 输入：
>s = "a1b2c3d4e"
>### 输出：
>"abbdcfdhe"
>### 解释：
>- s[1] -> shift('a',1) = 'b'
>- s[3] -> shift('b',2) = 'd'
>- s[5] -> shift('c',3) = 'f'
>- s[7] -> shift('d',4) = 'h'

## 代码:

1.

    public class Solution {
        public string ReplaceDigits(string s) {
            string str="";
            for(int i=0;i<s.Length;i++){   
                if(i%2==0){
                    str+=s[i];
                }
                else{
                    str+=shift(s[i-1], s[i]-'0');
                }                 
            }
            return str;
        }

        public char shift(char c, int x){
            return (char)(c+x);
        }
    }

2.

    public class Solution {
        public string ReplaceDigits(string s) {
            StringBuilder str=new StringBuilder();
            for(int i=0;i<s.Length;i++){   
                if(i%2==0){
                    str.Append(s[i]);
                }
                else{
                    str.Append(shift(s[i-1], s[i]-'0'));
                }                 
            }
            return str.ToString();
        }

        public char shift(char c, int x){
            return (char)(c+x);
        }
    }

3.

    public class Solution {
        public string ReplaceDigits(string s) {
            char[] arr = s.ToCharArray();
            int length = arr.Length;
            for (int i = 1; i < length; i += 2) {
                arr[i] = (char) (arr[i - 1] + (arr[i] - '0'));
            }
            return new string(arr);
        }
    }
