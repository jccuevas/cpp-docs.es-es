---
title: unchecked_array_iterator (Clase)
ms.date: 11/04/2016
f1_keywords:
- stdext::unchecked_array_iterator
ms.assetid: 693b3b30-4e3a-465b-be06-409700bc50b1
ms.openlocfilehash: 9b3db474bedca50922334bd4dbd09c71d4e6e987
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626205"
---
# <a name="uncheckedarrayiterator-class"></a>unchecked_array_iterator (Clase)

La clase `unchecked_array_iterator` permite ajustar una matriz o un puntero en un iterador no comprobado. Use esta clase como contenedor (mediante la función [make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator)) para punteros o matrices sin formato como una manera dirigida de administrar advertencias de puntero no comprobadas en lugar de silenciar de manera global estas advertencias. Si es posible, use la versión comprobada de esta clase, [checked_array_iterator](../standard-library/checked-array-iterator-class.md).

> [!NOTE]
> Esta clase es una extensión de Microsoft de la Biblioteca estándar de C++. El código implementado mediante esta función no es portable a los entornos de compilación estándar de C++ que no admiten esta extensión de Microsoft.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Iterator>
class unchecked_array_iterator;
```

## <a name="remarks"></a>Comentarios

Esta clase se define en el espacio de nombres [stdext](../standard-library/stdext-namespace.md).

Esta es la versión no comprobada de la [clase checked_array_iterator](../standard-library/checked-array-iterator-class.md) y admite las mismas sobrecargas y los mismos miembros. Para más información sobre la característica de iterador activado con ejemplos de código, vea [Iteradores activados](../standard-library/checked-iterators.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<iterator>

**Espacio de nombres:** stdext

## <a name="see-also"></a>Vea también

[\<iterator>](../standard-library/iterator.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
