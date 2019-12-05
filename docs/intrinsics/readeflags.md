---
title: __readeflags
ms.date: 09/02/2019
f1_keywords:
- __readeflags
helpviewer_keywords:
- __readeflags intrinsic
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
ms.openlocfilehash: 6afdc0f20a3ae72865a80ba2eb7f896f79f63171
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857910"
---
# <a name="__readeflags"></a>__readeflags

**Específicos de Microsoft**

Lee el registro de estado y control (EFLAGS) del programa.

## <a name="syntax"></a>Sintaxis

```C
unsigned     int __readeflags(void); /* x86 */
unsigned __int64 __readeflags(void); /* x64 */
```

## <a name="return-value"></a>Valor devuelto

El valor del registro EFLAGS. El valor devuelto es de 32 bits de longitud en una plataforma de 32 bits y de 64 bits en una plataforma de 64 bits.

## <a name="remarks"></a>Notas

Estas rutinas solo están disponibles como intrínsecos.

## <a name="requirements"></a>Requisitos de

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__readeflags`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del Compilador](../intrinsics/compiler-intrinsics.md)\
[__writeeflags](../intrinsics/writeeflags.md)
