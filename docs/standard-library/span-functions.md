---
title: '&lt;&gt;funciones span'
ms.date: 05/28/2020
f1_keywords:
- span/std::span::as_bytes
- span/std::as_writable_bytes
helpviewer_keywords:
- std::span [C++], as_writable_bytes
- std::as_bytes [C++]
ms.openlocfilehash: 6573ea061673091113244ada0ab0cd84bdd7db75
ms.sourcegitcommit: 1a8fac06478da8bee1f6d70e25afbad94144af1a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/30/2020
ms.locfileid: "84226329"
---
# <a name="ltspangt-functions"></a>&lt;&gt;funciones span

El \<span> encabezado incluye las siguientes funciones no miembro que operan en objetos de **intervalo** .

| **Funciones no miembro** | **Descripción** |
|-|-|
|[as_bytes](#as_bytes) | Obtiene una vista de solo lectura de la representación de objeto de los elementos del intervalo. |
|[as_writable_bytes](#as_writable_bytes) | Obtiene una vista de lectura/escritura de la representación de objeto de los elementos del intervalo. |

## <a name="as_bytes"></a>`as_bytes`

Obtiene una vista de solo lectura de la representación de objeto de los elementos del intervalo.

```cpp
template <class T, size_t Extent>
auto as_bytes(span<T, Extent> s) noexcept;
```

### <a name="parameters"></a>Parámetros

*H*\
Tipo de los elementos del intervalo.

*Expresa*\
Número de elementos del intervalo (si se conoce en tiempo de compilación), de lo contrario, `dynamic_extent` indica que el número de elementos no es conocido hasta el tiempo de ejecución.

*seg*\
Intervalo del que se va a obtener la representación sin formato.

### <a name="return-value"></a>Valor devuelto

`span<const byte, S>`Al primer elemento almacenado en el intervalo donde `S` es`{reinterpret_cast<const std::byte*>(s.data()), s.size_bytes()}`

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

void main()
{
    int a[] = { 0,1,2 };
    span <int> mySpan(a);
    auto bytes = std::as_bytes(mySpan);
}
```

## <a name="as_writable_bytes"></a>`as_writable_bytes`

Si `T` no es `const` , obtiene una vista de lectura/escritura de la representación de bytes sin formato de los elementos del intervalo.

```cpp
template <class T, size_t Extent>
auto as_writable_bytes(span<T, Extent> s) noexcept;
```

### <a name="parameters"></a>Parámetros

*H*\
Tipo de los elementos del intervalo.

*Expresa*\
Número de elementos del intervalo (si se conoce en tiempo de compilación), de lo contrario, `dynamic_extent` indica que el número de elementos no es conocido hasta el tiempo de ejecución.

*seg*\
Intervalo del que se va a obtener la representación sin formato.

### <a name="return-value"></a>Valor devuelto

`span<byte, S>`Al primer elemento almacenado en el intervalo donde `S` es`{reinterpret_cast<std::byte*>(s.data()), s.size_bytes()}`

### <a name="example"></a>Ejemplo

```cpp
#include <span>
#include <iostream>

using namespace std;

void main()
{
    int a[] = { 0,1,2 };
    span <int> mySpan(a);
    auto bytes = as_writable_bytes(mySpan);
}
```

## <a name="see-also"></a>Vea también

[\<span>](span.md)
