---
title: "private (C++) | Microsoft Docs"
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
  - "private_cpp"
  - "private"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "private (palabra clave) [C++]"
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# private (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
private:  
   [member-list]  
private base-class  
```  
  
## Comentarios  
 Cuando precede a una lista de miembros de clase, la palabra clave `private` especifica que esos miembros son accesibles solo desde funciones miembro y friend de la clase.  Esto se aplica a todos los miembros declarados hasta el especificador de acceso siguiente o el final de la clase.  
  
 Cuando precede al nombre de una clase base, la palabra clave `private` especifica que los miembros públicos y protegidos de la clase base son miembros privados de la clase derivada.  
  
 El acceso predeterminado de miembros de una clase es privado.  El acceso predeterminado de miembros de una estructura o unión es público.  
  
 El acceso predeterminado de una clase base es privado para las clases y público para las estructuras.  Las uniones no pueden tener clases base.  
  
 Para obtener información relacionada, vea [friend](../cpp/friend-cpp.md), [public](../cpp/public-cpp.md), [protected](../cpp/protected-cpp.md) y la tabla de acceso a miembros en [Controlar el acceso a los miembros de clase](../misc/controlling-access-to-class-members.md).  
  
## Específicos de \/clr  
 En los tipos de CLR, las palabras clave de especificador de acceso de C\+\+ \(**public**, `private` y `protected`\) pueden afectar a la visibilidad de los tipos y los métodos con respecto a los ensamblados.  Para obtener más información, consulte este artículo sobre la [Visibilidad de tipos y de miembros](../misc/type-and-member-visibility.md).  
  
> [!NOTE]
>  Los archivos compilados con [\/LN](../build/reference/ln-create-msil-module.md) no se ven afectados por este comportamiento.  En este caso, todas las clases administradas \(ya sean públicas o privadas\) estarán visibles.  
  
## Específicos de END \/clr  
  
## Ejemplo  
  
```  
// keyword_private.cpp  
class BaseClass {  
public:  
   // privMem accessible from member function  
   int pubFunc() { return privMem; }  
private:  
   void privMem;  
};  
  
class DerivedClass : public BaseClass {  
public:  
   void usePrivate( int i )  
      { privMem = i; }   // C2248: privMem not accessible  
                         // from derived class  
};  
  
class DerivedClass2 : private BaseClass {  
public:  
   // pubFunc() accessible from derived class  
   int usePublic() { return pubFunc(); }  
};  
  
int main() {  
   BaseClass aBase;  
   DerivedClass aDerived;  
   DerivedClass2 aDerived2;  
   aBase.privMem = 1;     // C2248: privMem not accessible  
   aDerived.privMem = 1;  // C2248: privMem not accessible  
                          //    in derived class  
   aDerived2.pubFunc();   // C2247: pubFunc() is private in  
                          //    derived class  
}  
```  
  
## Vea también  
 [Controlar el acceso a los miembros de clase](../misc/controlling-access-to-class-members.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)