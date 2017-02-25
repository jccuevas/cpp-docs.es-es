---
title: "Error del compilador C2748 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2748"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2748"
ms.assetid: b63ac78b-a200-499c-afea-15af1a1e819e
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Error del compilador C2748
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la creación de matrices administradas o WinRT debe disponer de un tamaño de matriz o un inicializador de matriz  
  
 Una matriz administrada o WinRT estaba mal formada.  Para obtener más información, vea [Matriz](../../windows/arrays-cpp-component-extensions.md).  
  
 El ejemplo siguiente genera el error C2748 y muestra cómo corregirlo:  
  
```  
// C2748.cpp  
// compile with: /clr  
int main() {  
   array<int> ^p1 = new array<int>();   // C2748  
   // try the following line instead  
   array<int> ^p2 = new array<int>(2);  
}  
```