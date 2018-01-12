---
title: "Cómo: utilizar expresiones regulares para reorganizar los datos (C++ / CLI) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- regular expressions [C++], rearranging data
- data [C++], rearranging
ms.assetid: 5f91e777-9471-424e-ba75-dca3d1b49e42
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bf60fff6c15313a6f7df1104f67c1f043f885eac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-regular-expressions-to-rearrange-data-ccli"></a>Cómo: Utilizar expresiones regulares para reorganizar los datos (C++/CLI)
En el ejemplo de código siguiente se muestra cómo se puede utilizar la compatibilidad con expresiones regulares de .NET Framework para reorganizar o cambiar el formato de datos. El siguiente ejemplo de código utiliza el <xref:System.Text.RegularExpressions.Regex> y <xref:System.Text.RegularExpressions.Match> clases para extraer nombres y apellidos de una cadena y, a continuación, mostrar estos elementos en orden inverso.  
  
 La <xref:System.Text.RegularExpressions.Regex> clase se utiliza para construir una expresión regular que describe el formato actual de los datos. Los dos nombres se supone que estar separados por una coma y pueden utilizar cualquier cantidad de espacio en blanco alrededor de la coma. El <xref:System.Text.RegularExpressions.Match> método, a continuación, se usa para analizar cada cadena. Si se realiza correctamente, los nombres y apellidos se recuperan de la <xref:System.Text.RegularExpressions.Match> del objeto y se muestra.  
  
## <a name="example"></a>Ejemplo  
  
```  
// regex_reorder.cpp  
// compile with: /clr  
#using <System.dll>  
using namespace System;  
using namespace Text::RegularExpressions;  
  
int main()  
{  
   array<String^>^ name =   
   {  
      "Abolrous, Sam",   
      "Berg,Matt",   
      "Berry , Jo",  
      "www.contoso.com"  
   };  
  
   Regex^ reg = gcnew Regex("(?<last>\\w*)\\s*,\\s*(?<first>\\w*)");  
  
   for ( int i=0; i < name->Length; i++ )  
   {  
      Console::Write( "{0,-20}", name[i] );  
      Match^ m = reg->Match( name[i] );  
      if ( m->Success )  
      {  
         String^ first = m->Groups["first"]->Value;  
         String^ last = m->Groups["last"]->Value;  
         Console::WriteLine("{0} {1}", first, last);  
      }  
      else  
         Console::WriteLine("(invalid)");  
   }  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Expresiones regulares de .NET Framework](/dotnet/standard/base-types/regular-expressions)   
 [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)