---
title: vector (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::vector
- vector
- std.vector
dev_langs:
- C++
helpviewer_keywords:
- vector class
ms.assetid: a3e0a8f8-7565-4fe0-93e4-e4d74ae1b70d
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 2a2235788f548dbe40625999935cdf396107cbd6
ms.lasthandoff: 02/24/2017

---
# <a name="vector-class"></a>vector (Clase)
La clase vector de la biblioteca estándar de C++ es una clase de plantilla de contenedores de secuencias que organiza los elementos de un tipo determinado en una organización lineal y permite el acceso aleatorio rápido a cualquier elemento. Deberían ser el contenedor más apropiado para una secuencia cuando el rendimiento de acceso aleatorio sea importante.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Type, class Allocator = allocator<Type>>  
class vector  
```  
  
#### <a name="parameters"></a>Parámetros  
 *ype*  
 Tipo de datos de elementos que se almacenará en el vector.  
  
 `Allocator`  
 Tipo que representa el objeto asignador almacenado que encapsula los detalles sobre la asignación y la desasignación de memoria del vector. Este argumento es opcional y el valor predeterminado es **allocator***\<Type>.*  
  
## <a name="remarks"></a>Comentarios  
 Los vectores permiten inserciones y eliminaciones de tiempo constante al final de la secuencia. Insertar o eliminar elementos en medio de un vector requiere tiempo lineal. El rendimiento del contenedor [deque (Clase)](../standard-library/deque-class.md) es superior respecto a las inserciones y eliminaciones al principio y al final de una secuencia. El contenedor [list (Clase)](../standard-library/list-class.md) es superior respecto a las inserciones y eliminaciones en cualquier ubicación dentro de una secuencia.  
  
 Se produce una reasignación del vector cuando una función miembro debe aumentar la secuencia contenida en el objeto de vectores más allá de su capacidad de almacenamiento actual. Otras inserciones y eliminaciones pueden modificar varias direcciones de almacenamiento dentro de la secuencia. En todos estos casos, los iteradores y referencias que apuntan a partes alteradas de la secuencia dejan de ser válidos. Si no se produce ninguna reasignación, solo los iteradores y referencias antes del punto de inserción o eliminación siguen siendo válidos.  
  
 La [clase vector\<bool>](../standard-library/vector-bool-class.md) es una especialización completa del vector de clase de plantilla para los elementos de tipo booleano, con un asignador para el tipo subyacente que usa la especialización.  
  
 La [clase de referencia vector\<bool>](../standard-library/vector-bool-class.md#vector_lt_bool_gt___reference_class) es una clase anidada cuyos objetos pueden proporcionar referencias a elementos (bits únicos) dentro de un objeto vector\<bool>.  
  
## <a name="members"></a>Miembros  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[vector](#vector__vector)|Construye un vector de un tamaño determinado o con elementos de un valor determinado, o con un `allocator` específico, o como una copia de algún otro vector.|  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[allocator_type](#vector__allocator_type)|Tipo que representa la clase `allocator` para el objeto vector.|  
|[const_iterator](#vector__const_iterator)|Tipo que proporciona un iterador de acceso aleatorio que puede leer un elemento `const` en un vector.|  
|[const_pointer](#vector__const_pointer)|Tipo que proporciona un puntero a un elemento `const` en un vector.|  
|[const_reference](#vector__const_reference)|Tipo que proporciona una referencia a un elemento `const` almacenado en un vector para leer y realizar operaciones `const`.|  
|[const_reverse_iterator](#vector__const_reverse_iterator)|Tipo que proporciona un iterador de acceso aleatorio que puede leer cualquier elemento `const` en el vector.|  
|[difference_type](#vector__difference_type)|Tipo que proporciona la diferencia entre las direcciones de dos elementos en un vector.|  
|[iterator](#vector__iterator)|Tipo que proporciona un iterador de acceso aleatorio que puede leer o modificar cualquier elemento de un vector.|  
|[pointer](#vector__pointer)|Tipo que proporciona un puntero a un elemento en un vector.|  
|[reference](#vector__reference)|Tipo que proporciona una referencia a un elemento almacenado en un vector.|  
|[reverse_iterator](#vector__reverse_iterator)|Tipo que proporciona un iterador de acceso aleatorio que puede leer o modificar cualquier elemento en un vector invertido.|  
|[size_type](#vector__size_type)|Tipo que cuenta el número de elementos de un vector.|  
|[value_type](#vector__value_type)|Tipo que representa el tipo de datos almacenado en un vector.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[assign](#vector__assign)|Borra un vector y copia los elementos especificados al vector vacío.|  
|[at](#vector__at)|Devuelve una referencia al elemento en una ubicación especificada del vector.|  
|[back](#vector__back)|Devuelve una referencia al último elemento del vector.|  
|[begin](#vector__begin)|Devuelve un iterador de acceso aleatorio al primer elemento del vector.|  
|[capacity](#vector__capacity)|Devuelve el número de elementos que puede contener el vector sin asignar más espacio de almacenamiento.|  
|[cbegin](#vector__cbegin)|Devuelve un iterador const de acceso aleatorio al primer elemento del vector.|  
|[cend](#vector__cend)|Devuelve un iterador const de acceso aleatorio que apunta justo después del final del vector.|  
|[crbegin](#vector__crbegin)|Devuelve un iterador constante al primer elemento de un vector invertido.|  
|[crend](#vector__crend)|Devuelve un iterador constante al final de un vector invertido.|  
|[clear](#vector__clear)|Borra los elementos del vector.|  
|[data](#vector__data)|Devuelve un puntero al primer elemento del vector.|  
|[emplace](#vector__emplace)|Inserta en una posición especificada del vector un elemento construido en contexto.|  
|[emplace_back](#vector__emplace_back)|Agrega al final del vector un elemento construido en contexto.|  
|[empty](#vector__empty)|Comprueba si el contenedor de vectores está vacío.|  
|[end](#vector__end)|Devuelve un iterador de acceso aleatorio que apunta al final del vector.|  
|[erase](#vector__erase)|Quita un elemento o un intervalo de elementos en un vector a partir de posiciones especificadas.|  
|[front](#vector__front)|Devuelve una referencia al primer elemento de un vector.|  
|[get_allocator](#vector__get_allocator)|Devuelve un objeto a la clase `allocator` usada por un vector.|  
|[insert](#vector__insert)|Inserta uno o varios elementos en el vector en una posición especificada.|  
|[max_size](#vector__max_size)|Devuelve la longitud máxima del vector.|  
|[pop_back](#vector__pop_back)|Elimina el elemento situado al final del vector.|  
|[push_back](#vector__push_back)|Agrega un elemento al final del vector.|  
|[rbegin](#vector__rbegin)|Devuelve un iterador al primer elemento en un vector inverso.|  
|[rend](#vector__rend)|Devuelve un iterador al final de un vector invertido.|  
|[reserve](#vector__reserve)|Reserva una longitud mínima de almacenamiento para un objeto vectorial.|  
|[resize](#vector__resize)|Especifica un nuevo tamaño de un vector.|  
|[shrink_to_fit](#vector__shrink_to_fit)|Descarta el exceso de capacidad.|  
|[size](#vector__size)|Devuelve el número de elementos del vector.|  
|[swap](#vector__swap)|Intercambia los elementos de dos vectores.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator&#91;&#93;](#vector__operator_at)|Devuelve una referencia al elemento vector en una posición especificada.|  
|[operator=](#vector__operator_eq)|Reemplaza los elementos del vector con una copia de otro vector.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<vector>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namevectorallocatortypea--vectorallocatortype"></a><a name="vector__allocator_type"></a>  vector::allocator_type  
 Tipo que representa la clase de asignador para el objeto de vector.  
  
```  
typedef Allocator allocator_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 `allocator_type` es un sinónimo del parámetro de plantilla **Allocator**.  
  
### <a name="example"></a>Ejemplo  
  Vea en el ejemplo de [get_allocator](#vector__get_allocator) cómo se usa `allocator_type`.  
  
##  <a name="a-namevectorassigna--vectorassign"></a><a name="vector__assign"></a>  vector::assign  
 Borra un vector y copia los elementos especificados al vector vacío.  
  
```  
void assign(size_type Count, const Type& Val);
void assign(initializer_list<Type> IList);

template <class InputIterator>  
void assign(InputIterator First, InputIterator Last);
```  
  
### <a name="parameters"></a>Parámetros  
 `First`  
 Posición del primer elemento en el intervalo de elementos que se va a copiar.  
  
 `Last`  
 Posición del primer elemento más allá del intervalo de elementos que se va a copiar.  
  
 `Count`  
 Número de copias de un elemento que se va a insertar en el vector.  
  
 `Val`  
 Valor del elemento que se va a insertar en el vector.  
  
 `IList`  
 initializer_list que contiene los elementos que se van a insertar.  
  
### <a name="remarks"></a>Comentarios  
 Después de borrar los elementos existentes en un vector, assign inserta en un vector un intervalo especificado de elementos del vector original o inserta en un vector copias de un nuevo elemento de un valor especificado.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
/ vector_assign.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    vector<int> v1, v2, v3;  
  
    v1.push_back(10);  
    v1.push_back(20);  
    v1.push_back(30);  
    v1.push_back(40);  
    v1.push_back(50);  
  
    cout << "v1 = ";  
    for (auto& v : v1){  
        cout << v << " ";  
    }  
    cout << endl;  
  
    v2.assign(v1.begin(), v1.end());  
    cout << "v2 = ";  
    for (auto& v : v2){  
        cout << v << " ";  
    }  
    cout << endl;  
  
    v3.assign(7, 4);  
    cout << "v3 = ";  
    for (auto& v : v3){  
        cout << v << " ";  
    }  
    cout << endl;  
  
    v3.assign({ 5, 6, 7 });  
    for (auto& v : v3){  
        cout << v << " ";  
    }  
    cout << endl;  
}  
  
```  
  
##  <a name="a-namevectorata--vectorat"></a><a name="vector__at"></a>  vector::at  
 Devuelve una referencia al elemento en una ubicación especificada del vector.  
  
```  
reference at(size_type _Pos);

const_reference at(size_type _Pos) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Pos`  
 Subíndice o número de posición del elemento al que se va a hacer referencia en el vector.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al elemento indicado en el argumento. Si `_Off` es mayor que el tamaño del vector, **at** inicia una excepción.  
  
### <a name="remarks"></a>Comentarios  
 Si el valor devuelto de **at** se asigna a una `const_reference`, el objeto de vector no se puede modificar. Si el valor devuelto de **at** se asigna a una **referencia**, el objeto de vector puede modificarse.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_at.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
  
   v1.push_back( 10 );  
   v1.push_back( 20 );  
  
   const int &i = v1.at( 0 );  
   int &j = v1.at( 1 );  
   cout << "The first element is " << i << endl;  
   cout << "The second element is " << j << endl;  
}  
```  
  
```Output  
The first element is 10  
The second element is 20  
```  
  
##  <a name="a-namevectorbacka--vectorback"></a><a name="vector__back"></a>  vector::back  
 Devuelve una referencia al último elemento del vector.  
  
```  
reference back();

const_reference back() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Último elemento del vector. Si el vector está vacío, el valor devuelto no está definido.  
  
### <a name="remarks"></a>Comentarios  
 Si el valor devuelto de **back** se asigna a una `const_reference`, el objeto de vector no se puede modificar. Si el valor devuelto de **back** se asigna a una **referencia**, el objeto de vector puede modificarse.  
  
 Al compilar con [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definido como 1 o 2, se produce un error de tiempo de ejecución si intenta tener acceso a un elemento en un vector vacío.  Para más información, vea [Iteradores activados](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_back.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main() {  
   using namespace std;     
   vector <int> v1;  
  
   v1.push_back( 10 );  
   v1.push_back( 11 );  
  
   int& i = v1.back( );  
   const int& ii = v1.front( );  
  
   cout << "The last integer of v1 is " << i << endl;  
   i--;  
   cout << "The next-to-last integer of v1 is "<< ii << endl;  
}  
```  
  
##  <a name="a-namevectorbegina--vectorbegin"></a><a name="vector__begin"></a>  vector::begin  
 Devuelve un iterador de acceso aleatorio al primer elemento del vector.  
  
```  
const_iterator begin() const;

 
iterator begin();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de acceso aleatorio que se dirige al primer elemento del `vector` o a la ubicación que sigue a un `vector` vacío. Siempre debe comparar el valor devuelto con [vector::end](#vector__end) para asegurarse de que es válido.  
  
### <a name="remarks"></a>Comentarios  
 Si el valor devuelto de `begin` se asigna a un [vector::const_iterator](#vector__const_iterator), el objeto `vector` no se puede modificar. Si el valor devuelto de `begin` se asigna a un [vector::iterator](#vector__iterator), el objeto `vector` se puede modificar.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_begin.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    vector<int> c1;  
    vector<int>::iterator c1_Iter;  
    vector<int>::const_iterator c1_cIter;  
  
    c1.push_back(1);  
    c1.push_back(2);  
  
    cout << "The vector c1 contains elements:";  
    c1_Iter = c1.begin();  
    for (; c1_Iter != c1.end(); c1_Iter++)  
    {  
        cout << " " << *c1_Iter;  
    }  
    cout << endl;  
  
    cout << "The vector c1 now contains elements:";  
    c1_Iter = c1.begin();  
 *c1_Iter = 20;  
    for (; c1_Iter != c1.end(); c1_Iter++)  
    {  
        cout << " " << *c1_Iter;  
    }  
    cout << endl;  
  
    // The following line would be an error because iterator is const  
    // *c1_cIter = 200;  
}  
```  
  
```Output  
The vector c1 contains elements: 1 2  
The vector c1 now contains elements: 20 2  
```  
  
##  <a name="a-namevectorcapacitya--vectorcapacity"></a><a name="vector__capacity"></a>  vector::capacity  
 Devuelve el número de elementos que puede contener el vector sin asignar más espacio de almacenamiento.  
  
```  
size_type capacity() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Longitud actual de almacenamiento asignado para el vector.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro [resize](#vector__resize) es más eficaz si se asigna memoria suficiente para tenerla en cuenta. Use la función miembro [reserve](#vector__reserve) para especificar la cantidad de memoria asignada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_capacity.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
  
   v1.push_back( 1 );  
   cout << "The length of storage allocated is "  
        << v1.capacity( ) << "." << endl;  
  
   v1.push_back( 2 );  
   cout << "The length of storage allocated is now "  
        << v1.capacity( ) << "." << endl;  
}  
```  
  
```Output  
The length of storage allocated is 1.  
The length of storage allocated is now 2.  
```  
  
##  <a name="a-namevectorcbegina--vectorcbegin"></a><a name="vector__cbegin"></a>  vector::cbegin  
 Devuelve un iterador `const` que direcciona el primer elemento del intervalo.  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador `const` de acceso aleatorio que apunta al primer elemento del intervalo o la ubicación situada más allá del final de un intervalo vacío (para un intervalo vacío, `cbegin() == cend()`).  
  
### <a name="remarks"></a>Comentarios  
 Con el valor devuelto de `cbegin`, los elementos del intervalo no se pueden modificar.  
  
 Se puede usar esta función miembro en lugar de la función miembro `begin()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo se considera que `Container` es un contenedor modificable (distinto de `const`) de cualquier naturaleza que admite `begin()` y `cbegin()`.  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="a-namevectorcenda--vectorcend"></a><a name="vector__cend"></a>  vector::cend  
 Devuelve un iterador `const` que direcciona la ubicación situada más allá del último elemento de un intervalo.  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador `const` de acceso aleatorio que apunta justo después del final del intervalo.  
  
### <a name="remarks"></a>Comentarios  
 `cend` se usa para probar si un iterador ha sobrepasado el final de su intervalo.  
  
 Se puede usar esta función miembro en lugar de la función miembro `end()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo, se considera que `Container` es un contenedor modificable (distinto de `const`) de cualquier naturaleza que admite `end()` y `cend()`.  
  
```cpp  
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator  
```  
  
 El valor devuelto por `cend` no se debe desreferenciar.  
  
##  <a name="a-namevectorcleara--vectorclear"></a><a name="vector__clear"></a>  vector::clear  
 Borra los elementos del vector.  
  
```  
void clear();
```  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_clear.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
  
   v1.push_back( 10 );  
   v1.push_back( 20 );  
   v1.push_back( 30 );  
  
   cout << "The size of v1 is " << v1.size( ) << endl;  
   v1.clear( );  
   cout << "The size of v1 after clearing is " << v1.size( ) << endl;  
}  
```  
  
```Output  
The size of v1 is 3  
The size of v1 after clearing is 0  
```  
  
##  <a name="a-namevectorconstiteratora--vectorconstiterator"></a><a name="vector__const_iterator"></a>  vector::const_iterator  
 Un tipo que proporciona un iterador de acceso aleatorio que puede leer un elemento **const** en un vector.  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo `const_iterator` no se puede utilizar para modificar el valor de un elemento.  
  
### <a name="example"></a>Ejemplo  
  Vea en el ejemplo de [back](#vector__back) cómo se usa `const_iterator`.  
  
##  <a name="a-namevectorconstpointera--vectorconstpointer"></a><a name="vector__const_pointer"></a>  vector::const_pointer  
 Un tipo que proporciona un puntero a un elemento **const** en un vector.  
  
```  
typedef typename Allocator::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo `const_pointer` no se puede utilizar para modificar el valor de un elemento.  
  
 Un [iterador](#vector__iterator) se usa normalmente para tener acceso a un elemento de vector.  
  
##  <a name="a-namevectorconstreferencea--vectorconstreference"></a><a name="vector__const_reference"></a>  vector::const_reference  
 Un tipo que proporciona una referencia a un elemento **const** almacenado en un vector para leer operaciones **const** y realizarlas.  
  
```  
typedef typename Allocator::const_reference const_reference;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo `const_reference` no se puede utilizar para modificar el valor de un elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_const_ref.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
  
   v1.push_back( 10 );  
   v1.push_back( 20 );  
  
   const vector <int> v2 = v1;  
   const int &i = v2.front( );  
   const int &j = v2.back( );  
   cout << "The first element is " << i << endl;  
   cout << "The second element is " << j << endl;  
  
   // The following line would cause an error as v2 is const  
   // v2.push_back( 30 );  
}  
```  
  
```Output  
The first element is 10  
The second element is 20  
```  
  
##  <a name="a-namevectorconstreverseiteratora--vectorconstreverseiterator"></a><a name="vector__const_reverse_iterator"></a>  vector::const_reverse_iterator  
 Un tipo que proporciona un iterador de acceso aleatorio que puede leer cualquier elemento **const** en el vector.  
  
```  
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo `const_reverse_iterator` no puede modificar el valor de un elemento y se usa para procesar una iteración en el vector en orden inverso.  
  
### <a name="example"></a>Ejemplo  
  Vea [rbegin](#vector__rbegin) para obtener un ejemplo de cómo declarar y usar un iterador.  
  
##  <a name="a-namevectorcrbegina--vectorcrbegin"></a><a name="vector__crbegin"></a>  vector::crbegin  
 Devuelve un iterador constante al primer elemento de un vector invertido.  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador inverso constante de acceso aleatorio que se dirige al primer elemento de un [vector](../standard-library/vector-class.md) inverso o al que fue el último elemento del `vector` sin invertir.  
  
### <a name="remarks"></a>Comentarios  
 Con el valor devuelto de `crbegin`, el objeto `vector` no se puede modificar.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_crbegin.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   vector <int>::iterator v1_Iter;  
   vector <int>::const_reverse_iterator v1_rIter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
  
   v1_Iter = v1.begin( );  
   cout << "The first element of vector is "  
        << *v1_Iter << "." << endl;  
  
   v1_rIter = v1.crbegin( );  
   cout << "The first element of the reversed vector is "  
        << *v1_rIter << "." << endl;  
}  
```  
  
```Output  
The first element of vector is 1.  
The first element of the reversed vector is 2.  
```  
  
##  <a name="a-namevectorcrenda--vectorcrend"></a><a name="vector__crend"></a>  vector::crend  
 Devuelve un iterador constante que se dirige a la ubicación que sigue al último elemento de un vector invertido.  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador inverso constante de acceso aleatorio que se dirige a la ubicación siguiente al último elemento de un [vector](../standard-library/vector-class.md) invertido (la ubicación que había precedido al primer elemento del `vector` sin invertir).  
  
### <a name="remarks"></a>Comentarios  
 `crend` se usa con un `vector` invertido igual que [vector::cend](#vector__cend) se usa con un `vector`.  
  
 Con el valor devuelto de `crend` (adecuadamente reducido), el objeto de `vector` no se puede modificar.  
  
 Se puede utilizar `crend` para comprobar si un iterador inverso llegó al final de su `vector`.  
  
 El valor devuelto por `crend` no se debe desreferenciar.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_crend.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   vector <int>::const_reverse_iterator v1_rIter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
  
   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )  
      cout << *v1_rIter << endl;  
}  
```  
  
```Output  
2  
1  
```  
  
##  <a name="a-namevectordataa--vectordata"></a><a name="vector__data"></a>  vector::data  
 Devuelve un puntero al primer elemento del vector.  
  
```  
const_pointer data() const;

 
pointer data();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al primer elemento del [vector](../standard-library/vector-class.md) o a la ubicación que sigue a un `vector` vacío.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_data.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    vector<int> c1;  
    vector<int>::pointer c1 ptr;  
    vector<int>::const_pointer c1_cPtr;  
  
    c1.push_back(1);  
    c1.push_back(2);  
  
    cout << "The vector c1 contains elements:";  
    c1_cPtr = c1.data();  
    for (size_t n = c1.size(); 0 < n; --n, c1_cPtr++)  
    {  
        cout << " " << *c1_cPtr;  
    }  
    cout << endl;  
  
    cout << "The vector c1 now contains elements:";  
    c1 ptr = c1.data();  
 *c1 ptr = 20;  
    for (size_t n = c1.size(); 0 < n; --n, c1 ptr++)  
    {  
        cout << " " << *c1 ptr;  
    }  
    cout << endl;  
}  
```  
  
```Output  
The vector c1 contains elements: 1 2  
The vector c1 now contains elements: 20 2  
```  
  
##  <a name="a-namevectordifferencetypea--vectordifferencetype"></a><a name="vector__difference_type"></a>  vector::difference_type  
 Tipo que proporciona la diferencia entre dos iteradores que hacen referencia a elementos del mismo vector.  
  
```  
typedef typename Allocator::difference_type difference_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un `difference_type` también se puede describir como el número de elementos entre dos punteros, dado que un puntero a un elemento contiene su dirección.  
  
 Un [iterador](#vector__iterator) se usa normalmente para tener acceso a un elemento de vector.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <vector>  
#include <algorithm>  
  
int main( )  
{  
   using namespace std;  
  
   vector <int> c1;  
   vector <int>::iterator c1_Iter, c2_Iter;  
  
   c1.push_back( 30 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
   c1.push_back( 10 );  
   c1.push_back( 30 );  
   c1.push_back( 20 );  
  
   c1_Iter = c1.begin( );  
   c2_Iter = c1.end( );  
  
   vector <int>::difference_type   df_typ1, df_typ2, df_typ3;  
  
   df_typ1 = count( c1_Iter, c2_Iter, 10 );  
   df_typ2 = count( c1_Iter, c2_Iter, 20 );  
   df_typ3 = count( c1_Iter, c2_Iter, 30 );  
   cout << "The number '10' is in c1 collection " << df_typ1 << " times.\n";  
   cout << "The number '20' is in c1 collection " << df_typ2 << " times.\n";  
   cout << "The number '30' is in c1 collection " << df_typ3 << " times.\n";  
}  
```  
  
```Output  
The number '10' is in c1 collection 1 times.  
The number '20' is in c1 collection 2 times.  
The number '30' is in c1 collection 3 times.  
```  
  
##  <a name="a-namevectoremplacea--vectoremplace"></a><a name="vector__emplace"></a>  vector::emplace  
 Inserta en una posición especificada del vector un elemento construido en contexto.  
  
```  
iterator emplace(
    const_iterator _Where,  
    Type&& val);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`_Where`|La posición del [vector](../standard-library/vector-class.md) donde se inserta el primer elemento.|  
|` val`|Valor del elemento insertado en el `vector`.|  
  
### <a name="return-value"></a>Valor devuelto  
 La función devuelve un iterador que apunta a la posición en la que se insertó el nuevo elemento en el `vector`.  
  
### <a name="remarks"></a>Comentarios  
 Las operaciones de inserción pueden ser costosas, vea [vector (Clase)](../standard-library/vector-class.md) para obtener una explicación del rendimiento de `vector`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_emplace.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   vector <int>::iterator Iter;  
  
   v1.push_back( 10 );  
   v1.push_back( 20 );  
   v1.push_back( 30 );  
  
   cout << "v1 =" ;  
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
  
// initialize a vector of vectors by moving v1  
   vector < vector <int> > vv1;  
  
   vv1.emplace( vv1.begin(), move( v1 ) );  
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )  
      {  
      cout << "vv1[0] =";  
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )  
         cout << " " << *Iter;  
      cout << endl;  
      }  
}  
```  
  
```Output  
v1 = 10 20 30  
vv1[0] = 10 20 30  
```  
  
##  <a name="a-namevectoremplacebacka--vectoremplaceback"></a><a name="vector__emplace_back"></a>  vector::emplace_back  
 Agrega al final del vector un elemento construido en contexto.  
  
```  
template <class... Types>  
void emplace_back(Types&&... _Args);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`_Args`|Argumentos del constructor. La función deduce qué sobrecarga de constructor invocar según los argumentos que se proporcionan.|  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
#include <vector>  
struct obj  
{  
   obj(int, double) {}  
};  
  
