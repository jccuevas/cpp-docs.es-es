---
title: "feraiseexcept | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "feraiseexcept"
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
apitype: "HeaderDef"
f1_keywords: 
  - "feraiseexcept"
  - "fenv/feraiseexcept"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "feraiseexcept (función)"
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# feraiseexcept
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Genera las excepciones de punto flotante especificadas.  
  
## Sintaxis  
  
```  
int feraiseexcept(  
   int excepts  
);  
```  
  
#### Parámetros  
 `excepts`  
 Excepciones de punto flotante que se va a generar.  
  
## Valor devuelto  
 Si todas las excepciones especificadas se producen correctamente, devuelve 0.  
  
## Comentarios  
 El `feraiseexcept` función intenta generar las excepciones de punto flotante especificadas por `excepts`.   El `feraiseexcept` función admite estas macros de excepción, definidas en \< fenv.h \>:  
  
|Macros de excepción|Descripción|  
|-------------------------|-----------------|  
|FE\_DIVBYZERO|Se produjo un error de singularidad o polo en una operación punto flotante anteriormente; se creó un valor infinito.|  
|FE\_INEXACT|Se forzó la función redondear el resultado de una operación de punto flotante anteriormente almacenado.|  
|FE\_INVALID|Se produjo un error de dominio en una operación de punto flotante anteriormente.|  
|FE\_OVERFLOW|Se produjo un error de intervalo; un resultado de la operación de punto flotante anterior era demasiado grande para representarse.|  
|FE\_UNDERFLOW|Un resultado de la operación de punto flotante anterior era demasiado pequeño para representarlo en precisión completa; se creó un valor desnormalizados.|  
|FE\_ALLEXCEPT|La operación OR bit a bit de todos los admite excepciones de punto flotante.|  
  
 El `excepts` argumento puede ser cero, uno de los valores de macros de excepción o bit a bit o de dos o más de las macros de excepción admitidas. Si una de las macros de excepción especificada es FE\_OVERFLOW o FE\_UNDERFLOW, se puede generar la excepción FE\_INEXACT como un efecto secundario.  
  
 Para utilizar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante el uso de la `#pragma fenv_access(on)` Directiva antes de la llamada. Para obtener más información, consulta [fenv\_access](../../preprocessor/fenv-access.md).  
  
 **Specific de Microsoft:** las excepciones especificadas en `excepts` se generan en el orden FE\_INVALID, FE\_DIVBYZERO, FE\_OVERFLOW, FE\_UNDERFLOW, FE\_INEXACT. Sin embargo, FE\_INEXACT se puede generar cuando se genera FE\_OVERFLOW o FE\_UNDERFLOW, incluso si no se especifica en `excepts`.**Fin de Específicos de Microsoft**  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`feraiseexcept`|\<fenv.h\>|\<cfenv\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fetestexcept](../../c-runtime-library/reference/fetestexcept1.md)   
 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md)