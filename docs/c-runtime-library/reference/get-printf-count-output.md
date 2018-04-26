---
title: _get_printf_count_output | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _get_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_printf_count_output
- _get_printf_count_output
dev_langs:
- C++
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b96aab9e075386f71439a5c528fcf072097d389
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="getprintfcountoutput"></a>_get_printf_count_output

Indica si [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)-familia de funciones de compatibilidad con la **%n** formato.

## <a name="syntax"></a>Sintaxis

```C
int _get_printf_count_output();
```

## <a name="return-value"></a>Valor devuelto

Es distinto de cero if **%n** se admite, 0 si **%n** no se admite.

## <a name="remarks"></a>Comentarios

Si **%n** es no compatible (predeterminada), encontrar **%n** en la cadena de formato de cualquiera de los **printf** funciones invocará el controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si **%n** compatibilidad está habilitada (vea [_set_printf_count_output](set-printf-count-output.md)), a continuación, **%n** se comportarán como se describe en [sintaxis de especificación de formato: printf y wprintf Funciones](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_get_printf_count_output**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [_set_printf_count_output](set-printf-count-output.md).

## <a name="see-also"></a>Vea también

[_set_printf_count_output](set-printf-count-output.md)<br/>
