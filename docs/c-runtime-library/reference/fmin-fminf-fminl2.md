---
title: "Fmin, fminf, fminl | Microsoft Docs"
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
  - "fmin"
  - "fminf"
  - "fminl"
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
  - "fmin"
  - "fminf"
  - "fminl"
  - "math/fmin"
  - "math/fminf"
  - "math/fminl"
helpviewer_keywords: 
  - "fmin (función)"
  - "fminf (función)"
  - "fminl (función)"
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Fmin, fminf, fminl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina el menor de los dos valores especificados.  
  
## Sintaxis  
  
```  
double fmin(  
   double x,   
   double y  
);  
  
float fmin(  
   float x,   
   float y  
); //C++ only  
  
long double fmin(  
   long double x,   
   long double y  
); //C++ only  
  
float fminf(  
   float x,   
   float y  
);  
  
long double fminl(  
   long double x,   
   long double y  
);  
  
```  
  
#### Parámetros  
 `x`  
 Primer valor que se va a comparar.  
  
 `y`  
 Segundo valor que se va a comparar.  
  
## Valor devuelto  
 Si se realiza correctamente, devuelve el menor de `x` o `y`.  
  
|Entrada|Resultado|  
|-------------|---------------|  
|`x` es NaN|`y`|  
|`y` es NaN|`x`|  
|`x` y `y` son NaN|NaN|  
  
 No hace que la función [\_matherr](../../c-runtime-library/reference/matherr.md) para que se invoca, hacer que las excepciones de punto flotante o cambie el valor de `errno`.  
  
## Comentarios  
 Como C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `fmin` que toman y devuelven los tipos float y double de tiempo. En un programa de C, `fmin` siempre toma y devuelve un tipo double.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`fmin`, `fminf`,  `fminl`|C: \< math.h \><br /><br /> C\+\+: \< math.h \> o \< cmath \>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)