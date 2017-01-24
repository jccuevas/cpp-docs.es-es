---
title: "C&#243;mo: Solicitar expl&#237;citamente la conversi&#243;n boxing | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "boxing (conversión), solicitar explícitamente"
ms.assetid: 1359e6e5-162d-4f5d-9b6a-1690d93df3ee
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Solicitar expl&#237;citamente la conversi&#243;n boxing
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede aplicar explícitamente la conversión boxing asignando una variable a una variable de `Object`escrito.  
  
## Ejemplo  
  
```  
// vcmcppv2_explicit_boxing3.cpp  
// compile with: /clr  
using namespace System;  
  
void f(int i) {  
   Console::WriteLine("f(int i)");  
}  
  
void f(Object ^o) {  
   Console::WriteLine("f(Object^ o)");  
}  
  
int main() {  
   int i = 5;  
   Object ^ O = i;   // forces i to be boxed  
   f(i);  
   f(O);  
   f( (Object^)i );  // boxes i  
}  
```  
  
  **f \(int i\)**  
**f \(Object^ o\)**  
**f \(Object^ o\)**   
## Vea también  
 [Conversión boxing](../windows/boxing-cpp-component-extensions.md)