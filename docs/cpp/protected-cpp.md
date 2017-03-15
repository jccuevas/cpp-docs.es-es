---
title: "protected (C++) | Microsoft Docs"
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
  - "protected"
  - "protected_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "protected (palabra clave) [C++]"
  - "protected (palabra clave) [C++], acceso a miembros"
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# protected (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
protected:  
   [member-list]  
protected base-class  
```  
  
## Comentarios  
 La palabra clave `protected` especifica el acceso a los miembros de clase en *member\-list* hasta el especificador de acceso siguiente \(**public** o `private`\) o el final de la definición de clase.  Los miembros de clase declarados como `protected` solo los pueden utilizar los siguientes elementos:  
  
-   Funciones miembro de la clase que declaró originalmente estos miembros.  
  
-   Objetos friend de la clase que declaró originalmente estos miembros.  
  
-   Clases derivadas con acceso público o protegido desde la clase que declaró originalmente estos miembros.  
  
-   Clases directas derivadas de forma privada que también tienen acceso privado a miembros protegidos.  
  
 Cuando precede al nombre de una clase base, la palabra clave `protected` especifica que los miembros públicos y protegidos de la clase base son miembros protegidos de sus clases derivadas.  
  
 Los miembros protegidos no son tan privados como los miembros `private`, que solo son accesibles a los miembros de la clase en que se declaran, pero no son tan públicos como los miembros **public**, que son accesibles en cualquier función.  
  
 Los miembros protegidos que también se declaran como **static** son accesibles a cualquier función miembro o friend de una clase derivada.  Los miembros protegidos que no se declaran como **static** son accesibles a las funciones miembro y friend en una clase derivada solo a través de un puntero a, una referencia a, o un objeto de la clase derivada.  
  
 Para obtener información relacionada, vea [friend](../cpp/friend-cpp.md), [public](../cpp/public-cpp.md), [private](../cpp/private-cpp.md) y la tabla de acceso a miembros en [Controlar el acceso a los miembros de clase](../misc/controlling-access-to-class-members.md).  
  
## Específicos de \/clr  
 En los tipos de CLR, las palabras clave de especificador de acceso de C\+\+ \(**public**, `private` y `protected`\) pueden afectar a la visibilidad de los tipos y los métodos con respecto a los ensamblados.  Para obtener más información, vea el tema sobre la [Visibilidad de tipos y de miembros](../misc/type-and-member-visibility.md).  
  
> [!NOTE]
>  Los archivos compilados con [\/LN](../build/reference/ln-create-msil-module.md) no se ven afectados por este comportamiento.  En este caso, todas las clases administradas \(ya sean públicas o privadas\) estarán visibles.  
  
## Específicos de END \/clr  
  
## Ejemplo  
  
```  
// keyword_protected.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class X {  
public:  
   void setProtMemb( int i ) { m_protMemb = i; }  
   void Display() { cout << m_protMemb << endl; }  
protected:  
   int  m_protMemb;  
   void Protfunc() { cout << "\nAccess allowed\n"; }  
} x;  
  
class Y : public X {  
public:  
   void useProtfunc() { Protfunc(); }  
} y;  
  
int main() {  
   // x.m_protMemb;         error, m_protMemb is protected  
   x.setProtMemb( 0 );   // OK, uses public access function  
   x.Display();  
   y.setProtMemb( 5 );   // OK, uses public access function  
   y.Display();  
   // x.Protfunc();         error, Protfunc() is protected  
   y.useProtfunc();      // OK, uses public access function  
                        // in derived class  
}  
```  
  
## Vea también  
 [Controlar el acceso a los miembros de clase](../misc/controlling-access-to-class-members.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)