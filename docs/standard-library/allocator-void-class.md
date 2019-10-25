---
title: allocator&lt;void&gt; (Clase)
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
ms.openlocfilehash: c8d787fe03dfe6f67fb8e228308ec74b6e7f620a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688526"
---
# <a name="allocatorltvoidgt-class"></a>allocator&lt;void&gt; (Clase)

Una especialización del asignador de plantilla de clase para el tipo **void**, que define los tipos que tienen sentido en este contexto.

## <a name="syntax"></a>Sintaxis

```cpp
template <>
class allocator<void> {
    typedef void *pointer;
    typedef const void *const_pointer;
    typedef void value_type;
    template <class Other>
    struct rebind;
    allocator();
    allocator(const allocator<void>&);

    template <class Other>
    allocator(const allocator<Other>&);

    template <class Other>
    allocator<void>& operator=(const allocator<Other>&);
};
```

## <a name="remarks"></a>Comentarios

La clase especializa explícitamente el [asignador](../standard-library/allocator-class.md) de plantillas de clase para el tipo **void**. Sus constructores y el operador de asignación se comportan igual que para la plantilla de clase, pero solo define los siguientes tipos:

- [const_pointer](../standard-library/allocator-class.md#const_pointer).

- [pointer](../standard-library/allocator-class.md#pointer).

- [value_type](../standard-library/allocator-class.md#value_type).

- volver a [enlazar](../standard-library/allocator-class.md#rebind), una plantilla de clase anidada.
