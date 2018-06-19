---
title: 'Cómo: Enumerar tipos de datos mediante la reflexión (C++ / CLI) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- assemblies [C++], enumerating data types in
- public types [C++]
- reflection [C++], external assemblies
- assemblies [C++]
- data types [C++], enumerating
- public members [C++]
ms.assetid: c3578e6d-bb99-4599-80e1-ab795305f878
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5a4b85cb5af9d390d92bcca3e0462b0ae5b4d832
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135084"
---
# <a name="how-to-enumerate-data-types-in-assemblies-using-reflection-ccli"></a>Cómo: Enumerar tipos de datos en ensamblados mediante reflexión (C++/CLI)
El código siguiente muestra la enumeración de los tipos públicos y miembros mediante <xref:System.Reflection>.  
  
 Dado el nombre de un ensamblado, en el directorio local o en la GAC, el código siguiente intenta abrir el ensamblado y recuperar descripciones. Si es correcto, cada tipo se muestra con sus miembros públicos.  
  
 Tenga en cuenta que <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> requiere que no se use ninguna extensión de archivo. Por lo tanto, el uso de "mscorlib.dll" como un argumento de línea de comandos se producirá un error, aunque el uso de "mscorlib" dará como resultado la presentación de los tipos de .NET Framework. Si no se proporciona ningún nombre de ensamblado, el código detectará y notifican los tipos en el ensamblado actual (el EXE resultantes de este código).  
  
## <a name="example"></a>Ejemplo  
  
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
  
## <a name="see-also"></a>Vea también  
 [Reflexión (C++-CLI)](../dotnet/reflection-cpp-cli.md)