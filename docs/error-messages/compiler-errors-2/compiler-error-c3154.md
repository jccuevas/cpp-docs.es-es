---
title: "Error del compilador C3154 | Microsoft Docs"
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
  - "C3154"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3154"
ms.assetid: 78005c74-eaaf-4ac2-88ae-6c25d01a302a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3154
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se esperaba ',' antes de los puntos suspensivos.No se admiten puntos suspensivos separados por valores que no sean coma en funciones de matriz.  
  
 No se declaró ninguna función de argumento variable correctamente.  
  
 Para obtener más información, vea [Listas de argumentos de variables \(...\) \(C\+\+\/CLI\)](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3154.  
  
```  
// C3154.cpp  
// compile with: /clr  
ref struct R {  
   void Func(int ... array<int> ^);   // C3154  
   void Func2(int i, ... array<int> ^){}   // OK  
   void Func3(array<int> ^){}   // OK  
   void Func4(... array<int> ^){}   // OK  
};  
  
int main() {  
   R ^ r = gcnew R;  
   r->Func4(1,2,3);  
}  
```