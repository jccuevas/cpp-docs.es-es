---
title: Control de errores (CRT) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.errors
dev_langs:
- C++
helpviewer_keywords:
- error handling, C routines for
- logic errors
- error handling, library routines
- testing, for program errors
ms.assetid: 125ac697-9eb0-4152-a440-b7842f23d97f
caps.latest.revision: 8
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
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: ab0f6998aa2f4f6ba5066cbc1d4c6813dcbaab0b
ms.lasthandoff: 02/24/2017

---
# <a name="error-handling-crt"></a>Control de errores (CRT)
Utilice estas rutinas para controlar los errores de programa.  
  
### <a name="error-handling-routines"></a>Rutinas de control de errores  
  
|Rutina|Uso|Equivalente de .NET Framework|  
|-------------|---------|-------------------------------|  
|[assert](../c-runtime-library/reference/assert-macro-assert-wassert.md) (Macro)|Comprueba los errores lógicos de programación; disponible en las versiones de lanzamiento y depuración de la biblioteca de tiempo de ejecución.|[System::Diagnostics::Debug::Assert](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[_ASSERT, _ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) (Macros)|Similar a `assert`, pero disponible únicamente en las versiones de depuración de las biblioteca en tiempo de ejecución.|[System::Diagnostics::Debug::Assert](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[clearerr](../c-runtime-library/reference/clearerr.md)|Indicador de error de restablecimiento. La llamada a `rewind` o el cierre de una secuencia también restaura el indicador de error.|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, consulte [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).|  
|[_eof](../c-runtime-library/reference/eof.md)|Comprueba el final de archivo en E/S de bajo nivel.|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, consulte [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).|  
|[feof](../c-runtime-library/reference/feof.md)|Prueba el fin del archivo. El final del archivo también se indica cuando `_read` devuelve 0.|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, consulte [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).|  
|[ferror](../c-runtime-library/reference/ferror.md)|Comprueba los errores de E/S de secuencia.|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, consulte [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).|  
|[_RPT, _RPTF](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) (Macros)|Genera un informe similar a `printf`, pero disponible únicamente en las versiones de depuración de las biblioteca en tiempo de ejecución.|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, consulte [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).|  
|[_set_error_mode](../c-runtime-library/reference/set-error-mode.md)|Modifica `__error_mode` para determinar una ubicación no predeterminada en donde el tiempo de ejecución de C escribe un mensaje de error si hay un error que podría finalizar el programa.||  
|[_set_purecall_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)|Establece el controlador de una llamada de función virtual pura.||  
  
## <a name="see-also"></a>Vea también  
 [Rutinas en tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)
