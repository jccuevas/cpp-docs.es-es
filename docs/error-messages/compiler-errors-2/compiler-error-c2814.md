---
title: "Error del compilador C2814 | Microsoft Docs"
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
  - "C2814"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2814"
ms.assetid: 7d165136-a08b-4497-a76d-60a21bb19404
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2814
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'miembro': un tipo nativo no se puede anidar dentro de un 'tipo' administrado o WinRT  
  
## Ejemplo  
 Un tipo nativo no se puede anidar en un tipo CLR o WinRT.  El ejemplo siguiente genera el error C2814 y muestra cómo corregirlo.  
  
```  
// C2814.cpp  
// compile with: /clr /c  
ref class A {  
   class B {};   // C2814  
   ref class C {};   // OK  
};  
```  
  
## Ejemplo  
 Use las extensiones administradas de C\+\+ para especificar de forma explícita el carácter administrado de un tipo incrustado mediante una de las siguientes palabras clave: [\_\_gc](../../misc/gc.md), [\_\_nogc](../../misc/nogc.md) o [\_\_value](../../misc/value.md).  
  
 El ejemplo siguiente genera el error C2814 y muestra cómo corregirlo.  
  
```  
// C2814_b.cpp  
// compile with: /clr:oldSyntax /c  
__gc class A {  
   class B {};   // C2814  
   __gc class C {};   // OK  
};  
```