---
title: ftell, _ftelli64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _ftelli64
- ftell
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
- _ftelli64
- ftell
dev_langs:
- C++
helpviewer_keywords:
- ftell function
- ftelli64 function
- _ftelli64 function
- file pointers [C++], getting current position
- file pointers [C++]
ms.assetid: 40149cd8-65f2-42ff-b70c-68e3e918cdd7
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3661f4fa36ff83ca47a4847ff416edb3cef0c2fc
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="ftell-ftelli64"></a>ftell, _ftelli64

Obtiene la posición actual de un puntero de archivo.

## <a name="syntax"></a>Sintaxis

```C
long ftell(
   FILE *stream
);
__int64 _ftelli64(
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*Secuencia*<br/>
Destino **archivo** estructura.

## <a name="return-value"></a>Valor devuelto

**ftell** y **_ftelli64** devolver la posición actual del archivo. El valor devuelto por **ftell** y **_ftelli64** podría no reflejar el desplazamiento de bytes físico para las secuencias que se abre en modo de texto, porque el modo de texto hace que la traducción de avance de línea de retorno de carro. Use **ftell** con [fseek](fseek-fseeki64.md) o **_ftelli64** con [_fseeki64](fseek-fseeki64.md) para volver a ubicaciones de archivos correctamente. En caso de error, **ftell** y **_ftelli64** invocan el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven-1 L y establecen **errno** a uno de dos constantes, definidas en ERRNO. H. El **EBADF** constante significa el *flujo* el argumento no es un valor de puntero de archivo válido o no hace referencia a un archivo abierto. **EINVAL** significa que no es válida *flujo* argumento se pasó a la función. En los dispositivos sin capacidad de búsqueda (por ejemplo, los elementos terminales e impresoras), o cuando *flujo* no hace referencia a un archivo abierto, el valor devuelto es indefinido.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.

## <a name="remarks"></a>Comentarios

El **ftell** y **_ftelli64** funciones recuperan la posición actual del puntero de archivo (si existe) asociada a *flujo*. La posición se expresa como un desplazamiento en relación con el principio del flujo.

Tenga en cuenta que cuando un archivo se abre para anexar datos, la posición de archivo actual se determina con la última operación de E/S, no en función de dónde se produciría la siguiente escritura. Por ejemplo, si un archivo se abre para anexar y la última operación fue de lectura, la posición de archivo es el punto donde empezaría la siguiente operación de lectura, no donde empezaría la siguiente escritura. (Cuando se abre un archivo para anexar, la posición de archivo se mueve al final del archivo antes de cualquier operación de escritura). Si todavía no se ha producido ninguna operación de E/S en un archivo abierto para anexar, la posición de archivo se sitúa al principio del archivo.

En modo de texto, CTRL+Z se interpreta como un carácter de final de archivo en la entrada. En los archivos abiertos para lectura/escritura, **fopen** y todas las rutinas relacionadas, busque un CTRL+Z al final del archivo y quitarlo si es posible. Esto se hace porque usa la combinación de **ftell** y [fseek](fseek-fseeki64.md) o **_ftelli64** y [_fseeki64](fseek-fseeki64.md), para desplazarse por un archivo que termina por puede provocar un CTRL+Z **ftell** o **_ftelli64** para que se comporte de forma incorrecta cerca del final del archivo.

Esta función bloquea el subproceso de llamada durante la ejecución y por lo tanto es segura para subprocesos. Para obtener una versión de no bloqueo, vea **_ftell_nolock**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|Encabezados opcionales|
|--------------|---------------------|----------------------|
|**ftell**|\<stdio.h>|\<errno.h>|
|**_ftelli64**|\<stdio.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_ftell.c
// This program opens a file named CRT_FTELL.C
// for reading and tries to read 100 characters. It
// then uses ftell to determine the position of the
// file pointer and displays this position.

#include <stdio.h>

FILE *stream;

int main( void )
{
   long position;
   char list[100];
   if( fopen_s( &stream, "crt_ftell.c", "rb" ) == 0 )
   {
      // Move the pointer by reading data:
      fread( list, sizeof( char ), 100, stream );
      // Get position after read:
      position = ftell( stream );
      printf( "Position after trying to read 100 bytes: %ld\n",
              position );
      fclose( stream );
   }
}
```

```Output
Position after trying to read 100 bytes: 100
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[fgetpos](fgetpos.md)<br/>
[fseek, _fseeki64](fseek-fseeki64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
