---
title: "bad_cast (excepción) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bad_cast
- bad_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- exceptions [C++], bad_cast
- bad_cast keyword [C++]
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d7880a01f247d5dc3cce5a6f247297ef65289367
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="badcast-exception"></a>bad_cast (Excepción)
El operador `bad_cast` inicia la excepción `dynamic_cast` como resultado de una conversión incorrecta a un tipo de referencia.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
catch (bad_cast)  
   statement  
```  
  
## <a name="remarks"></a>Comentarios  
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
  
 Se inicia una excepción porque el objeto que se convierte (una forma) no se deriva del tipo de conversión especificado (Circle). Para evitar la excepción, agregue estas declaraciones a `main`:  
  
```  
Circle circle_instance;  
Circle& ref_circle = circle_instance;  
```  
  
 A continuación, invierta el sentido de la conversión en el bloque `try`, como sigue:  
  
```  
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);  
```  
  
## <a name="see-also"></a>Vea también  
 [dynamic_cast (operador)](../cpp/dynamic-cast-operator.md)   
 [Palabras clave](../cpp/keywords-cpp.md)   
 [Control de excepciones de C++](../cpp/cpp-exception-handling.md)