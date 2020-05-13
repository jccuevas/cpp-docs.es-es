---
title: class (C++)
ms.date: 11/04/2016
f1_keywords:
- class_cpp
helpviewer_keywords:
- class types [C++], class statements
- class keyword [C++]
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
ms.openlocfilehash: c1b9d8f6510dfe15644f0e47cad7e0aecbac36c9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180981"
---
# <a name="class-c"></a>class (C++)

La palabra clave **Class** declara un tipo de clase o define un objeto de un tipo de clase.

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

*Plantilla: Especificación*<br/>
Especificaciones de plantilla opcionales. Para obtener más información, consulte [plantillas](templates-cpp.md).

*class*<br/>
Palabra clave **Class** .

*MS-decl-Spec*<br/>
Especificación opcional de clase de almacenamiento. Para obtener más información, consulte la palabra clave [__declspec](../cpp/declspec.md) .

*etiqueta*<br/>
Nombre del tipo asignado a la clase. La etiqueta se convierte en una palabra reservada dentro del ámbito de la clase. La etiqueta es opcional. Si se omite, se define una clase anónima. Para obtener más información, vea [tipos de clase anónimos](../cpp/anonymous-class-types.md).

*base-list*<br/>
Lista opcional de clases o de estructuras de las que esta clase derivará sus miembros. Para obtener más información, vea [clases base](../cpp/base-classes.md) . Cada nombre de clase base o estructura puede ir precedido de un especificador de acceso ([Public](../cpp/public-cpp.md), [Private](../cpp/private-cpp.md), [Protected](../cpp/protected-cpp.md)) y la palabra clave [virtual](../cpp/virtual-cpp.md) . Vea la tabla de acceso a miembros en [controlar el acceso a miembros de clase](member-access-control-cpp.md) para obtener más información.

*lista de miembros*<br/>
Lista de miembros de clase. Consulte [información general sobre miembros de clase](../cpp/class-member-overview.md) para obtener más información.

*declarators*<br/>
Lista de declaradores que especifica los nombres de una o más instancias del tipo de clase. Los declaradores pueden incluir listas de inicializadores si todos los miembros de datos de la clase son **públicos**. Esto es más común en estructuras, cuyos miembros de datos son **públicos** de forma predeterminada, que en las clases. Vea [información general sobre declaradores](../cpp/overview-of-declarators.md) para obtener más información.

## <a name="remarks"></a>Observaciones

Para obtener más información sobre las clases en general, vea uno de los temas siguientes:

- [struct](../cpp/struct-cpp.md)

- [union](../cpp/unions.md)

- [__multiple_inheritance](../cpp/inheritance-keywords.md)

- [__single_inheritance](../cpp/inheritance-keywords.md)

- [__virtual_inheritance](../cpp/inheritance-keywords.md)

Para obtener información sobre las clases y los Structs administrados en C++/CLI y C++/CX, vea [clases y Structs](../extensions/classes-and-structs-cpp-component-extensions.md) .

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

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Clases y structs](../cpp/classes-and-structs-cpp.md)
