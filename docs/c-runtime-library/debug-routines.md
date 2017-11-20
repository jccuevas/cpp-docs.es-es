---
title: "Rutinas de depuración | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.debug
dev_langs: C++
helpviewer_keywords:
- debugging [CRT], using macros
- macros, debugging with
- debug routines
- debug macros
- debugging [CRT], run-time routines
ms.assetid: cb4d2664-10f3-42f7-a516-595558075471
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 25bbbfae7e12154f9e64540ce9f5e8bdb7ebef42
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="debug-routines"></a>Rutinas de depuración
La versión de depuración de la biblioteca en tiempo de ejecución de C ofrece muchos servicios de diagnóstico que facilitan la depuración de programas y permiten a los desarrolladores:  
  
-   Usar directamente funciones en tiempo de ejecución durante la depuración  
  
-   Resolver aserciones, errores y excepciones  
  
-   Realizar el seguimiento de las asignaciones del montón y evitar pérdidas de memoria  
  
-   Proporcionar mensajes de depuración al usuario  
  
 Para usar estas rutinas es necesario definir la marca [_DEBUG](../c-runtime-library/debug.md). Todas estas rutinas no hacen nada en una compilación comercial de una aplicación. Para obtener más información sobre cómo usar las nuevas rutinas de depuración, consulte [Técnicas de depuración de CRT](/visualstudio/debugger/crt-debugging-techniques).  
  
### <a name="debug-versions-of-the-c-run-time-library-routines"></a>Versiones de depuración de las rutinas de la biblioteca en tiempo de ejecución de C  
  
