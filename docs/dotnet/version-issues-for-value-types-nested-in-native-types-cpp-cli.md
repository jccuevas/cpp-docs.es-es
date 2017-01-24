---
title: "Problemas de versi&#243;n con tipos de valor anidados en tipos nativos (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "__nogc (declaraciones de tipos)"
  - "__value (palabra clave), problemas de anidación"
ms.assetid: 0a3b1a43-39c6-4b52-be2f-1074690188aa
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Problemas de versi&#243;n con tipos de valor anidados en tipos nativos (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Considere un componente de ensamblado firmado \(nombre seguro\) que se utiliza para compilar un ensamblado de cliente.  El componente contiene un tipo de valor que se usa en el cliente como tipo para un miembro de una unión nativa, una clase o una matriz.  Si una versión futura del componente cambia el tamaño o el diseño del tipo de valor, se debe volver a compilar el cliente.  
  
 Cree un archivo de claves con [sn.exe](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md) \(`sn -k mykey.snk`\).  
  
## Ejemplo  
 El ejemplo siguiente es el componente.  
  
```  
// nested_value_types.cpp  
// compile with: /clr /LD  
using namespace System::Reflection;  
[assembly:AssemblyVersion("1.0.0.*"),   
assembly:AssemblyKeyFile("mykey.snk")];  
  
public value struct S {  
   int i;  
   void Test() {  
      System::Console::WriteLine("S.i = {0}", i);  
   }  
};  
```  
  
## Ejemplo  
 Este ejemplo es el cliente:  
  
```  
// nested_value_types_2.cpp  
// compile with: /clr  
#using <nested_value_types.dll>  
  
struct S2 {  
   S MyS1, MyS2;  
};  
  
int main() {  
   S2 MyS2a, MyS2b;  
   MyS2a.MyS1.i = 5;  
   MyS2a.MyS2.i = 6;  
   MyS2b.MyS1.i = 10;  
   MyS2b.MyS2.i = 11;  
  
   MyS2a.MyS1.Test();  
   MyS2a.MyS2.Test();  
   MyS2b.MyS1.Test();  
   MyS2b.MyS2.Test();  
}  
```  
  
## Resultados  
  
```  
S.i = 5  
S.i = 6  
S.i = 10  
S.i = 11  
```  
  
### Comentarios  
 No obstante, si agrega otro miembro a `struct S` en nested\_value\_types.cpp, \(por ejemplo, `double d;`\) y vuelve a compilar el componente sin compilar de nuevo el cliente, el resultado es una excepción no controlada \(de tipo <xref:System.IO.FileLoadException?displayProperty=fullName>\).  
  
## Vea también  
 [Tipos administrados](../dotnet/managed-types-cpp-cli.md)