---
title: fwide | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd52c450e2eb34c40d44d00a76550c401abcb6c9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397276"
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