int main()  
{  
   std::vector<obj> v;  
   v.emplace_back(1, 3.14); // obj in created in place in the vector  
}  
  
```  
  
##  <a name="a-namevectoremptya--vectorempty"></a><a name="vector__empty"></a>  vector::empty  
 Comprueba si el vector está vacío.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 **true** si el vector está vacío, **false** si el vector no está vacío.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_empty.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
  
   v1.push_back( 10 );  
  
   if ( v1.empty( ) )  
      cout << "The vector is empty." << endl;  
   else  
      cout << "The vector is not empty." << endl;  
}  
```  
  
```Output  
The vector is not empty.  
```  
  
##  <a name="a-namevectorenda--vectorend"></a><a name="vector__end"></a>  vector::end  
 Devuelve el iterador más allá del final.  
  
```  
iterator end();

const_iterator end() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador más allá del final del vector. Si el vector está vacío, `vector::end() == vector::begin()`.  
  
### <a name="remarks"></a>Comentarios  
 Si el valor devuelto de **end** se asigna a una variable de tipo `const_iterator`, el objeto de vector no se puede modificar. Si el valor devuelto de **end** se asigna a una variable de tipo **iterator**, el objeto de vector se puede modificar.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_end.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator v1_Iter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
  
   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )  
      cout << *v1_Iter << endl;  
}  
```  
  
