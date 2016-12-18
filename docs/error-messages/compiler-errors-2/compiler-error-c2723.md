---
title: "Error del compilador C2723 | Microsoft Docs"
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
  - "C2723"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2723"
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2723
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': el especificador 'specifier' no es válido en la definición de función  
  
 El especificador no puede aparecer con una definición de función fuera de una declaración de clase.  El especificador `virtual` se puede especificar únicamente en una declaración de función miembro dentro de una declaración de clase.  
  
 El ejemplo siguiente genera el error C2723 y muestra cómo corregirlo:  
  
```  
// C2723.cpp  
struct X {  
   virtual void f();  
   virtual void g();  
};  
  
virtual void X::f() {}   // C2723  
  
// try the following line instead  
void X::g() {}  
```