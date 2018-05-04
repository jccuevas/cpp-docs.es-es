---
title: Punteros (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarators, pointers
- declarations, pointers
- pointers [C++]
- pointers, declarations
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04d794041df385a9e18a8a4b25460d961a340cda
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="pointers-c"></a>Punteros (C++)
Los punteros se declaran mediante la siguiente secuencia.  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers   
[ms-modifier] declarator ;  
```  
  
 donde se puede usar cualquier declarador de puntero válido para `declarator`.  La sintaxis de un declarador de puntero simple es la siguiente:  
  
```  
* [cv-qualifiers] identifier [= expression]  
```  
  
 1. Los especificadores de la declaración:  
  
-   Un especificador de clase de almacenamiento opcional. Para obtener más información, consulte [especificadores](../cpp/specifiers.md).  
  
-   Una palabra clave `const` o `volatile` opcional que se aplica al tipo de objeto al que se apunta.  
  
-   El especificador de tipo: el nombre de un tipo que representa el tipo del objeto al que se apunta.  
  
 2. El declarador:  
  
-   Un modificador opcional específico de Microsoft. Para obtener más información, consulte [modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md).  
  
-   El operador `*`.  
  
-   Una palabra clave `const` o `volatile` opcional que se aplica al propio puntero.  
  
-   El identificador.  
  
-   Un inicializador opcional.  
  
 El declarador de un puntero a función tiene el siguiente aspecto:  
  
```  
(* [cv-qualifiers] identifier )( argument-list ) [cv-qualifers]  
[exception specification] [= expression];  
```  
  
-   Para una matriz de punteros, la sintaxis es la siguiente:  
  
```  
* identifier [ [ constant-expression ] ]  
```  
  
-   Varios declaradores y sus inicializadores pueden aparecer juntos en una sola declaración en una lista separada por comas detrás del especificador de declaración.  
  
 Un ejemplo simple de una declaración de puntero es:  
  
```  
char *pch;  
```  
  
 La declaración anterior especifica que `pch` apunta un objeto de tipo `char`.  
  
 Un ejemplo más complejo es  
  
```  
static unsigned int * const ptr;  
```  
  
 La declaración anterior especifica que `ptr` es un puntero constante a un objeto de tipo `unsigned` `int` con una duración de almacenamiento estática.  
  
 En el ejemplo siguiente se muestra cómo se declaran e inicializan varios punteros:  
  
```  
static int *p = &i, *q = &j;  
```  
  
 En el ejemplo anterior, los punteros p y q apuntan a objetos de tipo `int` y se inicializan en las direcciones de i y j, respectivamente.  El especificador de clase de almacenamiento `static` se aplica a ambos punteros.  
  
## <a name="example"></a>Ejemplo  
  
```  
// pointer.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   int i = 1, j = 2; // local variables on the stack  
   int *p;  
  
   // a pointer may be assigned to "point to" the value of  
   // another variable using the & (address of) operator  
   p = & j;   
  
   // since j was on the stack, this address will be somewhere  
   // on the stack.  Pointers are printed in hex format using  
   // %p and conventionally marked with 0x.    
   printf_s("0x%p\n",  p);  
  
   // The * (indirection operator) can be read as "the value  
   // pointed to by".  
   // Since p is pointing to j, this should print "2"  
   printf_s("0x%p %d\n",  p, *p);  
  
   // changing j will change the result of the indirection  
   // operator on p.  
   j = 7;  
   printf_s("0x%p %d\n",  p, *p );  
  
   // The value of j can also be changed through the pointer  
   // by making an assignment to the dereferenced pointer  
   *p = 10;  
   printf_s("j is %d\n", j); // j is now 10  
  
   // allocate memory on the heap for an integer,  
   // initialize to 5  
   p = new int(5);  
  
   // print the pointer and the object pointed to  
   // the address will be somewhere on the heap  
   printf_s("0x%p %d\n",  p, *p);  
  
   // free the memory pointed to by p  
   delete p;  
  
   // At this point, dereferencing p with *p would trigger  
   // a runtime access violation.  
  
   // Pointer arithmetic may be done with an array declared  
   // on the stack or allocated on the heap with new.  
   // The increment operator takes into account the size   
   // of the objects pointed to.  
   p = new int[5];  
   for (i = 0; i < 5; i++, p++) {  
      *p = i * 10;  
      printf_s("0x%p %d\n", p, *p);  
   }  
  
   // A common expression seen is dereferencing in combination  
   // with increment or decrement operators, as shown here.  
   // The indirection operator * takes precedence over the   
   // increment operator ++.   
   // These are particularly useful in manipulating char arrays.  
   char s1[4] = "cat";  
   char s2[4] = "dog";  
   char* p1 = s1;  
   char* p2 = s2;  
  
   // the following is a string copy operation  
   while (*p1++ = *p2++);  
  
   // s2 was copied into s1, so now they are both equal to "dog"  
   printf_s("%s %s", s1, s2);  
}  
```  
  
```Output  
0x0012FEC8  
0x0012FEC8 2  
0x0012FEC8 7  
j is 10  
0x00320850 5  
0x00320850 0  
0x00320854 10  
0x00320858 20  
0x0032085C 30  
0x00320860 40  
dog dog  
```  
  
## <a name="example"></a>Ejemplo  
 Otro ejemplo muestra el uso de punteros en estructuras de datos; en este caso, una lista vinculada.  
  
```  
// pointer_linkedlist.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
struct NewNode {  
   NewNode() : node(0){}  
   int i;  
   NewNode * node;  
};  
  
void WalkList(NewNode * ptr) {  
   if (ptr != 0) {  
      int i = 1;  
      while (ptr->node != 0 ) {  
         cout << "node " << i++ << " = " << ptr->i << endl;  
         ptr = ptr->node;  
      }  
      cout << "node " << i++ << " = " << ptr->i << endl;  
   }  
}  
  
void AddNode(NewNode ** ptr) {  
   NewNode * walker = 0;  
   NewNode * MyNewNode = new NewNode;  
   cout << "enter a number: " << endl;  
   cin >> MyNewNode->i;  
  
   if (*ptr == 0)  
      *ptr = MyNewNode;  
   else  {  
      walker = *ptr;  
      while (walker->node != 0)  
         walker = walker->node;  
  
      walker->node = MyNewNode;  
   }  
}  
  
int main() {  
   char ans = ' ';  
   NewNode * ptr = 0;  
   do {  
      cout << "a (add node)  d (display list)  q (quit)" << endl;  
      cin >> ans;  
      switch (ans) {  
      case 'a':  
         AddNode(&ptr);  
         break;  
      case 'd':  
         WalkList(ptr);  
         break;  
      }  
   } while (ans != 'q');  
}  
```  
  
```Output  
  
      a  
45  
d  
a  
789  
d  
qa (add node)  d (display list)  q (quit)  
enter a number:   
a (add node)  d (display list)  q (quit)  
node 1 = 45  
a (add node)  d (display list)  q (quit)  
enter a number:   
a (add node)  d (display list)  q (quit)  
node 1 = 45  
node 2 = 789  
a (add node)  d (display list)  q (quit)  
```  
  
## <a name="see-also"></a>Vea también  
 [Operador de direccionamiento indirecto: *](../cpp/indirection-operator-star.md)   
 [address-of (Operador): &](../cpp/address-of-operator-amp.md)