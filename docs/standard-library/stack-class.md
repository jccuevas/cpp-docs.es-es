---
title: "stack (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::stack"
  - "std.stack"
  - "stack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pila, stack (clase)"
  - "stack (clase)"
ms.assetid: 02151c1e-eab0-41b8-be94-a839ead78ecf
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# stack (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase de adaptador de contenedor de plantilla que proporciona una restricción de la funcionalidad que limita el acceso al elemento agregado más recientemente a algún tipo de contenedor subyacente. La clase de pila se usa cuando es importante tener claro que solo se están realizando operaciones de pila en el contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Type, class Container= deque <Type>>  
class stack  
```  
  
#### <a name="parameters"></a>Parámetros  
 *ype*  
 Tipo de datos de los elementos que se van a almacenar en la pila.  
  
 `Container`  
 Tipo del contenedor subyacente que se usa para implementar la pila. El valor predeterminado es la clase `deque`*\< tipo>*.  
  
## <a name="remarks"></a>Comentarios  
 Los elementos de la clase **tipo** estipulado en la primera plantilla son sinónimos de parámetro de un objeto de pila [value_type](#stack__value_type) y debe coincidir con el tipo de elemento de la clase de contenedor subyacente **contenedor** estipulado por el segundo parámetro de plantilla. El **tipo** debe ser asignable, por lo que es posible copiar objetos de ese tipo y para asignar valores a variables de ese tipo.  
  
 Incluyen clases de contenedor subyacente adecuadas para la pila [deque](../standard-library/deque-class.md), [list (clase)](../standard-library/list-class.md), y [vector, clase](vector%20Class.md), o cualquier otro contenedor de secuencia que admite las operaciones de **volver**, `push_back`, y `pop_back`. La clase de contenedor subyacente se encapsula dentro del adaptador de contenedor, que solo expone el conjunto limitado de las funciones miembro de contenedor de secuencias como una interfaz pública.  
  
 La pila de objetos son igualdad comparable si y solo si los elementos de la clase **tipo** son comparables igualdad y menor-que comparable si y solo si los elementos de la clase **tipo** son menores-que comparable.  
  
-   La clase de pila es compatible con una estructura de datos LIFO (el último en entrar es el primero en salir). Un buen símil sería una pila de platos. Solo se pueden insertar e inspeccionar elementos (platos) en la parte superior de la pila, que es el último elemento al final del contenedor base, y solo se pueden quitar de ahí. La restricción de acceder únicamente al elemento superior es el motivo por el que se usa la clase stack.  
  
-   El [queue clase](../standard-library/queue-class.md) admite una estructura de datos, primero en salir (FIFO). Un buen símil sería el de personas que hacen cola en un banco. Se pueden agregar elementos (personas) a la parte posterior de la línea y quitarlos de la parte delantera de la línea. Se puede inspeccionar tanto la parte delantera como trasera de una línea. La restricción de acceder únicamente a los elementos delanteros y traseros de esta manera es el motivo por el que se usa la clase queue.  
  
-   El [priority_queue (clase)](../standard-library/priority-queue-class.md) ordena sus elementos para que siempre es el elemento más grande en la parte superior. Admite la inserción de un elemento y la inspección y eliminación del elemento superior. Un buen símil sería el de personas alineadas y organizadas por edad, altura o cualquier otro criterio.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[pila](#stack__stack)|Construye una `stack` que está vacía o que es una copia de un objeto contenedor base.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[container_type](#stack__container_type)|Tipo que proporciona el contenedor base que debe adaptarse mediante una `stack`.|  
|[size_type](#stack__size_type)|Tipo entero sin signo que puede representar el número de elementos de un `stack`.|  
|[value_type](#stack__value_type)|Tipo que representa el tipo de objeto almacenado como elemento en una `stack`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[vacía](#stack__empty)|Comprueba si la `stack` está vacía.|  
|[POP](#stack__pop)|Quita el elemento de la parte superior de la `stack`.|  
|[inserción](#stack__push)|Agrega un elemento a la parte superior de la `stack`.|  
|[tamaño](#stack__size)|Devuelve el número de elementos de `stack`.|  
|[Arriba](#stack__top)|Devuelve una referencia a un elemento en la parte superior de la `stack`.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< pila>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namestackcontainertypea-stackcontainertype"></a><a name="stack__container_type"></a>  Stack:: container_type  
 Un tipo que proporciona el contenedor base debe adaptarse.  
  
```  
typedef Container container_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla `Container`. Las tres clases de contenedor STL secuencia: la clase vector, clase de lista y deque de clase predeterminado, cumplir los requisitos que se usará como el contenedor base para un objeto de la pila. También pueden utilizarse tipos definidos por el usuario que cumpla estos requisitos.  
  
 Para obtener más información sobre `Container`, vea la sección Comentarios de la [stack (clase)](../standard-library/stack-class.md) tema.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [Stack:: Stack](#stack__stack) para obtener un ejemplo de cómo declarar y utilizar `container_type`.  
  
##  <a name="a-namestackemptya-stackempty"></a><a name="stack__empty"></a>  Stack:: Empty  
 Comprueba si una pila está vacía.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** Si la pila está vacía; **false** Si la pila está vacía.  
  
### <a name="example"></a>Ejemplo  
  
```  
// stack_empty.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   // Declares stacks with default deque base container  
   stack <int> s1, s2;  
  
   s1.push( 1 );  
  
   if ( s1.empty( ) )  
      cout << "The stack s1 is empty." << endl;  
   else  
      cout << "The stack s1 is not empty." << endl;  
  
   if ( s2.empty( ) )  
      cout << "The stack s2 is empty." << endl;  
   else  
      cout << "The stack s2 is not empty." << endl;  
}  
```  
  
```Output  
The stack s1 is not empty.  
The stack s2 is empty.  
```  
  
##  <a name="a-namestackpopa-stackpop"></a><a name="stack__pop"></a>  Stack:: POP  
 Quita el elemento de la parte superior de la pila.  
  
```  
void pop();
```  
  
### <a name="remarks"></a>Comentarios  
 La pila no debe estar vacía para aplicar la función miembro. La parte superior de la pila es la posición ocupada por el elemento agregado más recientemente y el último elemento al final del contenedor.  
  
### <a name="example"></a>Ejemplo  
  
```  
// stack_pop.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   stack <int> s1, s2;  
  
   s1.push( 10 );  
   s1.push( 20 );  
   s1.push( 30 );  
  
   stack <int>::size_type i;  
   i = s1.size( );  
   cout << "The stack length is " << i << "." << endl;  
  
   i = s1.top( );  
   cout << "The element at the top of the stack is "  
        << i << "." << endl;  
  
   s1.pop( );  
  
   i = s1.size( );  
   cout << "After a pop, the stack length is "   
        << i << "." << endl;  
  
   i = s1.top( );  
   cout << "After a pop, the element at the top of the stack is "  
        << i << "." << endl;  
}  
```  
  
```Output  
The stack length is 3.  
The element at the top of the stack is 30.  
After a pop, the stack length is 2.  
After a pop, the element at the top of the stack is 20.  
```  
  
##  <a name="a-namestackpusha-stackpush"></a><a name="stack__push"></a>  Stack:: Push  
 Agrega un elemento al extremo superior de la pila.  
  
```  
void push(const Type& val);
```  
  
### <a name="parameters"></a>Parámetros  
 ` val`  
 El elemento agregado a la parte superior de la pila.  
  
### <a name="remarks"></a>Comentarios  
 La parte superior de la pila es la posición ocupada por el elemento agregado más recientemente y el último elemento al final del contenedor.  
  
### <a name="example"></a>Ejemplo  
  
```  
// stack_push.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   stack <int> s1;  
  
   s1.push( 10 );  
   s1.push( 20 );  
   s1.push( 30 );  
  
   stack <int>::size_type i;  
   i = s1.size( );  
   cout << "The stack length is " << i << "." << endl;  
  
   i = s1.top( );  
   cout << "The element at the top of the stack is "  
        << i << "." << endl;  
}  
```  
  
```Output  
The stack length is 3.  
The element at the top of the stack is 30.  
```  
  
##  <a name="a-namestacksizea-stacksize"></a><a name="stack__size"></a>  Stack:: Size  
 Devuelve el número de elementos en la pila.  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud actual de la pila.  
  
### <a name="example"></a>Ejemplo  
  
```  
// stack_size.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   stack <int> s1, s2;  
   stack <int>::size_type i;  
  
   s1.push( 1 );  
   i = s1.size( );  
   cout << "The stack length is " << i << "." << endl;  
  
   s1.push( 2 );  
   i = s1.size( );  
   cout << "The stack length is now " << i << "." << endl;  
}  
```  
  
```Output  
The stack length is 1.  
The stack length is now 2.  
```  
  
##  <a name="a-namestacksizetypea-stacksizetype"></a><a name="stack__size_type"></a>  Stack:: size_type  
 Un tipo de entero sin signo que puede representar el número de elementos de una pila.  
  
```  
typedef typename Container::size_type size_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `size_type` del contenedor base adaptado la pila.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [tamaño](#stack__size) para obtener un ejemplo de cómo declarar y utilizar `size_type`.  
  
##  <a name="a-namestackstacka-stackstack"></a><a name="stack__stack"></a>  Stack:: Stack  
 Construye una pila que está vacío o que es una copia de una clase de contenedor base.  
  
```  
stack();

explicit stack(const container_type& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 El contenedor del que la pila construida es a ser una copia.  
  
### <a name="example"></a>Ejemplo  
  
```  
// stack_stack.cpp  
// compile with: /EHsc  
#include <stack>  
#include <vector>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares stack with default deque base container  
   stack <char> dsc1;  
  
   //Explicitly declares a stack with deque base container  
   stack <char, deque<char> > dsc2;  
  
   // Declares a stack with vector base containers  
   stack <int, vector<int> > vsi1;  
  
   // Declares a stack with list base container  
   stack <int, list<int> > lsi;  
  
   // The second member function copies elements from a container  
   vector<int> v1;  
   v1.push_back( 1 );  
   stack <int, vector<int> > vsi2( v1 );  
   cout << "The element at the top of stack vsi2 is "  
        << vsi2.top( ) << "." << endl;  
}  
```  
  
```Output  
The element at the top of stack vsi2 is 1.  
```  
  
##  <a name="a-namestacktopa-stacktop"></a><a name="stack__top"></a>  Stack  
 Devuelve una referencia a un elemento en la parte superior de la pila.  
  
```  
reference top();

const_reference top() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al último elemento del contenedor en la parte superior de la pila.  
  
### <a name="remarks"></a>Comentarios  
 La pila no debe estar vacía para aplicar la función miembro. La parte superior de la pila es la posición ocupada por el elemento agregado más recientemente y el último elemento al final del contenedor.  
  
 Si el valor devuelto de **superior** se asigna a un `const_reference`, no se puede modificar el objeto de pila. Si el valor devuelto de **superior** se asigna a un **referencia**, se puede modificar el objeto de pila.  
  
### <a name="example"></a>Ejemplo  
  
```  
// stack_top.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   stack <int> s1;  
  
   s1.push( 1 );  
   s1.push( 2 );  
  
   int& i = s1.top( );  
   const int& ii = s1.top( );  
  
   cout << "The top integer of the stack s1 is "  
        << i << "." << endl;  
   i--;  
   cout << "The next integer down is "<< ii << "." << endl;  
}  
```  
  
```Output  
The top integer of the stack s1 is 2.  
The next integer down is 1.  
```  
  
##  <a name="a-namestackvaluetypea-stackvaluetype"></a><a name="stack__value_type"></a>  Stack:: value_type  
 Tipo que representa el tipo de objeto almacenado como un elemento en una pila.  
  
```  
typedef typename Container::value_type value_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `value_type` del contenedor base adaptado la pila.  
  
### <a name="example"></a>Ejemplo  
  
```  
// stack_value_type.cpp  
// compile with: /EHsc  
#include <stack>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   // Declares stacks with default deque base container  
   stack<int>::value_type AnInt;  
  
   AnInt = 69;  
   cout << "The value_type is AnInt = " << AnInt << endl;  
  
   stack<int> s1;  
   s1.push( AnInt );  
   cout << "The element at the top of the stack is "  
        << s1.top( ) << "." << endl;  
}  
```  
  
```Output  
The value_type is AnInt = 69  
The element at the top of the stack is 69.  
```  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)

