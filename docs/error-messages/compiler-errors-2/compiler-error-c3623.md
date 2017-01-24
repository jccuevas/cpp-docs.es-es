---
title: "Error del compilador C3623 | Microsoft Docs"
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
  - "C3623"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3623"
ms.assetid: a0341b45-062a-4f67-beb9-ba74201ed1ed
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3623
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'variable': no se admiten campos de bits en los tipos WinRT o administrados  
  
 No se permite el uso de campos de bits en variables de tipo administrado o clase de WinRT.  
  
 El ejemplo siguiente genera el error C3623:  
  
```  
// C3623.cpp  
// compile with: /clr  
using namespace System;  
ref class CMyClass {  
public:  
   int i : 1;   // C3623  
};  
  
int main() {  
   CMyClass^ pMyClass = gcnew CMyClass();  
   pMyClass->i = 3;  
   Console::Out->WriteLine(pMyClass->i);  
}  
```  
  
 El ejemplo siguiente genera el error C3623:  
  
```  
// C3623_2.cpp  
// compile with: /clr:oldSyntax  
using namespace System;  
__gc class CMyClass {  
   public:  
      int i : 1;   // C3623  
};  
  
int main() {  
   CMyClass *pMyClass = new CMyClass();  
   pMyClass->i = 3;  
   Console::Out->WriteLine(pMyClass->i);  
}  
```