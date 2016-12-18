---
title: "public (C++) | Microsoft Docs"
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
  - "public"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "public (palabra clave) [C++]"
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# public (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
public:  
   [member-list]  
public base-class  
```  
  
## Comentarios  
 Cuando precede a una lista de miembros de clase, la palabra clave **public** especifica que esos miembros son accesibles desde cualquier función.  Esto se aplica a todos los miembros declarados hasta el especificador de acceso siguiente o el final de la clase.  
  
 Cuando precede al nombre de una clase base, la palabra clave **public** especifica que los miembros públicos y protegidos de la clase base son miembros públicos y protegidos, respectivamente, de la clase derivada.  
  
 El acceso predeterminado de miembros de una clase es privado.  El acceso predeterminado de miembros de una estructura o unión es público.  
  
 El acceso predeterminado de una clase base es privado para las clases y público para las estructuras.  Las uniones no pueden tener clases base.  
  
 Para obtener más información, vea [private](../cpp/private-cpp.md), [protected](../cpp/protected-cpp.md), [friend](../cpp/friend-cpp.md) y la tabla de acceso a miembros en [Controlar el acceso a miembros de clase](../misc/controlling-access-to-class-members.md).  
  
## Específicos de \/clr  
 En los tipos de CLR, las palabras clave de especificador de acceso de C\+\+ \(**public**, `private` y `protected`\) pueden afectar a la visibilidad de los tipos y los métodos con respecto a los ensamblados.  Para obtener más información, vea [Visibilidad de tipos y de miembros](../misc/type-and-member-visibility.md).  
  
> [!NOTE]
>  Los archivos compilados con [\/LN](../build/reference/ln-create-msil-module.md) no se ven afectados por este comportamiento.  En este caso, todas las clases administradas \(ya sean públicas o privadas\) estarán visibles.  
  
## Específicos de END \/clr  
  
## Ejemplo  
  
```  
// keyword_public.cpp  
class BaseClass {  
public:  
   int pubFunc() { return 0; }  
};  
  
class DerivedClass : public BaseClass {};  
  
int main() {  
   BaseClass aBase;  
   DerivedClass aDerived;  
   aBase.pubFunc();       // pubFunc() is accessible   
                          //    from any function  
   aDerived.pubFunc();    // pubFunc() is still public in   
                          //    derived class  
}  
```  
  
## Vea también  
 [Controlar el acceso a los miembros de clase](../misc/controlling-access-to-class-members.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)