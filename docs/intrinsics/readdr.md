---
title: __readdr
ms.date: 11/04/2016
f1_keywords:
- __readdr
helpviewer_keywords:
- __readdr intrinsic
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
ms.openlocfilehash: 9d265fe75abaa7ad3cfd508613766cc3b600ee14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62263288"
---
# <a name="readdr"></a>__readdr

Lee el valor del registro de depuración especificado.

## <a name="syntax"></a>Sintaxis

```
unsigned         __readdr(unsigned int DebugRegister);
unsigned __int64 __readdr(unsigned int DebugRegister);
```

#### <a name="parameters"></a>Parámetros

*DebugRegister*<br/>
[in] Registrar una constante de 0 a 7 que identifica la depuración.

## <a name="return-value"></a>Valor devuelto

El valor del registro de depuración especificado.

## <a name="remarks"></a>Comentarios

Estas funciones intrínsecas están disponibles solo en modo kernel, y las rutinas sólo están disponibles como intrínsecos.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__readdr`|x86, x64|

**Archivo de encabezado** \<intrin.h >

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[__readeflags](../intrinsics/readeflags.md)