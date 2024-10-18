---
---
P A Y P A L I S H I R I N G
0 1 2 1 0 1 2 1 0 1 2 1 0 1
0 1 2 3 4 5 6 7 8 9 101112
(i%(numRow\*2-2) > (numRow-1)
```
public static String convert(String s, int numRows){
        String[] res = new String[numRows];
        String ans = "";
        if(numRows == 1){
            return s;
        }
        if(s.length() < numRows){
            return s;
        }
        for(int i = 0; i<s.length(); i++){
            if(i%(2*numRows-2) > (numRows-1)){
                res[numRows-1-((i%(2*numRows-2))-(numRows-1))] += s.charAt(i);
            } else{
                if(res[i%(2*numRows-2)] == null){
                    res[i%(2*numRows-2)] = String.valueOf(s.charAt(i));
                } else{
                    res[i%(2*numRows-2)] += s.charAt(i);
                }
            }
        }
        for(int i = 0; i< numRows; i++){
            ans += res[i];
        }
        return ans;
    }
```
