---
title: "Lvalues y rvalues | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "valores L"
  - "valores R"
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Lvalues y rvalues
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cada expresión de C\+\+ es un valor L o un valor R.  Un valor L hace referencia a un objeto que se conserva más allá de una sola expresión.  Puede considerar un valor L como un objeto que tiene nombre.  Todas las variables, incluidas las variables no modificables \(`const`\), son valores L.  Un valor R es un valor temporal que no se conserva más allá de la expresión que lo utiliza.  Para comprender mejor la diferencia entre valores L y valores R, considere el siguiente ejemplo:  
  
```  
// lvalues_and_rvalues1.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
int main()  
{  
   int x = 3 + 4;  
   cout << x << endl;  
}  
```  
  
 En este ejemplo, `x` es un valor L porque se conserva más allá de la expresión que lo define.  La expresión `3 + 4` es un valor R porque se evalúa como un valor temporal que no se conserva más allá de la expresión que lo define.  
  
 En el ejemplo siguiente se muestran varios usos correctos e incorrectos de valores L y valores R:  
  
```  
// lvalues_and_rvalues2.cpp  
int main()  
{  
   int i, j, *p;  
  
   // Correct usage: the variable i is an lvalue.  
   i = 7;  
  
   // Incorrect usage: The left operand must be an lvalue (C2106).  
   7 = i; // C2106  
   j * 4 = 7; // C2106  
  
   // Correct usage: the dereferenced pointer is an lvalue.  
   *p = i;   
  
   const int ci = 7;  
   // Incorrect usage: the variable is a non-modifiable lvalue (C3892).  
   ci = 9; // C3892  
  
   // Correct usage: the conditional operator returns an lvalue.  
   ((i < 3) ? i : j) = 7;  
}  
```  
  
> [!NOTE]
>  En los ejemplos de este tema se muestra el uso correcto e incorrecto cuando los operadores no están sobrecargados.  Si sobrecarga operadores, puede convertir una expresión tal como `j * 4` en un valor L.  
  
 Los términos *valor L* y *valor R* suelen utilizarse para referirse a referencias a objetos.  Para obtener más información sobre las referencias, vea [Declarador de referencia a un valor L: &](../cpp/lvalue-reference-declarator-amp.md) y [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## Vea también  
 [Conceptos básicos](../cpp/basic-concepts-cpp.md)   
 [Declarador de referencia a un valor L: &](../cpp/lvalue-reference-declarator-amp.md)   
 [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md)