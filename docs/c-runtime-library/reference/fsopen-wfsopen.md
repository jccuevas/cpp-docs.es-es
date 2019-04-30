---
title: _fsopen, _wfsopen
ms.date: 11/04/2016
apiname:
- _wfsopen
- _fsopen
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
- wfsopen
- fsopen
- tfsopen
- _tfsopen
- _wfsopen
- _fsopen
helpviewer_keywords:
- opening files, streams
- fsopen function
- tfsopen function
- wfsopen function
- _fsopen function
- files [C++], opening
- _tfsopen function
- _wfsopen function
- file sharing [C++]
ms.assetid: 5e4502ab-48a9-4bee-a263-ebac8d638dec
ms.openlocfilehash: 197a4f690a6626edbfec27ea4abef1999b6cedaf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287711"
---
# <a name="fsopen-wfsopen"></a>_fsopen, _wfsopen

Abre un flujo con uso compartido de archivos.

## <a name="syntax"></a>Sintaxis

```C
FILE *_fsopen(
   const char *filename,
   const char *mode,
   int shflag
);
FILE *_wfsopen(
   const wchar_t *filename,
   const wchar_t *mode,
   int shflag
);
```

### <a name="parameters"></a>Parámetros

*filename*<br/>
Nombre del archivo que se va a abrir.

*mode*<br/>
Tipo de acceso permitido.

*shflag*<br/>
Tipo de uso compartido permitido.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un puntero al flujo. Un valor de puntero null indica un error. Si *filename* o *modo* es **NULL** o una cadena vacía, estas funciones invocan el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros ](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven **NULL** y establecer **errno** a **EINVAL**.

Para obtener más información sobre estos y otros códigos error, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_fsopen** función abre el archivo especificado por *filename* como una secuencia y prepara el archivo para la posterior lectura o escritura compartida, como se define en el modo y *shflag*argumentos. **_wfsopen** es una versión con caracteres anchos de **_fsopen**; el *filename* y *modo* argumentos **_wfsopen** son cadenas de caracteres anchos. **_wfsopen** y **_fsopen** se comportan exactamente igual.

La cadena de caracteres *modo* especifica el tipo de acceso solicitado para el archivo, como se muestra en la tabla siguiente.

|Término|Definición|
|----------|----------------|
|**"r"**|Abre para lectura. Si el archivo no existe o no se encuentra el **_fsopen** llamar se produce un error.|
|**"w"**|Abre un archivo vacío para escritura. Si el archivo especificado existe, se destruye su contenido.|
|**"a"**|Se abre para escribir al final del archivo (anexo); primero crea el archivo si no existe.|
|**"r+"**|Abre para lectura y escritura. (El archivo debe existir.)|
|**"w+"**|Abre un archivo vacío para lectura y escritura. Si el archivo especificado existe, se destruye su contenido.|
|**"a+"**|Se abre para leer y anexar; primero crea el archivo si no existe.|

Use la **"w"** y **"w +"** tipos con cuidado, ya que podrían destruir archivos existentes.

Cuando se abre un archivo con el **"a"** o **"a +"** acceso tipo, todas las operaciones se producen al final del archivo de escritura. Se puede mover el puntero de archivo mediante [fseek](fseek-fseeki64.md) o [rebobinar](rewind.md), pero se desplaza siempre al final del archivo antes de cualquier escritura operación se lleva a cabo. Por consiguiente, los datos existentes no pueden sobrescribirse. Cuando el **"r +"**, **"w +"**, o **"a +"** se especifica el tipo de acceso, se permiten operaciones de lectura y escritura (se dice que el archivo está abierto para actualización). En cambio, si se cambia entre lectura y escritura, debe haber una operación intermedia [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md) o [rewind](rewind.md). Se puede especificar la posición actual para el [fsetpos](fsetpos.md) o [fseek](fseek-fseeki64.md) operación, si lo desea. Además de los valores anteriores, uno de los siguientes caracteres puede incluirse en *modo* para especificar el modo de traducción para las nuevas líneas y de administración de archivos.

|Término|Definición|
|----------|----------------|
|**t**|Abre un archivo en modo de texto (traducido). En este modo, fuente (CR-LF) combinaciones de retorno de la línea de carro se traducen en avances de una línea (LF) en la entrada y caracteres de LF se traducen en combinaciones CR-LF en la salida. Además, CTRL+Z se interpreta como carácter de final de archivo en la entrada. En los archivos abiertos para lectura o lectura/escritura, **_fsopen** comprueba un CTRL+Z al final del archivo y lo quita, si es posible. Esto se hace porque utilizar [fseek](fseek-fseeki64.md) y [ftell](ftell-ftelli64.md) para desplazarse por un archivo que finaliza con CTRL+Z puede hacer que [fseek](fseek-fseeki64.md) para que se comporte de forma incorrecta cerca del final del archivo.|
|**b**|Abre un archivo en modo binario (sin traducir); las conversiones anteriores se suprimen.|
|**S**|Especifica que el almacenamiento en caché está optimizado para el acceso secuencial (pero no restringido a este) desde el disco.|
|**R**|Especifica que el almacenamiento en caché está optimizado para el acceso aleatorio (pero no restringido a este) desde el disco.|
|**T**|Especifica un archivo como temporal. Si es posible, no se vuelca en el disco.|
|**D**|Especifica un archivo como temporal. Se elimina cuando se cierra el puntero del último archivo.|

Si no se especifica **t** o **b** en *mode*, el modo de traducción está definido por la variable de modo predeterminado **_fmode**. Si **t** o **b** tiene como prefijo para el argumento, la función produce un error y devuelve **NULL**. Para obtener una descripción de los modos de texto y binario, consulte [E/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

El argumento *shflag* es una expresión constante compuesta por una de las siguientes constantes de manifiesto, definidas en Share.h.

|Término|Definición|
|----------|----------------|
|**_SH_COMPAT**|Establece el modo de compatibilidad para aplicaciones de 16 bits.|
|**_SH_DENYNO**|Permite el acceso de lectura y escritura.|
|**_SH_DENYRD**|Deniega el acceso de lectura al archivo.|
|**_SH_DENYRW**|Deniega el acceso de lectura y escritura al archivo.|
|**_SH_DENYWR**|Deniega el acceso de escritura al archivo.|

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfsopen**|**_fsopen**|**_fsopen**|**_wfsopen**|

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|Encabezados opcionales|
|--------------|---------------------|----------------------|
|**_fsopen**|\<stdio.h>|\<share.h><br /><br /> Para la constante de manifiesto para *shflag* parámetro.|
|**_wfsopen**|\<stdio.h> o \<wchar.h>|\<share.h><br /><br /> Para la constante de manifiesto para *shflag* parámetro.|

## <a name="example"></a>Ejemplo

```C
// crt_fsopen.c

#include <stdio.h>
#include <stdlib.h>
#include <share.h>

int main( void )
{
   FILE *stream;

   // Open output file for writing. Using _fsopen allows us to
   // ensure that no one else writes to the file while we are
   // writing to it.
    //
   if( (stream = _fsopen( "outfile", "wt", _SH_DENYWR )) != NULL )
   {
      fprintf( stream, "No one else in the network can write "
                       "to this file until we are done.\n" );
      fclose( stream );
   }
   // Now others can write to the file while we read it.
   system( "type outfile" );
}
```

```Output
No one else in the network can write to this file until we are done.
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
