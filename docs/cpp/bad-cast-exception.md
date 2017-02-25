---
title: "bad_cast (Excepci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "bad_cast"
  - "bad_cast_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bad_cast (palabra clave) [C++]"
  - "excepciones, bad_cast"
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# bad_cast (Excepci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El operador `dynamic_cast` inicia la excepción `bad_cast` como resultado de una conversión incorrecta a un tipo de referencia.  
  
## Sintaxis  
  
```  
catch (bad_cast)  
   statement  
```  
  
## Comentarios  
 La interfaz de `bad_cast` es:  
  
```  
class bad_cast : public exception {  
public:  
   bad_cast(const char * _Message = "bad cast");  
   bad_cast(const bad_cast &);  
   virtual ~bad_cast();  
};  
```  
  
 El código siguiente contiene un ejemplo de `dynamic_cast` con errores que inicia la excepción `bad_cast`.  
  
```  
// expre_bad_cast_Exception.cpp  
// compile with: /EHsc /GR  
#include <typeinfo.h>  
#include <iostream>  
  
class Shape {  
public:  
   virtual void virtualfunc() const {}  
};  
  
class Circle: public Shape {  
public:  
   virtual void virtualfunc() const {}  
};  
  
using namespace std;  
int main() {  
   Shape shape_instance;  
   Shape& ref_shape = shape_instance;  
   try {  
      Circle& ref_circle = dynamic_cast<Circle&>(ref_shape);   
   }  
   catch (bad_cast b) {  
      cout << "Caught: " << b.what();  
   }  
}  
```  
  
 Se inicia una excepción porque el objeto que se convierte \(una forma\) no se deriva del tipo de conversión especificado \(Circle\).  Para evitar la excepción, agregue estas declaraciones a `main`:  
  
```  
Circle circle_instance;  
Circle& ref_circle = circle_instance;  
```  
  
 A continuación, invierta el sentido de la conversión en el bloque `try`, como sigue:  
  
```  
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);  
```  
  
## Vea también  
 [dynamic\_cast \(Operador\)](../cpp/dynamic-cast-operator.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [Control de excepciones de C\+\+](../cpp/cpp-exception-handling.md)