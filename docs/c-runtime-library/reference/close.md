---
title: _close
ms.date: 11/04/2016
api_name:
- _close
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _close
helpviewer_keywords:
- _close function
- close function
- files [C++], closing
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
ms.openlocfilehash: e274cd45c42a5cf49430ecce69e111cbbf6fe88b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942929"
---
# <a name="_close"></a>_close

Cierra un archivo.

## <a name="syntax"></a>Sintaxis

```C
int _close(
   int fd
);
```

### <a name="parameters"></a>Parámetros

*fd*<br/>
Descriptor de archivo que hace referencia al archivo abierto.

## <a name="return-value"></a>Valor devuelto

**_close** devuelve 0 si el archivo se ha cerrado correctamente. Un valor devuelto de-1 indica un error.

## <a name="remarks"></a>Comentarios

La función **_close** cierra el archivo asociado con *FD*.

El descriptor de archivo y el identificador de archivos del sistema operativo subyacente se cierran. Por lo tanto, no es necesario llamar a **CloseHandle** si el archivo se abrió originalmente con la función de Win32 **CreateFile** y se convirtió en un descriptor de archivo mediante **_open_osfhandle**.

Esta función valida sus parámetros. Si *FD* es un descriptor de archivo incorrecto, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones devuelven-1 y **errno** se establece en **EBADF**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_close**|\<io.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [_open](open-wopen.md).

## <a name="see-also"></a>Vea también

[E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)<br/>
[_chsize](chsize.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_unlink, _wunlink](unlink-wunlink.md)<br/>
