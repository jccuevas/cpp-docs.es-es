---
title: clase (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- class_cpp
dev_langs:
- CPP
helpviewer_keywords:
- class types [C++], class statements
- class keyword [C++]
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a3c3defdfb882db69f7789c97feba11d346e540
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405592"
---
# <a name="class-c"></a>class (C++)
El **clase** palabra clave declara un tipo de clase o define un objeto de un tipo de clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[template-spec]  
class [ms-decl-spec] [tag [: base-list ]]  
{  
   member-list  
} [declarators];  
[ class ] tag declarators;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *especificación de plantilla*  
 Especificaciones de plantilla opcionales. Para obtener más información, consulte [plantillas](templates-cpp.md).  
  
 *class*  
 El **clase** palabra clave.  
  
 *MS-decl-spec*  
 Especificación opcional de clase de almacenamiento. Para obtener más información, consulte el [__declspec](../cpp/declspec.md) palabra clave.  
  
 *Etiqueta*  
 Nombre del tipo asignado a la clase. La etiqueta se convierte en una palabra reservada dentro del ámbito de la clase. La etiqueta es opcional. Si se omite, se define una clase anónima. Para obtener más información, consulte [tipos de clase anónima](../cpp/anonymous-class-types.md).  
  
 *base-list*  
 Lista opcional de clases o de estructuras de las que esta clase derivará sus miembros. Consulte [clases Base](../cpp/base-classes.md) para obtener más información. Cada nombre de clase o estructura base puede ir precedido por un especificador de acceso ([pública](../cpp/public-cpp.md), [privada](../cpp/private-cpp.md), [protegido](../cpp/protected-cpp.md)) y el [virtual](../cpp/virtual-cpp.md) palabra clave. Vea la tabla de acceso a miembros de [controlar el acceso a los miembros de clase](member-access-control-cpp.md) para obtener más información.  
  
 *lista de miembros*  
 Lista de miembros de clase. Consulte [información general sobre miembros de clase](../cpp/class-member-overview.md) para obtener más información.  
  
 *declaradores*  
 Lista de declaradores que especifica los nombres de una o más instancias del tipo de clase. Los declaradores pueden incluir listas de inicializadores si todos los miembros de datos de la clase son **pública**. Esto es más común en estructuras, cuyos miembros de datos son **pública** de forma predeterminada, que en las clases. Consulte [información general de los declaradores](../cpp/overview-of-declarators.md) para obtener más información.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información sobre las clases en general, vea uno de los temas siguientes:  
  
-   [struct](../cpp/struct-cpp.md)  
  
-   [union](../cpp/unions.md)  
  
-   [__multiple_inheritance](../cpp/inheritance-keywords.md)  
  
-   [__single_inheritance](../cpp/inheritance-keywords.md)  
  
-   [__virtual_inheritance](../cpp/inheritance-keywords.md)  
  
 Para obtener información sobre las clases administradas y los structs, vea [clases y Structs](../windows/classes-and-structs-cpp-component-extensions.md)  
  
## <a name="example"></a>Ejemplo  
  
```cpp 
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
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)   
 [Clases y structs](../cpp/classes-and-structs-cpp.md)