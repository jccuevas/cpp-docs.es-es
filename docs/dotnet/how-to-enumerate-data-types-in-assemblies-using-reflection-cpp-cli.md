---
title: "C&#243;mo: Enumerar tipos de datos en ensamblados mediante reflexi&#243;n (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "ensamblados [C++]"
  - "ensamblados [C++], enumerar tipos de datos"
  - "tipos de datos [C++], enumerar"
  - "miembros públicos [C++]"
  - "tipos públicos [C++]"
  - "reflexión [C++], ensamblados externos"
ms.assetid: c3578e6d-bb99-4599-80e1-ab795305f878
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Enumerar tipos de datos en ensamblados mediante reflexi&#243;n (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El código siguiente muestra la enumeración de tipos y miembros públicos mediante <xref:System.Reflection>.  
  
 Dado el nombre de un ensamblado, ya sea en el directorio local o en la GAC, el código que sigue trata de abrir el ensamblado y recuperar descripciones.  Si lo consigue, cada tipo se muestra con sus miembros públicos.  
  
 Observe que <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> requiere que no se utilice ninguna extensión de archivo.  Por tanto, el uso de "mscorlib.dll" como argumento de la línea de comandos generará un error, mientras que el uso de "mscorlib" resultará en la presentación de los tipos de .NET Framework.  Si no se proporciona ningún nombre de ensamblado, el código detectará y creará informes de los tipos incluidos en el ensamblado actual \(el EXE que resulta de este código\).  
  
## Ejemplo  
  
```  
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
  
## Vea también  
 [Reflexión](../dotnet/reflection-cpp-cli.md)