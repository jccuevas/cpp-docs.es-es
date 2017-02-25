---
title: "Error irrecuperable C1094 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1094"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1094"
ms.assetid: 9e1193b2-cb95-44f9-bf6f-019e0d41dd97
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error irrecuperable C1094
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\-Zmval1' : la opción de la línea de comandos no es coherente con el valor utilizado para compilar el encabezado precompilado \('\-Zmval2'\)  
  
 El valor pasado a [\/Yc](../../build/reference/yc-create-precompiled-header-file.md) debe tener el mismo valor que el que se pasa a [\/Yu](../../build/reference/yu-use-precompiled-header-file.md) \(**\/Zm** los valores deben ser iguales para todas las compilaciones que usan o crean el mismo archivo de encabezado precompilado\).  
  
 El código siguiente genera el error C1094:  
  
```  
// C1094.h  
int func1();  
```  
  
 Y, a continuación,  
  
```  
// C1094.cpp  
// compile with: /Yc"C1094.h" /Zm200  
int u;  
int main() {  
   int sd = 32;  
}  
#include "C1094.h"  
```  
  
 Y, a continuación,  
  
```  
// C1094b.cpp  
// compile with: /Yu"C1094.h" /Zm300 /c  
#include "C1094.h"   // C1094 compile with /Zm200  
void Test() {}  
```