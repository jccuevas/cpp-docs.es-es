---
title: list (Clase)
ms.date: 11/04/2016
f1_keywords:
- list/std::list
- list/std::list::allocator_type
- list/std::list::const_iterator
- list/std::list::const_pointer
- list/std::list::const_reference
- list/std::list::const_reverse_iterator
- list/std::list::difference_type
- list/std::list::iterator
- list/std::list::pointer
- list/std::list::reference
- list/std::list::reverse_iterator
- list/std::list::size_type
- list/std::list::value_type
- list/std::list::assign
- list/std::list::back
- list/std::list::begin
- list/std::list::cbegin
- list/std::list::cend
- list/std::list::clear
- list/std::list::crbegin
- list/std::list::crend
- list/std::list::emplace
- list/std::list::emplace_back
- list/std::list::emplace_front
- list/std::list::empty
- list/std::list::end
- list/std::list::erase
- list/std::list::front
- list/std::list::get_allocator
- list/std::list::insert
- list/std::list::max_size
- list/std::list::merge
- list/std::list::pop_back
- list/std::list::pop_front
- list/std::list::push_back
- list/std::list::push_front
- list/std::list::rbegin
- list/std::list::remove
- list/std::list::remove_if
- list/std::list::rend
- list/std::list::resize
- list/std::list::reverse
- list/std::list::size
- list/std::list::sort
- list/std::list::splice
- list/std::list::swap
- list/std::list::unique
helpviewer_keywords:
- std::list [C++]
- std::list [C++], allocator_type
- std::list [C++], const_iterator
- std::list [C++], const_pointer
- std::list [C++], const_reference
- std::list [C++], const_reverse_iterator
- std::list [C++], difference_type
- std::list [C++], iterator
- std::list [C++], pointer
- std::list [C++], reference
- std::list [C++], reverse_iterator
- std::list [C++], size_type
- std::list [C++], value_type
- std::list [C++], assign
- std::list [C++], back
- std::list [C++], begin
- std::list [C++], cbegin
- std::list [C++], cend
- std::list [C++], clear
- std::list [C++], crbegin
- std::list [C++], crend
- std::list [C++], emplace
- std::list [C++], emplace_back
- std::list [C++], emplace_front
- std::list [C++], empty
- std::list [C++], end
- std::list [C++], erase
- std::list [C++], front
- std::list [C++], get_allocator
- std::list [C++], insert
- std::list [C++], max_size
- std::list [C++], merge
- std::list [C++], pop_back
- std::list [C++], pop_front
- std::list [C++], push_back
- std::list [C++], push_front
- std::list [C++], rbegin
- std::list [C++], remove
- std::list [C++], remove_if
- std::list [C++], rend
- std::list [C++], resize
- std::list [C++], reverse
- std::list [C++], size
- std::list [C++], sort
- std::list [C++], splice
- std::list [C++], swap
- std::list [C++], unique
ms.assetid: d3707f4a-10fd-444f-b856-f9ca2077c1cd
ms.openlocfilehash: d990efb7d4c363b8d8e38f42f9edac7eea0a3882
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413221"
---
# <a name="list-class"></a>list (Clase)

