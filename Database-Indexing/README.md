Every developer needs to know about database indexing<br>
So why we use indexing ?
<br>
To improve Query performance<br>
Indexing is the way to optimise the performance of a database by minimizing the number of <br>
disk Accesses required when a query is processed. It is a data structure technique that is used to <br>
quickly locate and access the data in a database.<br> 

You can read more about it here <br>
<a href="https://www.geeksforgeeks.org/indexing-in-databases-set-1/">DataBase Indexing </a><br>
Now my understanding and some extra learning<br>
Index is a ordered representation of indexed data<br>
Introducing concept of BTree in indexing <br>
As you can see image below every node left to root(23) is less than 23 and every node right to Root(23)<br>
is greater than or equal to 23 and one important thing is all leave nodes are on same level(Balanced Tree)<br>
which ensures that time taken to access every node is same and every leave node is connected in a doubly linked list form
<br>
<img src="../Src/Btree.jpg"></img><br>
Doubly linked list ensures that during scanning we don't have to go up the tree<br>
Actually how it is store is shown below <br>
<img src="../Src/Btree2.jpg"></img><br>
It stores value + Rowid which is location of or Address of row inside the memory <br>
Pros for storing like this<br>
1. Searching is very fast (logarithmic)<br>
2. Logarithmic Scaling<br>

Cons <br>
Indexing makes reading faster but writing slower<br>
Indexing has a attribute which is very useful <br>
which is <br>
Access Types: This refers to the type of access such as value based search, range access, etc.<br>
so if it is <br>
1. Const/EQ_Ref <br>
it means perform a btree traversal to find a single value<br>
and it can only be used if uniqueness is guaranteed  <br>
2. Ref/Range<br>
Also known as index range scan<br>
Perform a b tree traversal to find the starting point <br>
Scan values from that point on<br>
Stops if it finds a value that doesn't meet the criteria<br>
3. Index<br>
Also known as full index scan<br>
Start at first leave node <br>
Traverse through the entire index <br>
still use index<br>
4. All<br>
Also known as full table scan<br>
does not use a index at all<br>
loads every column of every row from the table<br>
Scan through all of them and emits or discard accordingly<br>
<h4>Some of serious cons of indexing</h4>

1. Index can't be used on functions like
in my SQL Query 
where Func() .. some function call = equals something then 
here index will not work
solution to this is we can use Between if we can so we can make it a Range Scan
2. Order matter in multicolumn index
like i have a index of 
cola colb cloc
then in qurey they should be called like this only in this pattern 
because they are sorted like that you can't skip a cloumn
3. Index also not supports inequality operation
like in ordered way you can't use between

In short index is responsibility of developers (all caps)





