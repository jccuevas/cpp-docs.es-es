---
title: "Rutinas de depuraci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.debug"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "depurar [CRT], usar macros"
  - "macros, depurar con"
  - "rutinas de depuración"
  - "macros de depuración"
  - "depurar [CRT], rutinas en tiempo de ejecución"
ms.assetid: cb4d2664-10f3-42f7-a516-595558075471
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Rutinas de depuraci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La versión de depuración de la biblioteca en tiempo de ejecución de C ofrece muchos servicios de diagnóstico que facilitan la depuración de programas y permiten a los desarrolladores:  
  
-   Usar directamente funciones en tiempo de ejecución durante la depuración  
  
-   Resolver aserciones, errores y excepciones  
  
-   Realizar el seguimiento de las asignaciones del montón y evitar pérdidas de memoria  
  
-   Proporcionar mensajes de depuración al usuario  
  
 Para utilizar estas rutinas es necesario definir la marca [\_DEBUG](../c-runtime-library/debug.md).  Todas estas rutinas no hacen nada en una compilación comercial de una aplicación.  Para obtener más información sobre cómo usar las nuevas rutinas de depuración, vea [Técnicas de depuración de CRT](../Topic/CRT%20Debugging%20Techniques.md).  
  
### Versiones de depuración de las rutinas de la biblioteca en tiempo de ejecución de C  
  
