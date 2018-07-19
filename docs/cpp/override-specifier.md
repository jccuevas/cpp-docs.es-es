---
title: Especificador de invalidación | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b50ffc096cc710f4028c7effc2dda8822f077f29
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940659"
---
# <a name="override-specifier"></a>override (especificador)
Puede usar el **invalidar** palabra clave para designar funciones que invalidan una función virtual en una clase base de miembro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
function-declaration override;  
```  
  
## <a name="remarks"></a>Comentarios  
 **invalidar** es contextual y tiene especiales, lo que significa que solo cuando se utiliza después de una declaración de función miembro; de lo contrario, no es una palabra clave reservada.  
  
## <a name="example"></a>Ejemplo  
 Use **invalidar** para ayudar a evitar el comportamiento inadvertido de herencia en el código. El ejemplo siguiente muestra dónde, sin usar **invalidar**, el comportamiento de la función miembro de la clase derivada puede no haberse previsto. El compilador no genera ningún error para este código.  
  
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
  
 Cuando usas **invalidar**, el compilador genera errores en lugar de en modo silencioso crear nuevo miembro de las funciones.  
  
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
  
 Para especificar que no se puede invalidar las funciones y clases que no se puede heredar, use el [final](../cpp/final-specifier.md) palabra clave.  
  
## <a name="see-also"></a>Vea también  
 [final (especificador)](../cpp/final-specifier.md)   
 [Palabras clave](../cpp/keywords-cpp.md)   
 