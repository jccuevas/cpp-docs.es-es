---
title: "Advertencia del compilador (nivel 4) C4625 | Microsoft Docs"
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
  - "C4625"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4625"
ms.assetid: 4cc99e50-846c-4784-97da-48b977067851
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4625
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'derived class': el constructor de copias se definió implícitamente como eliminado porque un constructor de copias de clase base es inaccesible o se ha eliminado  
  
 Se eliminó un constructor de copias o no está accesible en una clase base y, por tanto, no se generó para una clase derivada.  Cualquier intento de copiar un objeto de este tipo provocará un error del compilador.  
  
 De forma predeterminada, esta advertencia está desactivada.  Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.  
  
## Ejemplo  
 El siguiente ejemplo genera el error C4625 y muestra cómo corregirlo.  
  
```  
// C4625.cpp  
// compile with: /W4 /c  
#pragma warning(default : 4625)  
  
struct A {  
   A() {}  
  
private:  
   A(const A&) {}  
};  
  
struct C : private virtual A {};  
struct B :  C {};   // C4625 no copy constructor  
  
struct D : A {};  
struct E :  D {};   // OK  
```