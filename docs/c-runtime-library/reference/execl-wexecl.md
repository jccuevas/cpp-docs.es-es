---
title: _execl, _wexecl | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _execl
- _wexecl
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
- api-ms-win-crt-process-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _execl
- _wexecl
- wexecl
dev_langs:
- C++
helpviewer_keywords:
- _execl function
- wexecl function
- _wexecl function
- execl function
ms.assetid: 81fefb8a-0a06-4221-b2bc-be18e38e89f4
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 670d4ddaa4209830f842c68eb84d1840e1592790
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="execl-wexecl"></a>_execl, _wexecl
Carga y ejecuta nuevos procesos secundarios.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
intptr_t _execl(   
   const char *cmdname,  
   const char *arg0,  
   ... const char *argn,  
   NULL   
);  
intptr_t _wexecl(  
   const wchar_t *cmdname,  
   const wchar_t *arg0,  
   ... const wchar_t *argn,  
   NULL   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cmdname`  
 Ruta de acceso del archivo que se va a ejecutar.  
  
 `arg0, ... argn`  
 Lista de punteros a los parámetros.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se ejecutan correctamente, estas funciones no vuelven al proceso de llamada. Un valor devuelto de -1 indica un error, en cuyo caso el `errno` se establece la variable global.  
  
|valor de errno|Descripción|  
|-----------------|-----------------|  
|`E2BIG`|El espacio necesario para los argumentos y la configuración de entorno supera los 32 kB.|  
|`EACCES`|El archivo especificado tiene un bloqueo o una infracción de uso compartido.|  
|`EINVAL`|Parámetro no válido (uno o varios parámetros eran un puntero nulo o una cadena vacía).|  
|`EMFILE`|Hay demasiados archivos abiertos (se debe abrir el archivo especificado para determinar si es ejecutable).|  
|`ENOENT`|No se encuentra el archivo o la ruta de acceso.|  
|`ENOEXEC`|El archivo especificado no es ejecutable o tiene un formato de archivo ejecutable no válido.|  
|`ENOMEM`|Memoria insuficiente para ejecutar el nuevo proceso; la memoria disponible se ha dañado; o existe un bloque no válido, lo que indica que el proceso de llamada no se asignó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Cada una de estas funciones carga y ejecuta un proceso nuevo, pasando cada argumento de la línea de comandos como parámetro independiente. El primer argumento es el nombre del comando o el archivo ejecutable, y el segundo argumento debe ser igual que el primero. Se convierte en `argv[0]` en el proceso ejecutado. El tercer argumento es el primer argumento, `argv[1]`, del proceso que se está ejecutando.  
  
 Las funciones `_execl` validan sus parámetros. Si `cmdname` o `arg0` es un puntero nulo o una cadena vacía, estas funciones invocan al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven -1. No se ejecuta ningún proceso nuevo.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|Encabezado opcional|  
|--------------|---------------------|---------------------|  
|`_execl`|\<process.h>|\<errno.h>|  
|`_wexecl`|\<process.h> o \<wchar.h>|\<errno.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
 Consulte el ejemplo de [Funciones _exec y _wexec](../../c-runtime-library/exec-wexec-functions.md).  
  
## <a name="see-also"></a>Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [_exec, _wexec (Funciones)](../../c-runtime-library/exec-wexec-functions.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit, _onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_spawn, _wspawn (Funciones)](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)
