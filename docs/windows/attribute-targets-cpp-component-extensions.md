---
title: Atributo de destinos (extensiones de componentes de C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- custom attributes, targets
ms.assetid: b4e6e224-da77-4520-b6e6-b96846e0ebc1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f89eb3fcc48d8341190ceb5fe74a25570543e0cd
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645596"
---
# <a name="attribute-targets-c-component-extensions"></a>Destinos de atributo (Extensiones de componentes de C++)
Especificadores de uso del atributo le permiten especificar los destinos de atributo.  Cada atributo se define para que se aplican a determinados elementos del lenguaje. Por ejemplo, un atributo puede definirse para que solo se aplican a las clases y structs.  La siguiente lista muestra los elementos sintácticos en el que se puede usar un atributo personalizado. Combinaciones de estos valores (utilizando lógica o) se pueden usar.  
  
 Para especificar el destino de atributo, para pasar uno o varios <xref:System.AttributeTargets> enumeradores a <xref:System.AttributeUsageAttribute> al definir el atributo.  
  
 La siguiente es una lista de los destinos de atributo válido:  
  
-   `All` (se aplica a todas las construcciones)  
  
    ```cpp  
    using namespace System;  
    [AttributeUsage(AttributeTargets::All)]  
    ref class Attr : public Attribute {};  
  
    [assembly:Attr];  
    ```  
  
-   `Assembly` (se aplica a un ensamblado como un todo)  
  
    ```cpp  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Assembly)]  
    ref class Attr : public Attribute {};  
  
    [assembly:Attr];  
    ```  
  
-   `Module` (se aplica a un módulo como un todo)  
  
    ```cpp  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Module)]  
    ref class Attr : public Attribute {};  
  
    [module:Attr];  
    ```  
  
-   `Class`  
  
    ```cpp  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Class)]  
    ref class Attr : public System::Attribute {};  
  
    [Attr]   // same as [class:Attr]  
    ref class MyClass {};  
    ```  
  
-   `Struct`  
  
    ```cpp  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Struct)]  
    ref class Attr : public Attribute {};  
  
    [Attr]   // same as [struct:Attr]  
    value struct MyStruct{};  
    ```  
  
-   `enum`  
  
    ```cpp  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Enum)]  
    ref class Attr : public Attribute {};  
  
    [Attr]   // same as [enum:Attr]  
    enum struct MyEnum{e, d};  
    ```  
  
-   `Constructor`  
  
    ```cpp  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Constructor)]  
    ref class Attr : public Attribute {};  
  
    ref struct MyStruct{  
    [Attr] MyStruct(){}   // same as [constructor:Attr]  
    };  
    ```  
  
-   `Method`  
  
    ```cpp  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Method)]  
    ref class Attr : public Attribute {};  
  
    ref struct MyStruct{  
    [Attr] void Test(){}   // same as [method:Attr]  
    };  
    ```  
  
-   `Property`  
  
    ```cpp  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Property)]  
    ref class Attr : public Attribute {};  
  
    ref struct MyStruct{  
    [Attr] property int Test;   // same as [property:Attr]  
    };  
    ```  
  
-   `Field`  
  
    ```cpp  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Field)]  
    ref class Attr : public Attribute {};  
  
    ref struct MyStruct{  
    [Attr] int Test;   // same as [field:Attr]  
    };  
    ```  
  
-   `Event`  
  
    ```cpp  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Event)]  
    ref class Attr : public Attribute {};  
  
    delegate void ClickEventHandler(int, double);  
  
    ref struct MyStruct{  
    [Attr] event ClickEventHandler^ OnClick;   // same as [event:Attr]  
    };  
    ```  
  
-   `Interface`  
  
    ```cpp  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Interface)]  
    ref class Attr : public Attribute {};  
  
    [Attr]   // same as [event:Attr]  
    interface struct MyStruct{};  
    ```  
  
-   `Parameter`  
  
    ```cpp  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Parameter)]  
    ref class Attr : public Attribute {};  
  
    ref struct MyStruct{  
    void Test([Attr] int i);  
    void Test2([parameter:Attr] int i);  
    };  
    ```  
  
-   `Delegate`  
  
    ```cpp  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Delegate)]  
    ref class Attr : public Attribute {};  
  
    [Attr] delegate void Test();  
    [delegate:Attr] delegate void Test2();  
    ```  
  
-   `ReturnValue`  
  
    ```cpp  
    using namespace System;  
    [AttributeUsage(AttributeTargets::ReturnValue)]  
    ref class Attr : public Attribute {};  
  
    ref struct MyStruct {  
    // Note required specifier  
    [returnvalue:Attr] int Test() { return 0; }  
    };  
    ```  
  
 Normalmente, un atributo precede directamente el elemento de lenguaje al que se aplica. Sin embargo, en algunos casos, no es suficiente para determinar el destino del atributo la posición de un atributo. Considere este ejemplo:  
  
```cpp  
[Attr] int MyFn(double x)...  
```  
  
 Sintácticamente, no hay ninguna forma de saber si se pretende que el atributo se aplica al método o al valor devuelto del método (en este caso, el valor predeterminado es el método). En tales casos, se puede usar un especificador de uso del atributo. Por ejemplo, para que el atributo se aplica al valor devuelto, use el `returnvalue` especificador, como se indica a continuación:  
  
```cpp  
[returnvalue:Attr] int MyFn(double x)... // applies to return value  
```  
  
 Especificadores de uso del atributo son necesarias en las situaciones siguientes:  
  
-   Para especificar un atributo de nivel de ensamblado o módulo.  
  
-   Para especificar que un atributo se aplica al valor devuelto de un método, no el método:  
  
    ```cpp  
    [method:Attr] int MyFn(double x)...     // Attr applies to method  
    [returnvalue:Attr] int MyFn(double x)...// Attr applies to return value  
    [Attr] int MyFn(double x)...            // default: method  
    ```  
  
-   Para especificar que un atributo se aplica al descriptor de acceso de una propiedad, no la propiedad:  
  
    ```cpp  
    [method:MyAttr(123)] property int Property()    
    [property:MyAttr(123)] property int Property()  
    [MyAttr(123)] property int get_MyPropy() // default: property  
    ```  
  
-   Para especificar que un atributo se aplica al descriptor de acceso de un evento, no el evento:  
  
    ```cpp  
    delegate void MyDel();  
    ref struct X {  
       [field:MyAttr(123)] event MyDel* MyEvent;   //field  
       [event:MyAttr(123)] event MyDel* MyEvent;   //event  
       [MyAttr(123)] event MyDel* MyEvent;   // default: event  
    }  
    ```  
  
 Un especificador de uso del atributo se aplica solo al atributo que le sigue inmediatamente; Es decir  
  
```cpp  
[returnvalue:Attr1, Attr2]  
```  
  
 es diferente de  
  
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
  
## <a name="see-also"></a>Vea también  
 [Atributos definidos por el usuario](../windows/user-defined-attributes-cpp-component-extensions.md)