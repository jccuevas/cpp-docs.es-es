---
title: VerifyInheritanceHelper (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
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
ms.openlocfilehash: 2a011b0583d8221ec49d16236add978ac647acc3
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788934"
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename I, typename Base>
struct VerifyInheritanceHelper;

template <typename I>
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
