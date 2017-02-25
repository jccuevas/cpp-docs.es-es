---
title: "Advertencia del compilador (nivel 1) C4353 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4353"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4353"
ms.assetid: 6e79f186-ed82-4c95-9923-0ad5bb9c4db1
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 1) C4353
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se ha utilizado una extensión no estándar: constante 0 como expresión de función.Utilice en su lugar la función intrínseca '\_\_noop'  
  
 No se puede utilizar la constante cero \(0\) como expresión de función.  Para obtener más información, vea [\_\_noop](../../intrinsics/noop.md).  
  
 El código siguiente genera el error C4353:  
  
```  
// C4353.cpp  
// compile with: /W1  
void MyPrintf(void){};  
#define X 0  
#if X  
   #define DBPRINT MyPrint  
#else  
   #define DBPRINT 0   // C4353 expected  
#endif  
int main(){  
DBPRINT();  
}  
```