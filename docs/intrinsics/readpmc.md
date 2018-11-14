---
title: __readpmc
ms.date: 11/04/2016
f1_keywords:
- __readpmc
helpviewer_keywords:
- Read Performance Monitoring Counters instruction
- __readpmc intrinsic
- rdpmc instruction
ms.assetid: 14ed45a6-28b6-4635-8437-a597c04b43d4
ms.openlocfilehash: 059d9344fa329e69666abaca4d73122ab29f8d2a
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326438"
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