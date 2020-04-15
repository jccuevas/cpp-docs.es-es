---
title: VerifyInheritanceHelper (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInheritanceHelper structure
- Microsoft::WRL::Details::VerifyInheritanceHelper::Verify method
ms.assetid: 8a48a702-0f71-4807-935b-8311f0a7a8b6
ms.openlocfilehash: 3650cfb70ffc12572b3965534eff4e1f2ecb2cf5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374225"
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper (estructura)

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename I, typename Base>
struct VerifyInheritanceHelper;

template <typename I>
struct VerifyInheritanceHelper<I, Nil>;
```

### <a name="parameters"></a>Parámetros

*Ⅰ*<br/>
Un tipo.

*Base*<br/>
Otro tipo.

## <a name="remarks"></a>Observaciones

Comprueba si una interfaz se deriva de otra interfaz.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

Nombre                                       | Descripción
------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------
[VerifyInheritanceHelper::Verify](#verify) | Prueba las dos interfaces especificadas por los parámetros de plantilla actuales y determina si una interfaz se deriva de la otra.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`VerifyInheritanceHelper`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL::Details

## <a name="verifyinheritancehelperverify"></a><a name="verify"></a>VerifyInheritanceHelper::Verify

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
static void Verify();
```

### <a name="remarks"></a>Observaciones

Prueba las dos interfaces especificadas por los parámetros de plantilla actuales y determina si una interfaz se deriva de la otra.

Se emite un error si una interfaz no se deriva de la otra.
