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
ms.openlocfilehash: 09c2cc7e08e2dc0e8df42c64d285c37627c5925a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374248"
---
# <a name="verifyinterfacehelper-structure"></a>VerifyInterfaceHelper (estructura)

Admite la infraestructura de la biblioteca de plantillas C++ de Windows runtime y no está diseñada para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <bool isWinRTInterface, typename I>
struct VerifyInterfaceHelper;

template <typename I>
struct VerifyInterfaceHelper<false, I>;
```

### <a name="parameters"></a>Parámetros

*Ⅰ*<br/>
Una interfaz para verificar.

*isWinRTInterface*

## <a name="remarks"></a>Observaciones

Comprueba que la interfaz especificada por el parámetro template cumple ciertos requisitos.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

Nombre                                            | Descripción
----------------------------------------------- | ---------------------------------------------------------------------------------------------------
[VerifyInterfaceHelper::Verify (Método)](#verify) | Comprueba que la interfaz especificada por el parámetro de plantilla actual cumple ciertos requisitos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`VerifyInterfaceHelper`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL::Details

## <a name="verifyinterfacehelperverify"></a><a name="verify"></a>VerifyInterfaceHelper::Verify

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
static void Verify();
```

### <a name="remarks"></a>Observaciones

Comprueba que la interfaz especificada por el parámetro de plantilla actual cumple ciertos requisitos.
