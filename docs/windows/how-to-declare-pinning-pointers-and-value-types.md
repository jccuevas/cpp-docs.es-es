---
title: "C&#243;mo: Declarar punteros anclados y tipos de valor | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fijar punteros"
  - "tipos de valor, declarar"
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Declarar punteros anclados y tipos de valor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un tipo de valor puede aplicar la conversión boxing implícita.  Puede declarar un puntero anclado al objeto del propio tipo de y utilizar **pin\_ptr** al tipo de valor de conversión boxing.  
  
## Ejemplo  
  
### Código  
  
```  
// pin_ptr_value.cpp  
// compile with: /clr  
value struct V {  
   int i;  
};  
  
int main() {  
   V ^ v = gcnew V;   // imnplicit boxing  
   v->i=8;  
   System::Console::WriteLine(v->i);  
   pin_ptr<V> mv = &*v;  
   mv->i = 7;  
   System::Console::WriteLine(v->i);  
   System::Console::WriteLine(mv->i);  
}  
```  
  
### Resultados  
  
```  
8  
7  
7  
```  
  
## Vea también  
 [pin\_ptr \(C\+\+\/CLI\)](../Topic/pin_ptr%20\(C++-CLI\).md)