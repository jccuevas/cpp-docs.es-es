---
title: "Advertencia del compilador (nivel 1) C4572 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4572"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4572"
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 1) C4572
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El atributo \[ParamArray\] está desusado en \/clr; use '...' en su lugar  
  
 Se ha utilizado un estilo obsoleto para especificar una lista de argumentos de variable.  Al compilar para CLR, utilice la sintaxis de puntos suspensivos en lugar de <xref:System.ParamArrayAttribute>.  Para obtener más información, vea [Listas de argumentos de variables \(...\) \(C\+\+\/CLI\)](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4572.  
  
```  
// C4572.cpp  
// compile with: /clr /W1  
void Func([System::ParamArray] array<int> ^);   // C4572  
void Func2(... array<int> ^){}   // OK  
  
int main() {  
   Func2(1, 2, 3);  
}  
```