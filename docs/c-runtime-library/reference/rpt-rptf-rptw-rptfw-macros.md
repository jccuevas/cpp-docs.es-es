---
title: _RPT, _RPTF, _RPTW, _RPTFW (Macros) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
- RPT3
- RPTF4
- _RPT4
- RPT1
- _RPTF0
- RPTF3
- _RPTF4
- RPTF1
- RPT4
- _RPT1
- _RPT0
- RPT0
- _RPTF2
- RPTF0
- _RPT3
- _RPT2
- _RPTF3
- RPT2
- _RPTF1
dev_langs: C++
helpviewer_keywords:
- debugging [CRT], using macros
- _RPTW3 macro
- _RPT0 macro
- RPTW4 macro
- _RPTF3 macro
- _RPTW4 macro
- RPTF4 macro
- RPTFW2 macro
- RPTW macros
- RPT1 macro
- _RPTF macros
- RPTFW3 macro
- _RPTW0 macro
- _RPTF0 macro
- macros, debugging with
- _RPTW2 macro
- RPTF3 macro
- RPT3 macro
- RPT0 macro
- _RPT macros
- RPTW3 macro
- _RPTFW macros
- debug reporting macros
- RPTF macros
- RPT macros
- _RPTW macros
- RPTF2 macro
- _RPTF1 macro
- _RPT1 macro
- _RPT4 macro
- _RPTFW2 macro
- _RPTFW1 macro
- RPTF0 macro
- _RPT2 macro
- RPTFW macros
- _RPTW1 macro
- _RPTFW0 macro
- RPT4 macro
- _RPT3 macro
- _RPTFW3 macro
- _RPTF4 macro
- _RPTFW4 macro
- _RPTF2 macro
- RPTW0 macro
- RPTFW4 macro
- RPTFW0 macro
- RPTW2 macro
- RPTF1 macro
- RPT2 macro
- RPTFW1 macro
- RPTW1 macro
ms.assetid: a5bf8b30-57f7-4971-8030-e773b7a1ae13
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 453b04174325a7c112105bdef1147e1b7909ccdb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="rpt-rptf-rptw-rptfw-macros"></a>_RPT, _RPTF, _RPTW, _RPTFW (Macros)
Realiza el seguimiento del progreso de la aplicación generando un informe de depuración (únicamente una versión de depuración). Tenga en cuenta que  *n*  especifica el número de argumentos en `args` y puede ser 0, 1, 2, 3, 4 o 5.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      _RPT  
      n  
      (  
   reportType,  
   format,  
...[args]  
);  
_RPTFn(  
   reportType,  
   format,  
   [args]  
);  
_RPTWn(  
   reportType,  
   format   
   [args]  
);  
_RPTFWn(  
   reportType,  
   format   
   [args]  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `reportType`  
 Tipo de informe: `_CRT_WARN`, `_CRT_ERROR` o `_CRT_ASSERT`.  
  
 `format`  
 Cadena de control de formato usada para crear el mensaje de usuario.  
  
 `args`  
 Argumentos de sustitución usados por `format`.  
  
## <a name="remarks"></a>Comentarios  
 Todas estas macros toman el `reportType` y `format` parámetros. Además, también pueden tomar hasta cuatro argumentos adicionales, indicados con el número anexado al nombre de la macro. Por ejemplo, `_RPT0` y `_RPTF0` no toman ningún argumento adicional, `_RPT1` y `_RPTF1` toman `arg1`, `_RPT2` y `_RPTF2` toman `arg1` y `arg2`, y así sucesivamente.  
  
 Las `_RPT` y `_RPTF` son similares a la función [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md), ya que se pueden usar para realizar un seguimiento del progreso de la aplicación durante el proceso de depuración. Sin embargo, estas macros son más flexibles que `printf`, puesto que no tienen que incluirse en las instrucciones `#ifdef` para evitar que se llamen en una compilación comercial de una aplicación. Esta flexibilidad se logra usando la macro [_DEBUG](../../c-runtime-library/debug.md); las macros `_RPT` y `_RPTF` solo están disponibles si se define la marca `_DEBUG`. Cuando no se define `_DEBUG` , las llamadas a estas macros se quitan durante el preprocesamiento.  
  
 Las macros `_RPTW` y `_RPTFW` son versiones de caracteres anchos de estas macros. Son como `wprintf` y toman las cadenas de caracteres anchos como argumentos.  
  
 Las macros `_RPT` llaman a la función [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) para generar un informe de depuración con un mensaje de usuario. Las macros `_RPTW` llaman a la función `_CrtDbgReportW` para generar el mismo informe con caracteres anchos. Las macros `_RPTF` y `_RPTFW` crean un informe de depuración con el archivo de origen y el número de línea donde se llamó a la macro del informe, además del mensaje de usuario. El mensaje de usuario se crea al sustituir el `arg`[*n*] argumentos a la `format` de cadena, utilizando las mismas reglas definidas por el [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) función.  
  
 `_CrtDbgReport` o `_CrtDbgReportW` genera el informe de depuración y determina sus destinos en función de los modos de informe actuales y del archivo definido para `reportType`. Las funciones [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) y [_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md) se usan para definir los destinos de cada tipo de informe.  
  
 Si se llama a una macro `_RPT` y no se ha llamado ni a `_CrtSetReportMode` ni a `_CrtSetReportFile`, los mensajes se muestran del siguiente modo.  
  
|Tipo de informe|Destino de salida|  
|-----------------|------------------------|  
|`_CRT_WARN`|No se muestra el texto de advertencia.|  
|`_CRT_ERROR`|Ventana emergente. Lo mismo que si se hubiera especificado `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);`.|  
|`_CRT_ASSERT`|Igual a `_CRT_ERROR`.|  
  
 Cuando el destino es una ventana de mensaje de depuración y el usuario pulsa el botón **Reintentar**, `_CrtDbgReport` o `_CrtDbgReportW` devuelve 1, lo que hace que estas macros inicien el depurador, siempre y cuando la depuración Just-In-Time (JIT) esté habilitada. Para obtener más información sobre cómo usar estas macros como mecanismo de control de errores de depuración, vea [Using Macros for Verification and Reporting](/visualstudio/debugger/macros-for-reporting) (Uso de macros para comprobación e informes).  
  
 Existen otras dos macros que generan un informe de depuración. La macro [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) genera un informe, pero solo cuando su argumento de expresión se evalúa como FALSE. [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) es exactamente igual que `_ASSERT`, pero incluye la expresión incorrecta en el informe generado.  
  
## <a name="requirements"></a>Requisitos  
  
|Macro|Encabezado necesario|  
|-----------|---------------------|  
|`_RPT` macros|\<crtdbg.h>|  
|`_RPTF` macros|\<crtdbg.h>|  
|`_RPTW` macros|\<crtdbg.h>|  
|`_RPTFW` macros|\<crtdbg.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
 Aunque se trata de macros y se obtienen incluyendo Crtdbg.h, la aplicación debe vincularse con una de las bibliotecas de depuración, ya que estas macros llaman a otras funciones en tiempo de ejecución.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo del tema [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md).  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)