---
title: "Reflexi&#243;n (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".NET Framework [C++], reflexión"
  - "tipos de datos [C++], reflexión"
  - "GetType (método)"
  - "metadatos, reflexión"
  - "reflexión [C++}"
  - "reflexión [C++}, acerca de la reflexión"
  - "typeid (palabra clave) [C++]"
ms.assetid: 46b6ff4a-e441-4022-8892-78e69422f230
caps.latest.revision: 24
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Reflexi&#243;n (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La reflexión permite inspeccionar tipos de datos conocidos en tiempo de ejecución.  La reflexión permite enumerar los tipos de datos en un ensamblado especificado y detectar los miembros de una clase o de un tipo de valor dados.  Esto es cierto independientemente de si el tipo se conoce o se hace referencia a él en tiempo de compilación.  Esto hace que la reflexión sea una característica útil para las herramientas de desarrollo y de administración de código.  
  
 Observe que el nombre del ensamblado es un nombre seguro \(vea [Ensamblados con nombre seguro](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)\) que incluye información de la versión de ensamblado, de referencia cultural y de firma.  Observe además que puede recuperarse el nombre del espacio de nombres en el que se define el tipo de datos, al igual que el nombre de la clase base.  
  
 La manera más común de obtener acceso a las características de reflexión es utilizar el método <xref:System.Object.GetType%2A>.  Este método lo proporciona [System::Object](https://msdn.microsoft.com/en-us/library/system.object.aspx), del que derivan todas las clases de recolección de elementos no utilizados.  
  
 La reflexión en un archivo .exe creado con el compilador de Visual C\+\+ se permite si el archivo .exe se ha creado con las opciones del compilador **\/clr:pure** o **\/clr:safe**.  Vea [\/clr \(Compilación de Common Language Runtime\)](../build/reference/clr-common-language-runtime-compilation.md) para obtener más información.  
  
 Temas de esta sección:  
  
-   [Cómo: Implementar una arquitectura de componentes complementarios mediante reflexión](../dotnet/how-to-implement-a-plug-in-component-architecture-using-reflection-cpp-cli.md)  
  
-   [Cómo: Enumerar tipos de datos en ensamblados mediante reflexión](../dotnet/how-to-enumerate-data-types-in-assemblies-using-reflection-cpp-cli.md)  
  
 Para obtener más información, vea [System.Reflection \(Espacio de nombres\)](https://msdn.microsoft.com/en-us/library/system.reflection.aspx).  
  
## Ejemplo  
 El método `GetType` devuelve un puntero a un objeto de clase <xref:System.Type>, que describe el tipo en el que se basa el objeto. \(El objeto **Type** no contiene ninguna información específica de la instancia\). Un elemento de esta clase es el nombre completo del tipo, que puede mostrarse de la siguiente forma:  
  
 Observe que el nombre de tipo incluye el ámbito completo en el que se define el tipo, incluido el espacio de nombres, y se muestra en la sintaxis de .NET con un punto como operador de resolución de ámbito.  
  
```  
// vcpp_reflection.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   String ^ s = "sample string";  
   Console::WriteLine("full type name of '{0}' is '{1}'", s, s->GetType());  
}  
```  
  
  **el nombre de tipo completo de la 'cadena de ejemplo' es 'System.String'**   
## Ejemplo  
 Los tipos de valor pueden utilizarse también con la función `GetType` pero se les debe aplicar primero una conversión boxing.  
  
```  
// vcpp_reflection_2.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   Int32 i = 100;   
   Object ^ o = i;  
   Console::WriteLine("type of i = '{0}'", o->GetType());  
}  
```  
  
  **tipo de i \= 'System.Int32'**   
## Ejemplo  
 Al igual que ocurre con el método `GetType`, el operador [typeid](../Topic/typeid%20%20\(C++%20Component%20Extensions\).md) devuelve un puntero a un objeto **Type**, por lo que este código indica el nombre de tipo **System.Int32**.  Mostrar los nombres de tipo es la característica de reflexión más básica, pero una técnica posiblemente más útil es inspeccionar o detectar los valores válidos para los tipos enumerados.  Esto puede realizarse mediante la función estática **Enum::GetNames**, que devuelve una matriz de cadenas, cada una de las cuales contiene un valor de enumeración en formato de texto.  El ejemplo siguiente recupera una matriz de cadenas que describe los valores de enumeración de valor para la enumeración **Options** \(CLR\) y los muestra en un bucle.  
  
 Si se agrega la cuarta opción a la enumeración **Options**, este código notificará la nueva opción sin recompilación, incluso si la enumeración se define en un ensamblado independiente.  
  
```  
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
  
  **hay 3 opciones en la enumeración 'Options'**  
**0: Opción1**  
**1: Opción2**  
**2: Opción3**  
**el valor de 'o' es Opción2**   
## Ejemplo  
 El objeto `GetType` admite un número de miembros y propiedades que pueden utilizarse para examinar un tipo.  Este código recupera y muestra una parte de esta información:  
  
```  
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
  
  **información de tipo para 'String':**  
**nombre de ensamblado: mscorlib, Version\=1.0.5000.0, Culture\=neutral,**   
**PublicKeyToken\=b77a5c561934e089**  
**espacio de nombres: System**  
**tipo base: System.Object**  
**es una matriz: False**  
**es una clase: True**   
## Ejemplo  
 La reflexión también permite la enumeración de tipos dentro de un ensamblado y de miembros dentro de las clases.  Para demostrar esta característica, defina una clase simple:  
  
```  
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
  
## Ejemplo  
 Si el código anterior se compila en un archivo DLL denominado vcpp\_reflection\_6.dll, puede utilizar la reflexión para inspeccionar el contenido de este ensamblado.  Esto implica utilizar la función API de reflexión estática [Assembly::Load](https://msdn.microsoft.com/en-us/library/system.reflection.assembly.load.aspx) para cargar el ensamblado.  Esta función devuelve la dirección de un objeto **Assembly** al que se le pueden consultar los módulos y tipos que incluye.  
  
 Cuando el sistema de reflexión haya cargado correctamente el ensamblado, se recupera una matriz de objetos **Type** con la función [Assembly::GetTypes](https://msdn.microsoft.com/en-us/library/system.reflection.assembly.gettypes.aspx).  Cada elemento de la matriz contiene información sobre un tipo diferente, aunque en este caso solo se define una clase.  Mediante un bucle, se consultan los miembros de tipos de cada elemento **Type** a través de la función **Type::GetMembers**.  Esta función devuelve una matriz de objetos **MethodInfo**, cada uno de los cuales contiene información acerca de la función miembro, el miembro de datos o la propiedad en el tipo.  
  
 Observe que la lista de métodos incluye las funciones definidas explícitamente en **TestClass** y las funciones heredadas implícitamente de la clase **System::Object**.  Por haberse descrito en .NET y no en la sintaxis de Visual C\+\+, las propiedades aparecen como el miembro de datos subyacente al que se obtiene acceso mediante funciones get o set.  Las funciones get y set aparecen en esta lista con métodos periódicas.  La reflexión se admite a través de Common Language Runtime, no del compilador de Visual C\+\+.  
  
 Aunque utilice este código para examinar un ensamblado que haya definido, también puede utilizarlo para examinar ensamblados de .NET.  Por ejemplo, si cambia TestAssembly por mscorlib, se mostrará una lista de todos los tipos y métodos definidos en mscorlib.dll.  
  
```  
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
  
## Vea también  
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)