```Output  
1  
2  
```  
  
##  <a name="a-namevectorerasea--vectorerase"></a><a name="vector__erase"></a>  vector::erase  
 Quita un elemento o un intervalo de elementos en un vector a partir de posiciones especificadas.  
  
```  
iterator erase(
    const_iterator _Where);

iterator erase(
    const_iterator first,  
    const_iterator last);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`_Where`|Posición del elemento que se quita del vector.|  
|` first`|Posición del primer elemento que se quita del vector.|  
|` last`|Posición inmediatamente siguiente al último elemento que se quita del vector.|  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador que designa el primer elemento restante después de los elementos quitados o, si no hay ningún elemento después, un puntero al final del vector.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_erase.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   vector <int>::iterator Iter;  
  
   v1.push_back( 10 );  
   v1.push_back( 20 );  
   v1.push_back( 30 );  
   v1.push_back( 40 );  
   v1.push_back( 50 );  
  
   cout << "v1 =" ;  
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
  
   v1.erase( v1.begin( ) );  
   cout << "v1 =";  
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
  
   v1.erase( v1.begin( ) + 1, v1.begin( ) + 3 );  
   cout << "v1 =";  
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
}  
```  
  
```Output  
v1 = 10 20 30 40 50  
v1 = 20 30 40 50  
v1 = 20 50  
```  
  
