---
title: "final (especificador) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "final"
  - "final_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "final (identificador)"
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# final (especificador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede utilizar la palabra clave `final` para designar funciones virtuales que no se pueden invalidar en una clase derivada.  También puede utilizarla para designar clases que no se pueden heredar.  
  
## Sintaxis  
  
```  
  
function-declaration final;  
```  
  
```  
  
class class-name final base-classes  
```  
  
## Comentarios  
 `final` es contextual y tiene un significado especial solo cuando se utiliza después de una declaración de función o nombre de clase; de lo contrario, no es una palabra clave reservada.  
  
 Cuando `final` se utiliza en declaraciones de clase, `base-classes` es una parte opcional de la declaración.  
  
## Ejemplo  
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
  
 Para obtener información sobre cómo especificar que las funciones miembro se puedan invalidar, vea [override \(especificador\)](../cpp/override-specifier.md).  
  
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
  
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [\(NOTINBUILD\) C\+\+ Type Names](http://msdn.microsoft.com/es-es/b53ba470-e583-4e5c-b634-6018f6110674)   
 [override \(especificador\)](../cpp/override-specifier.md)