Download Link: https://assignmentchef.com/product/solved-ds-lab1-linked-list
<br>
After completed this tutorial, you can implement a list ADT with linked list. Please review Generic before starting this tutorial.

1.      UML model of Linked list

The following figure presents an UML model of linked list:

<ul>

 <li>ListInterface represents public functions of linked list, e.g., add new item, remove an item.</li>

 <li>Node class represents an item (node) in linked list.</li>

 <li>MyLinkedList class implements ListInterface and includes items have Node types.</li>

</ul>

In the next section, we will approach how to implement a linked list based on the above UML model.

<h1>2.      <em>Node </em>class</h1>

<em>Node </em>is the basic item in list, thus we need to implement it first.

<table width="529">

 <tbody>

  <tr>

   <td width="529">public class Node &lt;E&gt; { private E data; private Node &lt;E&gt; next; public Node(){ data = null; next = null;}public Node(E data){ this(data, null);}public Node(E data, Node &lt;E&gt; next){ this.data = data; this.next = next;}public Node &lt;E&gt; getNext(){ return next;}public E getData(){ return data;}public void setNext(Node &lt;E&gt; n){ next = n;}}</td>

  </tr>

 </tbody>

</table>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

<h1>3.      <em>ListInterface </em>interface</h1>

<em>ListInterface </em>defines the operations (methods) we would like to have in a List ADT.

<table width="529">

 <tbody>

  <tr>

   <td width="529">import java.util.NoSuchElementException; public interface ListInterface &lt;E&gt; { public void addFirst(E item); public void addAfter(Node &lt;E&gt; curr, E item); public void addLast(E item);public E removeFirst() throws NoSuchElementException; public E removeAfter(Node &lt;E&gt; curr) throwsNoSuchElementException; public E removeLast() throws NoSuchElementException;public void print(); public boolean isEmpty(); public E getFirst() throws NoSuchElementException; public Node &lt;E&gt; getHead(); public int size();public boolean contains(E item);}</td>

  </tr>

 </tbody>

</table>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

<h1>4.      <em>MyLinkedList </em>class</h1>

This <em>MyLinkedList </em>class will implement the <em>ListInterface </em>interface.

<table width="529">

 <tbody>

  <tr>

   <td width="529">import java.util.NoSuchElementException;public class MyLinkedList &lt;E&gt; implements ListInterface&lt;E&gt; { private Node &lt;E&gt; head; private int numNode; public MyLinkedList(){ head = null; numNode = 0;}@Overridepublic void addFirst(E item){ head = new Node&lt;E&gt;(item, head);numNode++;}@Overridepublic void addAfter(Node&lt;E&gt; curr, E item){ if(curr == null){ addFirst(item);} else{Node&lt;E&gt; newNode = new Node&lt;E&gt;(item, curr.getNext()); curr.setNext(newNode);}numNode++;}@Overridepublic void addLast(E item){ if(head == null){ addFirst(item);}else{Node&lt;E&gt; tmp = head; while(tmp.getNext() != null){ tmp = tmp.getNext();}Node&lt;E&gt; newNode = new Node&lt;&gt;(item, null);tmp.setNext(newNode); numNode++;}}@Overridepublic E removeFirst() throws NoSuchElementException{ if(head == null){ throw new NoSuchElementException(“Can’t remove elementfrom an empty list”);}else{Node&lt;E&gt; tmp = head; head = head.getNext(); numNode–;return tmp.getData();}}</td>

  </tr>

 </tbody>

</table>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

25

26

27

28

29

30

31

32

33

34

35

36

37

38

39

40

41

42

43

44

45

46

47

48

49

50

51

<table width="529">

 <tbody>

  <tr>

   <td width="529">@Override public E removeAfter(Node&lt;E&gt; curr) throwsNoSuchElementException{ if(curr == null){ throw new NoSuchElementException(“Can’t remove elementfrom an empty list”);} else{Node&lt;E&gt; delNode = curr.getNext(); if(delNode != null) { curr.setNext(delNode.getNext()); numNode–;return delNode.getData();} else{ throw new NoSuchElementException(“No next node to remove”);}}}@Override public E removeLast() throws NoSuchElementException{if(head == null){ throw new NoSuchElementException(“Can’t remove elementfrom an empty list”);}else{Node&lt;E&gt; preNode = null;Node&lt;E&gt; delNode = head; while(delNode.getNext() != null){ preNode = delNode;delNode = delNode.getNext();} preNode.setNext(delNode.getNext()); delNode.setNext(null); numNode–;return delNode.getData(); }}@Override public void print(){ if(head != null){Node&lt;E&gt; tmp = head;System.out.print(“List: ” + tmp.getData()); tmp = tmp.getNext();while(tmp != null){System.out.print(” -&gt; ” + tmp.getData()); tmp = tmp.getNext();}System.out.println();} else{System.out.println(“List is empty!”);</td>

  </tr>

 </tbody>

</table>

52

53

54

55

56

57

58

59

60

61

62

63

64

65

66

67

68

69

70

71

72

73

74

75

76

77

78

79

80

81

82

83

84

85

86

87

88

89

90

91

92

93

94

95

96

97

98

99

100

101

102

103

104

<table width="529">

 <tbody>

  <tr>

   <td width="27">}</td>

   <td width="502">}}@Overridepublic boolean isEmpty(){ if(numNode == 0) return true;return false;}@Overridepublic E getFirst() throws NoSuchElementException{ if(head == null){ throw new NoSuchElementException(“Can’t get elementfrom an empty list”);} else{ return head.getData(); }}@Overridepublic Node&lt;E&gt; getHead(){ return head;}@Override public int size(){ return numNode;}@Overridepublic boolean contains(E item){ Node&lt;E&gt; tmp = head; while(tmp != null){ if(tmp.getData().equals(item)) return true;tmp = tmp.getNext();}return false;}</td>

  </tr>

 </tbody>

</table>

105

106

107

108

109

110

111

112

113

114

115

116

117

118

119

120

121

122

123

124

125

126

127

128

129

130

131

132

133

134

135

136

137

138

139

<h1>5.      Test Integer Linked List</h1>

<table width="529">

 <tbody>

  <tr>

   <td width="529">public class Test { public static void main(String[] args){MyLinkedList&lt;Integer&gt; list = new MyLinkedList&lt;Integer&gt;(); list.addFirst(new Integer(2)); list.addLast(new Integer(3)); list.print();}}</td>

  </tr>

 </tbody>

</table>

1

2

3

4

5

6

7

8

9

<ol start="6">

 <li><strong> Excercise</strong></li>

</ol>

<h1>Exercise 1</h1>

Giving <strong>Fraction </strong>class as the following class diagram:

You need to implement a linked list to contain Fraction items.

<h1>Exercise 2</h1>

Suppose that we have an abstract method with signature as follow:

<strong>public E removeCurr(Node&lt;E&gt; curr)</strong>

This method removes the node at position <em>curr</em>. You need to add this abstract method to your program and implement it.

<h1>Exercise 3</h1>

Suppose we are having a list of integer numbers, do the following requirements:

<ul>

 <li>Count the number of even item in the list.</li>

 <li>Count the number of prime item in the list.</li>

 <li>Add item X before the first even element in the list.</li>

 <li>Find the maximum number in the list.</li>

 <li>(*) Reverse the list without using temporary list.</li>

 <li>(*) Sort the list in ascending order.</li>

</ul>