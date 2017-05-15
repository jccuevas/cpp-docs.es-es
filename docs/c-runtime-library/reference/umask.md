---
title: _umask | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _umask
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _umask
dev_langs:
- C++
helpviewer_keywords:
- masks, file-permission-setting
- _umask function
- masks
- umask function
- file permissions [C++]
- files [C++], permission settings for
ms.assetid: 5e9a13ba-5321-4536-8721-6afb6f4c8483
caps.latest.revision: 21
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
ms.openlocfilehash: f2ad9c75caa5f3816ab4791dc4e67cb7937bfad4
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="umask"></a>_umask
Establece la máscara de permisos de archivo predeterminados. Hay disponible una versión más segura de esta función; vea [_umask_s](../../c-runtime-library/reference/umask-s.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _umask(  
   int pmode   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pmode`  
 Configuración de permisos predeterminada.  
  
## <a name="return-value"></a>Valor devuelto  
 `_umask` devuelve el valor anterior de `pmode`. No se devuelve ningún error.  
  
## <a name="remarks"></a>Comentarios  
 El `_umask` función establece la máscara de permisos de archivo del proceso actual en el modo especificado por `pmode`. La máscara de permisos de archivo modifica la configuración de permisos de los nuevos archivos creados por `_creat`, `_open` o `_sopen`. Si un bit de la máscara es 1, el bit correspondiente del valor de permiso solicitado del archivo se establece en 0 (no permitido). Si un bit de la máscara es 0, el bit correspondiente se deja sin modificar. La configuración de permisos de un nuevo archivo no se establece hasta que se cierra el archivo por primera vez.  
  
 La expresión de entero `pmode` contiene una o las dos constantes del manifiesto siguientes, definidas en SYS\STAT.H:  
  
 `_S_IWRITE`  
 Escritura permitida.  
  
 `_S_IREAD`  
 Lectura permitida.  
  
 `_S_IREAD | _S_IWRITE`  
 Lectura y escritura permitidas.  
  
 Cuando se proporcionan ambas constantes, se unen mediante el operador OR bit a bit (`|`). Si el argumento `pmode` es `_S_IREAD`, no se permite la lectura (el archivo es de solo escritura). Si el argumento `pmode` es `_S_IWRITE`, no se permite la escritura (el archivo es de solo lectura). Por ejemplo, si el bit de escritura está establecido en la máscara, los nuevos archivos serán de solo lectura. Tenga en cuenta que en los sistemas operativos MS-DOS y Windows, todos los archivos se pueden leer; no se puede conceder permiso de solo escritura. Por tanto, el establecimiento del bit de lectura con `_umask` no tiene ningún efecto sobre los modos del archivo.  
  
 Si `pmode` no es una combinación de una de las constantes del manifiesto o incorpora un conjunto alternativo de constantes, la función simplemente las omitirá.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_umask`|\<io.h>, \<sys/stat.h>, \<sys/types.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_umask.c  
// compile with: /W3  
// This program uses _umask to set  
// the file-permission mask so that all future  
// files will be created as read-only files.  
// It also displays the old mask.  
#include <sys/stat.h>  
#include <sys/types.h>  
#include <io.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int oldmask;  
  
   /* Create read-only files: */  
   oldmask = _umask( _S_IWRITE ); // C4996  
   // Note: _umask is deprecated; consider using _umask_s instead  
   printf( "Oldmask = 0x%.4x\n", oldmask );  
}  
```  
  
```Output  
Oldmask = 0x0000  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)   
 [_chmod, _wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_creat, _wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_mkdir, _wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)
