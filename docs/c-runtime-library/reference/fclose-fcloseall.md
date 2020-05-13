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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 3f8567f7bb01c519938f5a4e28bbb33bce09dffe
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920226"
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

*misiones*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

**fclose** devuelve 0 si la secuencia se ha cerrado correctamente. **_fcloseall** devuelve el número total de secuencias cerradas. Ambas funciones devuelven **EOF** para indicar un error.

## <a name="remarks"></a>Observaciones

La función **fclose** cierra la *secuencia*. Si *Stream* es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **fclose** establece **errno** en **EINVAL** y devuelve **EOF**. Se recomienda comprobar siempre el puntero de *secuencia* antes de llamar a esta función.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.

La función **_fcloseall** cierra todas las secuencias abiertas excepto **stdin**, **stdout**, **stderr** (y, en MS-dos, **_stdaux** y **_stdprn**). También cierra y elimina los archivos temporales creados por **tmpfile**. En ambas funciones, se vacían todos los búferes asociados a la secuencia antes de cerrarla. Los búferes asignados por el sistema se liberan cuando se cierra la secuencia. Los búferes asignados por el usuario con **setbuf** y **setvbuf (** no se liberan automáticamente.

**Nota:** Cuando estas funciones se usan para cerrar una secuencia, se cierran el descriptor de archivo subyacente y el identificador de archivos del SO (o socket), además de la secuencia. Por lo tanto, si el archivo se abrió originalmente como un identificador de archivo o un descriptor de archivo y se cierra con **fclose**, no llame también **_close** para cerrar el descriptor de archivo; no llame a la función de Win32 **CloseHandle** para cerrar el identificador de archivo.

**fclose** y **_fcloseall** incluyen código para proteger frente a interferencias de otros subprocesos. Para obtener una versión que no sea de bloqueo de un **fclose**, vea **_fclose_nolock**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fclose**|\<stdio.h>|
|**_fcloseall**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [fopen](fopen-wfopen.md).

## <a name="see-also"></a>Consulta también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
