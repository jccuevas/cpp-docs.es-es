---
title: Clase initializer_list | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- initializer_list/std::initializer_list::initializer_list
- initializer_list/std::initializer_list::begin
- initializer_list/std::initializer_list::end
- initializer_list/std::initializer_list::size
dev_langs:
- C++
ms.assetid: 1f2c0ff4-5636-4f79-b008-e75426e3d2ab
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::initializer_list::initializer_list
- std::initializer_list::begin
- std::initializer_list::end
- std::initializer_list::size
ms.workload:
- cplusplus
ms.openlocfilehash: b84ed250bcacc07b421318429458c889546e9e6a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060655"
---
# <a name="initializerlist-class"></a>initializer_list (Clase)

Proporciona acceso a una matriz de elementos en la que cada miembro es del tipo especificado.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type>
class initializer_list
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Type*|Tipo de datos de elementos que se va a almacenar en la `initializer_list`.|

## <a name="remarks"></a>Comentarios

Se puede construir `initializer_list` con una lista de inicializadores entre llaves:

```cpp
initializer_list<int> i1{ 1, 2, 3, 4 };
```

El compilador transforma las listas de inicializadores entre llaves con elementos homogéneos en una `initializer_list` siempre y cuando la signatura de la función requiera una `initializer_list`. Para obtener información detallada sobre el uso de `initializer_list`, vea [Inicialización uniforme y constructores de delegación](../cpp/uniform-initialization-and-delegating-constructors.md).

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[initializer_list](../standard-library/forward-list-class.md#forward_list)|Construye un objeto de tipo `initializer_list`.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|value_type|Tipo de los elementos de `initializer_list`.|
|referencia|Tipo que proporciona una referencia a un elemento de `initializer_list`.|
|const_reference|Tipo que proporciona una referencia constante a un elemento de `initializer_list`.|
|size_type|Tipo que representa el número de elementos de `initializer_list`.|
|iterator|Tipo que proporciona un iterador para `initializer_list`.|
|const_iterator|Tipo que proporciona un iterador constante para `initializer_list`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[begin](#begin)|Devuelve un puntero al primer elemento de `initializer_list`.|
|[end](#end)|Devuelve un puntero a un elemento más allá del último elemento de `initializer_list`.|
|[size](#size)|Devuelve el número de elementos de `initializer_list`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<initializer_list>

**Espacio de nombres:** std

## <a name="begin"></a>  initializer_list::begin

Devuelve un puntero al primer elemento de `initializer_list`.

```cpp
constexpr const InputIterator* begin() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Puntero al primer elemento de `initializer_list`. Si la lista está vacía, el puntero es el mismo para el principio y el final de la lista.

### <a name="remarks"></a>Comentarios

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

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Primero*|Posición del primer elemento en el intervalo de elementos que se va a copiar.|
|*Último*|Posición del primer elemento más allá del intervalo de elementos que se va a copiar.|

### <a name="remarks"></a>Comentarios

Una `initializer_list` se basa en una matriz de objetos del tipo especificado. Al copiar una `initializer_list` se crea una segunda instancia de una lista que apunta a los mismos objetos; los objetos subyacentes no se copian.

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

    cout << "c4 =";
    for (auto c : c4)
        cout << " " << c;
    cout << endl;

    cout << "c5 =";
    for (auto c : c5)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 3c2 = 5 4 3 2 1c3 = 5 4 3 2 1c4 = 5 4c5 = 5 4
```

## <a name="size"></a>  initializer_list::size

Devuelve el número de elementos de la lista.

```cpp
constexpr size_t size() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos de la lista.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[<forward_list>](../standard-library/forward-list.md)<br/>
