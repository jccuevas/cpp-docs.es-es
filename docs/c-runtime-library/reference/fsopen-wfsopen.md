---
title: _fsopen, _wfsopen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs:
- C++
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
caps.latest.revision: 20
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: c53bdd4bdd5d6707e6da15def20b6375dcf6e0dd
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="fsopen-wfsopen"></a>_fsopen, _wfsopen
Abre un flujo con uso compartido de archivos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
  
#### <a name="parameters"></a>Parámetros  
 `filename`  
 Nombre del archivo que se va a abrir.  
  
 `mode`  
 Tipo de acceso permitido.  
  
 `shflag`  
 Tipo de uso compartido permitido.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada una de estas funciones devuelve un puntero al flujo. Un valor de puntero null indica un error. Si `filename` o `mode` es `NULL` o una cadena vacía, estas funciones invocan al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven `NULL` y establecen `errno` en `EINVAL`.  
  
 Para obtener más información sobre estos y otros códigos error, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 La función `_fsopen` abre el archivo especificado por `filename` como un flujo y lo prepara para una lectura o escritura compartida posterior, como establecen los argumentos `shflag` y el modo. `_wfsopen` es una versión con caracteres anchos de `_fsopen`; los argumentos `filename` y `mode` para `_wfsopen` son cadenas de caracteres anchos. Por lo demás, `_wfsopen` y `_fsopen` se comportan de forma idéntica.  
  
 La cadena de caracteres `mode` especifica el tipo de acceso solicitado para el archivo, como se muestra en la tabla siguiente.  
  
|Término|Definición|  
|----------|----------------|  
|`"r"`|Abre para lectura. Si el archivo no existe o no se encuentra, la llamada de `_fsopen` falla.|  
|`"w"`|Abre un archivo vacío para escritura. Si el archivo especificado existe, se destruye su contenido.|  
|`"a"`|Se abre para escribir al final del archivo (anexo); primero crea el archivo si no existe.|  
|`"r+"`|Abre para lectura y escritura. (El archivo debe existir.)|  
|`"w+"`|Abre un archivo vacío para lectura y escritura. Si el archivo especificado existe, se destruye su contenido.|  
|`"a+"`|Se abre para leer y anexar; primero crea el archivo si no existe.|  
  
 Use los tipos `"w"` y `"w+"` con cuidado, ya que podrían destruir archivos existentes.  
  
 Cuando un archivo se abre con el tipo de acceso `"a"` o `"a+"`, todas las operaciones de escritura se producen al final del archivo. El puntero de archivo se puede mover mediante `fseek` o `rewind`, pero se desplaza siempre al final del archivo antes de que se realice cualquier operación de escritura. Por consiguiente, los datos existentes no pueden sobrescribirse. Cuando se especifica el tipo de acceso `"r+"`, `"w+"` o `"a+"`, se permiten la lectura y la escritura (se dice que el archivo está abierto para actualización). En cambio, si se cambia entre lectura y escritura, debe haber una operación intermedia [fsetpos](../../c-runtime-library/reference/fsetpos.md), [fseek](../../c-runtime-library/reference/fseek-fseeki64.md) o [rewind](../../c-runtime-library/reference/rewind.md). Si se desea, se puede especificar la posición actual para la operación `fsetpos` o `fseek`. Además de los valores anteriores, uno de los caracteres siguientes se puede incluir en `mode` para especificar el modo de traducción de las nuevas líneas y de la administración de archivos.  
  
|Término|Definición|  
|----------|----------------|  
|`t`|Abre un archivo en modo de texto (traducido). En este modo, carro retorno-combinaciones de línea (CR-LF) se traducen en avances de una línea (LF) en la entrada y caracteres de LF se traducen en combinaciones de CR-LF en la salida. Además, CTRL+Z se interpreta como carácter de final de archivo en la entrada. En los archivos abiertos para lectura o lectura y escritura, `_fsopen` comprueba si hay un Ctrl+Z al final del archivo y lo quita, si es posible. Se hace así porque el uso de `fseek` y `ftell` para desplazarse por un archivo que finaliza con CTRL+Z puede hacer que `fseek` se comporte de forma incorrecta cerca del final del archivo.|  
|`b`|Abre un archivo en modo binario (sin traducir); las conversiones anteriores se suprimen.|  
|`S`|Especifica que el almacenamiento en caché está optimizado para el acceso secuencial (pero no restringido a este) desde el disco.|  
|`R`|Especifica que el almacenamiento en caché está optimizado para el acceso aleatorio (pero no restringido a este) desde el disco.|  
|`T`|Especifica un archivo como temporal. Si es posible, no se vuelca en el disco.|  
|`D`|Especifica un archivo como temporal. Se elimina cuando se cierra el puntero del último archivo.|  
  
 Si no se especifica `t` o `b` en `mode`, el modo de traducción está definido por la variable de modo predeterminado `_fmode`. Si se agrega `t` o `b` como prefijo al argumento, se produce un error en la función y devuelve `NULL`. Para obtener una descripción de los modos de texto y binario, consulte [E/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md).  
  
 El argumento `shflag` es una expresión constante compuesta por una de las constantes de manifiesto siguientes, que se definen en Share.h.  
  
|Término|Definición|  
|----------|----------------|  
|`_SH_COMPAT`|Establece el modo de compatibilidad para aplicaciones de 16 bits.|  
|`_SH_DENYNO`|Permite el acceso de lectura y escritura.|  
|`_SH_DENYRD`|Deniega el acceso de lectura al archivo.|  
|`_SH_DENYRW`|Deniega el acceso de lectura y escritura al archivo.|  
|`_SH_DENYWR`|Deniega el acceso de escritura al archivo.|  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tfsopen`|`_fsopen`|`_fsopen`|`_wfsopen`|  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|Encabezados opcionales|  
|--------------|---------------------|----------------------|  
|`_fsopen`|\<stdio.h>|\<share.h><br /><br /> Para la constante de manifiesto del parámetro `shflag`.|  
|`_wfsopen`|\<stdio.h> o \<wchar.h>|\<share.h><br /><br /> Para la constante de manifiesto del parámetro `shflag`.|  
  
## <a name="example"></a>Ejemplo  
  
```  
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
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fclose, _fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [_fdopen, _wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [_fileno](../../c-runtime-library/reference/fileno.md)   
 [fopen, _wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen, _wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_setmode](../../c-runtime-library/reference/setmode.md)   
 [_sopen, _wsopen](../../c-runtime-library/reference/sopen-wsopen.md)
