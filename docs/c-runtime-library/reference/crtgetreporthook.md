---
title: _CrtGetReportHook | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtGetReportHook
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
- CrtGetReportHook
- _CrtGetReportHook
dev_langs:
- C++
helpviewer_keywords:
- CrtGetReportHook function
- _CrtGetReportHook function
ms.assetid: 922758ed-7edd-4359-9c92-0535192dc11a
caps.latest.revision: 12
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 35916e544ac6fdf5ff6597fa52fbb0489011a5e4
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="crtgetreporthook"></a>_CrtGetReportHook
Recupera la función de creación de informes definida por el usuario para enlazarla al tiempo de ejecución de C para el proceso de creación de informes de depuración (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
_CRT_REPORT_HOOK _CrtGetReportHook( void );  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve la función actual de creación de informes definida por el cliente.  
  
## <a name="remarks"></a>Comentarios  
 `_CrtGetReportHook` permite que una aplicación recupere la función actual de creación de informes para el proceso de creación de informes de la biblioteca de depuración en tiempo de ejecución de C.  
  
 Para obtener más información sobre cómo usar otras funciones con capacidad de enlace en tiempo de ejecución y cómo escribir funciones de enlace definidas por el cliente, consulte [Creación de funciones de enlace de depuración](/visualstudio/debugger/debug-hook-function-writing).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_CrtGetReportHook`|\<crtdbg.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo de cómo usar `_CrtSetReportHook`, consulte [report](http://msdn.microsoft.com/en-us/f6e08c30-6bd9-459a-830a-56deec0d2051).  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [_CrtSetReportHook](../../c-runtime-library/reference/crtsetreporthook.md)
