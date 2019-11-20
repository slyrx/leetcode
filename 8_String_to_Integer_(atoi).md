## 答案代码
```

   def myAtoi(self, str):
        """
        :type str: str
        :rtype: int
        """
        #case: discard many whitespace;
        #      plus or minus sign
        #      can follow additional chr after int number
        #      empty and only whitespace not convert
        
        
        t_s = str.strip()
        if t_s == "":
            return 0
        
        t_s = t_s.split(" ")
        
        num_list = ""
        sign = 1
        if t_s[0][:2] == "+-" or t_s[0][:2] == "-+" or t_s[0][:2] == "++" or t_s[0][:2] == "--":
            return 0
        
        for i in t_s[0]:
            if i in "+-" and num_list == "":
                if i == "-":
                    sign = -1
                if i == "+":
                    sign = 1
            elif i >= 'a' and i <= 'z':
                if num_list:
                    break
                else:
                    return 0
            elif i >= '0' and i <= '9':
                num_list += i
            else:
                break
        
        if num_list:
            number = int(num_list) * sign
        else:
            return 0
        
        if number > (2**31 -1):
            number = 2**31 - 1;
        elif number < (-2**31):
            number = -2**31
            
        return number
                
```
