---
title: "_fpclass, _fpclassf | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fpclass"
  - "_fpclassf"
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
  - "api-ms-win-crt-math-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "fpclass"
  - "_fpclass"
  - "_fpclassf"
  - "math/_fpclass"
  - "float/_fpclass"
  - "math/_fpclassf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "fpclass (función)"
  - "números de punto flotante, representación de IEEE"
  - "_fpclass (función)"
  - "_fpclassf (función)"
ms.assetid: 2774872d-3543-446f-bc72-db85f8b95a6b
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fpclass, _fpclassf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve un valor que indica la clasificación del argumento de punto flotante.  
  
## Sintaxis  
  
```  
int _fpclass(   
   double x   
);  
  
int _fpclassf(   
   float x   
); /* x64 only */  
```  
  
#### Parámetros  
 `x`  
 Valor de punto flotante que se va a probar.  
  
## Valor devuelto  
 El `_fpclass` y `_fpclassf` funciones devuelven un valor entero que indica la clasificación de punto flotante del argumento `x`. La clasificación puede tener uno de los valores siguientes, que se define en \< float.h \>.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`_FPCLASS_SNAN`|NaN de señalización|  
|`_FPCLASS_QNAN`|NaN quiet|  
|`_FPCLASS_NINF`|Infinito negativo \(– INF\)|  
|`_FPCLASS_NN`|Negativo normalizado distinto de cero|  
|`_FPCLASS_ND`|Negativo desnormalizado|  
|`_FPCLASS_NZ`|Cero negativo \(\-0\)|  
|`_FPCLASS_PZ`|0 positivo \(\+ 0\)|  
|`_FPCLASS_PD`|Positivo desnormalizado|  
|`_FPCLASS_PN`|Normalizado de positivo distinto de cero|  
|`_FPCLASS_PINF`|Infinito positivo \(\+ INF\)|  
  
## Comentarios  
 El `_fpclass` y `_fpclassf` funciones son específicos de Microsoft. Son similares a [fpclassify](../../c-runtime-library/reference/fpclassify.md), pero devuelve información más detallada sobre el argumento. El `_fpclassf` función sólo está disponible cuando se compila para la x64 plataforma.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_fpclass`|\<float.h\>|  
  
 Para obtener información de compatibilidad y conformidad, consulte [compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [isNaN, \_isnan, \_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)   
 [fpclassify](../../c-runtime-library/reference/fpclassify.md)