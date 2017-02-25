---
title: "Advertencia del compilador (nivel 1) C4393 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4393"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4393"
ms.assetid: 353a0539-d1ea-4c1b-8849-c9b321ec9842
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Advertencia del compilador (nivel 1) C4393
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' : const no tiene efecto en el miembro de datos literal; se pasará por alto  
  
 Se especificó un miembro de datos de [literal](../../windows/literal-cpp-component-extensions.md) también como const.  Puesto que un miembro de datos literal implica const, no necesita agregar const a la declaración.  
  
 El código siguiente genera el error C4393:  
  
```  
// C4393.cpp  
// compile with: /clr /W1 /c  
ref struct Y1 {  
   literal const int staticConst = 10;   // C4393  
   literal int staticConst2 = 10;   // OK  
};  
```