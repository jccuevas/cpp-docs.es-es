---
title: Reflexión (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- typeid keyword [C++]
- reflection [C++}, about reflection
- metadata, reflection
- GetType method
- .NET Framework [C++], reflection
- data types [C++], reflection
- reflection [C++}
- plug-ins [C++]
- reflection [C++}, plug-ins
- assemblies [C++], enumerating data types in
- public types [C++]
- reflection [C++], external assemblies
- assemblies [C++]
- data types [C++], enumerating
- public members [C++]
ms.assetid: 46b6ff4a-e441-4022-8892-78e69422f230
ms.openlocfilehash: 9d7d2623608d7dab27de78567582c7043468e98f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444023"
---
# <a name="reflection-ccli"></a>Reflexión (C++/CLI)

La reflexión permite inspeccionar tipos de datos conocidos en tiempo de ejecución. La reflexión permite enumerar los tipos de datos en un ensamblado especificado y detectar los miembros de una clase o de un tipo de valor dados. Esto es cierto independientemente de si el tipo se conoce o se hace referencia a él en tiempo de compilación. Esto hace que la reflexión sea una característica útil para las herramientas de desarrollo y de administración de código.

Tenga en cuenta que el nombre del ensamblado es el nombre seguro (vea [crear y utilizar ensamblados](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)), que incluye la versión del ensamblado, la referencia cultural y la información de firma. Observe además que puede recuperarse el nombre del espacio de nombres en el que se define el tipo de datos, al igual que el nombre de la clase base.

La manera más común de obtener acceso a las características de reflexión es utilizar el método <xref:System.Object.GetType%2A>. Este método se proporciona por [System:: Object](https://msdn.microsoft.com/library/system.object.aspx), desde que se derivan todas las clases de recolección.

> [!NOTE]
> Solo se permite la reflexión en un .exe compilado con el compilador de Visual C++ si se ha creado el archivo .exe con el **/CLR: pure** o **/CLR: safe** opciones del compilador. El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no está disponible en Visual Studio 2017. Consulte [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md) para obtener más información.

Para obtener más información, consulte [Namespace System.Reflection](https://msdn.microsoft.com/library/system.reflection.aspx)

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

Igual que con el `GetType` método, el [typeid](../windows/typeid-cpp-component-extensions.md) operador devuelve un puntero a un **tipo** objeto, por lo que este código indica el nombre de tipo **System.Int32**. Mostrar los nombres de tipo es la característica de reflexión más básica, pero una técnica posiblemente más útil es inspeccionar o detectar los valores válidos para los tipos enumerados. Esto puede hacerse mediante el uso de estático **enum:: GetNames** funcione, que devuelve una matriz de cadenas, cada una con un valor de enumeración en forma de texto.  El ejemplo siguiente recupera una matriz de cadenas que se describen los valores de enumeración de valor para el **opciones** enum (CLR) y los muestra en un bucle.

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

Si el código anterior se compila en un archivo DLL denominado vcpp_reflection_6.dll, puede utilizar la reflexión para inspeccionar el contenido de este ensamblado. Esto implica el uso de la función de la API de reflexión estática [Assembly:: Load](https://msdn.microsoft.com/library/system.reflection.assembly.load.aspx) para cargar el ensamblado. Esta función devuelve la dirección de un **ensamblado** objeto que, a continuación, se puede consultar acerca de los módulos y tipos de dentro.

Una vez que el sistema de reflexión carga correctamente el ensamblado, una matriz de **tipo** se recuperan los objetos con el [Assembly:: GetTypes](https://msdn.microsoft.com/library/system.reflection.assembly.gettypes.aspx) función. Cada elemento de la matriz contiene información sobre un tipo diferente, aunque en este caso solo se define una clase. Mediante un bucle, cada **tipo** en esta matriz se consultan los miembros de tipo usando el **Type:: GetMembers** función. Esta función devuelve una matriz de **MethodInfo** objetos, cada objeto que contiene información acerca de la función miembro, el miembro de datos o la propiedad del tipo.

Tenga en cuenta que la lista de métodos incluye las funciones explícitamente definidos en **TestClass** y las funciones hereden implícitamente de la **System:: Object** clase. Por haberse descrito en .NET y no en la sintaxis de Visual C++, las propiedades aparecen como el miembro de datos subyacente al que se obtiene acceso mediante funciones get o set. Las funciones get y set aparecen en esta lista con métodos periódicas. La reflexión se admite a través de Common Language Runtime, no del compilador de Visual C++.

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

## <a name="implement"></a> Cómo: implementar una arquitectura de componentes complementarios mediante reflexión

Ejemplos de código siguientes muestran el uso de reflexión para implementar una arquitectura de "complemento" simple. La primera lista es la aplicación y el segundo es el complemento. La aplicación es un formulario de múltiples documentos que se rellena mediante cualquier clase basada en formularios que se encuentra en la DLL del complemento proporcionada como un argumento de línea de comandos.

La aplicación intenta cargar el ensamblado proporcionado usando el <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> método. Si es correcto, los tipos dentro del ensamblado se enumeran utilizando el <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName> método. Cada tipo, a continuación, se comprueba para el uso de la compatibilidad del <xref:System.Type.IsAssignableFrom%2A?displayProperty=fullName> método. En este ejemplo, las clases que se encuentran en el ensamblado proporcionado se deben derivar de la <xref:System.Windows.Forms.Form> clase para calificar como un complemento.

A continuación, se crean instancias de las clases compatibles con el <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> método, que acepta un <xref:System.Type> como argumento y devuelve un puntero a una nueva instancia. Cada nueva instancia, a continuación, se adjunta al formulario y se muestra.

Tenga en cuenta que el <xref:System.Reflection.Assembly.Load%2A> método no acepta nombres de ensamblado que incluyen la extensión de archivo. La función principal en la aplicación recorta cualquier extensión proporcionada, por lo que el siguiente ejemplo de código funciona en ambos casos.

### <a name="example"></a>Ejemplo

El código siguiente define la aplicación que acepta los complementos. Como primer argumento, se debe proporcionar un nombre de ensamblado. Este ensamblado debe contener al menos un público <xref:System.Windows.Forms.Form> tipo derivado.

```cpp
// plugin_application.cpp
// compile with: /clr /c
#using <system.dll>
#using <system.drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;
using namespace System::Reflection;

ref class PluggableForm : public Form  {
public:
   PluggableForm() {}
   PluggableForm(Assembly^ plugAssembly) {
      Text = "plug-in example";
      Size = Drawing::Size(400, 400);
      IsMdiContainer = true;

      array<Type^>^ types = plugAssembly->GetTypes( );
      Type^ formType = Form::typeid;

      for (int i = 0 ; i < types->Length ; i++) {
         if (formType->IsAssignableFrom(types[i])) {
            // Create an instance given the type description.
            Form^ f = dynamic_cast<Form^> (Activator::CreateInstance(types[i]));
            if (f) {
               f->Text = types[i]->ToString();
               f->MdiParent = this;
               f->Show();
            }
         }
      }
   }
};

int main() {
   Assembly^ a = Assembly::LoadFrom("plugin_application.exe");
   Application::Run(gcnew PluggableForm(a));
}
```

### <a name="example"></a>Ejemplo

El código siguiente define tres clases derivadas de <xref:System.Windows.Forms.Form>. Cuando el nombre del ensamblado resultante se pasa al archivo ejecutable en la lista anterior, cada una de estas clases se detectará y se crea una instancia, a pesar del hecho de que éstos no eran todas desconocidas para la aplicación de hospedaje en tiempo de compilación.

```cpp
// plugin_assembly.cpp
// compile with: /clr /LD
#using <system.dll>
#using <system.drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;
using namespace System::Reflection;
using namespace System::Drawing;

public ref class BlueForm : public Form {
public:
   BlueForm() {
      BackColor = Color::Blue;
   }
};

public ref class CircleForm : public Form {
protected:
   virtual void OnPaint(PaintEventArgs^ args) override {
      args->Graphics->FillEllipse(Brushes::Green, ClientRectangle);
   }
};

public ref class StarburstForm : public Form {
public:
   StarburstForm(){
      BackColor = Color::Black;
   }
protected:
   virtual void OnPaint(PaintEventArgs^ args) override {
      Pen^ p = gcnew Pen(Color::Red, 2);
      Random^ r = gcnew Random( );
      Int32 w = ClientSize.Width;
      Int32 h = ClientSize.Height;
      for (int i=0; i<100; i++) {
         float x1 = w / 2;
         float y1 = h / 2;
         float x2 = r->Next(w);
         float y2 = r->Next(h);
         args->Graphics->DrawLine(p, x1, y1, x2, y2);
      }
   }
};
```

## <a name="enumerate"></a> Cómo: Enumerar tipos de datos en ensamblados mediante reflexión

El código siguiente muestra la enumeración de tipos y miembros mediante públicos <xref:System.Reflection>.

Dado el nombre de un ensamblado, en el directorio local o en la GAC, el código siguiente intenta abrir el ensamblado y recuperar descripciones. Si se realiza correctamente, se muestra cada tipo con sus miembros públicos.

Tenga en cuenta que <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> requiere que no se use ninguna extensión de archivo. Por lo tanto, usa "mscorlib.dll" como un argumento de línea de comandos se producirá un error, aunque el uso de "mscorlib" dará como resultado la presentación de los tipos de .NET Framework. Si se proporciona ningún nombre de ensamblado, el código detectará y notifican a los tipos en el ensamblado actual (el EXE resultante de este código).

### <a name="example"></a>Ejemplo

```cpp
// self_reflection.cpp
// compile with: /clr
using namespace System;
using namespace System::Reflection;
using namespace System::Collections;

public ref class ExampleType {
public:
   ExampleType() {}
   void Func() {}
};

int main() {
   String^ delimStr = " ";
   array<Char>^ delimiter = delimStr->ToCharArray( );
   array<String^>^ args = Environment::CommandLine->Split( delimiter );

// replace "self_reflection.exe" with an assembly from either the local
// directory or the GAC
   Assembly^ a = Assembly::LoadFrom("self_reflection.exe");
   Console::WriteLine(a);

   int count = 0;
   array<Type^>^ types = a->GetTypes();
   IEnumerator^ typeIter = types->GetEnumerator();

   while ( typeIter->MoveNext() ) {
      Type^ t = dynamic_cast<Type^>(typeIter->Current);
      Console::WriteLine("   {0}", t->ToString());

      array<MemberInfo^>^ members = t->GetMembers();
      IEnumerator^ memberIter = members->GetEnumerator();
      while ( memberIter->MoveNext() ) {
         MemberInfo^ mi = dynamic_cast<MemberInfo^>(memberIter->Current);
         Console::Write("      {0}", mi->ToString( ) );
         if (mi->MemberType == MemberTypes::Constructor)
            Console::Write("   (constructor)");

         Console::WriteLine();
      }
      count++;
   }
   Console::WriteLine("{0} types found", count);
}
```

## <a name="see-also"></a>Vea también

- [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
