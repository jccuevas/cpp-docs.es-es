---
title: "Error del compilador C2061 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2061"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2061"
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Error del compilador C2061
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

error de sintaxis : identificador 'identificador'  
  
 El compilador ha encontrado un identificador donde no se esperaba.  Asegúrese de que se declara `identifier` antes de utilizarlo.  
  
 Los inicializadores pueden aparecer entre paréntesis.  Para evitar este problema, escriba el declarador entre paréntesis o conviértalo en un tipo `typedef`.  
  
 También puede producirse este error cuando el compilador detecta una expresión como un argumento de plantilla de clase; utilice [typename](../../cpp/typename.md) para indicar al compilador que se trata de un tipo.  
  
 El código siguiente genera el error C2061:  
  
```  
// C2061.cpp  
// compile with: /c  
template < A a >   // C2061  
// try the following line instead  
// template < typename b >  
class c{};  
```  
  
 C2061 puede aparecer si pasa un nombre de instancia a [typeid](../Topic/typeid%20%20\(C++%20Component%20Extensions\).md):  
  
```  
// C2061b.cpp  
// compile with: /clr  
ref struct G {  
   int i;  
};  
  
int main() {  
   G ^ pG = gcnew G;  
   System::Type ^ pType = typeid<pG>;   // C2061  
   System::Type ^ pType2 = typeid<G>;   // OK  
}  
```