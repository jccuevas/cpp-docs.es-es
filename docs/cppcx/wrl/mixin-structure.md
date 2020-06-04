---
title: MixIn (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
ms.openlocfilehash: b302d6e08e401a24b465508d5ddabcae8b16bd8f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213700"
---
# <a name="mixin-structure"></a>MixIn (estructura)

Garantiza que una clase en tiempo de ejecución deriva de interfaces de Windows en tiempo de ejecución, si las hubiera, y luego de interfaces de COM clásico.

## <a name="syntax"></a>Sintaxis

```cpp
template<
    typename Derived,
    typename MixInType,
    bool hasImplements = __is_base_of(Details::ImplementsBase, MixInType)
>
struct MixIn;
```

### <a name="parameters"></a>Parámetros

*Obtienen*<br/>
Tipo derivado de la estructura [Implements](implements-structure.md) .

*MixInType*<br/>
Tipo base.

*hasImplements*<br/>
**true** si *MixInType* se deriva de la implementación actual del tipo base; de lo contrario, **false** .

## <a name="remarks"></a>Observaciones

Si una clase se deriva de interfaces COM de Windows Runtime y de clase, la lista de declaraciones de clase debe enumerar primero cualquier interfaz Windows Runtime y, a continuación, cualquier interfaz COM clásica. **Mixin (** garantiza que las interfaces se especifican en el orden correcto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`MixIn`

## <a name="requirements"></a>Requisitos

**Encabezado:** implementa. h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Consulte también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)
