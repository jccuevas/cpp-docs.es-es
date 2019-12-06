---
title: __writedr
ms.date: 09/02/2019
f1_keywords:
- __writedr
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
ms.openlocfilehash: 473e7223e9974d0125e772c152ea85ae90b97342
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858066"
---
# <a name="__writedr"></a>__writedr

**Específicos de Microsoft**

Escribe el valor especificado en el registro de depuración especificado.

## <a name="syntax"></a>Sintaxis

```C
void __writedr(unsigned DebugRegister, unsigned DebugValue); /* x86 */
void __writedr(unsigned DebugRegister, unsigned __int64 DebugValue); /* x64 */
```

### <a name="parameters"></a>Parameters

\ *DebugRegister*
de Número del 0 al 7 que identifica el registro de depuración.

\ *DebugValue*
de Valor que se va a escribir en el registro de depuración.

## <a name="remarks"></a>Notas

Estos intrínsecos solo están disponibles en modo kernel y las rutinas solo están disponibles como intrínsecos.

## <a name="requirements"></a>Requisitos de

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__writedr`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del Compilador](../intrinsics/compiler-intrinsics.md)\
[__readdr](../intrinsics/readdr.md)
