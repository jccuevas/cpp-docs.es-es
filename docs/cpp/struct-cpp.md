---
title: struct (C++)
ms.date: 11/04/2016
f1_keywords:
- struct_cpp
helpviewer_keywords:
- struct constructors
ms.assetid: 3c6ba273-e248-4ff1-8c69-d2abcf1263c6
ms.openlocfilehash: 78d3df4a96cb769cb31760c53c8486c86189e00c
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893345"
---
# <a name="struct-c"></a>struct (C++)

El **struct** palabra clave define un tipo de estructura o una variable de un tipo de estructura.

## <a name="syntax"></a>Sintaxis

```
[template-spec] struct [ms-decl-spec] [tag [: base-list ]]
{
   member-list
} [declarators];
[struct] tag declarators;
```

#### <a name="parameters"></a>Parámetros

*template-spec*<br/>
Especificaciones de plantilla opcionales. Para obtener más información, consulte [especificaciones de plantilla](templates-cpp.md).

*struct*<br/>
El **struct** palabra clave.

*ms-decl-spec*<br/>
Especificación opcional de clase de almacenamiento. Para obtener más información, consulte el [__declspec](../cpp/declspec.md) palabra clave.

*tag*<br/>
Nombre del tipo dado a la estructura. La etiqueta se convierte en una palabra reservada dentro del ámbito de la estructura. La etiqueta es opcional. Si se omite, se define una estructura anónima. Para obtener más información, consulte [tipos de clase anónima](../cpp/anonymous-class-types.md).

*base-list*<br/>
La lista opcional de clases o de estructuras de la que esta estructura derivará sus miembros. Consulte [clases Base](../cpp/base-classes.md) para obtener más información. Cada nombre de clase o estructura base puede ir precedido por un especificador de acceso ([pública](../cpp/public-cpp.md), [privada](../cpp/private-cpp.md), [protegido](../cpp/protected-cpp.md)) y el [virtual](../cpp/virtual-cpp.md) palabra clave. Vea la tabla de acceso a miembros de [controlar el acceso a los miembros de clase](member-access-control-cpp.md) para obtener más información.

*member-list*<br/>
Lista de miembros de la estructura. Consulte [información general sobre miembros de clase](../cpp/class-member-overview.md) para obtener más información. La única diferencia es que **struct** se utiliza en lugar de **clase**.

*declarators*<br/>
Lista de declaradores que especifican los nombres de la estructura. Las listas de declaradores declaran una o más instancias del tipo de estructura. Los declaradores pueden incluir listas de inicializadores si todos los miembros de datos de la estructura son **pública**. Las listas de inicializadores son comunes en estructuras porque son miembros de datos **pública** de forma predeterminada.  Consulte [información general de los declaradores](../cpp/overview-of-declarators.md) para obtener más información.

## <a name="remarks"></a>Comentarios

Un tipo de estructura es un tipo compuesto definido por el usuario. Se compone de campos o de miembros que pueden tener diferentes tipos.

En C++, una estructura es igual que una clase salvo que sus miembros son **pública** de forma predeterminada.

Para obtener información sobre las clases administradas y los structs, vea [clases y Structs](../windows/classes-and-structs-cpp-component-extensions.md).

## <a name="using-a-structure"></a>Uso de una estructura

En C, debe utilizar explícitamente la **struct** palabra clave para declarar una estructura. En C++, no es necesario usar el **struct** palabra clave una vez definido el tipo.

Tiene la opción de declarar variables al definir el tipo de estructura, para lo cual debe insertar uno o más nombres de variable separados por comas entre la llave de cierre y el punto y coma.

Las variables de estructura se pueden inicializar. La inicialización de cada variable se debe incluir entre llaves.

Para obtener información relacionada, consulte [clase](../cpp/class-cpp.md), [unión](../cpp/unions.md), y [enum](../cpp/enumerations-cpp.md).

## <a name="example"></a>Ejemplo

```cpp
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
