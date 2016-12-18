---
title: "fegetenv | Microsoft Docs"
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
  - "fetegenv"
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
  - "fegetenv"
  - "fenv/fegetenv"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "fetegenv (función)"
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fegetenv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El entorno actual de punto flotante se almacena en el objeto especificado.  
  
## Sintaxis  
  
```  
int fegetenv(  
   fenv_t *penv  
);  
  
```  
  
#### Parámetros  
 `penv`  
 Puntero a un `fenv_t` objeto para contener los valores de punto flotante del entorno actual.  
  
## Valor devuelto  
 Devuelve 0 si el entorno de punto flotante se almacenó correctamente en `penv`. De lo contrario, devuelve un valor distinto de cero.  
  
## Comentarios  
 El `fegetenv` función almacena el entorno actual de punto flotante en el objeto al que señala `penv`. Flotante entorno punto es el conjunto de indicadores de estado y control de los modos que afectan a los cálculos de punto flotante. Esto incluye el modo de redondeo de dirección y los indicadores de estado para las excepciones de punto flotante. Si `penv` no señala a una `fenv_t` objeto posterior comportamiento es indefinido.  
  
 Para utilizar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante el uso de la `#pragma fenv_access(on)` Directiva antes de la llamada. Para obtener más información, consulta [fenv\_access](../../preprocessor/fenv-access.md).  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`fegetenv`|\<fenv.h\>|\<cfenv\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fesetenv](../../c-runtime-library/reference/fesetenv1.md)