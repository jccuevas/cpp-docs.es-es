---
title: "Error del compilador C2505 | Microsoft Docs"
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
  - "C2505"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2505"
ms.assetid: b19f5c53-399d-425e-90db-fe3ca9b40858
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2505
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'símbolo' : '\_\_declspec \(modifer\)' solamente se puede aplicar a declaraciones o definiciones de objetos globales o miembros de datos estáticos  
  
 Un modificador `__declspec` diseñado para ser usado sólo en el ámbito global se utilizó en una función.  
  
 Para obtener más información, vea [appdomain](../../cpp/appdomain.md) y [proceso](../../cpp/process.md).  
  
 El código siguiente genera el error C2505:  
  
```  
// C2505.cpp  
// compile with: /clr  
  
// OK  
__declspec(process) int ii;  
__declspec(appdomain) int jj;  
  
int main() {  
   __declspec(process) int i;   // C2505  
   __declspec(appdomain) int j;   // C2505  
}  
```