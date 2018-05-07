---
title: Problemas de versión con tipos de valor anidados en tipos nativos (C++ / CLI) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __nogc type declarations
- __value keyword, issues when nesting
ms.assetid: 0a3b1a43-39c6-4b52-be2f-1074690188aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4c4f2598594930f49c1217c937c9142b3f84a47e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="version-issues-for-value-types-nested-in-native-types-ccli"></a>Problemas de versión con tipos de valor anidados en tipos nativos (C++/CLI)
Considere la posibilidad de un componente de ensamblado firmado (nombre seguro) usado para generar un ensamblado de cliente. El componente contiene un tipo de valor que se usa en el cliente como el tipo de un miembro de una unión nativa, una clase o una matriz. Si una versión futura del componente cambia el tamaño o el diseño del tipo de valor, se debe volver a compilar el cliente.  
  
 Crear un archivo de clave con [sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) (`sn -k mykey.snk`).  
  
## <a name="example"></a>Ejemplo  
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
  
## <a name="example"></a>Ejemplo  
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
  
## <a name="output"></a>Salida  
  
```  
S.i = 5  
S.i = 6  
S.i = 10  
S.i = 11  
```  
  
### <a name="comments"></a>Comentarios  
 Sin embargo, si agrega otro miembro del `struct S` en nested_value_types.cpp, (por ejemplo, `double d;`) y vuelva a compilar el componente sin tener que recompilar el cliente, el resultado es una excepción no controlada (de tipo <xref:System.IO.FileLoadException?displayProperty=fullName>).  
  
## <a name="see-also"></a>Vea también  
 [Tipos administrados (C++/CLI)](../dotnet/managed-types-cpp-cli.md)