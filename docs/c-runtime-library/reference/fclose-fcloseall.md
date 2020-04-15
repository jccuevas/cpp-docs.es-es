---
title: fclose, _fcloseall
ms.date: 4/2/2020
api_name:
- fclose
- _fcloseall
- _o__fcloseall
- _o_fclose
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fclose
- _fcloseall
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
ms.openlocfilehash: b2ee14c5fc8bb47cc2652443c0263bd14147c90d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347488"
---
# <a name="fclose-_fcloseall"></a>fclose, _fcloseall

Cierra una secuencia (**fclose**) o cierra todas las secuencias abiertas (**_fcloseall**).

## <a name="syntax"></a>Sintaxis

```C
int fclose(
   FILE *stream
);
int _fcloseall( void );
```

### <a name="parameters"></a>Parámetros

*Corriente*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

**fclose** devuelve 0 si la secuencia se cierra correctamente. **_fcloseall** devuelve el número total de secuencias cerradas. Ambas funciones devuelven **EOF** para indicar un error.

## <a name="remarks"></a>Observaciones

La función **fclose** cierra *la secuencia*. Si *stream* es **NULL**, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **fclose** establece **errno** en **EINVAL** y devuelve **EOF**. Se recomienda comprobar siempre que el puntero de *secuencia* antes de llamar a esta función.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.

La función **_fcloseall** cierra todas las secuencias abiertas excepto **stdin**, **stdout**, **stderr** (y, en MS-DOS, **_stdaux** y **_stdprn).** También cierra y elimina los archivos temporales creados por **tmpfile**. En ambas funciones, se vacían todos los búferes asociados a la secuencia antes de cerrarla. Los búferes asignados por el sistema se liberan cuando se cierra la secuencia. Los búferes asignados por el usuario con **setbuf** y **setvbuf** no se liberan automáticamente.

**Nota:** Cuando estas funciones se usan para cerrar una secuencia, se cierran el descriptor de archivo subyacente y el identificador de archivos del SO (o socket), además de la secuencia. Por lo tanto, si el archivo se abrió originalmente como un identificador de archivo o descriptor de archivo y se cierra con **fclose**, no llame también a **_close** para cerrar el descriptor de archivo; no llame a la función **De32 CloseHandle** para cerrar el identificador de archivo.

**fclose** y **_fcloseall** incluir código para proteger contra interferencias de otros subprocesos. Para ver la versión sin bloqueo de un **fclose**, consulte **_fclose_nolock**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fclose**|\<stdio.h>|
|**_fcloseall**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [fopen](fopen-wfopen.md).

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
