---
title: atributo (atributo de COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.attribute
dev_langs:
- C++
helpviewer_keywords:
- __typeof keyword
- custom attributes, creating
- attribute attribute
- attributes [C++/CLI], custom
ms.assetid: 8cb3489f-65c4-44ea-b0aa-3c3c6b15741d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7fc581d35b1bb1c36808f77783e9724ac6ed6def
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48792203"
---
# <a name="attribute"></a>Atributo

Le permite crear un atributo personalizado.

## <a name="syntax"></a>Sintaxis

```cpp
[ attribute(
   AllowOn,
   AllowMultiple=boolean,
   Inherited=boolean
) ]
```

### <a name="parameters"></a>Parámetros

*AllowOn*<br/>
Especifica los elementos del lenguaje al que se puede aplicar el atributo personalizado. El valor predeterminado es `System::AttributeTargets::All` (consulte [System::AttributeTargets](https://msdn.microsoft.com/library/system.attributetargets.aspx)).

*AllowMultiple*<br/>
Especifica si el atributo personalizado se puede aplicar varias veces a una construcción. Valor predeterminado es FALSE.

*Heredado*<br/>
Indica si el atributo se va a ser heredadas por las subclases. El compilador no proporciona compatibilidad especial para esta funcionalidad; es el trabajo de los consumidores de atributo (`Reflection`, por ejemplo) para respetar esta información. Si *Inherited* es TRUE, el atributo es heredado. Si *AllowMultiple* es TRUE, el atributo se acumulará en el miembro derivado; si *AllowMultiple* es FALSE, el atributo invalidará (o reemplace) en la herencia. Si *Inherited* es FALSE, no se hereda el atributo. Valor predeterminado es TRUE.

## <a name="remarks"></a>Comentarios

> [!NOTE]
> El **atributo** atributo está en desuso.  Utilice el atributo de tiempo de ejecución de lenguaje común `System.Attribute` a directamente para crear attirbutes definido por el usuario. Para obtener más información, consulte [User-Defined Attributes](../user-defined-attributes-cpp-component-extensions.md).

Define un [atributo personalizado](custom-attributes-cpp.md) colocando el **atributo** atributo en una definición de clase o estructura administrada. El nombre de la clase es el atributo personalizado. Por ejemplo:

```cpp
[ attribute(Parameter) ]
public ref class MyAttr {};
```

define un atributo denominado `MyAttr` que se puede aplicar a parámetros de función. La clase debe ser pública si el atributo se va a usar en otros ensamblados.

> [!NOTE]
> Para evitar conflictos de espacio de nombres, todos los nombres de atributo implícitamente terminan con "Attribute"; en este ejemplo, el nombre del atributo y la clase es realmente `MyAttrAttribute`, pero `MyAttr` y `MyAttrAttribute` se pueden usar indistintamente.

Los constructores públicos de la clase definen parámetros sin nombre del atributo. Los constructores sobrecargados permiten varias formas de especificar el atributo, por lo que un atributo personalizado que define del siguiente modo:

```cpp
// cpp_attr_ref_attribute.cpp
// compile with: /c /clr
using namespace System;
[ attribute(AttributeTargets::Class) ]   // apply attribute to classes
public ref class MyAttr {
public:
   MyAttr() {}   // Constructor with no parameters
   MyAttr(int arg1) {}   // Constructor with one parameter
};

[MyAttr]
ref class ClassA {};   // Attribute with no parameters

[MyAttr(123)]
ref class ClassB {};   // Attribute with one parameter
```

Los miembros de datos públicos y propiedades de la clase son los parámetros con nombre opcional del atributo:

```cpp
// cpp_attr_ref_attribute_2.cpp
// compile with: /c /clr
using namespace System;
[ attribute(AttributeTargets::Class) ]
ref class MyAttr {
public:
   // Property Priority becomes attribute's named parameter Priority
    property int Priority {
       void set(int value) {}
       int get() { return 0;}
   }
   // Data member Version becomes attribute's named parameter Version
   int Version;
   MyAttr() {}   // constructor with no parameters
   MyAttr(int arg1) {}   // constructor with one parameter
};

[MyAttr(123, Version=2)]
ref class ClassC {};
```

Para obtener una lista de tipos de parámetro de atributo posibles, consulte [atributos personalizados](custom-attributes-cpp.md).

Consulte [User-Defined Attributes](../user-defined-attributes-cpp-component-extensions.md) para obtener información sobre los destinos de atributo.

El **atributo** atributo tiene un *AllowMultiple* parámetro que especifica si el atributo personalizado es un solo uso o multiuse (puede aparecer más de una vez en la misma entidad).

```cpp
// cpp_attr_ref_attribute_3.cpp
// compile with: /c /clr
using namespace System;
[ attribute(AttributeTargets::Class, AllowMultiple = true) ]
ref struct MyAttr {
   MyAttr(){}
};   // MyAttr is a multiuse attribute

[MyAttr, MyAttr()]
ref class ClassA {};
```

Clases de atributos personalizados se derivan directa o indirectamente <xref:System.ComponentModel.AttributeCollection.%23ctor%2A>, lo que hace que identifica las definiciones de atributos en metadatos rápida y sencilla. El **atributo** atributo implica la herencia de `System::Attribute`, por lo que no es necesario derivación explícita:

```cpp
[ attribute(Class) ]
ref class MyAttr
```

es equivalente a

```cpp
[ attribute(Class) ]
ref class MyAttr : System::Attribute   // OK, but redundant.
```

**atributo** es un alias para <xref:System.AttributeUsageAttribute?displayProperty=fullName> (no AttributeAttribute; se trata de una excepción a la regla de nomenclatura de atributo).

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase ref**, **un struct ref**|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, vea [contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_attribute_4.cpp
// compile with: /c /clr
using namespace System;
[attribute(AttributeTargets::Class)]
ref struct ABC {
   ABC(Type ^) {}
};

[ABC(String::typeid)]   // typeid operator yields System::Type ^
ref class MyClass {};
```

## <a name="example"></a>Ejemplo

El `Inherited` argumento con nombre se especifica si un atributo personalizado aplicado en una clase base se mostrará en la reflexión de una clase derivada.

```cpp
// cpp_attr_ref_attribute_5.cpp
// compile with: /clr
using namespace System;
using namespace System::Reflection;

[attribute( AttributeTargets::Method, Inherited=false )]
ref class BaseOnlyAttribute { };

[attribute( AttributeTargets::Method, Inherited=true )]
ref class DerivedTooAttribute { };

ref struct IBase {
public:
   [BaseOnly, DerivedToo]
   virtual void meth() {}
};

// Reflection on Derived::meth will show DerivedTooAttribute
// but not BaseOnlyAttribute.
ref class Derived : public IBase {
public:
   virtual void meth() override {}
};

int main() {
   IBase ^ pIB = gcnew Derived;

   MemberInfo ^ pMI = pIB->GetType( )->GetMethod( "meth" );
   array<Object ^> ^ pObjs = pMI->GetCustomAttributes( true );
   Console::WriteLine( pObjs->Length ) ;
}
```

```Output
2
```

## <a name="see-also"></a>Vea también

[Referencia alfabética de los atributos](attributes-alphabetical-reference.md)  
