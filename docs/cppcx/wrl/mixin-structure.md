---
title: MixIn (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
ms.openlocfilehash: 16fd6b46d616df7163a304afa7f32ac3c095d398
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325363"
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

*Derivados*<br/>
Un tipo derivado de la [implementa](implements-structure.md) estructura.

*MixInType*<br/>
Tipo base.

*hasImplements*<br/>
**True** si *MixInType* es derivado de la implementación actual del tipo base; **false** en caso contrario.

## <a name="remarks"></a>Comentarios

Si una clase se deriva de Windows en tiempo de ejecución y las interfaces de clases COM, la lista de declaración de clase primero debe mostrar ninguna interfaz de Windows en tiempo de ejecución y, a continuación, las interfaces de cualquier COM clásico. **MixIn** garantiza que las interfaces se especifican en el orden correcto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`MixIn`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres**: Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)