##  <a name="a-namevectorfronta--vectorfront"></a><a name="vector__front"></a>  vector::front  
 Devuelve una referencia al primer elemento de un vector.  
  
```  
reference front();

const_reference front() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al primer elemento en el objeto de vector. Si el vector está vacío, el valor devuelto no está definido.  
  
### <a name="remarks"></a>Comentarios  
 Si el valor devuelto de `front` se asigna a `const_reference`, el objeto vector no se puede modificar. Si el valor devuelto de `front` se asigna a una **referencia**, el objeto de vector se puede modificar.  
  
 Al compilar con [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definido como 1 o 2, se produce un error de tiempo de ejecución si intenta tener acceso a un elemento en un vector vacío.  Para más información, vea [Iteradores activados](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_front.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
  
   v1.push_back( 10 );  
   v1.push_back( 11 );  
  
   int& i = v1.front( );  
   const int& ii = v1.front( );  
  
   cout << "The first integer of v1 is "<< i << endl;  
   // by incrementing i, we move the the front reference to the second element  
   i++;  
   cout << "Now, the first integer of v1 is "<< i << endl;  
}  
```  
  
##  <a name="a-namevectorgetallocatora--vectorgetallocator"></a><a name="vector__get_allocator"></a>  vector::get_allocator  
 Devuelve una copia del objeto de asignador usado para construir el vector.  
  
