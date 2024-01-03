# String-to-Integer-atoi-

class Solution:
    def myAtoi(self, s):
        INT_MIN, INT_MAX = -2**31, 2**31 - 1
        i, n = 0, len(s)     
        while i < n and s[i] == ' ':
            i += 1
        sign = 1
        if i < n and (s[i] == '+' or s[i] == '-'):
            sign = -1 if s[i] == '-' else 1
            i += 1     
        result = 0
        while i < n and s[i].isdigit():
            digit = int(s[i])
           
            if result > (INT_MAX - digit) // 10:
                return INT_MAX if sign == 1 else INT_MIN
            result = result * 10 + digit
            i += 1       
        result *= sign      
        return max(min(result, INT_MAX), INT_MIN)
sol = Solution()
s1 = "42"
print(sol.myAtoi(s1))  # Output: 42
s2 = "   -42"
print(sol.myAtoi(s2))  # Output: -42
s3 = "4193 with words"
print(sol.myAtoi(s3))  # Output: 4193
