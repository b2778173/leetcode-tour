# 49. Group Anagrams

**Example 1:**

```text
Input: strs = ["eat","tea","tan","ate","nat","bat"]
Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
```

**Example 2:**

```text
Input: strs = [""]
Output: [[""]]
```

#### Think

1. 同組字串在排序後都會相同
2. 排序後的字串當作key , groud list當value,存在 map中

#### Steps

1. new map, key is a collection.
2. iterate the strs , to char \[\] and sort to make a common key.
3. if map contain , get the list and add to it, otherwise create a list and add.
4. create a answer to collect all from map.

```java
 public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<>();
        for(String s : strs){
               char[] ca = s.toCharArray();
               Arrays.sort(ca);
               String cas =  String.valueOf(ca);
               if(map.containsKey(cas)){
                      map.get(cas).add(s);
               }else{
                      List<String> group = new ArrayList<>();
                      group.add(s);
                      s.put(cas ,group);
               }
        }
        List<List<String>> ans = new ArrayList<>();
        for(String e : map.keySet()){
               ans.add(map.get(e));
        }
        return ans;       
 }
```

