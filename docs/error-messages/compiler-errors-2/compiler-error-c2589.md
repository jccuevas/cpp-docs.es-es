---
title: "Error del compilador C2589 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2589"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2589"
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2589
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : símbolo \(token\) no válido en el lado derecho de '::'  
  
 Si un nombre de clase, estructura o unión aparece a la izquierda del operador de resolución de ámbito \(dos puntos dobles\), el token de la derecha debe ser un miembro de clase, estructura o unión.  En caso contrario, puede aparecer a la derecha cualquier identificador global.  
  
 El operador de resolución de ámbito no puede sobrecargarse.  
  
 El código siguiente genera el error C2589:  
  
```  
// C2589.cpp  
void Test(){}  
class A {};  
void operator :: ();   // C2589  
  
int main() {  
   ::Test();  
}  
```