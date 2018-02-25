---
title: multimap (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- map/std::multimap
- map/std::multimap::allocator_type
- map/std::multimap::const_iterator
- map/std::multimap::const_pointer
- map/std::multimap::const_reference
- map/std::multimap::const_reverse_iterator
- map/std::multimap::difference_type
- map/std::multimap::iterator
- map/std::multimap::key_compare
- map/std::multimap::key_type
- map/std::multimap::mapped_type
- map/std::multimap::pointer
- map/std::multimap::reference
- map/std::multimap::reverse_iterator
- map/std::multimap::size_type
- map/std::multimap::value_type
- map/std::multimap::begin
- map/std::multimap::cbegin
- map/std::multimap::cend
- map/std::multimap::clear
- map/std::multimap::count
- map/std::multimap::crbegin
- map/std::multimap::crend
- map/std::multimap::emplace
- map/std::multimap::emplace_hint
- map/std::multimap::empty
- map/std::multimap::end
- map/std::multimap::equal_range
- map/std::multimap::erase
- map/std::multimap::find
- map/std::multimap::get_allocator
- map/std::multimap::insert
- map/std::multimap::key_comp
- map/std::multimap::lower_bound
- map/std::multimap::max_size
- map/std::multimap::rbegin
- map/std::multimap::rend
- map/std::multimap::size
- map/std::multimap::swap
- map/std::multimap::upper_bound
- map/std::multimap::value_comp
dev_langs:
- C++
helpviewer_keywords:
- std::multimap [C++]
- std::multimap [C++], allocator_type
- std::multimap [C++], const_iterator
- std::multimap [C++], const_pointer
- std::multimap [C++], const_reference
- std::multimap [C++], const_reverse_iterator
- std::multimap [C++], difference_type
- std::multimap [C++], iterator
- std::multimap [C++], key_compare
- std::multimap [C++], key_type
- std::multimap [C++], mapped_type
- std::multimap [C++], pointer
- std::multimap [C++], reference
- std::multimap [C++], reverse_iterator
- std::multimap [C++], size_type
- std::multimap [C++], value_type
- std::multimap [C++], begin
- std::multimap [C++], cbegin
- std::multimap [C++], cend
- std::multimap [C++], clear
- std::multimap [C++], count
- std::multimap [C++], crbegin
- std::multimap [C++], crend
- std::multimap [C++], emplace
- std::multimap [C++], emplace_hint
- std::multimap [C++], empty
- std::multimap [C++], end
- std::multimap [C++], equal_range
- std::multimap [C++], erase
- std::multimap [C++], find
- std::multimap [C++], get_allocator
- std::multimap [C++], insert
- std::multimap [C++], key_comp
- std::multimap [C++], lower_bound
- std::multimap [C++], max_size
- std::multimap [C++], rbegin
- std::multimap [C++], rend
- std::multimap [C++], size
- std::multimap [C++], swap
- std::multimap [C++], upper_bound
- std::multimap [C++], value_comp
ms.assetid: 8796ae05-37c4-475a-9e61-75fde9d4a463
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 554ea4bac3e374013a511b75f27158ad897195f7
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="multimap-class"></a>multimap (Clase)
La clase multimap de la Biblioteca estándar de C++ se usa para el almacenamiento y la recuperación de datos de una colección en la que cada elemento es un par que tiene un valor de datos y una clave de ordenación. El valor de la clave no necesita ser único y se utiliza para ordenar los datos automáticamente. El valor de un elemento de una clase multimap se puede cambiar directamente, pero no su valor de clave asociado. En su lugar, se deben eliminar los valores de clave asociados a los antiguos elementos e insertar los nuevos valores de clave asociados a los elementos nuevos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Key,   
    class Type,   
    class Traits=less <Key>,   
    class Allocator=allocator <pair  <const Key, Type>>>  
class multimap;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Key`  
 Tipo de datos de clave que se almacenará en la clase multimap.  
  
 `Type`  
 Tipo de datos de elemento que se almacenará en la clase multimap.  
  
 `Traits`  
 Tipo que proporciona un objeto de función que puede comparar dos valores de elementos como claves de ordenación para determinar su orden relativo en la clase multimap. El predicado binario `less<Key>` es el valor predeterminado.  
  
 En C++14 puede habilitar la búsqueda heterogénea especificando el predicado `std::less<>` o `std::greater<>`, que no tienen ningún parámetro de tipo. Para obtener más información, vea [Búsqueda heterogénea en los contenedores asociativos](../standard-library/stl-containers.md#sequence_containers).  
  
 `Allocator`  
 Tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria de la asignación. Este argumento es opcional y el valor predeterminado es `allocator<pair <const Key, Type> >`.  
  
## <a name="remarks"></a>Comentarios  
 La clase multimap de la Biblioteca estándar de C++ es  
  
-   Un contenedor asociativo de tamaño variable que admite la recuperación eficaz de valores de elemento según un valor de clave asociado.  
  
-   Reversible, porque proporciona iteradores bidireccionales para tener acceso a sus elementos.  
  
-   Ordenada, porque sus elementos se ordenan según los valores de clave dentro del contenedor de acuerdo con una función de comparación especificada.  
  
-   Múltiple, porque sus elementos no necesitan tener claves únicas, de modo que un valor de clave puede tener asociados varios valores de datos de elemento.  
  
-   Un contenedor asociativo de pares, ya que los valores de datos de sus elementos son distintos de sus valores de clave.  
  
-   Una clase de plantilla, porque la funcionalidad que proporciona es genérica y por tanto independiente del tipo específico de datos contenido como elementos o claves. Los tipos de datos que se usarán para los elementos y las claves se especifican como parámetros en la plantilla de clase junto con la función de comparación y el asignador.  
  
 El iterador proporcionado por la clase map es un iterador bidireccional, pero las funciones miembro [insert](#insert) y [multimap](#multimap) de la clase tienen versiones que toman como parámetros de plantilla un iterador de entrada menos seguro, cuyos requisitos de función son más mínimos que los garantizados por la clase de iteradores bidireccionales. Los distintos conceptos de iterador forman una familia relacionada por los refinamientos de su funcionalidad. Cada concepto de iterador tiene su propio conjunto de requisitos y los algoritmos que funcionan con ellos deben limitar sus suposiciones a los requisitos proporcionados por ese tipo de iterador. Se puede suponer que se puede desreferenciar un iterador de entrada para hacer referencia a un objeto y que se puede incrementar hasta el iterador siguiente de la secuencia. Se trata de un conjunto mínimo de funcionalidad, pero es suficiente para poder comunicarse sobre un intervalo de iteradores `[First, Last)` en el contexto de las funciones miembro de la clase.  
  
 En general, la elección del tipo de contenedor se debe tomar según el tipo de búsqueda y de inserción que necesite la aplicación. Los contenedores asociativos están optimizados para las operaciones de búsqueda, inserción y eliminación. Las funciones miembro que admiten estas operaciones explícitamente las realizan de forma eficiente en un tiempo que es proporcional en promedio al logaritmo del número de elementos del contenedor. La inserción de elementos no invalida ningún iterador y al quitar elementos solo se invalidan los iteradores que habían apuntado específicamente a los elementos quitados.  
  
 La clase multimap debe ser el contenedor asociativo preferido cuando la aplicación satisfaga las condiciones que asocian los valores a sus claves. Un modelo para este tipo de estructura es una lista ordenada de palabras clave con valores de cadena asociados que proporcionan por ejemplo definiciones, donde las palabras no siempre están definidas de forma única. Si, por el contrario, las palabras clave se definieran de forma única para que fueran únicas, el contenedor más adecuado sería map. Por otra parte, si solo se almacenara la lista de palabras, el contenedor correcto sería set. Si se permitieran varias repeticiones de las palabras, la estructura de contenedor adecuada sería multiset.  
  
 El mapa múltiple ordena la secuencia que controla llamando a un objeto de función almacenado de tipo [key_compare](#key_compare). Este objeto almacenado es una función de comparación a la que se puede tener acceso mediante una llamada a la función miembro [key_comp](#key_comp). En general, se debe poder comparar si los elementos son menores que otros para poder establecer este orden; de este modo, dados dos elementos cualesquiera, se puede determinar que son equivalentes (en el sentido de que ninguno es menor que el otro) o que uno es menor que el otro. Esto produce una ordenación entre los elementos no equivalentes. En un sentido más técnico, la función de comparación es un predicado binario que induce una ordenación débil estricta en el sentido matemático estándar. Un predicado binario `f(x,y)` es un objeto de función que tiene dos objetos de argumento `x` e `y` y un valor devuelto de true o false. Una ordenación impuesta en un conjunto es una ordenación débil estricta si el predicado binario es irreflexivo, antisimétrico y transitivo, y si la equivalencia es transitiva, donde dos objetos `x` e `y` se definen como equivalentes cuando `f(x,y)` y `f(y,x)` son falsos. Si la condición más fuerte de igualdad entre las claves reemplaza la de equivalencia, la ordenación se convierte en total (en el sentido de que todos los elementos se ordenan entre sí) y las claves coincidentes serán indiscernibles unas de otras.  
  
 En C++14 puede habilitar la búsqueda heterogénea especificando el predicado `std::less<>` o `std::greater<>`, que no tienen ningún parámetro de tipo. Para obtener más información, vea [Búsqueda heterogénea en los contenedores asociativos](../standard-library/stl-containers.md#sequence_containers).  
  
## <a name="members"></a>Miembros  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[multimap](#multimap)|Construye un `multimap` que está vacío o que es una copia de todo o de parte de otro `multimap`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|Tipo que representa la clase `allocator` para el objeto `multimap`.|  
|[const_iterator](#const_iterator)|Tipo que proporciona un iterador bidireccional que puede leer un elemento `const` en `multimap`.|  
|[const_pointer](#const_pointer)|Tipo que proporciona un puntero a un elemento `const` en un `multimap`.|  
|[const_reference](#const_reference)|Tipo que proporciona una referencia a un elemento `const` almacenado en un `multimap` para leer y realizar operaciones `const`.|  
|[const_reverse_iterator](#const_reverse_iterator)|Tipo que proporciona un iterador bidireccional que puede leer cualquier elemento `const` en `multimap`.|  
|[difference_type](#difference_type)|Tipo entero con signo que se puede usar para representar el número de elementos de un `multimap` en un intervalo entre elementos a los que apuntan los iteradores.|  
|[iterator](#iterator)|Tipo que proporciona la diferencia entre dos iteradores que hacen referencia a elementos de la misma clase `multimap`.|  
|[key_compare](#key_compare)|Tipo que proporciona un objeto de función que puede comparar dos claves de ordenación para determinar el orden relativo de dos elementos en el `multimap`.|  
|[key_type](#key_type)|Tipo que describe el objeto de clave de ordenación que constituye cada elemento de `multimap`.|  
|[mapped_type](#mapped_type)|Tipo que representa el tipo de datos almacenados en un `multimap`.|  
|[pointer](#pointer)|Tipo que proporciona un puntero a un elemento `const` en un `multimap`.|  
|[reference](#reference)|Tipo que proporciona una referencia a un elemento almacenado en un `multimap`.|  
|[reverse_iterator](#reverse_iterator)|Tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento de `multimap` invertido.|  
|[size_type](#size_type)|Un tipo entero sin signo que proporciona un puntero a un elemento `const` de una clase `multimap`.|  
|[value_type](#value_type)|Tipo que proporciona un objeto de función que puede comparar dos elementos como claves de ordenación para determinar su orden relativo en el `multimap`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[begin](#begin)|Devuelve un iterador que direcciona el primer elemento del `multimap`.|  
|[cbegin](#cbegin)|Devuelve un iterador constante que direcciona el primer elemento del `multimap`.|  
|[cend](#cend)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de `multimap`.|  
|[clear](#clear)|Borra todos los elementos de un `multimap`.|  
|[count](#count)|Devuelve el número de elementos de un `multimap` cuya clave coincide con una clave especificada por un parámetro.|  
|[crbegin](#crbegin)|Devuelve un iterador constante que direcciona el primer elemento de `multimap` invertido.|  
|[crend](#crend)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de `multimap` invertido.|  
|[emplace](#emplace)|Inserta en un `multimap` un elemento construido en contexto.|  
|[emplace_hint](#emplace_hint)|Inserta un elemento construido en contexto en `multimap`, con una sugerencia de colocación.|  
|[empty](#empty)|Comprueba si un `multimap` está vacío.|  
|[end](#end)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de `multimap`.|  
|[equal_range](#equal_range)|Encuentra el intervalo de elementos donde la clave del elemento coincide con un valor especificado.|  
|[erase](#erase)|Quita un elemento o un intervalo de elementos de una clase `multimap` de las posiciones especificadas o quita los elementos que coinciden con una clave especificada.|  
|[find](#find)|Devuelve un iterador que direcciona la primera ubicación de un elemento de `multimap` que tiene una clave equivalente a una clave especificada.|  
|[get_allocator](#get_allocator)|Devuelve una copia del objeto `allocator` utilizado para construir el `multimap`.|  
|[insert](#insert)|Inserta un elemento o un intervalo de elementos en un `multimap`.|  
|[key_comp](#key_comp)|Recupera una copia del objeto de comparación utilizado para ordenar claves de un `multimap`.|  
|[lower_bound](#lower_bound)|Devuelve un iterador al primer elemento de `multimap` cuyo valor de clave es igual o mayor que el de una clave especificada.|  
|[max_size](#max_size)|Devuelve la longitud máxima del `multimap`.|  
|[rbegin](#rbegin)|Devuelve un iterador que direcciona el primer elemento de `multimap` invertido.|  
|[rend](#rend)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de `multimap` invertido.|  
|[size](#size)|Devuelve el número de elementos de `multimap`.|  
|[swap](#swap)|Intercambia los elementos de dos `multimap`.|  
|[upper_bound](#upper_bound)|Devuelve un iterador al primer elemento de `multimap` con un valor de clave que es mayor que una clave especificada.|  
|[value_comp](#value_comp)|La función miembro devuelve un objeto de función que determina el orden de los elementos de `multimap` mediante la comparación de sus valores de clave.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator=](#op_eq)|Reemplaza los elementos de un `multimap` con una copia de otro `multimap`.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<map>  
  
 **Espacio de nombres:** std  
  
 Los pares (**key**, **value**) se almacenan en multimap como objetos de tipo `pair`. La clase pair requiere el encabezado \<utility>, que \<map> incluye automáticamente.  
  
##  <a name="allocator_type"></a> multimap::allocator_type  
 Un tipo que representa la clase de asignador para el objeto multimap.  
  
```  
typedef Allocator allocator_type;  
```  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [get_allocator](#get_allocator) para obtener un ejemplo que usa `allocator_type`.  
  
##  <a name="begin"></a> multimap::begin  
 Devuelve un iterador que se dirige al primer elemento del mapa múltiple.  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador bidireccional que se dirige al primer elemento del mapa múltiple o a la ubicación siguiente a un mapa múltiple vacío.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_begin.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multimap <int, int> m1;  
  
   multimap <int, int> :: iterator m1_Iter;  
   multimap <int, int> :: const_iterator m1_cIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 0, 0 ) );  
   m1.insert ( Int_Pair ( 1, 1 ) );  
   m1.insert ( Int_Pair ( 2, 4 ) );  
  
   m1_cIter = m1.begin ( );  
   cout << "The first element of m1 is " << m1_cIter -> first << endl;  
  
   m1_Iter = m1.begin ( );  
   m1.erase ( m1_Iter );  
  
   // The following 2 lines would err as the iterator is const  
   // m1_cIter = m1.begin ( );  
   // m1.erase ( m1_cIter );  
  
   m1_cIter = m1.begin( );  
   cout << "First element of m1 is now " << m1_cIter -> first << endl;  
}  
```  
  
```Output  
The first element of m1 is 0  
First element of m1 is now 1  
```  
  
##  <a name="cbegin"></a> multimap::cbegin  
 Devuelve un iterador `const` que direcciona el primer elemento del intervalo.  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador `const` de acceso bidireccional que apunta al primer elemento del intervalo o la ubicación situada más allá del final de un intervalo vacío (para un intervalo vacío, `cbegin() == cend()`).  
  
### <a name="remarks"></a>Comentarios  
 Con el valor devuelto de `cbegin`, los elementos del intervalo no se pueden modificar.  
  
 Se puede usar esta función miembro en lugar de la función miembro `begin()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo, se considera que `Container` es un contenedor modificable (distinto de `const`) de cualquier naturaleza que admite `begin()` y `cbegin()`.  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="cend"></a> multimap::cend  
 Devuelve un iterador `const` que direcciona la ubicación situada más allá del último elemento de un intervalo.  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador `const` de acceso bidireccional que apunta justo después del final del intervalo.  
  
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
  
##  <a name="clear"></a> multimap::clear  
 Borra todos los elementos de una asignación múltiple.  
  
```  
void clear();
```  
  
### <a name="example"></a>Ejemplo  
  En el siguiente ejemplo se muestra el uso de la función miembro multimap::clear.  
  
```  
// multimap_clear.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap<int, int> m1;  
   multimap<int, int>::size_type i;  
   typedef pair<int, int> Int_Pair;  
  
   m1.insert(Int_Pair(1, 1));  
   m1.insert(Int_Pair(2, 4));  
  
   i = m1.size();  
   cout << "The size of the multimap is initially "  
        << i << "." << endl;  
  
   m1.clear();  
   i = m1.size();  
   cout << "The size of the multimap after clearing is "  
        << i << "." << endl;  
}  
```  
  
```Output  
The size of the multimap is initially 2.  
The size of the multimap after clearing is 0.  
```  
  
##  <a name="const_iterator"></a> multimap::const_iterator  
 Un tipo que proporciona un iterador bidireccional que puede leer un elemento **const** del mapa múltiple.  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo `const_iterator` no se puede utilizar para modificar el valor de un elemento.  
  
 El `const_iterator` definido por puntos multimap a objetos de [value_type](#value_type), que son de tipo `pair` * \< * **clave const**, **Tipo *** >*. El valor de la clave está disponible mediante el primer miembro del par y el valor del elemento asignado está disponible mediante el segundo miembro del par.  
  
 A fin de desreferenciar una `const_iterator` `cIter` apunta a un elemento de una asignación múltiple, utilice la  **->**  operador.  
  
 Para tener acceso al valor de clave del elemento, use `cIter` -> **first**, que es equivalente a (\* `cIter`). **first**. Para tener acceso al valor de la referencia asignada del elemento, use `cIter` -> **second**, que es equivalente a (\* `cIter`). **second**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [begin](#begin) para obtener un ejemplo que usa `const_iterator`.  
  
##  <a name="const_pointer"></a> multimap::const_pointer  
 Un tipo que proporciona un puntero a un elemento **const** en un mapa múltiple.  
  
```  
typedef typename allocator_type::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo `const_pointer` no se puede utilizar para modificar el valor de un elemento.  
  
 En la mayoría de los casos, se debe usar un elemento [iterator](#iterator) para obtener acceso a los elementos de un objeto multimap.  
  
##  <a name="const_reference"></a> multimap::const_reference  
 Un tipo que proporciona una referencia a un elemento **const** almacenado en un mapa múltiple para leer operaciones **const** y realizarlas.  
  
```  
typedef typename allocator_type::const_reference const_reference;  
```  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_const_ref.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap <int, int> m1;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the key of the first element  
   const int &Ref1 = ( m1.begin( ) -> first );  
  
   // The following line would cause an error because the   
   // non-const_reference cannot be used to access the key  
   // int &Ref1 = ( m1.begin( ) -> first );  
  
   cout << "The key of the first element in the multimap is "  
        << Ref1 << "." << endl;  
  
   // Declare and initialize a reference &Ref2   
   // to the data value of the first element  
   int &Ref2 = ( m1.begin( ) -> second );  
  
   cout << "The data value of the first element in the multimap is "  
        << Ref2 << "." << endl;  
}  
```  
  
```Output  
The key of the first element in the multimap is 1.  
The data value of the first element in the multimap is 10.  
```  
  
##  <a name="const_reverse_iterator"></a> multimap::const_reverse_iterator  
 Un tipo que proporciona un iterador bidireccional que puede leer cualquier elemento **const** del mapa múltiple.  
  
```  
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo `const_reverse_iterator` no puede modificar el valor de un elemento y se usa para iterar en el mapa múltiple en orden inverso.  
  
 El `const_reverse_iterator` definido por puntos multimap a objetos de [value_type](#value_type), que son de tipo `pair` * \< * **clave const**, **Tipo *** >*. El valor de la clave está disponible mediante el primer miembro del par y el valor del elemento asignado está disponible mediante el segundo miembro del par.  
  
 A fin de desreferenciar una `const_reverse_iterator` `crIter` apunta a un elemento de una asignación múltiple, utilice la  **->**  operador.  
  
 Para tener acceso al valor de clave del elemento, use `crIter` -> **first**, que es equivalente a (\* `crIter`). **first**. Para tener acceso al valor de la referencia asignada del elemento, use `crIter` -> **second**, que es equivalente a (\* `crIter`). **first**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [rend](#rend) para obtener un ejemplo de cómo declarar y usar `const_reverse_iterator`.  
  
##  <a name="count"></a> multimap::count  
 Devuelve el número de elementos de una asignación múltiple cuya clave coincide con una clave especificada por un parámetro.  
  
```  
size_type count(const Key& key) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 La clave de los elementos de la asignación múltiple que deben coincidir.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos cuyos criterios de ordenación coinciden con la clave del parámetro; 0 si la asignación múltiple no contiene ningún elemento con la misma clave.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve el número de elementos del intervalo  
  
 [ `lower_bound` (_ *Key* ), `upper_bound` (\_ *Key* ) )  
  
 que tienen un valor de clave `key`.  
  
### <a name="example"></a>Ejemplo  
  En el ejemplo siguiente se muestra el uso de la función de miembro multimap::count.  
  
```  
// multimap_count.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    multimap<int, int> m1;  
    multimap<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    m1.insert(Int_Pair(1, 1));  
    m1.insert(Int_Pair(2, 1));  
    m1.insert(Int_Pair(1, 4));  
    m1.insert(Int_Pair(2, 1));  
  
    // Elements do not need to have unique keys in multimap,  
    // so duplicates are allowed and counted  
    i = m1.count(1);  
    cout << "The number of elements in m1 with a sort key of 1 is: "  
         << i << "." << endl;  
  
    i = m1.count(2);  
    cout << "The number of elements in m1 with a sort key of 2 is: "  
         << i << "." << endl;  
  
    i = m1.count(3);  
    cout << "The number of elements in m1 with a sort key of 3 is: "  
         << i << "." << endl;  
}  
```  
  
```Output  
The number of elements in m1 with a sort key of 1 is: 2.  
The number of elements in m1 with a sort key of 2 is: 2.  
The number of elements in m1 with a sort key of 3 is: 0.  
```  
  
##  <a name="crbegin"></a> multimap::crbegin  
 Devuelve un iterador const que se dirige al primer elemento de un mapa múltiple invertido.  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador constante bidireccional inverso que se dirige al primer elemento de un [mapa múltiple](../standard-library/multimap-class.md) invertido o que se dirige a lo que ha sido el último elemento de `multimap` sin invertir.  
  
### <a name="remarks"></a>Comentarios  
 `crbegin` se usa con un `multimap` invertido igual que [begin](#begin) se usa con un `multimap`.  
  
 Con el valor devuelto de `crbegin`, el objeto `multimap` no se puede modificar.  
  
 `crbegin` puede usarse para iterar `multimap` hacia atrás.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_crbegin.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap <int, int> m1;  
  
   multimap <int, int> :: const_reverse_iterator m1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
  
   m1_crIter = m1.crbegin( );  
   cout << "The first element of the reversed multimap m1 is "  
        << m1_crIter -> first << "." << endl;  
}  
```  
  
```Output  
The first element of the reversed multimap m1 is 3.  
```  
  
##  <a name="crend"></a> multimap::crend  
 Devuelve un iterador const que se dirige a la ubicación que sigue al último elemento de un mapa múltiple invertido.  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador constante bidireccional inverso que se dirige a la ubicación siguiente al último elemento de un [mapa múltiple](../standard-library/multimap-class.md) invertido (la ubicación que había precedido al primer elemento del `multimap` sin invertir).  
  
### <a name="remarks"></a>Comentarios  
 `crend` se usa con un`multimap` invertido igual que [multimap::end](#end) se usa con un `multimap`.  
  
 Con el valor devuelto de `crend`, el objeto `multimap` no se puede modificar.  
  
 Se puede utilizar `crend` para comprobar si un iterador inverso llegó al final de su `multimap`.  
  
 El valor devuelto por `crend` no se debe desreferenciar.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_crend.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap <int, int> m1;  
  
   multimap <int, int> :: const_reverse_iterator m1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
  
   m1_crIter = m1.crend( );  
   m1_crIter--;  
   cout << "The last element of the reversed multimap m1 is "  
        << m1_crIter -> first << "." << endl;  
}  
```  
  
```Output  
The last element of the reversed multimap m1 is 1.  
```  
  
##  <a name="difference_type"></a> multimap::difference_type  
 Un tipo entero con signo que se puede usar para representar el número de elementos de un mapa múltiple en un intervalo entre elementos a los que apuntan los iteradores.  
  
```  
typedef typename allocator_type::difference_type difference_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El `difference_type` es el tipo devuelto al restar o incrementar los iteradores del contenedor. El `difference_type` normalmente se utiliza para representar el número de elementos del intervalo [*primer*, *última*) entre los iteradores `first` y `last`, incluye el elemento al que apunta a por `first` y el intervalo de elementos hacia arriba, pero sin incluir, el elemento al que señala `last`.  
  
 Tenga en cuenta que, aunque `difference_type` está disponible para todos los iteradores que cumplen los requisitos de un iterador de entrada, incluida la clase de iteradores bidireccionales admitida por los contenedores reversibles como set, solo los iteradores de acceso aleatorio proporcionados por un contenedor de acceso aleatorio, como vector, admiten la resta entre iteradores.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <map>  
#include <algorithm>  
  
int main( )  
{  
   using namespace std;  
   multimap <int, int> m1;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 3, 20 ) );  
  
   // The following will insert as multimap keys are not unique  
   m1.insert ( Int_Pair ( 2, 30 ) );     
  
   multimap <int, int>::iterator m1_Iter, m1_bIter, m1_eIter;     
   m1_bIter = m1.begin( );  
   m1_eIter = m1.end( );  
  
   // Count the number of elements in a multimap  
   multimap <int, int>::difference_type  df_count = 0;  
   m1_Iter = m1.begin( );  
   while ( m1_Iter != m1_eIter )  
   {  
      df_count++;  
      m1_Iter++;  
   }  
  
   cout << "The number of elements in the multimap m1 is: "   
        << df_count << "." << endl;  
}  
```  
  
```Output  
The number of elements in the multimap m1 is: 4.  
```  
  
##  <a name="emplace"></a> multimap::emplace  
 Inserta un elemento construido en contexto (no se realiza ninguna operación de copia o de movimiento).  
  
```  
template <class... Args>  
iterator emplace(Args&&... args);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`args`|Argumentos reenviados para construir un elemento que se va a insertar en la asignación múltiple.|  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador al elemento recién insertado.  
  
