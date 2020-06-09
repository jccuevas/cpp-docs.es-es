---
title: allocator&lt;void&gt; (Clase)
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
ms.openlocfilehash: af29c70dca56b1e68eef3614357269c587a77ec9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623679"
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

## <a name="remarks"></a>Observaciones

La clase especializa explícitamente el [asignador](allocator-class.md) de plantillas de clase para el tipo **void**. Sus constructores y el operador de asignación se comportan igual que para la plantilla de clase, pero solo define los siguientes tipos:

- [const_pointer](allocator-class.md#const_pointer).

- [puntero](allocator-class.md#pointer).

- [value_type](allocator-class.md#value_type).

- volver a [enlazar](allocator-class.md#rebind), una plantilla de clase anidada.
