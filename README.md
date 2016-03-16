package zn_1;
 
import java.util.Map;  
import java.util.StringTokenizer;  
import java.util.Map.Entry; 
import java.util.ArrayList;  
import java.util.HashMap;  
import java.util.List;
import java.util.regex.Pattern;
import java.util.regex.Matcher;
import java.util.Collections;  
import java.util.Comparator; 
    
public class zn_1  {  
public static void main(String arg[]){      
  
    String sentence="Word is case insensitive, i.e. “file”, “FILE” and “File” are considered the same word."; 
    Map<String,Integer> map=new HashMap<String,Integer>();  
    String turn_sentence= sentence.toLowerCase();
    StringTokenizer token=new StringTokenizer(turn_sentence); 
    while(token.hasMoreTokens()){  
        
        String word=token.nextToken(", :\"\".“”");  
        if(map.containsKey(word)){      
            int count=map.get(word);  
            map.put(word, count+1);     
        }  
        else  
            map.put(word, 1);          
    }  
    small(map);                        
}  
public static boolean isNumeric(String str) {
Pattern pattern = Pattern.compile("[0-9]*");
Matcher isNum = pattern.matcher(str.charAt(0)+"");
if (!isNum.matches()) {
return false;
}
return true;
}
public static void small(Map<String,Integer> map){ 
    List<Map.Entry<String, Integer>> infoids = new ArrayList<Map.Entry<String, Integer>>(map.entrySet());   
    Collections.sort(infoids, new Comparator<Map.Entry<String, Integer>>() {    
        public int compare(Map.Entry<String, Integer> o1, Map.Entry<String, Integer> o2) {     
            return (o2.getValue() - o1.getValue());     
        }     
});
    for (int i = 0; i <infoids.size(); i++) {   
        Entry<String, Integer> id =infoids.get(i);  
        if(id.getKey().length()>3){
    System.out.println(id.getKey()+":"+id.getValue()); 
}
        }  
}  
}
