---
title: "bad_typeid (Excepci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "bad_typeid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bad_typeid (excepción)"
  - "excepciones, bad_typeid"
ms.assetid: 5963ed58-4ede-4597-957d-f7bbd06299c2
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# bad_typeid (Excepci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La excepción `bad_typeid` la produce el [operador typeid](../cpp/typeid-operator.md) cuando el operando de `typeid` es un puntero NULL.  
  
## Sintaxis  
  
```  
  
      catch (bad_typeid)  
   statement  
```  
  
## Comentarios  
 La interfaz de `bad_typeid` es:  
  
```  
class bad_typeid : public exception  
{  
public:  
   bad_typeid(const char * _Message = "bad typeid");  
   bad_typeid(const bad_typeid &);  
   virtual ~bad_typeid();  
};  
```  
  
 En el ejemplo siguiente se muestra el operador `typeid` que produce una excepción `bad_typeid`.  
  
```  
// expre_bad_typeid.cpp  
// compile with: /EHsc /GR  
#include <typeinfo.h>  
#include <iostream>  
  
class A{  
public:  
   // object for class needs vtable  
   // for RTTI  
   virtual ~A();  
};  
  
using namespace std;  
int main() {  
A* a = NULL;  
  
try {  
   cout << typeid(*a).name() << endl;  // Error condition  
   }  
catch (bad_typeid){  
   cout << "Object is NULL" << endl;  
   }  
}  
```  
  
## Salida  
  
```  
Object is NULL  
```  
  
## Vea también  
 [Información de tipos en tiempo de ejecución](../cpp/run-time-type-information.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)