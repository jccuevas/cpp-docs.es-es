---
title: Clase array (Biblioteca estándar de C++)| Microsoft Docs
ms.date: 11/13/2019
f1_keywords:
- array/std::array
- array/std::array::const_iterator
- array/std::array::const_pointer
- array/std::array::const_reference
- array/std::array::const_reverse_iterator
- array/std::array::difference_type
- array/std::array::iterator
- array/std::array::pointer
- array/std::array::reference
- array/std::array::reverse_iterator
- array/std::array::size_type
- array/std::array::value_type
- array/std::array::assign
- array/std::array::at
- array/std::array::back
- array/std::array::begin
- array/std::array::cbegin
- array/std::array::cend
- array/std::array::crbegin
- array/std::array::crend
- array/std::array::data
- array/std::array::empty
- array/std::array::end
- array/std::array::fill
- array/std::array::front
- array/std::array::max_size
- array/std::array::rbegin
- array/std::array::rend
- array/std::array::size
- array/std::array::swap
- array/std::array::operator=
- array/std::array::operator[]
helpviewer_keywords:
- std::array [C++]
- std::array [C++], const_iterator
- std::array [C++], const_pointer
- std::array [C++], const_reference
- std::array [C++], const_reverse_iterator
- std::array [C++], difference_type
- std::array [C++], iterator
- std::array [C++], pointer
- std::array [C++], reference
- std::array [C++], reverse_iterator
- std::array [C++], size_type
- std::array [C++], value_type
- std::array [C++], assign
- std::array [C++], at
- std::array [C++], back
- std::array [C++], begin
- std::array [C++], cbegin
- std::array [C++], cend
- std::array [C++], crbegin
- std::array [C++], crend
- std::array [C++], data
- std::array [C++], empty
- std::array [C++], end
- std::array [C++], fill
- std::array [C++], front
- std::array [C++], max_size
- std::array [C++], rbegin
- std::array [C++], rend
- std::array [C++], size
- std::array [C++], swap
- ', '
- std::array [C++], const_iterator
- std::array [C++], const_pointer
- std::array [C++], const_reference
- std::array [C++], const_reverse_iterator
- std::array [C++], difference_type
- std::array [C++], iterator
- std::array [C++], pointer
- std::array [C++], reference
- std::array [C++], reverse_iterator
- std::array [C++], size_type
- std::array [C++], value_type
- std::array [C++], assign
- std::array [C++], at
- std::array [C++], back
- std::array [C++], begin
- std::array [C++], cbegin
- std::array [C++], cend
- std::array [C++], crbegin
- std::array [C++], crend
- std::array [C++], data
- std::array [C++], empty
- std::array [C++], end
- std::array [C++], fill
- std::array [C++], front
- std::array [C++], max_size
- std::array [C++], rbegin
- std::array [C++], rend
- std::array [C++], size
- std::array [C++], swap
ms.assetid: fdfd43a5-b2b5-4b9e-991f-93bf10fb4293
ms.openlocfilehash: 90c68d00475a622ec89b81cc86639f63b1190d02
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364944"
---
# <a name="array-class-c-standard-library"></a>Clase array (Biblioteca estándar de C++)

Describe un objeto que controla una secuencia de longitud `N` de elementos de tipo `Ty`. La secuencia se almacena como matriz de `Ty`, que se encuentra en el objeto `array<Ty, N>`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty, std::size_t N>
class array;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|`Ty`|El tipo de un elemento.|
|`N`|Número de elementos.|

## <a name="members"></a>Miembros

