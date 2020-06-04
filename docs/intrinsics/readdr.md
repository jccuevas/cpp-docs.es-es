---
title: __readdr
ms.date: 09/02/2019
f1_keywords:
- __readdr
helpviewer_keywords:
- __readdr intrinsic
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
ms.openlocfilehash: fbaf9e761f9f1450ccd12dc378ab6e498aa0df08
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857884"
---
# <a name="__readdr"></a>__readdr

**Específicos de Microsoft**

Lee el valor del registro de depuración especificado.

## <a name="syntax"></a>Sintaxis

```C
unsigned         __readdr(unsigned int DebugRegister); /* x86 */
unsigned __int64 __readdr(unsigned int DebugRegister); /* x64 */
```

### <a name="parameters"></a>Parameters

\ *DebugRegister*
de Constante de 0 a 7 que identifica el registro de depuración.

## <a name="return-value"></a>Valor devuelto

Valor del registro de depuración especificado.

## <a name="remarks"></a>Notas

Estos intrínsecos solo están disponibles en modo kernel y las rutinas solo están disponibles como intrínsecos.

## <a name="requirements"></a>Requisitos de

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__readdr`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del Compilador](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
