---
title: "fesetexceptflag2 | Microsoft Docs"
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
  - "fesetexceptflag"
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
  - "fesetexceptflag"
  - "fenv/fesetexceptflag"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fesetexceptflag (función)"
ms.assetid: 2f7dad77-9e54-4097-a3e3-35176ace4de5
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# fesetexceptflag
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece los indicadores de estado de punto flotante especificado en el entorno actual de punto flotante.  
  
## Sintaxis  
  
```  
int fesetexceptflag(  
     const fexcept_t *pstatus,  
     int excepts  
);  
  
```  
  
#### Parámetros  
 `pstatus`  
 Puntero a un  `fexcept_t` que contiene los valores para establecer los indicadores de estado de la excepción en el objeto. El objeto se puede establecer mediante una llamada anterior a [fegetexceptflag](../Topic/fegetexceptflag1.md).  
  
 `excepts`  
 Los indicadores de estado de excepción de punto flotante para establecer.  
  
## Valor devuelto  
 Si todos los indicadores de estado de excepción especificada se establecen correctamente, devuelve 0. De lo contrario, devuelve un valor distinto de cero.  
  
## Comentarios  
 El `fesetexceptflag` función establece el estado de los indicadores de estado de excepción de punto flotante especificado por `excepts` a los valores correspondientes el `fexcept_t` objeto señalado por `pstatus`.  No se genera las excepciones. El `pstatus` puntero debe señalar a una `fexcept_t` objeto o comportamiento subsiguiente es indefinido. El `fesetexceptflag` función admite estos valores de macros de excepción en `excepts`, definido en \< fenv.h \>:  
  
|Macros de excepción|Descripción|  
|-------------------------|-----------------|  
|FE\_DIVBYZERO|Se produjo un error de singularidad o polo en una operación punto flotante anteriormente; se creó un valor infinito.|  
|FE\_INEXACT|Se forzó la función redondear el resultado de una operación de punto flotante anteriormente almacenado.|  
|FE\_INVALID|Se produjo un error de dominio en una operación de punto flotante anteriormente.|  
|FE\_OVERFLOW|Se produjo un error de intervalo; un resultado de la operación de punto flotante anterior era demasiado grande para representarse.|  
|FE\_UNDERFLOW|Un resultado de la operación de punto flotante anterior era demasiado pequeño para representarlo en precisión completa; se creó un valor desnormalizados.|  
|FE\_ALLEXCEPT|La operación OR bit a bit de todos los admite excepciones de punto flotante.|  
  
 El `excepts` argumento puede ser cero, una de las macros de excepción de punto flotante compatibles o bit a bit o de dos o más de las macros. El efecto de cualquier otro valor del argumento es indefinido.  
  
 Para utilizar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante el uso de la `#pragma fenv_access(on)` Directiva antes de la llamada. Para obtener más información, consulta [fenv\_access](../../preprocessor/fenv-access.md).  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`fesetexceptflag`|\<fenv.h\>|\<cfenv\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fegetexceptflag](../../c-runtime-library/reference/fegetexceptflag2.md)