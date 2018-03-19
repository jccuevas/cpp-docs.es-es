---
title: multiset (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- set/std::multiset
- set/std::multiset::allocator_type
- set/std::multiset::const_iterator
- set/std::multiset::const_pointer
- set/std::multiset::const_reference
- set/std::multiset::const_reverse_iterator
- set/std::multiset::difference_type
- set/std::multiset::iterator
- set/std::multiset::key_compare
- set/std::multiset::key_type
- set/std::multiset::pointer
- set/std::multiset::reference
- set/std::multiset::reverse_iterator
- set/std::multiset::size_type
- set/std::multiset::value_compare
- set/std::multiset::value_type
- set/std::multiset::begin
- set/std::multiset::cbegin
- set/std::multiset::cend
- set/std::multiset::clear
- set/std::multiset::count
- set/std::multiset::crbegin
- set/std::multiset::crend
- set/std::multiset::emplace
- set/std::multiset::emplace_hint
- set/std::multiset::empty
- set/std::multiset::end
- set/std::multiset::equal_range
- set/std::multiset::erase
- set/std::multiset::find
- set/std::multiset::get_allocator
- set/std::multiset::insert
- set/std::multiset::key_comp
- set/std::multiset::lower_bound
- set/std::multiset::max_size
- set/std::multiset::rbegin
- set/std::multiset::rend
- set/std::multiset::size
- set/std::multiset::swap
- set/std::multiset::upper_bound
- set/std::multiset::value_comp
dev_langs:
- C++
helpviewer_keywords:
- std::multiset [C++]
- std::multiset [C++], allocator_type
- std::multiset [C++], const_iterator
- std::multiset [C++], const_pointer
- std::multiset [C++], const_reference
- std::multiset [C++], const_reverse_iterator
- std::multiset [C++], difference_type
- std::multiset [C++], iterator
- std::multiset [C++], key_compare
- std::multiset [C++], key_type
- std::multiset [C++], pointer
- std::multiset [C++], reference
- std::multiset [C++], reverse_iterator
- std::multiset [C++], size_type
- std::multiset [C++], value_compare
- std::multiset [C++], value_type
- std::multiset [C++], begin
- std::multiset [C++], cbegin
- std::multiset [C++], cend
- std::multiset [C++], clear
- std::multiset [C++], count
- std::multiset [C++], crbegin
- std::multiset [C++], crend
- std::multiset [C++], emplace
- std::multiset [C++], emplace_hint
- std::multiset [C++], empty
- std::multiset [C++], end
- std::multiset [C++], equal_range
- std::multiset [C++], erase
- std::multiset [C++], find
- std::multiset [C++], get_allocator
- std::multiset [C++], insert
- std::multiset [C++], key_comp
- std::multiset [C++], lower_bound
- std::multiset [C++], max_size
- std::multiset [C++], rbegin
- std::multiset [C++], rend
- std::multiset [C++], size
- std::multiset [C++], swap
- std::multiset [C++], upper_bound
- std::multiset [C++], value_comp
ms.assetid: 630e8c10-0ce9-4ad9-8d79-9e91a600713f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a8953fd24b62784e36f12fb96e3005e21a86bc62
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2018
---
# <a name="multiset-class"></a>multiset (Clase)
La clase multiset de la Biblioteca estándar de C++ se usa para el almacenamiento y la recuperación de datos de una colección en la que los valores de los elementos contenidos no tienen por qué ser únicos y en la que actúan como valores de clave según los cuales los datos se ordenan automáticamente. El valor de clave de un elemento de un multiset no se puede cambiar directamente. En su lugar, se deben eliminar los valores anteriores e insertar elementos con valores nuevos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Key, class Compare =less <Key>, class Allocator =allocator <Key>>  
class multiset  
```  
  
#### <a name="parameters"></a>Parámetros  
 *Key*  
 Tipo de datos de elemento que se va a almacenar en la clase multiset.  
  
 *Compare*  
 Tipo que proporciona un objeto de función que puede comparar dos valores de elementos como claves de ordenación para determinar su orden relativo en la clase multiset. El predicado binario **less**\<Key> es el valor predeterminado.  
  
 En C++14 puede habilitar la búsqueda heterogénea especificando el predicado `std::less<>` o `std::greater<>`, que no tienen ningún parámetro de tipo. Para obtener más información, vea [Búsqueda heterogénea en los contenedores asociativos](../standard-library/stl-containers.md#sequence_containers).  
  
 `Allocator`  
 Tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria de la clase multiset. El valor predeterminado es **asignador***\<clave >.*  
  
## <a name="remarks"></a>Comentarios  
 La clase multiset de la Biblioteca estándar de C++ es:  
  
-   Un contenedor asociativo de tamaño variable que admite la recuperación eficaz de valores de elemento según un valor de clave asociado.  
  
-   Reversible, porque proporciona iteradores bidireccionales para tener acceso a sus elementos.  
  
-   Ordenada, porque sus elementos se ordenan según los valores de clave dentro del contenedor de acuerdo con una función de comparación especificada.  
  
-   Múltiple en el sentido de que sus elementos no necesitan tener claves únicas, de modo que un valor de clave puede tener asociados varios valores de elemento.  
  
-   Un contenedor asociativo simple porque sus valores de elemento son sus valores de clave.  
  
-   Una clase de plantilla, porque la funcionalidad que proporciona es genérica y por tanto independiente del tipo específico de datos contenido como elementos. En su lugar, el tipo de datos que se usará se especifica como un parámetro en la plantilla de clase junto con la función de comparación y el asignador.  
  
 El iterador proporcionado por la clase multiset es un iterador bidireccional, pero las funciones miembro de clase [insert](#insert) y [multiset](#multiset) tienen versiones que toman como parámetros de plantilla un iterador de entrada menos seguro, cuyos requisitos de función son más mínimos que los garantizados por la clase de iteradores bidireccionales. Los distintos conceptos de iterador forman una familia relacionada por los refinamientos de su funcionalidad. Cada concepto de iterador tiene su propio conjunto de requisitos y los algoritmos que funcionan con ellos deben limitar sus suposiciones a los requisitos proporcionados por ese tipo de iterador. Se puede suponer que se puede desreferenciar un iterador de entrada para hacer referencia a un objeto y que se puede incrementar hasta el iterador siguiente de la secuencia. Se trata de un conjunto mínimo de función, pero es suficiente para poder comunicarse sobre un intervalo de iteradores [ `First`, `Last`) en el contexto de las funciones miembro de clase.  
  
 En general, la elección del tipo de contenedor se debe tomar según el tipo de búsqueda y de inserción que necesite la aplicación. Los contenedores asociativos están optimizados para las operaciones de búsqueda, inserción y eliminación. Las funciones miembro que admiten estas operaciones explícitamente las realizan de forma eficiente en un tiempo que es proporcional en promedio al logaritmo del número de elementos del contenedor. La inserción de elementos no invalida ningún iterador y al quitar elementos solo se invalidan los iteradores que habían apuntado específicamente a los elementos quitados.  
  
 La clase multiset debe ser el contenedor asociativo preferido cuando la aplicación satisfaga las condiciones que asocian los valores a sus claves. Los elementos de una clase multiset pueden ser varios y actuar como sus propias claves de ordenación, por lo que las claves no son únicas. Un modelo para este tipo de estructura es una lista ordenada, por ejemplo, de palabras en las que las palabras pueden aparecer más de una vez. Si no se permitieran varias repeticiones de las palabras, la estructura de contenedor adecuada sería un set. Si se asociaron definiciones únicas como valores a la lista de palabras clave únicas, la estructura adecuada para contener estos datos sería una clase map. Si por el contrario las definiciones no son únicas, un multimap sería el contenedor preferido.  
  
 La clase multiset ordena la secuencia que controla llamando a un objeto de función almacenado de tipo `Compare`. Este objeto almacenado es una función de comparación a la que se puede tener acceso mediante una llamada a la función miembro [key_comp](#key_comp). En general, se debe poder comparar si los elementos son menores que otros para poder establecer este orden; de este modo, dados dos elementos cualesquiera, se puede determinar que son equivalentes (en el sentido de que ninguno es menor que el otro) o que uno es menor que el otro. Esto produce una ordenación entre los elementos no equivalentes. En un sentido más técnico, la función de comparación es un predicado binario que induce una ordenación débil estricta en el sentido matemático estándar. Un predicado binario *f*( *x*, *y*) es un objeto de función que tiene dos objetos de argumento *x* e *y*, y un valor devuelto de **True** o **False**. Una ordenación impuesta en un conjunto es una ordenación débil estricta si el predicado binario es irreflexivo, antisimétrico y transitivo, y si la equivalencia es transitiva, donde dos objetos x e y se definen como equivalentes cuando tanto *f*( *x,y*) y *f*( *y,x*) son False. Si la condición más fuerte de igualdad entre las claves reemplaza la de equivalencia, la ordenación se convierte en total (en el sentido de que todos los elementos se ordenan entre sí) y las claves coincidentes serán indiscernibles unas de otras.  
  
 En C++14 puede habilitar la búsqueda heterogénea especificando el predicado `std::less<>` o `std::greater<>`, que no tienen ningún parámetro de tipo. Para obtener más información, vea [Búsqueda heterogénea en los contenedores asociativos](../standard-library/stl-containers.md#sequence_containers).  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[multiset](#multiset)|Construye un `multiset` que está vacío o que es una copia de todo o de parte de un `multiset` especificado.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|Definición de tipos para la clase `allocator` del objeto `multiset`.|  
|[const_iterator](#const_iterator)|Definición de tipos para un iterador bidireccional que puede leer un elemento `const` del `multiset`.|  
|[const_pointer](#const_pointer)|Definición de tipos para un puntero a un elemento `const` de un `multiset`.|  
|[const_reference](#const_reference)|Definición de tipos para una referencia a un elemento `const` almacenado en un `multiset` para leer y realizar operaciones `const`.|  
|[const_reverse_iterator](#const_reverse_iterator)|Definición de tipos para un iterador bidireccional que puede leer cualquier elemento `const` del `multiset`.|  
|[difference_type](#difference_type)|Definición de tipos enteros con signo para el número de elementos de un `multiset` en un intervalo entre los elementos a los que apuntan los iteradores.|  
|[iterator](#iterator)|Definición de tipos para un iterador bidireccional que puede leer o modificar cualquier elemento de un `multiset`.|  
|[key_compare](#key_compare)|Definición de tipos para un objeto de función que puede comparar dos claves para determinar el orden relativo de dos elementos del `multiset`.|  
|[key_type](#key_type)|Definición de tipos para un objeto de función que puede comparar dos claves de ordenación para determinar el orden relativo de dos elementos del `multiset`.|  
|[pointer](#pointer)|Definición de tipos para un puntero a un elemento de un `multiset`.|  
|[reference](#reference)|Definición de tipos para una referencia a un elemento almacenado en un `multiset`.|  
|[reverse_iterator](#reverse_iterator)|Definición de tipos para un iterador bidireccional que puede leer o modificar un elemento de un `multiset` invertido.|  
|[size_type](#size_type)|Tipo entero sin signo que puede representar el número de elementos de un `multiset`.|  
|[value_compare](#value_compare)|Definición de tipos para un objeto de función que puede comparar dos elementos como claves de ordenación para determinar su orden relativo en el `multiset`.|  
|[value_type](#value_type)|Definición de tipos que describe un objeto almacenado como un elemento como un `multiset` en su capacidad como valor.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[begin](#begin)|Devuelve un iterador que apunta al primer elemento del `multiset`.|  
|[cbegin](#cbegin)|Devuelve un iterador const que direcciona el primer elemento del `multiset`.|  
|[cend](#cend)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de `multiset`.|  
|[clear](#clear)|Borra todos los elementos de un `multiset`.|  
|[count](#count)|Devuelve el número de elementos de un `multiset` cuya clave coincide con la clave especificada como parámetro.|  
|[crbegin](#crbegin)|Devuelve un iterador const que direcciona el primer elemento de un set invertido.|  
|[crend](#crend)|Devuelve un iterador const que direcciona la ubicación que sigue al último elemento de un set invertido.|  
|[emplace](#emplace)|Inserta en un `multiset` un elemento construido en contexto.|  
|[emplace_hint](#emplace_hint)|Inserta en un `multiset` un elemento construido en contexto, con una sugerencia de colocación.|  
|[empty](#empty)|Comprueba si un `multiset` está vacío.|  
|[end](#end)|Devuelve un iterador que apunta a la ubicación posterior al último elemento de un `multiset` invertido.|  
|[equal_range](#equal_range)|Devuelve un par de iteradores. El primer iterador del par apunta al primer elemento de un `multiset` cuya clave es mayor que una clave especificada. El segundo iterador del par apunta al primer elemento del `multiset` cuya clave es igual o mayor que la clave especificada.|  
|[erase](#erase)|Quita un elemento o un intervalo de elementos de una clase `multiset` de las posiciones especificadas o quita los elementos que coinciden con una clave especificada.|  
|[find](#find)|Devuelve un iterador que apunta a la primera ubicación de un elemento en un `multiset` que tiene una clave igual que una clave especificada.|  
|[get_allocator](#get_allocator)|Devuelve una copia del objeto `allocator` utilizado para construir el `multiset`.|  
|[insert](#insert)|Inserta un elemento o un intervalo de elementos en un `multiset`.|  
|[key_comp](#key_comp)|Proporciona un objeto de función que puede comparar dos claves de ordenación para determinar el orden relativo de dos elementos en el `multiset`.|  
|[lower_bound](#lower_bound)|Devuelve un iterador al primer elemento de un `multiset` cuya clave es igual o mayor que una clave especificada.|  
|[max_size](#max_size)|Devuelve la longitud máxima del `multiset`.|  
|[rbegin](#rbegin)|Devuelve un iterador que apunta al primer elemento de un `multiset` invertido.|  
|[rend](#rend)|Devuelve un iterador que apunta a la ubicación posterior al último elemento de un `multiset` invertido.|  
|[size](#size)|Devuelve el número de elementos de un `multiset`.|  
|[swap](#swap)|Intercambia los elementos de dos `multiset`.|  
|[upper_bound](#upper_bound)|Devuelve un iterador al primer elemento de un `multiset` con una clave que es mayor que una clave especificada.|  
|[value_comp](#value_comp)|Recupera una copia del objeto de comparación que se emplea para ordenar los valores de elementos de un `multiset`.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator=](#op_eq)|Reemplaza los elementos de un `multiset` con una copia de otro `multiset`.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<set>  
  
 **Espacio de nombres:** std  
  
##  <a name="allocator_type"></a> multiset::allocator_type  
 Un tipo que representa la clase de asignador para el objeto multiset  
  
```  
typedef Allocator allocator_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 `allocator_type` es un sinónimo del parámetro de plantilla `Allocator`.  
  
 Para obtener más información sobre `Allocator`, vea la sección Comentarios del tema [multiset (Clase)](../standard-library/multiset-class.md).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [get_allocator](#get_allocator) para obtener un ejemplo que usa `allocator_type`  
  
##  <a name="begin"></a> multiset::begin  
 Devuelve un iterador que se dirige al primer elemento del conjunto múltiple.  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador bidireccional que se dirige al primer elemento del conjunto múltiple o a la ubicación siguiente a un conjunto múltiple vacío.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_begin.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int>::iterator ms1_Iter;  
   multiset <int>::const_iterator ms1_cIter;  
  
   ms1.insert( 1 );  
   ms1.insert( 2 );  
   ms1.insert( 3 );  
  
   ms1_Iter = ms1.begin( );  
   cout << "The first element of ms1 is " << *ms1_Iter << endl;  
  
   ms1_Iter = ms1.begin( );  
   ms1.erase( ms1_Iter );  
  
   // The following 2 lines would err as the iterator is const  
   // ms1_cIter = ms1.begin( );  
   // ms1.erase( ms1_cIter );  
  
   ms1_cIter = ms1.begin( );  
   cout << "The first element of ms1 is now " << *ms1_cIter << endl;  
}  
```  
  
```Output  
The first element of ms1 is 1  
The first element of ms1 is now 2  
```  
  
##  <a name="cbegin"></a> multiset::cbegin  
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
  
##  <a name="cend"></a> multiset::cend  
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
  
##  <a name="clear"></a> multiset::clear  
 Borra todos los elementos de un conjunto múltiple.  
  
```  
void clear();
```  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_clear.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
  
   ms1.insert( 1 );  
   ms1.insert( 2 );  
  
   cout << "The size of the multiset is initially "  
        << ms1.size( ) << "." << endl;  
  
   ms1.clear( );  
   cout << "The size of the multiset after clearing is "   
        << ms1.size( ) << "." << endl;  
}  
```  
  
```Output  
The size of the multiset is initially 2.  
The size of the multiset after clearing is 0.  
```  
  
##  <a name="const_iterator"></a> multiset::const_iterator  
 Un tipo que proporciona un iterador bidireccional que puede leer un elemento **const** del conjunto múltiple.  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo `const_iterator` no se puede utilizar para modificar el valor de un elemento.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [begin](#begin) para obtener un ejemplo que usa `const_iterator`.  
  
##  <a name="const_pointer"></a> multiset::const_pointer  
 Un tipo que proporciona un puntero a un elemento **const** en un conjunto múltiple.  
  
```  
typedef typename allocator_type::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo `const_pointer` no se puede utilizar para modificar el valor de un elemento.  
  
 En la mayoría de los casos, se debe usar un elemento [iterator](#iterator) para obtener acceso a los elementos de un objeto multiset.  
  
##  <a name="const_reference"></a> multiset::const_reference  
 Un tipo que proporciona una referencia a un elemento **const** almacenado en un conjunto múltiple para leer operaciones **const** y realizarlas.  
  
```  
typedef typename allocator_type::const_reference const_reference;  
```  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_const_ref.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> ms1;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the 1st element  
   const int &Ref1 = *ms1.begin( );  
  
   cout << "The first element in the multiset is "  
        << Ref1 << "." << endl;  
  
   // The following line would cause an error because the   
   // const_reference cannot be used to modify the multiset  
   // Ref1 = Ref1 + 5;  
}  
```  
  
```Output  
The first element in the multiset is 10.  
```  
  
##  <a name="const_reverse_iterator"></a> multiset::const_reverse_iterator  
 Un tipo que proporciona un iterador bidireccional que puede leer cualquier elemento **const** del conjunto múltiple.  
  
```  
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo `const_reverse_iterator` no puede modificar el valor de un elemento y se usa para iterar en el conjunto múltiple en orden inverso.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [rend](#rend) para obtener un ejemplo de cómo declarar y usar `const_reverse_iterator`.  
  
##  <a name="count"></a> multiset::count  
 Devuelve el número de elementos de un conjunto múltiple cuya clave coincide con una clave especificada por un parámetro.  
  
```  
size_type count(const Key& key) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Clave de los elementos del conjunto múltiple que deben coincidir.  
  
### <a name="return-value"></a>Valor devuelto  
 Número de elementos del conjunto múltiple cuyo criterio de ordenación coincide con la clave de parámetro.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve el número de elementos *x* del intervalo  
  
 [ `lower_bound` (_ *Key* ), `upper_bound` (\_ *Key* ) ).  
  
### <a name="example"></a>Ejemplo  
  En el ejemplo siguiente se muestra el uso de la función miembro multiset::count.  
  
```  
// multiset_count.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    multiset<int> ms1;  
    multiset<int>::size_type i;  
  
    ms1.insert(1);  
    ms1.insert(1);  
    ms1.insert(2);  
  
    // Elements do not need to be unique in multiset,  
    // so duplicates are allowed and counted.  
    i = ms1.count(1);  
    cout << "The number of elements in ms1 with a sort key of 1 is: "  
         << i << "." << endl;  
  
    i = ms1.count(2);  
    cout << "The number of elements in ms1 with a sort key of 2 is: "  
         << i << "." << endl;  
  
    i = ms1.count(3);  
    cout << "The number of elements in ms1 with a sort key of 3 is: "  
         << i << "." << endl;  
}  
```  
  
```Output  
The number of elements in ms1 with a sort key of 1 is: 2.  
The number of elements in ms1 with a sort key of 2 is: 1.  
The number of elements in ms1 with a sort key of 3 is: 0.  
```  
  
##  <a name="crbegin"></a> multiset::crbegin  
 Devuelve un iterador const que direcciona el primer elemento de un conjunto múltiple invertido.  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador const bidireccional invertido que direcciona el primer elemento de un conjunto múltiple invertido o que direcciona lo que habría sido el último elemento del conjunto múltiple sin invertir.  
  
### <a name="remarks"></a>Comentarios  
 `crbegin` se usa con un conjunto múltiple invertido igual que begin se usa con un conjunto múltiple.  
  
 Con el valor devuelto de `crbegin`, el objeto de conjunto múltiple no se puede modificar.  
  
 `crbegin` puede usarse para iterar un conjunto múltiple hacia atrás.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_crbegin.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int>::const_reverse_iterator ms1_crIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   ms1_crIter = ms1.crbegin( );  
   cout << "The first element in the reversed multiset is "  
        << *ms1_crIter << "." << endl;  
}  
```  
  
```Output  
The first element in the reversed multiset is 30.  
```  
  
##  <a name="crend"></a> multiset::crend  
 Devuelve un iterador const que se dirige a la ubicación que sigue al último elemento de un conjunto múltiple invertido.  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador constante bidireccional inverso que se dirige a la ubicación siguiente al último elemento de un conjunto múltiple invertido (la ubicación que había precedido al primer elemento del conjunto múltiple sin invertir).  
  
### <a name="remarks"></a>Comentarios  
 `crend` se usa con un conjunto múltiple invertido igual que [end](#end) se usa con un conjunto múltiple.  
  
 Con el valor devuelto de `crend`, el objeto multiset no se puede modificar.  
  
 Se puede usar `crend` para comprobar si un iterador inverso ha llegado al final de su conjunto múltiple.  
  
 El valor devuelto por `crend` no se debe desreferenciar.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_crend.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main() {  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int>::const_reverse_iterator ms1_crIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   ms1_crIter = ms1.crend( ) ;  
   ms1_crIter--;  
   cout << "The last element in the reversed multiset is "  
        << *ms1_crIter << "." << endl;  
}  
```  
  
##  <a name="difference_type"></a> multiset::difference_type  
 Un tipo entero con signo que se puede usar para representar el número de elementos de un conjunto múltiple en un intervalo entre elementos a los que apuntan los iteradores.  
  
```  
typedef typename allocator_type::difference_type difference_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El `difference_type` es el tipo devuelto al restar o incrementar los iteradores del contenedor. `difference_type` se suele usar para representar el número de elementos que hay en el intervalo [ `first`, `last`) entre los iteradores `first` y `last`. Incluye el elemento al que apunta `first` y el intervalo de elementos que abarca hasta el elemento al que apunta `last` sin incluirlo.  
  
 Tenga en cuenta que, aunque `difference_type` está disponible para todos los iteradores que cumplen los requisitos de un iterador de entrada, incluida la clase de iteradores bidireccionales admitida por los contenedores reversibles como set, solo los iteradores de acceso aleatorio proporcionados por un contenedor de acceso aleatorio, como vector, admiten la resta entre iteradores.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <set>  
#include <algorithm>  
  
int main( )  
{  
   using namespace std;  
  
   multiset <int> ms1;  
   multiset <int>::iterator ms1_Iter, ms1_bIter, ms1_eIter;  
  
   ms1.insert( 20 );  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
  
   ms1_bIter = ms1.begin( );  
   ms1_eIter = ms1.end( );  
  
   multiset <int>::difference_type   df_typ5, df_typ10, df_typ20;  
  
   df_typ5 = count( ms1_bIter, ms1_eIter, 5 );  
   df_typ10 = count( ms1_bIter, ms1_eIter, 10 );  
   df_typ20 = count( ms1_bIter, ms1_eIter, 20 );  
  
   // The keys, and hence the elements, of a multiset are not unique  
   cout << "The number '5' occurs " << df_typ5  
        << " times in multiset ms1.\n";  
   cout << "The number '10' occurs " << df_typ10  
        << " times in multiset ms1.\n";  
   cout << "The number '20' occurs " << df_typ20  
        << " times in multiset ms1.\n";  
  
   // Count the number of elements in a multiset   
   multiset <int>::difference_type  df_count = 0;  
   ms1_Iter = ms1.begin( );  
   while ( ms1_Iter != ms1_eIter)  
   {  
      df_count++;  
      ms1_Iter++;  
   }  
  
   cout << "The number of elements in the multiset ms1 is: "   
        << df_count << "." << endl;  
}  
```  
  
```Output  
The number '5' occurs 0 times in multiset ms1.  
The number '10' occurs 1 times in multiset ms1.  
The number '20' occurs 2 times in multiset ms1.  
The number of elements in the multiset ms1 is: 3.  
```  
  
##  <a name="emplace"></a> multiset::emplace  
 Inserta un elemento construido en contexto (no se realiza ninguna operación de copia o de movimiento), con una sugerencia de colocación.  
  
```  
template <class... Args>  
iterator emplace(Args&&... args);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`args`|Argumentos reenviados para construir un elemento que se va a insertar en el conjunto múltiple.|  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador al elemento recién insertado.  
  
### <a name="remarks"></a>Comentarios  
 Esta función no invalida ninguna referencia a elementos contenedores, pero puede invalidar todos los iteradores al contenedor.  
  
 Durante el emplazamiento, si se produce una excepción, el estado del contenedor no se modifica.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_emplace.cpp  
// compile with: /EHsc  
#include <set>  
#include <string>  
#include <iostream>  
  
using namespace std;  
  
template <typename S> void print(const S& s) {  
    cout << s.size() << " elements: ";  
  
    for (const auto& p : s) {  
        cout << "(" << p << ") ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    multiset<string> s1;  
  
    s1.emplace("Anna");  
    s1.emplace("Bob");  
    s1.emplace("Carmine");  
  
    cout << "multiset modified, now contains ";  
    print(s1);  
    cout << endl;  
  
    s1.emplace("Bob");  
  
    cout << "multiset modified, now contains ";  
    print(s1);  
    cout << endl;  
}  
  
```  
  
##  <a name="emplace_hint"></a> multiset::emplace_hint  
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
|`args`|Argumentos reenviados para construir un elemento que se va a insertar en el conjunto múltiple.|  
|`where`|Lugar donde se va a iniciar la búsqueda del punto de inserción correcto. (Si ese punto precede inmediatamente a `where`, la inserción se puede realizar en tiempo constante amortizado en lugar de en tiempo logarítmico).|  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador al elemento recién insertado.  
  
### <a name="remarks"></a>Comentarios  
 Esta función no invalida ninguna referencia a elementos contenedores, pero puede invalidar todos los iteradores al contenedor.  
  
 Durante el emplazamiento, si se produce una excepción, el estado del contenedor no se modifica.  
  
 Para obtener un ejemplo de código, vea [set::emplace_hint](../standard-library/set-class.md#emplace_hint).  
  
##  <a name="empty"></a> multiset::empty  
 Prueba si un conjunto múltiple está vacío.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el conjunto múltiple está vacío; **False** si el conjunto múltiple no está vacío.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_empty.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> ms1, ms2;  
   ms1.insert ( 1 );  
  
   if ( ms1.empty( ) )  
      cout << "The multiset ms1 is empty." << endl;  
   else  
      cout << "The multiset ms1 is not empty." << endl;  
  
   if ( ms2.empty( ) )  
      cout << "The multiset ms2 is empty." << endl;  
   else  
      cout << "The multiset ms2 is not empty." << endl;  
}  
```  
  
```Output  
The multiset ms1 is not empty.  
The multiset ms2 is empty.  
```  
  
##  <a name="end"></a> multiset::end  
 Devuelve el iterador más allá del final.  
  
```  
const_iterator end() const;

 
 
iterator end();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El iterador siguiente al final. Si el conjunto múltiple está vacío, `multiset::end() == multiset::begin()`.  
  
### <a name="remarks"></a>Comentarios  
 **end** se usa para probar si un iterador ha sobrepasado el final de su conjunto múltiple.  
  
 El valor devuelto por **end** no se debe desreferenciar.  
  
 Para obtener un ejemplo de código, vea [multiset::find](#find).  
  
##  <a name="equal_range"></a> multiset::equal_range  
 Devuelve un par de iteradores, respectivamente, al primer elemento de un conjunto múltiple cuya clave es mayor que una clave especificada y al primer elemento del conjunto múltiple cuya clave es igual o mayor que la clave especificada.  
  
```  
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 La clave de argumento que se comparará con la clave de ordenación de un elemento del conjunto múltiple que se está buscando.  
  
### <a name="return-value"></a>Valor devuelto  
 Un par de iteradores donde el primero es el elemento [lower_bound](#lower_bound) de la clave y el segundo es el elemento [upper_bound](#upper_bound) de la clave.  
  
 Para tener acceso al primer iterador de un par `pr` devuelto por la función miembro, use `pr`. **first** y para desreferenciar el iterador de límite inferior, use \*( `pr`. **first**). Para tener acceso al segundo iterador de un par `pr` devuelto por la función miembro, use `pr`. **second** y para desreferenciar el iterador de límite superior, use \*( `pr`. **second**).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_equal_range.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;      
   typedef multiset<int, less<int> > IntSet;  
   IntSet ms1;  
   multiset <int> :: const_iterator ms1_RcIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   pair <IntSet::const_iterator, IntSet::const_iterator> p1, p2;  
   p1 = ms1.equal_range( 20 );  
  
   cout << "The upper bound of the element with "  
        << "a key of 20 in the multiset ms1 is: "  
        << *( p1.second ) << "." << endl;  
  
   cout << "The lower bound of the element with "  
        << "a key of 20 in the multiset ms1 is: "  
        << *( p1.first ) << "." << endl;  
  
   // Compare the upper_bound called directly   
   ms1_RcIter = ms1.upper_bound( 20 );  
   cout << "A direct call of upper_bound( 20 ) gives "  
        << *ms1_RcIter << "," << endl  
        << "matching the 2nd element of the pair"  
        << " returned by equal_range( 20 )." << endl;  
  
   p2 = ms1.equal_range( 40 );  
  
   // If no match is found for the key,  
   // both elements of the pair return end( )  
   if ( ( p2.first == ms1.end( ) ) && ( p2.second == ms1.end( ) ) )  
      cout << "The multiset ms1 doesn't have an element "  
              << "with a key less than 40." << endl;  
   else  
      cout << "The element of multiset ms1 with a key >= 40 is: "  
                << *( p1.first ) << "." << endl;  
}  
```  
  
```Output  
The upper bound of the element with a key of 20 in the multiset ms1 is: 30.  
The lower bound of the element with a key of 20 in the multiset ms1 is: 20.  
A direct call of upper_bound( 20 ) gives 30,  
matching the 2nd element of the pair returned by equal_range( 20 ).  
The multiset ms1 doesn't have an element with a key less than 40.  
```  
  
##  <a name="erase"></a> multiset::erase  
 Quita un elemento o un intervalo de elementos de un conjunto múltiple de las posiciones especificadas o quita los elementos que coinciden con una clave especificada.  
  
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
 Valor de clave de los elementos que se van a quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 Para las dos primeras funciones miembro, iterador bidireccional que designa el primer elemento que permanece más allá de los elementos quitados, o un elemento que es el final del conjunto múltiple si no existe ese elemento.  
  
 Para la tercera función miembro, devuelve el número de elementos que se han quitado del conjunto múltiple.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener un ejemplo de código, vea [set::erase](../standard-library/set-class.md#erase).  
  
##  <a name="find"></a> multiset::find  
 Devuelve un iterador que hace referencia a la ubicación de un elemento de un conjunto múltiple que tiene una clave equivalente a una clave especificada.  
  
```  
iterator find(const Key& key);

 
const_iterator find(const Key& key) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 El valor de la clave con el que debe coincidir el criterio de ordenación de un elemento del conjunto múltiple en el que se buscará.  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador que hace referencia a la ubicación de un elemento con una clave especificada, o la ubicación siguiente al último elemento del conjunto múltiple (`multiset::end()`) si no se encuentra ninguna coincidencia con la clave.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve un iterador que hace referencia a un elemento del conjunto múltiple cuya clave es equivalente al argumento `key` de un predicado binario que induce a una ordenación basada en una relación de comparabilidad de menor que.  
  
 Si el valor devuelto de **find** se asigna a **const_iterator**, el objeto multiset no se puede modificar. Si el valor devuelto de **find** se asigna a un elemento **iterator**, el objeto multiset se puede modificar.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// compile with: /EHsc /W4 /MTd  
#include <set>  
#include <iostream>  
#include <vector>  
#include <string>  
  
using namespace std;  
  
template <typename T> void print_elem(const T& t) {  
    cout << "(" << t << ") ";  
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
    multiset<int> s1({ 40, 45 });  
    cout << "The starting multiset s1 is: " << endl;  
    print_collection(s1);  
  
    vector<int> v;  
    v.push_back(43);  
    v.push_back(41);  
    v.push_back(46);  
    v.push_back(42);  
    v.push_back(44);  
    v.push_back(44); // attempt a duplicate  
  
    cout << "Inserting the following vector data into s1: " << endl;  
    print_collection(v);  
  
    s1.insert(v.begin(), v.end());  
  
    cout << "The modified multiset s1 is: " << endl;  
    print_collection(s1);  
    cout << endl;  
    findit(s1, 45);  
    findit(s1, 6);  
}  
```  
  
##  <a name="get_allocator"></a> multiset::get_allocator  
 Devuelve una copia del objeto de asignador usado para construir el conjunto múltiple.  
  
```  
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El asignador usado por el conjunto múltiple.  
  
### <a name="remarks"></a>Comentarios  
 Los asignadores de la clase multiset especifican cómo la clase administra el almacenamiento. Los asignadores predeterminados proporcionados con las clases contenedoras de la biblioteca estándar de C++ son suficientes para la mayoría de las necesidades de programación. La escritura y el uso de sus propias clases de asignador son temas avanzados de C++.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_get_allocator.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int>::allocator_type ms1_Alloc;  
   multiset <int>::allocator_type ms2_Alloc;  
   multiset <double>::allocator_type ms3_Alloc;  
   multiset <int>::allocator_type ms4_Alloc;  
  
   // The following lines declare objects  
   // that use the default allocator.  
   multiset <int> ms1;  
   multiset <int, allocator<int> > ms2;  
   multiset <double, allocator<double> > ms3;  
  
   cout << "The number of integers that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << ms2.max_size( ) << "." << endl;  
  
   cout << "The number of doubles that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << ms3.max_size( ) <<  "." << endl;  
  
   // The following lines create a multiset ms4  
   // with the allocator of multiset ms1  
   ms1_Alloc = ms1.get_allocator( );  
   multiset <int> ms4( less<int>( ), ms1_Alloc );  
   ms4_Alloc = ms4.get_allocator( );  
  
   // Two allocators are interchangeable if  
   // storage allocated from each can be  
   // deallocated with the other  
   if( ms1_Alloc == ms4_Alloc )     
   {  
      cout << "Allocators are interchangeable."  
           << endl;     
   }  
   else     
   {  
      cout << "Allocators are not interchangeable."  
           << endl;     
   }  
}  
```  
  
##  <a name="insert"></a> multiset::insert  
 Inserta un elemento o un intervalo de elementos en un multiset.  
  
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
|`Val`|Valor de un elemento que se va a insertar en el multiset.|  
|`Where`|Lugar donde se va a iniciar la búsqueda del punto de inserción correcto. (Si ese punto precede inmediatamente a `Where`, la inserción se puede realizar en tiempo constante amortizado en lugar de en tiempo logarítmico).|  
|`ValTy`|Parámetro de plantilla que especifica el tipo de argumento que el conjunto múltiple puede usar para construir un elemento de [value_type](../standard-library/map-class.md#value_type) y realiza un reenvío directo de `Val` como argumento.|  
|`First`|Posición del primer elemento que se va a copiar.|  
|`Last`|Posición situada más allá del último elemento que se va a copiar.|  
|`InputIterator`|Argumento de la función de plantilla que cumple los requisitos de un [iterador de entrada](../standard-library/input-iterator-tag-struct.md) que apunta a elementos de un tipo que se puede usar para crear objetos [value_type](../standard-library/map-class.md#value_type).|  
|`IList`|El elemento [initializer_list](../standard-library/initializer-list.md) del que se van a copiar los elementos.|  
  
### <a name="return-value"></a>Valor devuelto  
 Las funciones miembro de inserción de un solo elemento, (1) y (2), devuelven un iterador a la posición donde se insertó el nuevo elemento en el multiset.  
  
 Las funciones miembro de inserción de un solo elemento con sugerencia, (3) y (4), devuelven un iterador que apunta a la posición donde se insertó el nuevo elemento en el multiset.  
  
### <a name="remarks"></a>Comentarios  
 Esta función no invalida ningún puntero ni ninguna referencia, pero puede invalidar todos los iteradores al contenedor.  
  
 Durante la inserción de un solo elemento, si se produce una excepción, no se modifica el estado del contenedor. Durante la inserción de varios elementos, si se produce una excepción, el contenedor se deja en un estado sin especificar pero válido.  
  
 El objeto [value_type](../standard-library/map-class.md#value_type) de un contenedor es una definición de tipo que pertenece al contenedor y, para set, `multiset<V>::value_type` es de tipo `const V`.  
  
 La función miembro de intervalo (5) inserta la secuencia de valores de elemento en un multiset que corresponde a cada elemento direccionado por un iterador en el intervalo `[First, Last)`; por tanto, `Last` no se inserta. La función miembro de contenedor `end()` hace referencia a la posición situada justo después del último elemento del contenedor; por ejemplo, la instrucción `s.insert(v.begin(), v.end());` inserta todos los elementos de `v` en `s`.  
  
 La función miembro de lista de inicializadores (6) usa [initializer_list](../standard-library/initializer-list.md) para copiar los elementos al conjunto múltiple.  
  
 Para la inserción de un elemento construido en contexto (es decir, no se realiza ninguna operación de copia o movimiento), vea [multiset::emplace](#emplace) y [multiset::emplace_hint](#emplace_hint).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_insert.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
#include <string>  
#include <vector>  
  
using namespace std;  
  
template <typename S> void print(const S& s) {  
    cout << s.size() << " elements: ";  
  
    for (const auto& p : s) {  
        cout << "(" << p << ") ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
  
    // insert single values   
    multiset<int> s1;  
    // call insert(const value_type&) version  
    s1.insert({ 1, 10 });  
    // call insert(ValTy&&) version   
    s1.insert(20);  
  
    cout << "The original multiset values of s1 are:" << endl;  
    print(s1);  
  
    // intentionally attempt a duplicate, single element  
    s1.insert(1);  
    cout << "The modified multiset values of s1 are:" << endl;  
    print(s1);  
    cout << endl;  
  
    // single element, with hint  
    s1.insert(s1.end(), 30);  
    cout << "The modified multiset values of s1 are:" << endl;  
    print(s1);  
    cout << endl;  
  
    // The templatized version inserting a jumbled range  
    multiset<int> s2;  
    vector<int> v;  
    v.push_back(43);  
    v.push_back(294);  
    v.push_back(41);  
    v.push_back(330);  
    v.push_back(42);  
    v.push_back(45);  
  
    cout << "Inserting the following vector data into s2:" << endl;  
    print(v);  
  
    s2.insert(v.begin(), v.end());  
  
    cout << "The modified multiset values of s2 are:" << endl;  
    print(s2);  
    cout << endl;  
  
    // The templatized versions move-constructing elements  
    multiset<string>  s3;  
    string str1("blue"), str2("green");  
  
    // single element  
    s3.insert(move(str1));  
    cout << "After the first move insertion, s3 contains:" << endl;  
    print(s3);  
  
    // single element with hint  
    s3.insert(s3.end(), move(str2));  
    cout << "After the second move insertion, s3 contains:" << endl;  
    print(s3);  
    cout << endl;  
  
    multiset<int> s4;  
    // Insert the elements from an initializer_list  
    s4.insert({ 4, 44, 2, 22, 3, 33, 1, 11, 5, 55 });  
    cout << "After initializer_list insertion, s4 contains:" << endl;  
    print(s4);  
    cout << endl;  
}  
  
```  
  
##  <a name="iterator"></a> multiset::iterator  
 Un tipo que proporciona un [iterador bidireccional](../standard-library/bidirectional-iterator-tag-struct.md) constante que puede leer cualquier elemento de un conjunto múltiple.  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [begin](#begin) para obtener un ejemplo de cómo declarar y usar **iterator**.  
  
##  <a name="key_comp"></a> multiset::key_comp  
 Recupera una copia del objeto de comparación que se ha usado para ordenar claves de un conjunto múltiple.  
  
```  
key_compare key_comp() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el objeto de función que usa un conjunto múltiple para ordenar sus elementos, que es el parámetro de plantilla `Compare`.  
  
 Para obtener más información sobre `Compare`, vea la sección Comentarios del tema [multiset (Clase)](../standard-library/multiset-class.md).  
  
### <a name="remarks"></a>Comentarios  
 El objeto almacenado define la función miembro:  
  
 **bool operator**( **const Key&** *x*, **const Key&** *y*);  
  
 que devuelve True si *x* precede estrictamente a *y* en el criterio de ordenación.  
  
 Tenga en cuenta que [key_compare](#key_compare) y [value_compare](#value_compare) son sinónimos para el parámetro de plantilla `Compare`. Ambos tipos se proporcionan para las clases set y multiset, donde son idénticos, para la compatibilidad con las clases map y multimap, donde son distintos.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_key_comp.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   multiset <int, less<int> > ms1;  
   multiset <int, less<int> >::key_compare kc1 = ms1.key_comp( ) ;  
   bool result1 = kc1( 2, 3 ) ;  
   if( result1 == true )     
   {  
      cout << "kc1( 2,3 ) returns value of true, "  
           << "where kc1 is the function object of s1."  
           << endl;  
   }  
   else     
   {  
      cout << "kc1( 2,3 ) returns value of false "  
           << "where kc1 is the function object of ms1."  
           << endl;  
   }  
  
   multiset <int, greater<int> > ms2;  
   multiset <int, greater<int> >::key_compare kc2 = ms2.key_comp( ) ;  
   bool result2 = kc2( 2, 3 ) ;  
   if( result2 == true )     
   {  
      cout << "kc2( 2,3 ) returns value of true, "  
           << "where kc2 is the function object of ms2."  
           << endl;  
   }  
   else     
   {  
      cout << "kc2( 2,3 ) returns value of false, "  
           << "where kc2 is the function object of ms2."  
           << endl;  
   }  
}  
```  
  
```Output  
kc1( 2,3 ) returns value of true, where kc1 is the function object of s1.  
kc2( 2,3 ) returns value of false, where kc2 is the function object of ms2.  
```  
  
##  <a name="key_compare"></a> multiset::key_compare  
 Un tipo que proporciona un objeto de función que puede comparar dos criterios de ordenación para determinar el orden relativo de dos elementos en el conjunto múltiple.  
  
```  
typedef Compare key_compare;  
```  
  
### <a name="remarks"></a>Comentarios  
 **key_compare** es un sinónimo del parámetro de plantilla `Compare`.  
  
 Para obtener más información sobre `Compare`, vea la sección Comentarios del tema [multiset (Clase)](../standard-library/multiset-class.md).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [key_comp](#key_comp) para obtener un ejemplo de cómo declarar y usar `key_compare`.  
  
##  <a name="key_type"></a> multiset::key_type  
 Un tipo que proporciona un objeto de función que puede comparar criterios de ordenación para determinar el orden relativo de dos elementos en el conjunto múltiple.  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 `key_type` es un sinónimo del parámetro de plantilla `Key`.  
  
 Para obtener más información sobre `Key`, vea la sección Comentarios del tema [multiset (Clase)](../standard-library/multiset-class.md).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [value_type](#value_type) para obtener un ejemplo de cómo declarar y usar `key_type`.  
  
##  <a name="lower_bound"></a> multiset::lower_bound  
 Devuelve un iterador al primer elemento de un conjunto múltiple cuyo valor de clave es igual o mayor que el de una clave especificada.  
  
```  
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 La clave de argumento que se comparará con la clave de ordenación de un elemento del conjunto múltiple que se está buscando.  
  
### <a name="return-value"></a>Valor devuelto  
 Un **iterador** o `const_iterator` que se dirige a la ubicación de un elemento en un conjunto múltiple que tiene una clave igual o mayor que la clave de argumento, o que se dirige a la ubicación siguiente al último elemento del conjunto múltiple si no se encuentra ninguna coincidencia con la clave.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_lower_bound.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int> :: const_iterator ms1_AcIter, ms1_RcIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   ms1_RcIter = ms1.lower_bound( 20 );  
   cout << "The element of multiset ms1 with a key of 20 is: "  
        << *ms1_RcIter << "." << endl;  
  
   ms1_RcIter = ms1.lower_bound( 40 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( ms1_RcIter == ms1.end( ) )  
      cout << "The multiset ms1 doesn't have an element "  
           << "with a key of 40." << endl;  
   else  
      cout << "The element of multiset ms1 with a key of 40 is: "  
           << *ms1_RcIter << "." << endl;  
  
   // The element at a specific location in the multiset can be   
   // found using a derefenced iterator addressing the location  
   ms1_AcIter = ms1.end( );  
   ms1_AcIter--;  
   ms1_RcIter = ms1.lower_bound( *ms1_AcIter );  
   cout << "The element of ms1 with a key matching "  
        << "that of the last element is: "  
        << *ms1_RcIter << "." << endl;  
}  
```  
  
```Output  
The element of multiset ms1 with a key of 20 is: 20.  
The multiset ms1 doesn't have an element with a key of 40.  
The element of ms1 with a key matching that of the last element is: 30.  
```  
  
##  <a name="max_size"></a> multiset::max_size  
 Devuelve la longitud máxima del conjunto múltiple.  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud máxima posible del conjunto múltiple.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_max_size.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int>::size_type i;  
  
   i = ms1.max_size( );     
   cout << "The maximum possible length "  
        << "of the multiset is " << i << "." << endl;  
}  
```  
  
##  <a name="multiset"></a> multiset::multiset  
 Construye un multiset que está vacío o que es una copia de todo o de parte de otro multiset.  
  
```  
multiset();

explicit multiset (
    const Compare& Comp);

multiset (
    const Compare& Comp,  
    const Allocator& Al);

multiset(
    const multiset& Right);

multiset(
    multiset&& Right);

multiset(
    initializer_list<Type> IList);

multiset(
    initializer_list<Type> IList,   
    const Compare& Comp);

multiset(
    initializer_list<Type> IList,   
    const Compare& Comp,   
    const Allocator& Al);

 
template <class InputIterator>  
multiset (
    InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
multiset (
    InputIterator First,  
    InputIterator Last,  
    const Compare& Comp);

template <class InputIterator>  
multiset (
    InputIterator First,  
    InputIterator Last,  
    const Compare& Comp,  
    const Allocator& Al);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`Al`|Clase de asignador de almacenamiento que se va a utilizar para este objeto multiset, que toma como valor predeterminado `Allocator`.|  
|`Comp`|Función de comparación de tipo `const Compare` que se utiliza para ordenar los elementos del multiset, que de forma predeterminada es `Compare`.|  
|`Right`|Multiset del que el multiset construido va a ser una copia.|  
|`First`|Posición del primer elemento en el intervalo de elementos que se va a copiar.|  
|`Last`|Posición del primer elemento más allá del intervalo de elementos que se va a copiar.|  
|`IList`|initializer_list de la que se van a copiar los elementos.|  
  
### <a name="remarks"></a>Comentarios  
 Todos los constructores almacenan un tipo de objeto de asignador que administra el almacenamiento en memoria del conjunto múltiple y que se puede devolver más tarde llamando a [get_allocator](#get_allocator). El parámetro de asignador se suele omitir en las declaraciones de clase y las macros de preprocesamiento que se utilizan para sustituir asignadores alternativos.  
  
 Todos los constructores inicializan su multiset.  
  
 Todos los constructores almacenan un objeto de función de tipo Compare que se usa para establecer un orden entre las claves del conjunto múltiple y que se puede devolver más tarde llamando a [key_comp](#key_comp).  
  
 Los tres primeros constructores especifican un conjunto múltiple inicial vacío, el segundo especifica el tipo de función de comparación (`Comp`) que se usará para establecer el orden de los elementos y el tercero especifica explícitamente el tipo de asignador (`Al`) que se va a usar. La palabra clave `explicit` suprime ciertas clases de conversión automática de tipos.  
  
 El cuarto constructor especifica una copia del multiset `Right`.  
  
 El quinto constructor especifica una copia del multiset moviendo `Right`.  
  
 Los constructores sexto, séptimo y octavos especifican una initializer_list de la que se van a copiar los elementos.  
  
 Los tres constructores siguientes copian el intervalo `[First, Last)` de un multiset especificando de forma cada vez más explícita el tipo de función de comparación y el asignador.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_ctor.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    //multiset <int>::iterator ms1_Iter, ms2_Iter, ms3_Iter;  
    multiset <int>::iterator ms4_Iter, ms5_Iter, ms6_Iter, ms7_Iter;  
  
    // Create an empty multiset ms0 of key type integer  
    multiset <int> ms0;  
  
    // Create an empty multiset ms1 with the key comparison  
    // function of less than, then insert 4 elements  
    multiset <int, less<int> > ms1;  
    ms1.insert(10);  
    ms1.insert(20);  
    ms1.insert(20);  
    ms1.insert(40);  
  
    // Create an empty multiset ms2 with the key comparison  
    // function of geater than, then insert 2 elements  
    multiset <int, less<int> > ms2;  
    ms2.insert(10);  
    ms2.insert(20);  
  
    // Create a multiset ms3 with the   
    // allocator of multiset ms1  
    multiset <int>::allocator_type ms1_Alloc;  
    ms1_Alloc = ms1.get_allocator();  
    multiset <int> ms3(less<int>(), ms1_Alloc);  
    ms3.insert(30);  
  
    // Create a copy, multiset ms4, of multiset ms1  
    multiset <int> ms4(ms1);  
  
    // Create a multiset ms5 by copying the range ms1[ first,  last)  
    multiset <int>::const_iterator ms1_bcIter, ms1_ecIter;  
    ms1_bcIter = ms1.begin();  
    ms1_ecIter = ms1.begin();  
    ms1_ecIter++;  
    ms1_ecIter++;  
    multiset <int> ms5(ms1_bcIter, ms1_ecIter);  
  
    // Create a multiset ms6 by copying the range ms4[ first,  last)  
    // and with the allocator of multiset ms2  
    multiset <int>::allocator_type ms2_Alloc;  
    ms2_Alloc = ms2.get_allocator();  
    multiset <int> ms6(ms4.begin(), ++ms4.begin(), less<int>(), ms2_Alloc);  
  
    cout << "ms1 =";  
    for (auto i : ms1)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "ms2 =";  
    for (auto i : ms2)  
        cout << " " << i;  
   cout << endl;  
  
   cout << "ms3 =";  
   for (auto i : ms3)  
       cout << " " << i;  
    cout << endl;  
  
    cout << "ms4 =";  
    for (auto i : ms4)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "ms5 =";  
    for (auto i : ms5)  
        cout << " " << i;  
    cout << endl;  
  
    cout << "ms6 =";  
    for (auto i : ms6)  
        cout << " " << i;  
    cout << endl;  
  
    // Create a multiset by moving ms5  
    multiset<int> ms7(move(ms5));  
    cout << "ms7 =";  
    for (auto i : ms7)  
        cout << " " << i;  
    cout << endl;  
  
    // Create a multiset with an initializer_list  
    multiset<int> ms8({1, 2, 3, 4});  
    cout << "ms8=";  
    for (auto i : ms8)  
        cout << " " << i;  
    cout << endl;  
}  
```  
  
##  <a name="op_eq"></a> multiset::operator=  
 Reemplaza los elementos de este `multiset` con elementos de otro `multiset`.  
  
```  
multiset& operator=(const multiset& right);

multiset& operator=(multiset&& right);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`right`|El objeto `multiset` del que se copian o mueven los elementos.|  
  
### <a name="remarks"></a>Comentarios  
 `operator=` copia o mueve los elementos de `right` en `multiset`, dependiendo del tipo de referencia (lvalue o rvalue) que se ha usado. Se descartan los elementos que estén en este `multiset` antes de que `operator=` se ejecute.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_operator_as.cpp  
// compile with: /EHsc  
#include <multiset>  
#include <iostream>  
  
int main( )  
   {  
   using namespace std;  
   multiset<int> v1, v2, v3;  
   multiset<int>::iterator iter;  
  
   v1.insert(10);  
  
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
  
##  <a name="pointer"></a> multiset::pointer  
 Un tipo que proporciona un puntero a un elemento de un conjunto múltiple.  
  
```  
typedef typename allocator_type::pointer pointer;  
```  
  
### <a name="remarks"></a>Comentarios  
 Se puede usar un tipo **pointer** para modificar el valor de un elemento.  
  
 En la mayoría de los casos, se debe usar un elemento [iterator](#iterator) para obtener acceso a los elementos de un objeto multiset.  
  
##  <a name="rbegin"></a> multiset::rbegin  
 Devuelve un iterador que direcciona el primer elemento en un conjunto múltiple invertido.  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador bidireccional invertido que direcciona el primer elemento de un conjunto múltiple invertido o que direcciona lo que habría sido el último elemento del conjunto múltiple sin invertir.  
  
### <a name="remarks"></a>Comentarios  
 `rbegin` se usa con un conjunto múltiple invertido igual que rbegin se usa con un conjunto múltiple.  
  
 Si el valor devuelto de `rbegin` se asigna a un `const_reverse_iterator`, el objeto del conjunto múltiple no puede modificarse. Si el valor devuelto de `rbegin` se asigna a un `reverse_iterator`, el objeto del conjunto múltiple puede modificarse.  
  
 `rbegin` puede usarse para iterar un conjunto múltiple hacia atrás.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_rbegin.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int>::iterator ms1_Iter;  
   multiset <int>::reverse_iterator ms1_rIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   ms1_rIter = ms1.rbegin( );  
   cout << "The first element in the reversed multiset is "  
        << *ms1_rIter << "." << endl;  
  
   // begin can be used to start an interation   
   // throught a multiset in a forward order  
   cout << "The multiset is:";  
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )  
      cout << " " << *ms1_Iter;  
   cout << endl;  
  
   // rbegin can be used to start an interation   
   // throught a multiset in a reverse order  
   cout << "The reversed multiset is:";  
   for ( ms1_rIter = ms1.rbegin( ) ; ms1_rIter != ms1.rend( ); ms1_rIter++ )  
      cout << " " << *ms1_rIter;  
   cout << endl;  
  
   // A multiset element can be erased by dereferencing to its key   
   ms1_rIter = ms1.rbegin( );  
   ms1.erase ( *ms1_rIter );  
  
   ms1_rIter = ms1.rbegin( );  
   cout << "After the erasure, the first element "  
        << "in the reversed multiset is "<< *ms1_rIter << "."   
        << endl;  
}  
```  
  
```Output  
The first element in the reversed multiset is 30.  
The multiset is: 10 20 30  
The reversed multiset is: 30 20 10  
After the erasure, the first element in the reversed multiset is 20.  
```  
  
##  <a name="reference"></a> multiset::reference  
 Un tipo que proporciona una referencia a un elemento almacenado en un conjunto múltiple.  
  
```  
typedef typename allocator_type::reference reference;  
```  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_ref.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
  
   // Declare and initialize a reference &Ref1 to the 1st element  
   const int &Ref1 = *ms1.begin( );  
  
   cout << "The first element in the multiset is "  
        << Ref1 << "." << endl;  
}  
```  
  
```Output  
The first element in the multiset is 10.  
```  
  
##  <a name="rend"></a> multiset::rend  
 Devuelve un iterador que se dirige a la ubicación que sigue al último elemento en un conjunto múltiple invertido.  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador bidireccional inverso que se dirige a la ubicación siguiente al último elemento de un conjunto múltiple invertido (la ubicación que había precedido al primer elemento del conjunto múltiple sin invertir).  
  
### <a name="remarks"></a>Comentarios  
 `rend` se usa con un conjunto múltiple invertido igual que [end](#end) se usa con un conjunto múltiple.  
  
 Si el valor devuelto de `rend` se asigna a un `const_reverse_iterator`, el objeto del conjunto múltiple no puede modificarse. Si el valor devuelto de `rend` se asigna a un `reverse_iterator`, el objeto del conjunto múltiple puede modificarse.  
  
 Se puede usar `rend` para comprobar si un iterador inverso ha llegado al final de su conjunto múltiple.  
  
 El valor devuelto por `rend` no se debe desreferenciar.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_rend.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main() {  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int>::iterator ms1_Iter;  
   multiset <int>::reverse_iterator ms1_rIter;  
   multiset <int>::const_reverse_iterator ms1_crIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   ms1_rIter = ms1.rend( ) ;  
   ms1_rIter--;  
   cout << "The last element in the reversed multiset is "  
        << *ms1_rIter << "." << endl;  
  
   // end can be used to terminate an interation   
   // throught a multiset in a forward order  
   cout << "The multiset is: ";  
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )  
      cout << *ms1_Iter << " ";  
   cout << "." << endl;  
  
   // rend can be used to terminate an interation   
   // throught a multiset in a reverse order  
   cout << "The reversed multiset is: ";  
   for ( ms1_rIter = ms1.rbegin( ) ; ms1_rIter != ms1.rend( ); ms1_rIter++ )  
      cout << *ms1_rIter << " ";  
   cout << "." << endl;  
  
   ms1_rIter = ms1.rend( );  
   ms1_rIter--;  
   ms1.erase ( *ms1_rIter );  
  
   ms1_rIter = ms1.rend( );  
   --ms1_rIter;  
   cout << "After the erasure, the last element in the "  
        << "reversed multiset is " << *ms1_rIter << "." << endl;  
}  
```  
  
##  <a name="reverse_iterator"></a> multiset::reverse_iterator  
 Un tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento en un conjunto múltiple invertido.  
  
```  
typedef std::reverse_iterator<iterator> reverse_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo `reverse_iterator` se usa para iterar en el conjunto múltiple en orden inverso.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [rbegin](#rbegin) para obtener un ejemplo de cómo declarar y usar `reverse_iterator`.  
  
##  <a name="size"></a> multiset::size  
 Devuelve el número de elementos del conjunto múltiple.  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud actual del mapa múltiple.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_size.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int> :: size_type i;  
  
   ms1.insert( 1 );  
   i = ms1.size( );  
   cout << "The multiset length is " << i << "." << endl;  
  
   ms1.insert( 2 );  
   i = ms1.size( );  
   cout << "The multiset length is now " << i << "." << endl;  
}  
```  
  
```Output  
The multiset length is 1.  
The multiset length is now 2.  
```  
  
##  <a name="size_type"></a> multiset::size_type  
 Un tipo entero sin signo que puede representar el número de elementos de un conjunto múltiple.  
  
```  
typedef typename allocator_type::size_type size_type;  
```  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [size](#size) para obtener un ejemplo de cómo declarar y usar `size_type`.  
  
##  <a name="swap"></a> multiset::swap  
 Intercambia los elementos de dos conjuntos múltiples.  
  
```  
void swap(
    multiset<Key, Compare, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 El conjunto múltiple de argumentos que proporciona los elementos que se van a intercambiar con el conjunto múltiple de destino.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro no invalida ninguna referencia, puntero o iterador que designan los elementos de los dos conjuntos múltiples cuyos elementos se intercambian.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_swap.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> ms1, ms2, ms3;  
   multiset <int>::iterator ms1_Iter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
   ms2.insert( 100 );  
   ms2.insert( 200 );  
   ms3.insert( 300 );  
  
   cout << "The original multiset ms1 is:";  
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )  
      cout << " " << *ms1_Iter;  
   cout << "." << endl;  
  
   // This is the member function version of swap  
   ms1.swap( ms2 );  
  
   cout << "After swapping with ms2, list ms1 is:";  
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )  
      cout << " " << *ms1_Iter;  
   cout << "." << endl;  
  
   // This is the specialized template version of swap  
   swap( ms1, ms3 );  
  
   cout << "After swapping with ms3, list ms1 is:";  
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )  
      cout << " " << *ms1_Iter;  
   cout   << "." << endl;  
}  
```  
  
```Output  
The original multiset ms1 is: 10 20 30.  
After swapping with ms2, list ms1 is: 100 200.  
After swapping with ms3, list ms1 is: 300.  
```  
  
##  <a name="upper_bound"></a> multiset::upper_bound  
 Devuelve un iterador al primer elemento de un conjunto múltiple con un valor de clave que es mayor que una clave especificada.  
  
```  
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 La clave de argumento que se comparará con la clave de ordenación de un elemento del conjunto múltiple que se está buscando.  
  
### <a name="return-value"></a>Valor devuelto  
 Un **iterador** o `const_iterator` que se dirige a la ubicación de un elemento de un conjunto múltiple que tiene una clave mayor que la clave de argumento o que se dirige a la ubicación siguiente al último elemento del conjunto múltiple si no se encuentra ninguna coincidencia con la clave.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_upper_bound.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   multiset <int> ms1;  
   multiset <int> :: const_iterator ms1_AcIter, ms1_RcIter;  
  
   ms1.insert( 10 );  
   ms1.insert( 20 );  
   ms1.insert( 30 );  
  
   ms1_RcIter = ms1.upper_bound( 20 );  
   cout << "The first element of multiset ms1 with a key greater "  
           << "than 20 is: " << *ms1_RcIter << "." << endl;  
  
   ms1_RcIter = ms1.upper_bound( 30 );  
  
   // If no match is found for the key, end( ) is returned  
   if ( ms1_RcIter == ms1.end( ) )  
      cout << "The multiset ms1 doesn't have an element "  
              << "with a key greater than 30." << endl;  
   else  
      cout << "The element of multiset ms1 with a key > 40 is: "  
           << *ms1_RcIter << "." << endl;  
  
   // The element at a specific location in the multiset can be   
   // found using a dereferenced iterator addressing the location  
   ms1_AcIter = ms1.begin( );  
   ms1_RcIter = ms1.upper_bound( *ms1_AcIter );  
   cout << "The first element of ms1 with a key greater than"  
        << endl << "that of the initial element of ms1 is: "  
        << *ms1_RcIter << "." << endl;  
}  
```  
  
```Output  
The first element of multiset ms1 with a key greater than 20 is: 30.  
The multiset ms1 doesn't have an element with a key greater than 30.  
The first element of ms1 with a key greater than  
that of the initial element of ms1 is: 20.  
```  
  
##  <a name="value_comp"></a> multiset::value_comp  
 Recupera una copia del objeto de comparación usado para ordenar valores de elemento de un conjunto múltiple.  
  
```  
value_compare value_comp() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el objeto de función que usa un conjunto múltiple para ordenar sus elementos, que es el parámetro de plantilla `Compare`.  
  
 Para obtener más información sobre `Compare`, vea la sección Comentarios del tema [multiset (Clase)](../standard-library/multiset-class.md).  
  
### <a name="remarks"></a>Comentarios  
 El objeto almacenado define la función miembro:  
  
 **bool operator**( **const Key&**`_xVal`, **const Key&**`_yVal`);  
  
 que devuelve True si `_xVal` precede y no es igual a `_yVal` en el criterio de ordenación.  
  
 Tenga en cuenta que [key_compare](#key_compare) y [value_compare](#value_compare) son sinónimos para el parámetro de plantilla `Compare`. Ambos tipos se proporcionan para las clases set y multiset, donde son idénticos, para la compatibilidad con las clases map y multimap, donde son distintos.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_value_comp.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   multiset <int, less<int> > ms1;  
   multiset <int, less<int> >::value_compare vc1 = ms1.value_comp( );  
   bool result1 = vc1( 2, 3 );  
   if( result1 == true )     
   {  
      cout << "vc1( 2,3 ) returns value of true, "  
           << "where vc1 is the function object of ms1."  
           << endl;  
   }  
   else     
   {  
      cout << "vc1( 2,3 ) returns value of false, "  
           << "where vc1 is the function object of ms1."  
           << endl;  
   }  
  
   set <int, greater<int> > ms2;  
   set<int, greater<int> >::value_compare vc2 = ms2.value_comp( );  
   bool result2 = vc2( 2, 3 );  
   if( result2 == true )     
   {  
      cout << "vc2( 2,3 ) returns value of true, "  
           << "where vc2 is the function object of ms2."  
           << endl;  
   }  
   else     
   {  
      cout << "vc2( 2,3 ) returns value of false, "  
           << "where vc2 is the function object of ms2."  
           << endl;  
   }  
}  
```  
  
```Output  
vc1( 2,3 ) returns value of true, where vc1 is the function object of ms1.  
vc2( 2,3 ) returns value of false, where vc2 is the function object of ms2.  
```  
  
##  <a name="value_compare"></a> multiset::value_compare  
 El tipo que proporciona un objeto de función que puede comparar dos claves de ordenación para determinar su orden relativo en el conjunto múltiple.  
  
```  
typedef key_compare value_compare;  
```  
  
### <a name="remarks"></a>Comentarios  
 `value_compare` es un sinónimo del parámetro de plantilla `Compare`.  
  
 Tenga en cuenta que [key_compare](#key_compare) y **value_compare** son sinónimos para el parámetro de plantilla `Compare`. Ambos tipos se proporcionan para las clases set y multiset, donde son idénticos, para la compatibilidad con las clases map y multimap, donde son distintos.  
  
 Para obtener más información sobre `Compare`, vea la sección Comentarios del tema [multiset (Clase)](../standard-library/multiset-class.md).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [value_comp](#value_comp) para obtener un ejemplo de cómo declarar y usar `value_compare`.  
  
##  <a name="value_type"></a> multiset::value_type  
 Un tipo que describe un objeto almacenado como un elemento de un conjunto múltiple en su capacidad como valor.  
  
```  
typedef Key value_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 `value_type` es un sinónimo del parámetro de plantilla `Key`.  
  
 Tenga en cuenta que [key_type](#key_type) y `value_type` son sinónimos para el parámetro de plantilla **Key**. Ambos tipos se proporcionan para las clases set y multiset, donde son idénticos, para la compatibilidad con las clases map y multimap, donde son distintos.  
  
 Para obtener más información sobre `Key`, vea la sección Comentarios del tema.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// multiset_value_type.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> ms1;  
   multiset <int>::iterator ms1_Iter;  
  
   multiset <int> :: value_type svt_Int;   // Declare value_type  
   svt_Int = 10;             // Initialize value_type  
  
   multiset <int> :: key_type skt_Int;   // Declare key_type  
   skt_Int = 20;             // Initialize key_type  
  
   ms1.insert( svt_Int );         // Insert value into s1  
   ms1.insert( skt_Int );         // Insert key into s1  
  
   // A multiset accepts key_types or value_types as elements  
   cout << "The multiset has elements:";  
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )  
      cout << " " << *ms1_Iter;  
   cout << "." << endl;  
}  
```  
  
```Output  
The multiset has elements: 10 20.  
```  
  
## <a name="see-also"></a>Vea también  
 [\<Miembros set>](http://msdn.microsoft.com/en-us/0c2d57c0-173f-4204-b579-c5f06aad8b95)   
 [Contenedores](../cpp/containers-modern-cpp.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)

