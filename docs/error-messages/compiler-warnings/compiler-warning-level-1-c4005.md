---
title: "Advertencia del compilador (nivel 1) C4005 | Microsoft Docs"
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
  - "C4005"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4005"
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4005
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : redefinición de macro  
  
 Se ha definido dos veces el identificador de macro.  El compilador utilizó la segunda definición de macro.  
  
### Posibles causas del error:  
  
1.  Definir una macro en la línea de comandos y en el código con una directiva `#define`.  
  
2.  Macros importadas de archivos de inclusión.  
  
### Se corrige mediante algunas de las siguientes posibles soluciones  
  
1.  Quite una de las definiciones.  
  
2.  Utilice una directiva [\#undef](../../preprocessor/hash-undef-directive-c-cpp.md) antes de la segunda definición.  
  
 El código siguiente genera el error C4005:  
  
```  
// C4005.cpp  
// compile with: /W1 /EHsc  
#include <iostream>  
using namespace std;  
  
#define TEST "test1"  
#define TEST "test2"   // C4005 delete or rename to resolve the warning  
  
int main() {  
   cout << TEST << endl;  
}  
```