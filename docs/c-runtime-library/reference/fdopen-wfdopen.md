---
title: _fdopen, _wfdopen
ms.date: 4/2/2020
api_name:
- _fdopen
- _wfdopen
- _o__fdopen
- _o__wfdopen
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
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tfdopen
- _fdopen
- _wfdopen
- wfdopen
- tfdopen
helpviewer_keywords:
- wfdopen function
- _fdopen function
- _wfdopen function
- tfdopen function
- fdopen function
- _tfdopen function
- streams, associating with files
ms.assetid: 262757ff-1e09-4472-a5b6-4325fc28f971
ms.openlocfilehash: 82a7e891e8bd6031ebbf761534b6df7cd8488d36
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347387"
---
# <a name="_fdopen-_wfdopen"></a>_fdopen, _wfdopen

Asocia un flujo a un archivo que se abrió previamente para E/S de bajo nivel.

## <a name="syntax"></a>Sintaxis

```C
FILE *_fdopen(
   int fd,
   const char *mode
);
FILE *_wfdopen(
   int fd,
   const wchar_t *mode
);
```

### <a name="parameters"></a>Parámetros

*Fd*<br/>
Descriptor del archivo abierto.

*Modo*<br/>
Tipo de acceso a archivos.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un puntero al flujo abierto. Un valor de puntero null indica un error. Si se produce un error, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EBADF**, que indica un descriptor de archivo incorrecto, o **EINVAL**, que indica que *el modo* era un puntero nulo.

Para obtener más información sobre estos y otros códigos error, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

La función **_fdopen** asocia una secuencia de E/S con el archivo identificado por *fd*y, por lo tanto, permite que un archivo que se abre para E/S de bajo nivel se almacena en búfer y se formatea. **_wfdopen** es una versión de caracteres anchos de **_fdopen;** el argumento *mode* para **_wfdopen** es una cadena de caracteres anchos. **_wfdopen** y **_fdopen** comportarse de manera idéntica.

Los descriptores de archivo pasados **a _fdopen** son propiedad de la secuencia de &#42;**file devuelta.** Si **_fdopen** se realiza correctamente, no llame a [ \_close](close.md) en el descriptor de archivo. Al llamar a [fclose](fclose-fcloseall.md) en el **&#42;FILE** devuelto también se cierra el descriptor de archivo.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|\_UNICODE \_y MBCS no definidos|\_MBCS definido|\_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

La cadena de caracteres de *modo* especifica el tipo de acceso a archivos solicitado para el archivo:

| *Modo* | Acceso |
|--------|--------|
| **"R"** | Abre para lectura. Si el archivo no existe o no se puede encontrar, se produce un error en la llamada **fopen.** |
| **"W"** | Abre un archivo vacío para escritura. Si el archivo especificado existe, se destruye su contenido. |
| **"A"** | Se abre para escribir al final del archivo (anexar). Crea el archivo si no existe. |
| **"r+"** | Abre para lectura y escritura. El archivo debe existir. |
| **"w+"** | Abre un archivo vacío para lectura y escritura. Si el archivo existe, se destruye su contenido. |
| **"a+"** | Se abre para lectura y anexado. Crea el archivo si no existe. |

Cuando se abre un archivo con el tipo de acceso **"a"** o **"a+",** todas las operaciones de escritura se producen al final del archivo. El puntero de archivo se puede cambiar de posición mediante [fseek](fseek-fseeki64.md) o [rebobinado](rewind.md), pero siempre se mueve de nuevo al final del archivo antes de que se lleve a cabo cualquier operación de escritura. Por lo tanto, los datos existentes no se pueden sobrescribir. Cuando se especifica el tipo de acceso **"r+"**, **"w+"** o **"a+",** se permiten tanto la lectura como la escritura (se dice que el archivo está abierto para "actualización"). Sin embargo, al cambiar entre lectura y escritura, debe haber una operación [de fflush,](fflush.md) [fsetpos,](fsetpos.md) [fseek](fseek-fseeki64.md)o [rebobinado](rewind.md) que intervenga. Puede especificar la posición actual para la operación [fsetpos](fsetpos.md) o [fseek,](fseek-fseeki64.md) si lo desea.

Además de los valores anteriores, los siguientes caracteres también se pueden incluir en el *modo* para especificar el modo de traducción para los caracteres de nueva línea:

