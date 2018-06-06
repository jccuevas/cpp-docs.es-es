---
title: Reflexión (C++ / CLI) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- typeid keyword [C++]
- reflection [C++}, about reflection
- metadata, reflection
- GetType method
- .NET Framework [C++], reflection
- data types [C++], reflection
- reflection [C++}
ms.assetid: 46b6ff4a-e441-4022-8892-78e69422f230
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d41d7f627a50dd1a09f4256fbd8448d82c6d5f27
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705249"
---
# <a name="reflection-ccli"></a>Reflexión (C++/CLI)

La reflexión permite inspeccionar tipos de datos conocidos en tiempo de ejecución. La reflexión permite enumerar los tipos de datos en un ensamblado especificado y detectar los miembros de una clase o de un tipo de valor dados. Esto es cierto independientemente de si el tipo se conoce o se hace referencia a él en tiempo de compilación. Esto hace que la reflexión sea una característica útil para las herramientas de desarrollo y de administración de código.

Tenga en cuenta que el nombre del ensamblado es el nombre seguro (vea [crear y utilizar ensamblados](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)), que incluye la versión del ensamblado, la referencia cultural y la información de firma. Observe además que puede recuperarse el nombre del espacio de nombres en el que se define el tipo de datos, al igual que el nombre de la clase base.

