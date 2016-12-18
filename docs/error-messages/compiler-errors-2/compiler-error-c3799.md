---
title: "Error del compilador C3799 | Microsoft Docs"
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
  - "C3799"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3799"
ms.assetid: 336a2811-9370-4e6e-b03b-325bda470805
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3799
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la propiedad indizada no puede tener una lista de parámetros vacía  
  
 Se declaró incorrectamente una propiedad indizada.  Para obtener más información, vea [Cómo: Usar las propiedades indizadas](../../misc/how-to-use-indexed-properties.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3799.  
  
```  
// C3799.cpp  
// compile with: /clr /c  
ref struct C {  
   property int default[] {   // C3799  
   // try the following line instead  
   // property int default[int] {  
      int get(int index) { return 0; }  
      void set(int index, int value) {}  
   }  
};  
```