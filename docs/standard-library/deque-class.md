---
title: deque (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- deque/std::deque
- deque/std::deque::allocator_type
- deque/std::deque::const_iterator
- deque/std::deque::const_pointer
- deque/std::deque::const_reference
- deque/std::deque::const_reverse_iterator
- deque/std::deque::difference_type
- deque/std::deque::iterator
- deque/std::deque::pointer
- deque/std::deque::reference
- deque/std::deque::reverse_iterator
- deque/std::deque::size_type
- deque/std::deque::value_type
- deque/std::deque::assign
- deque/std::deque::at
- deque/std::deque::back
- deque/std::deque::begin
- deque/std::deque::cbegin
- deque/std::deque::cend
- deque/std::deque::clear
- deque/std::deque::crbegin
- deque/std::deque::crend
- deque/std::deque::emplace
- deque/std::deque::emplace_back
- deque/std::deque::emplace_front
- deque/std::deque::empty
- deque/std::deque::end
- deque/std::deque::erase
- deque/std::deque::front
- deque/std::deque::get_allocator
- deque/std::deque::insert
- deque/std::deque::max_size
- deque/std::deque::pop_back
- deque/std::deque::pop_front
- deque/std::deque::push_back
- deque/std::deque::push_front
- deque/std::deque::rbegin
- deque/std::deque::rend
- deque/std::deque::resize
- deque/std::deque::shrink_to_fit
- deque/std::deque::size
- deque/std::deque::swap
dev_langs:
- C++
helpviewer_keywords:
- std::deque [C++]
- std::deque [C++], allocator_type
- std::deque [C++], const_iterator
- std::deque [C++], const_pointer
- std::deque [C++], const_reference
- std::deque [C++], const_reverse_iterator
- std::deque [C++], difference_type
- std::deque [C++], iterator
- std::deque [C++], pointer
- std::deque [C++], reference
- std::deque [C++], reverse_iterator
- std::deque [C++], size_type
- std::deque [C++], value_type
- std::deque [C++], assign
- std::deque [C++], at
- std::deque [C++], back
- std::deque [C++], begin
- std::deque [C++], cbegin
- std::deque [C++], cend
- std::deque [C++], clear
- std::deque [C++], crbegin
- std::deque [C++], crend
- std::deque [C++], emplace
- std::deque [C++], emplace_back
- std::deque [C++], emplace_front
- std::deque [C++], empty
- std::deque [C++], end
- std::deque [C++], erase
- std::deque [C++], front
- std::deque [C++], get_allocator
- std::deque [C++], insert
- std::deque [C++], max_size
- std::deque [C++], pop_back
- std::deque [C++], pop_front
- std::deque [C++], push_back
- std::deque [C++], push_front
- std::deque [C++], rbegin
- std::deque [C++], rend
- std::deque [C++], resize
- std::deque [C++], shrink_to_fit
- std::deque [C++], size
- std::deque [C++], swap
ms.assetid: 64842ee5-057a-4063-8c16-4267a0332584
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0ed609de9d36b602bf525a9643534cf5d1d55a8
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963039"
---
# <a name="deque-class"></a>deque (Clase)

Organiza los elementos de un tipo determinado en una organización lineal y, como un vector, permite un acceso aleatorio rápido a cualquier elemento y, una inserción y eliminación eficaces al final del contenedor. Sin embargo, a diferencia de un vector, la clase `deque` también admite la inserción y la eliminación eficaces al principio del contenedor.

## <a name="syntax"></a>Sintaxis

```unstlib
template <class Type, class Allocator =allocator<Type>>
class deque
```

### <a name="parameters"></a>Parámetros

*Tipo* tipo de los datos del elemento que se almacenará en el deque.

*Asignador* el tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca del deque asignación y desasignación de memoria. Este argumento es opcional y el valor predeterminado es **asignador\<tipo>***.*

## <a name="remarks"></a>Comentarios

En general, la elección del tipo de contenedor se debe tomar según el tipo de búsqueda y de inserción que necesite la aplicación. [Vectores](../standard-library/vector-class.md) debe ser el contenedor preferido para administrar una secuencia cuando el acceso aleatorio a cualquier elemento sea importante y las inserciones o eliminaciones de elementos solo sean necesarias al final de una secuencia. El rendimiento del contenedor de lista es superior cuando las inserciones y eliminaciones eficaces (en tiempo constante) en cualquier ubicación dentro de la secuencia son importantes. Esas operaciones en medio de la secuencia requieren copias y asignaciones de elementos proporcionales al número de elementos de la secuencia (tiempo lineal).

La reasignación de deque se realiza cuando una función miembro debe insertar o borrar elementos de la secuencia:

- Si un elemento se inserta en una secuencia vacía, o si un elemento se borra para dejar una secuencia vacía, los iteradores anteriores devueltos por [begin](#begin) y [end](#end) dejan de ser válidos.

- Si se inserta un elemento en la primera posición del deque, todos los iteradores, pero ninguna referencia, que designan elementos existentes dejan de ser válidos.

- Si se inserta un elemento al final del deque, [end](#end) y todos los iteradores, pero ninguna referencia, que designan elementos existentes dejan de ser válidos.

- Si se borra un elemento al principio del deque, solo el iterador y las referencias al elemento borrado dejan de ser válidos.

- Si se borra el último elemento del final del deque, solo el iterador al elemento final y las referencias al elemento borrado dejan de ser válidos.

De lo contrario, al insertar o borrar un elemento se invalidan todos los iteradores y referencias.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[deque](#deque)|Construye un objeto `deque`. Se proporcionan varios constructores para configurar el contenido del nuevo `deque` de maneras diferentes: vacío; cargado con un número especificado de elementos vacíos; contenido movido o copiado de otro `deque`; contenido copiado o movido mediante un iterador; y un elemento copiado en el `deque` `count` veces. Algunos de los constructores permiten usar un `allocator` personalizado para crear elementos.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[allocator_type](#allocator_type)|Tipo que representa la clase `allocator` para el objeto `deque`.|
|[const_iterator](#const_iterator)|Tipo que proporciona un iterador de acceso aleatorio que puede obtener acceso a elementos de `deque` como `const` y leerlos.|
|[const_pointer](#const_pointer)|Tipo que proporciona un puntero a un elemento de `deque` como `const.`|
|[const_reference](#const_reference)|Tipo que proporciona una referencia a un elemento de `deque` para operaciones de lectura y de otro tipo como `const.`|
|[const_reverse_iterator](#const_reverse_iterator)|Un tipo que proporciona un iterador de acceso aleatorio que puede obtener acceso y leer los elementos de la `deque` como **const**. El deque se ve en orden inverso. Para obtener más información, vea [reverse_iterator (Clase)](../standard-library/reverse-iterator-class.md)|
|[difference_type](#difference_type)|Tipo que proporciona la diferencia entre dos iteradores de acceso aleatorio que hacen referencia a elementos del mismo `deque`.|
|[iterator](#iterator)|Tipo que proporciona un iterador de acceso aleatorio que puede leer o modificar cualquier elemento de `deque`.|
|[pointer](#pointer)|Tipo que proporciona un puntero a un elemento de `deque`.|
|[reference](#reference)|Tipo que proporciona una referencia a un elemento almacenado en un `deque`.|
|[reverse_iterator](#reverse_iterator)|Tipo que proporciona un iterador de acceso aleatorio que puede leer o modificar un elemento de `deque`. El deque se ve en orden inverso.|
|[size_type](#size_type)|Tipo que cuenta el número de elementos de un `deque`.|
|[value_type](#value_type)|Tipo que representa el tipo de datos almacenados en un `deque`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[assign](#assign)|Borra elementos de un `deque` y copia una nueva secuencia de elementos al `deque` de destino.|
|[at](#at)|Devuelve una referencia al elemento situado en una ubicación especificada del `deque`.|
|[back](#back)|Devuelve una referencia al último elemento del `deque`.|
|[begin](#begin)|Devuelve un iterador de acceso aleatorio que direcciona el primer elemento del `deque`.|
|[cbegin](#cbegin)|Devuelve un iterador constante al primer elemento del `deque`.|
|[cend](#cend)|Devuelve un acceso aleatorio **const** iterador que apunta justo después del final de la `deque`.|
|[clear](#clear)|Borra todos los elementos de un `deque`.|
|[crbegin](#crbegin)|Devuelve un iterador constante de acceso aleatorio al primer elemento de `deque` que se ve en orden inverso.|
|[crend](#crend)|Devuelve un iterador constante de acceso aleatorio al primer elemento de `deque` que se ve en orden inverso.|
|[emplace](#emplace)|Inserta en una posición especificada del `deque` un elemento construido en contexto.|
|[emplace_back](#emplace_back)|Agrega un elemento construido en contexto al final del `deque`.|
|[emplace_front](#emplace_front)|Agrega un elemento construido en contexto al principio del `deque`.|
|[empty](#empty)|Devuelve **true** si el `deque` contiene cero elementos, y **false** si contiene uno o más elementos.|
|[end](#end)|Devuelve un iterador de acceso aleatorio que apunta justo después del final del `deque`.|
|[erase](#erase)|Quita un elemento o un intervalo de elementos de un `deque` de las posiciones especificadas.|
|[front](#front)|Devuelve una referencia al primer elemento de `deque`.|
|[get_allocator](#get_allocator)|Devuelve una copia del objeto `allocator` utilizado para construir el `deque`.|
|[insert](#insert)|Inserta un elemento, varios elementos o un intervalo de elementos en una posición especificada del `deque`.|
|[max_size](#max_size)|Devuelve la longitud máxima posible del `deque`.|
|[pop_back](#pop_back)|Borra el elemento situado al final del `deque`.|
|[pop_front](#pop_front)|Borra el elemento situado al principio del `deque`.|
|[push_back](#push_back)|Agrega un elemento al final del `deque`.|
|[push_front](#push_front)|Agrega un elemento al principio del `deque`.|
|[rbegin](#rbegin)|Devuelve un iterador de acceso aleatorio al primer elemento de `deque` invertido.|
|[rend](#rend)|Devuelve un iterador de acceso aleatorio que apunta justo detrás del último elemento de `deque` invertido.|
|[resize](#resize)|Especifica un nuevo tamaño para un `deque`.|
|[shrink_to_fit](#shrink_to_fit)|Descarta el exceso de capacidad.|
|[size](#size)|Devuelve el número de elementos de `deque`.|
|[swap](#swap)|Intercambia los elementos de dos `deque`.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator&#91;&#93;](#op_at)|Devuelve una referencia al elemento del `deque` en una posición especificada.|
|[operator=](#op_eq)|Reemplaza los elementos del `deque` con una copia de otro `deque`.|

## <a name="requirements"></a>Requisitos

**Encabezado**: \<deque>

## <a name="allocator_type"></a>  deque::allocator_type

Tipo que representa la clase de asignador del objeto deque.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Comentarios

`allocator_type` es un sinónimo del parámetro de plantilla `Allocator`.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [get_allocator](#get_allocator).

## <a name="assign"></a>  deque::assign

Borra elementos de un deque y copia un nuevo conjunto de elementos en el deque de destino.

```cpp
template <class InputIterator>
void assign(
    InputIterator First,
    InputIterator Last);

void assign(
    size_type Count,
    const Type& Val);

void assign(initializer_list<Type> IList);
```

### <a name="parameters"></a>Parámetros

*Primera* posición del primer elemento del intervalo de elementos va a copiar del argumento deque.

*Último* posición del primer elemento más allá del intervalo de elementos va a copiar del argumento deque.

*Recuento de* el número de copias de un elemento que se va a insertar en el deque.

*Val* el valor del elemento que se va a insertar en el deque.

*IList* initializer_list que se va a insertar en el deque.

### <a name="remarks"></a>Comentarios

Después de borrar los elementos existentes en el deque de destino, `assign` inserta un intervalo especificado de elementos del deque original o de otro deque en el deque de destino, o inserta copias de un nuevo elemento de un valor especificado en el deque de destino.

### <a name="example"></a>Ejemplo

```cpp
// deque_assign.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
#include <initializer_list>

int main()
{
    using namespace std;
    deque <int> c1, c2;
    deque <int>::const_iterator cIter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    deque<int> d1{ 1, 2, 3, 4 };
    initializer_list<int> iList{ 5, 6, 7, 8 };
    d1.assign(iList);

    cout << "d1 = ";
    for (int i : d1)
        cout << i;
    cout << endl;

    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;

    c1.assign(++c2.begin(), c2.end());
    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;

    c1.assign(7, 4);
    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;

}

```

```Output
d1 = 5678c1 =102030c1 =5060c1 =4444444
```

## <a name="at"></a>  deque::at

Devuelve una referencia al elemento en una ubicación especificada del deque.

```cpp
reference at(size_type pos);

const_reference at(size_type pos) const;
```

### <a name="parameters"></a>Parámetros

*PDV* el subíndice (o el número de posición) del elemento al que hace referencia en el deque.

### <a name="return-value"></a>Valor devuelto

Si *pos* es mayor que el tamaño del deque, `at` produce una excepción.

### <a name="return-value"></a>Valor devuelto

Si el valor devuelto de `at` se asigna a un `const_reference`, el objeto deque no se puede modificar. Si el valor devuelto de `at` se asigna a un `reference`, el objeto deque se puede modificar.

### <a name="example"></a>Ejemplo

```cpp
// deque_at.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const int& i = c1.at( 0 );
   int& j = c1.at( 1 );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="back"></a>  deque::back

Devuelve una referencia al último elemento del deque.

```cpp
reference back();
const_reference back() const;
```

### <a name="return-value"></a>Valor devuelto

El último elemento del deque. Si el deque está vacío, el valor devuelto es indefinido.

### <a name="remarks"></a>Comentarios

Si el valor devuelto de `back` se asigna a un `const_reference`, el objeto deque no se puede modificar. Si el valor devuelto de `back` se asigna a un `reference`, el objeto deque se puede modificar.

Al compilar con [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definido como 1 o 2, se producirá un error en tiempo de ejecución si intenta acceder a un elemento en un deque vacío.  Vea [Iteradores comprobados](../standard-library/checked-iterators.md) para obtener más información.

### <a name="example"></a>Ejemplo

```cpp
// deque_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

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

## <a name="begin"></a>  deque::begin

Devuelve un iterador que se dirige al primer elemento del deque.

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>Valor devuelto

Un iterador de acceso aleatorio que se dirige al primer elemento del deque o a la ubicación que sigue a un deque vacío.

### <a name="remarks"></a>Comentarios

Si el valor devuelto de `begin` se asigna a un `const_iterator`, el objeto deque no se puede modificar. Si el valor devuelto de `begin` se asigna a un `iterator`, el objeto deque puede modificarse.

### <a name="example"></a>Ejemplo

```cpp
// deque_begin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::const_iterator c1_cIter;

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

## <a name="cbegin"></a>  deque::cbegin

Devuelve un **const** iterador que direcciona el primer elemento del intervalo.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Un **const** iterador de acceso aleatorio que apunta al primer elemento del intervalo o la ubicación situada más allá del final de un intervalo vacío (para un intervalo vacío, `cbegin() == cend()`).

### <a name="remarks"></a>Comentarios

Con el valor devuelto de `cbegin`, los elementos del intervalo no se pueden modificar.

Se puede usar esta función miembro en lugar de la función miembro `begin()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo, se considera que `Container` es un contenedor modificable (distinto de `const`) de cualquier naturaleza que admite `begin()` y `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  deque::cend

Devuelve un **const** iterador que direcciona la ubicación situada más allá del último elemento de un intervalo.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador de acceso aleatorio que apunta justo después del final del intervalo.

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

## <a name="clear"></a>  deque::clear

Borra todos los elementos de un deque.

```cpp
void clear();
```

### <a name="example"></a>Ejemplo

```cpp
// deque_clear.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "The size of the deque is initially " << c1.size( ) << endl;
   c1.clear( );
   cout << "The size of the deque after clearing is " << c1.size( ) << endl;
}
```

```Output
The size of the deque is initially 3
The size of the deque after clearing is 0
```

## <a name="const_iterator"></a>  deque::const_iterator

Tipo que proporciona un iterador de acceso aleatorio que puede acceder a un elemento **const** del deque y leerlo.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Comentarios

Un tipo `const_iterator` no se puede utilizar para modificar el valor de un elemento.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [back](#back).

## <a name="const_pointer"></a>  deque::const_pointer

Proporciona un puntero a un **const** elemento de un deque.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Comentarios

Un tipo `const_pointer` no se puede utilizar para modificar el valor de un elemento. Un [iterator](#iterator) se usa normalmente para tener acceso a un elemento de deque.

## <a name="const_reference"></a>  deque::const_reference

Tipo que proporciona una referencia a un elemento **const** almacenado en un deque para leer operaciones **const** y realizarlas.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Comentarios

Un tipo `const_reference` no se puede utilizar para modificar el valor de un elemento.

### <a name="example"></a>Ejemplo

```cpp
// deque_const_ref.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const deque <int> c2 = c1;
   const int &i = c2.front( );
   const int &j = c2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error as c2 is const
   // c2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a>  deque::const_reverse_iterator

Tipo que proporciona un iterador de acceso aleatorio que puede leer cualquier elemento **const** en el deque.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Comentarios

Un tipo `const_reverse_iterator` no puede modificar el valor de un elemento y se usa para iterar en el deque en orden inverso.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [rbegin](#rbegin) para obtener un ejemplo de cómo declarar y usar un iterador.

## <a name="crbegin"></a>  deque::crbegin

Devuelve un iterador constante al primer elemento de un deque inverso.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador inverso constante de acceso aleatorio que se dirige al primer elemento de un [deque](../standard-library/deque-class.md) inverso o al que fue el último elemento del `deque` sin invertir.

### <a name="remarks"></a>Comentarios

Con el valor devuelto de `crbegin`, el objeto `deque` no se puede modificar.

### <a name="example"></a>Ejemplo

```cpp
// deque_crbegin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::iterator v1_Iter;
   deque <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of deque is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed deque is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of deque is 1.
The first element of the reversed deque is 2.
```

## <a name="crend"></a>  deque::crend

Devuelve un iterador constante que se dirige a la ubicación que sigue al último elemento de un deque invertido.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador constante de acceso aleatorio inverso que se dirige a la ubicación siguiente al último elemento de un [deque](../standard-library/deque-class.md) invertido (la ubicación que había precedido al primer elemento del deque sin invertir).

### <a name="remarks"></a>Comentarios

`crend` se usa con un `deque` invertido igual que [array::cend](../standard-library/array-class-stl.md#cend) se usa con un `deque`.

Con el valor devuelto de `crend` (adecuadamente reducido), el objeto `deque` no se puede modificar.

Se puede usar `crend` para comprobar si un iterador inverso ha llegado al final de su deque.

El valor devuelto por `crend` no se debe desreferenciar.

### <a name="example"></a>Ejemplo

```cpp
// deque_crend.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::const_reverse_iterator v1_rIter;

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

## <a name="deque"></a>  deque::deque

Construye un deque de un tamaño específico, con elementos de un valor específico, con un asignador específico o como una copia de todo o de parte de otro deque.

```cpp
deque();

explicit deque(const Allocator& Al);
explicit deque(size_type Count);
deque(size_type Count, const Type& Val);

deque(
    size_type Count,
    const Type& Val,
    const Allocator& Al);

deque(const deque& Right);

template <class InputIterator>
deque(InputIterator First,  InputIterator Last);

template <class InputIterator>
deque(
   InputIterator First,
   InputIterator Last,
   const Allocator& Al);

deque(initializer_list<value_type> IList, const Allocator& Al);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Al*|La clase de asignador que se usa con este objeto.|
|*Recuento*|Número de elementos del deque construido.|
|*Val*|Valor de los elementos del deque construido.|
|*Derecha*|Deque del cual el deque construido va a ser una copia.|
|*Primero*|Posición del primer elemento en el intervalo de elementos que se va a copiar.|
|*Último*|Posición del primer elemento más allá del intervalo de elementos que se va a copiar.|
|* IList'|initializer_list que se va a copiar.|

### <a name="remarks"></a>Comentarios

Todos los constructores almacenan un objeto de asignador (*Al*) e inicializan el deque.

Los dos primeros constructores especifican un deque inicial vacío y el segundo especifica también el tipo de asignador (`_Al`) que se va a usar.

El tercer constructor especifica una repetición de un número especificado (`count`) de elementos del valor predeterminado para la clase `Type`.

Los constructores cuarto y quinto especifican una repetición de (*recuento*) elementos del valor `val`.

El sexto constructor especifica una copia del deque *derecha*.

Los constructores séptimo y octavo copian el intervalo `[First, Last)` de un deque.

El séptimo constructor mueve el deque *derecha*.

El octavo constructor copia el contenido de una initializer_list.

Ninguno de los constructores realiza ninguna reasignación provisional.

### <a name="example"></a>Ejemplo

```cpp
/ compile with: /EHsc
#include <deque>
#include <iostream>
#include <forward_list>

int main()
{
    using namespace std;

    forward_list<int> f1{ 1, 2, 3, 4 };

    f1.insert_after(f1.begin(), { 5, 6, 7, 8 });

    deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;

    // Create an empty deque c0
    deque <int> c0;

    // Create a deque c1 with 3 elements of default value 0
    deque <int> c1(3);

    // Create a deque c2 with 5 elements of value 2
    deque <int> c2(5, 2);

    // Create a deque c3 with 3 elements of value 1 and with the
    // allocator of deque c2
    deque <int> c3(3, 1, c2.get_allocator());

    // Create a copy, deque c4, of deque c2
    deque <int> c4(c2);

    // Create a deque c5 by copying the range c4[ first,  last)
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    deque <int> c5(c4.begin(), c4_Iter);

    // Create a deque c6 by copying the range c4[ first,  last) and
    // c2 with the allocator of deque
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    c4_Iter++;
    deque <int> c6(c4.begin(), c4_Iter, c2.get_allocator());

    // Create a deque c8 by copying the contents of an initializer_list
    // using brace initialization
    deque<int> c8({ 1, 2, 3, 4 });

    initializer_list<int> iList{ 5, 6, 7, 8 };
    deque<int> c9( iList);

    cout << "c1 = ";
    for (int i : c1)
        cout << i << " ";
    cout << endl;

    cout << "c2 = ";
    for (int i : c2)
        cout << i << " ";
    cout << endl;

    cout << "c3 = ";
    for (int i : c3)
        cout << i << " ";
    cout << endl;

    cout << "c4 = ";
    for (int i : c4)
        cout << i << " ";
    cout << endl;

    cout << "c5 = ";
    for (int i : c5)
        cout << i << " ";
    cout << endl;

    cout << "c6 = ";
    for (int i : c6)
        cout << i << " ";
    cout << endl;

    // Move deque c6 to deque c7
    deque <int> c7(move(c6));
    deque <int>::iterator c7_Iter;

    cout << "c7 =";
    for (int i : c7)
        cout << i << " ";
    cout << endl;

    cout << "c8 = ";
    for (int i : c8)
        cout << i << " ";
    cout << endl;

    cout << "c9 = ";
    for (int i : c9)
        cout << i << " ";
    cout << endl;

    int x = 3;
}
// deque_deque.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
    using namespace std;
   deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;

    // Create an empty deque c0
    deque <int> c0;

    // Create a deque c1 with 3 elements of default value 0
    deque <int> c1( 3 );

    // Create a deque c2 with 5 elements of value 2
    deque <int> c2( 5, 2 );

    // Create a deque c3 with 3 elements of value 1 and with the
    // allocator of deque c2
    deque <int> c3( 3, 1, c2.get_allocator( ) );

    // Create a copy, deque c4, of deque c2
    deque <int> c4( c2 );

    // Create a deque c5 by copying the range c4[ first,  last)
    c4_Iter = c4.begin( );
    c4_Iter++;
    c4_Iter++;
    deque <int> c5( c4.begin( ), c4_Iter );

    // Create a deque c6 by copying the range c4[ first,  last) and
    // c2 with the allocator of deque
    c4_Iter = c4.begin( );
   c4_Iter++;
   c4_Iter++;
   c4_Iter++;
   deque <int> c6( c4.begin( ), c4_Iter, c2.get_allocator( ) );

    // Create a deque c8 by copying the contents of an initializer_list
    // using brace initialization
    deque<int> c8({ 1, 2, 3, 4 });

        initializer_list<int> iList{ 5, 6, 7, 8 };
    deque<int> c9( iList);

    cout << "c1 = ";
    for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
        cout << *c1_Iter << " ";
    cout << endl;

    cout << "c2 = ";
    for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
        cout << *c2_Iter << " ";
    cout << endl;

    cout << "c3 = ";
    for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
        cout << *c3_Iter << " ";
    cout << endl;

    cout << "c4 = ";
    for ( c4_Iter = c4.begin( ); c4_Iter != c4.end( ); c4_Iter++ )
        cout << *c4_Iter << " ";
    cout << endl;

    cout << "c5 = ";
    for ( c5_Iter = c5.begin( ); c5_Iter != c5.end( ); c5_Iter++ )
        cout << *c5_Iter << " ";
    cout << endl;

    cout << "c6 = ";
    for ( c6_Iter = c6.begin( ); c6_Iter != c6.end( ); c6_Iter++ )
        cout << *c6_Iter << " ";
    cout << endl;

    // Move deque c6 to deque c7
    deque <int> c7( move(c6) );
    deque <int>::iterator c7_Iter;

    cout << "c7 =" ;
    for ( c7_Iter = c7.begin( ) ; c7_Iter != c7.end( ) ; c7_Iter++ )
        cout << " " << *c7_Iter;
    cout << endl;

    cout << "c8 = ";
    for (int i : c8)
        cout << i << " ";
    cout << endl;

    cout << "c9 = ";
    or (int i : c9)
        cout << i << " ";
    cout << endl;
}
```

## <a name="difference_type"></a>  deque::difference_type

Tipo que proporciona la diferencia entre dos iteradores que hacen referencia a elementos del mismo deque.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Comentarios

Un `difference_type` también se puede describir como el número de elementos entre dos punteros.

### <a name="example"></a>Ejemplo

```cpp
// deque_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <deque>
#include <algorithm>

int main( )
{
   using namespace std;

   deque <int> c1;
   deque <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

   deque <int>::difference_type df_typ1, df_typ2, df_typ3;

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

## <a name="emplace"></a>  deque::emplace

Inserta en una posición especificada del deque un elemento construido en contexto.

```cpp
iterator emplace(
    const_iterator _Where,
    Type&& val);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*_WHERE*|Posición del [deque](../standard-library/deque-class.md) en la que se inserta el primer elemento.|
|*Val*|Valor del elemento insertado en el `deque`.|

### <a name="return-value"></a>Valor devuelto

La función devuelve un iterador que apunta a la posición en la que se ha insertado el nuevo elemento en el deque.

### <a name="remarks"></a>Comentarios

Las operaciones de inserción pueden ser costosas, vea `deque` para obtener una explicación del rendimiento de un `deque`.

### <a name="example"></a>Ejemplo

```cpp
// deque_emplace.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

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

## <a name="emplace_back"></a>  deque::emplace_back

Agrega al final del deque un elemento construido en contexto.

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Val*|El elemento que se agrega al final del [deque](../standard-library/deque-class.md).|

### <a name="example"></a>Ejemplo

```cpp
// deque_emplace_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;

   v1.push_back( 1 );
   if ( v1.size( ) != 0 )
      cout << "Last element: " << v1.back( ) << endl;

   v1.push_back( 2 );
   if ( v1.size( ) != 0 )
      cout << "New last element: " << v1.back( ) << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace_back( move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      cout << "Moved last element: " << vv1[0].back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved last element: 2
```

## <a name="emplace_front"></a>  deque::emplace_front

Agrega al final del deque un elemento construido en contexto.

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Val*|El elemento que se agrega al principio del [deque](../standard-library/deque-class.md).|

### <a name="example"></a>Ejemplo

```cpp
// deque_emplace_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;

   v1.push_back( 1 );
   if ( v1.size( ) != 0 )
      cout << "Last element: " << v1.back( ) << endl;

   v1.push_back( 2 );
   if ( v1.size( ) != 0 )
      cout << "New last element: " << v1.back( ) << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace_front( move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      cout << "Moved last element: " << vv1[0].back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved last element: 2
```

## <a name="empty"></a>  deque::empty

Comprueba si un deque está vacío.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valor devuelto

**True** si el deque está vacío; **False** si no lo está.

### <a name="example"></a>Ejemplo

```cpp
// deque_empty.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   if ( c1.empty( ) )
      cout << "The deque is empty." << endl;
   else
      cout << "The deque is not empty." << endl;
}
```

```Output
The deque is not empty.
```

## <a name="end"></a>  deque::end

Devuelve un iterador que se dirige a la ubicación que sigue al último elemento de un deque.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Valor devuelto

Un iterador de acceso aleatorio que se dirige a la ubicación que sigue al último elemento de un deque. Si el deque está vacío, deque::end == deque::begin.

### <a name="remarks"></a>Comentarios

`end` se usa para comprobar si un iterador ha llegado al final de su deque.

### <a name="example"></a>Ejemplo

```cpp
// deque_end.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_Iter = c1.end( );
   c1_Iter--;
   cout << "The last integer of c1 is " << *c1_Iter << endl;

   c1_Iter--;
 *c1_Iter = 400;
   cout << "The new next-to-last integer of c1 is " << *c1_Iter << endl;

   // If a const iterator had been declared instead with the line:
   // deque <int>::const_iterator c1_Iter;
   // an error would have resulted when inserting the 400

   cout << "The deque is now:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
}
```

```Output
The last integer of c1 is 30
The new next-to-last integer of c1 is 400
The deque is now: 10 400 30
```

## <a name="erase"></a>  deque::erase

Quita un elemento o un intervalo de elementos de un deque de las posiciones especificadas.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>Parámetros

*_WHERE* posición del elemento que se quitará del deque.

*primera* posición del primer elemento se ha quitado del deque.

*último* posición inmediatamente siguiente al último elemento se ha quitado del deque.

### <a name="return-value"></a>Valor devuelto

Un iterador de acceso aleatorio que designa el primer elemento restante después de los elementos quitados o, si no hay ningún elemento después, un puntero al final del deque.

### <a name="remarks"></a>Comentarios

`erase` nunca inicia una excepción.

### <a name="example"></a>Ejemplo

```cpp
// deque_erase.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 40 );
   c1.push_back( 50 );
   cout << "The initial deque is: ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
   c1.erase( c1.begin( ) );
   cout << "After erasing the first element, the deque becomes:  ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
   Iter = c1.begin( );
   Iter++;
   c1.erase( Iter, c1.end( ) );
   cout << "After erasing all elements but the first, deque becomes: ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
}
```

```Output
The initial deque is: 10 20 30 40 50
After erasing the first element, the deque becomes:  20 30 40 50
After erasing all elements but the first, deque becomes: 20
```

## <a name="front"></a>  deque::front

Devuelve una referencia al primer elemento de un deque.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Valor devuelto

Si el deque está vacío, el valor devuelto es indefinido.

### <a name="remarks"></a>Comentarios

Si el valor devuelto de `front` se asigna a un `const_reference`, el objeto deque no se puede modificar. Si el valor devuelto de `front` se asigna a un `reference`, el objeto deque se puede modificar.

Al compilar con [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definido como 1 o 2, se producirá un error en tiempo de ejecución si intenta acceder a un elemento en un deque vacío.  Vea [Iteradores comprobados](../standard-library/checked-iterators.md) para obtener más información.

### <a name="example"></a>Ejemplo

```cpp
// deque_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.front( );
   const int& ii = c1.front( );

   cout << "The first integer of c1 is " << i << endl;
   i++;
   cout << "The second integer of c1 is " << ii << endl;
}
```

```Output
The first integer of c1 is 10
The second integer of c1 is 11
```

## <a name="get_allocator"></a>  deque::get_allocator

Devuelve una copia del objeto de asignador usado para construir el deque.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Valor devuelto

El asignador usado por el deque.

### <a name="remarks"></a>Comentarios

Los asignadores de la clase deque especifican cómo la clase administra el almacenamiento. Los asignadores predeterminados proporcionados con las clases contenedoras de la biblioteca estándar de C++ son suficientes para la mayoría de las necesidades de programación. La escritura y el uso de sus propias clases de asignador son temas avanzados de C++.

### <a name="example"></a>Ejemplo

```cpp
// deque_get_allocator.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects that use the default allocator.
   deque <int> c1;
   deque <int, allocator<int> > c2 = deque <int, allocator<int> >( allocator<int>( ) );

   // c3 will use the same allocator class as c1
   deque <int> c3( c1.get_allocator( ) );

   deque <int>::allocator_type xlst = c1.get_allocator( );
   // You can now call functions on the allocator class used by c1
}
```

## <a name="insert"></a>  deque::insert

Inserta un elemento, varios elementos o un intervalo de elementos en el deque en una posición especificada.

```cpp
iterator insert(
    const_iterator Where,
    const Type& Val);

iterator insert(
    const_iterator Where,
    Type&& Val);

void insert(
    iterator Where,
    size_type Count,
    const Type& Val);

template <class InputIterator>
void insert(
    iterator Where,
    InputIterator First,
    InputIterator Last);

iterator insert(
    iterator Where,initializer_list<Type>
IList);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Where*|Posición del deque de destino donde se inserta el primer elemento.|
|*Val*|Valor del elemento que se va a insertar en el deque.|
|*Recuento*|Número de elementos que se van a insertar en el deque.|
|*Primero*|Posición del primer elemento en el intervalo de elementos del argumento deque que se va a copiar.|
|*Último*|Posición del primer elemento más allá del intervalo de elementos del argumento deque que se va a copiar.|
|*IList*|initializer_list de los elementos que se van a insertar.|

### <a name="return-value"></a>Valor devuelto

Las dos primeras funciones insert devuelven un iterador que apunta a la posición donde se insertó el nuevo elemento en el deque.

### <a name="remarks"></a>Comentarios

Las operaciones de inserción pueden ser muy costosas.

## <a name="iterator"></a>  deque::iterator

Tipo que proporciona un iterador de acceso aleatorio que puede leer o modificar cualquier elemento de un deque.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Comentarios

Un tipo `iterator` puede usarse para modificar el valor de un elemento.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [begin](#begin).

## <a name="max_size"></a>  deque::max_size

Devuelve la longitud máxima del deque.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valor devuelto

Longitud máxima posible del deque.

### <a name="example"></a>Ejemplo

```cpp
// deque_max_size.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::size_type i;

   i = c1.max_size( );
   cout << "The maximum possible length of the deque is " << i << "." << endl;
}
```

## <a name="op_at"></a>  deque::operator[]

Devuelve una referencia al elemento del deque en una posición especificada.

```cpp
reference operator[](size_type pos);

const_reference operator[](size_type pos) const;
```

### <a name="parameters"></a>Parámetros

*PDV* la posición del elemento deque al que se hace referencia.

### <a name="return-value"></a>Valor devuelto

Una referencia al elemento cuya posición se especifica en el argumento. Si la posición especificada es mayor que el tamaño del deque, el resultado no está definido.

### <a name="remarks"></a>Comentarios

Si el valor devuelto de `operator[]` se asigna a un `const_reference`, el objeto deque no se puede modificar. Si el valor devuelto de `operator[]` se asigna a un `reference`, el objeto deque se puede modificar.

Al compilar con [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definido como 1 o 2, se producirá un error en tiempo de ejecución si intenta acceder a un elemento fuera de los límites del deque.  Vea [Iteradores comprobados](../standard-library/checked-iterators.md) para obtener más información.

### <a name="example"></a>Ejemplo

```cpp
// deque_op_ref.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   cout << "The first integer of c1 is " << c1[0] << endl;
   int& i = c1[1];
   cout << "The second integer of c1 is " << i << endl;

}
```

```Output
The first integer of c1 is 10
The second integer of c1 is 20
```

## <a name="op_eq"></a>  deque::operator=

Reemplaza los elementos de este deque con los elementos de otro deque.

```cpp
deque& operator=(const deque& right);

deque& operator=(deque&& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*right*|Deque que proporciona el nuevo contenido.|

### <a name="remarks"></a>Comentarios

La primera invalidación copia elementos en este deque desde *derecho*, el origen de la asignación. La segunda invalidación mueve elementos a este deque desde *derecho*.

Se quitan los elementos contenidos en este deque antes de que se ejecute el operador.

### <a name="example"></a>Ejemplo

```cpp
// deque_operator_as.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
using namespace std;

typedef deque<int> MyDeque;

template<typename MyDeque> struct S;

template<typename MyDeque> struct S<MyDeque&> {
  static void show( MyDeque& d ) {
    MyDeque::const_iterator iter;
    for (iter = d.cbegin(); iter != d.cend(); iter++)
       cout << *iter << " ";
    cout << endl;
  }
};

template<typename MyDeque> struct S<MyDeque&&> {
  static void show( MyDeque&& d ) {
    MyDeque::const_iterator iter;
    for (iter = d.cbegin(); iter != d.cend(); iter++)
       cout << *iter << " ";
cout << " via unnamed rvalue reference " << endl;
  }
};

int main( )
{
   MyDeque d1, d2;

   d1.push_back(10);
   d1.push_back(20);
   d1.push_back(30);
   d1.push_back(40);
   d1.push_back(50);

   cout << "d1 = " ;
   S<MyDeque&>::show( d1 );

   d2 = d1;
   cout << "d2 = ";
   S<MyDeque&>::show( d2 );

   cout << "     ";
   S<MyDeque&&>::show ( move< MyDeque& > (d1) );
 }
```

## <a name="pointer"></a>  deque::pointer

Proporciona un puntero a un elemento de un [deque](../standard-library/deque-class.md).

```unstlib
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Comentarios

Un tipo `pointer` puede usarse para modificar el valor de un elemento. Un [iterator](#iterator) se usa normalmente para tener acceso a un elemento de deque.

## <a name="pop_back"></a>  deque::pop_back

Elimina el elemento situado al final del deque.

```cpp
void pop_back();
```

### <a name="remarks"></a>Comentarios

El último elemento no debe estar vacío. `pop_back` nunca inicia una excepción.

### <a name="example"></a>Ejemplo

```cpp
// deque_pop_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The last element is: " << c1.back( ) << endl;

   c1.pop_back( );
   cout << "After deleting the element at the end of the deque, the "
      "last element is: " << c1.back( ) << endl;
}
```

```Output
The first element is: 1
The last element is: 2
After deleting the element at the end of the deque, the last element is: 1
```

## <a name="pop_front"></a>  deque::pop_front

Elimina el elemento situado al principio del deque.

```cpp
void pop_front();
```

### <a name="remarks"></a>Comentarios

El primer elemento no debe estar vacío. `pop_front` nunca inicia una excepción.

### <a name="example"></a>Ejemplo

```cpp
// deque_pop_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The second element is: " << c1.back( ) << endl;

   c1.pop_front( );
   cout << "After deleting the element at the beginning of the "
      "deque, the first element is: " << c1.front( ) << endl;
}
```

```Output
The first element is: 1
The second element is: 2
After deleting the element at the beginning of the deque, the first element is: 2
```

## <a name="push_back"></a>  deque::push_back

Agrega un elemento al final del deque.

```cpp
void push_back(const Type& val);

void push_back(Type&& val);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Val*|El elemento que se agrega al final del deque.|

### <a name="remarks"></a>Comentarios

Si se lanza una excepción, el deque se deja sin modificar y se vuelve a iniciar la excepción.

## <a name="push_front"></a>  deque::push_front

Agrega un elemento al principio del deque.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Val*|El elemento que se agrega al principio del deque.|

### <a name="remarks"></a>Comentarios

Si se lanza una excepción, el deque se deja sin modificar y se vuelve a iniciar la excepción.

### <a name="example"></a>Ejemplo

```cpp
// deque_push_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_front( 1 );
   if ( c1.size( ) != 0 )
      cout << "First element: " << c1.front( ) << endl;

   c1.push_front( 2 );
   if ( c1.size( ) != 0 )
      cout << "New first element: " << c1.front( ) << endl;

// move initialize a deque of strings
   deque <string> c2;
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

## <a name="rbegin"></a>  deque::rbegin

Devuelve un iterador al primer elemento en un deque inverso.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Valor devuelto

Un iterador inverso de acceso aleatorio que se dirige al primer elemento de un deque inverso o al que fue el último elemento del deque sin invertir.

### <a name="remarks"></a>Comentarios

`rbegin` se usa con un deque invertido igual que [begin](#begin) se usa con un deque.

Si el valor devuelto de `rbegin` se asigna a un `const_reverse_iterator`, el objeto deque no se puede modificar. Si el valor devuelto de `rbegin` se asigna a un `reverse_iterator`, el objeto deque se puede modificar.

`rbegin` puede usarse para iterar un deque hacia atrás.

### <a name="example"></a>Ejemplo

```cpp
// deque_rbegin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::reverse_iterator c1_rIter;

   // If the following line had replaced the line above, an error
   // would have resulted in the line modifying an element
   // (commented below) because the iterator would have been const
   // deque <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rbegin( );
   cout << "Last element in the deque is " << *c1_rIter << "." << endl;

   cout << "The deque contains the elements: ";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << *c1_Iter << " ";
   cout << "in that order.";
   cout << endl;

   // rbegin can be used to iterate through a deque in reverse order
   cout << "The reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;

   c1_rIter = c1.rbegin( );
 *c1_rIter = 40;  // This would have caused an error if a
                    // const_reverse iterator had been declared as
                    // noted above
   cout << "Last element in deque is now " << *c1_rIter << "." << endl;
}
```

```Output
Last element in the deque is 30.
The deque contains the elements: 10 20 30 in that order.
The reversed deque is: 30 20 10
Last element in deque is now 40.
```

## <a name="reference"></a>  deque::reference

Tipo que proporciona una referencia a un elemento almacenado en un deque.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>Ejemplo

```cpp
// deque_reference.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const int &i = c1.front( );
   int &j = c1.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="rend"></a>  deque::rend

Devuelve un iterador que se dirige a la ubicación que sigue al último elemento en un deque invertido.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Valor devuelto

Un iterador inverso de acceso aleatorio que se dirige a la ubicación siguiente al último elemento de un deque invertido (la ubicación que había precedido al primer elemento del deque sin invertir).

### <a name="remarks"></a>Comentarios

`rend` se usa con un deque invertido igual que [end](#end) se usa con un deque.

Si el valor devuelto de `rend` se asigna a un `const_reverse_iterator`, el objeto deque no se puede modificar. Si el valor devuelto de `rend` se asigna a un `reverse_iterator`, el objeto deque se puede modificar.

Se puede usar `rend` para comprobar si un iterador inverso ha llegado al final de su deque.

El valor devuelto por `rend` no se debe desreferenciar.

### <a name="example"></a>Ejemplo

```cpp
// deque_rend.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;

   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::reverse_iterator c1_rIter;
   // If the following line had replaced the line above, an error
   // would have resulted in the line modifying an element
   // (commented below) because the iterator would have been const
   // deque <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rend( );
   c1_rIter --; // Decrementing a reverse iterator moves it forward
                // in the deque (to point to the first element here)
   cout << "The first element in the deque is: " << *c1_rIter << endl;

   cout << "The deque is: ";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << *c1_Iter << " ";
   cout << endl;

   // rend can be used to test if an iteration is through all of
   // the elements of a reversed deque
   cout << "The reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;

   c1_rIter = c1.rend( );
   c1_rIter--; // Decrementing the reverse iterator moves it backward
               // in the reversed deque (to the last element here)
 *c1_rIter = 40; // This modification of the last element would
                   // have caused an error if a const_reverse
                   // iterator had been declared (as noted above)
   cout << "The modified reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;
}
```

```Output
The first element in the deque is: 10
The deque is: 10 20 30
The reversed deque is: 30 20 10
The modified reversed deque is: 30 20 40
```

## <a name="resize"></a>  deque::resize

Especifica un nuevo tamaño de un deque.

```cpp
void resize(size_type _Newsize);

void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>Parámetros

*_Newsize* el nuevo tamaño del deque.

*Val* el valor de los nuevos elementos que se agregarán al deque si el nuevo tamaño es mayor que el tamaño original. Si el valor se omite, a los nuevos elementos se les asigna el valor predeterminado para la clase.

### <a name="remarks"></a>Comentarios

Si el tamaño del deque es menor que el tamaño solicitado, *_Newsize*, se agregan elementos al deque hasta que alcance el tamaño solicitado.

Si el tamaño del deque es mayor que el tamaño solicitado, se eliminan los elementos más cercanos al final del deque hasta que este alcanza el tamaño *_Newsize*.

Si el tamaño actual del deque es igual que el tamaño solicitado, no se lleva a cabo ninguna acción.

[size](#size) refleja el tamaño actual del deque.

### <a name="example"></a>Ejemplo

```cpp
// deque_resize.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1.resize( 4,40 );
   cout << "The size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is " << c1.back( ) << endl;

   c1.resize( 5 );
   cout << "The size of c1 is now: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;

   c1.resize( 2 );
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;
}
```

```Output
The size of c1 is: 4
The value of the last element is 40
The size of c1 is now: 5
The value of the last element is now 0
The reduced size of c1 is: 2
The value of the last element is now 20
```

## <a name="reverse_iterator"></a>  deque::reverse_iterator

Tipo que proporciona un iterador de acceso aleatorio que puede leer o modificar un elemento de un deque invertido.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Comentarios

Un tipo `reverse_iterator` se usa para iterar en el deque.

### <a name="example"></a>Ejemplo

Vea el ejemplo de rbegin.

## <a name="shrink_to_fit"></a>  deque::shrink_to_fit

Descarta el exceso de capacidad.

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>Comentarios

No hay ninguna manera portátil de determinar si `shrink_to_fit` reduce el almacenamiento usado por un [deque](../standard-library/deque-class.md).

### <a name="example"></a>Ejemplo

```cpp
// deque_shrink_to_fit.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   //deque <int>::iterator Iter;

   v1.push_back( 1 );
   v1.push_back( 2 );
   cout << "Current size of v1 = "
      << v1.size( ) << endl;
   v1.shrink_to_fit();
   cout << "Current size of v1 = "
      << v1.size( ) << endl;
}
```

```Output
Current size of v1 = 1
Current size of v1 = 1
```

## <a name="size"></a>  deque::size

Devuelve el número de elementos del deque.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valor devuelto

Longitud actual del deque.

### <a name="example"></a>Ejemplo

```cpp
// deque_size.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::size_type i;

   c1.push_back( 1 );
   i = c1.size( );
   cout << "The deque length is " << i << "." << endl;

   c1.push_back( 2 );
   i = c1.size( );
   cout << "The deque length is now " << i << "." << endl;
}
```

```Output
The deque length is 1.
The deque length is now 2.
```

## <a name="size_type"></a>  deque::size_type

Tipo que cuenta el número de elementos de un deque.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [size](#size).

## <a name="swap"></a>  deque::swap

Intercambia los elementos de dos deques.

```cpp
void swap(deque<Type, Allocator>& right);

friend void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right) template <class Type, class Allocator>
void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*derecha* deque que proporciona los elementos que se van a intercambiar o el deque cuyos elementos se van a intercambiar con los del deque `left`.

*izquierdo* un deque cuyos elementos se van a intercambiar con los del deque *derecho*.

### <a name="example"></a>Ejemplo

```cpp
// deque_swap.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2, c3;
   deque <int>::iterator c1_Iter;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 3 );
   c2.push_back( 10 );
   c2.push_back( 20 );
   c3.push_back( 100 );

   cout << "The original deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.swap( c2 );

   cout << "After swapping with c2, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap( c1,c3 );

   cout << "After swapping with c3, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap<>(c1, c2);
   cout << "After swapping with c2, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
The original deque c1 is: 1 2 3
After swapping with c2, deque c1 is: 10 20
After swapping with c3, deque c1 is: 100
After swapping with c2, deque c1 is: 1 2 3
```

## <a name="value_type"></a>  deque::value_type

Tipo que representa el tipo de datos almacenados en un deque.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Comentarios

`value_type` es un sinónimo del parámetro de plantilla `Type`.

### <a name="example"></a>Ejemplo

```cpp
// deque_value_type.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
int main( )
{
   using namespace std;
   deque<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