|Definición de tipo|Descripción|
|-|-|
|[const_iterator](#const_iterator)|El tipo de un iterador constante para la secuencia controlada.|
|[const_pointer](#const_pointer)|El tipo de un puntero constante a un elemento.|
|[const_reference](#const_reference)|El tipo de una referencia constante a un elemento.|
|[const_reverse_iterator](#const_reverse_iterator)|El tipo de un iterador invertido constante para la secuencia controlada.|
|[difference_type](#difference_type)|El tipo de una distancia con signo entre dos elementos.|
|[Iterador](#iterator)|El tipo de un iterador para la secuencia controlada.|
|[puntero](#pointer)|El tipo de un puntero a un elemento.|
|[Referencia](#reference)|El tipo de una referencia a un elemento.|
|[reverse_iterator](#reverse_iterator)|El tipo de un iterador invertido para la secuencia controlada.|
|[size_type](#size_type)|El tipo de una distancia sin signo entre dos elementos.|
|[value_type](#value_type)|El tipo de un elemento.|

|Función miembro|Descripción|
|-|-|
|[array](#array)|Construye un objeto de matriz.|
|[Asignar](#assign)|(Obsoleto. Usar `fill`.) Reemplaza todos los elementos.|
|[En](#at)|Obtiene acceso a un elemento en una posición especificada.|
|[Atrás](#back)|Obtiene acceso al último elemento.|
|[Comenzar](#begin)|Designa el principio de la secuencia controlada.|
|[cbegin](#cbegin)|Devuelve un iterador const de acceso aleatorio al primer elemento de la matriz.|
|[cend](#cend)|Devuelve un iterador const de acceso aleatorio que apunta justo después del final de la matriz.|
|[crbegin](#crbegin)|Devuelve un iterador constante al primer elemento de una matriz inversa.|
|[crend](#crend)|Devuelve un iterador constante al final de una matriz invertida.|
|[datos](#data)|Obtiene la dirección del primer elemento.|
|[Vacío](#empty)|Comprueba si hay algún elemento presente.|
|[Final](#end)|Designa el final de la secuencia controlada.|
|[Llenar](#fill)|Reemplaza todos los elementos por un valor especificado.|
|[Frente](#front)|Obtiene acceso al primer elemento.|
|[max_size](#max_size)|Cuenta el número de elementos.|
|[rbegin](#rbegin)|Designa el principio de la secuencia controlada inversa.|
|[rend](#rend)|Designa el final de la secuencia controlada inversa.|
|[Tamaño](#size)|Cuenta el número de elementos.|
|[swap](#swap)|Intercambia el contenido de dos contenedores.|

|Operator|Descripción|
|-|-|
|[matriz::operador ?](#op_eq)|Reemplaza la secuencia controlada.|
|[array::operator\[\]](#op_at)|Obtiene acceso a un elemento en una posición especificada.|

## <a name="remarks"></a>Observaciones

El tipo tiene un constructor predeterminado `array()` y un operador de asignación predeterminado `operator=`, y cumple los requisitos de un `aggregate`. Por lo tanto, los objetos de tipo `array<Ty, N>` se pueden inicializar con un inicializador agregado. Por ejemplo,

```cpp
array<int, 4> ai = { 1, 2, 3 };
```

crea el objeto `ai` que contiene cuatro valores enteros, inicializa los tres primeros elementos a los valores 1, 2 y 3, respectivamente, e inicializa el cuarto a 0.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<array>

**Espacio de nombres:** std

## <a name="arrayarray"></a><a name="array"></a>array::array

Construye un objeto de matriz.

```cpp
array();

array(const array& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Objeto o intervalo que se va a insertar.

### <a name="remarks"></a>Observaciones

El constructor predeterminado `array()` deja la secuencia controlada sin inicializar (o inicializada de forma predeterminada). Se usa para especificar una secuencia controlada sin inicializar.

El constructor `array(const array& right)` de copias inicializa la secuencia controlada con la secuencia [*right*`.begin()`, *right*`.end()`). Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de matriz *right*.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    typedef std::array<int, 4> Myarray;

    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1(c0);

    // display contents " 0 1 2 3"
    for (const auto& it : c1)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="arrayassign"></a><a name="assign"></a>array::assign

Obsoleto en C++11, se ha sustituido por [fill](#fill). Reemplaza todos los elementos.

## <a name="arrayat"></a><a name="at"></a>array::at

Obtiene acceso a un elemento en una posición especificada.

```cpp
reference at(size_type off);

constexpr const_reference at(size_type off) const;
```

### <a name="parameters"></a>Parámetros

*fuera*\
Posición del elemento al que se accederá.

### <a name="remarks"></a>Observaciones

Las funciones miembro devuelven una referencia al elemento de la secuencia controlada en la posición *desactivada.* Si esa posición no es válida, la función produce un objeto de clase `out_of_range`.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display odd elements " 1 3"
    std::cout << " " << c0.at(1);
    std::cout << " " << c0.at(3);
    std::cout << std::endl;

    return (0);
}
```

## <a name="arrayback"></a><a name="back"></a>array::back

Obtiene acceso al último elemento.

```cpp
reference back();

constexpr const_reference back() const;
```

### <a name="remarks"></a>Observaciones

Las funciones miembro devuelven una referencia al último elemento de la secuencia controlada, que no debe estar vacío.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    std::cout << " " << c0.back();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="arraybegin"></a><a name="begin"></a>array::begin

Designa el principio de la secuencia controlada.

```cpp
iterator begin() noexcept;
const_iterator begin() const noexcept;
```

### <a name="remarks"></a>Observaciones

Las funciones miembro devuelven un iterador de acceso aleatorio que apunta al primer elemento de la secuencia (o más allá del final de una secuencia vacía).

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::iterator it2 = c0.begin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arraycbegin"></a><a name="cbegin"></a>array::cbegin

Devuelve un **iterador const** que direcciona el primer elemento del intervalo.

```cpp
const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Iterador de acceso aleatorio **const** que apunta al primer elemento del intervalo o a la ubicación `cbegin() == cend()`justo más allá del final de un intervalo vacío (para un intervalo vacío, ).

### <a name="remarks"></a>Observaciones

Con el valor devuelto de `cbegin`, los elementos del intervalo no se pueden modificar.

Se puede usar esta función miembro en lugar de la función miembro `begin()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el `Container` ejemplo, considere que es un contenedor modificable (no **const**) de cualquier tipo que admita `begin()` y `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="arraycend"></a><a name="cend"></a>array::cend

Devuelve un **iterador const** que direcciona la ubicación justo más allá del último elemento de un intervalo.

```cpp
const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Iterador de acceso aleatorio que apunta justo después del final del intervalo.

### <a name="remarks"></a>Observaciones

`cend` se usa para probar si un iterador ha sobrepasado el final de su intervalo.

Se puede usar esta función miembro en lugar de la función miembro `end()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el `Container` ejemplo, considere que es un contenedor modificable (no **const**) de cualquier tipo que admita `end()` y `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

El valor devuelto por `cend` no se debe desreferenciar.

## <a name="arrayconst_iterator"></a><a name="const_iterator"></a>array::const_iterator

El tipo de un iterador constante para la secuencia controlada.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto que puede actuar como un iterador de acceso aleatorio constante para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for (MyArray::const_iterator it1 = c0.begin();
        it1 != c0.end();
        ++it1) {
        std::cout << " " << *it1;
    }
    std::cout << std::endl;

    // display first element " 0"
    MyArray::const_iterator it2 = c0.begin();
    std::cout << "it2:";
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
it1: 0 1 2 3
it2: 0
```

## <a name="arrayconst_pointer"></a><a name="const_pointer"></a>array::const_pointer

El tipo de un puntero constante a un elemento.

```cpp
typedef const Ty *const_pointer;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto que puede actuar como un puntero constante a elementos de la secuencia.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::const_pointer ptr = &*c0.begin();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayconst_reference"></a><a name="const_reference"></a>array::const_reference

El tipo de una referencia constante a un elemento.

```cpp
typedef const Ty& const_reference;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto que puede actuar como referencia constante a un elemento de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::const_reference ref = *c0.begin();
    std::cout << " " << ref;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>array::const_reverse_iterator

El tipo de un iterador invertido constante para la secuencia controlada.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto que puede actuar como un iterador inverso constante para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    Myarray::const_reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="arraycrbegin"></a><a name="crbegin"></a>array::crbegin

Devuelve un iterador constante al primer elemento de una matriz inversa.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador inverso constante de acceso aleatorio que dirige al primer elemento de una matriz inversa o al que fue el último elemento de la matriz sin invertir.

### <a name="remarks"></a>Observaciones

Con el valor devuelto de `crbegin`, el objeto de matriz no se puede modificar.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::iterator v1_Iter;
   array<int, 2>::const_reverse_iterator v1_rIter;

   v1_Iter = v1.begin( );
   cout << "The first element of array is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed array is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of array is 1.
The first element of the reversed array is 2.
```

## <a name="arraycrend"></a><a name="crend"></a>array::crend

Devuelve un iterador constante que dirige a la ubicación siguiente al último elemento de una matriz invertida.

```cpp
const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Iterador constante de acceso aleatorio inverso que dirige a la ubicación siguiente al último elemento de una matriz invertida (la ubicación que había precedido al primer elemento de la matriz sin invertir).

### <a name="remarks"></a>Observaciones

`crend` se usa con una matriz invertida igual que [array::cend](#cend) se emplea con una matriz.

Con el valor devuelto de `crend` (adecuadamente reducido), el objeto de matriz no se puede modificar.

Se puede utilizar `crend` para comprobar si un iterador inverso ha llegado al final de su matriz.

El valor devuelto por `crend` no se debe desreferenciar.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::const_reverse_iterator v1_rIter;

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="arraydata"></a><a name="data"></a>array::data

Obtiene la dirección del primer elemento.

```cpp
Ty *data();

const Ty *data() const;
```

### <a name="remarks"></a>Observaciones

Las funciones miembro devuelven la dirección del primer elemento de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::pointer ptr = c0.data();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arraydifference_type"></a><a name="difference_type"></a>array::difference_type

El tipo de una distancia con signo entre dos elementos.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Observaciones

El tipo de entero con signo describe un objeto que puede representar la diferencia entre las direcciones de dos elementos cualesquiera de la secuencia controlada. Es un sinónimo del tipo `std::ptrdiff_t`.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display distance first-last " -4"
    Myarray::difference_type diff = c0.begin() - c0.end();
    std::cout << " " << diff;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
-4
```

## <a name="arrayempty"></a><a name="empty"></a>array::empty

Comprueba si no hay ningún elemento presente.

```cpp
constexpr bool empty() const;
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve true solo si `N == 0`.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display whether c0 is empty " false"
    std::cout << std::boolalpha << " " << c0.empty();
    std::cout << std::endl;

    std::array<int, 0> c1;

    // display whether c1 is empty " true"
    std::cout << std::boolalpha << " " << c1.empty();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
false
true
```

## <a name="arrayend"></a><a name="end"></a>array::end

Designa el final de la secuencia controlada.

```cpp
reference end();

const_reference end() const;
```

### <a name="remarks"></a>Observaciones

Las funciones miembro devuelven un iterador de acceso aleatorio que apunta inmediatamente después del final de la secuencia.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    Myarray::iterator it2 = c0.end();
    std::cout << " " << *--it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="arrayfill"></a><a name="fill"></a>array::fill

Borra una matriz y copia los elementos especificados en la matriz vacía.

```cpp
void fill(const Type& val);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Val*|Valor del elemento que se va a insertar en la matriz.|

### <a name="remarks"></a>Observaciones

`fill` reemplaza cada elemento de la matriz por el valor especificado.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

int main()
{
    using namespace std;
    array<int, 2> v1 = { 1, 2 };

    cout << "v1 = ";
    for (const auto& it : v1)
    {
        std::cout << " " << it;
    }
    cout << endl;

    v1.fill(3);
    cout << "v1 = ";
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    cout << endl;
}
```

## <a name="arrayfront"></a><a name="front"></a>array::front

Obtiene acceso al primer elemento.

```cpp
reference front();

constexpr const_reference front() const;
```

### <a name="remarks"></a>Observaciones

Las funciones miembro devuelven una referencia al primer elemento de la secuencia controlada, que no debe estar vacío.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    std::cout << " " << c0.front();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayiterator"></a><a name="iterator"></a>array::iterator

El tipo de un iterador para la secuencia controlada.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto que puede actuar como un iterador de acceso aleatorio de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for (MyArray::iterator it1 = c0.begin();
        it1 != c0.end();
        ++it1) {
        std::cout << " " << *it1;
    }
    std::cout << std::endl;

    // display first element " 0"
    MyArray::iterator it2 = c0.begin();
    std::cout << "it2:";
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
it1: 0 1 2 3

it2: 0
```

## <a name="arraymax_size"></a><a name="max_size"></a>array::max_size

Cuenta el número de elementos.

```cpp
constexpr size_type max_size() const;
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve `N`.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display (maximum) size " 4"
    std::cout << " " << c0.max_size();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4
```

## <a name="arrayoperator"></a><a name="op_at"></a>array::operator[]

Obtiene acceso a un elemento en una posición especificada.

```cpp
reference operator[](size_type off);

constexpr const_reference operator[](size_type off) const;
```

### <a name="parameters"></a>Parámetros

*fuera*\
Posición del elemento al que se accederá.

### <a name="remarks"></a>Observaciones

Las funciones miembro devuelven una referencia al elemento de la secuencia controlada en la posición *desactivada.* Si esa posición no es válida, el comportamiento es indefinido.

También hay una función [get](array-functions.md#get) no miembro disponible para obtener una referencia a un elemento de una **matriz.**

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display odd elements " 1 3"
    std::cout << " " << c0[1];
    std::cout << " " << c0[3];
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
1 3
```

## <a name="arrayoperator"></a><a name="op_eq"></a>matriz::operador ?

Reemplaza la secuencia controlada.

```cpp
array<Value> operator=(array<Value> right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Contenedor que se va a copiar.

### <a name="remarks"></a>Observaciones

El operador miembro asigna cada elemento de *right* al elemento correspondiente `*this`de la secuencia controlada y, a continuación, devuelve . Se utiliza para reemplazar la secuencia controlada con una copia de la secuencia controlada a *la derecha.*

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1;
    c1 = c0;

    // display copied contents " 0 1 2 3"
        // display contents " 0 1 2 3"
    for (auto it : c1)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="arraypointer"></a><a name="pointer"></a>array::pointer

El tipo de un puntero a un elemento.

```cpp
typedef Ty *pointer;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto que puede actuar como un puntero a elementos de la secuencia.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::pointer ptr = &*c0.begin();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayrbegin"></a><a name="rbegin"></a>array::rbegin

Designa el principio de la secuencia controlada inversa.

```cpp
reverse_iterator rbegin()noexcept;
const_reverse_iterator rbegin() const noexcept;
```

### <a name="remarks"></a>Observaciones

Las funciones miembro devuelven un iterador inverso que apunta inmediatamente después del final de la secuencia controlada. Por tanto, designa el principio de la secuencia inversa.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    Myarray::const_reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="arrayreference"></a><a name="reference"></a>array::reference

El tipo de una referencia a un elemento.

```cpp
typedef Ty& reference;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto que puede actuar como referencia a un elemento de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::reference ref = *c0.begin();
    std::cout << " " << ref;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayrend"></a><a name="rend"></a>array::rend

Designa el final de la secuencia controlada inversa.

```cpp
reverse_iterator rend()noexcept;
const_reverse_iterator rend() const noexcept;
```

### <a name="remarks"></a>Observaciones

Las funciones miembro devuelven un iterador inverso que apunta al primer elemento de la secuencia (o más allá del final de una secuencia vacía). Por tanto, designa el final de la secuencia inversa.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::const_reverse_iterator it2 = c0.rend();
    std::cout << " " << *--it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="arrayreverse_iterator"></a><a name="reverse_iterator"></a>array::reverse_iterator

El tipo de un iterador invertido para la secuencia controlada.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto que puede actuar como un iterador inverso para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    Myarray::reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="arraysize"></a><a name="size"></a>array::size

Cuenta el número de elementos.

```cpp
constexpr size_type size() const;
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve `N`.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display size " 4"
    std::cout << " " << c0.size();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4
```

## <a name="arraysize_type"></a><a name="size_type"></a>array::size_type

Tipo de una distancia sin signo entre dos elementos.

```cpp
typedef std::size_t size_type;
```

### <a name="remarks"></a>Observaciones

El tipo de entero sin signo describe un objeto que puede representar la longitud de cualquier secuencia controlada. Es un sinónimo del tipo `std::size_t`.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display distance last-first " 4"
    Myarray::size_type diff = c0.end() - c0.begin();
    std::cout << " " << diff;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4
```

## <a name="arrayswap"></a><a name="swap"></a>array::swap

Intercambia el contenido de esta matriz con otra matriz.

```cpp
void swap(array& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Matriz con la que se va a intercambiar el contenido.

### <a name="remarks"></a>Observaciones

La función miembro intercambia las `*this` secuencias controladas entre y *derecha*. Realiza una serie de asignaciones de elementos y llamadas de contructores proporcionales a `N`.

También hay una función de [intercambio](array-functions.md#swap) no miembro disponible para intercambiar dos instancias de **matriz.**

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1 = { 4, 5, 6, 7 };
    c0.swap(c1);

    // display swapped contents " 4 5 6 7"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    swap(c0, c1);

    // display swapped contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4 5 6 7
0 1 2 3
```

## <a name="arrayvalue_type"></a><a name="value_type"></a>array::value_type

El tipo de un elemento.

```cpp
typedef Ty value_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla `Ty`.

### <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        Myarray::value_type val = it;
        std::cout << " " << val;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="see-also"></a>Consulte también

[\<matriz>](../standard-library/array.md)
