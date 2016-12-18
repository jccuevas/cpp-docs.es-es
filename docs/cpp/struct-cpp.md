---
title: "struct (C++) | Microsoft Docs"
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
  - "struct"
  - "struct_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "struct (constructores)"
ms.assetid: 3c6ba273-e248-4ff1-8c69-d2abcf1263c6
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# struct (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La palabra clave `struct` define un tipo de estructura o una variable de un tipo de estructura.  
  
## Sintaxis  
  
```  
[template-spec] struct [ms-decl-spec] [tag [: base-list ]]  
{   
   member-list   
} [declarators];  
[struct] tag declarators;  
```  
  
#### Parámetros  
 `template-spec`  
 Especificaciones de plantilla opcionales.  Para obtener más información, vea [Especificaciones de plantilla](../Topic/Template%20Specifications.md).  
  
 `struct`  
 Palabra clave `struct`.  
  
 `ms-decl-spec`  
 Especificación opcional de clase de almacenamiento.  Para obtener más información, vea la palabra clave [\_\_declspec](../cpp/declspec.md).  
  
 `tag`  
 Nombre del tipo dado a la estructura.  La etiqueta se convierte en una palabra reservada dentro del ámbito de la estructura.  La etiqueta es opcional.  Si se omite, se define una estructura anónima.  Para obtener más información, vea [Tipos de clase anónimos](../cpp/anonymous-class-types.md).  
  
 `base-list`  
 La lista opcional de clases o de estructuras de la que esta estructura derivará sus miembros.  Para obtener más información, vea [Clases base](../cpp/base-classes.md).  Cada nombre de clase base o de estructura puede ir precedido de un especificador de acceso \([public](../cpp/public-cpp.md), [private](../cpp/private-cpp.md), [protected](../cpp/protected-cpp.md)\) y la palabra clave [virtual](../cpp/virtual-cpp.md).  Vea la tabla de acceso a miembros en [Controlar el acceso a miembros de clase](../misc/controlling-access-to-class-members.md) para obtener más información.  
  
 `member-list`  
 Lista de miembros de la estructura.  Vea [Información general sobre miembros de clase](../cpp/class-member-overview.md) para obtener más información.  La única diferencia aquí es que se utiliza `struct` en lugar de `class`.  
  
 `declarators`  
 Lista de declaradores que especifican los nombres de la clase.  Las listas de declaradores declaran una o más instancias del tipo de estructura.  Los declaradores pueden incluir listas de inicializadores si todos los miembros de datos de la clase son `public`.  Las listas de inicializadores son comunes en estructuras porque los miembros de datos son `public` de forma predeterminada.  Para obtener más información, vea [Información general sobre los declaradores](../cpp/overview-of-declarators.md).  
  
## Comentarios  
 Un tipo de estructura es un tipo compuesto definido por el usuario.  Se compone de campos o de miembros que pueden tener diferentes tipos.  
  
 En C\+\+, una estructura es igual que una clase salvo que sus miembros son `public` de forma predeterminada.  
  
 Para obtener información sobre las clases administradas y los structs, vea [Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md).  
  
## Uso de una estructura  
 En C, debe utilizar explícitamente la palabra clave `struct` para declarar una estructura.  En C\+\+, no es necesario usar la palabra clave `struct` una vez definido el tipo.  
  
 Tiene la opción de declarar variables al definir el tipo de estructura, para lo cual debe insertar uno o más nombres de variable separados por comas entre la llave de cierre y el punto y coma.  
  
 Las variables de estructura se pueden inicializar.  La inicialización de cada variable se debe incluir entre llaves.  
  
 Para obtener información relacionada, vea [clase](../cpp/class-cpp.md), [unión](../cpp/unions.md) y [enumeración](../cpp/enumerations-cpp.md).  
  
## Ejemplo  
  
```  
#include <iostream>  
using namespace std;  
  
struct PERSON {   // Declare PERSON struct type  
    int age;   // Declare member types  
    long ss;  
    float weight;  
    char name[25];  
} family_member;   // Define object of type PERSON  
  
struct CELL {   // Declare CELL bit field  
    unsigned short character  : 8;  // 00000000 ????????  
    unsigned short foreground : 3;  // 00000??? 00000000  
    unsigned short intensity  : 1;  // 0000?000 00000000  
    unsigned short background : 3;  // 0???0000 00000000  
    unsigned short blink      : 1;  // ?0000000 00000000  
} screen[25][80];       // Array of bit fields   
  
int main() {  
    struct PERSON sister;   // C style structure declaration  
    PERSON brother;   // C++ style structure declaration  
    sister.age = 13;   // assign values to members  
    brother.age = 7;  
    cout << "sister.age = " << sister.age << '\n';  
    cout << "brother.age = " << brother.age << '\n';  
  
    CELL my_cell;  
    my_cell.character = 1;  
    cout << "my_cell.character = " << my_cell.character;  
}  
// Output:  
// sister.age = 13  
// brother.age = 7  
// my_cell.character = 1  
```  
  
## Vea también  
 [Definir tipos de clase](http://msdn.microsoft.com/es-es/e8c65425-0f3a-4dca-afc2-418c3b1e57da)