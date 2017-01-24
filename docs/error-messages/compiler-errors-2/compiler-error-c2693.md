---
title: "Error del compilador C2693 | Microsoft Docs"
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
  - "C2693"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2693"
ms.assetid: b7364ca8-b6be-48c0-97d6-6029787fb171
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2693
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operador' : comparación no válida de referencias a una matriz administrada o de WinRT  
  
 No puede probar una matriz administrada o de WinRT para cualquier clase de desigualdad.  Por ejemplo, puede realizar una prueba para ver si las matrices administradas son iguales, pero no para ver si una matriz es mayor o menor que otra.  
  
 **Extensiones administradas de C\+\+**  
  
 No puede probar una matriz de [\_\_gc](../../misc/gc.md) para cualquier clase de desigualdad.  Por ejemplo, puede realizar una prueba para ver si las matrices administradas son iguales, pero no para ver si una matriz es mayor o menor que otra.  
  
 El siguiente ejemplo genera el error C2693:  
  
```  
// C2693b.cpp  
// compile with: /clr:oldSyntax /c  
#using <mscorlib.dll>  
int func3(int a __gc[], int b __gc[]) {  
   return a < b;    // C2693  
}  
int func1(int a __gc[], int b __gc[]) {  
   return a != b;   // OK  
}  
  
int func2(int a __gc[], int b __gc[]) {  
   return a == b;   // OK  
}  
```