La biblioteca estándar de C++ es una clase de plantilla de contenedores de secuencias que mantienen sus elementos en disposición lineal y permiten realizar inserciones y eliminaciones de manera eficiente en cualquier ubicación de la secuencia. La secuencia se almacena como una lista de elementos vinculada de forma bidireccional, cada uno de los cuales contiene un miembro de algún tipo *Type*.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type, class Allocator= allocator<Type>>
class list
```

### <a name="parameters"></a>Parámetros

*Type*<br/>
El tipo de datos de elementos que se almacenará en la lista.

*Allocator*<br/>
El tipo que representa el objeto asignador almacenado que encapsula los detalles sobre la asignación y la desasignación de memoria de la lista. Este argumento es opcional y el valor predeterminado es **asignador**\<*tipo*>.

## <a name="remarks"></a>Comentarios

En general, la elección del tipo de contenedor se debe tomar según el tipo de búsqueda y de inserción que necesite la aplicación. Los vectores deben ser el contenedor preferido para administrar una secuencia cuando escasee el acceso aleatorio a algún elemento y solo sea necesario realizar inserciones o eliminaciones de elementos al final de una secuencia. El rendimiento del contenedor deque de la clase es superior cuando el acceso aleatorio es necesario y escasean las inserciones y eliminaciones al principio y al final de una secuencia.

Las funciones miembro de lista [merge](#merge), [reverse](#reverse), [unique](#unique), [remove](#remove) y [remove_if](#remove_if) se han optimizado para funcionar en objetos de lista y ofrecer una alternativa de alto rendimiento a sus equivalentes genéricos.

La reasignación de lista se realiza cuando una función miembro debe insertar o borrar elementos de la lista. En todos esos casos, solo los iteradores o las referencias que apuntan a partes borradas de la secuencia controlada dejan de ser válidas.

Incluya el encabezado estándar \<list> de la biblioteca estándar de C++ para definir la lista de clases de plantilla [container](../standard-library/stl-containers.md) y varias plantillas auxiliares.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[lista](#list)|Construye una lista de un tamaño específico, con elementos de un valor específico, con un `allocator` específico o como copia de alguna otra lista.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[allocator_type](#allocator_type)|Tipo que representa la clase `allocator` para un objeto de lista.|
|[const_iterator](#const_iterator)|Tipo que proporciona un iterador bidireccional que puede leer un elemento **const** de una lista.|
|[const_pointer](#const_pointer)|Un tipo que proporciona un puntero a un **const** elemento de una lista.|
|[const_reference](#const_reference)|Tipo que proporciona una referencia a un elemento **const** almacenado en una lista para leer operaciones **const** y realizarlas.|
|[const_reverse_iterator](#const_reverse_iterator)|Tipo que proporciona un iterador bidireccional que puede leer cualquier elemento **const** de una lista.|
|[difference_type](#difference_type)|Tipo que proporciona la diferencia entre dos iteradores que hacen referencia a elementos de la misma lista.|
|[iterator](#iterator)|Tipo que proporciona un iterador bidireccional que puede leer o modificar cualquier elemento de una lista.|
|[pointer](#pointer)|Tipo que proporciona un puntero a un elemento de una lista.|
|[reference](#reference)|Tipo que proporciona una referencia a un elemento **const** almacenado en una lista para leer operaciones **const** y realizarlas.|
|[reverse_iterator](#reverse_iterator)|Tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento de una lista invertida.|
|[size_type](#size_type)|Tipo que cuenta el número de elementos de una lista.|
|[value_type](#value_type)|Tipo que representa el tipo de datos almacenados en una lista.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[assign](#assign)|Borra elementos de una lista y copia un nuevo conjunto de elementos a la lista de destino.|
|[back](#back)|Devuelve una referencia al último elemento de una lista.|
|[begin](#begin)|Devuelve un iterador que dirige al primer elemento de una lista.|
|[cbegin](#cbegin)|Devuelve un iterador constante que dirige al primer elemento de una lista.|
|[cend](#cend)|Devuelve un iterador constante que dirige a la ubicación siguiente al último elemento de una lista.|
|[clear](#clear)|Borra todos los elementos de una lista.|
|[crbegin](#crbegin)|Devuelve un iterador constante que dirige al primer elemento de una lista invertida.|
|[crend](#crend)|Devuelve un iterador constante que dirige a la ubicación siguiente al último elemento de una lista invertida.|
|[emplace](#emplace)|Inserta en una posición especificada de una lista un elemento construido en contexto.|
|[emplace_back](#emplace_back)|Agrega un elemento construido en contexto al final de una lista.|
|[emplace_front](#emplace_front)|Agrega un elemento construido en contexto al principio de una lista.|
|[empty](#empty)|Comprueba si una lista está vacía.|
|[end](#end)|Devuelve un iterador que dirige a la ubicación que sigue al último elemento de una lista.|
|[erase](#erase)|Quita un elemento o un intervalo de elementos de una lista de las posiciones especificadas.|
|[front](#front)|Devuelve una referencia al primer elemento de una lista.|
|[get_allocator](#get_allocator)|Devuelve una copia del objeto `allocator` utilizado para construir una lista.|
|[insert](#insert)|Inserta un elemento, varios elementos o un intervalo de elementos en una lista en una posición especificada.|
|[max_size](#max_size)|Devuelve la longitud máxima de una lista.|
|[merge](#merge)|Quita los elementos de la lista de argumentos, los inserta en la lista de objetivo y ordena el nuevo conjunto combinado de elementos en orden ascendente o en otro orden especificado.|
|[pop_back](#pop_back)|Elimina el elemento situado al final de una lista.|
|[pop_front](#pop_front)|Elimina el elemento situado al principio de una lista.|
|[push_back](#push_back)|Agrega un elemento al final de una lista.|
|[push_front](#push_front)|Agrega un elemento al principio de una lista.|
|[rbegin](#rbegin)|Devuelve un iterador que dirige al primer elemento de una lista invertida.|
|[remove](#remove)|Borra los elementos de una lista que coinciden con un valor especificado.|
|[remove_if](#remove_if)|Borra elementos de la lista para la que se cumple un predicado especificado.|
|[rend](#rend)|Devuelve un iterador que dirige a la ubicación siguiente al último elemento de una lista invertida.|
|[resize](#resize)|Especifica un nuevo tamaño de una lista.|
|[reverse](#reverse)|Invierte el orden en que aparecen los elementos en una lista.|
|[size](#size)|Devuelve el número de elementos de una lista.|
|[sort](#sort)|Organiza los elementos de una lista en orden ascendente o con respecto a otra relación de ordenación.|
|[splice](#splice)|Quita los elementos de la lista de argumentos y los inserta en la lista de destino.|
|[swap](#swap)|Intercambia los elementos de dos listas.|
|[unique](#unique)|Quita de la lista los elementos duplicados adyacentes o los elementos adyacentes que cumplan algún otro predicado binario.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[list::operator=](#op_eq)|Reemplaza los elementos de la lista por una copia de otra lista.|

## <a name="requirements"></a>Requisitos

**Encabezado**: \<list>

## <a name="allocator_type"></a>  list::allocator_type

Tipo que representa la clase de asignador para un objeto de lista.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Comentarios

`allocator_type` es un sinónimo del parámetro de plantilla *asignador*.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [get_allocator](#get_allocator).

## <a name="assign"></a>  list::assign

Borra elementos de una lista y copia un nuevo conjunto de elementos a una lista de destino.

```cpp
void assign(
    size_type Count,
    const Type& Val);

void assign
    initializer_list<Type> IList);

template <class InputIterator>
void assign(
    InputIterator First,
    InputIterator Last);
```

### <a name="parameters"></a>Parámetros

*First*<br/>
Posición del primer elemento en el intervalo de elementos que se va a copiar de la lista de argumentos.

*Último*<br/>
Posición del primer elemento que se encuentra más allá del intervalo de elementos que se va a copiar de la lista de argumentos.

*Recuento*<br/>
Número de copias de un elemento que se va a insertar en la lista.

*Val*<br/>
Valor del elemento que se va a insertar en la lista.

*IList*<br/>
initializer_list que contiene los elementos que se van a insertar.

### <a name="remarks"></a>Comentarios

Después de borrar los elementos existentes en la lista de destino, assign inserta un intervalo especificado de elementos de la lista original o de otra lista en la lista de destino, o inserta copias de un nuevo elemento de un valor especificado en la lista de destino.

### <a name="example"></a>Ejemplo

```cpp
// list_assign.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main()
{
    using namespace std;
    list<int> c1, c2;
    list<int>::const_iterator cIter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign(++c2.begin(), c2.end());
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign(7, 4);
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign({ 10, 20, 30, 40 });
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 10 20 30c1 = 50 60c1 = 4 4 4 4 4 4 4c1 = 10 20 30 40
```

## <a name="back"></a>  list::back

Devuelve una referencia al último elemento de una lista.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Valor devuelto

El último elemento de la lista. Si la lista está vacía, el valor devuelto es indefinido.

### <a name="remarks"></a>Comentarios

Si el valor devuelto de `back` se asigna a un `const_reference`, el objeto de lista no se puede modificar. Si el valor devuelto de `back` se asigna a un `reference`, el objeto de lista se puede modificar.

Al compilar con [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definido como 1 o 2, se producirá un error en tiempo de ejecución si intenta obtener acceso a un elemento de una lista vacía.  Vea [Iteradores activados](../standard-library/checked-iterators.md) para obtener más información.

### <a name="example"></a>Ejemplo

```cpp
// list_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.back( );
   const int& ii = c1.front( );

   cout << "The last integer of c1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of c1 is " << ii << endl;
}
```

```Output
The last integer of c1 is 11
The next-to-last integer of c1 is 10
```

## <a name="begin"></a>  list::begin

Devuelve un iterador que dirige al primer elemento de una lista.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional que dirige al primer elemento de la lista o a la ubicación siguiente a una lista vacía.

### <a name="remarks"></a>Comentarios

Si el valor devuelto de `begin` se asigna a un `const_iterator`, no se puede modificar los elementos del objeto de lista. Si el valor devuelto de `begin` se asigna a un `iterator`, se pueden modificar los elementos del objeto de lista.

### <a name="example"></a>Ejemplo

```cpp
// list_begin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::const_iterator c1_cIter;

   c1.push_back( 1 );
   c1.push_back( 2 );

   c1_Iter = c1.begin( );
   cout << "The first element of c1 is " << *c1_Iter << endl;

