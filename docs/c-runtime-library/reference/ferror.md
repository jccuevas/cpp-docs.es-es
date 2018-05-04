---
title: ferror | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- ferror
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
- ferror
dev_langs:
- C++
helpviewer_keywords:
- ferror function
- streams, testing for errors
- errors [C++], testing for stream
ms.assetid: 528a34bc-f2aa-4c3f-b89a-5b148e6864f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49aaff776a90dd687ee4dae1902903ed01b83e20
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ferror"></a>ferror

Pruebas de error en una secuencia.

## <a name="syntax"></a>Sintaxis

```C
int ferror(
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*Secuencia*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

Si no se ha producido ningún error en *flujo*, **ferror** devuelve 0. De lo contrario, devuelve un valor distinto de cero. Si la secuencia es **NULL**, **ferror** invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** a **EINVAL** y devuelve 0.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.

## <a name="remarks"></a>Comentarios

El **ferror** rutina (se implementa como una función y como una macro) comprueba al leer o escribir el error en el archivo asociado a *flujo*. Si se ha producido un error, el indicador de error de la secuencia permanece establecido hasta que la secuencia está cerrada o se rebobina o hasta que **clearerr** se llama con ella.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**ferror**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [feof](feof.md).

## <a name="see-also"></a>Vea también

[Control de errores](../../c-runtime-library/error-handling-crt.md)<br/>
[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
