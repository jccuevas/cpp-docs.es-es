---
title: "Error del compilador C2784 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2784"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2784"
ms.assetid: 3d761fe2-881c-48bd-afae-e2e714e20473
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Error del compilador C2784
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'declaration' : no se pudo deducir el argumento de plantilla para 'type' de 'type'  
  
 El compilador no puede determinar un argumento de plantilla a partir de los argumentos de función proporcionados.  
  
 El siguiente ejemplo genera el error C2784 e indica cómo corregirlo:  
  
```  
// C2784.cpp  
template<class T> class X {};  
template<class T> void f(X<T>) {}  
  
int main() {  
   X<int> x;  
   f(1);   // C2784  
  
   // To fix it, try the following line instead  
   f(x);  
}  
```