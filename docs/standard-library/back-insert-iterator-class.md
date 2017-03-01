---
title: back_insert_iterator (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- iterator/std::back_insert_iterator
- std::back_insert_iterator
- back_insert_iterator
- std.back_insert_iterator
dev_langs:
- C++
helpviewer_keywords:
- back_insert_iterator class
ms.assetid: a1ee07f2-cf9f-46a1-8608-cfaf207f9713
caps.latest.revision: 21
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
ms.openlocfilehash: b50819686ca10a5676c75fb47375572d39974a1f
ms.lasthandoff: 02/24/2017

---
# <a name="backinsertiterator-class"></a>back_insert_iterator (Clase)
Describe un adaptador de iterador que satisface los requisitos de un iterador de salida. Inserta, en lugar de sobrescribir, elementos en el final de una secuencia y proporciona así la semántica que es diferente de la semántica que sobrescribe proporcionada por los iteradores de los contenedores de la secuencia de C++. La clase `back_insert_iterator` se hace plantilla en el tipo de contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Container>  
class back_insert_iterator;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Container`  
 El tipo de contenedor en cuyo final `back_insert_iterator` va a insertar los elementos.  
  
## <a name="remarks"></a>Comentarios  
 El contenedor debe satisfacer los requisitos para una secuencia de inserción en el final donde sea posible insertar elementos al final de la secuencia en tiempo constante amortizado. Los contenedores de secuencia de la biblioteca estándar de C++ definidos por las clases [deque](../standard-library/deque-class.md), [list](../standard-library/list-class.md) y [vector](../standard-library/vector-class.md) proporcionan la función miembro `push_back` necesaria y satisfacen estos requisitos. Estos tres contenedores así como las cadenas se pueden adaptar para su uso con `back_insert_iterator`. Un `back_insert_iterator` debe inicializarse siempre con su contenedor.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[back_insert_iterator](#back_insert_iterator__back_insert_iterator)|Construye un `back_insert_iterator` que inserta elementos después del último elemento de un contenedor.|  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[container_type](#back_insert_iterator__container_type)|Tipo que proporciona un contenedor para `back_insert_iterator`.|  
|[reference](#back_insert_iterator__reference)|Tipo que proporciona una referencia para `back_insert_iterator`.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator*](#back_insert_iterator__operator_star)|Operador de desreferencia usado para implementar la expresión de iterador de salida * `i` = `x` para una inserción al final.|  
|[operator++](#back_insert_iterator__operator_add_add)|Incrementa el `back_insert_iterator` a la siguiente ubicación en la que puede almacenarse un valor.|  
|[operator=](#back_insert_iterator__operator_eq)|Operador de asignación usado para implementar la expresión de iterador de salida * `i` = `x` para una inserción al final.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<iterator>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namebackinsertiteratorbackinsertiteratora--backinsertiteratorbackinsertiterator"></a><a name="back_insert_iterator__back_insert_iterator"></a>  back_insert_iterator::back_insert_iterator  
 Construye un `back_insert_iterator` que inserta elementos después del último elemento de un contenedor.  
  
```   
explicit back_insert_iterator(Container& _Cont);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Cont`  
 Contenedor en el que `back_insert_iterator` va a insertar un elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 `back_insert_iterator` para el contenedor del parámetro.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// back_insert_iterator_back_insert_iterator.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for ( i = 1 ; i < 4 ; ++i )    
   {  
      vec.push_back ( i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   // Insertions with member function  
   back_inserter ( vec ) = 40;  
   back_inserter ( vec ) = 50;  
  
   // Alternatively, insertions can be done with template function  
   back_insert_iterator<vector<int> > backiter ( vec );  
 *backiter = 600;  
   backiter++;  
 *backiter = 700;  
  
   cout << "After the insertions, the vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 1 2 3 ).  
After the insertions, the vector vec is: ( 1 2 3 40 50 600 700 ).  
```  
  
##  <a name="a-namebackinsertiteratorcontainertypea--backinsertiteratorcontainertype"></a><a name="back_insert_iterator__container_type"></a>  back_insert_iterator::container_type  
 Tipo que proporciona un contenedor para `back_insert_iterator`.  
  
```   
typedef Container  
container_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **Container**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// back_insert_iterator_container_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 4 ; ++i )    
   {  
      vec.push_back (  i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The original vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   back_insert_iterator<vector<int> >::container_type vec1 = vec;  
   back_inserter ( vec1 ) = 40;  
  
   cout << "After the insertion, the vector is: ( ";  
   for ( vIter = vec1.begin ( ) ; vIter != vec1.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The original vector vec is: ( 1 2 3 ).  
After the insertion, the vector is: ( 1 2 3 40 ).  
```  
  
##  <a name="a-namebackinsertiteratoroperatorstara--backinsertiteratoroperator"></a><a name="back_insert_iterator__operator_star"></a>  back_insert_iterator::operator*  
 Operador de desreferencia usado para implementar la expresión de iterador de salida \* *i* = *x*.  
  
```  
back_insert_iterator<Container>& operator*();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al elemento insertado al final del contenedor.  
  
### <a name="remarks"></a>Comentarios  
 Se usa para implementar la expresión de iterador de salida **\*Iter** = **value**. Si **Iter** es un iterador que dirige un elemento de una secuencia, **\*Iter** = **value** sustituye ese elemento por el valor y no cambia el número total de elementos de la secuencia.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// back_insert_iterator_back_insert.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 4 ; ++i )    
   {  
      vec.push_back ( i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   back_insert_iterator<vector<int> > backiter ( vec );  
 *backiter = 10;  
   backiter++;      // Increment to the next element  
 *backiter = 20;  
   backiter++;  
  
   cout << "After the insertions, the vector vec becomes: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 1 2 3 ).  
After the insertions, the vector vec becomes: ( 1 2 3 10 20 ).  
```  
  
##  <a name="a-namebackinsertiteratoroperatoraddadda--backinsertiteratoroperator"></a><a name="back_insert_iterator__operator_add_add"></a>  back_insert_iterator::operator++  
 Incrementa el `back_insert_iterator` a la siguiente ubicación en la que puede almacenarse un valor.  
  
```  
back_insert_iterator<Container>& operator++();
back_insert_iterator<Container> operator++(int);
```  
  
### <a name="return-value"></a>Valor devuelto  
 `back_insert_iterator` que dirige a la siguiente ubicación en la que se puede almacenar un valor.  
  
### <a name="remarks"></a>Comentarios  
 Ambos operadores de incremento previo e incremento posterior devuelven el mismo resultado.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// back_insert_iterator_op_incre.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 3 ; ++i )    
   {  
      vec.push_back ( 10 * i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   back_insert_iterator<vector<int> > backiter ( vec );  
 *backiter = 30;  
   backiter++;      // Increment to the next element  
 *backiter = 40;  
   backiter++;  
  
   cout << "After the insertions, the vector vec becomes: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 10 20 ).  
After the insertions, the vector vec becomes: ( 10 20 30 40 ).  
```  
  
##  <a name="a-namebackinsertiteratoroperatoreqa--backinsertiteratoroperator"></a><a name="back_insert_iterator__operator_eq"></a>  back_insert_iterator::operator=  
 Anexa o inserta un valor en el extremo final de un contenedor.  
  
```  
back_insert_iterator<Container>& operator=(typename Container::const_reference val);
back_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```  
  
### <a name="parameters"></a>Parámetros  
 ` val`  
 Valor que se va a insertar en el contenedor.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al último elemento insertado al final del contenedor.  
  
### <a name="remarks"></a>Comentarios  
 El primer operador miembro evalúa `Container.push_back( val)`,  
  
 después, devuelve `*this`. El segundo operador miembro evalúa  
  
 `container->push_back((typename Container::value_type&&)val)`,  
  
 después, devuelve `*this`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// back_insert_iterator_op_assign.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 4 ; ++i )    
   {  
      vec.push_back ( i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   back_insert_iterator<vector<int> > backiter ( vec );  
 *backiter = 10;  
   backiter++;      // Increment to the next element  
 *backiter = 20;  
   backiter++;  
  
   cout << "After the insertions, the vector vec becomes: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="a-namebackinsertiteratorreferencea--backinsertiteratorreference"></a><a name="back_insert_iterator__reference"></a>  back_insert_iterator::reference  
 Tipo que proporciona una referencia para `back_insert_iterator`.  
  
```  
typedef typename Container::reference reference;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una referencia a un elemento de la secuencia controlada por el contenedor asociado.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// back_insert_iterator_reference.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 4 ; ++i )    
   {  
      vec.push_back ( i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   back_insert_iterator<vector<int> >::reference   
        RefLast = *(vec.end ( ) - 1 );  
   cout << "The last element in the vector vec is: "   
        << RefLast << "." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 1 2 3 ).  
The last element in the vector vec is: 3.  
```  
  
## <a name="see-also"></a>Vea también  
 [\<iterator>](../standard-library/iterator.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)


