---
title: IsSame (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame
dev_langs:
- C++
helpviewer_keywords:
- IsSame structure
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e9e45f64d8eda3e24fb7c85120f14e981963f7f1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595790"
---
# <a name="issame-structure"></a>IsSame (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <
   typename T1,
   typename T2
>
struct IsSame;
template <
   typename T1
>
struct IsSame<T1, T1>;
```

### <a name="parameters"></a>Parámetros

*T1*  
Un tipo.

*T2*  
Otro tipo.

## <a name="remarks"></a>Comentarios

Las pruebas si un tipo especificado es igual que otro tipo especificado.

## <a name="members"></a>Miembros

### <a name="public-constants"></a>Constantes públicas

|nombre|Descripción|
|----------|-----------------|
|[IsSame::value (constante)](../windows/issame-value-constant.md)|Indica si un tipo es igual a otro.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IsSame`

## <a name="requirements"></a>Requisitos

**Encabezado:** internal.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)