|Rutina|Utilice|Equivalente de .NET Framework|  
|------------|-------------|-----------------------------------|  
|[\_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|Evalúa una expresión y genera un informe de depuración cuando el resultado es FALSE|[\<caps:sentence id\="tgt15" sentenceid\="14fd9bf776829d73028df00162f7533f" class\="tgtSentence"\>System::Diagnostics::Debug::Assert\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[\_ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|Parecida a `_ASSERT`, pero incluye la expresión del error en el informe generado|[\<caps:sentence id\="tgt18" sentenceid\="14fd9bf776829d73028df00162f7533f" class\="tgtSentence"\>System::Diagnostics::Debug::Assert\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[\_CrtCheckMemory](../c-runtime-library/reference/crtcheckmemory.md)|Confirma la integridad de los bloques de memoria asignados en el montón de depuración|[\<caps:sentence id\="tgt20" sentenceid\="e42975224af21ff11a761e6a6bdbd602" class\="tgtSentence"\>System::Diagnostics::PerformanceCounter\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.performancecounter.aspx)|  
|[\_CrtDbgBreak](../c-runtime-library/reference/crtdbgbreak.md)|Establece un punto de interrupción|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_CrtDbgReport, \_CrtDbgReportW](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)|Genera un informe de depuración con un mensaje de usuario y envía el informe a tres destinos posibles|[System::Diagnostics::Debug::Write](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.write.aspx), [System::Diagnostics::Debug::Writeline](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.writeline.aspx), [System::Diagnostics::Debug::WriteIf](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.writeif.aspx), [System::Diagnostics::Debug::WriteLineIf](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.writelineif.aspx)|  
|[\_CrtDoForAllClientObjects](../c-runtime-library/reference/crtdoforallclientobjects.md)|Llama a una función suministrada por la aplicación para todos los tipos de `_CLIENT_BLOCK` del montón|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_CrtDumpMemoryLeaks](../c-runtime-library/reference/crtdumpmemoryleaks.md)|Vuelca todos los bloques de memoria del montón de depuración cuando se ha producido una pérdida de memoria significativa|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_CrtIsMemoryBlock](../c-runtime-library/reference/crtismemoryblock.md)|Comprueba que un bloque de memoria especificado está en el montón local y que tiene un identificador válido de tipo de bloque de montón de depuración|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_CrtIsValidHeapPointer](../c-runtime-library/reference/crtisvalidheappointer.md)|Comprueba que un puntero especificado está en el montón local|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_CrtIsValidPointer](../c-runtime-library/reference/crtisvalidpointer.md)|Comprueba que un intervalo de memoria especificado es válido para lectura y escritura|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_CrtMemCheckpoint](../c-runtime-library/reference/crtmemcheckpoint.md)|Obtiene el estado actual del montón de depuración y lo almacena en una estructura de `_CrtMemState` proporcionada por la aplicación|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_CrtMemDifference](../c-runtime-library/reference/crtmemdifference.md)|Compara si dos estados de memoria tienen diferencias significativas y devuelve los resultados|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md)|Vuelca la información sobre objetos del montón desde que se tomó un punto de comprobación especificado o desde que se empezó a ejecutar el programa|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_CrtMemDumpStatistics](../c-runtime-library/reference/crtmemdumpstatistics.md)|Vuelca la información de encabezado de depuración para un estado de memoria especificado con un formato legible para el usuario|[\<caps:sentence id\="tgt64" sentenceid\="e42975224af21ff11a761e6a6bdbd602" class\="tgtSentence"\>System::Diagnostics::PerformanceCounter\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.performancecounter.aspx)|  
|[\_CrtReportBlockType](../c-runtime-library/reference/crtreportblocktype.md)|Devuelve el tipo o subtipo de bloque asociado a un puntero de bloque especificado del montón de depuración.|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md)|Instala una función de asignación definida por el cliente enlazándola al proceso de asignación de memoria de depuración en tiempo de ejecución de C|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_CrtSetBreakAlloc](../c-runtime-library/reference/crtsetbreakalloc.md)|Establece un punto de interrupción en un número de orden especificado de la asignación de objetos|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md)|Recupera o modifica el estado de la marca `_crtDbgFlag` para controlar el comportamiento de asignación del administrador del montón de depuración|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_CrtSetDumpClient](../c-runtime-library/reference/crtsetdumpclient.md)|Instala una función definida por la aplicación a la que se llama cada vez que se llama a una función de volcado de depuración para volcar los bloques de memoria de tipo `_CLIENT_BLOCK`|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_CrtSetReportFile](../c-runtime-library/reference/crtsetreportfile.md)|Identifica el archivo o flujo que se va a usar como destino de un tipo de informe concreto `_CrtDbgReport`|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_CrtSetReportHook](../c-runtime-library/reference/crtsetreporthook.md)|Instala una función de creación de informes definida por el cliente enlazándola al proceso de creación de informes de depuración en tiempo de ejecución de C|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_CrtSetReportHook2, \_CrtSetReportHookW2](../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)|Instala o desinstala una función de generación de informes definida por el cliente enlazándola al proceso de creación de informes de depuración en tiempo de ejecución de C|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_CrtSetReportMode](../c-runtime-library/reference/crtsetreportmode.md)|Especifica los destinos generales de un tipo específico de informe generado por `_CrtDbgReport`|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_RPT&#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|Realiza el seguimiento del progreso de la aplicación generando un informe de depuración mediante una llamada a `_CrtDbgReport` con una cadena de formato y un número variable de argumentos.  No proporciona información sobre el archivo de código fuente y el número de línea.|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_RPTF &#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|Es parecida a las macros de `_RPTn`, pero proporciona el nombre del archivo de código fuente y el número de línea donde se originó la solicitud de informe|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_calloc\_dbg](../c-runtime-library/reference/calloc-dbg.md)|Asigna un número especificado de bloques de memoria del montón con espacio adicional para un encabezado de depuración y búferes de sobrescritura|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_expand\_dbg](../c-runtime-library/reference/expand-dbg.md)|Cambia el tamaño de un bloque de memoria especificado del montón, expandiendo o contrayendo el bloque|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_free\_dbg](../c-runtime-library/reference/free-dbg.md)|Libera un bloque de memoria del montón|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_fullpath\_dbg, \_wfullpath\_dbg](../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md)|Crea un nombre de ruta de acceso absoluta o completa para el nombre de ruta de acceso relativa especificado, utilizando [\_malloc\_dbg](../c-runtime-library/reference/malloc-dbg.md) para asignar memoria|[\<caps:sentence id\="tgt129" sentenceid\="57f5d14fd2f1847b8e44146f72e48f72" class\="tgtSentence"\>System::IO::File::Create\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)|  
|[\_getcwd\_dbg, \_wgetcwd\_dbg](../c-runtime-library/reference/getcwd-dbg-wgetcwd-dbg.md)|Obtiene el directorio de trabajo actual, usando [\_malloc\_dbg](../c-runtime-library/reference/malloc-dbg.md) para asignar memoria|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_malloc\_dbg](../c-runtime-library/reference/malloc-dbg.md)|Asigna un bloque de memoria del montón con espacio adicional para un encabezado de depuración y búferes de sobrescritura|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_msize\_dbg](../c-runtime-library/reference/msize-dbg.md)|Calcula el tamaño de un bloque de memoria del montón|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_realloc\_dbg](../c-runtime-library/reference/realloc-dbg.md)|Reasigna un bloque de memoria especificado en el montón, para lo que lo mueve o lo cambia de tamaño|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_strdup\_dbg, \_wcsdup\_dbg](../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md)|Duplica una cadena, usando [\_malloc\_dbg](../c-runtime-library/reference/malloc-dbg.md) para asignar memoria|[\<caps:sentence id\="tgt151" sentenceid\="74a4ca1462af4bfed5950888b5c554e1" class\="tgtSentence"\>System::String::Clone\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.string.clone.aspx)|  
|[\_tempnam\_dbg, \_wtempnam\_dbg](../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md)|Genera nombres que se pueden usar para crear archivos temporales, usando [\_malloc\_dbg](../c-runtime-library/reference/malloc-dbg.md) para asignar memoria|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
  
 Las rutinas de depuración se pueden usar para recorrer el código fuente de la mayoría de las demás rutinas en tiempo de ejecución de C durante el proceso de depuración.  Sin embargo, Microsoft considera que alguna tecnología es de su propiedad y, por consiguiente, no proporciona el código fuente de estas rutinas.  La mayoría de estas rutinas pertenecen a los grupos de control de excepciones o de procesamiento de punto flotante, pero también se incluyen algunas otras.  En la siguiente tabla se enumeran estas rutinas.  
  
