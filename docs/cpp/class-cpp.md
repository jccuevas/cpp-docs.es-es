---
title: "class (C++) | Microsoft Docs"
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
  - "class_cpp"
  - "class"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "class (palabra clave) [C++]"
  - "tipos de clase, Class (instrucciones)"
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# class (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La palabra clave `class` declara un tipo de clase o define un objeto de un tipo de clase.  
  
## Sintaxis  
  
```  
  
      [template-spec]  
       class [ms-decl-spec] [tag [: base-list ]]  
{  
   member-list  
} [declarators];  
[ class ] tag declarators;  
```  
  
#### Parámetros  
 `template-spec`  
 Especificaciones de plantilla opcionales.  Para obtener más información, vea [Especificaciones de plantilla](../Topic/Template%20Specifications.md).  
  
 `class`  
 Palabra clave `class`.  
  
 `ms-decl-spec`  
 Especificación opcional de clase de almacenamiento.  Para obtener más información, vea la palabra [\_\_declspec](../cpp/declspec.md).  
  
 `tag`  
 Nombre del tipo asignado a la clase.  La etiqueta se convierte en una palabra reservada dentro del ámbito de la clase.  La etiqueta es opcional.  Si se omite, se define una clase anónima.  Para obtener más información, vea [Tipos de clase anónimos](../cpp/anonymous-class-types.md).  
  
 `base-list`  
 Lista opcional de clases o de estructuras de las que esta clase derivará sus miembros.  Vea [Clases base](../cpp/base-classes.md) para obtener más información.  Cada nombre de clase base o de estructura puede ir precedido de un especificador de acceso \([public](../cpp/public-cpp.md), [private](../cpp/private-cpp.md), [protected](../cpp/protected-cpp.md)\) y la palabra clave [virtual](../cpp/virtual-cpp.md).  Vea la tabla de acceso a miembros en [Controlar el acceso a miembros de clase](../misc/controlling-access-to-class-members.md) para obtener más información.  
  
 `member-list`  
 Lista de miembros de clase.  Vea [Información general sobre miembros de clase](../cpp/class-member-overview.md) para obtener más información.  
  
 `declarators`  
 Lista de declaradores que especifica los nombres de una o más instancias del tipo de clase.  Los declaradores pueden incluir listas de inicializadores si todos los miembros de datos de la clase son `public`.  Esto es más frecuente en las estructuras, cuyos miembros de datos son `public` de forma predeterminada, que en las clases.  Vea [Información general sobre los declaradores](../cpp/overview-of-declarators.md) para obtener más información.  
  
## Comentarios  
 Para obtener más información sobre las clases en general, vea uno de los temas siguientes:  
  
-   [struct](../cpp/struct-cpp.md)  
  
-   [union](../cpp/unions.md)  
  
-   [\_\_multiple\_inheritance](../cpp/inheritance-keywords.md)  
  
-   [\_\_single\_inheritance](../cpp/inheritance-keywords.md)  
  
-   [\_\_virtual\_inheritance](../cpp/inheritance-keywords.md)  
  
 Para obtener información sobre las clases administradas y los structs, vea [Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md).  
  
## Ejemplo  
  
```  
// class.cpp  
// compile with: /EHsc  
// Example of the class keyword  
// Exhibits polymorphism/virtual functions.  
  
#include <iostream>  
#include <string>  
#define TRUE = 1  
using namespace std;  
  
class dog  
{  
public:  
   dog()  
   {  
      _legs = 4;  
      _bark = true;  
   }  
  
   void setDogSize(string dogSize)  
   {  
      _dogSize = dogSize;  
   }  
   virtual void setEars(string type)      // virtual function  
   {  
      _earType = type;  
   }  
  
private:  
   string _dogSize, _earType;  
   int _legs;  
   bool _bark;  
  
};  
  
class breed : public dog  
{  
public:  
   breed( string color, string size)  
   {  
      _color = color;  
      setDogSize(size);  
   }  
  
   string getColor()  
   {  
      return _color;  
   }  
  
   // virtual function redefined  
   void setEars(string length, string type)  
   {  
      _earLength = length;  
      _earType = type;  
   }  
  
protected:  
   string _color, _earLength, _earType;  
};  
  
int main()  
{  
   dog mongrel;  
   breed labrador("yellow", "large");  
   mongrel.setEars("pointy");  
   labrador.setEars("long", "floppy");  
   cout << "Cody is a " << labrador.getColor() << " labrador" << endl;  
}  
```  
  
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [Clases y structs](../cpp/classes-and-structs-cpp.md)