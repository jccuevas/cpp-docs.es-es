---
title: Atributos definidos por el usuario (C++/CLI y C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
ms.openlocfilehash: 6d200c36946e7bc7d441c2c4db1bdfe96d4aeef9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516000"
---
# <a name="user-defined-attributes--ccli-and-ccx"></a>Atributos definidos por el usuario (C++/CLI y C++/CX)

C++/CLI y C++/CX le permiten crear atributos específicos de la plataforma que extienden los metadatos de una interfaz, clase o estructura, método, parámetro o enumeración. Estos atributos son distintos de los [atributos de C++ estándar](../cpp/attributes.md).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

Puede aplicar atributos de C++/CX a las propiedades, pero no a constructores ni a métodos.

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

La información y sintaxis presentada en este tema está pensada para sustituir a la información presentada en el [atributo](../windows/attributes/attribute.md).

Puede definir un atributo personalizado definiendo un tipo, haciendo de <xref:System.Attribute> una clase base del tipo y, de forma opcional, aplicando el atributo <xref:System.AttributeUsageAttribute>.

Para obtener más información, consulte:

- [Destinos de atributo](attribute-targets-cpp-component-extensions.md)

- [Tipos de parámetros de atributo](attribute-parameter-types-cpp-component-extensions.md)

Para obtener información sobre cómo firmar ensamblados en Visual C++, consulte [Ensamblados de nombre seguro (Firma de ensamblados) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

En el ejemplo siguiente se muestra cómo definir un atributo personalizado.

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

En el siguiente ejemplo se muestran algunas características importantes de los atributos personalizados. Por ejemplo, aquí se muestra un uso habitual de los atributos personalizados: la creación de una instancia de un servidor que se puede describir a sí mismo a los clientes.

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

```Output
Service Priority = 0

Service Access = Write

Service Priority = 3

Service Access = Write

Service Priority = 1

Service Access = Read
```

El tipo `Object^` reemplaza el tipo de datos variable. En el siguiente ejemplo se define un atributo personalizado que toma una matriz de `Object^` como parámetros.

Los argumentos de atributo deben ser constantes en tiempo de compilación; en la mayoría de los casos, deben ser literales constantes.

Consulte [typeid](typeid-cpp-component-extensions.md) para obtener información sobre cómo devolver un valor de System::Type de un bloque de atributos personalizado.

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

El runtime requiere que la parte pública de la clase de atributos personalizada sea serializable.  Al crear atributos personalizados, los argumentos con nombre de su atributo personalizado se limitan a las constantes en tiempo de compilación  (piense en ello como una secuencia de bits anexados al diseño de la clase en los metadatos).

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

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)