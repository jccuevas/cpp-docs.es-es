---
title: "Error del compilador C2675 | Microsoft Docs"
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
  - "C2675"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2675"
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2675
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operador' unario : 'tipo' no define este operador o una conversión a un tipo aceptable para el operador predefinido  
  
 También puede producirse el error C2675 cuando se utiliza un operador unario y el tipo no define el operador o una conversión a un tipo aceptable para el operador predefinido.  Para usar este operador, debe sobrecargarlo para el tipo especificado o definir una conversión a un tipo para el que esté definido el operador.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2675.  
  
```  
// C2675.cpp  
struct C {   
   C(){}  
} c;  
  
struct D {   
   D(){}  
   void operator-(){}  
} d;  
  
int main() {  
   -c;   // C2675  
   -d;   // OK  
}  
```