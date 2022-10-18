# Longest-Common-Substring

In this problem we are supposed to find out the longest common substring. One of the easiest approach is to generate substrings from  first, store them into a hashmap, next generate the substrings from second and check for the key in hashmap. Not sure about the time complexity but it would definitlely be more than n^2 since while comparing two keys it takes n. So for a rough idea it would be O(n^3).

To reduce the time comeplxity we will use a dynamic programming approach, we will generate all the prefixes of first and second string and store it into separate tables. After that we will find the max suffix length by comparing all the prefixes from table1 with all the prefixes from table2.
Sharing the code approach.

`````cpp
class Solution{
    int longestCommonSubstr(String s1, String s2, int n, int m){
        // code here
       int[][] dp = new int[n][m];
       int max =0;
       for(int i=0;i<n;i++){
           for(int j=0;j<m;j++){
               int val =0;
               if(i!=0&&j!=0){
                   if(s1.charAt(i)==s2.charAt(j))
                   dp[i][j]=1+dp[i-1][j-1];
               }
               else{
                   if(s1.charAt(i)==s2.charAt(j)){
                       dp[i][j]=1;
                   }
               }
               if(max<dp[i][j])
                max=dp[i][j];
           }
       }
       return max;
    }
    
}

`````

Time complexlity : O(n^2)

Space Complexity : O(n^2)
