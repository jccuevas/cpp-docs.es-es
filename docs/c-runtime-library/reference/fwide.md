---
title: fwide
ms.date: 11/04/2016
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
helpviewer_keywords:
- fwide function
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
ms.openlocfilehash: d992ebc527744beeb4ef14175e3f10646a77a064
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557854"
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

*secuencia*<br/>
Puntero a **archivo** estructura (omitido).

*mode*<br/>
Nuevo ancho de la secuencia: positivo para carácter ancho, negativo para byte, cero para dejarlo sin cambios. (Este valor se omite).

## <a name="return-value"></a>Valor devuelto

Actualmente, solo devuelve esta función *modo*.

## <a name="remarks"></a>Comentarios

La versión actual de esta función no cumple con el estándar.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fwide**|\<wchar.h>|

Para obtener más información, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).