*c1_Iter = 20;
   c1_Iter = c1.begin( );
   cout << "The first element of c1 is now " << *c1_Iter << endl;

   // The following line would be an error because iterator is const
   // *c1_cIter = 200;
}
```

```Output
The first element of c1 is 1
The first element of c1 is now 20
```

## <a name="cbegin"></a>  list::cbegin

Devuelve un **const** iterador que direcciona el primer elemento del intervalo.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Un **const** iterador de acceso bidireccional que apunta al primer elemento del intervalo o la ubicación situada más allá del final de un intervalo vacío (para un intervalo vacío, `cbegin() == cend()`).

### <a name="remarks"></a>Comentarios

Con el valor devuelto de `cbegin`, los elementos del intervalo no se pueden modificar.

Se puede usar esta función miembro en lugar de la función miembro `begin()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo, considere la posibilidad de `Container` sea modificable (no - **const**) contenedor de cualquier naturaleza que admite `begin()` y `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  list::cend

Devuelve un iterador `const` que direcciona la ubicación situada más allá del último elemento de un intervalo.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador `const` de acceso bidireccional que apunta justo después del final del intervalo.

### <a name="remarks"></a>Comentarios

`cend` se usa para probar si un iterador ha sobrepasado el final de su intervalo.

Se puede usar esta función miembro en lugar de la función miembro `end()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo, considere la posibilidad de `Container` sea modificable (no - **const**) contenedor de cualquier naturaleza que admite `end()` y `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

El valor devuelto por `cend` no se debe desreferenciar.

## <a name="clear"></a>  list::clear

Borra todos los elementos de una lista.

```cpp
void clear();
```

### <a name="example"></a>Ejemplo

```cpp
// list_clear.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main() {
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "The size of the list is initially " << c1.size( ) << endl;
   c1.clear( );
   cout << "The size of list after clearing is " << c1.size( ) << endl;
}
```

```Output
The size of the list is initially 3
The size of list after clearing is 0
```

## <a name="const_iterator"></a>  list::const_iterator

Tipo que proporciona un iterador bidireccional que puede leer un elemento **const** de una lista.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Comentarios

Un tipo `const_iterator` no se puede utilizar para modificar el valor de un elemento.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [back](#back).

## <a name="const_pointer"></a>  list::const_pointer

Proporciona un puntero a un **const** elemento de una lista.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Comentarios

Un tipo `const_pointer` no se puede utilizar para modificar el valor de un elemento.

En la mayoría de los casos, se debe usar [iterator](#iterator) para obtener acceso a los elementos de un objeto de lista.

## <a name="const_reference"></a>  list::const_reference

Tipo que proporciona una referencia a un elemento **const** almacenado en una lista para leer operaciones **const** y realizarlas.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Comentarios

Un tipo `const_reference` no se puede utilizar para modificar el valor de un elemento.

### <a name="example"></a>Ejemplo

```cpp
// list_const_ref.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const list <int> c2 = c1;
   const int &i = c2.front( );
   const int &j = c2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error because c2 is const
   // c2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a>  list::const_reverse_iterator

Tipo que proporciona un iterador bidireccional que puede leer cualquier elemento **const** de una lista.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Comentarios

Los tipos `const_reverse_iterator` no pueden modificar el valor de un elemento. Se utilizan para procesar una iteración en la lista en orden inverso.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [rbegin](#rbegin).

## <a name="crbegin"></a>  list::crbegin

Devuelve un iterador constante que dirige al primer elemento de una lista invertida.

```cpp
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional inverso const que direcciona el primer elemento de una lista invertida (o que direcciona lo que fue el último elemento de la `list` sin invertir).

### <a name="remarks"></a>Comentarios

`crbegin` se usa con una lista invertida igual que [list::begin](#begin) se usa con una `list`.

Con el valor devuelto de `crbegin`, el objeto de lista no se puede modificar. [list::rbegin](#rbegin) puede usarse para iterar una lista hacia atrás.

### <a name="example"></a>Ejemplo

```cpp
// list_crbegin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::const_reverse_iterator c1_crIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1_crIter = c1.crbegin( );
   cout << "The last element in the list is " << *c1_crIter << "." << endl;
}
```

```Output
The last element in the list is 30.
```

## <a name="crend"></a>  list::crend

Devuelve un iterador constante que dirige a la ubicación siguiente al último elemento de una lista invertida.

```cpp
const_reverse_iterator rend() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional inverso const que direcciona la ubicación que sigue al último elemento de una [list](../standard-library/list-class.md) invertida (la ubicación que había precedido al primer elemento de la `list` sin invertir).

### <a name="remarks"></a>Comentarios

`crend` se usa con una lista invertida igual que [list::end](#end) se usa con una `list`.

Con el valor devuelto de `crend`, el objeto `list` no se puede modificar.

Se puede utilizar `crend` para comprobar si un iterador inverso llegó al final de su `list`.

El valor devuelto por `crend` no se debe desreferenciar.

### <a name="example"></a>Ejemplo

```cpp
// list_crend.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::const_reverse_iterator c1_crIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_crIter = c1.crend( );
   c1_crIter --;  // Decrementing a reverse iterator moves it forward in
                 // the list (to point to the first element here)
   cout << "The first element in the list is: " << *c1_crIter << endl;
}
```

```Output
The first element in the list is: 10
```

## <a name="difference_type"></a>  list::difference_type

Tipo de entero con signo que se puede usar para representar el número de elementos de una lista en un intervalo entre elementos a los que apuntan los iteradores.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Comentarios

El `difference_type` es el tipo devuelto al restar o incrementar los iteradores del contenedor. `difference_type` se suele usar para representar el número de elementos que hay en el intervalo [ `first`, `last`) entre los iteradores `first` y `last`. Incluye el elemento al que apunta `first` y el intervalo de elementos que abarca hasta el elemento al que apunta `last` sin incluirlo.

Tenga en cuenta que, aunque `difference_type` está disponible para todos los iteradores que cumplen los requisitos de un iterador de entrada, incluida la clase de iteradores bidireccionales admitida por los contenedores reversibles como set, solo los iteradores de acceso aleatorio proporcionados por un contenedor de acceso aleatorio, como la [clase vector](../standard-library/vector-class.md), admiten la resta entre iteradores.

### <a name="example"></a>Ejemplo

```cpp
// list_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <list>
#include <algorithm>

int main( )
{
   using namespace std;

   list <int> c1;
   list <int>::iterator   c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

    list <int>::difference_type df_typ1, df_typ2, df_typ3;

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

## <a name="emplace"></a>  list::emplace

Inserta en una posición especificada de una lista un elemento construido en contexto.

```cpp
void emplace(iterator Where, Type&& val);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Where*|Posición de la [list](../standard-library/list-class.md) de destino donde se inserta el primer elemento.|
|*val*|El elemento que se agrega al final de la `list`.|

### <a name="remarks"></a>Comentarios

Si se lanza una excepción, la `list` se deja sin modificar y se vuelve a lanzar la excepción.

### <a name="example"></a>Ejemplo

```cpp
// list_emplace.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace(c2.begin(), move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="emplace_back"></a>  list::emplace_back

Agrega un elemento construido en contexto al final de una lista.

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*val*|Elemento que se agrega al final de [list](../standard-library/list-class.md).|

### <a name="remarks"></a>Comentarios

Si se lanza una excepción, la `list` se deja sin modificar y se vuelve a lanzar la excepción.

### <a name="example"></a>Ejemplo

```cpp
// list_emplace_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace_back( move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="emplace_front"></a>  list::emplace_front

Agrega un elemento construido en contexto al principio de una lista.

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*val*|Elemento que se agrega al principio de [list](../standard-library/list-class.md).|

### <a name="remarks"></a>Comentarios

Si se lanza una excepción, la `list` se deja sin modificar y se vuelve a lanzar la excepción.

### <a name="example"></a>Ejemplo

```cpp
// list_emplace_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="empty"></a>  list::empty

Comprueba si una lista está vacía.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valor devuelto

**True** si la lista está vacía, **False** si la lista no está vacía.

### <a name="example"></a>Ejemplo

```cpp
// list_empty.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   if ( c1.empty( ) )
      cout << "The list is empty." << endl;
   else
      cout << "The list is not empty." << endl;
}
```

```Output
The list is not empty.
```

## <a name="end"></a>  list::end

Devuelve un iterador que dirige a la ubicación que sigue al último elemento de una lista.

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional que dirige a la ubicación que sigue al último elemento de una lista. Si la lista está vacía, `list::end == list::begin`.

### <a name="remarks"></a>Comentarios

`end` se usa para comprobar si un iterador ha llegado al final de su lista.

### <a name="example"></a>Ejemplo

```cpp
// list_end.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_Iter = c1.end( );
   c1_Iter--;
   cout << "The last integer of c1 is " << *c1_Iter << endl;

   c1_Iter--;
