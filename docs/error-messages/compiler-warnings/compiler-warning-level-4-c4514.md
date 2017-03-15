---
title: "Advertencia del compilador (nivel 4) C4514 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4514"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4514"
ms.assetid: cdae966a-9cd4-4e31-af30-2a014e68f614
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 4) C4514
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función': se ha quitado una función inline a la que no se hace referencia  
  
 El optimizador quitó una función inline a la que no se llamaba.  
  
 De forma predeterminada, esta advertencia está desactivada.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 El código siguiente genera el error C4514:  
  
```  
// C4514.cpp  
// compile with: /W4  
#pragma warning(default : 4514)  
class A  
{  
   public:  
      void func()   // C4514, remove the function to resolve  
      {  
      }  
};  
  
int main()  
{  
}  
```