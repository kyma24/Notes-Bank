-   AcWing #16: replacing spaces (Python)
    
    Takes in an input that has less than 1000 characters.
    
    Replaces all spaces with "%20" and outputs.
    
    ```python
    class Solution(object):
        def replaceSpaces(self, s):
            """
            :type s: str
            :rtype: str
            """
            s2 = "";
            
            for i in range (0, len(s)):
                
                if (s[i]) == " ":
                    s2 += "%20"
                else:
                    s2 += s[i]
                
            return s2
    ```