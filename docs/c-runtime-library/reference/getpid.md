---
title: _getpid | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _getpid
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
- _getpid
dev_langs:
- C++
helpviewer_keywords:
- getpid function
- _getpid function
- process identification numbers
ms.assetid: d3e13bae-9a0c-4f33-86d3-ec9df9519285
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 3321121628e57f7d77cfab33944bf54d9b945459
ms.lasthandoff: 02/24/2017

---
# <a name="getpid"></a>_getpid
Obtiene el identificador del proceso.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea                  [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _getpid( void );  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el identificador del proceso obtenido del sistema. No se devuelve ningún error.  
  
## <a name="remarks"></a>Comentarios  
 La función `_getpid` obtiene el identificador del proceso del sistema. El identificador del proceso identifica el proceso de llamada de forma única.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_getpid`|\<process.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_getpid.c  
// This program uses _getpid to obtain  
// the process ID and then prints the ID.  
  
#include <stdio.h>  
#include <process.h>  
  
int main( void )  
{  
   // If run from command line, shows different ID for   
   // command line than for operating system shell.  
  
   printf( "Process id: %d\n", _getpid() );  
}  
```  
  
```Output  
Process id: 3584  
```  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 [System::Diagnostics::Process::Id](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.id.aspx)  
  
## <a name="see-also"></a>Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [_mktemp, _wmktemp](../../c-runtime-library/reference/mktemp-wmktemp.md)
