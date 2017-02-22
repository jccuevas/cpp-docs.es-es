---
title: "TRUNC, truncf, truncl | Microsoft Docs"
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
  - "trunc"
  - "truncf"
  - "truncl"
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
  - "trunc"
  - "truncf"
  - "truncl"
  - "math/trunc"
  - "math/truncf"
  - "math/truncl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "trunc (función)"
  - "truncf (función)"
  - "truncl (función)"
ms.assetid: de2038ac-ac0b-483e-870c-e8992dcd4fd0
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# TRUNC, truncf, truncl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina el entero más cercano que es menor o igual que el valor de punto flotante especificado.  
  
## Sintaxis  
  
```  
double trunc(  
   double x  
);  
  
float trunc(  
   float x  
); //C++ only  
  
long double trunc(  
   long double x  
); //C++ only  
  
float trunc(  
   float x  
); //C++ only  
  
long double truncl(  
   long double x  
);  
  
```  
  
#### Parámetros  
 \[in\] `x`  
 El valor que se va a truncar.  
  
## Valor devuelto  
 Si se realiza correctamente, devuelve un valor entero de `x`, redondeados hacia cero.  
  
 De lo contrario, puede devolver uno de los siguientes:  
  
|Problema|Volver|  
|--------------|------------|  
|`x` \= ±INFINITY|x|  
|`x` \=  ±0|x|  
|`x` \= NaN|NaN|  
  
 Los errores se notifican como se especifica en [\_matherr](../../c-runtime-library/reference/matherr.md).  
  
## Comentarios  
 Como C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `trunc` que toman y devuelven los tipos float y double de tiempo. En un programa de C, `trunc` siempre toma y devuelve un tipo double.  
  
 Dado que los valores de punto flotante más grandes son enteros exactas, esta función no se desborde por sí mismo. Sin embargo, puede hacer que la función desborde devolviendo un valor en un tipo entero.  
  
 También se puede redondear hacia abajo mediante la conversión implícita de punto flotante a entero; Sin embargo, hacer esto es limitado a los valores que pueden almacenarse en el tipo de destino.  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`trunc`, `truncf`,  `truncl`|\<math.h\>|\<cmath\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [floor, floorf, floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [ceil, ceilf, ceill](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [round, roundf, roundl](../../c-runtime-library/reference/round-roundf-roundl.md)