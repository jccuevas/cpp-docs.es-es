---
title: Contenedores de STL/CLR
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR, containers
- containers, STL/CLR
ms.assetid: 34ca8031-2041-46b9-aed9-29082d1972ea
ms.openlocfilehash: dc2e5ce3263c61839a1ba434ab0d2a39e6a9078f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58774547"
---
# <a name="stlclr-containers"></a>Contenedores de STL/CLR

La biblioteca STL/CLR consta de los contenedores que se encuentran similares a las de la biblioteca estándar de C++, pero se ejecuta en el entorno administrado de .NET Framework. No se mantiene actualizada con la biblioteca estándar de C++ real y se mantiene por compatibilidad heredada.

Este documento proporciona información general de los contenedores de STL/CLR, como los requisitos para los elementos del contenedor, los tipos de elementos que puede insertar en los contenedores y los problemas de la propiedad con los elementos de los contenedores. En su caso, se mencionan las diferencias entre la biblioteca estándar de C++ nativo y la STL/CLR.

## <a name="requirements-for-container-elements"></a>Requisitos para los elementos de contenedor

Todos los elementos insertados en contenedores STL/CLR deben obedecer ciertas instrucciones. Para obtener más información, consulte [requisitos para los elementos del contenedor STL/CLR](../dotnet/requirements-for-stl-clr-container-elements.md).

## <a name="valid-container-elements"></a>Elementos de contenedor válido

Contenedores STL/CLR pueden contener uno de dos tipos de elementos:

- Controla los tipos de referencia.

- Tipos de referencia.

- Tipos de valor con conversión unboxing.

No se puede insertar tipos de valor con conversión boxing en cualquiera de los contenedores STL/CLR.

### <a name="handles-to-reference-types"></a>Identificadores de tipos de referencia

Puede insertar un identificador de un tipo de referencia en un contenedor de STL/CLR. Un identificador de C++ orientado a CLR es análoga a un puntero en C++ nativo. Para obtener más información, consulte [identificador de operador de objeto (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md).

#### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo insertar un identificador para un objeto de empleado en un [cliext::set](../dotnet/set-stl-clr.md).

```
// cliext_container_valid_reference_handle.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

ref class Employee
{
public:
    // STL/CLR containers might require a public constructor, so it
    // is a good idea to define one.
    Employee() :
        name(nullptr),
        employeeNumber(0) { }

    // All STL/CLR containers require a public copy constructor.
    Employee(const Employee% orig) :
        name(orig.name),
        employeeNumber(orig.employeeNumber) { }

    // All STL/CLR containers require a public assignment operator.
    Employee% operator=(const Employee% orig)
    {
        if (this != %orig)
        {
            name = orig.name;
            employeeNumber = orig.employeeNumber;
        }

        return *this;
    }

    // All STL/CLR containers require a public destructor.
    ~Employee() { }

    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee^ empl1419 = gcnew Employee();
    empl1419->Name = L"Darin Lockert";
    empl1419->EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee^>^ emplSet = gcnew set<Employee^>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee^ empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl->EmployeeNumber, empl->Name);
    }

    return 0;
}
```

### <a name="reference-types"></a>Tipos de referencia

También es posible insertar un tipo de referencia (en lugar de un identificador de un tipo de referencia) en un contenedor STL/CLR. La principal diferencia es que, cuando se elimina un contenedor de tipos de referencia, se llama al destructor para todos los elementos dentro de ese contenedor. En un contenedor de identificadores a tipos de referencia, no se llama a los destructores de estos elementos.

#### <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo insertar un objeto de empleado en un `cliext::set`.

```
// cliext_container_valid_reference.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

ref class Employee
{
public:
    // STL/CLR containers might require a public constructor, so it
    // is a good idea to define one.
    Employee() :
        name(nullptr),
        employeeNumber(0) { }

    // All STL/CLR containers require a public copy constructor.
    Employee(const Employee% orig) :
        name(orig.name),
        employeeNumber(orig.employeeNumber) { }

    // All STL/CLR containers require a public assignment operator.
    Employee% operator=(const Employee% orig)
    {
        if (this != %orig)
        {
            name = orig.name;
            employeeNumber = orig.employeeNumber;
        }

        return *this;
    }

    // All STL/CLR containers require a public destructor.
    ~Employee() { }

    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee empl1419;
    empl1419.Name = L"Darin Lockert";
    empl1419.EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee>^ emplSet = gcnew set<Employee>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee^ empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl->EmployeeNumber, empl->Name);
    }

    return 0;
}
```

### <a name="unboxed-value-types"></a>Tipos de valor con conversión unboxing

También puede insertar un tipo de valor con conversión unboxing en un contenedor STL/CLR. Un tipo de valor con conversión unboxing es un tipo de valor que no ha sido *boxed* en un tipo de referencia.

Un elemento de tipo de valor puede ser uno de los tipos de valor estándar, como un `int`, o puede ser un tipo de valor definido por el usuario, como un `value class`. Para obtener más información, consulte [clases y Structs](../extensions/classes-and-structs-cpp-component-extensions.md)

#### <a name="example"></a>Ejemplo

El ejemplo siguiente modifica el primer ejemplo mediante la realización de un tipo de valor de clase del empleado. Este tipo de valor, a continuación, se inserta en un `cliext::set` al igual que en el primer ejemplo.

```
// cliext_container_valid_valuetype.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

value class Employee
{
public:
    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee empl1419;
    empl1419.Name = L"Darin Lockert";
    empl1419.EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee>^ emplSet = gcnew set<Employee>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl.EmployeeNumber, empl.Name);
    }

    return 0;
}
```

Si se intenta insertar un identificador de un tipo de valor en un contenedor, [Error del compilador C3225](../error-messages/compiler-errors-2/compiler-error-c3225.md) se genera.

### <a name="performance-and-memory-implications"></a>Rendimiento y las implicaciones de memoria

Debe tener en cuenta varios factores a la hora de determinar si se debe usar identificadores de hacer referencia a tipos o tipos de valor como elementos de contenedor. Si decide utilizar los tipos de valor, recuerde que se realiza una copia del elemento cada vez que se inserta un elemento en el contenedor. Para objetos pequeños, esto no debería ser un problema, pero si los objetos que se insertan son grandes, el rendimiento podría verse afectado. Además, si utiliza tipos de valor, es imposible almacenar un elemento en varios contenedores al mismo tiempo, ya que cada contenedor tendría su propia copia del elemento.

Si decide utilizar identificadores a tipos de referencia en su lugar, podría aumentar rendimiento porque no es necesario realizar una copia del elemento cuando se inserta en el contenedor. Además, a diferencia de con los tipos de valor, el mismo elemento puede existir en varios contenedores. Sin embargo, si decide utilizar identificadores, debe tener cuidado para asegurarse de que el identificador es válido y que el objeto a que hace referencia no se ha eliminado en otro lugar en el programa.

## <a name="ownership-issues-with-containers"></a>Problemas de propiedad con contenedores

Los contenedores de STL/CLR funcionan en la semántica del valor. Cada vez que inserte un elemento en un contenedor, se inserta una copia de ese elemento. Si desea obtener semántica similar a la referencia, puede insertar un identificador de un objeto en lugar del propio objeto.

Al llamar a sin cifrar o erase (método) de un contenedor de objetos de controlador, no se liberarán los objetos que hacen referencia los identificadores de la memoria. Debe explícitamente eliminar el objeto, o, ya que estos objetos residen en el montón administrado, permitir que el recolector de elementos no utilizados liberar la memoria una vez que determina que el objeto ya no se está utilizando.

## <a name="see-also"></a>Vea también

[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
