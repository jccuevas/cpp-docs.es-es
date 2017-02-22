---
title: "front_insert_iterator (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "iterator/std::front_insert_iterator"
  - "std::front_insert_iterator"
  - "std.front_insert_iterator"
  - "front_insert_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "front_insert_iterator (clase)"
ms.assetid: a9a9c075-136a-4419-928b-c4871afa033c
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# front_insert_iterator (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

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
 El contenedor debe satisfacer los requisitos para una secuencia de inserción en el inicio donde sea posible insertar elementos al inicio de la secuencia en tiempo constante amortizado. Los contenedores de secuencia de la biblioteca de plantillas estándar definidos por el [deque (clase)](../standard-library/deque-class.md) y [list (clase)](../standard-library/list-class.md) proporcionan el necesaria `push_front` miembro de función y cumplen estos requisitos. Por el contrario, contenedores de secuencias definidos por el [vector, clase](vector%20Class.md) no cumplen estos requisitos y no se puede adaptar para su uso con `front_insert_iterator`s. Un `front_insert_iterator` debe inicializarse siempre con su contenedor.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[front_insert_iterator](#front_insert_iterator__front_insert_iterator)|Crea un iterador que puede insertar elementos en el inicio de un objeto contenedor especificado.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[container_type](#front_insert_iterator__container_type)|Tipo que representa el contenedor en el que se va a hacer una inserción inicial.|  
|[referencia](#front_insert_iterator__reference)|Tipo que proporciona una referencia a un elemento de una secuencia controlada por el contenedor asociado.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operador *](#front_insert_iterator__operator_star)|Operador de desreferencia usado para implementar la expresión de iterador de salida * `i` = `x` para una inserción inicial.|  
|[operator ++](#front_insert_iterator__operator_add_add)|Incrementa el `front_insert_iterator` a la siguiente ubicación en la que puede almacenarse un valor.|  
|[operador =](#front_insert_iterator__operator_eq)|Operador de asignación usado para implementar la expresión de iterador de salida * `i` = `x` para una inserción inicial.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado**: \< iterator>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namefrontinsertiteratorcontainertypea-frontinsertiteratorcontainertype"></a><a name="front_insert_iterator__container_type"></a>  front_insert_iterator:: container_type  
 Tipo que representa el contenedor en el que se va a hacer una inserción inicial.  
  
```  
typedef Container container_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **contenedor**.  
  
### <a name="example"></a>Ejemplo  
  
```  
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
  
##  <a name="a-namefrontinsertiteratorfrontinsertiteratora-frontinsertiteratorfrontinsertiterator"></a><a name="front_insert_iterator__front_insert_iterator"></a>  front_insert_iterator:: front_insert_iterator  
 Crea un iterador que puede insertar elementos en el inicio de un objeto contenedor especificado.  
  
```  
explicit front_insert_iterator(Container& _Cont);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Cont`  
 El objeto de contenedor en el que los `front_insert_iterator` consiste en Insertar elementos.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `front_insert_iterator` para el objeto de contenedor de parámetro.  
  
### <a name="example"></a>Ejemplo  
  
```  
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
  
##  <a name="a-namefrontinsertiteratoroperatorstara-frontinsertiteratoroperator"></a><a name="front_insert_iterator__operator_star"></a>  front_insert_iterator:: operator *  
 Desreferencia el iterador de inserción devolver el elemento al que apunta.  
  
```  
front_insert_iterator<Container>& operator*();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La función miembro devuelve el valor del elemento direccionado.  
  
### <a name="remarks"></a>Comentarios  
 Utilizado para implementar la expresión de iterador de salida **\*Iter** = **valor**. Si **Iter** es un iterador que direcciona un elemento de una secuencia, a continuación, **\*Iter** = **valor** reemplaza ese elemento con el valor y no cambia el número total de elementos de la secuencia.  
  
### <a name="example"></a>Ejemplo  
  
```  
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
  
##  <a name="a-namefrontinsertiteratoroperatoraddadda-frontinsertiteratoroperator"></a><a name="front_insert_iterator__operator_add_add"></a>  front_insert_iterator:: operator ++  
 Incrementa el `back_insert_iterator` a la siguiente ubicación en la que puede almacenarse un valor.  
  
```  
front_insert_iterator<Container>& operator++();

front_insert_iterator<Container> operator++(int);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `front_insert_iterator` direcciona la ubicación siguiente en el que se puede almacenar un valor.  
  
### <a name="remarks"></a>Comentarios  
 Operadores de preincrementation y postincrementation devuelven el mismo resultado.  
  
### <a name="example"></a>Ejemplo  
  
```  
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
  
##  <a name="a-namefrontinsertiteratoroperatoreqa-frontinsertiteratoroperator"></a><a name="front_insert_iterator__operator_eq"></a>  front_insert_iterator:: operator =  
 Anexa (inserciones) un valor en la parte frontal del contenedor.  
  
```  
front_insert_iterator<Container>& operator=(typename Container::const_reference val);

front_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```  
  
### <a name="parameters"></a>Parámetros  
 ` val`  
 El valor que se asigna al contenedor.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al último elemento insertado al principio del contenedor.  
  
### <a name="remarks"></a>Comentarios  
 El primer operador de miembro se evalúa como `container.push_front( val)`, a continuación, devuelve `*this`.  
  
 Evalúa el segundo operador de miembro  
  
 `container->push_front((typename Container::value_type&&) val)`,  
  
 a continuación, devuelve `*this`.  
  
### <a name="example"></a>Ejemplo  
  
```  
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
  
##  <a name="a-namefrontinsertiteratorreferencea-frontinsertiteratorreference"></a><a name="front_insert_iterator__reference"></a>  front_insert_iterator:: Reference  
 Tipo que proporciona una referencia a un elemento de una secuencia controlada por el contenedor asociado.  
  
```  
typedef typename Container::reference reference;  
```  
  
### <a name="example"></a>Ejemplo  
  
```  
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
 [\< iterador>](../standard-library/iterator.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)

