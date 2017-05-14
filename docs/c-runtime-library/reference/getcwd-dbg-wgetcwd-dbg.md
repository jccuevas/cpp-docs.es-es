---
title: _getcwd_dbg, _wgetcwd_dbg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wgetcwd_dbg
- _getcwd_dbg
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getcwd_dbg
- _wgetcwd_dbg
- getcwd_dbg
- wgetcwd_dbg
dev_langs:
- C++
helpviewer_keywords:
- wgetcwd_dbg function
- working directory
- _getcwd_dbg function
- getcwd_dbg function
- current working directory
- _wgetcwd_dbg function
- directories [C++], current working
ms.assetid: 8d5d151f-d844-4aa6-a28c-1c11a22dc00d
caps.latest.revision: 15
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
ms.openlocfilehash: 9814916e32878a1e1a11f534fce64aeaf2f6a57e
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="getcwddbg-wgetcwddbg"></a>_getcwd_dbg, _wgetcwd_dbg
Versiones de depuración de las funciones [_getcwd, _wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md) (disponibles únicamente durante la depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
char *_getcwd_dbg(   
   char *buffer,  
   int maxlen,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
wchar_t *_wgetcwd_dbg(   
   wchar_t *buffer,  
   int maxlen,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `buffer`  
 Ubicación de almacenamiento de la ruta de acceso.  
  
 `maxlen`  
 Longitud máxima de la ruta de acceso en caracteres: `char` para `_getcwd_dbg` y `wchar_t` para `_wgetcwd_dbg`.  
  
 `blockType`  
 Tipo de bloque de memoria solicitado: `_CLIENT_BLOCK` o `_NORMAL_BLOCK`.  
  
 `filename`  
 Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o valor `NULL`.  
  
 `linenumber`  
 Número de línea del archivo de código fuente en la que se solicitó la operación de asignación o valor `NULL`.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a `buffer`. Un valor devuelto de `NULL` indica un error, y `errno` se establece en `ENOMEM`, que indica que no hay memoria suficiente para asignar los bytes de `maxlen` (cuando un argumento de `NULL` se proporciona como `buffer`), o en `ERANGE`, que indica que la ruta de acceso es más larga que los caracteres de `maxlen`.  
  
 Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 El `_getcwd_dbg` y `_wgetcwd_dbg` funciones son idénticas a `_getcwd` y `_wgetcwd` salvo que, cuando `_DEBUG` está definido, estas funciones usan la versión de depuración `malloc` y `_malloc_dbg` para asignar memoria si `NULL` se pasa como primer parámetro. Para obtener más información, consulte [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md).  
  
 En la mayoría de los casos, no es necesario llamar a estas funciones explícitamente en la mayoría. En lugar de ello, se puede definir la marca `_CRTDBG_MAP_ALLOC`. Si se define `_CRTDBG_MAP_ALLOC`, las llamadas a `_getcwd` y `_wgetcwd` se reasignan a `_getcwd_dbg` y `_wgetcwd_dbg`, respectivamente, con el parámetro `blockType` establecido en `_NORMAL_BLOCK`. Por consiguiente, no necesario llamar a estas funciones explícitamente a menos que se desee marcar los bloques del montón como `_CLIENT_BLOCK`. Para obtener más información, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tgetcwd_dbg`|`_getcwd_dbg`|`_getcwd_dbg`|`_wgetcwd_dbg`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_getcwd_dbg`|\<crtdbg.h>|  
|`_wgetcwd_dbg`|\<crtdbg.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="see-also"></a>Vea también  
 [_getcwd, _wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [Control de directorio](../../c-runtime-library/directory-control.md)   
 [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)