```  
Allocator get_allocator() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Asignador utilizado por el vector.  
  
### <a name="remarks"></a>Comentarios  
 Los asignadores de la clase vector especifican cómo la clase administra el almacenamiento. Los asignadores predeterminados proporcionados con las clases contenedoras de la biblioteca estándar de C++ son suficientes para la mayoría de las necesidades de programación. La escritura y el uso de sus propias clases de asignador son temas avanzados de C++.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_get_allocator.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   // The following lines declare objects that use the default allocator.  
   vector<int> v1;  
   vector<int, allocator<int> > v2 = vector<int, allocator<int> >(allocator<int>( )) ;  
  
   // v3 will use the same allocator class as v1  
   vector <int> v3( v1.get_allocator( ) );  
  
   vector<int>::allocator_type xvec = v3.get_allocator( );  
   // You can now call functions on the allocator class used by vec  
}  
```  
  
##  <a name="a-namevectorinserta--vectorinsert"></a><a name="vector__insert"></a>  vector::insert  
 Inserta un elemento, varios elementos o un intervalo de elementos en el vector en una posición especificada.  
  
```  
iterator insert(
    const_iterator _Where,  
    const Type& val);

iterator insert(
    const_iterator _Where,  
    Type&& val);

void insert(
    const_iterator _Where,  
    size_type count,  
    const Type& val);

template <class InputIterator>  
void insert(
    const_iterator _Where,  
    InputIterator first,  
    InputIterator last);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`_Where`|Posición del vector donde se inserta el primer elemento.|  
|`val`|Valor del elemento que se va a insertar en el vector.|  
|`count`|Número de elementos que se van a insertar en el vector.|  
|`first`|Posición del primer elemento en el intervalo de elementos que se va a copiar.|  
|`last`|Posición del primer elemento más allá del intervalo de elementos que se va a copiar.|  
  
### <a name="return-value"></a>Valor devuelto  
 Las dos primeras funciones `insert` devuelven un iterador que apunta a la posición del vector en la que se insertó el nuevo elemento.  
  
### <a name="remarks"></a>Comentarios  
 Como condición previa, `first` y `last` no deben ser iteradores en el vector o el comportamiento es indefinido. Las operaciones de inserción pueden ser costosas, vea [vector (Clase)](../standard-library/vector-class.md) para obtener una explicación del rendimiento de `vector`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_insert.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   vector <int>::iterator Iter;  
  
   v1.push_back( 10 );  
   v1.push_back( 20 );  
   v1.push_back( 30 );  
  
   cout << "v1 =" ;  
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
  
   v1.insert( v1.begin( ) + 1, 40 );  
   cout << "v1 =";  
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
   v1.insert( v1.begin( ) + 2, 4, 50 );  
  
   cout << "v1 =";  
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
  
   v1.insert( v1.begin( )+1, v1.begin( )+2, v1.begin( )+4 );  
   cout << "v1 =";  
   for (Iter = v1.begin( ); Iter != v1.end( ); Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
  
// initialize a vector of vectors by moving v1  
   vector < vector <int> > vv1;  
  
   vv1.insert( vv1.begin(), move( v1 ) );  
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )  
      {  
      vector < vector <int> >::iterator Iter;  
      cout << "vv1[0] =";  
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )  
         cout << " " << *Iter;  
      cout << endl;  
      }  
}  
```  
  
```Output  
v1 = 10 20 30  
v1 = 10 40 20 30  
v1 = 10 40 50 50 50 50 20 30  
v1 = 10 50 50 40 50 50 50 50 20 30  
vv1[0] = 10 50 50 40 50 50 50 50 20 30  
```  
  
##  <a name="a-namevectoriteratora--vectoriterator"></a><a name="vector__iterator"></a>  vector::iterator  
 Tipo que proporciona un iterador de acceso aleatorio que puede leer o modificar cualquier elemento de un vector.  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 Se puede usar un tipo **iterator** para modificar el valor de un elemento.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [begin](#vector__begin).  
  
##  <a name="a-namevectormaxsizea--vectormaxsize"></a><a name="vector__max_size"></a>  vector::max_size  
 Devuelve la longitud máxima del vector.  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Máxima longitud posible del vector.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_max_size.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   vector <int>::size_type i;  
  
   i = v1.max_size( );     
   cout << "The maximum possible length of the vector is " << i << "." << endl;  
}  
```  
  
##  <a name="a-namevectoroperatorata--vectoroperator"></a><a name="vector__operator_at"></a>  vector::operator[]  
 Devuelve una referencia al elemento vector en una posición especificada.  
  
```  
reference operator[](size_type Pos);

