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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 227f9e31c689b0259c429e2ffd9fce074903bd71
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920177"
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

*FD*<br/>
Descriptor del archivo abierto.

*mode*<br/>
Tipo de acceso a archivos.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un puntero al flujo abierto. Un valor de puntero null indica un error. Si se produce un error, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EBADF**, que indica un descriptor de archivo incorrecto, o **EINVAL**, que indica que el *modo* era un puntero nulo.

Para obtener más información sobre estos y otros códigos error, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

La función **_fdopen** asocia un flujo de e/s con el archivo identificado por *FD*y, por lo tanto, permite almacenar en búfer y dar formato a un archivo que se abre para la e/s de bajo nivel. **_wfdopen** es una versión con caracteres anchos de **_fdopen**; el argumento de *modo* para **_wfdopen** es una cadena de caracteres anchos. de lo contrario, **_wfdopen** y **_fdopen** se comportan exactamente igual.

Los descriptores de archivo pasados en **_fdopen** son propiedad del **archivo** devuelto &#42;flujo. Si **_fdopen** se realiza correctamente, no llame a [ \_Close](close.md) en el descriptor de archivo. La llamada a [fclose](fclose-fcloseall.md) en el archivo devuelto **&#42;** también cierra el descriptor de archivo.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|\_Unicode y \_MBCS no definidos|\_MBCS definido|\_Unicode definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

La cadena de caracteres *mode* especifica el tipo de acceso a archivos solicitado para el archivo:

| *mode* | Acceso |
|--------|--------|
| **c** | Abre para lectura. Si el archivo no existe o no se encuentra, se produce un error en la llamada **fopen** . |
| **con** | Abre un archivo vacío para escritura. Si el archivo especificado existe, se destruye su contenido. |
| **un** | Abre para escribir al final del archivo (anexando). Crea el archivo si no existe. |
| **"r +"** | Abre para lectura y escritura. El archivo debe existir. |
| **"w +"** | Abre un archivo vacío para lectura y escritura. Si el archivo existe, se destruye su contenido. |
| **"a +"** | Se abre para lectura y anexado. Crea el archivo si no existe. |

Cuando un archivo se abre con el tipo de acceso **"a"** o **"a +"** , todas las operaciones de escritura se producen al final del archivo. El puntero de archivo se puede cambiar de posición mediante [fseek](fseek-fseeki64.md) o [Rewind](rewind.md), pero siempre se vuelve al final del archivo antes de que se realice cualquier operación de escritura. Por lo tanto, los datos existentes no se pueden sobrescribir. Cuando se especifica el tipo de acceso **"r +"**, **"w +"** o **"a +"** , se permiten la lectura y la escritura (se dice que el archivo está abierto para "actualización"). Sin embargo, cuando se cambia entre lectura y escritura, debe haber una operación intermedia [fflush](fflush.md), [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md)o [Rewind](rewind.md) . Si lo desea, puede especificar la posición actual para la operación [fsetpos](fsetpos.md) o [fseek](fseek-fseeki64.md) .

Además de los valores anteriores, también se pueden incluir los caracteres siguientes en *modo* para especificar el modo de traducción de los caracteres de nueva línea:

| modificador de *modo* | Comportamiento |
|-----------------|----------|
| **h** | Abra en modo de texto (traducido). En este modo, las combinaciones de retorno de carro-avance de línea (CR-LF) se convierten en avances de una línea (LF) en la entrada, y los caracteres de LF se traducen en combinaciones de CR-LF en la salida. Además, Ctrl+Z se interpreta como carácter de final de archivo en la entrada. |
| **b** | Abre en modo binario (sin traducir). Se suprimen todas las traducciones del modo **t** . |
| **unidad** | Habilite la marca de confirmación para el *nombre de archivo* asociado para que el contenido del búfer de archivo se escriba directamente en el disco si se llama a **fflush** o **_flushall** . |
| **n** | Restablezca la marca de confirmación para el *nombre de archivo* asociado a "no-commit". Este es el valor predeterminado. También invalida la marca de confirmación global si vincula el programa con Commode. obj. El valor predeterminado de la marca de confirmación global es "no-commit" a menos que vincule explícitamente el programa con Commode. obj. |

Las opciones de *modo* **t**, **c**y **n** son extensiones de Microsoft para **fopen** y **_fdopen**. No las use si desea conservar la portabilidad ANSI.

Si **t** o **b** no se especifican en el *modo*, el modo de traducción predeterminado se define mediante [ \_](../../c-runtime-library/fmode.md)la variable global fmode. Si **t** o **b** tiene como prefijo el argumento, la función produce un error y devuelve NULL. Para obtener una descripción de los modos de texto y binario, consulte [E/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Los caracteres válidos para la cadena de *modo* utilizada en **fopen** y **_fdopen** corresponden a los argumentos *Oflag* usados en [ \_Open](open-wopen.md) y [ \_sopen](sopen-wsopen.md), tal como se muestra en esta tabla:

|Caracteres en cadena de *modo*|Valor *Oflag* equivalente para **_open** y **_sopen**|
|---------------------------------|---------------------------------------------------|
|**un**|**\_O\_WRONLY &#124; \_o\_Append** (normalmente ** \_o\_WRONLY &#124; \_o\_crear &#124; \_o\_Append**)|
|**a +**|**\_O\_RDWR &#124; \_o\_anexar** ( ** \_normalmente\_o RDWR \_&#124;\_o anexar &#124; \_o\_crear** )|
|**r**|**\_O\_RDONLY**|
|**r +**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** (normalmente ** \_o\_WRONLY &#124; \_o\_crear &#124; \_o\_trunc**)|
|**w +**|**\_O\_RDWR** (normalmente ** \_o\_RDWR &#124; \_o\_crear &#124; \_o\_trunc**)|
|**b**|**\_binario O\_**|
|**h**|**\_O\_texto**|
|**unidad**|None|
|**n**|None|

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

### <a name="output"></a>Salida

```Output
Lines in file: 2
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[\_DUP, \_dup2](dup-dup2.md)<br/>
[fclose, \_fcloseall](fclose-fcloseall.md)<br/>
[fopen, \_wfopen](fopen-wfopen.md)<br/>
[freopen, \_wfreopen](freopen-wfreopen.md)<br/>
[\_Open, \_wopen](open-wopen.md)<br/>
