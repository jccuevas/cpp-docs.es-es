---
title: VerifyInheritanceHelper (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInheritanceHelper structure
- Microsoft::WRL::Details::VerifyInheritanceHelper::Verify method
ms.assetid: 8a48a702-0f71-4807-935b-8311f0a7a8b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6231345b837cae8f36e8441173300d804c0ea167
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169638"
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <
   typename I,
   typename Base
>
struct VerifyInheritanceHelper;
template <
   typename I
>
struct VerifyInheritanceHelper<I, Nil>;
```

### <a name="parameters"></a>Parámetros

*I*<br/>
Un tipo.

*base*<br/>
Otro tipo.

## <a name="remarks"></a>Comentarios

Comprueba si una interfaz se deriva de otra interfaz.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

Name                                       | Descripción
------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------
[Verifyinheritancehelper](#verify) | Prueba de las dos interfaces especificadas por los parámetros de plantilla actual y determina si una interfaz se deriva de la otra.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`VerifyInheritanceHelper`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="verify"></a>Verifyinheritancehelper

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
static void Verify();
```

### <a name="remarks"></a>Comentarios

Prueba de las dos interfaces especificadas por los parámetros de plantilla actual y determina si una interfaz se deriva de la otra.

Se genera un error si una interfaz no se derive de la otra.
