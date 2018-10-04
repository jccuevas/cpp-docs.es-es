---
title: VerifyInterfaceHelper (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper::Verify
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInterfaceHelper structure
- Microsoft::WRL::Details::VerifyInterfaceHelper::Verify method
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b70155566695ade6b6778ade3b4758faebb3ea67
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788870"
---
# <a name="verifyinterfacehelper-structure"></a>VerifyInterfaceHelper (estructura)

Admite la infraestructura de la biblioteca de plantillas C++ de Windows en tiempo de ejecución y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <bool isWinRTInterface, typename I>
struct VerifyInterfaceHelper;

template <typename I>
struct VerifyInterfaceHelper<false, I>;
```

### <a name="parameters"></a>Parámetros

*I*<br/>
Para comprobar una interfaz.

*isWinRTInterface*

## <a name="remarks"></a>Comentarios

Comprueba que la interfaz especificada por el parámetro de plantilla cumple determinados requisitos.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

Name                                            | Descripción
----------------------------------------------- | ---------------------------------------------------------------------------------------------------
[VerifyInterfaceHelper::Verify (método)](#verify) | Comprueba que la interfaz especificada por el parámetro de plantilla actual cumple determinados requisitos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`VerifyInterfaceHelper`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="verify"></a>Verifyinterfacehelper

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
static void Verify();
```

### <a name="remarks"></a>Comentarios

Comprueba que la interfaz especificada por el parámetro de plantilla actual cumple determinados requisitos.
