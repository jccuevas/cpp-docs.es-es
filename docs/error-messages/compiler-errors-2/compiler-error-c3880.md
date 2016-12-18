---
title: "Error del compilador C3880 | Microsoft Docs"
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
  - "C3880"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3880"
ms.assetid: b0e05d1e-32d0-4034-9246-f37d23573ea9
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3880
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' : no puede ser un miembro de datos literal  
  
 El tipo de un atributo [literal](../../windows/literal-cpp-component-extensions.md) debe ser uno de los tipos siguientes \(convertible en tiempo de compilación\):  
  
-   tipo entero  
  
-   string  
  
-   enumeración con un tipo integral o subyacente  
  
 El código siguiente genera el error C3880:  
  
```  
// C3880.cpp  
// compile with: /clr /c  
ref struct Y1 {  
   literal System::Decimal staticConst1 = 10;   // C3880  
   literal int staticConst2 = 10;   // OK  
};  
```