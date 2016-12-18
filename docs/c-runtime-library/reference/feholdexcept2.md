---
title: "feholdexcept | Microsoft Docs"
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
  - "feholdexcept"
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
  - "feholdexcept"
  - "fenv/feholdexcept"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "feholdexcept (función)"
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# feholdexcept
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Guarda el entorno actual de punto flotante en el objeto especificado, borra los indicadores de estado de punto flotante y, si es posible, coloca el entorno de punto flotante en modo continuo.  
  
## Sintaxis  
  
```  
int feholdexcept(  
   fenv_t *penv  
);  
  
```  
  
#### Parámetros  
 `penv`  
 Puntero a un `fenv_t` objeto que contiene una copia del entorno de punto flotante.  
  
## Valor devuelto  
 Devuelve cero si y solo si la función es capaz de activar correctamente el control de excepciones de punto flotante sin interrupciones.  
  
## Comentarios  
 El `feholdexcept` función se utiliza para almacenar el estado del entorno de punto flotante actual en la `fenv_t` objeto señalado por `penv`, y para establecer el entorno para no interrumpir la ejecución de las excepciones de punto flotante. Esto se conoce como modo continuo.  Este modo continúa hasta que el entorno se restaura mediante [fesetenv](../Topic/fesetenv2.md) o [feupdateenv](../../c-runtime-library/reference/feupdateenv.md).  
  
 Puede utilizar esta función al principio de una subrutina que necesita para ocultar una o más excepciones de punto flotante del llamador. Para informar de una excepción, simplemente puede borrar las excepciones no deseadas mediante [feclearexcept,](../../c-runtime-library/reference/feclearexcept1.md) y, a continuación, finalice el modo continuo con una llamada a `feupdateenv`.  
  
 Para utilizar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante el uso de la `#pragma fenv_access(on)` Directiva antes de la llamada. Para obtener más información, consulta [fenv\_access](../../preprocessor/fenv-access.md).  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`feholdexcept`|\<fenv.h\>|\<cfenv\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [fesetenv](../Topic/fesetenv2.md)   
 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md)