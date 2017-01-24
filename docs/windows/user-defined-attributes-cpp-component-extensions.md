---
title: "Atributos definidos por el usuario (Extensiones de componentes de C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "atributos personalizados, extender metadatos"
  - "metadatos, extender"
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
caps.latest.revision: 27
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Atributos definidos por el usuario (Extensiones de componentes de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los atributos personalizados permiten ampliar los metadatos de una interfaz, clase o estructura, un método, un parámetro, o una enumeración.  
  
## Todos los runtimes  
 Todos los atributos personalizados admiten runtimes.  
  
## Windows en tiempo de ejecución  
 Los atributos de C\+\+\/CX sólo admiten propiedades, pero no constructores de atributos o métodos.  
  
### Comentarios  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
## Common Language Runtime  
 Los atributos personalizados permiten extender los metadatos de un elemento administrado.  Para obtener más información, vea [Atributos](../Topic/Extending%20Metadata%20Using%20Attributes.md).  
  
### Comentarios  
 La información y la sintaxis presentadas en este tema se ha diseñado para reemplazar la información mostrada en [attribute](../windows/attribute.md).  
  
 Puede definir un atributo personalizado definiendo un tipo y crear <xref:System.Attribute> una clase base para el tipo y opcionalmente aplicando el atributo de <xref:System.AttributeUsageAttribute> .  
  
 Por ejemplo, en Microsoft Transaction Server \(MTS\) 1,0, comportamiento con respecto a las transacciones, sincronización, equilibrio de carga, etc. se especificado mediante GUID personalizado incrustado en la biblioteca de tipos mediante el atributo personalizado ODL.  Por consiguiente, un cliente de un servidor de MTS podría determinar sus características leyendo la biblioteca de tipos.  En .NET Framework, el analógico de la biblioteca de tipos es metadatos, y el analógico de atributo personalizado ODL es atributos personalizados.  También, leer la biblioteca de tipos es análogo a utilizar la reflexión en tipos.  
  
 Para obtener más información, vea  
  
-   [Destinos de atributo](../windows/attribute-targets-cpp-component-extensions.md)  
  
-   [Tipos de parámetros de atributo](../windows/attribute-parameter-types-cpp-component-extensions.md)  
  
 Para obtener información sobre la firma de ensamblados en Visual C\+\+, vea [Ensamblados de nombre seguro \(Firma de ensamblados\)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
### Ejemplos  
 **Ejemplo**  
  
 El ejemplo siguiente se muestra cómo definir un atributo personalizado.  
  
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
  
 El ejemplo siguiente muestra algunas características importantes de atributos personalizados.  Por ejemplo, este ejemplo muestra un uso común de los atributos personalizados: crear instancias de un servidor que puede describirse totalmente a los clientes.  
  
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
  
 **Resultados**  
  
  **Mantenga presionada la prioridad \= 0**  
 **Mantenga Access \= la escritura**  
 **Mantenga presionada la prioridad \= 3**  
 **Mantenga Access \= la escritura**  
 **Mantenga presionada la prioridad \= 1**  
 **Mantenga Access \= leído** **Ejemplo**  
  
 El tipo de Object^ reemplaza el tipo de datos variant.  El ejemplo siguiente define un atributo personalizado que toma una matriz de Object^ como parámetros.  
  
 Los argumentos de atributo deben ser constantes en tiempo de compilación; en la mayoría de los casos, deben ser literales constantes.  
  
 Vea [typeid](../Topic/typeid%20%20\(C++%20Component%20Extensions\).md) para obtener información sobre cómo devolver un valor de System::Type de un bloque de atributos personalizados.  
  
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
  
 El tiempo de ejecución requiere que la parte pública de la clase de atributos personalizada debe ser serializable.  Al crear atributos personalizados, los argumentos con nombre del atributo personalizado se limitan a constantes en tiempo de compilación.  \(Piense en él como una secuencia de bits anexado al diseño de la clase de metadatos\).  
  
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
  
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)