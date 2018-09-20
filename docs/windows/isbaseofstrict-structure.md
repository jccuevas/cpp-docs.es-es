---
title: IsBaseOfStrict (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
dev_langs:
- C++
helpviewer_keywords:
- IsBaseOfStrict structure
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 52db5abd0487624f52f692e785007adaf9eac7ee
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428270"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <
   typename Base,
   typename Derived
>

struct IsBaseOfStrict;
template <
   typename Base
>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>Parámetros

*base*<br/>
El tipo base.

*Derivados*<br/>
El tipo derivado.

## <a name="remarks"></a>Comentarios

Comprueba si un tipo es la base de otro.

La primera plantilla comprueba si un tipo se deriva de un tipo base, que podría producir **true** o **false**. La segunda plantilla comprueba si un tipo se deriva de sí misma, que siempre produce **false**.

## <a name="members"></a>Miembros

### <a name="public-constants"></a>Constantes públicas

|nombre|Descripción|
|----------|-----------------|
|[IsBaseOfStrict::value (constante)](../windows/isbaseofstrict-value-constant.md)|Indica si un tipo es la base de otro.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IsBaseOfStrict`

## <a name="requirements"></a>Requisitos

**Encabezado:** internal.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)