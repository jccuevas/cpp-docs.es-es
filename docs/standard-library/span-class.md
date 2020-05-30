---
title: span (clase, biblioteca estándar de C++) | Microsoft Docs
ms.date: 05/28/2020
f1_keywords:
- span/std::span
- span/std::span::const_pointer
- span/std::span::const_reference
- span/std::span::difference_type
- span/std::span::element_type
- span/std::span::iterator
- span/std::span::pointer
- span/std::span::reference
- span/std::span::reverse_iterator
- span/std::span::size_type
- span/std::span::value_type
- span/std::span::at
- span/std::span::assign
- span/std::span::back
- span/std::span::begin
- span/std::span::data
- span/std::span::empty
- span/std::span::end
- span/std::span::front
- span/std::span::rbegin
- span/std::span::rend
- span/std::span::size
- span/std::span::size_bytes
- span/std::span::operator=
- span/std::span::operator[]
helpviewer_keywords:
- std::span [C++]
- std::span [C++], const_pointer
- std::span [C++], const_reference
- std::span [C++], difference_type
- std::span [C++], element_type
- std::span [C++], iterator
- std::span [C++], pointer
- std::span [C++], reference
- std::span [C++], reverse_iterator
- std::span [C++], size_type
- std::span [C++], value_type
- std::span [C++], assign
- std::span [C++], at
- std::span [C++], back
- std::span [C++], begin
- std::span [C++], data
- std::span [C++], empty
- std::span [C++], end
- std::span [C++], front
- std::span [C++], rbegin
- std::span [C++], rend
- std::span [C++], size
- std::span [C++], size_bytes
ms.openlocfilehash: b76c1db2176c27983ccdcd4742f889f5a4d95af6
ms.sourcegitcommit: 1a8fac06478da8bee1f6d70e25afbad94144af1a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/30/2020
ms.locfileid: "84226323"
---
# <a name="span-class-c-standard-library"></a>span (clase, biblioteca estándar de C++)

Proporciona una vista ligera sobre una secuencia contigua de objetos. Un intervalo proporciona una manera segura de recorrer en iteración e indexar en los objetos que se organizan de nuevo en memoria, como los objetos almacenados en una matriz integrada, `std::array` o `std::vector` .

Si normalmente obtiene acceso a una secuencia de objetos que se van a devolver mediante un puntero y un índice, un `span` es una alternativa más segura y ligera.

El tamaño de un `span` se puede establecer en tiempo de compilación si se especifica como un argumento de plantilla o en tiempo de ejecución mediante la especificación de `dynamic_extent` .

## <a name="syntax"></a>Sintaxis

```cpp
template<class T, size_t Extent = dynamic_extent>
class span;
```

### <a name="template-parameters"></a>Parámetros de plantilla

|Parámetro|Descripción|
|-|-|
|`T`| Tipo de los elementos del intervalo. |
|`Extent`| Número de elementos del intervalo si se especifica en tiempo de compilación. De lo contrario, `std::dynamic_extent` si el número de elementos se especifica en tiempo de ejecución. |

