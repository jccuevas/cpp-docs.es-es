---
title: atributo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
- attributes [C++], custom
ms.assetid: 8cb3489f-65c4-44ea-b0aa-3c3c6b15741d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9826b689e2b8a640efe66e8625b97b3cec347acf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862067"
---
# <a name="attribute"></a>Atributo
Permite crear un atributo personalizado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ attribute(  
   AllowOn,  
   AllowMultiple=boolean,  
   Inherited=boolean  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 *AllowOn*  
 Especifica los elementos del lenguaje al que se puede aplicar el atributo personalizado. Valor predeterminado es **System::AttributeTargets::All** (consulte [System::AttributeTargets](https://msdn.microsoft.com/en-us/library/system.attributetargets.aspx)).  
  
 `AllowMultiple`  
 Especifica si el atributo personalizado se puede aplicar varias veces a una construcción. Valor predeterminado es **FALSE**.  
  
 `Inherited`  
 Indica si el atributo se va a ser heredadas por las subclases. El compilador no proporciona ninguna compatibilidad especial para esta funcionalidad; es el trabajo de los consumidores de atributo (por ejemplo, reflexión) respetan esta información. Si `Inherited` es **TRUE**, se hereda el atributo. Si `AllowMultiple` es **TRUE**, el atributo se acumulará en el miembro derivado; si `AllowMultiple` es **FALSE**, el atributo invalidará (o reemplazar) en la herencia. Si `Inherited` es **FALSE**, el atributo no se heredarán. Valor predeterminado es **TRUE**.  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  El `attribute` atributo está en desuso.  Utilice el atributo de tiempo de ejecución lenguaje System.Attribute común directamente para crear attirbutes definido por el usuario.  Para obtener más información, consulte [atributos definidos por el usuario](../windows/user-defined-attributes-cpp-component-extensions.md).  
  
 Defina un [atributo personalizado](../windows/custom-attributes-cpp.md) colocando el `attribute` atributo en una definición de clase o estructura administrada. El nombre de la clase es el atributo personalizado. Por ejemplo:  
  
```  
[ attribute(Parameter) ]  
public ref class MyAttr {};  
```  
  
 define un atributo denominado MyAttr que se pueden aplicar a los parámetros de función. La clase debe ser pública si el atributo se va a usar en otros ensamblados.  
  
> [!NOTE]
>  Para evitar conflictos de espacio de nombres, todos los nombres de atributos terminan implícitamente con "Attribute"; en este ejemplo, el nombre del atributo y la clase es realmente MyAttrAttribute pero MyAttr y MyAttrAttribute se pueden usar indistintamente.  
  
 Constructores públicos de la clase definen los parámetros del atributo sin nombre. Los constructores sobrecargados permiten varias formas de especificar el atributo, por lo que un atributo personalizado que define del siguiente modo:  
  
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
  
 Miembros de datos públicos y las propiedades de la clase son los parámetros del atributo opcional con nombre:  
  
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
  
 Para obtener una lista de tipos de parámetro posibles del atributo, vea [atributos personalizados](../windows/custom-attributes-cpp.md).  
  
 Vea [atributos definidos por el usuario](../windows/user-defined-attributes-cpp-component-extensions.md) para obtener información sobre los destinos de atributo.  
  
 El `attribute` atributo tiene un `AllowMultiple` parámetro que especifica si el atributo personalizado es un solo uso o múltiples usuarios (puede aparecer más de una vez en la misma entidad).  
  
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
  
 Clases de atributos personalizados se derivan directa o indirectamente <xref:System.ComponentModel.AttributeCollection.%23ctor%2A>, que hace que las definiciones de atributos en metadatos de forma rápida y fácil de identificar. El `attribute` atributo implica la herencia de System:: Attribute, por lo que no es necesario derivación explícita:  
  
```  
[ attribute(Class) ]  
ref class MyAttr  
```  
  
 es equivalente a  
  
```  
[ attribute(Class) ]  
ref class MyAttr : System::Attribute   // OK, but redundant.  
```  
  
 `attribute` es un alias para <xref:System.AttributeUsageAttribute?displayProperty=fullName> (no atributoAttribute; se trata de una excepción a la regla de asignación de nombres de atributo).  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|`ref` **clase**, **un struct ref**|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="example"></a>Ejemplo  
  
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
  
## <a name="example"></a>Ejemplo  
 El `Inherited` argumento con nombre especifica si un atributo personalizado que se aplica en una clase base se mostrará en la reflexión de una clase derivada.  
  
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
  
```Output  
2  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia alfabética de los atributos](../windows/attributes-alphabetical-reference.md)   
 [Atributos personalizados](http://msdn.microsoft.com/en-us/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)