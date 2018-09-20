---
title: __readpmc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readpmc
dev_langs:
- C++
helpviewer_keywords:
- Read Performance Monitoring Counters instruction
- __readpmc intrinsic
- rdpmc instruction
ms.assetid: 14ed45a6-28b6-4635-8437-a597c04b43d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4574ac1c5ff1ab45dfdf935e5eba3a14a76b948a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419858"
---
# <a name="readpmc"></a>__readpmc

**Específicos de Microsoft**

Genera el `rdpmc` instrucción, que lee la supervisión especificado por el contador de rendimiento `counter`.

## <a name="syntax"></a>Sintaxis

```
unsigned __int64 __readpmc( 
   unsigned long counter 
);
```

#### <a name="parameters"></a>Parámetros

*Contador*<br/>
[in] El contador de rendimiento para leer.

## <a name="return-value"></a>Valor devuelto

El valor del contador de rendimiento especificado.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__readpmc`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Esta función intrínseca está disponible en modo de kernel solo, y la rutina solo está disponible como intrínseco.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)