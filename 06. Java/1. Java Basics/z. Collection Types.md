#### Basic Types

`ArrayList` - Array, enough said <br>
`Hashtable` - Dictionary that is not thread-safe <br>
`HashMap` - Dictionary that is thread-safe <br>
`HashSet` - Set <br>
`LinkedList` - Linked list, that's it <br>
`TreeMap` - Sorted Dictionary <br>


#### Array

```
ArrayList<String> array1 = new ArrayList<String>();
array1.add("Washington DC");
array1.add("Boston");
System.out.println(array1.size());

System.out.println(array1.get(1));
Iterator<String> iterator = array1.iterator();
while (iterator.hasNext()) {
    System.out.println(iterator.next());
}
```

#### Hashtable

```
Hashtable<String, String> hashtable1 = new Hashtable<>();
hashtable1.put("Boston", "MA");
hashtable1.put("Vienna", "VA");
System.out.println(hashtable1.get("Vienna"));
```

#### HashMap

```
HashMap<String, String> hashmap1 = new HashMap<>();
hashmap1.put("Slovakia", "Bratislava");
hashmap1.put("Hungary", "Budapest");
System.out.println(hashmap1.get("Hungary"));
```

#### HashSet

```
HashSet<String> hashSet1 = new HashSet<>();
hashSet1.add("Europe");
hashSet1.add("Asia");
hashSet1.add("Asia");
hashSet1.add("North America");
System.out.println(hashSet1);
```

#### LinkedList

```
LinkedList<String> linkedList1 = new LinkedList<String> () ;
linkedList1.add("Cricket");
linkedList1.add("Soccer");
linkedList1.add("Hockey");
linkedList1.add("Tennis");

Iterator iterator2 = linkedList1.iterator();
while (iterator2.hasNext()) {
    System.out.println(iterator2.next());
}
System.out.println(linkedList1.size());
```

#### TreeMap

```
TreeMap<Integer, String> treeMap1 = new TreeMap<Integer, String>();
treeMap1.put(4, "New Orleans");
treeMap1.put(2, "Cambridge");
```
