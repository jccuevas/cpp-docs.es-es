---
title: "Error del compilador C2673 | Microsoft Docs"
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
  - "C2673"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2673"
ms.assetid: 780230c0-619b-4a78-b01d-ff5886306741
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2673
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : las funciones globales no tienen punteros 'this'  
  
 Una función global intentó obtener acceso a `this`.  
  
 El código siguiente genera el error C2673:  
  
```  
// C2673.cpp  
int main() {  
   this = 0;   // C2673  
}  
```