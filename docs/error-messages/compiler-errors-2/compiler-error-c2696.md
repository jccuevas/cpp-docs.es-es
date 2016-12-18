---
title: "Error del compilador C2696 | Microsoft Docs"
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
  - "C2696"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2696"
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2696
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

No se puede crear un objeto temporal de un tipo administrado 'tipo'  
  
 Las referencias a `const` en un programa no administrado hacen que el compilador llame al constructor y cree un objeto temporal en la pila.  Sin embargo, nunca se puede crear una clase administrada en la pila.  
  
 Sólo se puede reproducir el error C2696 utilizando **\/clr:oldSyntax**.  
  
 El código siguiente genera el error C2696:  
  
```  
// C2696b.cpp  
// compile with: /clr:oldSyntax  
  
__gc class G {  
public:  
   G( int i ) {}  
};  
  
void func( const G& g );  
  
int main() {  
   func( 1 );   // C2696  
   G *myG = new G( 1 );   // OK  
   func( *myG );  
}  
```