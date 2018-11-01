---
title: __readeflags
ms.date: 11/04/2016
f1_keywords:
- __readeflags
helpviewer_keywords:
- __readeflags intrinsic
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
ms.openlocfilehash: e5294180904d0d7ca3bbd1de75e45e058a33c88f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594277"
---
# <a name="readeflags"></a>__readeflags

Lee que el estado del programa y control (EFLAGS) se registran.

## <a name="syntax"></a>Sintaxis

```
unsigned     int __readeflags(void);
unsigned __int64 __readeflags(void);
```

## <a name="return-value"></a>Valor devuelto

El valor del registro EFLAGS. El valor devuelto es de 32 bits largo en una plataforma de 32 bits y 64 bits largo en una plataforma de 64 bits.

## <a name="remarks"></a>Comentarios

Estas rutinas sólo están disponibles como intrínsecos.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__readeflags`|x86, x64|

**Archivo de encabezado** \<intrin.h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[__writeeflags](../intrinsics/writeeflags.md)