| modificador *de modo* | Comportamiento |
|-----------------|----------|
| **T** | Abra en modo de texto (traducido). En este modo, las combinaciones de retorno de carro-avance de línea (CR-LF) se convierten en avances de una línea (LF) en la entrada, y los caracteres de LF se traducen en combinaciones de CR-LF en la salida. Además, Ctrl+Z se interpreta como carácter de final de archivo en la entrada. |
| **B** | Abre en modo binario (sin traducir). Se suprimen todas las traducciones del modo **t.** |
| **C** | Habilite el indicador de confirmación para el nombre de *archivo* asociado para que el contenido del búfer de archivos se escriba directamente en el disco si se llama a **fflush** o **_flushall.** |
| **N** | Restablezca la marca de confirmación para el nombre de *archivo* asociado a "no-commit." Este es el valor predeterminado. También invalida la marca de confirmación global si vincula el programa con Commode.obj. El valor predeterminado de la marca de confirmación global es "no-commit" a menos que vincule explícitamente el programa con Commode.obj. |

Las opciones de **n** *modo* **t**, **c**y n son extensiones de Microsoft para **fopen** y **_fdopen**. No las use si desea conservar la portabilidad ANSI.

Si **t** o **b** no se da en *modo*, el modo de traducción predeterminado se define mediante la variable [ \_](../../c-runtime-library/fmode.md)global fmode . Si **t** o **b** tiene como prefijo el argumento, se produce un error en la función y devuelve NULL. Para obtener una descripción de los modos de texto y binario, consulte [E/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Los caracteres válidos para la cadena de *modo* utilizada en **fopen** y **_fdopen** corresponden a argumentos *oflag* utilizados en [ \_open](open-wopen.md) y [ \_sopen,](sopen-wsopen.md)como se muestra en esta tabla:

|Caracteres en cadena *de modo*|Valor *oflag* equivalente para **_open** y **_sopen**|
|---------------------------------|---------------------------------------------------|
|**Un**|**\_O\_WRONLY \_\_&#124; O APPEND** (normalmente ** \_O\_WRONLY &#124; \_O\_CREAT &#124; \_O\_APPEND)**|
|**a+**|**\_O\_RDWR \_\_&#124; O APPEND** (normalmente ** \_ \_O\_\_RDWR \_&#124; O\_APPEND &#124; O CREAT** )|
|**R**|**\_O\_RDONLY**|
|**r+**|**\_O\_RDWR**|
|**W**|**\_O\_WRONLY** (normalmente ** \_\_ \_O\_WRONLY \_\_&#124; O CREAT &#124; O TRUNC**)|
|**w+**|**\_O\_RDWR** (normalmente ** \_\_ \_O\_RDWR \_\_&#124; O CREAT &#124; O TRUNC**)|
|**B**|**\_O\_BINARY**|
|**T**|**\_O\_TEXTO**|
|**C**|None|
|**N**|None|

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fdopen**|\<stdio.h>|
|**_wfdopen**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```c
// crt_fdopen.c
// This program opens a file by using low-level
// I/O, then uses _fdopen to switch to stream
// access. It counts the lines in the file.

#include <stdlib.h>
#include <stdio.h>
#include <fcntl.h>
#include <io.h>
#include <share.h>

int main( void )
{
   FILE *stream;
   int  fd, count = 0;
   char inbuf[128];

   // Open a file.
   if( _sopen_s( &fd, "crt_fdopen.txt", _O_RDONLY, _SH_DENYNO, 0 ) )
      exit( 1 );

   // Get stream from file descriptor.
   if( (stream = _fdopen( fd, "r" )) == NULL )
      exit( 1 );

   while( fgets( inbuf, 128, stream ) != NULL )
      count++;

   // After _fdopen, close by using fclose, not _close.
   fclose( stream );
   printf( "Lines in file: %d\n", count );
}
```

### <a name="input-crt_fdopentxt"></a>Entrada: crt_fdopen.txt

```Input
Line one
Line two
```

### <a name="output"></a>Output

```Output
Lines in file: 2
```

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[\_dup, \_dup2](dup-dup2.md)<br/>
[fclose, \_fcloseall](fclose-fcloseall.md)<br/>
[fopen, \_wfopen](fopen-wfopen.md)<br/>
[freopen, \_wfreopen](freopen-wfreopen.md)<br/>
[\_abierto, \_wopen](open-wopen.md)<br/>
