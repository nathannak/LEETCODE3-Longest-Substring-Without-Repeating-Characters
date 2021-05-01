3. Longest Substring Without Repeating Characters

class Solution {
    fun lengthOfLongestSubstring(s: String): Int {
        
        var map = mutableMapOf<Char,Int>()
        var l   : Int = 0
        var r   : Int = 0
        var max : Int = 0
        
        while(r < s.toCharArray().size){
            
            val ch =  s.toCharArray()[r]
            print(ch)
            
            if(!map.containsKey(ch)){
                max = Math.max(max,r-l+1) // otherwise calc max
            }else{
                
                // 1 always look for smallest interval
                // 2 while updating l, don't calculate max, otherwise
                // do calculate max
                
                //have to do this, otherwise, smart cast exception
                val pos = map.get(ch)!!
                
                if(l <= pos){ // <= is super important
                    //always look for smallest interval
                    l = pos + 1 // while updating l, do not calc max
                }else{
                    max = Math.max(max,r-l+1) // otherwise calc max
                }
            }
            
            map.put(ch,r)
            r++
        }
        
        return max
    }
}
