---
title: "Conversiones est&#225;ndar y conversi&#243;n boxing impl&#237;cita | Microsoft Docs"
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
  - "boxing (conversión), implícita"
ms.assetid: 33f7fc7d-5674-44a2-a859-0e6a04fae519
caps.latest.revision: 6
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conversiones est&#225;ndar y conversi&#243;n boxing impl&#237;cita
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una conversión estándar se elegida por el compilador sobre una conversión que requiere la conversión boxing.  
  
## Ejemplo  
  
```  
// clr_implicit_boxing_Std_conversion.cpp  
// compile with: /clr  
int f3(int ^ i) {   // requires boxing  
   return 1;  
}  
  
int f3(char c) {   // no boxing required, standard conversion  
   return 2;  
}  
  
int main() {  
   int i = 5;  
   System::Console::WriteLine(f3(i));  
}  
```  
  
 **2**   
## Vea también  
 [Conversión boxing](../windows/boxing-cpp-component-extensions.md)