---
title: Destinos de atributo (C++/CLI y C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- custom attributes, targets
ms.assetid: b4e6e224-da77-4520-b6e6-b96846e0ebc1
ms.openlocfilehash: fe2c1d27042b51300d01ba70b951b7601d87701e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172625"
---
# <a name="attribute-targets-ccli-and-ccx"></a>Destinos de atributo (C++/CLI y C++/CX)

Los especificadores de uso de atributos le permiten especificar destinos de atributo.  Cada atributo se define para aplicarse a determinados elementos del lenguaje. Por ejemplo, un atributo podría definirse para aplicarse solo a clases y structs.  En la siguiente lista se muestran los posibles elementos sintácticos en los que puede usarse un atributo personalizado. Es posible que se utilicen combinaciones de estos valores (con el o lógico).

Para especificar el destino de atributo, pase uno o varios enumeradores <xref:System.AttributeTargets> a <xref:System.AttributeUsageAttribute> al definir el atributo.

A continuación se muestra una lista de los destinos de atributo válidos:

- `All` (se aplica a todas las construcciones)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::All)]
    ref class Attr : public Attribute {};

    [assembly:Attr];
    ```

- `Assembly` (se aplica a un ensamblado como un todo)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Assembly)]
    ref class Attr : public Attribute {};

    [assembly:Attr];
    ```

- `Module` (se aplica a un módulo como un todo)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Module)]
    ref class Attr : public Attribute {};

    [module:Attr];
    ```

- `Class`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Class)]
    ref class Attr : public System::Attribute {};

    [Attr]   // same as [class:Attr]
    ref class MyClass {};
    ```

- `Struct`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Struct)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [struct:Attr]
    value struct MyStruct{};
    ```

- `enum`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Enum)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [enum:Attr]
    enum struct MyEnum{e, d};
    ```

- `Constructor`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Constructor)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] MyStruct(){}   // same as [constructor:Attr]
    };
    ```

- `Method`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Method)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] void Test(){}   // same as [method:Attr]
    };
    ```

- `Property`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Property)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] property int Test;   // same as [property:Attr]
    };
    ```

- `Field`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Field)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] int Test;   // same as [field:Attr]
    };
    ```

- `Event`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Event)]
    ref class Attr : public Attribute {};

    delegate void ClickEventHandler(int, double);

    ref struct MyStruct{
    [Attr] event ClickEventHandler^ OnClick;   // same as [event:Attr]
    };
    ```

- `Interface`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Interface)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [event:Attr]
    interface struct MyStruct{};
    ```

- `Parameter`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Parameter)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    void Test([Attr] int i);
    void Test2([parameter:Attr] int i);
    };
    ```

- `Delegate`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Delegate)]
    ref class Attr : public Attribute {};

    [Attr] delegate void Test();
    [delegate:Attr] delegate void Test2();
    ```

- `ReturnValue`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::ReturnValue)]
    ref class Attr : public Attribute {};

    ref struct MyStruct {
    // Note required specifier
    [returnvalue:Attr] int Test() { return 0; }
    };
    ```

Normalmente, un atributo precede directamente al elemento del lenguaje al que se aplica. En algunos casos, sin embargo, la posición de un atributo no es suficiente para determinar el destino previsto del atributo. En este ejemplo:

```cpp
[Attr] int MyFn(double x)...
```

Sintácticamente, no es posible determinar si está previsto que el atributo se aplique al método o al valor devuelto del método (en este caso, el valor predeterminado es el método). En tales casos, es posible que se utilice un especificador de uso de atributos. Por ejemplo, para hacer que el atributo se aplique al valor devuelto, use el especificador `returnvalue` de la manera siguiente:

```cpp
[returnvalue:Attr] int MyFn(double x)... // applies to return value
```

Los especificadores de uso de atributos son obligatorios en las siguientes situaciones:

- Para especificar un ensamblado o atributo de nivel de módulo.

- Para especificar que un atributo se aplica al valor devuelto de un método, no al método:

    ```cpp
    [method:Attr] int MyFn(double x)...     // Attr applies to method
    [returnvalue:Attr] int MyFn(double x)...// Attr applies to return value
    [Attr] int MyFn(double x)...            // default: method
    ```

- Para especificar que un atributo se aplica al descriptor de acceso de una propiedad, no a la propiedad:

    ```cpp
    [method:MyAttr(123)] property int Property()
    [property:MyAttr(123)] property int Property()
    [MyAttr(123)] property int get_MyPropy() // default: property
    ```

- Para especificar que un atributo se aplica al descriptor de acceso de un evento, no al evento:

    ```cpp
    delegate void MyDel();
    ref struct X {
       [field:MyAttr(123)] event MyDel* MyEvent;   //field
       [event:MyAttr(123)] event MyDel* MyEvent;   //event
       [MyAttr(123)] event MyDel* MyEvent;   // default: event
    }
    ```

Un especificador de uso de atributos se aplica solo al atributo que le sigue inmediatamente; es decir,

```cpp
[returnvalue:Attr1, Attr2]
```

es distinto de

```cpp
[returnvalue:Attr1, returnvalue:Attr2]
```

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

En este ejemplo se muestra cómo especificar varios destinos.

### <a name="code"></a>Código

```cpp
using namespace System;
[AttributeUsage(AttributeTargets::Class | AttributeTargets::Struct, AllowMultiple = true )]
ref struct Attr : public Attribute {
   Attr(bool i){}
   Attr(){}
};

[Attr]
ref class MyClass {};

[Attr]
[Attr(true)]
value struct MyStruct {};
```

## <a name="see-also"></a>Consulte también

[Atributos definidos por el usuario](user-defined-attributes-cpp-component-extensions.md)
