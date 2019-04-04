---
title: VerifyInterfaceHelper (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInterfaceHelper structure
- Microsoft::WRL::Details::VerifyInterfaceHelper::Verify method
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
ms.openlocfilehash: cdd0272953b2399cd71efe207eb1c56e5de154e6
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785830"
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

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="verify"></a>VerifyInterfaceHelper::Verify

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
static void Verify();
```

### <a name="remarks"></a>Comentarios

Comprueba que la interfaz especificada por el parámetro de plantilla actual cumple determinados requisitos.
