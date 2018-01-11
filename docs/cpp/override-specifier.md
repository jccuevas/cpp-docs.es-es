---
title: override (especificador) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 677a6a0e0107f3ed0d0dc402f36e9d6dd4505c7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="override-specifier"></a>override (especificador)
Puede usar la palabra clave `override` para indicar las funciones miembro que invalidan una función virtual en una clase base.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
function-declaration override;  
```  
  
## <a name="remarks"></a>Comentarios  
 `override` es contextual y tiene un significado especial solo cuando se utiliza después de una declaración de función miembro; de lo contrario, no es una palabra clave reservada.  
  
## <a name="example"></a>Ejemplo  
 Utilice `override` para evitar el comportamiento inadvertido de herencia en el código. En el ejemplo siguiente se muestra dónde puede no haberse previsto el comportamiento de la función miembro de clase derivada, sin utilizar `override`. El compilador no genera ningún error para este código.  
  
```cpp  
class BaseClass  
{  
    virtual void funcA();  
    virtual void funcB() const;  
    virtual void funcC(int = 0);  
    void funcD();  
};  
  
class DerivedClass: public BaseClass  
{  
    virtual void funcA(); // ok, works as intended  
  
    virtual void funcB(); // DerivedClass::funcB() is non-const, so it does not  
                          // override BaseClass::funcB() const and it is a new member function  
  
    virtual void funcC(double = 0.0); // DerivedClass::funcC(double) has a different  
                                      // parameter type than BaseClass::funcC(int), so  
                                      // DerivedClass::funcC(double) is a new member function  
  
};  
  
```  
  
 Al usar `override`, el compilador genera errores en lugar de crear silenciosamente nuevas funciones miembro.  
  
```cpp  
class BaseClass  
{  
    virtual void funcA();  
    virtual void funcB() const;  
    virtual void funcC(int = 0);  
    void funcD();  
};  
  
class DerivedClass: public BaseClass  
{  
    virtual void funcA() override; // ok  
  
    virtual void funcB() override; // compiler error: DerivedClass::funcB() does not   
                                   // override BaseClass::funcB() const  
  
    virtual void funcC( double = 0.0 ) override; // compiler error:   
                                                 // DerivedClass::funcC(double) does not   
                                                 // override BaseClass::funcC(int)  
  
    void funcD() override; // compiler error: DerivedClass::funcD() does not   
                           // override the non-virtual BaseClass::funcD()  
};  
  
```  
  
 Para especificar que no se puede invalidar las funciones y que no se puede heredar clases, use la [final](../cpp/final-specifier.md) palabra clave.  
  
## <a name="see-also"></a>Vea también  
 [final (especificador)](../cpp/final-specifier.md)   
 [Palabras clave](../cpp/keywords-cpp.md)   
 