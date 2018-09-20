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
ms.openlocfilehash: 314853b103d74bd7907fb665b806f386ed7bd44e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397475"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>Parámetros

*TDelegateInterface*<br/>
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