const_reference operator[](size_type Pos) const;
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`Pos`|Posición del elemento vector.|  
  
### <a name="return-value"></a>Valor devuelto  
 Si la posición especificada es mayor o igual que el tamaño del contenedor, el resultado es sin definir.  
  
### <a name="remarks"></a>Comentarios  
 Si el valor devuelto de `operator[]` se asigna a `const_reference`, el objeto vector no se puede modificar. Si el valor devuelto de `operator[]` se asigna a una referencia, el objeto vector se puede modificar.  
  
 Al compilar con [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definido como 1 o 2, se produce un error de tiempo de ejecución si intenta tener acceso a un elemento fuera de los límites del vector.  Para más información, vea [Iteradores activados](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_op_ref.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
  
   v1.push_back( 10 );  
   v1.push_back( 20 );  
  
   int& i = v1[1];  
   cout << "The second integer of v1 is " << i << endl;  
}  
```  
  
##  <a name="a-namevectoroperatoreqa--vectoroperator"></a><a name="vector__operator_eq"></a>  vector::operator=  
 Reemplaza los elementos del vector con una copia de otro vector.  
  
```  
vector& operator=(const vector& right);

vector& operator=(vector&& right);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|` right`|El [vector](../standard-library/vector-class.md) que se copia en el `vector`.|  
  
### <a name="remarks"></a>Comentarios  
 Después de borrar todos los elementos existentes en un `vector`, `operator=` copia o mueve el contenido de ` right` al `vector`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_operator_as.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector<int> v1, v2, v3;  
   vector<int>::iterator iter;  
  
   v1.push_back(10);  
   v1.push_back(20);  
   v1.push_back(30);  
   v1.push_back(40);  
   v1.push_back(50);  
  
   cout << "v1 = " ;  
   for (iter = v1.begin(); iter != v1.end(); iter++)  
      cout << *iter << " ";  
   cout << endl;  
  
   v2 = v1;  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << *iter << " ";  
   cout << endl;  
  
// move v1 into v2  
   v2.clear();  
   v2 = move(v1);  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << *iter << " ";  
   cout << endl;  
}  
```  
  
##  <a name="a-namevectorpointera--vectorpointer"></a><a name="vector__pointer"></a>  vector::pointer  
 Tipo que proporciona un puntero a un elemento en un vector.  
  
```  
typedef typename Allocator::pointer pointer;  
```  
  
### <a name="remarks"></a>Comentarios  
 Se puede usar un tipo **pointer** para modificar el valor de un elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_pointer.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector<int> v;  
   v.push_back( 11 );  
   v.push_back( 22 );  
  
   vector<int>::pointer ptr = &v[0];  
   cout << *ptr << endl;  
   ptr++;  
   cout << *ptr << endl;  
 *ptr = 44;  
   cout << *ptr << endl;  
}  
```  
  
```Output  
11  
22  
44  
```  
  
##  <a name="a-namevectorpopbacka--vectorpopback"></a><a name="vector__pop_back"></a>  vector::pop_back  
 Elimina el elemento situado al final del vector.  
  
```  
void pop_back();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener un ejemplo de código, vea [vector::push_back()](#vector__push_back).  
  
##  <a name="a-namevectorpushbacka--vectorpushback"></a><a name="vector__push_back"></a>  vector::push_back  
 Agrega un elemento al final del vector.  
  
```  
void push_back(const T& Val);

 
void push_back(T&& Val);
```  
  
### <a name="parameters"></a>Parámetros  
 `Val`  
 El valor que se asignará al elemento que se agrega al final del vector.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// compile with: /EHsc /W4  
#include <vector>  
#include <iostream>  
  
using namespace std;  
  
template <typename T> void print_elem(const T& t) {  
    cout << "(" << t << ") ";  
}  
  
template <typename T> void print_collection(const T& t) {  
    cout << "  " << t.size() << " elements: ";  
  
    for (const auto& p : t) {  
        print_elem(p);  
    }  
    cout << endl;  
}  
  
int main()  
{  
    vector<int> v;  
    for (int i = 0; i < 10; ++i) {  
        v.push_back(10 + i);  
    }  
  
    cout << "vector data: " << endl;  
    print_collection(v);  
  
    // pop_back() until it's empty, printing the last element as we go  
    while (v.begin() != v.end()) {   
        cout << "v.back(): "; print_elem(v.back()); cout << endl;  
        v.pop_back();  
    }  
}  
```  
  
##  <a name="a-namevectorrbegina--vectorrbegin"></a><a name="vector__rbegin"></a>  vector::rbegin  
 Devuelve un iterador al primer elemento en un vector inverso.  
  
```  
reverse_iterator rbegin();
const_reverse_iterator rbegin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador inverso de acceso aleatorio que se dirige al primer elemento de un vector inverso o al que fue el último elemento del vector sin invertir.  
  
### <a name="remarks"></a>Comentarios  
 Si el valor devuelto de `rbegin` se asigna a `const_reverse_iterator`, el objeto vector no se puede modificar. Si el valor devuelto de `rbegin` se asigna a `reverse_iterator`, el objeto de vector se puede modificar.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_rbegin.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   vector <int>::iterator v1_Iter;  
   vector <int>::reverse_iterator v1_rIter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
  
   v1_Iter = v1.begin( );  
   cout << "The first element of vector is "  
        << *v1_Iter << "." << endl;  
  
   v1_rIter = v1.rbegin( );  
   cout << "The first element of the reversed vector is "  
        << *v1_rIter << "." << endl;  
}  
```  
  
```Output  
The first element of vector is 1.  
The first element of the reversed vector is 2.  
```  
  
##  <a name="a-namevectorreferencea--vectorreference"></a><a name="vector__reference"></a>  vector::reference  
 Tipo que proporciona una referencia a un elemento almacenado en un vector.  
  
```  
typedef typename Allocator::reference reference;  
```  
  
