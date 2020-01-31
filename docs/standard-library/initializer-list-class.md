---
title: initializer_list (Clase)
description: Una referencia para la clase initializer_list en la C++ biblioteca estándar, tal y como la implementa Microsoft en Visual Studio.
ms.date: 01/28/2020
f1_keywords:
- initializer_list/std::initializer_list::initializer_list
- initializer_list/std::initializer_list::begin
- initializer_list/std::initializer_list::end
- initializer_list/std::initializer_list::size
ms.assetid: 1f2c0ff4-5636-4f79-b008-e75426e3d2ab
helpviewer_keywords:
- std::initializer_list::initializer_list
- std::initializer_list::begin
- std::initializer_list::end
- std::initializer_list::size
ms.openlocfilehash: 6be51835958a07162ce22ff9d619fb793102669f
ms.sourcegitcommit: 684181561490e0d1955cf601d222f67f09af6d00
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2020
ms.locfileid: "76894338"
---
# <a name="initializer_list-class"></a>initializer_list (Clase)

Proporciona acceso a una matriz de elementos en la que cada miembro es del tipo especificado.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type>
class initializer_list
```

### <a name="parameters"></a>Parameters

*Escribir*\
Tipo de datos de elementos que se va a almacenar en la `initializer_list`.

## <a name="remarks"></a>Notas

Se puede construir `initializer_list` con una lista de inicializadores entre llaves:

```cpp
initializer_list<int> i1{ 1, 2, 3, 4 };
```

El compilador transforma las listas de inicializadores entre llaves con elementos homogéneos en una `initializer_list` siempre y cuando la signatura de la función requiera una `initializer_list`. Para obtener más información sobre el uso de `initializer_list`, vea [inicialización uniforme y constructores de delegación](../cpp/uniform-initialization-and-delegating-constructors.md) .

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[initializer_list](#initializer_list)|Construye un objeto de tipo `initializer_list`.|

### <a name="typedefs"></a>Definiciones de tipo

|Nombre de tipo|Descripción|
|-|-|
|`value_type`|Tipo de los elementos de `initializer_list`.|
|`reference`|Tipo que proporciona una referencia a un elemento de `initializer_list`.|
|`const_reference`|Tipo que proporciona una referencia constante a un elemento de `initializer_list`.|
|`size_type`|Tipo que representa el número de elementos de `initializer_list`.|
|`iterator`|Tipo que proporciona un iterador para `initializer_list`.|
|`const_iterator`|Tipo que proporciona un iterador constante para `initializer_list`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[begin](#begin)|Devuelve un puntero al primer elemento de `initializer_list`.|
|[end](#end)|Devuelve un puntero a un elemento más allá del último elemento de `initializer_list`.|
|[size](#size)|Devuelve el número de elementos de `initializer_list`.|

## <a name="requirements"></a>Requisitos de

**Encabezado:** \<initializer_list >

**Espacio de nombres:** std

## <a name="begin"></a>  initializer_list::begin

Devuelve un puntero al primer elemento de `initializer_list`.

```cpp
constexpr const InputIterator* begin() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Puntero al primer elemento de `initializer_list`. Si la lista está vacía, el puntero es el mismo para el principio y el final de la lista.

## <a name="end"></a>  initializer_list::end

Devuelve un puntero a un elemento más allá del último elemento de `initializer list`.

```cpp
constexpr const InputIterator* end() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Puntero a un elemento más allá del último elemento de la lista. Si la lista está vacía, es igual que el puntero al primer elemento de la lista.

## <a name="initializer_list"></a>  initializer_list::initializer_list

Construye un objeto de tipo `initializer_list`.

```cpp
constexpr initializer_list() noexcept;
initializer_list(const InputIterator First, const InputIterator Last);
```

### <a name="parameters"></a>Parameters

*Primer*\
Posición del primer elemento en el intervalo de elementos que se va a copiar.

*Última*\
Posición del primer elemento más allá del intervalo de elementos que se va a copiar.

### <a name="remarks"></a>Notas

Una `initializer_list` se basa en una matriz de objetos del tipo especificado. Al copiar un `initializer_list` se crea una segunda instancia de una lista que apunta a los mismos objetos; los objetos subyacentes no se copian.

### <a name="example"></a>Ejemplo

```cpp
// initializer_list_class.cpp
// compile with: /EHsc
#include <initializer_list>
#include <iostream>

int main()
{
    using namespace std;
    // Create an empty initializer_list c0
    initializer_list <int> c0;

    // Create an initializer_list c1 with 1 element
    initializer_list <int> c1{ 3 };

    // Create an initializer_list c2 with 5 elements
    initializer_list <int> c2{ 5, 4, 3, 2, 1 };

    // Create a copy, initializer_list c3, of initializer_list c2
    initializer_list <int> c3(c2);

    // Create a initializer_list c4 by copying the range c3[ first,  last)
    const int* c3_ptr = c3.begin();
    c3_ptr++;
    c3_ptr++;
    initializer_list <int> c4(c3.begin(), c3_ptr);

    // Move initializer_list c4 to initializer_list c5
    initializer_list <int> c5(move(c4));

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

    cout << "c5 =";
    for (auto c : c5)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 3
c2 = 5 4 3 2 1
c3 = 5 4 3 2 1
c5 = 5 4
```

## <a name="size"></a>  initializer_list::size

Devuelve el número de elementos de la lista.

```cpp
constexpr size_t size() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos de la lista.

## <a name="see-also"></a>Vea también

[<forward_list>](../standard-library/forward-list.md)
