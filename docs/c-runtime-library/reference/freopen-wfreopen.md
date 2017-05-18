---
title: freopen, _wfreopen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- freopen
- _wfreopen
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
- _wfreopen
- _tfreopen
- freopen
dev_langs:
- C++
helpviewer_keywords:
- _wfreopen function
- file pointers [C++], reassigning
- _tfreopen function
- freopen function
- tfreopen function
- wfreopen function
ms.assetid: de4b73f8-1043-4d62-98ee-30d2022da885
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 47b45dd9e2ad07032529652021172ea64b84d652
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="freopen-wfreopen"></a>freopen, _wfreopen
Reasigna un puntero de archivo. Hay disponibles versiones más seguras de estas funciones; consulte [freopen_s, _wfreopen_s](../../c-runtime-library/reference/freopen-s-wfreopen-s.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
FILE *freopen(   
   const char *path,  
   const char *mode,  
   FILE *stream   
);  
FILE *_wfreopen(   
   const wchar_t *path,  
   const wchar_t *mode,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `path`  
 Ruta de acceso del nuevo archivo.  
  
 `mode`  
 Tipo de acceso permitido.  
  
 `stream`  
 Puntero a la estructura `FILE`.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada una de estas funciones devuelve un puntero al archivo que se acaba de abrir. Si se produce un error, el archivo original se cierra y la función devuelve un valor de puntero `NULL`. Si `path`, `mode` o `stream` es un puntero nulo, o si `filename` es una cadena vacía, estas funciones invocan al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven `NULL`.  
  
 Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.  
  
## <a name="remarks"></a>Comentarios  
 Existen versiones más seguras de estas funciones, consulte [freopen_s, _wfreopen_s](../../c-runtime-library/reference/freopen-s-wfreopen-s.md).  
  
 El `freopen` función cierra el archivo asociado actualmente a `stream` y reasigna `stream` en el archivo especificado por `path`. `_wfreopen` es una versión con caracteres anchos de `_freopen`; los argumentos `path` y `mode` para `_wfreopen` son cadenas de caracteres anchos. Por lo demás, `_wfreopen` y `_freopen` se comportan de forma idéntica.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tfreopen`|`freopen`|`freopen`|`_wfreopen`|  
  
 `freopen` se suele usar para redirigir los archivos ya abiertos `stdin`, `stdout` y `stderr` a los archivos especificados por el usuario. El nuevo archivo asociado con `stream` se abre con `mode`, que es una cadena de caracteres que especifica el tipo de acceso solicitado para el archivo, como se indica a continuación:  
  
 `"r"`  
 Abre para lectura. Si el archivo no existe o no se encuentra, la llamada de `freopen` falla.  
  
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
  
 Cuando se especifica el tipo de acceso `"r+"`, `"w+"` o `"a+"`, se permiten la lectura y la escritura (el archivo está abierto para "actualización"). En cambio, si se cambia entre lectura y escritura, debe haber una operación intermedia [fsetpos](../../c-runtime-library/reference/fsetpos.md), [fseek](../../c-runtime-library/reference/fseek-fseeki64.md) o [rewind](../../c-runtime-library/reference/rewind.md). Si se desea, se puede especificar la posición actual para la operación `fsetpos` o `fseek`. Además de los valores anteriores, uno de los caracteres siguientes se puede incluir en la cadena de `mode` para especificar el modo de traducción para las nuevas líneas.  
  
 `t`  
 Abra en texto (traducido) modo; combinaciones de retorno y avance de línea (CR-LF) de carro se convierten en caracteres de solo avance de línea (LF) en la entrada; Caracteres de LF se traducen en combinaciones de CR-LF en la salida. Además, CTRL+Z se interpreta como carácter de final de archivo en la entrada. En archivos abiertos para lectura, o para escritura y lectura, con `"a+"`, la biblioteca en tiempo de ejecución comprueba si hay un CTRL+Z al final del archivo y lo quita, si es posible. Se hace así porque el uso de `fseek` y `ftell` para desplazarse por un archivo puede hacer que `fseek` se comporte de forma incorrecta cerca del final del archivo. La opción `t` es una extensión de Microsoft que no se debe usar si se desea disponer de portabilidad de ANSI.  
  
 `b`  
 Abrir en modo binario (sin traducir); las conversiones anteriores se suprimen.  
  
 Si no se especifica `t` o `b` en `mode`, el modo de traducción predeterminado está definido por la variable global [_fmode](../../c-runtime-library/fmode.md). Si se agrega `t` o `b` como prefijo al argumento, se produce un error en la función y devuelve `NULL`.  
  
 Para obtener una descripción de los modos de texto y binario, consulte [E/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`freopen`|\<stdio.h>|  
|`_wfreopen`|\<stdio.h> o \<wchar.h>|  
  
 La consola no se admite en las aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]. Se deben redirigir los identificadores estándar de flujo que están asociados a la consola, `stdin`, `stdout` y `stderr`, antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]. Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_freopen.c  
// compile with: /W3  
// This program reassigns stderr to the file  
// named FREOPEN.OUT and writes a line to that file.  
#include <stdio.h>  
#include <stdlib.h>  
  
FILE *stream;  
  
int main( void )  
{  
   // Reassign "stderr" to "freopen.out":   
   stream = freopen( "freopen.out", "w", stderr ); // C4996  
   // Note: freopen is deprecated; consider using freopen_s instead  
  
   if( stream == NULL )  
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
 [fclose, _fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [_fdopen, _wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [_fileno](../../c-runtime-library/reference/fileno.md)   
 [fopen, _wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_setmode](../../c-runtime-library/reference/setmode.md)
