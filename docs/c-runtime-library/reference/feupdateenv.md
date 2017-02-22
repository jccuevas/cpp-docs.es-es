---
title: "feupdateenv | Microsoft Docs"
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
  - "feupdateenv"
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
  - "feupdateenv"
  - "fenv/feupdateenv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "feupdateenv (función)"
ms.assetid: 3d170042-dfd5-4e4f-a55f-038cf2296cc9
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# feupdateenv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Guarda las excepciones de punto flotante actualmente elevadas, restaura el estado del entorno de punto flotante especificado y, a continuación, genera las excepciones de punto flotante guardadas.  
  
## Sintaxis  
  
```  
int feupdateenv(  
   const fenv_t* penv  
);  
```  
  
#### Parámetros  
 `penv`  
 Puntero a un `fenv_t` objeto que contiene un entorno de punto flotante como conjunto mediante una llamada a [fegetenv](../Topic/fegetenv2.md) o [feholdexcept](../Topic/feholdexcept1.md). También puede especificar el entorno de punto flotante de inicio predeterminado mediante la macro FE\_DFL\_ENV.  
  
## Valor devuelto  
 Devuelve 0 si todas las acciones se completan correctamente. De lo contrario, devuelve un valor distinto de cero.  
  
## Comentarios  
 El `feupdateenv` función realiza varias acciones. En primer lugar, almacena los indicadores de estado de excepción de punto flotante actual en el almacenamiento automático. A continuación, Establece el entorno actual de punto flotante del valor almacenado en el `fenv_t` objeto señalado por `penv`. Si `penv` no es FE\_DFL\_ENV o no apunta a una `fenv_t` objeto posterior comportamiento es indefinido. Por último, `feupdateenv` genera las excepciones de punto flotante almacenadas localmente.  
  
 Para utilizar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante el uso de la `#pragma fenv_access(on)` Directiva antes de la llamada. Para obtener más información, consulta [fenv\_access](../../preprocessor/fenv-access.md).  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`feupdateenv`|\<fenv.h\>|\<cfenv\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [fegetenv](../../c-runtime-library/reference/fegetenv1.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)