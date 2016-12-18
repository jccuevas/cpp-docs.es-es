---
title: "Error del compilador C3532 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3532"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3532"
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3532
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"tipo": uso incorrecto de "auto"  
  
 El tipo indicado no se puede declarar con la palabra clave `auto`.  Por ejemplo, no se puede usar la palabra clave `auto` para declarar una matriz o un tipo de valor devuelto por un método.  
  
### Para corregir este error  
  
1.  Asegúrese de que la expresión de inicialización genera un tipo válido.  
  
2.  Asegúrese de no declarar un matriz o un tipo de valor devuelto por un método.  
  
## Ejemplo  
 En el ejemplo siguiente se genera el error C3532 porque la palabra clave `auto` no puede declarar un tipo de valor devuelto por un método.  
  
```  
// C3532a.cpp  
// Compile with /Zc:auto  
auto f(){}   // C3532  
```  
  
## Ejemplo  
 En el ejemplo siguiente se genera el error C3532 porque la palabra clave `auto` no puede declarar una matriz.  
  
```  
// C3532b.cpp  
// Compile with /Zc:auto  
int main()  
{  
   int x[5];  
   auto a[5];            // C3532  
   auto b[1][2];         // C3532  
   auto y[5] = x;        // C3532  
   auto z[] = {1, 2, 3}; // C3532  
   auto w[] = x;         // C3532  
   return 0;  
}  
```  
  
## Vea también  
 [auto \(Palabra clave\)](../../cpp/auto-keyword.md)