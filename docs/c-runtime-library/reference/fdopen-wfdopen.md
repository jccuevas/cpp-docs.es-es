---
title: _fdopen, _wfdopen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fdopen
- _wfdopen
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
apitype: DLLExport
f1_keywords:
- _tfdopen
- _fdopen
- _wfdopen
- wfdopen
- tfdopen
dev_langs:
- C++
helpviewer_keywords:
- wfdopen function
- _fdopen function
- _wfdopen function
- tfdopen function
- fdopen function
- _tfdopen function
- streams, associating with files
ms.assetid: 262757ff-1e09-4472-a5b6-4325fc28f971
caps.latest.revision: 23
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
ms.openlocfilehash: 3efc15f9d9fa6544ad7af2c3809ee6562b7f36e0
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="fdopen-wfdopen"></a>_fdopen, _wfdopen
Asocia un flujo a un archivo que se abrió previamente para E/S de bajo nivel.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
FILE *_fdopen(    
   int fd,  
   const char *mode   
);  
FILE *_wfdopen(   
   int fd,  
   const wchar_t *mode   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fd`  
 Descriptor del archivo abierto.  
  
 `mode`  
 Tipo de acceso a archivos.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada una de estas funciones devuelve un puntero al flujo abierto. Un valor de puntero null indica un error. Si se produce un error, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EBADF`, que indica un descriptor de archivo incorrecto, o en `EINVAL`, que indica que `mode` era un puntero nulo.  
  
 Para obtener más información sobre estos y otros códigos error, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 La función `_fdopen` asocia un flujo de E/S al archivo identificado por `fd`, lo que permite almacenar en búfer y dar formato a un archivo que está abierto para E/S de bajo nivel. `_wfdopen` es una versión con caracteres anchos de `_fdopen`; el argumento `mode` para `_wfdopen` es una cadena de caracteres anchos. De lo contrario, `_wfdopen` y `_fdopen` se comportan de forma idéntica.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tfdopen`|`_fdopen`|`_fdopen`|`_wfdopen`|  
  
 La cadena de caracteres `mode` especifica el tipo de archivo y de acceso a archivos.  
  
 La cadena de caracteres `mode` especifica el tipo de acceso solicitado para el archivo, como se muestra en la tabla siguiente.  
  
 `"r"`  
 Abre para lectura. Si el archivo no existe o no se encuentra, la llamada de `fopen` falla.  
  
 `"w"`  
 Abre un archivo vacío para escritura. Si el archivo especificado existe, se destruye su contenido.  
  
 `"a"`  
 Abre para escritura, al final del archivo (anexo). Crea el archivo si no existe.  
  
 `"r+"`  
 Abre para lectura y escritura. (El archivo debe existir.)  
  
 `"w+"`  
 Abre un archivo vacío para lectura y escritura. Si el archivo especificado existe, se destruye su contenido.  
  
 `"a+"`  
 Se abre para lectura y anexado. Crea el archivo si no existe.  
  
 Cuando un archivo se abre con el tipo de acceso de `"a"` o de `"a+"`, todas las operaciones de escritura aparecen al final del archivo. El puntero de archivo se puede mover mediante `fseek` o `rewind`, pero se desplaza siempre al final del archivo antes de que se realice cualquier operación de escritura. Por consiguiente, los datos existentes no pueden sobrescribirse. Cuando se especifica el tipo de acceso `"r+"`, `"w+"` o `"a+"`, se permiten la lectura y la escritura (el archivo está abierto para "actualización"). Sin embargo, si se cambia entre lectura y escritura, debe haber una operación intermedia `fflush`, `fsetpos`, `fseek` o `rewind`. Puede especificar la posición actual para la operación `fsetpos` o `fseek`, si lo desea.  
  
 Además de los valores anteriores, también se pueden incluir los caracteres siguientes en `mode` para especificar el modo de traducción de los caracteres de nueva línea.  
  
 `t`  
 Abra en modo de texto (traducido). En este modo, las combinaciones de retorno de carro-avance de línea (CR-LF) se convierten en avances de una línea (LF) en la entrada, y los caracteres de LF se traducen en combinaciones de CR-LF en la salida. Además, Ctrl+Z se interpreta como carácter de final de archivo en la entrada. En los archivos abiertos para lectura/escritura, `fopen` comprueba un Ctrl+Z al final del archivo y lo elimina, si es posible. Esto se hace porque si se usan las funciones `fseek` y `ftell` para desplazarse por un archivo que finaliza con Ctrl+Z es posible que `fseek` se comporte de forma incorrecta cerca del final del archivo.  
  
 `b`  
 Abre en modo binario (sin traducir). Las traducciones del modo `t` se suprimen.  
  
 `c`  
 Habilite la marca de confirmación para el `filename` asociado para que el contenido del búfer del archivo se escriba directamente en disco si se llama a `fflush` o a `_flushall` .  
  
 `n`  
 Restaure la marca de confirmación para el `filename` asociado a "no-commit". Este es el valor predeterminado. También invalida la marca global de confirmación si vincula el programa a Commode.obj. El valor predeterminado de la marca global de confirmación es "no-commit" a menos que explícitamente vincule el programa a Commode.obj.  
  
 Las opciones `t`, `c` y `n` `mode` son extensiones de Microsoft para `fopen` y `_fdopen`. No las use si desea conservar la portabilidad ANSI.  
  
 Si no se especifica `t` o `b` en `mode`, el modo de traducción predeterminado está definido por la variable global [_fmode](../../c-runtime-library/fmode.md). Si se agrega `t` o `b` como prefijo al argumento, se produce un error en la función y devuelve `NULL`. Para obtener una descripción de los modos de texto y binario, consulte [E/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md).  
  
 Los caracteres válidos para la cadena `mode` que se usa en `fopen` y `_fdopen` corresponden a los argumentos `oflag` que se usan en [_open](../../c-runtime-library/reference/open-wopen.md) y [_sopen](../../c-runtime-library/reference/sopen-wsopen.md), de la manera siguiente.  
  
|Caracteres de la cadena `mode`|Valor `oflag` equivalente para `_open`/`_sopen`|  
|---------------------------------|---------------------------------------------------|  
|`a`|`_O_WRONLY &#124; _O_APPEND`(normalmente `_O_WRONLY &#124; _O_CREAT &#124; _O_APPEND`)|  
|`a+`|`_O_RDWR &#124; _O_APPEND` (normalmente `_O_RDWR &#124; _O_APPEND &#124; _O_CREAT` )|  
|`r`|`_O_RDONLY`|  
|`r+`|`_O_RDWR`|  
|`w`|`_O_WRONLY`(normalmente `_O_WRONLY &#124; _O_CREAT &#124; _O_TRUNC`)|  
|`w+`|`_O_RDWR`(normalmente `_O_RDWR &#124; _O_CREAT &#124; _O_TRUNC`)|  
|`b`|`_O_BINARY`|  
|`t`|`_O_TEXT`|  
|`c`|Ninguna|  
|`n`|Ninguna|  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`_fdopen`|\<stdio.h>|  
|`_wfdopen`|\<stdio.h> o \<wchar.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
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
  
## <a name="input-crtfdopentxt"></a>Entrada: crt_fdopen.txt  
  
```  
Line one  
Line two  
```  
  
### <a name="output"></a>Salida  
  
```  
Lines in file: 2  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [_dup, _dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [fclose, _fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fopen, _wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen, _wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)