|Rutina|Uso|  
|-------------|---------|  
|[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|Evalúa una expresión y genera un informe de depuración cuando el resultado es FALSE|  
|[_ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|Parecida a `_ASSERT`, pero incluye la expresión del error en el informe generado|  
|[_CrtCheckMemory](../c-runtime-library/reference/crtcheckmemory.md)|Confirma la integridad de los bloques de memoria asignados en el montón de depuración|  
|[_CrtDbgBreak](../c-runtime-library/reference/crtdbgbreak.md)|Establece un punto de interrupción|  
|[_CrtDbgReport, _CrtDbgReportW](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)|Genera un informe de depuración con un mensaje de usuario y envía el informe a tres destinos posibles|  
|[_CrtDoForAllClientObjects](../c-runtime-library/reference/crtdoforallclientobjects.md)|Llama a una función suministrada por la aplicación para todos los tipos de `_CLIENT_BLOCK` del montón|  
|[_CrtDumpMemoryLeaks](../c-runtime-library/reference/crtdumpmemoryleaks.md)|Vuelca todos los bloques de memoria del montón de depuración cuando se ha producido una fuga de memoria significativa|  
|[_CrtIsMemoryBlock](../c-runtime-library/reference/crtismemoryblock.md)|Comprueba que un bloque de memoria especificado está en el montón local y que tiene un identificador válido de tipo de bloque de montón de depuración|  
|[_CrtIsValidHeapPointer](../c-runtime-library/reference/crtisvalidheappointer.md)|Comprueba que un puntero especificado está en el montón local|  
|[_CrtIsValidPointer](../c-runtime-library/reference/crtisvalidpointer.md)|Comprueba que un intervalo de memoria especificado es válido para lectura y escritura|  
|[_CrtMemCheckpoint](../c-runtime-library/reference/crtmemcheckpoint.md)|Obtiene el estado actual del montón de depuración y lo almacena en una estructura de `_CrtMemState` proporcionada por la aplicación|  
|[_CrtMemDifference](../c-runtime-library/reference/crtmemdifference.md)|Compara si dos estados de memoria tienen diferencias significativas y devuelve los resultados|  
|[_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md)|Vuelca la información sobre objetos del montón desde que se tomó un punto de comprobación especificado o desde que se empezó a ejecutar el programa|  
|[_CrtMemDumpStatistics](../c-runtime-library/reference/crtmemdumpstatistics.md)|Vuelca la información de encabezado de depuración para un estado de memoria especificado con un formato legible para el usuario|  
|[_CrtReportBlockType](../c-runtime-library/reference/crtreportblocktype.md)|Devuelve el tipo o subtipo de bloque asociado a un puntero de bloque especificado del montón de depuración.|  
|[_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md)|Instala una función de asignación definida por el cliente enlazándola al proceso de asignación de memoria de depuración en tiempo de ejecución de C|  
|[_CrtSetBreakAlloc](../c-runtime-library/reference/crtsetbreakalloc.md)|Establece un punto de interrupción en un número de orden especificado de la asignación de objetos|  
|[_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md)|Recupera o modifica el estado de la marca `_crtDbgFlag` para controlar el comportamiento de asignación del administrador del montón de depuración|  
|[_CrtSetDumpClient](../c-runtime-library/reference/crtsetdumpclient.md)|Instala una función definida por la aplicación a la que se llama cada vez que se llama a una función de volcado de depuración para volcar los bloques de memoria de tipo `_CLIENT_BLOCK`|  
|[_CrtSetReportFile](../c-runtime-library/reference/crtsetreportfile.md)|Identifica el archivo o flujo que se va a usar como destino de un tipo de informe concreto `_CrtDbgReport`|  
|[_CrtSetReportHook](../c-runtime-library/reference/crtsetreporthook.md)|Instala una función de creación de informes definida por el cliente enlazándola al proceso de creación de informes de depuración en tiempo de ejecución de C|  
|[_CrtSetReportHook2, _CrtSetReportHookW2](../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)|Instala o desinstala una función de generación de informes definida por el cliente enlazándola al proceso de creación de informes de depuración en tiempo de ejecución de C|  
|[_CrtSetReportMode](../c-runtime-library/reference/crtsetreportmode.md)|Especifica los destinos generales de un tipo específico de informe generado por `_CrtDbgReport`|  
|[_RPT&#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|Realiza el seguimiento del progreso de la aplicación generando un informe de depuración mediante una llamada a `_CrtDbgReport` con una cadena de formato y un número variable de argumentos. No proporciona información sobre el archivo de código fuente y el número de línea.|  
|[_RPTF&#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|Es parecida a las macros de `_RPTn`, pero proporciona el nombre del archivo de código fuente y el número de línea donde se originó la solicitud de informe|  
|[_calloc_dbg](../c-runtime-library/reference/calloc-dbg.md)|Asigna un número especificado de bloques de memoria del montón con espacio adicional para un encabezado de depuración y búferes de sobrescritura|  
|[_expand_dbg](../c-runtime-library/reference/expand-dbg.md)|Cambia el tamaño de un bloque de memoria especificado del montón, expandiendo o contrayendo el bloque|  
|[_free_dbg](../c-runtime-library/reference/free-dbg.md)|Libera un bloque de memoria del montón|  
|[_fullpath_dbg, _wfullpath_dbg](../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md)|Crea un nombre de ruta de acceso absoluta o completa para el nombre de ruta de acceso relativa especificado, usando [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) para asignar memoria.|[System::IO::File::Create](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)|  
|[_getcwd_dbg, _wgetcwd_dbg](../c-runtime-library/reference/getcwd-dbg-wgetcwd-dbg.md)|Obtiene el directorio de trabajo actual, usando [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) para asignar memoria.|  
|[_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md)|Asigna un bloque de memoria del montón con espacio adicional para un encabezado de depuración y búferes de sobrescritura|  
|[_msize_dbg](../c-runtime-library/reference/msize-dbg.md)|Calcula el tamaño de un bloque de memoria del montón|  
|[_realloc_dbg](../c-runtime-library/reference/realloc-dbg.md)|Reasigna un bloque de memoria especificado en el montón, para lo que lo mueve o lo cambia de tamaño|  
|[_strdup_dbg, _wcsdup_dbg](../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md)|Duplica una cadena, usando [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) para asignar memoria.|  
|[_tempnam_dbg, _wtempnam_dbg](../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md)|Genera nombres que se pueden usar para crear archivos temporales, usando [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) para asignar memoria.|  
  
 Las rutinas de depuración se pueden usar para recorrer el código fuente de la mayoría de las demás rutinas en tiempo de ejecución de C durante el proceso de depuración. Sin embargo, Microsoft considera que alguna tecnología es de su propiedad y, por consiguiente, no proporciona el código fuente de estas rutinas. La mayoría de estas rutinas pertenecen a los grupos de control de excepciones o de procesamiento de punto flotante, pero también se incluyen algunas otras. En la siguiente tabla se enumeran estas rutinas.  
  
### <a name="c-run-time-routines-that-are-not-available-in-source-code-form"></a>Rutinas en tiempo de ejecución de C no disponibles en formato de código fuente  
  
||||  
|-|-|-|  
|[acos, acosf, acosl](../c-runtime-library/reference/acos-acosf-acosl.md)|[_fpclass](../c-runtime-library/reference/fpclass-fpclassf.md)|[_nextafter](../c-runtime-library/reference/nextafter-functions.md)|  
|[asin](../c-runtime-library/reference/asin-asinf-asinl.md)|[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|[pow](../c-runtime-library/reference/pow-powf-powl.md)|  
|[atan, atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[_fpreset](../c-runtime-library/reference/fpreset.md)|[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md), [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)*|  
|[_cabs](../c-runtime-library/reference/cabs.md)|[frexp](../c-runtime-library/reference/frexp.md)|[_scalb](../c-runtime-library/reference/scalb.md)|  
|[ceil](../c-runtime-library/reference/ceil-ceilf-ceill.md)|[_hypot](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md), [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)*|  
|[_chgsign, _chgsignf, _chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|[_isnan](../c-runtime-library/reference/isnan-isnan-isnanf.md)|[setjmp](../c-runtime-library/reference/setjmp.md)|  
|[_clear87, _clearfp](../c-runtime-library/reference/clear87-clearfp.md)|[_j0](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|[sin](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|  
|[_control87, _controlfp, \__control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md)|[_j1](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|[sinh](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|  
|[copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|[_jn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|  
|[cos](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|[ldexp](../c-runtime-library/reference/ldexp.md)|[_status87, _statusfp](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|  
|[cosh](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|[tan](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[Exp](../c-runtime-library/reference/exp-expf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[tanh](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[_logb](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|[_y0](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|  
|[_finite](../c-runtime-library/reference/finite-finitef.md)|[longjmp](../c-runtime-library/reference/longjmp.md)|[_y1](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|  
|[floor](../c-runtime-library/reference/floor-floorf-floorl.md)|[_matherr](../c-runtime-library/reference/matherr.md)|[_yn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|  
|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|[modf](../c-runtime-library/reference/modf-modff-modfl.md)||  
  
 \*   Aunque hay código fuente disponible para la mayor parte de esta rutina, realiza una llamada interna a otra rutina para la que no se proporciona código fuente.  
  
 Ciertas funciones en tiempo de ejecución de C y algunos operadores de C++ se comportan de manera diferente cuando se les llama desde una versión de depuración de una aplicación. (Observe que una compilación de depuración de una aplicación se puede generar definiendo la marca `_DEBUG` o vinculándola a una versión de depuración de la biblioteca en tiempo de ejecución de C). Las diferencias de comportamiento suelen tener relación con características adicionales o información proporcionada por la rutina para posibilitar el proceso de depuración. En la siguiente tabla se enumeran estas rutinas.  
  
### <a name="routines-that-behave-differently-in-a-debug-build-of-an-application"></a>Rutinas que se comportan de manera diferente en una compilación de depuración de una aplicación  
  
|||  
|-|-|  
|[abort](../c-runtime-library/reference/abort.md) (Rutina) de C|[delete](../cpp/delete-operator-cpp.md) (Operador) de C++|  
|[assert](../c-runtime-library/reference/assert-macro-assert-wassert.md) (Rutina) de C|[new](../cpp/new-operator-cpp.md) (Operador) de C++|  
  
## <a name="see-also"></a>Vea también  
 [Rutinas en tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)   
 [Comprobar errores en tiempo de ejecución](../c-runtime-library/run-time-error-checking.md)