*c1_Iter = 400;
   cout << "The new next-to-last integer of c1 is "
        << *c1_Iter << endl;

   // If a const iterator had been declared instead with the line:
   // list <int>::const_iterator c1_Iter;
   // an error would have resulted when inserting the 400

   cout << "The list is now:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
}
```

```Output
The last integer of c1 is 30
The new next-to-last integer of c1 is 400
The list is now: 10 400 30
```

## <a name="erase"></a>  list::erase

Quita un elemento o un intervalo de elementos de una lista de las posiciones especificadas.

```cpp
iterator erase(iterator Where);
iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>Parámetros

*Where*<br/>
Posición del elemento que se quitará de la lista.

*first*<br/>
Posición del primer elemento que se quitará de la lista.

*last*<br/>
Posición inmediatamente siguiente a la del último elemento que se quitará de la lista.

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional que designa el primer elemento restante después de los elementos quitados o, si no hay ningún elemento después, un puntero al final de la lista.

### <a name="remarks"></a>Comentarios

No se produce ninguna reasignación, así que los iteradores y las referencias solo dejarán de ser válidos para los elementos borrados.

`erase` nunca inicia una excepción.

### <a name="example"></a>Ejemplo

```cpp
// list_erase.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 40 );
   c1.push_back( 50 );
   cout << "The initial list is:";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;

   c1.erase( c1.begin( ) );
   cout << "After erasing the first element, the list becomes:";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;
   Iter = c1.begin( );
   Iter++;
   c1.erase( Iter, c1.end( ) );
   cout << "After erasing all elements but the first, the list becomes: ";
   for (Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;
}
```

```Output
The initial list is: 10 20 30 40 50
After erasing the first element, the list becomes: 20 30 40 50
After erasing all elements but the first, the list becomes:  20
```

## <a name="front"></a>  list::front

Devuelve una referencia al primer elemento de una lista.

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>Valor devuelto

Si la lista está vacía, la devolución no está definida.

### <a name="remarks"></a>Comentarios

Si el valor devuelto de `front` se asigna a un `const_reference`, el objeto de lista no se puede modificar. Si el valor devuelto de `front` se asigna a un `reference`, el objeto de lista se puede modificar.

