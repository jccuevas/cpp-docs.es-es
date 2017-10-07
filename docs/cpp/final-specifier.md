---
title: final (especificador) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- final_CPP
dev_langs:
- C++
helpviewer_keywords:
- final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: c9f0a638707466778e75a3eabfe838c84b0355d7
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="final-specifier"></a>final (especificador)
Puede utilizar la palabra clave `final` para designar funciones virtuales que no se pueden invalidar en una clase derivada. También puede utilizarla para designar clases que no se pueden heredar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
function-declaration final;  
```  
  
```  
  
class class-name final base-classes  
```  
  
## <a name="remarks"></a>Comentarios  
 `final` es contextual y tiene un significado especial solo cuando se utiliza después de una declaración de función o nombre de clase; de lo contrario, no es una palabra clave reservada.  
  
 Cuando `final` se utiliza en declaraciones de clase, `base-classes` es una parte opcional de la declaración.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa la palabra clave `final` para especificar que no se puede invalidar una función virtual.  
  
```cpp  
class BaseClass  
{  
    virtual void func() final;  
};  
  
class DerivedClass: public BaseClass  
{  
    virtual void func(); // compiler error: attempting to   
                         // override a final function  
};  
```  
  
 Para obtener información sobre cómo especificar que se pueden invalidar las funciones miembro, vea [especificador de reemplazo](../cpp/override-specifier.md).  
  
 En el ejemplo siguiente se usa la palabra clave `final` para especificar que una clase no se puede heredar.  
  
```cpp  
class BaseClass final   
{  
};  
  
class DerivedClass: public BaseClass // compiler error: BaseClass is   
                                     // marked as non-inheritable  
{  
};  
```  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)   
 [override (Especificador)](../cpp/override-specifier.md)
