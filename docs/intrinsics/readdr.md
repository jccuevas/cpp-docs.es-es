---
title: __readdr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readdr
dev_langs:
- C++
helpviewer_keywords:
- __readdr intrinsic
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dffb51782e87903feaeb733765fcf9f4763a64f6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385149"
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