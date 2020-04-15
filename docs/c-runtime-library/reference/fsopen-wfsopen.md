---
title: _fsopen, _wfsopen
ms.date: 4/2/2020
api_name:
- _wfsopen
- _fsopen
- _o__fsopen
- _o__wfsopen
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
ms.openlocfilehash: 49907808729375e3bea18a5f4bbf204852e0072a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345696"
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

*Nombre*<br/>
Nombre del archivo que se va a abrir.

*Modo*<br/>
Tipo de acceso permitido.

*shflag*<br/>
Tipo de uso compartido permitido.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un puntero al flujo. Un valor de puntero null indica un error. Si *filename* o *mode* es **NULL** o una cadena vacía, estas funciones invocan el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven **NULL** y **establecen errno en** **EINVAL**.

Para obtener más información sobre estos y otros códigos error, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

La función **_fsopen** abre el archivo especificado por *filename* como una secuencia y prepara el archivo para la lectura o escritura compartida sin continuación, tal como se define en los argumentos mode y *shflag.* **_wfsopen** es una versión de caracteres anchos de **_fsopen**; los argumentos *filename* y *mode* para **_wfsopen** son cadenas de caracteres anchos. **_wfsopen** y **_fsopen** comportarse de forma idéntica de lo contrario.

El *modo* de cadena de caracteres especifica el tipo de acceso solicitado para el archivo, como se muestra en la tabla siguiente.

|Término|Definición|
|----------|----------------|
|**"R"**|Abre para lectura. Si el archivo no existe o no se puede encontrar, se produce un error en la **llamada _fsopen.**|
|**"W"**|Abre un archivo vacío para escritura. Si el archivo especificado existe, se destruye su contenido.|
|**"A"**|Se abre para escribir al final del archivo (anexo); primero crea el archivo si no existe.|
|**"r+"**|Abre para lectura y escritura. (El archivo debe existir.)|
|**"w+"**|Abre un archivo vacío para lectura y escritura. Si el archivo especificado existe, se destruye su contenido.|
|**"a+"**|Se abre para leer y anexar; primero crea el archivo si no existe.|

Utilice los tipos **"w"** y **"w+"** con cuidado, ya que pueden destruir los archivos existentes.

Cuando se abre un archivo con el tipo de acceso **"a"** o **"a+",** todas las operaciones de escritura se producen al final del archivo. El puntero de archivo se puede cambiar de posición mediante [fseek](fseek-fseeki64.md) o [rebobinado](rewind.md), pero siempre se mueve de nuevo al final del archivo antes de que se lleve a cabo cualquier operación de escritura. Por lo tanto, los datos existentes no se pueden sobrescribir. Cuando se especifica el tipo de acceso **"r+"**, **"w+"** o **"a+",** se permiten tanto la lectura como la escritura (se dice que el archivo está abierto para la actualización). En cambio, si se cambia entre lectura y escritura, debe haber una operación intermedia [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md) o [rewind](rewind.md). La posición actual se puede especificar para la operación [fsetpos](fsetpos.md) o [fseek,](fseek-fseeki64.md) si lo desea. Además de los valores anteriores, se puede incluir uno de los siguientes caracteres en *modo* para especificar el modo de traducción para las nuevas líneas y para la administración de archivos.

|Término|Definición|
|----------|----------------|
|**T**|Abre un archivo en modo de texto (traducido). En este modo, las combinaciones de avance de línea de retorno de carro (CR-LF) se traducen en alimentaciones de línea única (LF) en la entrada y los caracteres LF se traducen a combinaciones CR-LF en la salida. Además, CTRL+Z se interpreta como carácter de final de archivo en la entrada. En los archivos abiertos para lectura o lectura/escritura, **_fsopen** comprueba si hay CTRL+Z al final del archivo y la elimina, si es posible. Esto se hace porque el uso de [fseek](fseek-fseeki64.md) y [ftell](ftell-ftelli64.md) para moverse dentro de un archivo que termina con CTRL+Z puede hacer que [fseek](fseek-fseeki64.md) se comporte incorrectamente cerca del final del archivo.|
|**B**|Abre un archivo en modo binario (sin traducir); las conversiones anteriores se suprimen.|
|**S**|Especifica que el almacenamiento en caché está optimizado para el acceso secuencial (pero no restringido a este) desde el disco.|
|**R**|Especifica que el almacenamiento en caché está optimizado para el acceso aleatorio (pero no restringido a este) desde el disco.|
|**T**|Especifica un archivo como temporal. Si es posible, no se vuelca en el disco.|
|**D**|Especifica un archivo como temporal. Se elimina cuando se cierra el puntero del último archivo.|

Si no se especifica **t** o **b** en *mode*, el modo de traducción está definido por la variable de modo predeterminado **_fmode**. Si **t** o **b** tiene como prefijo el argumento, se produce un error en la función y devuelve **NULL**. Para obtener una descripción de los modos de texto y binario, consulte [E/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

El argumento *shflag* es una expresión constante que consta de una de las siguientes constantes de manifiesto, definidas en Share.h.

|Término|Definición|
|----------|----------------|
|**_SH_COMPAT**|Establece el modo de compatibilidad para aplicaciones de 16 bits.|
|**_SH_DENYNO**|Permite el acceso de lectura y escritura.|
|**_SH_DENYRD**|Deniega el acceso de lectura al archivo.|
|**_SH_DENYRW**|Deniega el acceso de lectura y escritura al archivo.|
|**_SH_DENYWR**|Deniega el acceso de escritura al archivo.|

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfsopen**|**_fsopen**|**_fsopen**|**_wfsopen**|

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|Encabezados opcionales|
|--------------|---------------------|----------------------|
|**_fsopen**|\<stdio.h>|\<share.h><br /><br /> Para la constante de manifiesto para el parámetro *shflag.*|
|**_wfsopen**|\<stdio.h> o \<wchar.h>|\<share.h><br /><br /> Para la constante de manifiesto para el parámetro *shflag.*|

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

## <a name="see-also"></a>Consulte también

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
