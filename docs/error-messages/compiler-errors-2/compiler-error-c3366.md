---
title: "Error del compilador C3366 | Microsoft Docs"
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
  - "C3366"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3366"
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3366
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'variable': los miembros de datos estáticos de los tipos WinRT o administrados deben definirse en la definición de clase  
  
 Ha intentado hacer referencia a un miembro estático de una clase o interfaz .NET o WinRT fuera de la definición de esa clase o interfaz.  
  
 El compilador necesita conocer la definición completa de la clase \(para emitir los metadatos después de un paso\) y requiere que los miembros de datos estáticos se inicialicen en la clase.  
  
 Por ejemplo, en el ejemplo siguiente se genera el error C3366 y se muestra cómo corregirlo:  
  
```  
// C3366.cpp  
// compile with: /clr /c  
ref class X {  
   public:  
   static int i;   // initialize i here to avoid C3366  
};  
  
int X::i = 5;      // C3366  
```  
  
 En el ejemplo siguiente se genera el error C3366 y se muestra cómo corregirlo:  
  
```  
// C3366_b.cpp  
// compile with: /clr:oldSyntax /c  
__gc struct X {  
   static int i;   // initialize i here to avoid C3366  
};  
  
int X::i = 5;      // C3366  
```