---
title: "Compiler Error C3252 | Microsoft Docs"
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
  - "C3252"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3252"
ms.assetid: aa9ad096-e9ac-41c7-8ad9-b966751c7c75
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compiler Error C3252
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'método': no se puede reducir la accesibilidad de un método virtual en un tipo administrado o WinRT  
  
 Una clase que implementa un método virtual de una clase base o cualquier método de una interfaz no puede reducir el acceso a ese método.  
  
 Tenga en cuenta que todos los métodos de una interfaz son públicos.  
  
 En el ejemplo siguiente se genera el error C3252 y se muestra cómo corregirlo.  
  
```  
// C3252.cpp  
// compile with: /clr /c  
ref class A {  
public:  
   virtual void f1() {}  
};  
  
ref class B : public A {  
// To fix, uncomment the following line:   
// public:      
   virtual void f1() override sealed {}   // C3252, make this method public  
};  
```