Al compilar con [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definido como 1 o 2, se producirá un error en tiempo de ejecución si intenta obtener acceso a un elemento de una lista vacía.  Vea [Iteradores activados](../standard-library/checked-iterators.md) para obtener más información.

### <a name="example"></a>Ejemplo

```cpp
// list_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main() {
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );

   int& i = c1.front();
   const int& ii = c1.front();

   cout << "The first integer of c1 is " << i << endl;
   i++;
   cout << "The first integer of c1 is " << ii << endl;
}
```

```Output
The first integer of c1 is 10
The first integer of c1 is 11
```

## <a name="get_allocator"></a>  list::get_allocator

Devuelve una copia del objeto de asignador utilizado para construir una lista.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Valor devuelto

El asignador utilizado por la lista.

### <a name="remarks"></a>Comentarios

Los asignadores de la clase de lista especifican cómo la clase administra el almacenamiento. Los asignadores predeterminados proporcionados con las clases contenedoras de la biblioteca estándar de C++ son suficientes para la mayoría de las necesidades de programación. La escritura y el uso de sus propias clases de asignador son temas avanzados de C++.

### <a name="example"></a>Ejemplo

```cpp
// list_get_allocator.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   list <int> c1;
   list <int, allocator<int> > c2 = list <int, allocator<int> >( allocator<int>( ) );

   // c3 will use the same allocator class as c1
   list <int> c3( c1.get_allocator( ) );

   list<int>::allocator_type xlst = c1.get_allocator( );
   // You can now call functions on the allocator class used by c1
}
```

## <a name="insert"></a>  list::insert

Inserta un elemento, varios elementos o un intervalo de elementos en una lista en una posición especificada.

```cpp
iterator insert(iterator Where, const Type& Val);
iterator insert(iterator Where, Type&& Val);

void insert(iterator Where, size_type Count, const Type& Val);
iterator insert(iterator Where, initializer_list<Type> IList);

template <class InputIterator>
void insert(iterator Where, InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Where*|Posición de la lista de destino donde se inserta el primer elemento.|
|*Val*|Valor del elemento que se va a insertar en la lista.|
|*Recuento*|Número de elementos que se van a insertar en la lista.|
|*First*|Posición del primer elemento en el intervalo de elementos de la lista de argumentos que se va a copiar.|
|*Último*|Posición del primer elemento más allá del intervalo de elementos de la lista de argumentos que se va a copiar.|

### <a name="return-value"></a>Valor devuelto

Las dos primeras funciones insert devuelven un iterador que apunta a la posición donde se insertó el nuevo elemento en la lista.

### <a name="example"></a>Ejemplo

```cpp
// list_class_insert.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main()
{
    using namespace std;
    list <int> c1, c2;
    list <int>::iterator Iter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    Iter = c1.begin();
    Iter++;
    c1.insert(Iter, 100);
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    Iter = c1.begin();
    Iter++;
    Iter++;
    c1.insert(Iter, 2, 200);

    cout << "c1 =";
    for(auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.insert(++c1.begin(), c2.begin(), --c2.end());

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    // initialize a list of strings by moving
    list < string > c3;
    string str("a");

    c3.insert(c3.begin(), move(str));
    cout << "Moved first element: " << c3.front() << endl;

    // Assign with an initializer_list
    list <int> c4{ {1, 2, 3, 4} };
    c4.insert(c4.begin(), { 5, 6, 7, 8 });

    cout << "c4 =";
    for (auto c : c4)
        cout << " " << c;
    cout << endl;
}
```

## <a name="iterator"></a>  list::iterator

Tipo que proporciona un iterador bidireccional que puede leer o modificar cualquier elemento de una lista.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Comentarios

Un tipo `iterator` puede usarse para modificar el valor de un elemento.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [begin](#begin).

## <a name="list"></a>  list::list

Construye una lista de un tamaño específico o con elementos de un valor específico o con un asignador específico o como una copia de todo o de parte de alguna otra lista.

```cpp
list();
explicit list(const Allocator& Al);
explicit list(size_type Count);
list(size_type Count, const Type& Val);
list(size_type Count, const Type& Val, const Allocator& Al);

list(const list& Right);
list(list&& Right);
list(initializer_list<Type> IList, const Allocator& Al);

template <class InputIterator>
list(InputIterator First, InputIterator Last);

template <class InputIterator>
list(InputIterator First, InputIterator Last, const Allocator& Al);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Al*|La clase de asignador que se usa con este objeto.|
|*Recuento*|Número de elementos de la lista construida.|
|*Val*|Valor de los elementos de la lista.|
|*Derecha*|Lista de la que la lista construida va a ser una copia.|
|*First*|Posición del primer elemento en el intervalo de elementos que se va a copiar.|
|*Último*|Posición del primer elemento más allá del intervalo de elementos que se va a copiar.|
|*IList*|initializer_list que contiene los elementos que se van a copiar.|

### <a name="remarks"></a>Comentarios

Todos los constructores almacenan un objeto de asignador (*Al*) e inicializan la lista.

[get_allocator](#get_allocator) devuelve una copia del objeto de asignador usado para construir una lista.

Los dos primeros constructores especifican una lista inicial vacía y el segundo especifica el tipo de asignador (*Al*) que se usará.

El tercer constructor especifica una repetición de un número especificado (*recuento*) de elementos del valor predeterminado para la clase `Type`.

Los constructores cuarto y quinto especifican una repetición de (*recuento*) elementos del valor *Val*.

El sexto constructor especifica una copia de la lista *derecha*.

El séptimo constructor mueve la lista *derecha*.

El octavo constructor utiliza una initializer_list para especificar los elementos.

Los dos constructores siguientes copian el intervalo `[First, Last)` de una lista.

Ninguno de los constructores realiza ninguna reasignación provisional.

### <a name="example"></a>Ejemplo

```cpp
// list_class_list.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main()
{
    using namespace std;
    // Create an empty list c0
    list <int> c0;

    // Create a list c1 with 3 elements of default value 0
    list <int> c1(3);

    // Create a list c2 with 5 elements of value 2
    list <int> c2(5, 2);

    // Create a list c3 with 3 elements of value 1 and with the
    // allocator of list c2
    list <int> c3(3, 1, c2.get_allocator());

    // Create a copy, list c4, of list c2
    list <int> c4(c2);

    // Create a list c5 by copying the range c4[ first,  last)
    list <int>::iterator c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    list <int> c5(c4.begin(), c4_Iter);

    // Create a list c6 by copying the range c4[ first,  last) and with
    // the allocator of list c2
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    c4_Iter++;
    list <int> c6(c4.begin(), c4_Iter, c2.get_allocator());

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    cout << "c2 =";
    for (auto c : c2)
        cout << " " << c;
    cout << endl;

    cout << "c3 =";
    for (auto c : c3)
        cout << " " << c;
    cout << endl;

    cout << "c4 =";
    for (auto c : c4)
        cout << " " << c;
    cout << endl;

    cout << "c5 =";
    for (auto c : c5)
        cout << " " << c;
    cout << endl;

    cout << "c6 =";
    for (auto c : c6)
        cout << " " << c;
    cout << endl;

    // Move list c6 to list c7
    list <int> c7(move(c6));
    cout << "c7 =";
    for (auto c : c7)
        cout << " " << c;
    cout << endl;

    // Construct with initializer_list
    list<int> c8({ 1, 2, 3, 4 });
    cout << "c8 =";
    for (auto c : c8)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 0 0 0c2 = 2 2 2 2 2c3 = 1 1 1c4 = 2 2 2 2 2c5 = 2 2c6 = 2 2 2c7 = 2 2 2c8 = 1 2 3 4
```

## <a name="max_size"></a>  list::max_size

Devuelve la longitud máxima de una lista.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valor devuelto

Longitud máxima posible de la lista.

### <a name="example"></a>Ejemplo

```cpp
// list_max_size.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::size_type i;

   i = c1.max_size( );
   cout << "Maximum possible length of the list is " << i << "." << endl;
}
```

## <a name="merge"></a>  list::merge

Quita los elementos de la lista de argumentos, los inserta en la lista de objetivo y ordena el nuevo conjunto combinado de elementos en orden ascendente o en otro orden especificado.

```cpp
void merge(list<Type, Allocator>& right);

template <class Traits>
void merge(list<Type, Allocator>& right, Traits comp);
```

### <a name="parameters"></a>Parámetros

*right*<br/>
La lista de argumentos que se combinará con la lista de objetivo.

*comp*<br/>
El operador de comparación que se utiliza para ordenar los elementos de la lista de objetivo.

### <a name="remarks"></a>Comentarios

La lista de argumentos *derecho* se combina con la lista de destino.

Tanto los argumentos como las listas de objetivo se deben ordenar con la misma relación de comparación con la que se ordenará la secuencia resultante. El orden predeterminado de la primera función miembro es ascendente. La segunda función miembro impone la operación de comparación especificada por el usuario *comp* de clase `Traits`.

### <a name="example"></a>Ejemplo

```cpp
// list_merge.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2, c3;
   list <int>::iterator c1_Iter, c2_Iter, c3_Iter;

   c1.push_back( 3 );
   c1.push_back( 6 );
   c2.push_back( 2 );
   c2.push_back( 4 );
   c3.push_back( 5 );
   c3.push_back( 1 );

   cout << "c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   cout << "c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   c2.merge( c1 );  // Merge c1 into c2 in (default) ascending order
   c2.sort( greater<int>( ) );
   cout << "After merging c1 with c2 and sorting with >: c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   cout << "c3 =";
   for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
      cout << " " << *c3_Iter;
   cout << endl;

   c2.merge( c3, greater<int>( ) );
   cout << "After merging c3 with c2 according to the '>' comparison relation: c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
c1 = 3 6
c2 = 2 4
After merging c1 with c2 and sorting with >: c2 = 6 4 3 2
c3 = 5 1
After merging c3 with c2 according to the '>' comparison relation: c2 = 6 5 4 3 2 1
```

## <a name="op_eq"></a>  list::operator=

Reemplaza los elementos de la lista por una copia de otra lista.

```cpp
list& operator=(const list& right);
list& operator=(list&& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*right*|[list](../standard-library/list-class.md) que se copia en `list`.|

### <a name="remarks"></a>Comentarios

Después de borrar todos los elementos existentes en un `list`, el operador copia o mueve el contenido de *derecho* en el `list`.

### <a name="example"></a>Ejemplo

```cpp
// list_operator_as.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list<int> v1, v2, v3;
   list<int>::iterator iter;

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
   v2 = forward< list<int> >(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a>  list::pointer

Proporciona un puntero a un elemento de una lista.

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Comentarios

Un tipo `pointer` puede usarse para modificar el valor de un elemento.

En la mayoría de los casos, se debe usar [iterator](#iterator) para obtener acceso a los elementos de un objeto de lista.

## <a name="pop_back"></a>  list::pop_back

Elimina el elemento situado al final de una lista.

```cpp
void pop_back();
```

### <a name="remarks"></a>Comentarios

El último elemento no debe estar vacío. `pop_back` nunca inicia una excepción.

### <a name="example"></a>Ejemplo

```cpp
// list_pop_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The last element is: " << c1.back( ) << endl;

   c1.pop_back( );
   cout << "After deleting the element at the end of the list, "
           "the last element is: " << c1.back( ) << endl;
}
```

```Output
The first element is: 1
The last element is: 2
After deleting the element at the end of the list, the last element is: 1
```

## <a name="pop_front"></a>  list::pop_front

Elimina el elemento situado al principio de una lista.

```cpp
void pop_front();
```

### <a name="remarks"></a>Comentarios

El primer elemento no debe estar vacío. `pop_front` nunca inicia una excepción.

### <a name="example"></a>Ejemplo

```cpp
// list_pop_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The second element is: " << c1.back( ) << endl;

   c1.pop_front( );
   cout << "After deleting the element at the beginning of the list, "
         "the first element is: " << c1.front( ) << endl;
}
```

```Output
The first element is: 1
The second element is: 2
After deleting the element at the beginning of the list, the first element is: 2
```

## <a name="push_back"></a>  list::push_back

Agrega un elemento al final de una lista.

```cpp
void push_back(void push_back(Type&& val);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*val*|El elemento que se agrega al final de la lista.|

### <a name="remarks"></a>Comentarios

Si se lanza una excepción, la lista se deja sin modificar y se vuelve a lanzar la excepción.

### <a name="example"></a>Ejemplo

```cpp
// list_push_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   if ( c1.size( ) != 0 )
      cout << "Last element: " << c1.back( ) << endl;

   c1.push_back( 2 );
   if ( c1.size( ) != 0 )
      cout << "New last element: " << c1.back( ) << endl;

// move initialize a list of strings
   list <string> c2;
   string str("a");

   c2.push_back( move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved first element: a
```

## <a name="push_front"></a>  list::push_front

Agrega un elemento al principio de una lista.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*val*|El elemento que se agrega al principio de la lista.|

### <a name="remarks"></a>Comentarios

Si se lanza una excepción, la lista se deja sin modificar y se vuelve a lanzar la excepción.

### <a name="example"></a>Ejemplo

```cpp
// list_push_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_front( 1 );
   if ( c1.size( ) != 0 )
      cout << "First element: " << c1.front( ) << endl;

   c1.push_front( 2 );
   if ( c1.size( ) != 0 )
      cout << "New first element: " << c1.front( ) << endl;

// move initialize a list of strings
   list <string> c2;
   string str("a");

   c2.push_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
First element: 1
New first element: 2
Moved first element: a
```

## <a name="rbegin"></a>  list::rbegin

Devuelve un iterador que direcciona el primer elemento de una lista invertida.

```cpp
const_reverse_iterator rbegin() const;
reverse_iterator rbegin();
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional inverso que direcciona el primer elemento de una lista invertida (o que direcciona lo que habría sido el último elemento de la lista sin invertir).

### <a name="remarks"></a>Comentarios

`rbegin` se usa con una lista invertida igual que [begin](#begin) se usa con una lista.

Si el valor devuelto de `rbegin` se asigna a un `const_reverse_iterator`, el objeto de lista no se puede modificar. Si el valor devuelto de `rbegin` se asigna a un `reverse_iterator`, el objeto de lista se puede modificar.

`rbegin` puede utilizarse para recorrer en iteración una lista hacia atrás.

### <a name="example"></a>Ejemplo

```cpp
// list_rbegin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::reverse_iterator c1_rIter;

   // If the following line replaced the line above, *c1_rIter = 40;
   // (below) would be an error
   //list <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1_rIter = c1.rbegin( );
   cout << "The last element in the list is " << *c1_rIter << "." << endl;

   cout << "The list is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration through a list in
   // reverse order
   cout << "The reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;

   c1_rIter = c1.rbegin( );
*c1_rIter = 40;
   cout << "The last element in the list is now " << *c1_rIter << "." << endl;
}
```

```Output
The last element in the list is 30.
The list is: 10 20 30
The reversed list is: 30 20 10
The last element in the list is now 40.
```

## <a name="reference"></a>  list::reference

Tipo que proporciona una referencia a un elemento almacenado en una lista.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>Ejemplo

```cpp
// list_ref.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   int &i = c1.front( );
   int &j = c1.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="remove"></a>  list::remove

Borra los elementos de una lista que coinciden con un valor especificado.

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>Parámetros

*val*<br/>
Valor que, si lo contiene un elemento, hará que se quite ese elemento de la lista.

### <a name="remarks"></a>Comentarios

El orden de los elementos restantes no se ve afectado.

### <a name="example"></a>Ejemplo

```cpp
// list_remove.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 5 );
   c1.push_back( 100 );
   c1.push_back( 5 );
   c1.push_back( 200 );
   c1.push_back( 5 );
   c1.push_back( 300 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.remove( 5 );
   cout << "After removing elements with value 5, the list becomes c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = 5 100 5 200 5 300
After removing elements with value 5, the list becomes c2 = 100 200 300
```

## <a name="remove_if"></a>  list::remove_if

Borra elementos de una lista para la que se cumple el predicado especificado.

```cpp
template <class Predicate>
void remove_if(Predicate pred)
```

### <a name="parameters"></a>Parámetros

*pred*<br/>
Predicado unario que, si lo satisface un elemento, da lugar a la eliminación de ese elemento de la lista.

### <a name="example"></a>Ejemplo

```cpp
// list_remove_if.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

template <class T> class is_odd : public std::unary_function<T, bool>
{
public:
   bool operator( ) ( T& val )
   {
   return ( val % 2 ) == 1;
   }
};

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 3 );
   c1.push_back( 4 );
   c1.push_back( 5 );
   c1.push_back( 6 );
   c1.push_back( 7 );
   c1.push_back( 8 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.remove_if( is_odd<int>( ) );

   cout << "After removing the odd elements, "
        << "the list becomes c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = 3 4 5 6 7 8
After removing the odd elements, the list becomes c2 = 4 6 8
```

## <a name="rend"></a>  list::rend

Devuelve un iterador que direcciona la ubicación que sigue al último elemento de una lista invertida.

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional inverso que direcciona la ubicación del último elemento de una lista invertida (la ubicación que había precedido al primer elemento de la lista sin invertir).

### <a name="remarks"></a>Comentarios

`rend` se usa con una lista invertida igual que [end](#end) se usa con una lista.

Si el valor devuelto de `rend` se asigna a un `const_reverse_iterator`, el objeto de lista no se puede modificar. Si el valor devuelto de `rend` se asigna a un `reverse_iterator`, el objeto de lista se puede modificar.

Se puede utilizar `rend` para comprobar a si un iterador inverso ha llegado al final de su lista.

El valor devuelto por `rend` no se debe desreferenciar.

### <a name="example"></a>Ejemplo

```cpp
// list_rend.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::reverse_iterator c1_rIter;

   // If the following line had replaced the line above, an error would
   // have resulted in the line modifying an element (commented below)
   // because the iterator would have been const
   // list <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rend( );
   c1_rIter --;  // Decrementing a reverse iterator moves it forward in
                 // the list (to point to the first element here)
   cout << "The first element in the list is: " << *c1_rIter << endl;

   cout << "The list is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   // rend can be used to test if an iteration is through all of the
   // elements of a reversed list
   cout << "The reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;

   c1_rIter = c1.rend( );
   c1_rIter--;  // Decrementing the reverse iterator moves it backward
                // in the reversed list (to the last element here)

*c1_rIter = 40;  // This modification of the last element would have
                    // caused an error if a const_reverse iterator had
                    // been declared (as noted above)

   cout << "The modified reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;
}
```

```Output
The first element in the list is: 10
The list is: 10 20 30
The reversed list is: 30 20 10
The modified reversed list is: 30 20 40
```

## <a name="resize"></a>  list::resize

Especifica un nuevo tamaño de una lista.

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>Parámetros

*_Newsize*<br/>
Nuevo tamaño de la lista.

*val*<br/>
Valor de los nuevos elementos que se agregarán a la lista si el nuevo tamaño es mayor que el tamaño original. Si el valor se omite, a los nuevos elementos se les asigna el valor predeterminado para la clase.

### <a name="remarks"></a>Comentarios

Si el tamaño de la lista es menor que el tamaño solicitado, *_Newsize*, se agregan elementos a la lista hasta que alcance el tamaño solicitado.

Si el tamaño de la lista es mayor que el tamaño solicitado, se eliminan los elementos más cercanos al final de la lista hasta que la lista alcanza el tamaño *_Newsize*.

Si el tamaño actual de la lista es igual que el tamaño solicitado, no se lleva a cabo ninguna acción.

[size](#size) refleja el tamaño actual de la lista.

### <a name="example"></a>Ejemplo

```cpp
// list_resize.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1.resize( 4,40 );
   cout << "The size of c1 is " << c1.size( ) << endl;
   cout << "The value of the last element is " << c1.back( ) << endl;

   c1.resize( 5 );
   cout << "The size of c1 is now " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;

   c1.resize( 2 );
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;
}
```

```Output
The size of c1 is 4
The value of the last element is 40
The size of c1 is now 5
The value of the last element is now 0
The reduced size of c1 is: 2
The value of the last element is now 20
```

## <a name="reverse"></a>  list::reverse

Invierte el orden en que aparecen los elementos en una lista.

```cpp
void reverse();
```

### <a name="example"></a>Ejemplo

```cpp
// list_reverse.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.reverse( );
   cout << "Reversed c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
c1 = 10 20 30
Reversed c1 = 30 20 10
```

## <a name="reverse_iterator"></a>  list::reverse_iterator

Tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento de una lista invertida.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Comentarios

Los tipos `reverse_iterator` se utilizan para procesar una iteración en la lista en orden inverso.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [rbegin](#rbegin).

## <a name="size"></a>  list::size

Devuelve el número de elementos de una lista.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valor devuelto

Longitud actual de la lista.

### <a name="example"></a>Ejemplo

```cpp
// list_size.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::size_type i;

   c1.push_back( 5 );
   i = c1.size( );
   cout << "List length is " << i << "." << endl;

   c1.push_back( 7 );
   i = c1.size( );
   cout << "List length is now " << i << "." << endl;
}
```

```Output
List length is 1.
List length is now 2.
```

## <a name="size_type"></a>  list::size_type

Tipo que cuenta el número de elementos de una lista.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [size](#size).

## <a name="sort"></a>  list::sort

Organiza los elementos de una lista en orden ascendente o con respecto a otro orden especificado por el usuario.

```cpp
void sort();

template <class Traits>
void sort(Traits comp);
```

### <a name="parameters"></a>Parámetros

*comp*<br/>
Operador de comparación utilizado para ordenar elementos sucesivos.

### <a name="remarks"></a>Comentarios

La primera función miembro pone los elementos en orden ascendente de forma predeterminada.

La función de plantilla miembro ordena los elementos según la operación de comparación especificada por el usuario *comp* de clase `Traits`.

### <a name="example"></a>Ejemplo

```cpp
// list_sort.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 20 );
   c1.push_back( 10 );
   c1.push_back( 30 );

   cout << "Before sorting: c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.sort( );
   cout << "After sorting c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.sort( greater<int>( ) );
   cout << "After sorting with 'greater than' operation, c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
Before sorting: c1 = 20 10 30
After sorting c1 = 10 20 30
After sorting with 'greater than' operation, c1 = 30 20 10
```

## <a name="splice"></a>  list::splice

Quita elementos de una lista de origen y los inserta en una lista de destino.

```cpp
// insert the entire source list
void splice(const_iterator Where, list<Type, Allocator>& Source);
void splice(const_iterator Where, list<Type, Allocator>&& Source);

// insert one element of the source list
void splice(const_iterator Where, list<Type, Allocator>& Source, const_iterator Iter);
void splice(const_iterator Where, list<Type, Allocator>&& Source, const_iterator Iter);

// insert a range of elements from the source list
void splice(const_iterator Where, list<Type, Allocator>& Source, const_iterator First, const_iterator Last);
void splice(const_iterator Where, list<Type, Allocator>&& Source, const_iterator First, const_iterator Last);
```

### <a name="parameters"></a>Parámetros

*Where*<br/>
Posición en la lista de destino anterior a la posición de inserción.

*Origen*<br/>
Lista de origen que se va a insertar en la lista de destino.

*Iter*<br/>
Elemento que se va a insertar de la lista de origen.

*First*<br/>
Primer elemento del intervalo que se va a insertar de la lista de origen.

*Último*<br/>
Primera posición después del último elemento del intervalo que se va a insertar de la lista de origen.

### <a name="remarks"></a>Comentarios

El primer par de funciones miembro inserta todos los elementos en la lista de origen en la lista de destino antes de la posición hace referencia a *donde* y quita todos los elementos de la lista de origen. (`&Source` no debe ser igual `this`.)

El segundo par de funciones miembro inserta el elemento al que hace referencia *Iter* antes de la posición en la lista de destino al que hace referencia *donde* y quita *Iter* desde el lista de origen. (Si `Where == Iter || Where == ++Iter`, no ocurre ningún cambio.)

El tercer par de funciones miembro inserta el intervalo designado mediante por [ `First`, `Last`) antes de que el elemento en la lista de destino denominado *donde* y quita dicho intervalo de elementos de la lista de origen. (Si `&Source == this`, el intervalo `[First, Last)` no debe incluir el elemento indicado por *donde*.)

Si la unión del intervalo inserta `N` elementos y `&Source != this`, un objeto de clase [iterator](../standard-library/forward-list-class.md#iterator) se incrementa `N` veces.

En todos los casos, los iteradores, punteros o referencias que remitan a elementos insertos seguirán siendo válidos y se transferirán al contenedor de destino.

### <a name="example"></a>Ejemplo

```cpp
// list_splice.cpp
// compile with: /EHsc /W4
#include <list>
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
    list<int> c1{10,11};
    list<int> c2{20,21,22};
    list<int> c3{30,31};
    list<int> c4{40,41,42,43};

    list<int>::iterator where_iter;
    list<int>::iterator first_iter;
    list<int>::iterator last_iter;

    cout << "Beginning state of lists:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);
    cout << "c3 = ";
    print(c3);
    cout << "c4 = ";
    print(c4);

    where_iter = c2.begin();
    ++where_iter; // start at second element
    c2.splice(where_iter, c1);
    cout << "After splicing c1 into c2:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);

    first_iter = c3.begin();
    c2.splice(where_iter, c3, first_iter);
    cout << "After splicing the first element of c3 into c2:" << endl;
    cout << "c3 = ";
    print(c3);
    cout << "c2 = ";
    print(c2);

    first_iter = c4.begin();
    last_iter = c4.end();
    // set up to get the middle elements
    ++first_iter;
    --last_iter;
    c2.splice(where_iter, c4, first_iter, last_iter);
    cout << "After splicing a range of c4 into c2:" << endl;
    cout << "c4 = ";
    print(c4);
    cout << "c2 = ";
    print(c2);
}
```

```Output
Beginning state of lists:c1 = 2 elements: (10) (11)c2 = 3 elements: (20) (21) (22)c3 = 2 elements: (30) (31)c4 = 4 elements: (40) (41) (42) (43)After splicing c1 into c2:c1 = 0 elements:c2 = 5 elements: (20) (10) (11) (21) (22)After splicing the first element of c3 into c2:c3 = 1 elements: (31)c2 = 6 elements: (20) (10) (11) (30) (21) (22)After splicing a range of c4 into c2:c4 = 2 elements: (40) (43)c2 = 8 elements: (20) (10) (11) (30) (41) (42) (21) (22)
```

## <a name="swap"></a>  list::swap

Intercambia los elementos de dos listas.

```cpp
void swap(list<Type, Allocator>& right);
friend void swap(list<Type, Allocator>& left, list<Type, Allocator>& right)
```

### <a name="parameters"></a>Parámetros

*right*<br/>
La lista que proporciona los elementos deben intercambiar o la lista cuyos elementos se van a intercambiar con los de la lista *izquierdo*.

*left*<br/>
Una lista cuyos elementos se van a intercambiar con los de la lista *derecho*.

### <a name="example"></a>Ejemplo

```cpp
// list_swap.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2, c3;
   list <int>::iterator c1_Iter;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 3 );
   c2.push_back( 10 );
   c2.push_back( 20 );
   c3.push_back( 100 );

   cout << "The original list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.swap( c2 );

   cout << "After swapping with c2, list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap( c1,c3 );

   cout << "After swapping with c3, list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
The original list c1 is: 1 2 3
After swapping with c2, list c1 is: 10 20
After swapping with c3, list c1 is: 100
```

## <a name="unique"></a>  list::unique

Quita de una lista los elementos duplicados adyacentes o los elementos adyacentes que cumplan algún otro predicado binario.

```cpp
void unique();

template <class BinaryPredicate>
void unique(BinaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*pred*<br/>
El predicado binario que se usa para comparar los elementos sucesivos.

### <a name="remarks"></a>Comentarios

Esta función presupone que la lista está ordenada, por lo que todos los elementos duplicados son adyacentes. No se eliminarán los duplicados que no sean adyacentes.

La primera función miembro quita todos los elementos que compara con relación de igualdad con el elemento anterior.

La segunda función miembro quita todos los elementos que satisfacen la función de predicado *pred* en comparación con el elemento anterior. Puede usar cualquiera de los objetos de función binarios declarados en el \<funcional > encabezado para el argumento *pred* o crear los suyos propios.

### <a name="example"></a>Ejemplo

```cpp
// list_unique.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter,c3_Iter;
   not_equal_to<int> mypred;

   c1.push_back( -10 );
   c1.push_back( 10 );
   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 20 );
   c1.push_back( -10 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.unique( );
   cout << "After removing successive duplicate elements, c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   list <int> c3 = c2;
   c3.unique( mypred );
   cout << "After removing successive unequal elements, c3 =";
   for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
      cout << " " << *c3_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = -10 10 10 20 20 -10
After removing successive duplicate elements, c2 = -10 10 20 -10
After removing successive unequal elements, c3 = -10 -10
```

## <a name="value_type"></a>  list::value_type

Tipo que representa el tipo de datos almacenados en una lista.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Comentarios

`value_type` es un sinónimo del parámetro de plantilla *Type*.

### <a name="example"></a>Ejemplo

```cpp
// list_value_type.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```

## <a name="see-also"></a>Vea también

[\<list>](../standard-library/list.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