### <a name="example"></a>Ejemplo  
  Vea en [at](#vector__at) un ejemplo de cómo usar **reference** en la clase de vector.  
  
##  <a name="a-namevectorrenda--vectorrend"></a><a name="vector__rend"></a>  vector::rend  
 Devuelve un iterador que se dirige a la ubicación que sigue al último elemento en un vector invertido.  
  
```  
const_reverse_iterator rend() const;
reverse_iterator rend();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador inverso constante de acceso aleatorio que se dirige a la ubicación siguiente al último elemento de un vector invertido (la ubicación que había precedido al primer elemento del vector sin invertir).  
  
### <a name="remarks"></a>Comentarios  
 `rend` se usa con un vector invertido del mismo modo que [end](#vector__end) se usa con un vector.  
  
 Si el valor devuelto de `rend` se asigna a un `const_reverse_iterator`, el objeto de vector no se puede modificar. Si el valor devuelto de `rend` se asigna a un `reverse_iterator`, el objeto de vector se puede modificar.  
  
 Se puede usar `rend` para comprobar si un iterador invertido ha llegado al final de su vector.  
  
 El valor devuelto por `rend` no se debe desreferenciar.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_rend.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   vector <int>::reverse_iterator v1_rIter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
  
   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )  
      cout << *v1_rIter << endl;  
}  
```  
  
```Output  
2  
1  
```  
  
##  <a name="a-namevectorreservea--vectorreserve"></a><a name="vector__reserve"></a>  vector::reserve  
 Reserva una longitud mínima de almacenamiento para un objeto de vector y asigna espacio si es necesario.  
  
```  
void reserve(size_type count);
```  
  
### <a name="parameters"></a>Parámetros  
 ` count`  
 Longitud mínima de almacenamiento a asignar para el vector.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_reserve.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   //vector <int>::iterator Iter;  
  
   v1.push_back( 1 );  
   cout << "Current capacity of v1 = "   
      << v1.capacity( ) << endl;  
   v1.reserve( 20 );  
   cout << "Current capacity of v1 = "   
      << v1.capacity( ) << endl;  
}  
```  
  
```Output  
Current capacity of v1 = 1  
Current capacity of v1 = 20  
```  
  
##  <a name="a-namevectorresizea--vectorresize"></a><a name="vector__resize"></a>  vector::resize  
 Especifica un nuevo tamaño de un vector.  
  
```  
void resize(size_type Newsize);
void resize(size_type Newsize, Type Val);
```  
  
### <a name="parameters"></a>Parámetros  
 `Newsize`  
 Nuevo tamaño del vector.  
  
 `Val`  
 El valor de inicialización de elementos nuevos añadido al vector si el nuevo tamaño es mayor que el tamaño original. Si el valor se omite, los nuevos objetos utilizan su constructor predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 Si el tamaño del contenedor es menor que el tamaño solicitado, `Newsize`, se agregan elementos al vector hasta que esta alcanza el tamaño solicitado. Si el tamaño del contenedor es mayor que el tamaño solicitado, se eliminan los elementos más cercanos al final del contenedor hasta que este alcanza el tamaño `Newsize`. Si el tamaño actual del contenedor es igual que el tamaño solicitado, no se lleva a cabo ninguna acción.  
  
 [size](#vector__size) refleja el tamaño actual del vector.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vectorsizing.cpp  
// compile with: /EHsc /W4  
// Illustrates vector::reserve, vector::max_size,  
// vector::resize, vector::resize, and vector::capacity.  
//  
// Functions:  
//  
//    vector::max_size - Returns maximum number of elements vector could  
//                       hold.  
//  
//    vector::capacity - Returns number of elements for which memory has  
//                       been allocated.  
//  
//    vector::size - Returns number of elements in the vector.  
//  
//    vector::resize - Reallocates memory for vector, preserves its  
//                     contents if new size is larger than existing size.  
//  
//    vector::reserve - Allocates elements for vector to ensure a minimum  
//                      size, preserving its contents if the new size is  
//                      larger than existing size.  
//  
//    vector::push_back - Appends (inserts) an element to the end of a  
//                        vector, allocating memory for it if necessary.  
//  
//////////////////////////////////////////////////////////////////////  
  
// The debugger cannot handle symbols more than 255 characters long.  
// The C++ Standard Library often creates symbols longer than that.  
// The warning can be disabled:  
//#pragma warning(disable:4786)  
  
#include <iostream>  
#include <vector>  
#include <string>  
  
using namespace std;  
  
template <typename C> void print(const string& s, const C& c) {  
    cout << s;  
  
    for (const auto& e : c) {  
        cout << e << " ";  
    }  
    cout << endl;  
}  
  
void printvstats(const vector<int>& v) {  
    cout << "   the vector's size is: " << v.size() << endl;  
    cout << "   the vector's capacity is: " << v.capacity() << endl;  
    cout << "   the vector's maximum size is: " << v.max_size() << endl;  
}  
  
int main()  
{  
    // declare a vector that begins with 0 elements.  
    vector<int> v;  
  
    // Show statistics about vector.  
    cout << endl << "After declaring an empty vector:" << endl;  
    printvstats(v);  
    print("   the vector's contents: ", v);  
  
    // Add one element to the end of the vector.  
    v.push_back(-1);  
    cout << endl << "After adding an element:" << endl;  
    printvstats(v);  
    print("   the vector's contents: ", v);  
  
    for (int i = 1; i < 10; ++i) {  
        v.push_back(i);  
    }  
    cout << endl << "After adding 10 elements:" << endl;  
    printvstats(v);  
    print("   the vector's contents: ", v);  
  
    v.resize(6);  
    cout << endl << "After resizing to 6 elements without an initialization value:" << endl;  
    printvstats(v);  
    print("   the vector's contents: ", v);  
  
    v.resize(9, 999);  
    cout << endl << "After resizing to 9 elements with an initialization value of 999:" << endl;  
    printvstats(v);  
    print("   the vector's contents: ", v);  
  
    v.resize(12);  
    cout << endl << "After resizing to 12 elements without an initialization value:" << endl;  
    printvstats(v);  
    print("   the vector's contents: ", v);  
  
    // Ensure there's room for at least 1000 elements.  
    v.reserve(1000);  
    cout << endl << "After vector::reserve(1000):" << endl;  
    printvstats(v);  
  
    // Ensure there's room for at least 2000 elements.  
    v.resize(2000);  
    cout << endl << "After vector::resize(2000):" << endl;  
    printvstats(v);  
}  
```  
  
##  <a name="a-namevectorreverseiteratora--vectorreverseiterator"></a><a name="vector__reverse_iterator"></a>  vector::reverse_iterator  
 Tipo que proporciona un iterador de acceso aleatorio que puede leer o modificar cualquier elemento en un vector invertido.  
  
```  
typedef std::reverse_iterator<iterator> reverse_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo `reverse_iterator` se utiliza para procesar una iteración en el vector en orden inverso.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [rbegin](#vector__rbegin).  
  
##  <a name="a-namevectorshrinktofita--vectorshrinktofit"></a><a name="vector__shrink_to_fit"></a>  vector::shrink_to_fit  
 Descarta el exceso de capacidad.  
  
```  
void shrink_to_fit();
```  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_shrink_to_fit.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   //vector <int>::iterator Iter;  
  
   v1.push_back( 1 );  
   cout << "Current capacity of v1 = "   
      << v1.capacity( ) << endl;  
   v1.reserve( 20 );  
   cout << "Current capacity of v1 = "   
      << v1.capacity( ) << endl;  
   v1.shrink_to_fit();  
   cout << "Current capacity of v1 = "   
      << v1.capacity( ) << endl;  
}  
```  
  
```Output  
Current capacity of v1 = 1  
Current capacity of v1 = 20  
Current capacity of v1 = 1  
```  
  
