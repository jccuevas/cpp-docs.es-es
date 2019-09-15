---
title: _fsopen, _wfsopen
ms.date: 11/04/2016
api_name:
- _wfsopen
- _fsopen
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
ms.openlocfilehash: 1ffc3aa5801ff2ed63ecf815f3351e4d7a8cf459
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956481"
---
# <a name="_fsopen-_wfsopen"></a>_fsopen, _wfsopen

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

Cada una de estas funciones devuelve un puntero al flujo. Un valor de puntero null indica un error. Si *filename* o *mode* es **null** o una cadena vacía, estas funciones invocan el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven **null** y establecen **errno** en **EINVAL**.

Para obtener más información sobre estos y otros códigos error, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

La función **_fsopen** abre el archivo especificado por *filename* como una secuencia y prepara el archivo para la lectura o escritura compartida posterior, tal como se define en los argumentos Mode y *shflag* . **_wfsopen** es una versión con caracteres anchos de **_fsopen**; los argumentos *filename* y *mode* de **_wfsopen** son cadenas de caracteres anchos. **_wfsopen** y **_fsopen** se comportan de manera idéntica.

El *modo* de cadena de caracteres especifica el tipo de acceso solicitado para el archivo, como se muestra en la tabla siguiente.

|Término|Definición|
|----------|----------------|
|**"r"**|Abre para lectura. Si el archivo no existe o no se encuentra, se produce un error en la llamada a **_fsopen** .|
|**"w"**|Abre un archivo vacío para escritura. Si el archivo especificado existe, se destruye su contenido.|
|**"a"**|Se abre para escribir al final del archivo (anexo); primero crea el archivo si no existe.|
|**"r+"**|Abre para lectura y escritura. (El archivo debe existir.)|
|**"w+"**|Abre un archivo vacío para lectura y escritura. Si el archivo especificado existe, se destruye su contenido.|
|**"a+"**|Se abre para leer y anexar; primero crea el archivo si no existe.|

Use los tipos **"w"** y **"w +"** con cuidado, ya que pueden destruir archivos existentes.

Cuando un archivo se abre con el tipo de acceso **"a"** o **"a +"** , todas las operaciones de escritura se producen al final del archivo. El puntero de archivo se puede cambiar de posición con [fseek](fseek-fseeki64.md) o [rebobinar](rewind.md), pero siempre se vuelve a mover al final del archivo antes de que se realice cualquier operación de escritura. Por consiguiente, los datos existentes no pueden sobrescribirse. Cuando se especifica el tipo de acceso **"r +"** , **"w +"** o **"a +"** , se permiten la lectura y la escritura (se dice que el archivo está abierto para la actualización). En cambio, si se cambia entre lectura y escritura, debe haber una operación intermedia [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md) o [rewind](rewind.md). Si se desea, se puede especificar la posición actual para la operación [fsetpos](fsetpos.md) o [fseek](fseek-fseeki64.md) . Además de los valores anteriores, se puede incluir uno de los siguientes caracteres en el *modo* para especificar el modo de traducción de las nuevas líneas y para la administración de archivos.

|Término|Definición|
|----------|----------------|
|**t**|Abre un archivo en modo de texto (traducido). En este modo, las combinaciones de retorno de carro y avance de línea (CR-LF) se convierten en avances de una línea (LF) en la entrada y los caracteres de LF se traducen en combinaciones de CR-LF en la salida. Además, CTRL+Z se interpreta como carácter de final de archivo en la entrada. En los archivos abiertos para lectura o lectura/escritura, **_fsopen** comprueba si hay un Ctrl + Z al final del archivo y lo quita, si es posible. Esto se hace porque el uso de [fseek](fseek-fseeki64.md) y [ftell](ftell-ftelli64.md) para desplace dentro de un archivo que finaliza con Ctrl + Z puede hacer que [fseek](fseek-fseeki64.md) se comporte de forma incorrecta cerca del final del archivo.|
|**b**|Abre un archivo en modo binario (sin traducir); las conversiones anteriores se suprimen.|
|**S**|Especifica que el almacenamiento en caché está optimizado para el acceso secuencial (pero no restringido a este) desde el disco.|
|**R**|Especifica que el almacenamiento en caché está optimizado para el acceso aleatorio (pero no restringido a este) desde el disco.|
|**T**|Especifica un archivo como temporal. Si es posible, no se vuelca en el disco.|
|**D**|Especifica un archivo como temporal. Se elimina cuando se cierra el puntero del último archivo.|

Si no se especifica **t** o **b** en *mode*, el modo de traducción está definido por la variable de modo predeterminado **_fmode**. Si **t** o **b** tiene como prefijo el argumento, la función produce un error y devuelve **null**. Para obtener una descripción de los modos de texto y binario, consulte [E/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

El argumento *shflag* es una expresión constante formada por una de las constantes de manifiesto siguientes, definidas en Share. h.

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
|**_fsopen**|\<stdio.h>|\<share.h><br /><br /> Para la constante de manifiesto para el parámetro *shflag* .|
|**_wfsopen**|\<stdio.h> o \<wchar.h>|\<share.h><br /><br /> Para la constante de manifiesto para el parámetro *shflag* .|

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