### <a name="remarks"></a>Comentarios  
 Esta función no invalida ninguna referencia a elementos contenedores, pero puede invalidar todos los iteradores al contenedor.  
  
 Si se produce una excepción durante la inserción, el contenedor permanece inalterado y la excepción se vuelve a iniciar.  
  
 El [value_type](../standard-library/map-class.md#value_type) de un elemento es un par, de modo que el valor de un elemento será un par ordenado en el que el primer componente es igual que el valor de clave y el segundo componente es igual que el valor de datos del elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_emplace.cpp  
// compile with: /EHsc  
#include <map>  
#include <string>  
#include <iostream>  
  
using namespace std;  
  
template <typename M> void print(const M& m) {  
    cout << m.size() << " elements: " << endl;  
  
    for (const auto& p : m) {  
        cout << "(" << p.first <<  "," << p.second << ") ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    multimap<string, string> m1;  
  
    m1.emplace("Anna", "Accounting");  
    m1.emplace("Bob", "Accounting");  
    m1.emplace("Carmine", "Engineering");  
  
    cout << "multimap modified, now contains ";  
    print(m1);  
    cout << endl;  
  
    m1.emplace("Bob", "Engineering");  
  
    cout << "multimap modified, now contains ";  
    print(m1);  
    cout << endl;  
}  
  
```  
  
##  <a name="emplace_hint"></a> multimap::emplace_hint  
 Inserta un elemento construido en contexto (no se realiza ninguna operación de copia o de movimiento), con una sugerencia de colocación.  
  
```  
template <class... Args>  
iterator emplace_hint(
    const_iterator where,  
    Args&&... args);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`args`|Argumentos reenviados para construir un elemento que se va a insertar en la asignación múltiple.|  
|`where`|Lugar donde se va a iniciar la búsqueda del punto de inserción correcto. (Si ese punto precede inmediatamente a `where`, la inserción se puede realizar en tiempo constante amortizado en lugar de en tiempo logarítmico).|  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador al elemento recién insertado.  
  
### <a name="remarks"></a>Comentarios  
 Esta función no invalida ninguna referencia a elementos contenedores, pero puede invalidar todos los iteradores al contenedor.  
  
 Durante el emplazamiento, si se produce una excepción, el estado del contenedor no se modifica.  
  
 El [value_type](../standard-library/map-class.md#value_type) de un elemento es un par, de modo que el valor de un elemento será un par ordenado en el que el primer componente es igual que el valor de clave y el segundo componente es igual que el valor de datos del elemento.  
  
 Para obtener un ejemplo de código, vea [map::emplace_hint](../standard-library/map-class.md#emplace_hint).  
  
##  <a name="empty"></a> multimap::empty  
 Prueba si un mapa múltiple está vacío.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el mapa múltiple está vacío; **False** si el mapa múltiple no está vacío.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_empty.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap <int, int> m1, m2;  
  
   typedef pair <int, int> Int_Pair;  
   m1.insert ( Int_Pair ( 1, 1 ) );  
  
   if ( m1.empty( ) )  
      cout << "The multimap m1 is empty." << endl;  
   else  
      cout << "The multimap m1 is not empty." << endl;  
  
   if ( m2.empty( ) )  
      cout << "The multimap m2 is empty." << endl;  
   else  
      cout << "The multimap m2 is not empty." << endl;  
}  
```  
  
```Output  
The multimap m1 is not empty.  
The multimap m2 is empty.  
```  
  
##  <a name="end"></a> multimap::end  
 Devuelve el iterador más allá del final.  
  
```  
const_iterator end() const;

 
 
iterator end();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El iterador siguiente al final. Si la asignación múltiple está vacía, `multimap::end() == multimap::begin()`.  
  
### <a name="remarks"></a>Comentarios  
 **end** se usa para probar si un iterador ha sobrepasado el final de su mapa múltiple.  
  
 El valor devuelto por **end** no se debe desreferenciar.  
  
 Para ver un ejemplo de código, vea [multimap::find](#find).  
  
##  <a name="equal_range"></a> multimap::equal_range  
 Encuentra el intervalo de elementos donde la clave del elemento coincide con un valor especificado.  
  
```  
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 La clave de argumento que se comparará con la clave de ordenación de un elemento del mapa múltiple que se está buscando.  
  
### <a name="return-value"></a>Valor devuelto  
 Un par de iteradores donde el primero es el elemento [lower_bound](#lower_bound) de la clave y el segundo es el elemento [upper_bound](#upper_bound) de la clave.  
  
 Para tener acceso al primer iterador de un par `pr` devuelto por la función miembro, use `pr`. **first** y para desreferenciar el iterador de límite inferior, use \*( `pr`. **first**). Para tener acceso al segundo iterador de un par `pr` devuelto por la función miembro, use `pr`. **second** y para desreferenciar el iterador de límite superior, use \*( `pr`. **second**).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_equal_range.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   typedef multimap <int, int, less<int> > IntMMap;  
   IntMMap m1;  
   multimap <int, int> :: const_iterator m1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
  
   pair <IntMMap::const_iterator, IntMMap::const_iterator> p1, p2;  
   p1 = m1.equal_range( 2 );  
  
   cout << "The lower bound of the element with "  
        << "a key of 2 in the multimap m1 is: "  
        << p1.first -> second << "." << endl;  
  
   cout << "The upper bound of the element with "  
        << "a key of 2 in the multimap m1 is: "  
        << p1.second -> second << "." << endl;  
  
   // Compare the upper_bound called directly   
   m1_RcIter = m1.upper_bound( 2 );  
  
   cout << "A direct call of upper_bound( 2 ) gives "  
        << m1_RcIter -> second << "," << endl  
        << " matching the 2nd element of the pair"  
        << " returned by equal_range( 2 )." << endl;  
  
   p2 = m1.equal_range( 4 );  
  
   // If no match is found for the key,  
   // both elements of the pair return end( )  
   if ( ( p2.first == m1.end( ) ) && ( p2.second == m1.end( ) ) )  
      cout << "The multimap m1 doesn't have an element "  
           << "with a key less than 4." << endl;  
   else  
      cout << "The element of multimap m1 with a key >= 40 is: "  
           << p1.first -> first << "." << endl;  
}  
```  
  
```Output  
The lower bound of the element with a key of 2 in the multimap m1 is: 20.  
The upper bound of the element with a key of 2 in the multimap m1 is: 30.  
A direct call of upper_bound( 2 ) gives 30,  
 matching the 2nd element of the pair returned by equal_range( 2 ).  
The multimap m1 doesn't have an element with a key less than 4.  
```  
  
##  <a name="erase"></a> multimap::erase  
 Quita un elemento o un intervalo de elementos de un multimap de las posiciones especificadas o quita los elementos que coinciden con una clave especificada.  
  
```  
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,  
    const_iterator Last);

size_type erase(
    const key_type& Key);
```  
  
### <a name="parameters"></a>Parámetros  
 `Where`  
 Posición del elemento que se va a quitar.  
  
 `First`  
 Posición del primer elemento que se va a quitar.  
  
 `Last`  
 Posición situada más allá del último elemento que se va a quitar.  
  
 `Key`  
 Clave de los elementos que se van a quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 Para las dos primeras funciones miembro, iterador bidireccional que designa el primer elemento que permanece más allá de los elementos quitados, o un elemento que es el final de la asignación si no existe ese elemento.  
  
 Para la tercera función miembro, devuelve el número de elementos que se han quitado del multimap.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener un ejemplo de código, vea [map::erase](../standard-library/map-class.md#erase).  
  
##  <a name="find"></a> multimap::find  
 Devuelve un iterador que hace referencia a la primera ubicación de un elemento de una asignación múltiple que tiene una clave equivalente a una clave especificada.  
  
```  
iterator find(const Key& key);

 
const_iterator find(const Key& key) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 El valor de la clave con el que debe coincidir el criterio de ordenación de un elemento de la asignación múltiple en la que se buscará.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que hace referencia a la ubicación de un elemento con una clave especificada, o la ubicación siguiente al último elemento del mapa múltiple (`multimap::end()`) si no se encuentra ninguna coincidencia con la clave.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve un iterador que hace referencia a un elemento de la asignación múltiple cuyo criterio de ordenación es equivalente a la clave de argumento de un predicado binario que induce a una ordenación basada en una relación de comparabilidad de menor que.  
  
 Si el valor devuelto de **find** se asigna a un **const_iterator**, el objeto de mapa múltiple no se puede modificar. Si el valor devuelto de **find** se asigna a un elemento **iterator**, el objeto de mapa múltiple se puede modificar.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// compile with: /EHsc /W4 /MTd  
#include <map>  
#include <iostream>  
#include <vector>  
#include <string>  
#include <utility>  // make_pair()  
  
using namespace std;  
  
template <typename A, typename B> void print_elem(const pair<A, B>& p) {  
    cout << "(" << p.first << ", " << p.second << ") ";  
}  
  
template <typename T> void print_collection(const T& t) {  
    cout << t.size() << " elements: ";  
  
    for (const auto& p : t) {  
        print_elem(p);  
    }  
    cout << endl;  
}  
  
template <typename C, class T> void findit(const C& c, T val) {  
    cout << "Trying find() on value " << val << endl;  
    auto result = c.find(val);  
    if (result != c.end()) {  
        cout << "Element found: "; print_elem(*result); cout << endl;  
    } else {  
        cout << "Element not found." << endl;  
    }  
}  
  
int main()  
{  
    multimap<int, string> m1({ { 40, "Zr" }, { 45, "Rh" } });  
    cout << "The starting multimap m1 is (key, value):" << endl;  
    print_collection(m1);  
  
    vector<pair<int, string>> v;  
    v.push_back(make_pair(43, "Tc"));  
    v.push_back(make_pair(41, "Nb"));  
    v.push_back(make_pair(46, "Pd"));  
    v.push_back(make_pair(42, "Mo"));  
    v.push_back(make_pair(44, "Ru"));  
    v.push_back(make_pair(44, "Ru")); // attempt a duplicate  
  
    cout << "Inserting the following vector data into m1:" << endl;  
    print_collection(v);  
  
    m1.insert(v.begin(), v.end());  
  
    cout << "The modified multimap m1 is (key, value):" << endl;  
    print_collection(m1);  
    cout << endl;  
    findit(m1, 45);  
    findit(m1, 6);  
}  
  
```  
  
##  <a name="get_allocator"></a> multimap::get_allocator  
 Devuelve una copia del objeto de asignador usado para construir el mapa múltiple.  
  
```  
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El asignador que ha usado el mapa múltiple.  
  
### <a name="remarks"></a>Comentarios  
 Los asignadores de la clase multimap especifican cómo la clase administra el almacenamiento. Los asignadores predeterminados proporcionados con las clases contenedoras de la biblioteca estándar de C++ son suficientes para la mayoría de las necesidades de programación. La escritura y el uso de sus propias clases de asignador son temas avanzados de C++.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_get_allocator.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap <int, int>::allocator_type m1_Alloc;  
   multimap <int, int>::allocator_type m2_Alloc;  
   multimap <int, double>::allocator_type m3_Alloc;  
   multimap <int, int>::allocator_type m4_Alloc;  
  
   // The following lines declare objects  
   // that use the default allocator.  
   multimap <int, int> m1;  
   multimap <int, int, allocator<int> > m2;  
   multimap <int, double, allocator<double> > m3;  
  
   m1_Alloc = m1.get_allocator( );  
   m2_Alloc = m2.get_allocator( );  
   m3_Alloc = m3.get_allocator( );  
  
   cout << "The number of integers that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << m2.max_size( ) << ".\n" << endl;  
  
   cout << "The number of doubles that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << m3.max_size( ) <<  ".\n" << endl;  
  
   // The following line creates a multimap m4  
   // with the allocator of multimap m1.  
   map <int, int> m4( less<int>( ), m1_Alloc );  
  
   m4_Alloc = m4.get_allocator( );  
  
   // Two allocators are interchangeable if  
   // storage allocated from each can be  
   // deallocated via the other  
   if( m1_Alloc == m4_Alloc )  
   {  
      cout << "The allocators are interchangeable."  
           << endl;  
   }  
   else     
   {  
      cout << "The allocators are not interchangeable."  
           << endl;  
   }  
}  
```  
  
##  <a name="insert"></a> multimap::insert  
 Inserta un elemento o un rango de elementos en una asignación múltiple.  
  
```  
// (1) single element  
pair<iterator, bool> insert(
    const value_type& Val);

 
// (2) single element, perfect forwarded  
template <class ValTy>  
pair<iterator, bool>  
insert(
    ValTy&& Val);

 
// (3) single element with hint  
iterator insert(
    const_iterator Where,  
    const value_type& Val);

 
// (4) single element, perfect forwarded, with hint  
template <class ValTy>  
iterator insert(
    const_iterator Where,  
    ValTy&& Val);

 
// (5) range   
template <class InputIterator>   
void insert(
    InputIterator First,  
    InputIterator Last);

 
// (6) initializer list  
void insert(
    initializer_list<value_type>  
IList);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`Val`|Valor de un elemento que se va a insertar en la asignación múltiple.|  
|`Where`|Lugar donde se va a iniciar la búsqueda del punto de inserción correcto. (Si ese punto precede inmediatamente a `Where`, la inserción se puede realizar en tiempo constante amortizado en lugar de en tiempo logarítmico).|  
|`ValTy`|Parámetro de plantilla que especifica el tipo de argumento que el mapa puede usar para crear un elemento de [value_type](../standard-library/map-class.md#value_type), y realiza un reenvío directo de `Val` como argumento.|  
|`First`|Posición del primer elemento que se va a copiar.|  
|`Last`|Posición situada más allá del último elemento que se va a copiar.|  
|`InputIterator`|Argumento de la función de plantilla que cumple los requisitos de un [iterador de entrada](../standard-library/input-iterator-tag-struct.md) que apunta a elementos de un tipo que se puede usar para crear objetos [value_type](../standard-library/map-class.md#value_type).|  
|`IList`|El elemento [initializer_list](../standard-library/initializer-list.md) del que se van a copiar los elementos.|  
  
### <a name="return-value"></a>Valor devuelto  
 Las funciones miembro de inserción de un solo elemento, (1) y (2), devuelven un iterador a la posición donde se insertó el nuevo elemento en la asignación múltiple.  
  
 Las funciones miembro de inserción de un solo elemento con sugerencia, (3) y (4), devuelven un iterador que apunta a la posición donde se insertó el nuevo elemento en el multimap.  
  
### <a name="remarks"></a>Comentarios  
 Esta función no invalida ningún puntero ni ninguna referencia, pero puede invalidar todos los iteradores al contenedor.  
  
 Durante la inserción de un solo elemento, si se produce una excepción, no se modifica el estado del contenedor. Durante la inserción de varios elementos, si se produce una excepción, el contenedor se deja en un estado sin especificar pero válido.  
  
 El objeto [value_type](../standard-library/map-class.md#value_type) de un contenedor es una definición de tipo que pertenece al contenedor y, para map, `multimap<K, V>::value_type` es `pair<const K, V>`. El valor de un elemento es un par ordenado en el que el primer componente es igual al valor de clave y el segundo componente es igual al valor de datos del elemento.  
  
 La función miembro de intervalo (5) inserta la secuencia de valores de elemento en un multimap que corresponde a cada elemento direccionado por un iterador en el intervalo `[First, Last)`; por tanto, `Last` no se inserta. La función miembro de contenedor `end()` hace referencia a la posición situada justo después del último elemento del contenedor; por ejemplo, la instrucción `m.insert(v.begin(), v.end());` inserta todos los elementos de `v` en `m`.  
  
 La función miembro de lista de inicializadores (6) usa [initializer_list](../standard-library/initializer-list.md) para copiar los elementos al mapa.  
  
 Para la inserción de un elemento construido en contexto (es decir, no se realiza ninguna operación de copia o movimiento), vea [multimap::emplace](#emplace) y [multimap::emplace_hint](#emplace_hint).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_insert.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
#include <string>  
#include <vector>  
#include <utility>  // make_pair()  
  
using namespace std;  
  
template <typename M> void print(const M& m) {  
    cout << m.size() << " elements: ";  
  
    for (const auto& p : m) {  
        cout << "(" << p.first << ", " << p.second << ") ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
  
    // insert single values   
    multimap<int, int> m1;  
    // call insert(const value_type&) version  
    m1.insert({ 1, 10 });  
    // call insert(ValTy&&) version   
    m1.insert(make_pair(2, 20));  
  
    cout << "The original key and mapped values of m1 are:" << endl;  
    print(m1);  
  
    // intentionally attempt a duplicate, single element  
    m1.insert(make_pair(1, 111));  
  
    cout << "The modified key and mapped values of m1 are:" << endl;  
    print(m1);  
  
    // single element, with hint  
    m1.insert(m1.end(), make_pair(3, 30));  
    cout << "The modified key and mapped values of m1 are:" << endl;  
    print(m1);  
    cout << endl;  
  
    // The templatized version inserting a jumbled range  
    multimap<int, int> m2;  
    vector<pair<int, int>> v;  
    v.push_back(make_pair(43, 294));  
    v.push_back(make_pair(41, 262));  
    v.push_back(make_pair(45, 330));  
    v.push_back(make_pair(42, 277));  
    v.push_back(make_pair(44, 311));  
  
    cout << "Inserting the following vector data into m2:" << endl;  
    print(v);  
  
    m2.insert(v.begin(), v.end());  
  
    cout << "The modified key and mapped values of m2 are:" << endl;  
    print(m2);  
    cout << endl;  
  
    // The templatized versions move-constructing elements  
    multimap<int, string>  m3;  
    pair<int, string> ip1(475, "blue"), ip2(510, "green");  
  
    // single element  
    m3.insert(move(ip1));  
    cout << "After the first move insertion, m3 contains:" << endl;  
    print(m3);  
  
    // single element with hint  
    m3.insert(m3.end(), move(ip2));  
    cout << "After the second move insertion, m3 contains:" << endl;  
    print(m3);  
    cout << endl;  
  
    multimap<int, int> m4;  
    // Insert the elements from an initializer_list  
    m4.insert({ { 4, 44 }, { 2, 22 }, { 3, 33 }, { 1, 11 }, { 5, 55 } });  
    cout << "After initializer_list insertion, m4 contains:" << endl;  
    print(m4);  
    cout << endl;  
}  
  
```  
  
##  <a name="iterator"></a> multimap::iterator  
 Un tipo que proporciona un iterador bidireccional que puede leer o modificar cualquier elemento de un mapa múltiple.  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El **iterador** definido por puntos multimap a objetos de [value_type](#value_type), que son de tipo `pair` * \< * **clave const**, **Tipo *** >*. El valor de la clave está disponible mediante el primer miembro del par y el valor del elemento asignado está disponible mediante el segundo miembro del par.  
  
 Para desreferenciar un elemento **iterator**`Iter` que señala a un elemento de un mapa múltiple, use el operador **->**.  
  
 Para tener acceso al valor de clave del elemento, use `Iter` -> **first**, que es equivalente a (\* `Iter`). **first**. Para tener acceso al valor de la referencia asignada del elemento, use `Iter` -> **second**, que es equivalente a (\* `Iter`). **second**.  
  
 Se puede usar un tipo **iterator** para modificar el valor de un elemento.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [begin](#begin) para obtener un ejemplo de cómo declarar y usar **iterator**.  
  
##  <a name="key_comp"></a> multimap::key_comp  
 Recupera una copia del objeto de comparación que se ha usado para ordenar claves de un mapa múltiple.  
  
```  
key_compare key_comp() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el objeto de función que usa un mapa múltiple para ordenar sus elementos.  
  
### <a name="remarks"></a>Comentarios  
 El objeto almacenado define la función miembro  
  
 **bool operator**( **const Key&** *x*, **const Key&** *y*);  
  
 que devuelve True si *x* precede estrictamente a *y* en el criterio de ordenación.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_key_comp.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   multimap <int, int, less<int> > m1;  
   multimap <int, int, less<int> >::key_compare kc1 = m1.key_comp( ) ;  
   bool result1 = kc1( 2, 3 ) ;  
   if( result1 == true )     
   {  
      cout << "kc1( 2,3 ) returns value of true, "  
           << "where kc1 is the function object of m1."  
           << endl;  
   }  
   else     
   {  
      cout << "kc1( 2,3 ) returns value of false "  
           << "where kc1 is the function object of m1."  
           << endl;  
   }  
  
   multimap <int, int, greater<int> > m2;  
   multimap <int, int, greater<int> >::key_compare kc2 = m2.key_comp( );  
   bool result2 = kc2( 2, 3 ) ;  
   if( result2 == true )     
   {  
      cout << "kc2( 2,3 ) returns value of true, "  
           << "where kc2 is the function object of m2."  
           << endl;  
   }  
   else     
   {  
      cout << "kc2( 2,3 ) returns value of false, "  
           << "where kc2 is the function object of m2."  
           << endl;  
   }  
}  
```  
  
```Output  
kc1( 2,3 ) returns value of true, where kc1 is the function object of m1.  
kc2( 2,3 ) returns value of false, where kc2 is the function object of m2.  
```  
  
##  <a name="key_compare"></a> multimap::key_compare  
 Un tipo que proporciona un objeto de función que puede comparar dos criterios de ordenación para determinar el orden relativo de dos elementos en el mapa múltiple.  
  
```  
typedef Traits key_compare;  
```  
  
### <a name="remarks"></a>Comentarios  
 **key_compare** es un sinónimo del parámetro de plantilla `Traits`.  
  
 Para obtener más información sobre `Traits`, vea el tema [multimap (Clase)](../standard-library/multimap-class.md).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [key_comp](#key_comp) para obtener un ejemplo de cómo declarar y usar `key_compare`.  
  
##  <a name="key_type"></a> multimap::key_type  
 Tipo que describe el objeto de clave de ordenación que constituye cada elemento del mapa múltiple.  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 **key_type** es un sinónimo del parámetro de plantilla `Key`.  
  
 Para obtener más información sobre `Key`, vea la sección Comentarios del tema [multimap (Clase)](../standard-library/multimap-class.md).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [value_type](#value_type) para obtener un ejemplo de cómo declarar y usar `key_type`.  
  
##  <a name="lower_bound"></a> multimap::lower_bound  
 Devuelve un iterador al primer elemento de un mapa múltiple cuyo valor de clave es igual o mayor que el de una clave especificada.  
  
```  
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 La clave de argumento que se comparará con la clave de ordenación de un elemento del mapa múltiple que se está buscando.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador o `const_iterator` que se dirige a la ubicación de un elemento en un mapa múltiple que tiene una clave igual o mayor que la clave de argumento o que se dirige a la ubicación siguiente al último elemento del mapa múltiple si no se encuentra ninguna coincidencia con la clave.  
  
 Si el valor devuelto de `lower_bound` se asigna a un `const_iterator`, el objeto de mapa múltiple no se puede modificar. Si el valor devuelto de `lower_bound` se asigna a un elemento **iterator**, el objeto de mapa múltiple se puede modificar.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_lower_bound.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap <int, int> m1;  
   multimap <int, int> :: const_iterator m1_AcIter, m1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
  
   m1_RcIter = m1.lower_bound( 2 );  
   cout << "The element of multimap m1 with a key of 2 is: "  
        << m1_RcIter -> second << "." << endl;  
  
   m1_RcIter = m1.lower_bound( 3 );  
   cout << "The first element of multimap m1 with a key of 3 is: "  
        << m1_RcIter -> second << "." << endl;  
  
   // If no match is found for the key, end( ) is returned  
   m1_RcIter = m1.lower_bound( 4 );  
  
   if ( m1_RcIter == m1.end( ) )  
      cout << "The multimap m1 doesn't have an element "  
              << "with a key of 4." << endl;  
   else  
      cout << "The element of multimap m1 with a key of 4 is: "  
                << m1_RcIter -> second << "." << endl;  
  
   // The element at a specific location in the multimap can be  
   // found using a dereferenced iterator addressing the location  
   m1_AcIter = m1.end( );  
   m1_AcIter--;  
   m1_RcIter = m1.lower_bound( m1_AcIter -> first );  
   cout << "The first element of m1 with a key matching\n"  
        << "that of the last element is: "  
        << m1_RcIter -> second << "." << endl;  
  
   // Note that the first element with a key equal to  
   // the key of the last element is not the last element  
   if ( m1_RcIter == --m1.end( ) )  
      cout << "This is the last element of multimap m1."  
           << endl;  
   else  
      cout << "This is not the last element of multimap m1."  
           << endl;  
}  
```  
  
```Output  
The element of multimap m1 with a key of 2 is: 20.  
The first element of multimap m1 with a key of 3 is: 20.  
The multimap m1 doesn't have an element with a key of 4.  
The first element of m1 with a key matching  
that of the last element is: 20.  
This is not the last element of multimap m1.  
```  
  
##  <a name="mapped_type"></a> multimap::mapped_type  
 Un tipo que representa el tipo de datos almacenado en un mapa múltiple.  
  
```  
typedef Type mapped_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 `mapped_type` es un sinónimo del parámetro de plantilla `Type`.  
  
 Para obtener más información sobre `Type`, vea el tema [multimap (Clase)](../standard-library/multimap-class.md).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [value_type](#value_type) para obtener un ejemplo de cómo declarar y usar `key_type`.  
  
##  <a name="max_size"></a> multimap::max_size  
 Devuelve la longitud máxima del mapa múltiple.  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud máxima posible del mapa múltiple.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_max_size.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap <int, int> m1;  
   multimap <int, int> :: size_type i;  
  
   i = m1.max_size( );  
   cout << "The maximum possible length "  
        << "of the multimap is " << i << "." << endl;  
}  
```  
  
##  <a name="multimap"></a> multimap::multimap  
 Construye un multimap que está vacío o que es una copia de todo o de parte de otro multimap.  
  
```  
multimap();

explicit multimap(
    const Traits& Comp);

multimap(
    const Traits& Comp,  
    const Allocator& Al);

map(
    const multimap& Right);

multimap(
    multimap&& Right);

multimap(
    initializer_list<value_type> IList);

multimap(
    initializer_list<value_type> IList,  
    const Compare& Comp);

multimap(
    initializer_list<value_type> IList,  
    const Compare& Comp,   
    const Allocator& Al);

template <class InputIterator>  
multimap(
 InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
multimap(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp);

template <class InputIterator>  
multimap(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp,  
    const Allocator& Al);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`Al`|Clase de asignador de almacenamiento que se utilizará para este objeto multimap, que de forma predeterminada es Allocator.|  
|`Comp`|La función de comparación de tipo **constTraits** usada para ordenar los elementos de la asignación, que de manera predeterminada es **Traits**.|  
|`Right`|Asignación de la que el conjunto construido va a ser una copia.|  
|`First`|Posición del primer elemento en el intervalo de elementos que se va a copiar.|  
|`Last`|Posición del primer elemento más allá del intervalo de elementos que se va a copiar.|  
|`IList`|initializer_list de la que se van a copiar los elementos.|  
  
### <a name="remarks"></a>Comentarios  
 Todos los constructores almacenan un tipo de objeto de asignador que administra el almacenamiento en memoria del mapa múltiple y que se puede devolver más adelante llamando a [get_allocator](#get_allocator). El parámetro de asignador se suele omitir en las declaraciones de clase y las macros de preprocesamiento que se utilizan para sustituir asignadores alternativos.  
  
 Todos los constructores inicializan su multimap.  
  
 Todos los constructores almacenan un objeto de función de tipo `Traits` que se usa para establecer un orden entre las claves del mapa múltiple y que se puede devolver más adelante llamando a [key_comp](#key_comp).  
  
 Los tres primeros constructores especifican un mapa múltiple inicial vacío, el segundo especifica el tipo de función de comparación (`Comp`) que se usará para establecer el orden de los elementos y el tercero especifica explícitamente el tipo de asignador (`Al`) que se va a usar. La palabra clave `explicit` suprime ciertas clases de conversión automática de tipos.  
  
 El cuarto constructor especifica una copia del multimap `Right`.  
  
 El quinto constructor especifica una copia del multimap moviendo `Right`.  
  
 Los constructores sexto, séptimo y octavo copian los miembros de una initializer_list.  
  
 Los tres constructores siguientes copian el intervalo `[First, Last)` de un mapa especificando de manera cada vez más explícita el tipo de función de comparación de clase **Traits** y el asignador.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_ctor.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    typedef pair <int, int> Int_Pair;  
  
    // Create an empty multimap m0 of key type integer  
    multimap <int, int> m0;  
  
    // Create an empty multimap m1 with the key comparison  
    // function of less than, then insert 4 elements  
    multimap <int, int, less<int> > m1;  
    m1.insert(Int_Pair(1, 10));  
    m1.insert(Int_Pair(2, 20));  
    m1.insert(Int_Pair(3, 30));  
    m1.insert(Int_Pair(4, 40));  
  
    // Create an empty multimap m2 with the key comparison  
    // function of geater than, then insert 2 elements  
    multimap <int, int, less<int> > m2;  
    m2.insert(Int_Pair(1, 10));  
    m2.insert(Int_Pair(2, 20));  
  
    // Create a multimap m3 with the   
    // allocator of multimap m1  
    multimap <int, int>::allocator_type m1_Alloc;  
    m1_Alloc = m1.get_allocator();  
    multimap <int, int> m3(less<int>(), m1_Alloc);  
    m3.insert(Int_Pair(3, 30));  
  
    // Create a copy, multimap m4, of multimap m1  
    multimap <int, int> m4(m1);  
  
    // Create a multimap m5 by copying the range m1[ first,  last)  
    multimap <int, int>::const_iterator m1_bcIter, m1_ecIter;  
    m1_bcIter = m1.begin();  
    m1_ecIter = m1.begin();  
    m1_ecIter++;  
    m1_ecIter++;  
    multimap <int, int> m5(m1_bcIter, m1_ecIter);  
  
    // Create a multimap m6 by copying the range m4[ first,  last)  
    // and with the allocator of multimap m2  
    multimap <int, int>::allocator_type m2_Alloc;  
    m2_Alloc = m2.get_allocator();  
    multimap <int, int> m6(m4.begin(), ++m4.begin(), less<int>(), m2_Alloc);  
  
    cout << "m1 =";  
    for (auto i : m1)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    cout << "m2 =";  
    for (auto i : m2)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    cout << "m3 =";  
    for (auto i : m3)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    cout << "m4 =";  
    for (auto i : m4)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    cout << "m5 =";  
    for (auto i : m5)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    cout << "m6 =";  
    for (auto i : m6)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    // Create a multimap m8 by copying in an initializer_list  
    multimap<int, int> m8{ { { 1, 1 }, { 2, 2 }, { 3, 3 }, { 4, 4 } } };  
    cout << "m8: = ";  
    for (auto i : m8)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    // Create a multimap m9 with an initializer_list and a comparator  
    multimap<int, int> m9({ { 5, 5 }, { 6, 6 }, { 7, 7 }, { 8, 8 } }, less<int>());  
    cout << "m9: = ";  
    for (auto i : m9)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    // Create a multimap m10 with an initializer_list, a comparator, and an allocator  
    multimap<int, int> m10({ { 9, 9 }, { 10, 10 }, { 11, 11 }, { 12, 12 } }, less<int>(), m9.get_allocator());  
    cout << "m10: = ";  
    for (auto i : m10)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
}  
  
```  
  
##  <a name="op_eq"></a> multimap::operator=  
 Reemplaza los elementos de un mapa múltiple por una copia de otro mapa múltiple.  
  
```  
multimap& operator=(const multimap& right);

multimap& operator=(multimap&& right);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`right`|El [mapa múltiple](../standard-library/multimap-class.md) que se copia a `multimap`.|  
  
### <a name="remarks"></a>Comentarios  
 Después de borrar todos los elementos existentes en un `multimap`, `operator=` copia o mueve el contenido de `right` al `multimap`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_operator_as.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
   {  
   using namespace std;  
   multimap<int, int> v1, v2, v3;  
   multimap<int, int>::iterator iter;  
  
   v1.insert(pair<int, int>(1, 10));  
  
   cout << "v1 = " ;  
   for (iter = v1.begin(); iter != v1.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
  
   v2 = v1;  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
  
// move v1 into v2  
   v2.clear();  
   v2 = move(v1);  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
   }  
```  
  
##  <a name="pointer"></a> multimap::pointer  
 Un tipo que proporciona un puntero a un elemento de un mapa múltiple.  
  
```  
typedef typename allocator_type::pointer pointer;  
```  
  
### <a name="remarks"></a>Comentarios  
 Se puede usar un tipo **pointer** para modificar el valor de un elemento.  
  
 En la mayoría de los casos, se debe usar un elemento [iterator](#iterator) para obtener acceso a los elementos de un objeto multimap.  
  
##  <a name="rbegin"></a> multimap::rbegin  
 Devuelve un iterador que se dirige al primer elemento en un mapa múltiple invertido.  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador bidireccional invertido que se dirige al primer elemento de un mapa múltiple invertido o que se dirige a lo que habría sido el último elemento del mapa múltiple sin invertir.  
  
### <a name="remarks"></a>Comentarios  
 `rbegin` se usa con un mapa múltiple invertido igual que [begin](#begin) se usa con un mapa múltiple.  
  
 Si el valor devuelto de `rbegin` se asigna a un `const_reverse_iterator`, el objeto del mapa múltiple no puede modificarse. Si el valor devuelto de `rbegin` se asigna a un `reverse_iterator`, el objeto del mapa múltiple puede modificarse.  
  
 `rbegin` puede usarse para iterar un mapa múltiple hacia atrás.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_rbegin.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap <int, int> m1;  
  
   multimap <int, int> :: iterator m1_Iter;  
   multimap <int, int> :: reverse_iterator m1_rIter;  
   multimap <int, int> :: const_reverse_iterator m1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
  
   m1_rIter = m1.rbegin( );  
   cout << "The first element of the reversed multimap m1 is "  
        << m1_rIter -> first << "." << endl;  
  
   // begin can be used to start an iteration   
   // throught a multimap in a forward order  
   cout << "The multimap is: ";  
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)  
      cout << m1_Iter -> first << " ";  
      cout << "." << endl;  
  
   // rbegin can be used to start an iteration   
   // throught a multimap in a reverse order  
   cout << "The reversed multimap is: ";  
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)  
      cout << m1_rIter -> first << " ";  
      cout << "." << endl;  
  
   // A multimap element can be erased by dereferencing its key   
   m1_rIter = m1.rbegin( );  
   m1.erase ( m1_rIter -> first );  
  
   m1_rIter = m1.rbegin( );  
   cout << "After the erasure, the first element "  
        << "in the reversed multimap is "  
        << m1_rIter -> first << "." << endl;  
}  
```  
  
```Output  
The first element of the reversed multimap m1 is 3.  
The multimap is: 1 2 3 .  
The reversed multimap is: 3 2 1 .  
After the erasure, the first element in the reversed multimap is 2.  
```  
  
##  <a name="reference"></a> multimap::reference  
 Un tipo que proporciona una referencia a un elemento almacenado en un mapa múltiple.  
  
```  
typedef typename allocator_type::reference reference;  
```  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_ref.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap <int, int> m1;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the key of the first element  
   const int &Ref1 = ( m1.begin( ) -> first );  
  
   // The following line would cause an error because the   
   // non-const_reference cannot be used to access the key  
   // int &Ref1 = ( m1.begin( ) -> first );  
  
   cout << "The key of first element in the multimap is "  
        << Ref1 << "." << endl;  
  
   // Declare and initialize a reference &Ref2   
   // to the data value of the first element  
   int &Ref2 = ( m1.begin( ) -> second );  
  
   cout << "The data value of first element in the multimap is "  
        << Ref2 << "." << endl;  
  
   // The non-const_reference can be used to modify the   
   // data value of the first element  
   Ref2 = Ref2 + 5;  
   cout << "The modified data value of first element is "  
        << Ref2 << "." << endl;  
}  
```  
  
```Output  
The key of first element in the multimap is 1.  
The data value of first element in the multimap is 10.  
The modified data value of first element is 15.  
```  
  
##  <a name="rend"></a> multimap::rend  
 Devuelve un iterador que se dirige a la ubicación que sigue al último elemento en un mapa múltiple invertido.  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador bidireccional inverso que se dirige a la ubicación siguiente al último elemento de un mapa múltiple invertido (la ubicación que había precedido al primer elemento del mapa múltiple sin invertir).  
  
### <a name="remarks"></a>Comentarios  
 `rend` se usa con un mapa múltiple invertido igual que [end](../standard-library/map-class.md#end) se usa con un mapa múltiple.  
  
 Si el valor devuelto de `rend` se asigna a un `const_reverse_iterator`, el objeto del mapa múltiple no puede modificarse. Si el valor devuelto de `rend` se asigna a un `reverse_iterator`, el objeto del mapa múltiple puede modificarse.  
  
 Se puede usar `rend` para comprobar si un iterador inverso ha llegado al final de su mapa múltiple.  
  
 El valor devuelto por `rend` no se debe desreferenciar.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_rend.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap <int, int> m1;  
  
   multimap <int, int> :: iterator m1_Iter;  
   multimap <int, int> :: reverse_iterator m1_rIter;  
   multimap <int, int> :: const_reverse_iterator m1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
  
   m1_rIter = m1.rend( );  
   m1_rIter--;  
   cout << "The last element of the reversed multimap m1 is "  
        << m1_rIter -> first << "." << endl;  
  
   // begin can be used to start an iteration   
   // throught a multimap in a forward order  
   cout << "The multimap is: ";  
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)  
      cout << m1_Iter -> first << " ";  
      cout << "." << endl;  
  
   // rbegin can be used to start an iteration   
   // throught a multimap in a reverse order  
   cout << "The reversed multimap is: ";  
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)  
      cout << m1_rIter -> first << " ";  
      cout << "." << endl;  
  
   // A multimap element can be erased by dereferencing to its key   
   m1_rIter = --m1.rend( );  
   m1.erase ( m1_rIter -> first );  
  
   m1_rIter = m1.rend( );  
   m1_rIter--;  
   cout << "After the erasure, the last element "  
        << "in the reversed multimap is "  
        << m1_rIter -> first << "." << endl;  
}  
```  
  
```Output  
The last element of the reversed multimap m1 is 1.  
The multimap is: 1 2 3 .  
The reversed multimap is: 3 2 1 .  
After the erasure, the last element in the reversed multimap is 2.  
```  
  
##  <a name="reverse_iterator"></a> multimap::reverse_iterator  
 Un tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento en un mapa múltiple invertido.  
  
```  
typedef std::reverse_iterator<iterator> reverse_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo `reverse_iterator` se usa para iterar en el mapa múltiple en orden inverso.  
  
 El `reverse_iterator` definido por puntos multimap a objetos de [value_type](#value_type), que son de tipo `pair` * \< * **clave const**, **Tipo *** >*. El valor de la clave está disponible mediante el primer miembro del par y el valor del elemento asignado está disponible mediante el segundo miembro del par.  
  
 A fin de desreferenciar una `reverse_iterator` `rIter` apunta a un elemento de una asignación múltiple, use el operador ->.  
  
 Para tener acceso al valor de clave del elemento, use `rIter` -> **first**, que es equivalente a (\* `rIter`). **first**. Para tener acceso al valor de la referencia asignada del elemento, use `rIter` -> **second**, que es equivalente a (\* `rIter`). **first**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [rbegin](#rbegin) para obtener un ejemplo de cómo declarar y usar `reverse_iterator`.  
  
##  <a name="size"></a> multimap::size  
 Devuelve el número de elementos de multimap.  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud actual de multimap.  
  
### <a name="example"></a>Ejemplo  
  El ejemplo siguiente muestra cómo debe usarse la función miembro multimap::size.  
  
```  
// multimap_size.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    multimap<int, int> m1, m2;  
    multimap<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    m1.insert(Int_Pair(1, 1));  
    i = m1.size();  
    cout << "The multimap length is " << i << "." << endl;  
  
    m1.insert(Int_Pair(2, 4));  
    i = m1.size();  
    cout << "The multimap length is now " << i << "." << endl;  
}  
```  
  
```Output  
The multimap length is 1.  
The multimap length is now 2.  
```  
  
##  <a name="size_type"></a> multimap::size_type  
 Un tipo entero sin signo que cuenta el número de elementos de un mapa múltiple.  
  
```  
typedef typename allocator_type::size_type size_type;  
```  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [size](#size) para obtener un ejemplo de cómo declarar y usar `size_type`  
  
##  <a name="swap"></a> multimap::swap  
 Intercambia los elementos de dos mapas múltiples.  
  
```  
void swap(
    multimap<Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 Mapa múltiple que proporciona los elementos que se van a intercambiar o el mapa múltiple cuyos elementos se van a intercambiar con los del mapa múltiple `left`.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro no invalida ninguna referencia, puntero o iterador que designan los elementos de los dos mapas múltiples cuyos elementos se intercambian.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_swap.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap <int, int> m1, m2, m3;  
   multimap <int, int>::iterator m1_Iter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
   m2.insert ( Int_Pair ( 10, 100 ) );  
   m2.insert ( Int_Pair ( 20, 200 ) );  
   m3.insert ( Int_Pair ( 30, 300 ) );  
  
   cout << "The original multimap m1 is:";  
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )  
      cout << " " << m1_Iter -> second;  
   cout   << "." << endl;  
  
   // This is the member function version of swap  
   m1.swap( m2 );  
  
   cout << "After swapping with m2, multimap m1 is:";  
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )  
      cout << " " << m1_Iter -> second;  
   cout  << "." << endl;  
  
   // This is the specialized template version of swap  
   swap( m1, m3 );  
  
   cout << "After swapping with m3, multimap m1 is:";  
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )  
      cout << " " << m1_Iter -> second;  
   cout   << "." << endl;  
}  
```  
  
```Output  
The original multimap m1 is: 10 20 30.  
After swapping with m2, multimap m1 is: 100 200.  
After swapping with m3, multimap m1 is: 300.  
```  
  
##  <a name="upper_bound"></a> multimap::upper_bound  
 Devuelve un iterador al primer elemento de un mapa múltiple con un valor de clave que es mayor al de una clave especificada.  
  
```  
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 La clave de argumento que se comparará con la clave de ordenación de un elemento del mapa múltiple que se está buscando.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador o `const_iterator` que se dirige a la ubicación de un elemento en un mapa múltiple que tiene una clave mayor que la clave de argumento o que se dirige a la ubicación siguiente al último elemento del mapa múltiple si no se encuentra ninguna coincidencia con la clave.  
  
 Si el valor devuelto se asigna a un `const_iterator`, el objeto de mapa múltiple no se puede modificar. Si el valor devuelto se asigna a un elemento **iterator**, el objeto de mapa múltiple no se puede modificar.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_upper_bound.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap <int, int> m1;  
   multimap <int, int> :: const_iterator m1_AcIter, m1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
   m1.insert ( Int_Pair ( 3, 40 ) );  
  
   m1_RcIter = m1.upper_bound( 1 );  
   cout << "The 1st element of multimap m1 with "  
        << "a key greater than 1 is: "  
        << m1_RcIter -> second << "." << endl;  
  
   m1_RcIter = m1.upper_bound( 2 );  
   cout << "The first element of multimap m1 with a key "  
        << " greater than 2 is: "  
        << m1_RcIter -> second << "." << endl;  
  
   // If no match is found for the key, end( ) is returned  
   m1_RcIter = m1.lower_bound( 4 );  
  
   if ( m1_RcIter == m1.end( ) )  
      cout << "The multimap m1 doesn't have an element "  
           << "with a key of 4." << endl;  
   else  
      cout << "The element of multimap m1 with a key of 4 is: "  
           << m1_RcIter -> second << "." << endl;  
  
   // The element at a specific location in the multimap can be  
   // found using a derefenced iterator addressing the location  
   m1_AcIter = m1.begin( );  
   m1_RcIter = m1.upper_bound( m1_AcIter -> first );  
   cout << "The first element of m1 with a key greater than\n"  
        << "that of the initial element of m1 is: "  
        << m1_RcIter -> second << "." << endl;  
}  
```  
  
```Output  
The 1st element of multimap m1 with a key greater than 1 is: 20.  
The first element of multimap m1 with a key  greater than 2 is: 30.  
The multimap m1 doesn't have an element with a key of 4.  
The first element of m1 with a key greater than  
that of the initial element of m1 is: 20.  
```  
  
##  <a name="value_comp"></a> multimap::value_comp  
 La función miembro devuelve un objeto de función que determina el orden de los elementos de un mapa múltiple mediante la comparación de sus valores de clave.  
  
```  
value_compare value_comp() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el objeto de función de comparación que usa un mapa múltiple para ordenar sus elementos.  
  
### <a name="remarks"></a>Comentarios  
 Para un mapa múltiple *m*, si dos elementos *e*1( *k*1, *d*1) y *e*2( *k*2, `d`2) son objetos de tipo `value_type`, donde *k*1 y *k*2 son sus claves de tipo `key_type`, y `d`1 y `d`2 son sus datos de tipo `mapped_type`, entonces *m.*`value_comp`( *e*1, *e*2) es equivalente a *m.*`key_comp`( *k*1, *k*2).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_value_comp.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   multimap <int, int, less<int> > m1;  
   multimap <int, int, less<int> >::value_compare vc1 = m1.value_comp( );  
   multimap<int,int>::iterator Iter1, Iter2;  
  
   Iter1= m1.insert ( multimap <int, int> :: value_type ( 1, 10 ) );  
   Iter2= m1.insert ( multimap <int, int> :: value_type ( 2, 5 ) );  
  
   if( vc1( *Iter1, *Iter2 ) == true )     
   {  
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."  
           << endl;  
   }  
   else     
   {  
      cout << "The element ( 1,10 ) does "  
           << "not precede the element ( 2,5 )."  
           << endl;  
   }  
  
   if( vc1( *Iter2, *Iter1 ) == true )     
   {  
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."  
           << endl;  
   }  
   else     
   {  
      cout << "The element ( 2,5 ) does "  
           << "not precede the element ( 1,10 )."  
           << endl;  
   }  
}  
```  
  
```Output  
The element ( 1,10 ) precedes the element ( 2,5 ).  
The element ( 2,5 ) does not precede the element ( 1,10 ).  
```  
  
##  <a name="value_type"></a> multimap::value_type  
 Un tipo que representa el tipo de objeto almacenado como un elemento en un mapa.  
  
```  
typedef pair<const Key, Type> value_type;  
```  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multimap_value_type.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   typedef pair <const int, int> cInt2Int;  
   multimap <int, int> m1;  
   multimap <int, int> :: key_type key1;  
   multimap <int, int> :: mapped_type mapped1;  
   multimap <int, int> :: value_type value1;  
   multimap <int, int> :: iterator pIter;  
  
   // value_type can be used to pass the correct type  
   // explicitely to avoid implicit type conversion  
   m1.insert ( multimap <int, int> :: value_type ( 1, 10 ) );  
  
   // Compare another way to insert objects into a hash_multimap  
   m1.insert ( cInt2Int ( 2, 20 ) );  
  
   // Initializing key1 and mapped1  
   key1 = ( m1.begin( ) -> first );  
   mapped1 = ( m1.begin( ) -> second );  
  
   cout << "The key of first element in the multimap is "  
        << key1 << "." << endl;  
  
   cout << "The data value of first element in the multimap is "  
        << mapped1 << "." << endl;  
  
   // The following line would cause an error because  
   // the value_type is not assignable  
   // value1 = cInt2Int ( 4, 40 );  
  
   cout  << "The keys of the mapped elements are:";  
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )  
      cout << " " << pIter -> first;  
   cout << "." << endl;  
  
   cout  << "The values of the mapped elements are:";  
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )  
      cout << " " << pIter -> second;  
   cout << "." << endl;  
}  
```  
  
```Output  
The key of first element in the multimap is 1.  
The data value of first element in the multimap is 10.  
The keys of the mapped elements are: 1 2.  
The values of the mapped elements are: 10 20.  
```  
  
## <a name="see-also"></a>Vea también  
 [Miembros \<map>](http://msdn.microsoft.com/en-us/7e8f0bc2-6034-40f6-9d14-76d4cef86308)   
 [Contenedores](../cpp/containers-modern-cpp.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)

