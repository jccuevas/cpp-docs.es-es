---
title: "Error del compilador C2767 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2767"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2767"
ms.assetid: e8f84178-a160-4d71-a236-07e4fcc11e96
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Error del compilador C2767
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

administrado o incoherencia en la dimensión de la matriz de WinRT: se esperaban N argumentos N \- se proporcionaron M  
  
 Una declaración de matriz administrada o de WinRT estaba mal formada.  Para obtener más información, vea [array](../../windows/arrays-cpp-component-extensions.md).  
  
 El siguiente ejemplo genera el error C2767 y muestra cómo corregirlo:  
  
```  
// C2767.cpp  
// compile with: /clr  
int main() {  
   array<int> ^p1 = new array<int>(2,3); // C2767  
   array<int> ^p2 = new array<int>(2);   // OK  
}  
```