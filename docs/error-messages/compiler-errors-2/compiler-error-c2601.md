---
title: "Error del compilador C2601 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2601"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2601"
ms.assetid: 88275582-5f37-45d7-807d-05f06ba00965
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2601
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : las definiciones de funciones locales no son válidas  
  
 El código intenta definir una función dentro de otra función.  
  
 O bien, puede que haya una llave extra en el código fuente antes de la ubicación del error C2601.  
  
 El código siguiente genera el error C2601:  
  
```  
// C2601.cpp  
int main() {  
   int i = 0;  
  
   void funcname(int j) {   // C2601  
      j++;  
   }  
}  
```