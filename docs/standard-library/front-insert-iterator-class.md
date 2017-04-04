---
title: front_insert_iterator (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- iterator/std::front_insert_iterator
- std::front_insert_iterator
- std.front_insert_iterator
- front_insert_iterator
dev_langs:
- C++
helpviewer_keywords:
- front_insert_iterator class
ms.assetid: a9a9c075-136a-4419-928b-c4871afa033c
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 6468f372324cb6f62b5b09524cfbf5386b1502c6
ms.lasthandoff: 02/24/2017

---
# <a name="frontinsertiterator-class"></a>front_insert_iterator (Clase)
Describe un adaptador de iterador que satisface los requisitos de un iterador de salida. Inserta, en lugar de sobrescribir, elementos en el inicio de una secuencia y proporciona así la semántica que es diferente de la semántica que sobrescribe proporcionada por los iteradores de los contenedores de la secuencia de C++. La clase `front_insert_iterator` se hace plantilla en el tipo de contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Container>  
class front_insert_iterator;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Container`  
 El tipo de contenedor en cuyo inicio `front_insert_iterator` va a insertar los elementos.  
  
## <a name="remarks"></a>Comentarios  
 El contenedor debe satisfacer los requisitos para una secuencia de inserción en el inicio donde sea posible insertar elementos al inicio de la secuencia en tiempo constante amortizado. Los contenedores de secuencias de la biblioteca estándar de C++ definidos por las clases [deque](../standard-library/deque-class.md) y [list](../standard-library/list-class.md) proporcionan la función miembro `push_front` necesaria y cumplen estos requisitos. Por el contrario, los contenedores de secuencias definidos por la [clase vector](../standard-library/vector-class.md) no cumplen estos requisitos y no se pueden adaptar para su uso con `front_insert_iterator`s. Un `front_insert_iterator` debe inicializarse siempre con su contenedor.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[front_insert_iterator](#front_insert_iterator__front_insert_iterator)|Crea un iterador que puede insertar elementos en el inicio de un objeto contenedor especificado.|  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[container_type](#front_insert_iterator__container_type)|Tipo que representa el contenedor en el que se va a hacer una inserción inicial.|  
|[reference](#front_insert_iterator__reference)|Tipo que proporciona una referencia a un elemento de una secuencia controlada por el contenedor asociado.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator*](#front_insert_iterator__operator_star)|Operador de desreferencia usado para implementar la expresión del iterador de salida * `i` = `x` para una inserción inicial.|  
|[operator++](#front_insert_iterator__operator_add_add)|Incrementa el `front_insert_iterator` a la siguiente ubicación en la que puede almacenarse un valor.|  
|[operator=](#front_insert_iterator__operator_eq)|Operador de asignación usado para implementar la expresión del iterador de salida * `i` = `x` para una inserción inicial.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<iterator>  
  
 **Espacio de nombres:** std  
  
##  <a name="front_insert_iterator__container_type"></a>  front_insert_iterator::container_type  
 Tipo que representa el contenedor en el que se va a hacer una inserción inicial.  
  
```  
typedef Container container_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **Container**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// front_insert_iterator_container_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   list<int> L1;  
   front_insert_iterator<list<int> >::container_type L2 = L1;  
   front_inserter ( L2 ) = 20;  
   front_inserter ( L2 ) = 10;  
   front_inserter ( L2 ) = 40;  
  
   list <int>::iterator vIter;  
   cout << "The list L2 is: ( ";  
   for ( vIter = L2.begin ( ) ; vIter != L2.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L2 is: ( 40 10 20 ).  
*\  
```  
  
##  <a name="front_insert_iterator__front_insert_iterator"></a>  front_insert_iterator::front_insert_iterator  
 Crea un iterador que puede insertar elementos en el inicio de un objeto contenedor especificado.  
  
```  
explicit front_insert_iterator(Container& _Cont);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Cont`  
 Objeto contenedor en el que `front_insert_iterator` va a insertar elementos.  
  
### <a name="return-value"></a>Valor devuelto  
 `front_insert_iterator` para el objeto contenedor del parámetro.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// front_insert_iterator_front_insert_iterator.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   list <int>::iterator L_Iter;  
  
   list<int> L;  
   for (i = -1 ; i < 9 ; ++i )    
   {  
      L.push_back ( 2 * i );  
   }  
  
   cout << "The list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
  
   // Using the member function to insert an element  
   front_inserter ( L ) = 20;  
  
   // Alternatively, one may use the template function  
   front_insert_iterator< list < int> > Iter(L);  
 *Iter = 30;  
  
   cout << "After the front insertions, the list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L is:  
 ( -2 0 2 4 6 8 10 12 14 16 ).  
After the front insertions, the list L is:  
 ( 30 20 -2 0 2 4 6 8 10 12 14 16 ).  
*\  
```  
  
##  <a name="front_insert_iterator__operator_star"></a>  front_insert_iterator::operator*  
 Desreferencia el iterador de inserción que devuelve el elemento al que se dirige.  
  
```  
front_insert_iterator<Container>& operator*();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La función miembro devuelve el valor del elemento al que se dirige.  
  
### <a name="remarks"></a>Comentarios  
 Se usa para implementar la expresión de iterador de salida **\*Iter** = **value**. Si **Iter** es un iterador que dirige un elemento de una secuencia, **\*Iter** = **value** sustituye ese elemento por el valor y no cambia el número total de elementos de la secuencia.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// front_insert_iterator_deref.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   list <int>::iterator L_Iter;  
  
   list<int> L;  
   for ( i = -1 ; i < 9 ; ++i )   
   {  
      L.push_back ( 2 * i );  
   }  
  
   cout << "The list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
  
   front_insert_iterator< list < int> > Iter(L);  
 *Iter = 20;  
  
   // Alternatively, you may use  
   front_inserter ( L ) = 30;  
  
   cout << "After the front insertions, the list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L is:  
 ( -2 0 2 4 6 8 10 12 14 16 ).  
After the front insertions, the list L is:  
 ( 30 20 -2 0 2 4 6 8 10 12 14 16 ).  
*\  
```  
  
##  <a name="front_insert_iterator__operator_add_add"></a>  front_insert_iterator::operator++  
 Incrementa el `back_insert_iterator` a la siguiente ubicación en la que puede almacenarse un valor.  
  
```  
front_insert_iterator<Container>& operator++();

front_insert_iterator<Container> operator++(int);
```  
  
### <a name="return-value"></a>Valor devuelto  
 `front_insert_iterator` que dirige a la siguiente ubicación en la que se puede almacenar un valor.  
  
### <a name="remarks"></a>Comentarios  
 Ambos operadores de incremento previo e incremento posterior devuelven el mismo resultado.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// front_insert_iterator_op_incre.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   list<int> L1;  
   front_insert_iterator<list<int> > iter ( L1 );  
 *iter = 10;  
   iter++;  
 *iter = 20;  
   iter++;  
 *iter = 30;  
   iter++;  
  
   list <int>::iterator vIter;  
   cout << "The list L1 is: ( ";  
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L1 is: ( 30 20 10 ).  
*\  
```  
  
##  <a name="front_insert_iterator__operator_eq"></a>  front_insert_iterator::operator=  
 Anexa (inserta) un valor en el principio del contenedor.  
  
```  
front_insert_iterator<Container>& operator=(typename Container::const_reference val);

front_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```  
  
### <a name="parameters"></a>Parámetros  
 `val`  
 Valor que se va a asignar al contenedor.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al último elemento insertado al principio del contenedor.  
  
### <a name="remarks"></a>Comentarios  
 El primer operador miembro evalúa `container.push_front( val)` y después devuelve `*this`.  
  
 El segundo operador miembro evalúa  
  
 `container->push_front((typename Container::value_type&&) val)`,  
  
 después, devuelve `*this`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// front_insert_iterator_op_assign.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   list<int> L1;  
   front_insert_iterator<list<int> > iter ( L1 );  
 *iter = 10;  
   iter++;  
 *iter = 20;  
   iter++;  
 *iter = 30;  
   iter++;  
  
   list <int>::iterator vIter;  
   cout << "The list L1 is: ( ";  
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L1 is: ( 30 20 10 ).  
*\  
```  
  
##  <a name="front_insert_iterator__reference"></a>  front_insert_iterator::reference  
 Tipo que proporciona una referencia a un elemento de una secuencia controlada por el contenedor asociado.  
  
```  
typedef typename Container::reference reference;  
```  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// front_insert_iterator_reference.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   list<int> L;  
   front_insert_iterator<list<int> > fiivIter( L );  
 *fiivIter = 10;  
 *fiivIter = 20;  
 *fiivIter = 30;  
  
   list<int>::iterator LIter;  
   cout << "The list L is: ( ";  
   for ( LIter = L.begin ( ) ; LIter != L.end ( ); LIter++)  
      cout << *LIter << " ";  
   cout << ")." << endl;  
  
   front_insert_iterator<list<int> >::reference   
        RefFirst = *(L.begin ( ));  
   cout << "The first element in the list L is: "   
        << RefFirst << "." << endl;  
}  
\* Output:   
The list L is: ( 30 20 10 ).  
The first element in the list L is: 30.  
*\  
```  
  
## <a name="see-also"></a>Vea también  
 [\<iterator>](../standard-library/iterator.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)


