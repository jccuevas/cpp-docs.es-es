---
title: Compilador advertencia (nivel 1) C4743 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4743
dev_langs:
- C++
helpviewer_keywords:
- C4743
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1a7169afdf7fb4c9a03e509f0332e738a66a06f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4743"></a>Advertencia del compilador (nivel 1) C4743
'*tipo*'tiene un tamaño diferente '*file1*'y'*archivo2*': *número* y *número* bytes  
  
 Una variable externa al que hace referencia o definida en dos archivos tiene distintos tipos en dichos archivos, y el compilador ha determinado que el tamaño de la variable en *file1* difiere del tamaño de la variable en *archivo2*.  
  
 Es importante cuando esta advertencia se puede emitir para C++. Si declara los mismos tipos con el mismo nombre en dos archivos distintos, si estas declaraciones contienen funciones virtuales y si las declaraciones no son iguales, el compilador puede emitir la advertencia C4744 para las tablas de funciones virtuales. La advertencia se produce porque hay dos tablas de función virtual a un tamaño diferente para el mismo tipo y el vinculador debe elegir uno de ellos para incorporar en el archivo ejecutable.  Es posible que esto puede producir en el programa llama a la función virtual incorrecta.  
  
 Para resolver esta advertencia, utilice la misma definición de tipo o use nombres diferentes para los tipos o variables.  
  
## <a name="example"></a>Ejemplo  
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
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4743.  
  
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