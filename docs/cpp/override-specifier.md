---
title: "override (especificador) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "override (identificador)"
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# override (especificador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede usar la palabra clave `override` para indicar las funciones miembro que invalidan una función virtual en una clase base.  
  
## Sintaxis  
  
```  
  
function-declaration override;  
```  
  
## Comentarios  
 `override` es contextual y tiene un significado especial solo cuando se utiliza después de una declaración de función miembro; de lo contrario, no es una palabra clave reservada.  
  
## Ejemplo  
 Utilice `override` para evitar el comportamiento inadvertido de herencia en el código.  En el ejemplo siguiente se muestra dónde puede no haberse previsto el comportamiento de la función miembro de clase derivada, sin utilizar `override`.  El compilador no genera ningún error para este código.  
  
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
  
 Para especificar que las funciones no pueden reemplazarse y que las clases no se pueden heredar, use la palabra clave [final](../cpp/final-specifier.md).  
  
## Vea también  
 [final \(especificador\)](../cpp/final-specifier.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [\(NOTINBUILD\) C\+\+ Type Names](http://msdn.microsoft.com/es-es/b53ba470-e583-4e5c-b634-6018f6110674)