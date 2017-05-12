---
title: _CrtCheckMemory | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtCheckMemory
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
- CrtCheckMemory
- _CrtCheckMemory
dev_langs:
- C++
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
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
ms.openlocfilehash: 82b64afbdd80e9b1433f8f9873b4e295fc2e20c1
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="crtcheckmemory"></a>_CrtCheckMemory
Confirma la integridad de los bloques de memoria asignados en el montón de depuración (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
int _CrtCheckMemory( void );  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si se ejecuta correctamente, `_CrtCheckMemory` devuelve TRUE; de lo contrario, la función devuelve FALSE.  
  
## <a name="remarks"></a>Comentarios  
 La función `_CrtCheckMemory` valida la memoria asignada por el administrador del montón de depuración comprobando el montón base subyacente e inspeccionando cada bloque de memoria. Si se encuentra un error o una inconsistencia de memoria en el montón base subyacente, la información de encabezado de depuración o los búferes de sobrescritura, `_CrtCheckMemory` genera un informe de depuración en el que se describe la condición de error. Cuando no se define [_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtCheckMemory` se quitan durante el preprocesamiento.  
  
 El comportamiento de `_CrtCheckMemory` se puede controlar estableciendo los campos de bits de la marca [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) mediante la función [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md). Si se activa el campo de bits **_CRTDBG_CHECK_ALWAYS_DF**, se llama a `_CrtCheckMemory` cada vez que se solicita una operación de asignación de memoria. Aunque este método ralentiza la ejecución, es útil para detectar errores rápidamente. Si se desactiva el campo de bits **_CRTDBG_ALLOC_MEM_DF**, `_CrtCheckMemory` no comprueba el montón y devuelve inmediatamente **TRUE**.  
  
 Dado que esta función devuelve **TRUE** o **FALSE**, se puede pasar a una de las macros [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) para crear un mecanismo sencillo de control de errores de depuración. En el ejemplo siguiente se genera un error de aserción si se detectan daños en el montón:  
  
```  
_ASSERTE( _CrtCheckMemory( ) );  
```  
  
 Para obtener más información sobre cómo se puede usar `_CrtCheckMemory` con otras funciones de depuración, consulte [Funciones que indican el estado del montón](/visualstudio/debugger/crt-debug-heap-details). Para obtener información general sobre la administración de memoria y el montón de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_CrtCheckMemory`|\<crtdbg.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo de cómo usar `_CrtCheckMemory`, consulte [crt_dbg1](http://msdn.microsoft.com/en-us/17b4b20c-e849-48f5-8eb5-dca6509cbaf9).  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)   
 [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md)
