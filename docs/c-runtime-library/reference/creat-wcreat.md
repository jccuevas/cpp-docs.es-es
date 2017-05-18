---
title: _creat, _wcreat | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _creat
- _wcreat
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
- wcreat
- _wcreat
- _creat
- tcreat
- _tcreat
dev_langs:
- C++
helpviewer_keywords:
- wcreat function
- _wcreat function
- files [C++], creating
- _creat function
- tcreat function
- creat function
- _tcreat function
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: f034e2b80cc1bd3e7b5fc4578a6f5e77a060593c
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="creat-wcreat"></a>_creat, _wcreat
Crear un archivo nuevo. `_creat` y `_wcreat` han quedado en desuso; use [_sopen_s, _wsopen_s](../../c-runtime-library/reference/sopen-s-wsopen-s.md) en su lugar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _creat(   
   const char *filename,  
   int pmode   
);  
int _wcreat(   
   const wchar_t *filename,  
   int pmode   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `filename`  
 Nombre del nuevo archivo.  
  
 `pmode`  
 Configuración de permisos.  
  
## <a name="return-value"></a>Valor devuelto  
 Estas funciones, si se ejecutan correctamente, devuelven un descriptor de archivo para el archivo creado. De lo contrario, las funciones devuelven -1 y establecen `errno` tal como se muestra en la tabla siguiente.  
  
|Valor de `errno`|Descripción|  
|---------------------|-----------------|  
|`EACCES`|`filename` especifica un archivo existente de solo lectura o un directorio en lugar de un archivo.|  
|`EMFILE`|No hay más descriptores de archivo disponibles.|  
|`ENOENT`|No se pudo encontrar el archivo especificado.|  
  
 Si `filename` es NULL, estas funciones invocan al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven -1.  
  
 Para obtener más información sobre estos y otros códigos de retorno, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 La función `_creat` crea otro archivo o abre y trunca uno existente. `_wcreat` es una versión con caracteres anchos de `_creat`; el argumento `filename` para `_wcreat` es una cadena de caracteres anchos. Por lo demás, `_wcreat` y `_creat` se comportan de forma idéntica.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcreat`|`_creat`|`_creat`|`_wcreat`|  
  
 Si el archivo especificado con `filename` no existe, se crea otro archivo con la configuración de permisos especificada y se abre para escritura. Si el archivo ya existe y su configuración de permisos permite escritura, `_creat` trunca el archivo en la longitud 0, lo que destruye el contenido anterior y lo abre para escritura. La configuración de permisos, `pmode`, solo se aplica a archivos recién creados. El nuevo archivo recibe la configuración de permisos especificada cuando se cierra por primera vez. La expresión de entero `pmode` contiene una o ambas constantes del manifiesto, `_S_IWRITE` y `_S_IREAD`, que se definen en SYS\Stat.h. Cuando ambas constantes se especifican, se unen con el operador `OR` bit a bit ( **&#124;**). El parámetro `pmode` se establece en uno de los valores siguientes.  
  
|Valor|Definición|  
|-----------|----------------|  
|`_S_IWRITE`|Escritura permitida.|  
|`_S_IREAD`|Lectura permitida.|  
|`_S_IREAD &#124; _S_IWRITE`|Lectura y escritura permitidas.|  
  
 Si no se ha concedido el permiso de escritura, el archivo será de solo lectura. Todos los archivos son siempre legibles; es decir, no es posible conceder permisos de solo escritura. Por consiguiente, los modos `_S_IWRITE` y `_S_IREAD | _S_IWRITE` son equivalentes. Los archivos abiertos con `_creat` siempre se abren en modo de compatibilidad (consulte [_sopen](../../c-runtime-library/reference/sopen-wsopen.md)) con `_SH_DENYNO`.  
  
 `_creat` aplica la máscara de permisos de archivo actual a `pmode` antes de que se establezcan los permisos (consulte [_umask](../../c-runtime-library/reference/umask.md)). `_creat` sirve principalmente para la compatibilidad con bibliotecas anteriores. Una llamada a `_open` con `_O_CREAT` y `_O_TRUNC` en el parámetro `oflag` es equivalente a `_creat` y es preferible en caso de nuevo código.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|-------------|---------------------|---------------------|  
|`_creat`|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|  
|`_wcreat`|\<io.h> o \<wchar.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_creat.c  
// compile with: /W3  
// This program uses _creat to create  
// the file (or truncate the existing file)  
// named data and open it for writing.  
  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <io.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int fh;  
  
   fh = _creat( "data", _S_IREAD | _S_IWRITE ); // C4996  
   // Note: _creat is deprecated; use _sopen_s instead  
   if( fh == -1 )  
      perror( "Couldn't create data file" );  
   else  
   {  
      printf( "Created data file.\n" );  
      _close( fh );  
   }  
}  
```  
  
```Output  
Created data file.  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)   
 [_chmod, _wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_chsize](../../c-runtime-library/reference/chsize.md)   
 [_close](../../c-runtime-library/reference/close.md)   
 [_dup, _dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_sopen, _wsopen](../../c-runtime-library/reference/sopen-wsopen.md)   
 [_umask](../../c-runtime-library/reference/umask.md)
