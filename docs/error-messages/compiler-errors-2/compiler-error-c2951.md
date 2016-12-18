---
title: "Error del compilador C2951 | Microsoft Docs"
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
  - "C2951"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2951"
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2951
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

las declaraciones de tipos solo se permiten en un ámbito global, de espacio de nombres o de clase  
  
 No se puede declarar una clase genérica o de plantilla fuera del ámbito global o de espacio de nombres.  Si crea las declaraciones de plantilla o de genérico en un archivo de inclusión, asegúrese de que dicho archivo esté comprendido en el ámbito global.  
  
 El código siguiente genera el error C2951:  
  
```  
// C2951.cpp  
template <class T>  
class A {};  
  
int main() {  
   template <class T>   // C2951  
   class B {};  
}  
```  
  
 El error C2951 también puede producirse cuando se utilizan genéricos:  
  
```  
// C2951b.cpp  
// compile with: /clr /c  
  
// OK  
generic <class T>   
ref class GC { };  
  
int main() {  
   generic <class T> ref class GC2 {};   // C2951  
}  
```