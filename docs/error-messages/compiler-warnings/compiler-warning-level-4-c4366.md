---
title: "Advertencia del compilador (nivel 4) C4366 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4366"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4366"
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# Advertencia del compilador (nivel 4) C4366
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El resultado del operador 'operador' unario se puede desalinear  
  
 Si un miembro de una estructura se desalinea alguna vez debido al empaquetado, el compilador avisará cuando la dirección de ese miembro se asigne a un puntero alineado.  De forma predeterminada, todos los punteros están alineados.  
  
 Para solucionar el problema que origina la advertencia C4366, cambie la alineación de la estructura o declare el puntero con la palabra clave [\_\_unaligned](../../cpp/unaligned.md).  
  
 Para obtener más información, vea \_\_unaligned y [pack](../../preprocessor/pack.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4366.  
  
```  
// C4366.cpp  
// compile with: /W4 /c  
// processor: IPF x64  
#pragma pack(1)  
struct X {  
   short s1;  
   int s2;  
};  
  
int main() {  
   X x;  
   short * ps1 = &x.s1;   // OK  
   int * ps2 = &x.s2;   // C4366  
}  
```