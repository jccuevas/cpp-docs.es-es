---
title: "Advertencia del compilador (nivel 1) C4743 | Microsoft Docs"
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
  - "C4743"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4743"
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4743
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'*type*' tiene un tamaño diferente en '*file1*' y '*file2*': *number* y bytes de *number*  
  
 Una variable externa a la que se hace referencia o definida en dos archivos tiene diferente alineación en dichos archivos, y el compilador determinó que el tamaño de la variable en *file1* difiere del tamaño de la variable en *file2*.  
  
 Es importante cuando esta advertencia se puede emitir para C\+\+.  Si declara los mismos tipos con el mismo nombre en dos archivos distintos, si estas declaraciones contienen funciones virtuales y si las declaraciones no coinciden, el compilador puede emitir la advertencia C4744 para las tablas de funciones virtuales.  La advertencia se produce porque hay dos tablas de funciones virtuales con distintos tamaños para el mismo tipo, y el vinculador debe elegir una de ellas para incorporarla al ejecutable.  Es posible que esto pueda provocar que el programa llame a la función virtual equivocada.  
  
 Para resolver esta advertencia, utilice la misma definición de tipo o use nombres diferentes para los tipos o variables.  
  
## Ejemplo  
 Este ejemplo contiene una definición del tipo.  
  
```  
// C4743a.cpp  
// compile with: /c  
class C {  
public:  
    virtual void f1(void);  
    virtual void f2(void);  
    virtual void f3(void);  
};  
  
void C::f1(void) {}  
void C::f2(void) {}  
void C::f3(void) {}  
C q;  
```  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4743.  
  
```  
// C4743b.cpp  
// compile with: C4743a.cpp /W1 /GL /O2  
// C4743 expected  
class C {  
public:  
    virtual void f1(void);  
    virtual void f2(void);  
    virtual void f3(void);  
    virtual void f4(void);  
    virtual void f5(void);  
};  
  
void C::f4(void) {}  
void C::f5(void) {}  
C x;  
  
int main() {}   
```