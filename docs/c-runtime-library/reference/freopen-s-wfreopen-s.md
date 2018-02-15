---
title: freopen_s, _wfreopen_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _wfreopen_s
- freopen_s
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
- freopen_s
- _tfreopen_s
- _wfreopen_s
dev_langs:
- C++
helpviewer_keywords:
- _tfreopen_s function
- _wfreopen_s function
- file pointers [C++], reassigning
- tfreopen_s function
- wfreopen_s function
- freopen_s function
ms.assetid: ad25a4da-6ad4-476b-a86d-660b221ca84d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a62165fee7ed54a7eeadf5f381945936bb441908
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="freopens-wfreopens"></a>freopen_s, _wfreopen_s
Reasigna un puntero de archivo. Estas versiones de [freopen, _wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md) incluyen mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t freopen(   
   FILE** pFile,  
   const char *path,  
   const char *mode,  
   FILE *stream   
);  
errno_t _wfreopen(   
   FILE** pFile,  
   const wchar_t *path,  
   const wchar_t *mode,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [out] `pFile`  
 Puntero al puntero de archivo que la llamada va a proporcionar.  
  
 [in] `path`  
 Ruta de acceso del nuevo archivo.  
  
 [in] `mode`  
 Tipo de acceso permitido.  
  
 [in] `stream`  
 Puntero a la estructura `FILE`.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada una de estas funciones devuelve un código de error. Si se produce un error, el archivo original se cierra.  
  
## <a name="remarks"></a>Comentarios  
 La función `freopen_s` cierra el archivo asociado actualmente a `stream` y reasigna `stream` al archivo especificado por `path.`; `_wfreopen_s` es una versión con caracteres anchos de `_freopen_s`; los argumentos `path` y `mode` para `_wfreopen_s` son cadenas de caracteres anchos. Por lo demás, `_wfreopen_s` y `_freopen_s` se comportan de forma idéntica.  
  
 Si `pFile`, `path`, `mode` o `stream` son `NULL`, o si `path` es una cadena vacía, estas funciones invocan al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tfreopen_s`|`freopen_s`|`freopen_s`|`_wfreopen_s`|  
  
 `freopen_s` se suele usar para redirigir los archivos ya abiertos `stdin`, `stdout` y `stderr` a los archivos especificados por el usuario. El nuevo archivo asociado con `stream` se abre con `mode`, que es una cadena de caracteres que especifica el tipo de acceso solicitado para el archivo, como se indica a continuación:  
  
 `"r"`  
 Abre para lectura. Si el archivo no existe o no se encuentra, la llamada de `freopen_s` falla.  
  
 `"w"`  
 Abre un archivo vacío para escritura. Si el archivo especificado existe, se destruye su contenido.  
  
 `"a"`  
 Abre para escribir al final del archivo (anexar) sin quitar el marcador EOF antes de escribir nuevos datos en archivo; primero crea el archivo si no existe.  
  
 `"r+"`  
 Abre para lectura y escritura. (El archivo debe existir.)  
  
 `"w+"`  
 Abre un archivo vacío para lectura y escritura. Si el archivo especificado existe, se destruye su contenido.  
  
 `"a+"`  
 Abre para leer y anexar. La operación para anexar incluye la eliminación del marcador EOF antes de escribir los nuevos datos en el archivo; el marcador se restablece cuando se finaliza la escritura. Primero crea el archivo si no existe.  
  
 Use los tipos `"w"` y `"w+"` con cuidado, ya que podrían destruir archivos existentes.  
  
 Si se abre un archivo con el tipo de acceso `"a"` o `"a+"`, todas las operaciones de escritura se realizan en el final del archivo. Si bien el puntero de archivo se puede mover mediante `fseek` o `rewind`, siempre se desplaza al final del archivo antes de que se realice cualquier operación de escritura. Por consiguiente, los datos existentes no pueden sobrescribirse.  
  
 El modo `"a"` no quita el marcador EOF antes de que se anexe contenido al archivo. Una vez realizado el anexado, el comando TYPE de MS-DOS solo muestra los datos hasta el marcador EOF original, y no los datos anexados al archivo. El modo `"a+"` quita el marcador EOF antes de que se anexe contenido al archivo. Después de anexar, el comando TYPE de MS-DOS muestra todos los datos del archivo. El modo `"a+"` se requiere para anexar a un archivo de streaming terminado con el marcador EOF CTRL+Z.  
  
 Cuando el `"r+"`, `"w+",` o `"a+"` se especifica el tipo de acceso, se permiten la lectura y escritura (se dice que el archivo esté abierto para "actualización"). En cambio, si se cambia entre lectura y escritura, debe haber una operación intermedia [fsetpos](../../c-runtime-library/reference/fsetpos.md), [fseek](../../c-runtime-library/reference/fseek-fseeki64.md) o [rewind](../../c-runtime-library/reference/rewind.md). Si se desea, se puede especificar la posición actual para la operación `fsetpos` o `fseek`. Además de los valores anteriores, uno de los caracteres siguientes se puede incluir en la cadena de `mode` para especificar el modo de traducción para las nuevas líneas.  
  
 `t`  
 Abra en texto (traducido) modo; combinaciones de retorno y avance de línea (CR-LF) de carro se convierten en caracteres de solo avance de línea (LF) en la entrada; Caracteres de LF se traducen en combinaciones de CR-LF en la salida. Además, CTRL+Z se interpreta como carácter de final de archivo en la entrada. En archivos abiertos para lectura, o para escritura y lectura, con `"a+"`, la biblioteca en tiempo de ejecución comprueba si hay un CTRL+Z al final del archivo y lo quita, si es posible. Se hace así porque el uso de `fseek` y `ftell` para desplazarse por un archivo puede hacer que `fseek` se comporte de forma incorrecta cerca del final del archivo. La opción `t` es una extensión de Microsoft que no se debe usar si se desea disponer de portabilidad de ANSI.  
  
 `b`  
 Abrir en modo binario (sin traducir); las conversiones anteriores se suprimen.  
  
 Si no se especifica `t` o `b` en `mode`, el modo de traducción predeterminado está definido por la variable global [_fmode](../../c-runtime-library/fmode.md). Si se agrega `t` o `b` como prefijo al argumento, se produce un error en la función y devuelve `NULL`.  
  
 Para obtener una descripción de los modos de texto y binario, consulte [E/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`freopen_s`|\<stdio.h>|  
|`_wfreopen_s`|\<stdio.h> o \<wchar.h>|  
  
 La consola no se admite en aplicaciones de la plataforma Universal de Windows (UWP). Los identificadores de secuencia estándar que están asociados a la consola:`stdin`, `stdout`, y `stderr`, se deben redirigir antes funciones de tiempo de ejecución de C puedan usarlos en las aplicaciones UWP. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_freopen_s.c  
// This program reassigns stderr to the file  
// named FREOPEN.OUT and writes a line to that file.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
FILE *stream;  
  
int main( void )  
{  
   errno_t err;  
   // Reassign "stderr" to "freopen.out":   
   err = freopen_s( &stream, "freopen.out", "w", stderr );  
  
   if( err != 0 )  
      fprintf( stdout, "error on freopen\n" );  
   else  
   {  
      fprintf( stdout, "successfully reassigned\n" ); fflush( stdout );  
      fprintf( stream, "This will go to the file 'freopen.out'\n" );  
      fclose( stream );  
   }  
   system( "type freopen.out" );  
}  
```  
  
```Output  
successfully reassigned  
This will go to the file 'freopen.out'  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [freopen, _wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)   
 [fclose, _fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [_fdopen, _wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [_fileno](../../c-runtime-library/reference/fileno.md)   
 [fopen, _wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_setmode](../../c-runtime-library/reference/setmode.md)