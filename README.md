# TreeMap

1.  Напишете програма, която брои колко пъти се среща всяко число в дадена редица от числа.
Пример: array = {3, 4, 4, 2, 3, 3, 4, 3, 2}
2 a 2 пъти
3 a 4 пъти
4 a 3 път

import java.util.Map;
import java.util.TreeMap;

public class exam {
	
	   public static void main(String[] args) {
		   
		  int array[] = {3, 4, 4, 2, 3, 3, 4, 3, 2};	
		   
		  Map<Integer, Integer> tree = new TreeMap<Integer, Integer>();
		  for (int i : array) {
			  Integer count = tree.get(i);
			  if(count == null) {
				  count = 0;
			  }
			  tree.put(i, count + 1);
		}
		  for(Map.Entry<Integer, Integer> me : tree.entrySet()) {
			  System.out.printf("'%d' > %d%n", me.getKey(), me.getValue());
		  }
		  
	}
}

2.  Напишете програма, която премахва всички числа, които се срещат нечетен брой пъти в дадена редица.
 Например, ако имаме началната редица {4, 2, 2, 5, 2, 3, 2, 3, 1, 5, 2, 6, 6, 6},
 трябва да я редуцираме до редицата {5, 3, 3, 5}.
 
import java.util.HashMap;

public class exam {

	     public static void main(String[] args) {
	    	 
	    	 int array[] = {4, 2, 2, 5, 2, 3, 2, 3, 1, 5, 2, 6, 6, 6};
	    	 
	    	 HashMap<Integer, Integer> hashmap = new HashMap<Integer, Integer>();
			 int count = 0;
	    	 for (int i = 0; i < array.length; i++) {
				for (int j = 0; j < array.length; j++) {
					if (array[i] == array[j]) {
						count++;
					}
				}
				if (count % 2 == 0) {
					hashmap.put(i, array[i]);
				}
				count = 0;	
	    	 }
    		System.out.println(hashmap.values());
	     }
   }
 
 3.  Напишете програма, която по даден текст във текстов файл, преброява колко пъти се среща всяка дума.
 Отпечатайте на конзолата всички думи и по колко пъти се срещат, подредени по брой срещания.
Пример: "This is the TEXT. Text, text, text – THIS TEXT! Is this the text?"
Резултат:
is a 2, the a 2, this a 3, text a 6

package zad;

import java.util.LinkedHashMap;
import java.util.Map;
import java.util.Map.Entry;
import java.util.TreeMap;
import java.util.stream.Collectors;

public class Zad {

	  public static void main(String[] args) {
		  		   
		  String text = "This is the TEXT."                
			  		+ " Text, text, text – THIS TEXT!"
			  		+ " Is this the text?";
		  
		  TreeMap<String, Integer> treeMap = new TreeMap<String, Integer>();
		  text = text.toLowerCase();
		  String[] arrayText = text.split("\\W+");
		  for (int i = 0; i < arrayText.length; i++) {
			  Integer count = treeMap.get(arrayText[i]);
			  if (count == null) {
				  count = 0;
			  }
			  treeMap.put(arrayText[i], count + 1);

		  }
		  // sorted treeMap by Value in sortedMap
		  LinkedHashMap<String, Integer> sortedMap = 
				    treeMap.entrySet().stream().
				    sorted(Entry.comparingByValue()).
				    collect(Collectors.toMap(Entry::getKey, Entry::getValue,
				                             (e1, e2) -> e1, LinkedHashMap::new));
		  

		  System.out.println(treeMap + "\n");
		  //print sortedMap
		  for(Map.Entry<String, Integer> mapEntry : sortedMap.entrySet()) {
			  System.out.printf("%s > %d%n", mapEntry.getKey(), mapEntry.getValue());
		  }
	}
 }


 

 