La manera más común de obtener acceso a las características de reflexión es utilizar el método <xref:System.Object.GetType%2A>. Este método se proporciona por [System:: Object](https://msdn.microsoft.com/en-us/library/system.object.aspx), desde que se derivan todas las clases de recolección.

> [!NOTE]
> Solo se permite la reflexión en un .exe generado con el compilador de Visual C++ si el .exe se genera con el **/CLR: pure** o **/CLR: safe** opciones del compilador. El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no está disponible en Visual Studio de 2017. Vea [/clr (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) para obtener más información.

Para obtener más información, vea [System.Reflection Namespace](https://msdn.microsoft.com/en-us/library/system.reflection.aspx)

## <a name="example-gettype"></a>Ejemplo: GetType

El método `GetType` devuelve un puntero a un objeto de clase <xref:System.Type>, que describe el tipo en el que se basa el objeto. (El **tipo** objeto no contiene ninguna información específica de la instancia.) Un elemento de esta clase es el nombre completo del tipo, que puede mostrarse de la siguiente forma:

Observe que el nombre de tipo incluye el ámbito completo en el que se define el tipo, incluido el espacio de nombres, y se muestra en la sintaxis de .NET con un punto como operador de resolución de ámbito.

```cpp
// vcpp_reflection.cpp
// compile with: /clr
using namespace System;
int main() {
   String ^ s = "sample string";
   Console::WriteLine("full type name of '{0}' is '{1}'", s, s->GetType());
}
```

```Output
full type name of 'sample string' is 'System.String'
```

## <a name="example-boxed-value-types"></a>Ejemplo: tipos de valor con conversión boxing

Los tipos de valor pueden utilizarse también con la función `GetType` pero se les debe aplicar primero una conversión boxing.

```cpp
// vcpp_reflection_2.cpp
// compile with: /clr
using namespace System;
int main() {
   Int32 i = 100; 
   Object ^ o = i;
   Console::WriteLine("type of i = '{0}'", o->GetType());
}
```

```Output
type of i = 'System.Int32'
```

## <a name="example-typeid"></a>Ejemplo: typeid

Al igual que con la `GetType` método, el [typeid](../windows/typeid-cpp-component-extensions.md) operador devuelve un puntero a un **tipo** objeto, por lo que este código indica el nombre de tipo **System.Int32**. Mostrar los nombres de tipo es la característica de reflexión más básica, pero una técnica posiblemente más útil es inspeccionar o detectar los valores válidos para los tipos enumerados. Esto puede realizarse mediante el método estático **enum:: GetNames** funcione, que devuelve una matriz de cadenas, cada una con un valor de enumeración en formato de texto.  El ejemplo siguiente recupera una matriz de cadenas que describen los valores de enumeración de valor para el **opciones** enum (CLR) y lo muestra en un bucle.

Si se agrega una cuarta opción a la **opciones** enumeración, este código notificará la nueva opción sin recompilación, incluso si la enumeración se define en un ensamblado independiente.

```cpp
// vcpp_reflection_3.cpp
// compile with: /clr
using namespace System;

enum class Options {   // not a native enum
   Option1, Option2, Option3
};

int main() {
   array<String^>^ names = Enum::GetNames(Options::typeid);

   Console::WriteLine("there are {0} options in enum '{1}'", 
               names->Length, Options::typeid);

   for (int i = 0 ; i < names->Length ; i++)
      Console::WriteLine("{0}: {1}", i, names[i]);

   Options o = Options::Option2;
   Console::WriteLine("value of 'o' is {0}", o);
}
```

```Output
there are 3 options in enum 'Options'
0: Option1
1: Option2
2: Option3
value of 'o' is Option2
```

## <a name="example-gettype-members-and-properties"></a>Ejemplo: GetType miembros y propiedades

El objeto `GetType` admite un número de miembros y propiedades que pueden utilizarse para examinar un tipo. Este código recupera y muestra una parte de esta información:

```cpp
// vcpp_reflection_4.cpp
// compile with: /clr
using namespace System;
int main() {
   Console::WriteLine("type information for 'String':");
   Type ^ t = String::typeid;

   String ^ assemblyName = t->Assembly->FullName;
   Console::WriteLine("assembly name: {0}", assemblyName);

   String ^ nameSpace = t->Namespace;
   Console::WriteLine("namespace: {0}", nameSpace);

   String ^ baseType = t->BaseType->FullName;
   Console::WriteLine("base type: {0}", baseType);

   bool isArray = t->IsArray;
   Console::WriteLine("is array: {0}", isArray);

   bool isClass = t->IsClass;
   Console::WriteLine("is class: {0}", isClass);
}
```

```Output
type information for 'String':
assembly name: mscorlib, Version=1.0.5000.0, Culture=neutral, 
PublicKeyToken=b77a5c561934e089
namespace: System
base type: System.Object
is array: False
is class: True
```

## <a name="example-enumeration-of-types"></a>Ejemplo: enumeración de tipos

La reflexión también permite la enumeración de tipos dentro de un ensamblado y de miembros dentro de las clases. Para demostrar esta característica, defina una clase simple:

```cpp
// vcpp_reflection_5.cpp
// compile with: /clr /LD
using namespace System;
public ref class TestClass {
   int m_i;
public:
   TestClass() {}
   void SimpleTestMember1() {}
   String ^ SimpleMember2(String ^ s) { return s; } 
   int TestMember(int i) { return i; }
   property int Member {
      int get() { return m_i; }
      void set(int i) { m_i = i; }
   }
};
```

## <a name="example-inspection-of-assemblies"></a>Ejemplo: inspección de ensamblados

Si el código anterior se compila en un archivo DLL denominado vcpp_reflection_6.dll, puede utilizar la reflexión para inspeccionar el contenido de este ensamblado. Esto implica el uso de la función de la API de reflexión estática [Assembly:: Load](https://msdn.microsoft.com/en-us/library/system.reflection.assembly.load.aspx) para cargar el ensamblado. Esta función devuelve la dirección de un **ensamblado** objeto que, a continuación, se pueden consultar acerca de los módulos y tipos de.

Una vez que el sistema de reflexión cargado correctamente el ensamblado, una matriz de **tipo** objetos se recupera con el [Assembly:: GetTypes](https://msdn.microsoft.com/en-us/library/system.reflection.assembly.gettypes.aspx) función. Cada elemento de la matriz contiene información sobre un tipo diferente, aunque en este caso solo se define una clase. Mediante un bucle, cada **tipo** en esta matriz se consulta sobre los miembros de tipo usando el **Type:: GetMembers** función. Esta función devuelve una matriz de **MethodInfo** objetos, cada objeto que contiene información acerca de la función miembro, el miembro de datos o la propiedad en el tipo.

Tenga en cuenta que la lista de métodos incluye las funciones explícitamente definido en **TestClass** y las funciones heredaron implícitamente de la **System:: Object** clase. Por haberse descrito en .NET y no en la sintaxis de Visual C++, las propiedades aparecen como el miembro de datos subyacente al que se obtiene acceso mediante funciones get o set. Las funciones get y set aparecen en esta lista con métodos periódicas. La reflexión se admite a través de Common Language Runtime, no del compilador de Visual C++.

Aunque utilice este código para examinar un ensamblado que haya definido, también puede utilizarlo para examinar ensamblados de .NET. Por ejemplo, si cambia TestAssembly por mscorlib, se mostrará una lista de todos los tipos y métodos definidos en mscorlib.dll.

```cpp
// vcpp_reflection_6.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;
using namespace System::Reflection;
int main() {
   Assembly ^ a = nullptr;
   try {
      // load assembly -- do not use file extension
      // will look for .dll extension first
      // then .exe with the filename
      a = Assembly::Load("vcpp_reflection_5");
   }
   catch (FileNotFoundException ^ e) {
      Console::WriteLine(e->Message);
      return -1;
   }

   Console::WriteLine("assembly info:");
   Console::WriteLine(a->FullName);
   array<Type^>^ typeArray = a->GetTypes();

   Console::WriteLine("type info ({0} types):", typeArray->Length);

   int totalTypes = 0;
   int totalMembers = 0;
   for (int i = 0 ; i < typeArray->Length ; i++) {
      // retrieve array of member descriptions
      array<MemberInfo^>^ member = typeArray[i]->GetMembers();

      Console::WriteLine("  members of {0} ({1} members):", 
      typeArray[i]->FullName, member->Length);
      for (int j = 0 ; j < member->Length ; j++) {
         Console::Write("       ({0})", 
         member[j]->MemberType.ToString() );
         Console::Write("{0}  ", member[j]);
         Console::WriteLine("");
         totalMembers++;
      }
      totalTypes++;
   }
   Console::WriteLine("{0} total types, {1} total members",
   totalTypes, totalMembers);
}
```

## <a name="see-also"></a>Vea también

- [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
