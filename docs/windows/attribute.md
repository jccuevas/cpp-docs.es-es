---
title: "attribute | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.attribute"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__typeof keyword"
  - "custom attributes, creating"
  - "attribute attribute"
  - "attributes [C++], custom"
ms.assetid: 8cb3489f-65c4-44ea-b0aa-3c3c6b15741d
caps.latest.revision: 18
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# attribute
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Permite crear un atributo personalizado.  
  
## Sintaxis  
  
```  
  
      [ attribute(  
   AllowOn,  
   AllowMultiple=boolean,  
   Inherited=boolean  
) ]  
```  
  
#### Parámetros  
 *AllowOn*  
 Especifica los elementos del lenguaje a los que se puede aplicar el atributo personalizado.  El valor predeterminado es **System::AttributeTargets::Todo** \(vea [System:: AttributeTargets](https://msdn.microsoft.com/en-us/library/system.attributetargets.aspx)\).  
  
 `AllowMultiple`  
 Especifica si el atributo personalizado se puede aplicar repetidamente a una construcción.  El valor predeterminado es **FALSO**.  
  
 `Inherited`  
 Indica si el atributo a ser heredado por las subclases.  El compilador no proporciona ninguna compatibilidad especial para esta funcionalidad; es el trabajo de los consumidores del atributo \(Reflexión, por ejemplo\) respetar esta información.  si `Inherited` es **TRUE**, se hereda el atributo.  Si `AllowMultiple` es **TRUE**, el atributo creará en el miembro derivado; si `AllowMultiple` es **FALSO**, el atributo reemplazará \(o reemplazar\) en la herencia.  Si `Inherited` es **FALSO**, no será heredado.  El valor predeterminado es **TRUE**.  
  
## Comentarios  
  
> [!NOTE]
>  El atributo de `attribute` ahora está desusada.  Utilice el atributo System.Attribute de Common Language Runtime a directamente para crear attirbutes definido por el usuario.  Para obtener más información, vea [Atributos definidos por el usuario](../windows/user-defined-attributes-cpp-component-extensions.md).  
  
 Define [atributo personalizado](../windows/custom-attributes-cpp.md) colocando el atributo de `attribute` en una definición de clase administrada o struct.  el nombre de la clase es el atributo personalizado.  Por ejemplo:  
  
```  
[ attribute(Parameter) ]  
public ref class MyAttr {};  
```  
  
 define un atributo denominado MyAttr que se puede aplicar a los parámetros.  La clase debe ser pública si el atributo va a usar en otros ensamblados.  
  
> [!NOTE]
>  Para evitar conflictos de espacio de nombres, todos los nombres de atributo finalizan implícitamente con “atributo”; en este ejemplo, el nombre de atributo y la clase es realmente MyAttrAttribute, pero MyAttr y MyAttrAttribute se pueden usar indistintamente.  
  
 Los constructores públicos de la clase definen los parámetros sin nombre de atributo.  Los constructores sobrecargados permiten varias maneras de especificar el atributo, en un atributo personalizado que se definirán la manera siguiente:  
  
```  
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
  
 Los miembros de datos públicos y las propiedades de la clase son los parámetros con nombre opcionales del atributo:  
  
```  
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
  
 Para obtener una lista de tipos de parámetro posibles de atributos, vea [atributos personalizados](../windows/custom-attributes-cpp.md).  
  
 Vea [Atributos definidos por el usuario](../windows/user-defined-attributes-cpp-component-extensions.md) para obtener una explicación sobre los destinos del atributo.  
  
 El atributo de `attribute` tiene un parámetro de `AllowMultiple` que especifica si el atributo personalizado no es reutilizable o multiuso \(puede aparecer más de una vez en la misma entidad\).  
  
```  
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
  
 Las clases de atributos personalizadas son derivadas directa o indirectamente de <xref:System.ComponentModel.AttributeCollection.%23ctor%2A>, que crean definiciones de atributo de identificador en metadatos rápidas y fáciles.  El atributo de `attribute` implica herencia de system:: El atributo, por lo que la derivación explícita no es necesarios:  
  
```  
[ attribute(Class) ]  
ref class MyAttr  
```  
  
 es equivalente a  
  
```  
[ attribute(Class) ]  
ref class MyAttr : System::Attribute   // OK, but redundant.  
```  
  
 `attribute` es un alias de <xref:System.AttributeUsageAttribute?displayProperty=fullName> \(no AttributeAttribute; esto es una excepción al atributo que llama regla de aprendizaje de nombres\).  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|`ref` **clase**, **struct de referencia**|  
|**repetible**|No|  
|**Atributos necesarios**|None|  
|**Atributos no válidos**|None|  
  
 Para obtener más información sobre los contextos de atributos, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Ejemplo  
  
```  
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
  
## Ejemplo  
 El argumento con nombre de `Inherited` especifica si un atributo personalizado aplicados en una clase base aparecerá en la reflexión de una clase derivada.  
  
```  
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
  
  **2**   
## Vea también  
 [Attributes Alphabetical Reference](../windows/attributes-alphabetical-reference.md)   
 [Custom Attributes](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)