[Guía de deducción](#deduction_guides)

## <a name="members"></a>Miembros

| **Definiciones de tipos** | **Descripción** |
|-|-|
| [const_pointer](#pointer) | El tipo de un puntero a un `const` elemento. |
| [const_reference](#reference) | Tipo de una referencia a un `const` elemento. |
| [difference_type](#difference_type) | El tipo de una distancia con signo entre dos elementos. |
| [element_type](#element_type) | El tipo de un elemento span. |
| [apunta](#iterator) | El tipo de un iterador para un intervalo. |
| [puntero](#pointer) | El tipo de un puntero a un elemento. |
| [reference](#reference) | El tipo de una referencia a un elemento. |
| [reverse_iterator](#reverse_iterator) | Tipo de un iterador inverso para un intervalo. |
| [size_type](#size_type) | Tipo del resultado de la distancia sin signo entre dos elementos del intervalo. |
| [value_type](#value_type) | El tipo de un elemento, sin `const` o `volatile` calificaciones. |
| **Constructores** | **Descripción** |
|[extienda](#span)| Construya un `span` .|
| **Compatibilidad con iteradores** | **Descripción** |
|[inicia](#begin) | Obtiene un iterador que apunta al primer elemento del intervalo.|
|[end](#end) | Obtiene un iterador que apunta al final del intervalo. |
|[rbegin](#rbegin) | Obtiene un iterador inverso que apunta al último elemento del intervalo; es decir, el principio del intervalo invertido.|
|[rend](#rend) | Obtiene un iterador inverso que apunta al principio del intervalo; es decir, el final del intervalo invertido.|
| **Elementos de acceso**| **Descripción** |
|[Atrás](#back) | Obtiene el último elemento del intervalo.|
|[datos](#data) | Obtiene la dirección del primer elemento del intervalo.|
|[end](#front) | Obtiene el primer elemento del intervalo.|
|[Operator\[\]](#op_at) | Obtener acceso a un elemento en una posición especificada.|
| **Observadores** | **Descripción** |
|[empty](#empty)| Comprueba si el intervalo está vacío.|
|[size](#size) | Obtiene el número de elementos del intervalo.|
|[size_bytes](#size_bytes) | Obtiene el tamaño del intervalo en bytes.|
| **Subvistas** | **Descripción**|
| [first](#first_view) | Obtiene un subintervalo desde el principio del intervalo.|
| [last](#last_view) | Obtiene un subintervalo desde la parte posterior del intervalo.|
| [subintervalo](#sub_view) | Obtiene un subintervalo desde cualquier parte del intervalo.|
| **Operadores** | **Descripción** |
|[span:: Operator =](#op_eq)| Reemplace el intervalo.|
|[span:: Operator\[\]](#op_at)| Obtiene el elemento en la posición especificada. |

## <a name="remarks"></a>Comentarios

Todas `span` las funciones miembro tienen una complejidad constante.

A diferencia de `array` o `vector` , un intervalo no "posee" los elementos que contiene. Un intervalo no libera ningún almacenamiento para los elementos que contiene porque no posee el almacenamiento de esos objetos.

## <a name="requirements"></a>Requisitos

**Encabezado:**\<span>

**Espacio de nombres:** std

**Opción del compilador:** /STD: c + + latest

## <a name="spanback"></a><a name="back"></a> `span::back`

Obtiene el último elemento del intervalo.

```cpp
constexpr reference back() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Referencia al último elemento del intervalo.

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    cout << mySpan.back();
}
```

```Output
2
```

## <a name="spanbegin"></a><a name="begin"></a> `span::begin`

Obtiene un iterador que apunta al primer elemento del intervalo.

```cpp
constexpr iterator begin() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Iterador que apunta al primer elemento del intervalo.

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto i = mySpan.begin();
    cout << *i;
}
```

```Output
0
```

## <a name="spandata"></a><a name="data"></a> `span::data`

Obtiene un puntero al principio de los datos de intervalo.

```cpp
constexpr pointer data() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Puntero al primer elemento almacenado en el intervalo.

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    auto i = mySpan.data();
    cout << *i;
}
```

```Output
0
```

## <a name="spandifference_type"></a><a name="difference_type"></a> `span::difference_type`

Número de elementos entre dos elementos de un intervalo.

```cpp
using difference_type = std::ptrdiff_t;
```

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::difference_type distance = mySpan.end() - mySpan.begin();
    cout << distance << std::endl;
}
```

```Output
3
```

## <a name="spanelement_type"></a><a name="element_type"></a> `span::element_type`

Tipo de los elementos del intervalo.

```cpp
using element_type = T;
```

### <a name="remarks"></a>Comentarios

El tipo se toma del parámetro de plantilla `T` cuando se crea un intervalo.

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::element_type et = mySpan[2];
    cout << et << endl;
}
```

```Output
2
```

## <a name="spanempty"></a><a name="empty"></a> `span::empty`

Si el intervalo contiene elementos.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Devuelve `true` si `this->size() == 0` . De lo contrario, es `false`.

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    bool isEmpty = mySpan.empty(); // isEmpty == false
}
```

## <a name="spanend"></a><a name="end"></a> `span::end`

Obtiene un iterador al final del intervalo.

```cpp
constexpr iterator end() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Iterador que apunta justo después del final del intervalo.

### <a name="remarks"></a>Comentarios

`end` se usa para probar si un iterador ha sobrepasado el final de su intervalo.

No desreferenciar el valor devuelto por este iterador. Úselo para identificar si el iterador se ha alcanzado más allá del último elemento del intervalo.

### <a name="example"></a>Ejemplo

```cpp
// Iteration
for (auto it = s1.begin(); it != s1.end(); ++it)
{
    cout << *it;
}
```

## <a name="spanfirst"></a><a name="first_view"></a> `span::first`

Obtiene un subintervalo, tomado de la parte delantera de este intervalo.

```cpp
constexpr auto first(size_type count) const noexcept;
template <size_t count> constexpr auto first() const noexcept;
```

### <a name="parameters"></a>Parámetros

*contabiliza*\
Número de elementos desde el principio de este intervalo que se van a colocar en el subintervalo.  
El número de elementos se especifica como un parámetro para la plantilla o para la función, como se muestra a continuación.

### <a name="return-value"></a>Valor devuelto

Intervalo que contiene `count` los elementos del principio de este intervalo.

### <a name="remarks"></a>Comentarios

Use la versión de plantilla de esta función cuando sea posible para validar `count` en tiempo de compilación y para conservar la información sobre el intervalo, ya que devuelve un intervalo de extensión fija.

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    
    auto first2 = mySpan.first(2);
    cout << "mySpan.first(2): ";
    for (auto& i : first2)
    {
        cout << i;
    }
    
    cout << "\nmySpan.first<2>: ";
    auto viewSpan = mySpan.first<2>();
    for (auto& i : viewSpan)
    {
        cout << i;
    }
}
```

```Output
mySpan.first(2): 01
mySpan.first<2>: 01
```

## <a name="spanfront"></a><a name="front"></a> `span::front`

Obtiene el primer elemento del intervalo.

```cpp
constexpr reference front() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Referencia al primer elemento del intervalo.

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto i = mySpan.front();
    cout << i;
}
```

```Output
0
```

## <a name="spaniterator"></a><a name="iterator"></a> `span::iterator`

El tipo de un iterador en elementos de intervalo.

```cpp
using iterator = implementation-defined-iterator-type;
```

### <a name="remarks"></a>Comentarios

Este tipo actúa como un iterador sobre los elementos de un intervalo.

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::iterator it = mySpan.begin();
    cout << *it++ << *it++ << *it;
}
```

```Output
012
```

## <a name="spanlast"></a><a name="last_view"></a> `span::last`

Obtiene un subintervalo, tomado del final de este intervalo.

```cpp
constexpr span<element_type, dynamic_extent> last(const size_type count) const noexcept;
template <size_t count> constexpr span<element_type, count> last() const noexcept;
```

### <a name="parameters"></a>Parámetros

*contabiliza*\
Número de elementos del final de este intervalo que se van a colocar en el subintervalo.
El número se puede especificar como un parámetro para la plantilla o para la función, como se muestra a continuación.

### <a name="return-value"></a>Valor devuelto

Intervalo que contiene los últimos `count` elementos de este intervalo.

### <a name="remarks"></a>Comentarios

Use la versión de plantilla de esta función cuando sea posible para validar `count` en tiempo de compilación y para conservar la información sobre el intervalo, ya que devuelve un intervalo de extensión fija.

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    
    auto first2 = mySpan.last(2);
    cout << "mySpan.last(2): ";
    for (auto& i : last2)
    {
        cout << i;
    }
    
    cout << "\nmySpan.last<2>: ";
    auto viewSpan = mySpan.last<2>();
    for (auto& i : viewSpan)
    {
        cout << i;
    }
}
```

```Output
mySpan.last(2): 12
mySpan.last<2>: 12
```

## <a name="spanoperator"></a><a name="op_at"></a> `span::operator[]`

Obtiene el elemento del intervalo en una posición especificada.

```cpp
constexpr reference operator[](size_type offset) const;
```

### <a name="parameters"></a>Parámetros

*posición*\
Elemento de base cero del intervalo al que se va a obtener acceso.

### <a name="return-value"></a>Valor devuelto

Referencia al elemento en el *desplazamiento*de la posición. Si la posición no es válida, el comportamiento es indefinido.

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan[1];
}
```

```Output
1
```

## <a name="spanoperator"></a><a name="op_eq"></a> `span::operator=`

Asigne otro intervalo a este.

```cpp
constexpr span& operator=(const span& other) noexcept = default;
```

### <a name="parameters"></a>Parámetros

*distinta*\
Intervalo que se va a asignar a este.

### <a name="return-value"></a>Valor devuelto

`*this`

### <a name="remarks"></a>Comentarios

La asignación realiza una copia superficial del puntero de datos y el tamaño. Una copia superficial es segura porque `span` no asigna memoria a los elementos que contiene.

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    span<int> mySpan2;
    mySpan2 = mySpan;
    for (auto &i : mySpan2)
    {
        cout << it;
    }
}
```

```Output
012
```

## <a name="spanpointer"></a><a name="pointer"></a> `span::pointer`

Los tipos de un puntero, y `const` puntero, a un elemento span.

```cpp
using pointer = T*;
using const_pointer = const T*;
```

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    // pointer
    span<int>::pointer ptr = &mySpan[2];
    *ptr = 9;
    cout << mySpan[2];
    
    // const pointer
    span<int>::const_pointer cPtr = &mySpan[0];
    // *cPtr = 9; error - const
    cout << *cPtr;
}
```

```Output
90
```

## <a name="spanrbegin"></a><a name="rbegin"></a> `span::rbegin`

Obtiene un iterador inverso que apunta al último elemento de este intervalo.

```cpp
constexpr reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Iterador que apunta al principio del intervalo invertido.

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    for (auto rIt = s1.rbegin(); rIt != s1.rend(); ++rIt)
    {
        cout << *rIt;
    }
}
```

```Output
210
```

## <a name="spanreference"></a><a name="reference"></a> `span::reference`

Los tipos de una referencia, y una `const` referencia, a un elemento span.

```cpp
using reference = T&;
using const_reference = const T&;
```

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    // reference
    span<int>::reference ref = mySpan[0];
    ref = 9;
    cout << mySpan[0];
    // const reference
    span<int>::const_reference cRef = mySpan[1];
    // cRef = 9; error because const
    cout << cRef;
}
```

```Output
91
```

## <a name="spanrend"></a><a name="rend"></a> `span::rend`

Obtiene un iterador de acceso aleatorio que apunta inmediatamente después del final del intervalo invertido.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Un iterador inverso al marcador de posición que sigue al último elemento del intervalo invertido; es decir, el marcador de posición delante del primer elemento del intervalo sin invertir.

### <a name="remarks"></a>Comentarios

`rend`se usa con un intervalo invertido igual que [span:: end](#end) se usa con un intervalo. Úselo para comprobar si un iterador inverso llegó al final de su intervalo.

El valor devuelto por no `rend` se debe desreferenciar.

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    for (auto rIt = s1.rbegin(); rIt != s1.rend(); ++rIt)
    {
        cout << *rIt;
    }
}
```

## <a name="spanreverse_iterator"></a><a name="reverse_iterator"></a> `span::reverse_iterator`

Tipo de un iterador inverso para un intervalo.

```cpp
using reverse_iterator = std::reverse_iterator<iterator>;
```

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::reverse_iterator rIt = mySpan.rbegin();
    cout << *rIt++ << *rIt++ << *rIt;
}
```

```Output
210
```

## <a name="spansize"></a><a name="size"></a> `span::size`

Obtiene el número de elementos del intervalo.

```cpp
constexpr size_t size() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos del intervalo.

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan.size();
}
```

```Output
3
```

## <a name="spansize_bytes"></a><a name="size_bytes"></a> `span::size_bytes`

Obtiene el tamaño de los elementos del intervalo en bytes.

```cpp
constexpr size_type size_bytes() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

El número de bytes que ocupan todos los elementos del intervalo; es decir, se `sizeof(element_type)` multiplica por el número de elementos del intervalo.

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan.size_bytes(); // 3 elements * 4 (size of an int)
}
```

```Output
12
```

## <a name="spansize_type"></a><a name="size_type"></a> `span::size_type`

Tipo sin signo, adecuado para almacenar el número de elementos de un intervalo.

```cpp
using size_type = size_t;
```

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::size_type szType = mySpan.size();
    cout << szType;
}
```

```Output
3
```

## <a name="spanspan"></a><a name="span"></a> `span::span`

`span`constructores.

```cpp
constexpr span() noexcept
requires (Extent == 0 || Extent == dynamic_extent) = default;

template <class It>
constexpr explicit(Extent != dynamic_extent)
span(It first, size_type count) noexcept

template <class It, class End>
constexpr explicit(Extent != dynamic_extent)
span(It first, End last) noexcept(noexcept(last - first))

template <class T, size_t N>
requires (Extent == dynamic_extent || Extent == N) && is_convertible_v<T (*)[], T (*)[]>
constexpr span(array<T, N>& arr) noexcept

template <class T, size_t N>
requires (Extent == dynamic_extent || Extent == N) && is_convertible_v<const T (*)[], T (*)[]>
constexpr span(const array<T, N>& arr) noexcept

template <size_t N>
requires (Extent == dynamic_extent || Extent == N)
constexpr span(type_identity_t<T> (&arr)[N]) noexcept

template <class R>
constexpr explicit(Extent != dynamic_extent)
span(R&& r)

// default copy ctor
constexpr span(const span& other) noexcept = default;

// converting  ctor
template <class T, size_t OtherExtent>
requires (Extent == dynamic_extent || OtherExtent == dynamic_extent ||
              Extent == OtherExtent) && is_convertible_v<T (*)[], T (*)[]>
constexpr explicit(Extent != dynamic_extent && OtherExtent == dynamic_extent)
span(const span<T, OtherExtent>& other) noexcept
```

### <a name="parameters"></a>Parámetros

*ARR*\
Construya un intervalo a partir de una matriz.

*contabiliza*\
Número de elementos que estarán en el intervalo.

*lugar*\
Iterador al primer elemento del intervalo.

*guardado*\
Iterador al final del último elemento del intervalo.

*N*\
Número de elementos que se incluirán en el intervalo.

*distinta*\
Realice una copia de este intervalo.

*c*\
Construya un intervalo a partir de este intervalo.

### <a name="remarks"></a>Comentarios

Un intervalo no libera almacenamiento para los elementos del intervalo porque no posee el almacenamiento de los objetos que contiene.

|Constructor  | Descripción  |
|---------|---------|
|`span()` | Construya un intervalo vacío. Solo se tiene en cuenta durante la resolución de sobrecarga cuando el parámetro de plantilla `Extent` es `0` o `dynamic_extent` .|
|`span(It first, size_type count)` | Construya un intervalo a partir de los primeros `count` elementos de iterator `first` .  Solo se tiene en cuenta durante la resolución de sobrecarga cuando el parámetro de plantilla `Extent` no es `dynamic_extent` . |
|`span(It first, End last)` | Construya un intervalo a partir de los elementos del iterador `first` hasta que `last` se alcance el final. Solo se tiene en cuenta durante la resolución de sobrecarga cuando el parámetro de plantilla `Extent` no es `dynamic_extent` . `It`debe ser un `contiguous_iterator` .  |
|`span(array<T, N>& arr) noexcept;`<br /><br />`span(const array<T, N>& arr) noexcept;`<br /><br />`span(type_identity_t<element_type> (&arr)[N]) noexcept;` |  Construir un intervalo a partir de `N` los elementos de la matriz especificada. Solo se tiene en cuenta durante la resolución de sobrecarga cuando el parámetro `Extent` de plantilla es `dynamic_extent` o es igual a `N` . |
|`span(R&& r)` |  Cree un intervalo a partir de un intervalo. Solo participa en la resolución de sobrecarga si el parámetro de plantilla `Extent` no es `dynamic_extent` .|
|`span(const span& other)` |  Constructor de copias generado por el compilador. Una copia superficial del puntero de datos es segura porque el intervalo no asigna la memoria que contiene los elementos. |
|`span(const span<OtherElementType, OtherExtent>& s) noexcept;` | Constructor de conversión: cree un intervalo desde otro intervalo. Solo participa en la resolución de sobrecarga si el parámetro `Extent` de plantilla es `dynamic_extent` , o `N` es `dynamic_extent` o es igual a `Extent` .|

### <a name="example"></a>Ejemplo

```cpp
#include <span>

using namespace std;

int main()
{
    const int MAX=10;
    
    int x[MAX];
    for (int i = 0; i < MAX; i++)
    {
        x[i] = i;
    }
    
    span<int, MAX> span1{ x }; // fixed-size span: compiler error if size of x doesn't match template argument MAX
    span<int> span2{ x }; // size is inferred from x
    span<const int> span3 = span2; // converting constructor
    span<int> span4( span2 ); // copy constructor
}
```

## <a name="spansubspan"></a><a name="sub_view"></a> `span::subspan`

Obtiene un subintervalo de este intervalo.

```cpp
constexpr auto subspan(size_type offset, size_type count = dynamic_extent) const noexcept;

template <size_t offset, size_t count = dynamic_extent>
constexpr auto subspan() const noexcept
```

### <a name="parameters"></a>Parámetros

*contabiliza*\
Número de elementos que se van a colocar en el subintervalo. Si `count` es `dynamic_extent` (el valor predeterminado), el subintervalo se toma de `offset` hasta el final de este intervalo.

*posición*\
Ubicación de este intervalo en la que se va a iniciar el subintervalo.

### <a name="return-value"></a>Valor devuelto

Intervalo que comienza en `offset` en este intervalo. Contiene `count` elementos.

### <a name="remarks"></a>Comentarios

Hay disponible una versión de plantilla de esta función que comprueba el número en tiempo de compilación, que conserva la información sobre el intervalo devolviendo un intervalo de extensión fija.

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    
    cout << "mySpan.subspan(1,2): ";
    for (auto& i : mySpan.subspan(1,2))
    {
        cout << i;
    }
    cout << "\nmySpan.subspan<1,2>: ";
    for (auto& i : mySpan.subspan<1,2>())
    {
        cout << i;
    }
    cout << "\nmySpan.subspan<1>: ";
    for (auto& i : mySpan.subspan<1>)
    {
        cout << i;
    }
}
```

```Output
mySpan.subspan(1,2): 12
mySpan.subspan<1,2>: 12
mySpan.subspan<1>: 12
```

## <a name="spanvalue_type"></a><a name="value_type"></a> `span::value_type`

El tipo del elemento en el intervalo, sin `const` o `volatile` calificaciones.

```cpp
using value_type = std::remove_cv_t<T>;
```

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::value_type vType = mySpan[2];
    cout << vType;
}
```

```Output
2
```

## <a name="deduction-guides"></a><a name="deduction_guides"></a>Guías de deducción

Se proporcionan las siguientes guías de deducción para span.

```cpp
// Allows the extent to be deduced from std::array and C++ built-in arrays

template <class T, size_t Extent>
span(T (&)[Extent]) -> span<T, Extent>;

template <class T, size_t Size>
span(array<T, Size>&) -> span<T, Size>;

template <class T, size_t Size>
span(const array<T, Size>&) -> span<const T, Size>;

// Allows the element type to be deduced from the iterator and the end of the span.
// The iterator must be contiguous

template <contiguous_iterator It, class End>
span(It, End) -> span<remove_reference_t<iter_reference_t<It>>>;

// Allows the element type to be deduced from a range.
// The range must be contiguous

template <ranges::contiguous_range Rng>
span(Rng &&) -> span<remove_reference_t<ranges::range_reference_t<Rng>>>;
```

## <a name="see-also"></a>Vea también

[\<span>](../standard-library/span.md)  
[Cómo usar la deducción de argumentos de plantilla de clase](https://devblogs.microsoft.com/cppblog/how-to-use-class-template-argument-deduction/)
