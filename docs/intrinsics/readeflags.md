---
title: __readeflags
ms.date: 09/02/2019
f1_keywords:
- __readeflags
helpviewer_keywords:
- __readeflags intrinsic
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
ms.openlocfilehash: fe2365c2837b6c583810bb9fc908fe98486a2d38
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221225"
---
# <a name="__readeflags"></a>__readeflags

Lee el registro de estado y control (EFLAGS) del programa.

## <a name="syntax"></a>Sintaxis

```C
unsigned     int __readeflags(void); /* x86 */
unsigned __int64 __readeflags(void); /* x64 */
```

## <a name="return-value"></a>Valor devuelto

El valor del registro EFLAGS. El valor devuelto es de 32 bits de longitud en una plataforma de 32 bits y de 64 bits en una plataforma de 64 bits.

## <a name="remarks"></a>Comentarios

Estas rutinas solo están disponibles como intrínsecos.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__readeflags`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[__writeeflags](../intrinsics/writeeflags.md)
