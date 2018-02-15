---
title: _endthread, _endthreadex | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _endthread
- _endthreadex
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _endthread
- endthreadex
- _endthreadex
- endthread
dev_langs:
- C++
helpviewer_keywords:
- _endthread function
- endthread function
- terminating threads
- endthreadex function
- _endthreadex function
- threading [C++], terminating threads
ms.assetid: 18a91f2f-659e-40b4-b266-ec12dcf2abf5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 794dc5c4bbaf9653c5b6bbb08ea3e0a60ca438c4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="endthread-endthreadex"></a>_endthread, _endthreadex
Termina un subproceso; `_endthread` termina un subproceso creado por `_beginthread` y  `_endthreadex` termina un subproceso creado por `_beginthreadex`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _endthread( void );  
void _endthreadex(   
   unsigned retval   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `retval`  
 Código de salida del subproceso.  
  
## <a name="remarks"></a>Comentarios  
 Puede llamar a `_endthread` o `_endthreadex` explícitamente para terminar un subproceso; sin embargo, se llama a `_endthread` o `_endthreadex` automáticamente cuando el subproceso vuelve de la rutina que se pasa como parámetro a `_beginthread` o `_beginthreadex`. Si se finaliza un subproceso con una llamada a `endthread` o las ayudas de `_endthreadex` , se garantiza la recuperación correcta de los recursos que se asignan para el subproceso.  
  
> [!NOTE]
>  En el caso de un archivo ejecutable vinculado a Libcmt.lib, no llame a la API [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659.aspx) de Win32 porque esto impide que el sistema en tiempo de ejecución reclame los recursos asignados. `_endthread` y `_endthreadex` recuperan los recursos de subprocesos asignados y después llaman a `ExitThread`.  
  
 `_endthread` cierra automáticamente el identificador del subproceso. Este comportamiento es distinto que el de la API `ExitThread` de Win32. Por consiguiente, cuando use `_beginthread` y `_endthread`, no cierre el identificador de subproceso de forma explícita llamando a la API [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211.aspx) de Win32.  
  
 Al igual que la API `ExitThread` de Win32, `_endthreadex` no cierra el identificador del subproceso. Por consiguiente, al usar `_beginthreadex` y `_endthreadex`, debe cerrar el identificador de subproceso llamando a la API `CloseHandle` de Win32.  
  
> [!NOTE]
>  `_endthread` y `_endthreadex` hacen que no se llame a los destructores de C++ pendientes en el subproceso.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`_endthread`|\<process.h>|  
|`_endthreadex`|\<process.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Bibliotecas  
 Solo las versiones de multiproceso de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md) .  
  
## <a name="example"></a>Ejemplo  
 Consulte el ejemplo de [_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md).  
  
## <a name="see-also"></a>Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [_beginthread, _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)