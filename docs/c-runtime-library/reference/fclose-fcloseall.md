---
title: fclose, _fcloseall | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fclose
- _fcloseall
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
- fclose
- _fcloseall
dev_langs:
- C++
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71b98a239cd1a6504611bf436533e7b5fbe1302c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="fclose-fcloseall"></a>fclose, _fcloseall

Cierra una secuencia (**fclose**) o se cierra todas las secuencias abiertas (**_fcloseall**).

## <a name="syntax"></a>Sintaxis

```C
int fclose(
   FILE *stream
);
int _fcloseall( void );
```

### <a name="parameters"></a>Parámetros

*Secuencia*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

**fclose** devuelve 0 si la secuencia está cerrada correctamente. **_fcloseall** devuelve el número total de secuencias que se cierra. Ambas funciones devuelven **EOF** para indicar un error.

## <a name="remarks"></a>Comentarios

El **fclose** función se cierra *flujo*. Si *flujo* es **NULL**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **fclose** establece **errno** a **EINVAL** y devuelve **EOF**. Se recomienda que el *flujo* puntero siempre se comprueba antes de llamar a esta función.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.

El **_fcloseall** función cierra todas las secuencias abiertas excepto **stdin**, **stdout**, **stderr** (y, en MS-DOS, **_stdaux**  y **_stdprn**). También se cierra y se elimina los archivos temporales creados por **tmpfile**. En ambas funciones, se vacían todos los búferes asociados a la secuencia antes de cerrarla. Los búferes asignados por el sistema se liberan cuando se cierra la secuencia. Búferes asignados por el usuario con **setbuf** y **setvbuf ()** no se liberan automáticamente.

**Nota:** Cuando estas funciones se usan para cerrar una secuencia, se cierran el descriptor de archivo subyacente y el identificador de archivos del SO (o socket), además de la secuencia. Por lo tanto, si el archivo se abrió originalmente como un archivo controlar o descriptor de archivo y se cierra con **fclose**, hagan no también llamada **_close** para cerrar el descriptor de archivo; no llame a la función de Win32  **CloseHandle** para cerrar el identificador de archivo.

**fclose** y **_fcloseall** incluir código para proteger frente a interferencias de otros subprocesos. Para la versión no realiza el bloqueo de un **fclose**, consulte **_fclose_nolock**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fclose**|\<stdio.h>|
|**_fcloseall**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [fopen](fopen-wfopen.md).

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
