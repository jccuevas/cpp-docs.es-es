---
title: "Destinos de atributo (Extensiones de componentes de C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "atributos personalizados, destinos"
ms.assetid: b4e6e224-da77-4520-b6e6-b96846e0ebc1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Destinos de atributo (Extensiones de componentes de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especificadores de uso de atributos le permiten especificar los destinos de atributo.  Cada atributo se define para aplicar a ciertos elementos de lenguaje. Por ejemplo, se podría definir un atributo para aplicar sólo a clases y structs.  La siguiente lista muestra los elementos sintácticos en que se puede utilizar un atributo personalizado. Combinaciones de estos valores (utilizando lógica o) puede utilizarse.  
  
 Para especificar el destino de atributo, para pasar uno o más <xref:System.AttributeTargets> enumeradores a <xref:System.AttributeUsageAttribute> al definir el atributo.  
  
 La siguiente es una lista de los destinos de atributo válido:  
  
-   `All` (se aplica a todos los constructores)  
  
    ```  
  
    using namespace System;  
    [AttributeUsage(AttributeTargets::All)]  
    ref class Attr : public Attribute {};  
  
    [assembly:Attr];  
  
    ```  
  
-   `Assembly` (se aplica a un ensamblado como un todo)  
  
    ```  
  
    using namespace System;  
    [AttributeUsage(AttributeTargets::Assembly)]  
    ref class Attr : public Attribute {};  
  
    [assembly:Attr];  
  
    ```  
  
-   `Module` (se aplica a un módulo como un todo)  
  
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
  
 Normalmente, un atributo precede directamente el elemento de lenguaje al que se aplica. Sin embargo, en algunos casos, no es suficiente para determinar el destino del atributo la posición de un atributo. Considere este ejemplo:  
  
```  
[Attr] int MyFn(double x)...  
```  
  
 Sintácticamente, no hay ninguna manera de saber si se pretende que el atributo se aplica al método o al valor devuelto del método (en este caso, el valor predeterminado es el método). En tales casos, puede utilizarse un especificador de uso del atributo. Por ejemplo, para que el atributo se aplique al valor devuelto, utilice el `returnvalue` especificador, como sigue:  
  
```  
[returnvalue:Attr] int MyFn(double x)... // applies to return value  
```  
  
 Especificadores de uso de atributos son necesarios en las situaciones siguientes:  
  
-   Para especificar un atributo de nivel de ensamblado o módulo.  
  
-   Para especificar que un atributo se aplica al valor devuelto de un método, no al método:  
  
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
  
 Un especificador de uso de atributo sólo se aplica a los atributos que le sigue inmediatamente; Es decir  
  
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