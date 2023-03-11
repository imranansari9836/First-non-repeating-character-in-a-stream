# First-non-repeating-character-in-a-stream
Input: A = "aabc"
Output: "a#bb"
Explanation: For every character first non
repeating character is as follow-
"a" - first non-repeating character is 'a'
"aa" - no non-repeating character so '#'
"aab" - first non-repeating character is 'b'
"aabc" - first non-repeating character is 'b'



class Solution
{
    public String FirstNonRepeating(String A)
    {
        int[] freq = new int[26];
        Queue<Character> q = new LinkedList<>();
        StringBuilder sb = new StringBuilder();
        for(int i=0; i<A.length(); i++) {
            char ch = A.charAt(i);
            q.add(ch);
            freq[ch-'a']++;
            while(!q.isEmpty() && freq[q.peek()-'a']>1) {
                q.remove();
            }
            if(q.isEmpty())
                sb.append("#");
            else
                sb.append(q.peek());
        }
        return sb.toString();
    }
}