### Rutinas en tiempo de ejecución de C no disponibles en formato de código fuente  
  
||||  
|-|-|-|  
|[acos, acosf, acosl](../c-runtime-library/reference/acos-acosf-acosl.md)|[\_fpclass](../c-runtime-library/reference/fpclass-fpclassf.md)|[\_nextafter](../c-runtime-library/reference/nextafter-functions.md)|  
|[asin](../c-runtime-library/reference/asin-asinf-asinl.md)|[\_fpieee\_flt](../c-runtime-library/reference/fpieee-flt.md)|[pow](../c-runtime-library/reference/pow-powf-powl.md)|  
|[atan, atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[\_fpreset](../c-runtime-library/reference/fpreset.md)|[printf, \_printf\_l, wprintf, \_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md), [printf\_s, \_printf\_s\_l, wprintf\_s, \_wprintf\_s\_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)\*|  
|[\_cabs](../c-runtime-library/reference/cabs.md)|[frexp](../c-runtime-library/reference/frexp.md)|[\_scalb](../c-runtime-library/reference/scalb.md)|  
|[ceil](../c-runtime-library/reference/ceil-ceilf-ceill.md)|[\_hypot](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|[scanf, \_scanf\_l, wscanf, \_wscanf\_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md), [scanf\_s, \_scanf\_s\_l, wscanf\_s, \_wscanf\_s\_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)\*|  
|[\_chgsign, \_chgsignf, \_chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|[\_isnan](../c-runtime-library/reference/isnan-isnan-isnanf.md)|[setjmp](../c-runtime-library/reference/setjmp.md)|  
|[\_clear87, \_clearfp](../c-runtime-library/reference/clear87-clearfp.md)|[\_j0](../misc/bessel-functions-j0-j1-jn.md)|[sin](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|  
|[\_control87, \_controlfp, \_\_control87\_2](../c-runtime-library/reference/control87-controlfp-control87-2.md)|[\_j1](../misc/bessel-functions-j0-j1-jn.md)|[sinh](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|  
|[copysign, copysignf, copysignl, \_copysign, \_copysignf, \_copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|[\_jn](../misc/bessel-functions-j0-j1-jn.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|  
|[cos](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|[ldexp](../c-runtime-library/reference/ldexp.md)|[\_status87, \_statusfp](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|  
|[cosh](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|[tan](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[Exp](../c-runtime-library/reference/exp-expf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[tanh](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[\_logb](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|[\_y0](../Topic/Bessel%20Functions:%20_y0,%20_y1,%20_yn.md)|  
|[\_finite](../c-runtime-library/reference/finite-finitef.md)|[longjmp](../c-runtime-library/reference/longjmp.md)|[\_y1](../Topic/Bessel%20Functions:%20_y0,%20_y1,%20_yn.md)|  
|[floor](../c-runtime-library/reference/floor-floorf-floorl.md)|[\_matherr](../c-runtime-library/reference/matherr.md)|[\_yn](../Topic/Bessel%20Functions:%20_y0,%20_y1,%20_yn.md)|  
|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|[modf](../c-runtime-library/reference/modf-modff-modfl.md)||  
  
 \* Aunque hay código fuente disponible para la mayor parte de esta rutina, realiza una llamada interna a otra rutina para la que no se proporciona código.  
  
 Ciertas funciones en tiempo de ejecución de C y algunos operadores de C\+\+ se comportan de manera diferente cuando se les llama desde una versión de depuración de una aplicación. \(Observe que una compilación de depuración de una aplicación se puede generar definiendo la marca `_DEBUG` o vinculándola a una versión de depuración de la biblioteca en tiempo de ejecución de C\). Las diferencias de comportamiento suelen tener relación con características adicionales o información proporcionada por la rutina para posibilitar el proceso de depuración.  En la siguiente tabla se enumeran estas rutinas.  
  
### Rutinas que se comportan de manera diferente en una compilación de depuración de una aplicación  
  
|||  
|-|-|  
|Rutina [abort](../c-runtime-library/reference/abort.md) de C|Operador [delete](../cpp/delete-operator-cpp.md) de C\+\+|  
|Rutina [assert](../c-runtime-library/reference/assert-macro-assert-wassert.md) de C|Operador [new](../cpp/new-operator-cpp.md) de C\+\+|  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)   
 [Comprobar errores en tiempo de ejecución](../c-runtime-library/run-time-error-checking.md)