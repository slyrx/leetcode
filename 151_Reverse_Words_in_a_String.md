## 题意
对字符串数组中的单词进行逆序，而不要对单词内部进行逆序

## 输入
字符串数组

## 输出
字符串数组

## 答案代码
```
    def reverseWords(self, s):
        """
        :type s: str
        :rtype: str
        """
        
        result = s.strip().split(" ")
        result = result[::-1]
        
        r_s = []
        for i in result:
            if i != "":
                r_s.append(i.strip())
            
        return (" ").join(r_s)
```
