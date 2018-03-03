---
title: Atributo destinos (extensiones de componentes de C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- custom attributes, targets
ms.assetid: b4e6e224-da77-4520-b6e6-b96846e0ebc1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bdf54706673a3679582b93448f420d4a63680dee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="attribute-targets-c-component-extensions"></a>Destinos de atributo (Extensiones de componentes de C++)
Especificadores de uso de atributos permiten especificar los destinos de atributo.  Cada atributo se definió para aplicarse a determinados elementos de lenguaje. Por ejemplo, se podría definir un atributo para que solo se aplican a las clases y structs.  La siguiente lista muestra los elementos sintácticos en el que se puede utilizar un atributo personalizado. Combinaciones de estos valores (utilizando lógica o) se puede usar.  
  
 Para especificar el destino de atributo, para pasar uno o varios <xref:System.AttributeTargets> enumeradores para <xref:System.AttributeUsageAttribute> al definir el atributo.  
  
 La siguiente es una lista de los destinos de atributo válido:  
  
-   `All`(se aplica a todas las construcciones)  
  
    ```  
  
    using namespace System;  
    [AttributeUsage(AttributeTargets::All)]  
    ref class Attr : public Attribute {};  
  
    [assembly:Attr];  
  
    ```  
  
-   `Assembly`(se aplica a un ensamblado como un todo)  
  
    ```  
  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Assembly)]  
    ref class Attr : public Attribute {};  
  
    [assembly:Attr];  
  
    ```  
  
-   `Module`(se aplica a un módulo como un todo)  
  
    ```  
  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Module)]  
    ref class Attr : public Attribute {};  
  
    [module:Attr];  
  
    ```  
  
-   `Class`  
  
    ```  
  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Class)]  
    ref class Attr : public System::Attribute {};  
  
    [Attr]   // same as [class:Attr]  
    ref class MyClass {};  
  
    ```  
  
-   `Struct`  
  
    ```  
  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Struct)]  
    ref class Attr : public Attribute {};  
  
    [Attr]   // same as [struct:Attr]  
    value struct MyStruct{};  
  
    ```  
  
-   `enum`  
  
    ```  
  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Enum)]  
    ref class Attr : public Attribute {};  
  
    [Attr]   // same as [enum:Attr]  
    enum struct MyEnum{e, d};  
  
    ```  
  
-   `Constructor`  
  
    ```  
  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Constructor)]  
    ref class Attr : public Attribute {};  
  
    ref struct MyStruct{  
    [Attr] MyStruct(){}   // same as [constructor:Attr]  
    };  
  
    ```  
  
-   `Method`  
  
    ```  
  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Method)]  
    ref class Attr : public Attribute {};  
  
    ref struct MyStruct{  
    [Attr] void Test(){}   // same as [method:Attr]  
    };  
  
    ```  
  
-   `Property`  
  
    ```  
  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Property)]  
    ref class Attr : public Attribute {};  
  
    ref struct MyStruct{  
    [Attr] property int Test;   // same as [property:Attr]  
    };  
  
    ```  
  
-   `Field`  
  
    ```  
  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Field)]  
    ref class Attr : public Attribute {};  
  
    ref struct MyStruct{  
    [Attr] int Test;   // same as [field:Attr]  
    };  
  
    ```  
  
-   `Event`  
  
    ```  
  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Event)]  
    ref class Attr : public Attribute {};  
  
    delegate void ClickEventHandler(int, double);  
  
    ref struct MyStruct{  
    [Attr] event ClickEventHandler^ OnClick;   // same as [event:Attr]  
    };  
  
    ```  
  
-   `Interface`  
  
    ```  
  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Interface)]  
    ref class Attr : public Attribute {};  
  
    [Attr]   // same as [event:Attr]  
    interface struct MyStruct{};  
  
    ```  
  
-   `Parameter`  
  
    ```  
  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Parameter)]  
    ref class Attr : public Attribute {};  
  
    ref struct MyStruct{  
    void Test([Attr] int i);  
    void Test2([parameter:Attr] int i);  
    };  
  
    ```  
  
-   `Delegate`  
  
    ```  
  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Delegate)]  
    ref class Attr : public Attribute {};  
  
    [Attr] delegate void Test();  
    [delegate:Attr] delegate void Test2();  
  
    ```  
  
-   `ReturnValue`  
  
    ```  
  
    using namespace System;  
    [AttributeUsage(AttributeTargets::ReturnValue)]  
    ref class Attr : public Attribute {};  
  
    ref struct MyStruct {  
    // Note required specifier  
    [returnvalue:Attr] int Test() { return 0; }  
    };  
  
    ```  
  
 Normalmente, un atributo precede directamente al elemento de lenguaje al que se aplica. Sin embargo, en algunos casos, no es suficiente para determinar el destino del atributo la posición de un atributo. Considere este ejemplo:  
  
```  
[Attr] int MyFn(double x)...  
```  
  
 Sintácticamente, no hay ninguna manera de saber si el atributo está diseñado para aplicar al método o al valor devuelto del método (en este caso, el valor predeterminado es el método). En tales casos, se utiliza el especificador de uso de un atributo. Por ejemplo, para que el atributo se aplica al valor devuelto, utilice el `returnvalue` especificador, como se indica a continuación:  
  
```  
[returnvalue:Attr] int MyFn(double x)... // applies to return value  
```  
  
 Especificadores de uso de atributo son necesarias en las situaciones siguientes:  
  
-   Para especificar un atributo de nivel de ensamblado o módulo.  
  
-   Para especificar que un atributo se aplica al valor devuelto de un método, no el método:  
  
    ```  
    [method:Attr] int MyFn(double x)...     // Attr applies to method  
    [returnvalue:Attr] int MyFn(double x)...// Attr applies to return value  
    [Attr] int MyFn(double x)...            // default: method  
    ```  
  
-   Para especificar que un atributo se aplica al descriptor de acceso de una propiedad, no la propiedad:  
  
    ```  
    [method:MyAttr(123)] property int Property()    
    [property:MyAttr(123)] property int Property()  
    [MyAttr(123)] property int get_MyPropy() // default: property  
    ```  
  
-   Para especificar que un atributo se aplica al descriptor de acceso de un evento, no el evento:  
  
    ```  
    delegate void MyDel();  
    ref struct X {  
       [field:MyAttr(123)] event MyDel* MyEvent;   //field  
       [event:MyAttr(123)] event MyDel* MyEvent;   //event  
       [MyAttr(123)] event MyDel* MyEvent;   // default: event  
    }  
    ```  
  
 El especificador de uso de un atributo sólo se aplica a los atributos que sigue inmediatamente a él; Es decir  
  
```  
[returnvalue:Attr1, Attr2]  
```  
  
 es diferente de  
  
```  
[returnvalue:Attr1, returnvalue:Attr2]  
```  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 Este ejemplo muestra cómo especificar varios destinos.  
  
### <a name="code"></a>Código  
  
```  
  
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