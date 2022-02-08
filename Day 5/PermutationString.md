Given two strings s1 and s2, return true if s2 contains a permutation of s1, or false otherwise.

In other words, return true if one of s1's permutations is the substring of s2.

Example 1:

    Input: s1 = "ab", s2 = "eidbaooo"
    Output: true
    Explanation: s2 contains one permutation of s1 ("ba").
Example 2:

    Input: s1 = "ab", s2 = "eidboaoo"
    Output: false
Constraints:

    1 <= s1.length, s2.length <= 104
    s1 and s2 consist of lowercase English letters.

Solution:

    class Solution {
    public boolean checkInclusion(String s1, String s2) {
    
            HashMap<Character, Integer> map1 = new HashMap<Charcter, Integer>();
            HashMap<Character, Integer> map2 = new HashMap<Charcter, Integer>();
            int start=0;
            
            
            for(int i=0;i<s1.length();i++){
                map1.put(s1.charAt(i), map1.getOrDefault(s1.charAt(i), 0)+1);
            }
            
            int i=0;
            int j=0;
            
            while(i<s2.length()){
                if(map1.containsKey(s2.charAt(i))){
                    map2.put(s2.charAt(i), map2.getOrDefault(s2.charAt(i), 0)+1);
                    j=i;
                }
                i++;
            }
            
        }
    }