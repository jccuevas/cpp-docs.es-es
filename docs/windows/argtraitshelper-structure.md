---
title: ArgTraitsHelper (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
dev_langs:
- C++
helpviewer_keywords:
- ArgTraitsHelper structure
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bb0377de88ef5e782e0e11bc563409b7094eecf5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598689"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>Parámetros

*TDelegateInterface*  
Una interfaz de delegado.

## <a name="remarks"></a>Comentarios

Ayuda a define las características comunes de los argumentos de delegado.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`methodType`|Sinónimo de `decltype(&TDelegateInterface::Invoke)`.|
|`Traits`|Sinónimo de `ArgTraits<methodType>`.|

### <a name="public-constants"></a>Constantes públicas

|nombre|Descripción|
|----------|-----------------|
|[ArgTraitsHelper::args (constante)](../windows/argtraitshelper-args-constant.md)|Ayuda a [Argtraits](../windows/argtraits-args-constant.md) mantener el recuento del número de parámetros en el `Invoke` al método de interfaz de un delegado.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ArgTraitsHelper`

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)