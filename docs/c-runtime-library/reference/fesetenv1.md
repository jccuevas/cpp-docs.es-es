---
title: "fesetenv | Microsoft Docs"
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
  - "fesetenv"
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
  - "fesetenv"
  - "fenv/fesetenv"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "fesetenv (función)"
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fesetenv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece el entorno actual de punto flotante.  
  
## Sintaxis  
  
```  
int fesetenv(  
   const fenv_t *penv  
);  
  
```  
  
#### Parámetros  
 `penv`  
 Puntero a un `fenv_t` objeto que contiene un entorno de punto flotante como conjunto mediante una llamada a [fegetenv](../Topic/fegetenv2.md) o [feholdexcept](../Topic/feholdexcept1.md). También puede especificar el entorno de punto flotante de inicio predeterminado mediante la macro FE\_DFL\_ENV.  
  
## Valor devuelto  
 Devuelve 0 si el entorno se estableció correctamente. De lo contrario, devuelve un valor distinto de cero.  
  
## Comentarios  
 El `fesetenv` función establece el entorno actual de punto flotante del valor almacenado en el `fenv_t` objeto señalado por `penv`. Flotante entorno punto es el conjunto de indicadores de estado y control de los modos que afectan a los cálculos de punto flotante. Esto incluye el modo de redondeo y los indicadores de estado para las excepciones de punto flotante. Si `penv` no es FE\_DFL\_ENV o no apunta a una `fenv_t` objeto posterior comportamiento es indefinido.  
  
 Una llamada a esta función establece la excepción de los indicadores de estado que se encuentran en la `penv` objeto, pero no genera esas excepciones.  
  
 Para utilizar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante el uso de la `#pragma fenv_access(on)` Directiva antes de la llamada. Para obtener más información, consulta [fenv\_access](../../preprocessor/fenv-access.md).  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`fesetenv`|\<fenv.h\>|\<cfenv\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fegetenv](../../c-runtime-library/reference/fegetenv1.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)