##  <a name="a-namevectorsizea--vectorsize"></a><a name="vector__size"></a>  vector::size  
 Devuelve el número de elementos del vector.  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Longitud actual del vector.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_size.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1;  
   vector <int>::size_type i;  
  
   v1.push_back( 1 );  
   i = v1.size( );  
   cout << "Vector length is " << i << "." << endl;  
  
   v1.push_back( 2 );  
   i = v1.size( );  
   cout << "Vector length is now " << i << "." << endl;  
}  
```  
  
```Output  
Vector length is 1.  
Vector length is now 2.  
```  
  
##  <a name="a-namevectorsizetypea--vectorsizetype"></a><a name="vector__size_type"></a>  vector::size_type  
 Tipo que cuenta el número de elementos de un vector.  
  
```  
typedef typename Allocator::size_type size_type;  
```  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [capacity](#vector__capacity).  
  
##  <a name="a-namevectorswapa--vectorswap"></a><a name="vector__swap"></a>  vector::swap  
 Intercambia los elementos de dos vectores.  
  
```  
void swap(
    vector<Type, Allocator>& right);

friend void swap(
    vector<Type, Allocator>& left,  
    vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 Vector que proporciona los elementos que se van a intercambiar o vector cuyos elementos se van a intercambiar con los del vector ` left`.  
  
 ` left`  
 Vector cuyos elementos se van a intercambiar con los del vector ` right`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_swap.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   vector <int> v1, v2;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
   v1.push_back( 3 );  
  
   v2.push_back( 10 );  
   v2.push_back( 20 );  
  
   cout << "The number of elements in v1 = " << v1.size( ) << endl;  
   cout << "The number of elements in v2 = " << v2.size( ) << endl;  
   cout << endl;  
  
   v1.swap( v2 );  
  
   cout << "The number of elements in v1 = " << v1.size( ) << endl;  
   cout << "The number of elements in v2 = " << v2.size( ) << endl;  
}  
```  
  
```Output  
The number of elements in v1 = 3  
The number of elements in v2 = 2  
  
The number of elements in v1 = 2  
The number of elements in v2 = 3  
```  
  
##  <a name="a-namevectorvaluetypea--vectorvaluetype"></a><a name="vector__value_type"></a>  vector::value_type  
 Tipo que representa el tipo de datos almacenado en un vector.  
  
```  
typedef typename Allocator::value_type value_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 `value_type` es un sinónimo del parámetro de plantilla **Type**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_value_type.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector<int>::value_type AnInt;  
   AnInt = 44;  
   cout << AnInt << endl;  
}  
```  
  
```Output  
44  
```  
  
##  <a name="a-namevectorvectora--vectorvector"></a><a name="vector__vector"></a>  vector::vector  
 Construye un vector de un tamaño determinado o con elementos de un valor determinado o con un asignador específico o como una copia de todo o de parte de algún otro vector.  
  
```  
vector();
explicit vector(const Allocator& Al);
explicit vector(size_type Count);
vector(size_type Count, const Type& Val);
vector(size_type Count, const Type& Val, const Allocator& Al);

vector(const vector& Right);
vector(vector&& Right);
vector(initializer_list<Type> IList, const _Allocator& Al);

template <class InputIterator>  
vector(InputIterator First, InputIterator Last);
template <class InputIterator>  
vector(InputIterator First, InputIterator Last, const Allocator& Al);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`Al`|La clase de asignador que se usa con este objeto. [get_allocator](#vector__get_allocator) devuelve la clase de asignador del objeto.|  
|`Count`|Número de elementos del vector construido.|  
|`Val`|Valor de los elementos del vector construido.|  
|`Right`|Vector del que el vector construido va a ser una copia.|  
|`First`|Posición del primer elemento en el intervalo de elementos que se va a copiar.|  
|`Last`|Posición del primer elemento más allá del intervalo de elementos que se va a copiar.|  
|`IList`|initializer_list que contiene los elementos que se van a copiar.|  
  
### <a name="remarks"></a>Comentarios  
 Todos los constructores almacenan un objeto de asignador ( `Al`) e inicializan el vector.  
  
 Los dos primeros constructores especifican un vector inicial vacío. El segundo especifica explícitamente el tipo de asignador ( `Al`) que se va a usar.  
  
 El tercer constructor especifica una repetición de un número especificado ( `Count`) de elementos del valor predeterminado para la clase `Type`.  
  
 Los constructores cuarto y quinto especifican una repetición de elementos ( `Count`) de valor `Val`.  
  
 El sexto constructor especifica una copia del vector `Right`.  
  
 El séptimo constructor mueve el vector `Right`.  
  
 El octavo constructor utiliza una initializer_list para especificar los elementos.  
  
 Los constructores noveno y décimo copian el intervalo [ `First`, `Last`) de un vector.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_ctor.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    vector <int>::iterator v1_Iter, v2_Iter, v3_Iter, v4_Iter, v5_Iter, v6_Iter;  
  
    // Create an empty vector v0  
    vector <int> v0;  
  
    // Create a vector v1 with 3 elements of default value 0  
    vector <int> v1(3);  
  
    // Create a vector v2 with 5 elements of value 2  
    vector <int> v2(5, 2);  
  
    // Create a vector v3 with 3 elements of value 1 and with the allocator   
    // of vector v2  
    vector <int> v3(3, 1, v2.get_allocator());  
  
    // Create a copy, vector v4, of vector v2  
    vector <int> v4(v2);  
  
    // Create a new temporary vector for demonstrating copying ranges  
    vector <int> v5(5);  
    for (auto i : v5) {  
        v5[i] = i;  
    }  
  
    // Create a vector v6 by copying the range v5[ first,  last)  
    vector <int> v6(v5.begin() + 1, v5.begin() + 3);  
  
    cout << "v1 =";  
    for (auto& v : v1){  
        cout << " " << v;  
    }  
    cout << endl;  
  
    cout << "v2 =";  
    for (auto& v : v2){  
        cout << " " << v;  
    }  
    cout << endl;  
  
    cout << "v3 =";  
    for (auto& v : v3){  
        cout << " " << v;  
    }  
    cout << endl;  
    cout << "v4 =";  
    for (auto& v : v4){  
        cout << " " << v;  
    }  
    cout << endl;  
  
    cout << "v5 =";  
    for (auto& v : v5){  
        cout << " " << v;  
    }  
    cout << endl;  
  
    cout << "v6 =";  
    for (auto& v : v6){  
        cout << " " << v;  
    }  
    cout << endl;  
  
    // Move vector v2 to vector v7  
    vector <int> v7(move(v2));  
    vector <int>::iterator v7_Iter;  
  
    cout << "v7 =";  
    for (auto& v : v7){  
        cout << " " << v;  
    }  
    cout << endl;  
  
    vector<int> v8{ { 1, 2, 3, 4 } };  
    for (auto& v : v8){  
        cout << " " << v ;  
    }  
    cout << endl;  
}  
  
```  
  
```Output  
v1 = 0 0 0v2 = 2 2 2 2 2v3 = 1 1 1v4 = 2 2 2 2 2v5 = 0 1 2 3 4v6 = 1 2v7 = 2 2 2 2 21 2 3 4  
```  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)


