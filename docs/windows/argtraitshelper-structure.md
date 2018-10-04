---
title: ArgTraitsHelper (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
- event/Microsoft::WRL::Details::ArgTraitsHelper::args
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraitsHelper structure
- Microsoft::WRL::Details::ArgTraitsHelper::args constant
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b608f5da893019d7700891968dcdc06489c563ea
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234234"
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

Name         | Descripción
------------ | ------------------------------------------------------
`methodType` | Sinónimo de `decltype(&TDelegateInterface::Invoke)`.
`Traits`     | Sinónimo de `ArgTraits<methodType>`.

### <a name="public-constants"></a>Constantes públicas

nombre                           | Descripción
------------------------------ | ---------------------------------------------------------------------------------------------------------------------
[Argtraitshelper](#args) | Ayuda a [Argtraits](#args) mantener el recuento del número de parámetros en el `Invoke` al método de interfaz de un delegado.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ArgTraitsHelper`

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Namespace:** wrl

## <a name="args"></a>Argtraitshelper

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
static const int args = Traits::args;
```

### <a name="remarks"></a>Comentarios

Ayuda a `ArgTraitsHelper::args` mantener el recuento del número de parámetros en el `Invoke` al método de interfaz de un delegado.
