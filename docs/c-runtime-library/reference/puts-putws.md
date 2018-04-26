---
title: puts, _putws | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _putws
- puts
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
- _putts
- _putws
- puts
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], writing
- _putts function
- standard output, writing to
- putws function
- puts function
- putts function
- _putws function
ms.assetid: 32dada12-ed45-40ac-be06-3feeced9ecd6
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a823106478e575f9b2d65bc4e739236098da5124
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="puts-putws"></a>puts, _putws

Escribe una cadena en **stdout**.

## <a name="syntax"></a>Sintaxis

```C
int puts(
   const char *str
);
int _putws(
   const wchar_t *str
);
```

### <a name="parameters"></a>Parámetros

*str*<br/>
Cadena de salida

## <a name="return-value"></a>Valor devuelto

Devuelve un valor no negativo si se ejecuta correctamente. Si **coloca** produce un error, devuelve **EOF**; si **_putws** produce un error, devuelve **WEOF**. Si *str* es un puntero nulo, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones establecen **errno** a **EINVAL** y devolver **EOF** o **WEOF**.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **coloca** función escrituras *str* en el flujo de salida estándar **stdout**, reemplazando la cadena del carácter nulo de terminación ('\0') con un carácter de nueva línea ('\n') en el flujo de salida.

**_putws** es la versión con caracteres anchos de **coloca**; las dos funciones se comportan exactamente igual si el flujo se abre en modo ANSI. **coloca** no admite actualmente la salida en un flujo UNICODE.

**_putwch** escribe caracteres Unicode mediante la configuración regional de la consola actual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_putts**|**puts**|**puts**|**_putws**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**puts**|\<stdio.h>|
|**_putws**|\<stdio.h>|

La consola no se admite en aplicaciones de la plataforma Universal de Windows (UWP). Los identificadores de secuencia estándar que están asociados a la consola, **stdin**, **stdout**, y **stderr**, se deben redirigir antes funciones de tiempo de ejecución de C puedan usarlos en las aplicaciones UWP . Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_puts.c
// This program uses puts to write a string to stdout.

#include <stdio.h>

int main( void )
{
   puts( "Hello world from puts!" );
}
```

### <a name="output"></a>Salida

```Output
Hello world from puts!
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[fgets, fgetws](fgets-fgetws.md)<br/>
