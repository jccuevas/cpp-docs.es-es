---
title: fopen_s, _wfopen_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _wfopen_s
- fopen_s
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
- fopen_s
- _tfopen_s
- _wfopen_s
dev_langs:
- C++
helpviewer_keywords:
- _wfopen_s function
- opening files, for file I/O
- _tfopen_s function
- tfopen_s function
- wfopen_s function
- fopen_s function
- Unicode [C++], creating files
- Unicode [C++], writing files
- files [C++], opening
- Unicode [C++], files
ms.assetid: c534857e-39ee-4a3f-bd26-dfe551ac96c3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 97221d04dcd93fbaa32a3562320d0c098fa001ae
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="fopens-wfopens"></a>fopen_s, _wfopen_s
Abre un archivo. Estas versiones de [fopen, _wfopen](../../c-runtime-library/reference/fopen-wfopen.md) incluyen mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t fopen_s(   
   FILE** pFile,  
   const char *filename,  
   const char *mode   
);  
errno_t _wfopen_s(  
   FILE** pFile,  
   const wchar_t *filename,  
   const wchar_t *mode   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [out] `pFile`  
 Puntero al puntero de archivo que recibirá el puntero al archivo abierto.  
  
 [in] `filename`  
 Nombre de archivo.  
  
 [in] `mode`  
 Tipo de acceso permitido.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error. Consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos códigos de error.  
  
### <a name="error-conditions"></a>Condiciones de error  
  
|`pFile`|`filename`|`mode`|Valor devuelto|Contenido de `pFile`|  
|-------------|----------------|------------|------------------|------------------------|  
|`NULL`|any|any|`EINVAL`|sin cambios|  
|any|`NULL`|any|`EINVAL`|sin cambios|  
|any|any|NULL|`EINVAL`|sin cambios|  
  
## <a name="remarks"></a>Comentarios  
 Los archivos abiertos por `fopen_s` y `_wfopen_s` no se pueden compartir. Si necesita que un archivo se pueda compartir, use [_fsopen,_wfsopen](../../c-runtime-library/reference/fsopen-wfsopen.md) con la constante de modo compartido adecuada (por ejemplo, `_SH_DENYNO` para el uso compartido de lectura y escritura).  
  
 La función `fopen_s` abre el archivo especificado por `filename`. `_wfopen_s` es una versión con caracteres anchos de `fopen_s`; los argumentos a `_wfopen_s` son cadenas de caracteres anchos. Por lo demás, `_wfopen_s` y `fopen_s` se comportan de forma idéntica.  
  
 `fopen_s` acepta las rutas válidas en el sistema de archivos en el momento de la ejecución; `fopen_s` acepta las rutas UNC y las rutas que requieren unidades de red asignadas siempre y cuando el sistema que ejecuta el código tenga acceso al recurso compartido o a la unidad asignada en el momento de la ejecución. Cuando se construyen las rutas de `fopen_s`, no asuma nada sobre la disponibilidad de unidades, rutas o recursos compartidos de red en el entorno de ejecución. Puede usar barras diagonales (/) o barras diagonales inversas (\\) como separadores de directorio en una ruta de acceso.  
  
 Estas funciones validan sus parámetros. Si `pFile`, `filename` o `mode` es un puntero nulo, estas funciones generan una excepción de parámetro no válido, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
 Compruebe siempre el valor devuelto para ver si la función se realizó correctamente antes de realizar cualquier otra operación en el archivo. Si se produce un error, se devuelve el código de error y se establece la variable global `errno`. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="unicode-support"></a>Compatibilidad con Unicode  
 `fopen_s` admite secuencias de archivo Unicode. Para abrir un archivo Unicode nuevo o existente, pase una marca de `ccs` que especifique la codificación deseada a `fopen_s`:  
  
 `fopen_s(&fp, "newfile.txt", "rw, ccs=`*Codificación*`");`  
  
 Valores permitidos de *codificación* son `UNICODE`, `UTF-8`, y `UTF-16LE`. Si no existe ningún valor se especifica para *codificación*, `fopen_s` usa la codificación ANSI.  
  
 Si el archivo ya existe y está abierto para lectura o para anexar, la marca de orden de bytes (BOM), si está presente en el archivo, determina la codificación. La codificación de BOM tiene prioridad sobre la codificación especificada por la marca de `ccs`. La codificación de `ccs` solo se usa cuando no hay BOM presente o el archivo es nuevo.  
  
> [!NOTE]
>  La detección de BOM solo se aplica a los archivos abiertos en modo Unicode (es decir, pasando el indicador de `ccs`).  
  
 En la tabla siguiente se resumen los modos de las distintas marcas de `ccs` que se especifican en `fopen_s` y de las marcas de orden de bytes en el archivo.  
  
### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Codificaciones utilizadas basadas en el indicador de ccs y BOM  
  
|Marca de`ccs` |Ninguna BOM (o archivo nuevo)|BOM: UTF-8|BOM: UTF-16|  
|----------------|----------------------------|-----------------|------------------|  
|`UNICODE`|`UTF-16LE`|`UTF-8`|`UTF-16LE`|  
|`UTF-8`|`UTF-8`|`UTF-8`|`UTF-16LE`|  
|`UTF-16LE`|`UTF-16LE`|`UTF-8`|`UTF-16LE`|  
  
 En los archivos que se abren para escribir en el modo Unicode se escribe una BOM automáticamente.  
  
 Si `mode` es "un, ccs =*codificación*", `fopen_s` primero intenta abrir el archivo con acceso de lectura y acceso de escritura. Si la operación se realiza correctamente, la función lee la BOM para determinar la codificación del archivo; si se produce un error, la función usa la codificación predeterminada del archivo. En cualquier caso, `fopen_s` abre de nuevo el archivo con acceso de solo escritura. (Es así solo en el modo `a`, no `a+`.)  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tfopen_s`|`fopen_s`|`fopen_s`|`_wfopen_s`|  
  
 La cadena de caracteres `mode` especifica el tipo de acceso solicitado para el archivo, como se muestra a continuación:  
  
 `"r"`  
 Abre para lectura. Si el archivo no existe o no se encuentra, la llamada de `fopen_s` falla.  
  
 `"w"`  
 Abre un archivo vacío para escritura. Si el archivo existe, se destruye su contenido.  
  
 `"a"`  
 Abre para escritura al final del archivo (anexo) sin eliminar el marcador de fin de archivo (EOF) antes de escribir nuevos datos en el archivo. Crea el archivo si no existe.  
  
 `"r+"`  
 Abre para lectura y escritura. (El archivo debe existir.)  
  
 `"w+"`  
 Abre un archivo vacío para lectura y escritura. Si el archivo existe, se destruye su contenido.  
  
 `"a+"`  
 Se abre para lectura y anexado. La operación de anexo conlleva la eliminación del marcador EOF antes de escribir nuevos datos en el archivo. El marcador EOF se restablece una vez que finaliza la escritura. Crea el archivo si no existe.  
  
 Cuando un archivo se abre mediante el tipo de acceso de `"a"` o de `"a+"`, todas las operaciones de escritura aparecen al final del archivo. El puntero de archivo se puede cambiar de ubicación mediante `fseek` o `rewind`, pero siempre se vuelve a poner al final del archivo antes de que se realice cualquier operación de escritura, de forma los datos existentes no se puedan sobrescribir.  
  
 El modo `"a"` no quita el marcador EOF antes de que se anexe contenido al archivo. Una vez realizado el anexado, el comando TYPE de MS-DOS solo muestra los datos hasta el marcador EOF original, y no los datos anexados al archivo. El modo `"a+"` quita el marcador EOF antes de que se anexe contenido al archivo. Después de anexar, el comando TYPE de MS-DOS muestra todos los datos del archivo. El modo `"a+"` se requiere para anexar a un archivo de streaming terminado mediante el marcador EOF CTRL+Z.  
  
 Cuando el `"r+"`, `"w+",` o `"a+"` se especifica el tipo de acceso, se permiten la lectura y escritura. (Se dice que el archivo se abierto para “actualizar”). Sin embargo, cuando cambie de lectura a la escritura, la operación de entrada debe encontrar un marcador EOF. Si no hay ningún EOF, debe usar una llamada intermedia a una función de posición del archivo. Las funciones de posición de archivo son `fsetpos`, `fseek` y `rewind`. Cuando cambie de escritura a lectura, debe usar una llamada intermedia a `fflush` o una función de posición del archivo.  
  
 Además de los valores anteriores, los caracteres siguientes se pueden incluir en `mode` para especificar el modo de traducción de los caracteres de nueva línea:  
  
 `t`  
 Abra en modo de texto (traducido). En este modo, CTRL+Z se interpreta como un carácter de final de archivo en la entrada. En los archivos abiertos para lectura/escritura mediante `"a+"`, `fopen_s` comprueba un CTRL+Z al final del archivo y lo elimina, si es posible. Se hace así porque el uso de `fseek` y `ftell` para desplazarse por un archivo que finaliza con CTRL+Z puede hacer que `fseek` se comporte de forma incorrecta cerca del final del archivo.  
  
 Además, en modo de texto, combinaciones de avance de línea de retorno de carro se traducen en avances de línea únicos en la entrada y caracteres de avance de línea se traducen en combinaciones de avance de línea de retorno de carro en la salida. Cuando una función de E/S de flujo Unicode funciona en el modo de texto (valor predeterminado), se asume que el flujo de origen o de destino son una secuencia de caracteres multibyte. Por consiguiente, las funciones de entrada y flujo de Unicode convierten los caracteres multibyte en caracteres anchos (como si por una llamada a la función de `mbtowc` ). Por la misma razón, las funciones de salida y flujo Unicode convierten los caracteres anchos en caracteres multibyte (como si se realizara una llamada a la función de `wctomb` ).  
  
 `b`  
 Abra en modo binario (sin traducir); las traducciones que implican los caracteres de retorno de carro y avance de línea se suprimen.  
  
 Si no se especifica `t` o `b` en `mode`, el modo de traducción predeterminado está definido por la variable global [_fmode](../../c-runtime-library/fmode.md). Si se agrega `t` o `b` como prefijo al argumento, se produce un error en la función y devuelve `NULL`.  
  
 Para obtener más información sobre el uso de los modos de texto y binario en E/S de secuencias Unicode y multibyte, consulte [E/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md) y [E/S de secuencias Unicode en los modos binario y de texto](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).  
  
 `c`  
 Habilite la marca de confirmación para el `filename` asociado para que el contenido del búfer del archivo se escriba directamente en disco si se llama a `fflush` o a `_flushall` .  
  
 `n`  
 Restaure la marca de confirmación para el `filename` asociado a "no-commit". Este es el valor predeterminado. También invalida la marca global de confirmación si vincula el programa a COMMODE.OBJ. El valor predeterminado de la marca de confirmación global es "no-commit", a menos que vincule explícitamente el programa a COMMODE.OBJ (vea [Link Options](../../c-runtime-library/link-options.md)).  
  
 `N`  
 Especifica que el archivo no se hereda mediante procesos secundarios.  
  
 `S`  
 Especifica que el almacenamiento en caché está optimizado para el acceso secuencial (pero no restringido a este) desde el disco.  
  
 `R`  
 Especifica que el almacenamiento en caché está optimizado para el acceso aleatorio (pero no restringido a este) desde el disco.  
  
 `T`  
 Especifica un archivo como temporal. Si es posible, no se vuelca en el disco.  
  
 `D`  
 Especifica un archivo como temporal. Se elimina cuando se cierra el puntero del último archivo.  
  
 `ccs=ENCODING`  
 Especifique el juego de caracteres codificados que se debe usar (UTF-8, UTF-16LE y UNICODE) para este archivo. No lo especifique si desea usar la codificación ANSI.  
  
 Los caracteres válidos para la cadena `mode` que se usa en `fopen_s` y `_fdopen` corresponden a los argumentos `oflag` que se usan en [_open](../../c-runtime-library/reference/open-wopen.md) y [_sopen](../../c-runtime-library/reference/sopen-wsopen.md), de la manera siguiente.  
  
|Caracteres en cadena de modo|Valor `oflag` equivalente para `_open`/`_sopen`|  
|-------------------------------|----------------------------------------------------|  
|`a`|`_O_WRONLY &#124; _O_APPEND` (normalmente `_O_WRONLY &#124; _O_CREAT &#124; _O_APPEND`)|  
|`a+`|`_O_RDWR &#124; _O_APPEND` (normalmente `_O_RDWR &#124; _O_APPEND &#124; _O_CREAT` )|  
|`r`|`_O_RDONLY`|  
|`r+`|`_O_RDWR`|  
|`w`|`_O_WRONLY` (normalmente `_O_WRONLY &#124; _O_CREAT &#124; _O_TRUNC`)|  
|`w+`|`_O_RDWR` (normalmente `_O_RDWR &#124; _O_CREAT &#124; _O_TRUNC`)|  
|`b`|`_O_BINARY`|  
|`t`|`_O_TEXT`|  
|`c`|Ninguna|  
|`n`|Ninguna|  
|`S`|`_O_SEQUENTIAL`|  
|`R`|`_O_RANDOM`|  
|`T`|`_O_SHORTLIVED`|  
|`D`|`_O_TEMPORARY`|  
|`ccs=UNICODE`|`_O_WTEXT`|  
|`ccs=UTF-8`|`_O_UTF8`|  
|`ccs=UTF-16LE`|`_O_UTF16`|  
  
 Si usa el modo de `rb`, no necesita especificar el puerto del código, y si va a leer gran parte del archivo y el rendimiento de la red le da igual, también puede usar los archivos de Win32 asignados a la memoria.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`fopen_s`|\<stdio.h>|  
|`_wfopen_s`|\<stdio.h> o \<wchar.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
 Las opciones `c`, `n` y `t` `mode` son extensiones de Microsoft para `fopen_s` y `_fdopen` y no deben usarse si se quiere usar la portabilidad ANSI.  
  
## <a name="example"></a>Ejemplo  
  
```C  
// crt_fopen_s.c  
// This program opens two files. It uses  
// fclose to close the first file and  
// _fcloseall to close all remaining files.  
  
#include <stdio.h>  
  
FILE *stream, *stream2;  
  
int main( void )  
{  
   errno_t err;  
  
   // Open for read (will fail if file "crt_fopen_s.c" does not exist)  
   err  = fopen_s( &stream, "crt_fopen_s.c", "r" );  
   if( err == 0 )  
   {  
      printf( "The file 'crt_fopen_s.c' was opened\n" );  
   }  
   else  
   {  
      printf( "The file 'crt_fopen_s.c' was not opened\n" );  
   }  
  
   // Open for write   
   err = fopen_s( &stream2, "data2", "w+" );  
   if( err == 0 )  
   {  
      printf( "The file 'data2' was opened\n" );  
   }  
   else  
   {  
      printf( "The file 'data2' was not opened\n" );  
   }  
  
   // Close stream if it is not NULL   
   if( stream )  
   {  
      err = fclose( stream );  
      if ( err == 0 )  
      {  
         printf( "The file 'crt_fopen_s.c' was closed\n" );  
      }  
      else  
      {  
         printf( "The file 'crt_fopen_s.c' was not closed\n" );  
      }  
   }  
  
   // All other files are closed:  
   int numclosed = _fcloseall( );  
   printf( "Number of files closed by _fcloseall: %u\n", numclosed );  
}  
```  
  
```Output  
The file 'crt_fopen_s.c' was opened  
The file 'data2' was opened  
Number of files closed by _fcloseall: 1  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fclose, _fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [_fdopen, _wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [_fileno](../../c-runtime-library/reference/fileno.md)   
 [freopen, _wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_setmode](../../c-runtime-library/reference/setmode.md)