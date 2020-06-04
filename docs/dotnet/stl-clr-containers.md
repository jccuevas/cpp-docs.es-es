---
title: Contenedores de STL/CLR
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR, containers
- containers, STL/CLR
ms.assetid: 34ca8031-2041-46b9-aed9-29082d1972ea
ms.openlocfilehash: bfdbbeb735f98f77046790e21c19dd2d21b9d5c6
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79544842"
---
# <a name="stlclr-containers"></a>Contenedores de STL/CLR

La biblioteca de STL/CLR consta de contenedores similares a los que se encuentran en C++ la biblioteca estándar, pero se ejecuta en el entorno administrado del .NET Framework. No se mantiene actualizada con la biblioteca estándar real C++ y se mantiene para ofrecer soporte técnico heredado.

En este documento se proporciona información general sobre los contenedores de STL/CLR, como los requisitos de los elementos de contenedor, los tipos de elementos que se pueden insertar en los contenedores y los problemas de propiedad con los elementos de los contenedores. Cuando corresponda, se mencionan C++ las diferencias entre la biblioteca estándar nativa y STL/CLR.

## <a name="requirements-for-container-elements"></a>Requisitos para los elementos de contenedor

Todos los elementos insertados en los contenedores de STL/CLR deben obedecer ciertas instrucciones. Para obtener más información, vea [requisitos de los elementos de contenedor de STL/CLR](../dotnet/requirements-for-stl-clr-container-elements.md).

## <a name="valid-container-elements"></a>Elementos de contenedor válidos

Los contenedores de STL/CLR pueden contener uno de los dos tipos de elementos:

- Controla los tipos de referencia.

- Tipos de referencia.

- Tipos de valor con conversión unboxing.

No se pueden insertar tipos de valor con conversión boxing en ningún contenedor de STL/CLR.

### <a name="handles-to-reference-types"></a>Identificadores de tipos de referencia

Puede insertar un identificador en un tipo de referencia en un contenedor de STL/CLR. Un identificador en C++ que tiene como destino CLR es análogo a un puntero en C++Native. Para obtener más información, consulte [identificador del operador de objeto (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md).

#### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo insertar un identificador a un objeto de empleado en un [cliext (:: set](../dotnet/set-stl-clr.md).

```cpp
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

También es posible insertar un tipo de referencia (en lugar de un identificador de un tipo de referencia) en un contenedor de STL/CLR. La principal diferencia es que cuando se elimina un contenedor de tipos de referencia, se llama al destructor para todos los elementos dentro de ese contenedor. En un contenedor de identificadores para hacer referencia a los tipos, no se llama a los destructores para estos elementos.

#### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo insertar un objeto empleado en un `cliext::set`.

```cpp
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

También puede insertar un tipo de valor sin conversión boxing en un contenedor de STL/CLR. Un tipo de valor sin conversión boxing es un tipo de valor al que no se ha aplicado la *conversión boxing* a un tipo de referencia.

Un elemento de tipo de valor puede ser uno de los tipos de valor estándar, como un `int`, o puede ser un tipo de valor definido por el usuario, como un `value class`. Para obtener más información, vea [clases y Structs](../extensions/classes-and-structs-cpp-component-extensions.md) .

#### <a name="example"></a>Ejemplo

En el ejemplo siguiente se modifica el primer ejemplo haciendo que la clase Employee sea un tipo de valor. Este tipo de valor se inserta a continuación en un `cliext::set` igual que en el primer ejemplo.

```cpp
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

Si intenta insertar un identificador en un tipo de valor en un contenedor, se genera el [error del compilador C3225](../error-messages/compiler-errors-2/compiler-error-c3225.md) .

### <a name="performance-and-memory-implications"></a>Implicaciones en el rendimiento y la memoria

Debe tener en cuenta varios factores a la hora de determinar si se deben usar identificadores para hacer referencia a tipos o tipos de valor como elementos contenedores. Si decide usar tipos de valor, recuerde que se realiza una copia del elemento cada vez que se inserta un elemento en el contenedor. En el caso de los objetos pequeños, esto no debería ser un problema, pero si los objetos que se van a insertar son grandes, el rendimiento podría verse afectado. Además, si usa tipos de valor, es imposible almacenar un elemento en varios contenedores al mismo tiempo, ya que cada contenedor tendría su propia copia del elemento.

Si decide usar identificadores para hacer referencia a tipos en su lugar, el rendimiento podría aumentar porque no es necesario realizar una copia del elemento cuando se inserta en el contenedor. Además, a diferencia de los tipos de valor, el mismo elemento puede existir en varios contenedores. Sin embargo, si decide usar identificadores, debe tener cuidado para asegurarse de que el identificador es válido y de que el objeto al que hace referencia no se ha eliminado en ningún otro lugar del programa.

## <a name="ownership-issues-with-containers"></a>Problemas de propiedad con contenedores

Los contenedores de STL/CLR funcionan en la semántica del valor. Cada vez que se inserta un elemento en un contenedor, se inserta una copia de ese elemento. Si desea obtener una semántica similar a la de referencia, puede insertar un identificador en un objeto en lugar del propio objeto.

Cuando se llama al método Clear o Erase de un contenedor de objetos de controlador, los objetos a los que hacen referencia no se liberan de la memoria. Debe eliminar explícitamente el objeto o, ya que estos objetos residen en el montón administrado, permiten que el recolector de elementos no utilizados libere la memoria una vez que determine que el objeto ya no se utiliza.

## <a name="see-also"></a>Consulte también

[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
