---
title: "C&#243;mo: Aplicar la conversi&#243;n unboxing | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unboxing (conversión)"
ms.assetid: 75794696-9275-47bf-9a7d-5abe6585ab91
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# C&#243;mo: Aplicar la conversi&#243;n unboxing
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Muestra cómo unbox y modificar un valor.  
  
## Ejemplo  
  
```  
// vcmcppv2_unboxing.cpp  
// compile with: /clr  
using namespace System;  
  
int main() {  
   int ^ i = gcnew int(13);  
   int j;  
   Console::WriteLine(*i);   // unboxing  
   *i = 14;   // unboxing and assignment  
   Console::WriteLine(*i);  
   j = safe_cast<int>(i);   // unboxing and assignment  
   Console::WriteLine(j);  
}  
```  
  
  **13**  
**14**  
**14**   
## Vea también  
 [Conversión boxing](../windows/boxing-cpp-component-extensions.md)