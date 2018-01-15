---
title: Atributos (extensiones de componentes de C++) definido por el usuario | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9d974e8526f983801ed011520f7f78ff8c6cb564
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="user-defined-attributes--c-component-extensions"></a>Atributos definidos por el usuario (Extensiones de componentes de C++)
Atributos personalizados permiten ampliar los metadatos de una interfaz, clase o estructura, método, parámetro o enumeración.  
  
## <a name="all-runtimes"></a>Todos los runtimes  
 Todos los Runtimes admite atributos personalizados.  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
 C++ / atributos CX admite solo las propiedades, pero no atributo métodos o constructores.  
  
### <a name="remarks"></a>Comentarios  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 Atributos personalizados le permiten ampliar los metadatos de un elemento administrado. Para obtener más información, consulte [Attributes](/dotnet/standard/attributes/index) (Atributos).  
  
### <a name="remarks"></a>Comentarios  
 La información y la sintaxis que aparecen en este tema está pensado para sustituir la información presentada en [atributo](../windows/attribute.md).  
  
 Puede definir un atributo personalizado mediante la definición de un tipo y realice <xref:System.Attribute> una clase base para el tipo y, opcionalmente, aplicar el <xref:System.AttributeUsageAttribute> atributo.  
  
 Por ejemplo, en Microsoft Transaction Server (MTS) 1.0, comportamiento con respecto a las transacciones, sincronización, el equilibrio de carga, y así sucesivamente se especificó mediante GUID personalizados insertados en la biblioteca de tipos mediante el atributo personalizado ODL. Por lo tanto, un cliente de un servidor MTS podía determinar sus características leyendo la biblioteca de tipos. En .NET Framework, el equivalente de la biblioteca de tipos es los metadatos y del atributo personalizado ODL son atributos personalizados. Además, la lectura de la biblioteca de tipos es análogo a utilizando la reflexión en los tipos.  
  
 Para obtener más información, vea  
  
-   [Destinos de atributo](../windows/attribute-targets-cpp-component-extensions.md)  
  
-   [Tipos de parámetro de atributo](../windows/attribute-parameter-types-cpp-component-extensions.md)  
  
 Para obtener información sobre cómo firmar ensamblados en Visual C++, vea [ensamblados de nombre seguro (firma de ensamblados) (C++ / CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/clr**  
  
### <a name="examples"></a>Ejemplos  
 **Ejemplo**  
  
 El ejemplo siguiente muestra cómo definir un atributo personalizado.  
  
```cpp  
// user_defined_attributes.cpp  
// compile with: /clr /c  
using namespace System;  
  
[AttributeUsage(AttributeTargets::All)]  
ref struct Attr : public Attribute {  
   Attr(bool i){}  
   Attr(){}  
};  
  
[Attr]  
ref class MyClass {};  
```  
  
 **Ejemplo**  
  
 El ejemplo siguiente muestra algunas características importantes de atributos personalizados. Por ejemplo, este ejemplo muestra un uso común de los atributos personalizados: crear instancias de un servidor que se puede describir completamente a los clientes.  
  
```cpp  
// extending_metadata_b.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Reflection;  
  
public enum class Access { Read, Write, Execute };  
  
// Defining the Job attribute:  
[AttributeUsage(AttributeTargets::Class, AllowMultiple=true )]  
public ref class Job : Attribute {  
public:  
   property int Priority {  
      void set( int value ) { m_Priority = value; }  
      int get() { return m_Priority; }  
   }  
  
   // You can overload constructors to specify Job attribute in different ways  
   Job() { m_Access = Access::Read; }  
   Job( Access a ) { m_Access = a; }  
   Access m_Access;  
  
protected:  
   int m_Priority;  
};  
  
interface struct IService {  
   void Run();  
};  
  
   // Using the Job attribute:  
   // Here we specify that QueryService is to be read only with a priority of 2.  
   // To prevent namespace collisions, all custom attributes implicitly   
   // end with "Attribute".   
  
[Job( Access::Read, Priority=2 )]  
ref struct QueryService : public IService {  
   virtual void Run() {}  
};  
  
// Because we said AllowMultiple=true, we can add multiple attributes   
[Job(Access::Read, Priority=1)]  
[Job(Access::Write, Priority=3)]  
ref struct StatsGenerator : public IService {  
   virtual void Run( ) {}  
};  
  
int main() {  
   IService ^ pIS;  
   QueryService ^ pQS = gcnew QueryService;  
   StatsGenerator ^ pSG = gcnew StatsGenerator;  
  
   //  use QueryService  
   pIS = safe_cast<IService ^>( pQS );  
  
   // use StatsGenerator  
   pIS = safe_cast<IService ^>( pSG );  
  
   // Reflection  
   MemberInfo ^ pMI = pIS->GetType();  
   array <Object ^ > ^ pObjs = pMI->GetCustomAttributes(false);  
  
   // We can now quickly and easily view custom attributes for an   
   // Object through Reflection */  
   for( int i = 0; i < pObjs->Length; i++ ) {  
      Console::Write("Service Priority = ");  
      Console::WriteLine(static_cast<Job^>(pObjs[i])->Priority);  
      Console::Write("Service Access = ");  
      Console::WriteLine(static_cast<Job^>(pObjs[i])->m_Access);  
   }  
}  
```  
  
 **Salida**  
  
```Output  
Service Priority = 0  
  
Service Access = Write  
  
Service Priority = 3  
  
Service Access = Write  
  
Service Priority = 1  
  
Service Access = Read  
```  
  
 **Ejemplo**  
  
 El objeto ^ tipo reemplaza al tipo de datos variant. En el ejemplo siguiente se define un atributo personalizado que toma una matriz de objetos ^ como parámetros.  
  
 Argumentos de atributo deben ser constantes de tiempo de compilación; en la mayoría de los casos, deben ser literales constantes.  
  
 Vea [typeid](../windows/typeid-cpp-component-extensions.md) para obtener información sobre cómo devolver un valor de System:: Type de un bloque de atributos personalizados.  
  
```cpp  
// extending_metadata_e.cpp  
// compile with: /clr /c  
using namespace System;  
[AttributeUsage(AttributeTargets::Class | AttributeTargets::Method)]  
public ref class AnotherAttr : public Attribute {  
public:  
   AnotherAttr(array<Object^>^) {}  
   array<Object^>^ var1;  
};  
  
// applying the attribute  
[ AnotherAttr( gcnew array<Object ^> { 3.14159, "pi" }, var1 = gcnew array<Object ^> { "a", "b" } ) ]  
public ref class SomeClass {};  
```  
  
 **Ejemplo**  
  
 El tiempo de ejecución requiere que la parte pública de la clase de atributo personalizado debe ser serializable.  Al crear atributos personalizados, los argumentos con nombre del atributo personalizado se limitan a constantes en tiempo de compilación.  (Considerar como una secuencia de bits anexada al diseño de clase en los metadatos.)  
  
```cpp  
// extending_metadata_f.cpp  
// compile with: /clr /c  
using namespace System;  
ref struct abc {};  
  
[AttributeUsage( AttributeTargets::All )]  
ref struct A : Attribute {  
   A( Type^ ) {}  
   A( String ^ ) {}  
   A( int ) {}  
};  
  
[A( abc::typeid )]  
ref struct B {};  
```  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)