---
title: "Contenedores de STL/CLR | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contenedores, STL/CLR"
  - "STL/CLR, contenedores"
ms.assetid: 34ca8031-2041-46b9-aed9-29082d1972ea
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# Contenedores de STL/CLR
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La biblioteca de STL\/CLR tiene los mismos contenedores que se encuentran en la biblioteca estándar de C\+\+, pero se ejecuta en el entorno administrado de .NET Framework.  Si ya está familiarizado con la biblioteca estándar \(STL\) de plantilla, STL\/CLR es la mejor manera de seguir utilizando las funciones desarrollada ya mientras actualiza el código al destino Common Language Runtime \(CLR\).  
  
 En este documento se proporciona información general sobre los contenedores en STL\/CLR, como los requisitos para los elementos contenedor, los tipos de elementos que se pueden insertar en contenedores, y los problemas de propiedad con elementos en los contenedores.  En este caso, las diferencias entre la biblioteca de plantillas y el STL\/CLR estándar nativos se mencionan.  
  
## Requisitos para los elementos de contenedor  
 Todos los elementos insertados en los contenedores STL deben seguir ciertas instrucciones.  Para obtener más información, vea [Requisitos de los elementos contenedores de STL\/CLR](../dotnet/requirements-for-stl-clr-container-elements.md).  
  
## Elementos contenedores válidos  
 Los contenedores de STL\/CLR pueden contener uno de dos tipos de elementos:  
  
-   Identificadores a los tipos de referencia.  
  
-   Tipos de referencia.  
  
-   Tipos de valor con conversión unboxing.  
  
 No puede insertar tipos de valor de conversión boxing en los contenedores cualquiera de STL\/CLR.  
  
### Identificadores a los tipos de referencia  
 Puede insertar un identificador a un tipo de referencia en un contenedor de STL\/CLR.  Un identificador en C\+\+ destinado a CLR es análogo a un puntero en C\+\+ nativo.  Para obtener más información, vea [Identificador a un operador de objeto \(^\)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md).  
  
#### Ejemplo  
 El ejemplo siguiente se muestra cómo insertar un identificador a un objeto empleado en [cliext::set](../dotnet/set-stl-clr.md).  
  
```  
// cliext_container_valid_reference_handle.cpp  
// compile with: /clr  
  
#include <cliext/set>  
  
using namespace cliext;  
using namespace System;  
  
ref class Employee  
{  
public:  
    // STL containers might require a public constructor, so it  
    // is a good idea to define one.  
    Employee() :  
        name(nullptr),  
        employeeNumber(0) { }  
  
    // All STL containers require a public copy constructor.  
    Employee(const Employee% orig) :  
        name(orig.name),  
        employeeNumber(orig.employeeNumber) { }  
  
    // All STL containers require a public assignment operator.  
    Employee% operator=(const Employee% orig)  
    {  
        if (this != %orig)  
        {  
            name = orig.name;  
            employeeNumber = orig.employeeNumber;  
        }  
  
        return *this;  
    }  
  
    // All STL containers require a public destructor.  
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
  
### Tipos de referencia  
 También es posible insertar un tipo de referencia \(en lugar de un identificador a un tipo de referencia\) en un contenedor de STL\/CLR.  La diferencia principal es que cuando un contenedor de tipos de referencia se elimina, se llama al destructor para todo el interior de los elementos que contenedor.  En un contenedor de identificadores a los tipos de referencia, destructores para estos elementos no se denominados.  
  
#### Ejemplo  
 El ejemplo siguiente se muestra cómo insertar un objeto empleado en `cliext::set`.  
  
```  
// cliext_container_valid_reference.cpp  
// compile with: /clr  
  
#include <cliext/set>  
  
using namespace cliext;  
using namespace System;  
  
ref class Employee  
{  
public:  
    // STL containers might require a public constructor, so it  
    // is a good idea to define one.  
    Employee() :  
        name(nullptr),  
        employeeNumber(0) { }  
  
    // All STL containers require a public copy constructor.  
    Employee(const Employee% orig) :  
        name(orig.name),  
        employeeNumber(orig.employeeNumber) { }  
  
    // All STL containers require a public assignment operator.  
    Employee% operator=(const Employee% orig)  
    {  
        if (this != %orig)  
        {  
            name = orig.name;  
            employeeNumber = orig.employeeNumber;  
        }  
  
        return *this;  
    }  
  
    // All STL containers require a public destructor.  
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
  
### Tipos de valor con conversión unboxing  
 También puede insertar un tipo de valor dos en un contenedor de STL\/CLR.  Un tipo de valor dos es un tipo de valor que *no se ha convertido* en un tipo de referencia.  
  
 Un elemento de tipo de valor puede ser uno de los tipos de valor estándar, como `int`, o puede ser un tipo de valor definido por el usuario, como `value class`.  Para obtener más información, vea [Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md)  
  
#### Ejemplo  
 El ejemplo siguiente se modifica el primer ejemplo creando la clase employee un tipo de valor.  A continuación insertan a este tipo de valor en `cliext::set` igual que en el primer ejemplo.  
  
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
  
 Si intenta insertar un identificador a un tipo de valor en un contenedor, se genera [Error del compilador C3225](../error-messages/compiler-errors-2/compiler-error-c3225.md) .  
  
### Rendimiento y memoria Implications  
 Debe tener en cuenta varios factores al determinar si utilizar identificadores a los tipos de referencia o tipos de valor como elementos contenedores.  Si decide utilizar tipos de valor, recuerde que una copia del elemento se hace cada vez un elemento está incrustado en el contenedor.  Para objetos pequeños, esto no debe ser un problema, pero si los objetos que son insertados son grandes, el rendimiento puede sufrir.  Además, si utiliza tipos de valor, es imposible almacenar un elemento en contenedores al mismo tiempo porque cada contenedor tiene su propia copia del elemento.  
  
 Si decide utilizar identificadores a los tipos de referencia en su lugar, el rendimiento podría aumentar porque no es necesario realizar una copia del elemento cuando se inserta en el contenedor.  También, a diferencia de los tipos de valor, el mismo elemento puede existir en contenedores.  Sin embargo, si decide utilizar identificadores, debe tener cuidado para asegurarse de que el identificador es válido y que el objeto que se hace referencia no se ha eliminado en cualquier parte del programa.  
  
## Problemas de propiedad con contenedores  
 Contenedores en el trabajo de STL\/CLR en la semántica de valores.  Cada vez que se inserta un elemento en un contenedor, una copia del elemento se inserta.  Si desea obtener referencia\- como la semántica, puede insertar un identificador a un objeto en lugar del propio objeto.  
  
 Cuando se llama a desactive o desactive método de un contenedor de objetos ID, los objetos a los que los identificadores hacen referencia no se liberan de memoria.  Deberá eliminar explícitamente el objeto, o, porque estos objetos residen en el montón administrado, permita que el recolector de elementos no utilizados libere la memoria una vez que determina que el objeto ya no se utiliza.  
  
## Vea también  
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)