---
title: "Error del compilador C2955 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2955"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2955"
ms.assetid: 77709fb6-d69b-46fd-a62f-e8564563d01b
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# Error del compilador C2955
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador': el uso de la plantilla de clase o el alias genérico requiere una lista de plantillas o de argumentos genéricos  
  
 No puede usar una plantilla de clase o de clase genérica como identificador sin una lista de plantillas o de argumentos genéricos.  
  
 Para más información, vea [Plantillas de clase](../../cpp/class-templates.md).  
  
 El ejemplo siguiente genera el error C2955 y muestra cómo corregirlo.  
  
```  
// C2955.cpp  
// compile with: /c  
template<class T>   
class X {};  
  
X x1;   // C2955  
X<int> x2;   // OK - this is how to fix it.  
```  
  
 El error C2955 también se puede producir al intentar efectuar una definición fuera de línea para una función declarada en una plantilla de clase:  
  
```  
// C2955_b.cpp  
// compile with: /c  
template <class T>  
class CT {  
public:  
   void CTFunc();  
   void CTFunc2();  
};  
  
void CT::CTFunc() {}   // C2955  
  
// OK - this is how to fix it  
template <class T>  
void CT<T>::CTFunc2() {}  
  
```  
  
 También se puede producir el error C2955 al usar genéricos:  
  
```  
// C2955_c.cpp  
// compile with: /clr  
generic <class T>   
ref struct GC {   
   T t;  
};  
  
int main() {  
   GC^ g;   // C2955  
   GC <int>^ g;  
}  
```