---
title: "fetestexcept1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fetestexcept"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "fetestexcept"
  - "fenv/fetestexcept"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fetestexept (función)"
ms.assetid: ca4dc43f-5573-440d-bc19-ead7571b13dc
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# fetestexcept
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina cuál de los indicadores de estado de excepción de punto flotante especificado actualmente establecidos.  
  
## Sintaxis  
  
```  
int fetestexcept(  
   int excepts  
);  
  
```  
  
#### Parámetros  
 `excepts`  
 OR bit a bit de los indicadores de estado de punto flotante para probar.  
  
## Valor devuelto  
 Si se ejecuta correctamente, devuelve una máscara de bits que contiene una operación OR bit a bit de las macros de excepción de punto flotante que se corresponden con los indicadores de estado de excepción actualmente establecido. Devuelve 0 si ninguna de las excepciones se establece.  
  
## Comentarios  
 Utilice la función fetestexcept para determinar las excepciones producidas por un flotante operación de punto. Utilice el `excepts` para especificar qué marcas de estado de excepción para probar. El `fetestexcept` función usa estas macros de excepción definidas en \< fenv.h \> `excepts` y el valor devuelto:  
  
|Macros de excepción|Descripción|  
|-------------------------|-----------------|  
|FE\_DIVBYZERO|Se produjo un error de singularidad o polo en una operación punto flotante anteriormente; se creó un valor infinito.|  
|FE\_INEXACT|Se forzó la función redondear el resultado de una operación de punto flotante anteriormente almacenado.|  
|FE\_INVALID|Se produjo un error de dominio en una operación de punto flotante anteriormente.|  
|FE\_OVERFLOW|Se produjo un error de intervalo; un resultado de la operación de punto flotante anterior era demasiado grande para representarse.|  
|FE\_UNDERFLOW|Un resultado de la operación de punto flotante anterior era demasiado pequeño para representarlo en precisión completa; se creó un valor desnormalizados.|  
|FE\_ALLEXCEPT|La operación OR bit a bit de todos los admite excepciones de punto flotante.|  
  
 Especificado `excepts` argumento puede ser 0, una de las macros de excepción de punto flotante compatibles o bit a bit o de dos o más de las macros. El efecto de cualquier otro `excepts` el valor del argumento es indefinido.  
  
 Para utilizar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante el uso de la `#pragma fenv_access(on)` Directiva antes de la llamada. Para obtener más información, consulta [fenv\_access](../../preprocessor/fenv-access.md).  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`fetestexcept`|\<fenv.h\>|\<cfenv\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feraiseexcept](../../c-runtime-library/reference/feraiseexcept.md)