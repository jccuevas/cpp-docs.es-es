---
title: Value (Clases y structs) (C++/CX)
ms.date: 12/30/2016
helpviewer_keywords:
- value struct
- value class
ms.assetid: 262a0992-9721-4c02-8297-efc07d90e5a4
ms.openlocfilehash: 4a4897f0a3b5c95ffb58e5c9666a2d764d71b3ec
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752896"
---
# <a name="value-classes-and-structs-ccx"></a>Value (Clases y structs) (C++/CX)

Una *estructura de valor* o clase de *valor* es un POD compatible con Windows Runtime ("estructura de datos antigua simple"). Tiene un tamaño fijo y solo se compone de campos; a diferencia de una clase ref, no tiene propiedades.

En los ejemplos siguientes se muestra cómo declarar e inicializar structs de valor.

```

// in mainpage.xaml.h:
    value struct TestStruct
    {
        Platform::String^ str;
        int i;
    };

    value struct TestStruct2
    {
        TestStruct ts;
        Platform::String^ str;
        int i;
    };

// in mainpage.cpp:
    // Initialize a value struct with an int and String
    TestStruct ts = {"I am a TestStruct", 1};

    // Initialize a value struct that contains
    // another value struct, an int and a String
    TestStruct2 ts2 = {{"I am a TestStruct", 1}, "I am a TestStruct2", 2};

    // Initialize value struct members individually.
    TestStruct ts3;
    ts3.i = 108;
    ts3.str = "Another way to init a value struct.";
```

Cuando una variable de un tipo de valor se asigna a otra variable, se copia el valor, de modo que cada una de las dos variables tiene su propia copia de los datos. Un *struct de valor* es una estructura de tamaño fijo que contiene solo campos de datos públicos que se declaran con la palabra clave `value struct` .

Una *clase de valor* es exactamente igual que un `value struct` salvo que a sus campos se les debe dar accesibilidad pública de forma explícita. Se declara mediante la palabra clave `value class` .

Una estructura de valor o una clase de valor puede `Platform::String^`contener como campos solo tipos numéricos fundamentales, clases de enumeración, o [Platform::IBox \<T>,](../cppcx/platform-ibox-interface.md) donde T es un tipo numérico o una clase de enumeración o una clase de valor o struct. Un campo `IBox<T>^` puede tener un valor `nullptr`; esta es la forma que tiene C++ de implementar el concepto de *tipos de valor que aceptan valores NULL*.

Una clase de valor o struct de valor que contiene un tipo `Platform::String^` o `IBox<T>^` como miembro no se puede convertir en `memcpy`.

Dado que todos los miembros de una `value class` o `value struct` son públicos y se emiten en metadatos, no se permiten los tipos de C++ estándar como miembros. Son diferentes de las clases ref, que sí pueden contener tipos de C++ estándar `private` o `internal` .

En el siguiente fragmento de código se declaran los tipos `Coordinates` y `City` como structs de valor. Observa que uno de los miembros de datos `City` es un tipo `GeoCoordinates` . Un `value struct` puede contener otros structs de valor como miembros.

[!code-cpp[cx_classes#07](../cppcx/codesnippet/CPP/classesstructs/class1.h#07)]

## <a name="parameter-passing-for-value-types"></a>Pasar parámetros para los tipos de valor

Si tiene un tipo de valor como un parámetro de función o de método, normalmente se pasa por valor. Para los objetos de gran tamaño, esto puede causar un problema de rendimiento. En Visual Studio2013 y versiones anteriores, los tipos de valor C++/CX siempre se pasan por valor. En Visual Studio 2015 y versiones posteriores, puede pasar tipos de valor por referencia o por valor.

Para declarar un parámetro que pasa un tipo de valor por valor, use código como el siguiente:

```cpp
void Method1(MyValueType obj);
```

Para declarar un parámetro que pasa un tipo de valor por referencia, use el símbolo de referencia (&), como se muestra a continuación:

```cpp
void Method2(MyValueType& obj);
```

El tipo de Method2 es una referencia a MyValueType y funciona de la misma manera que un tipo de referencia en C++ estándar.

Al llamar a Method1 desde otro lenguaje, como C#, no es necesario usar la palabra clave `ref` o `out` . Al llamar a Method2, use la palabra clave `ref` .

```
Method2(ref obj);
```

También puede usar un símbolo de puntero (*) para pasar un tipo de valor por referencia. El comportamiento en relación a los llamadores en otros lenguajes es el mismo (los llamadores de C# usan la palabra clave `ref` ) pero, en el método, el tipo es un puntero al tipo de valor.

## <a name="nullable-value-types"></a>Tipos de valor que aceptan valores NULL

Como se mencionó anteriormente, una clase de valor o una estructura de valor puede tener un campo de tipo [Platform::IBox\<T>,](../cppcx/platform-ibox-interface.md)por ejemplo, `IBox<int>^`. Este tipo de campo puede tener cualquier valor numérico válido para el tipo `int` , o puede tener un valor `nullptr`. Puedes pasar un campo que acepta valores NULL como argumento a un método cuyo parámetro se declara como opcional, o a cualquier otra estructura en la que no se requiera que un tipo de valor tenga un valor.

En el ejemplo siguiente se muestra cómo inicializar un struct con un campo que acepta valores NULL.

```
public value struct Student
{
    Platform::String^ Name;
    int EnrollmentYear;
    Platform::IBox<int>^ GraduationYear; // Null if not yet graduated.
};
//To create a Student struct, one must populate the nullable type.
MainPage::MainPage()
{
    InitializeComponent();

    Student A;
    A.Name = "Alice";
    A.EnrollmentYear = 2008;
    A.GraduationYear = ref new Platform::Box<int>(2012);

    Student B;
    B.Name = "Bob";
    B.EnrollmentYear = 2011;
    B.GraduationYear = nullptr;

    IsCurrentlyEnrolled(A);
    IsCurrentlyEnrolled(B);
}
bool MainPage::IsCurrentlyEnrolled(Student s)
{
    if (s.GraduationYear == nullptr)
    {
        return true;
    }
    return false;
}
```

Un struct de valor se puede configurar para que acepte valores NULL de la misma manera, como se muestra aquí:

```

public value struct MyStruct
{
public:
    int i;
    Platform::String^ s;
};

public ref class MyClass sealed
{
public:
    property Platform::IBox<MyStruct>^ myNullableStruct;
};
```

## <a name="see-also"></a>Vea también

[Sistema de tipo (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Referencia del lenguaje C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)<br/>
[Ref (Clases y structs) (C++/CX)](../cppcx/ref-classes-and-structs-c-cx.md)
