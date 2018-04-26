---
title: fwide | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- fwide
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- fwide
dev_langs:
- C++
helpviewer_keywords:
- fwide function
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a055df312215b5ff424aff54cfee54e0568ab307
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="fwide"></a>fwide

Sin implementar.

## <a name="syntax"></a>Sintaxis

```C
int fwide(
   FILE *stream,
   int mode;
);
```

### <a name="parameters"></a>Parámetros

*Secuencia*<br/>
Puntero a **archivo** estructura (pasa por alto).

*mode*<br/>
Nuevo ancho de la secuencia: positivo para carácter ancho, negativo para byte, cero para dejarlo sin cambios. (Este valor se omite).

## <a name="return-value"></a>Valor devuelto

Esta función devuelve actualmente solo *modo*.

## <a name="remarks"></a>Comentarios

La versión actual de esta función no cumple con el estándar.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fwide**|\<wchar.h>|

Para obtener más información, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).