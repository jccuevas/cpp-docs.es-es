---
title: "C&#243;mo: Utilizar expresiones regulares para reorganizar los datos (C++/CLI) | Microsoft Docs"
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
  - "datos [C++], reorganizar"
  - "expresiones regulares [C++], reorganizar los datos"
ms.assetid: 5f91e777-9471-424e-ba75-dca3d1b49e42
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Utilizar expresiones regulares para reorganizar los datos (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El ejemplo de código siguiente muestra cómo se puede utilizar la compatibilidad de expresiones regulares de .NET Framework para reorganizar datos o cambiar el formato de los datos.  El ejemplo de código siguiente utiliza las clases <xref:System.Text.RegularExpressions.Regex> y <xref:System.Text.RegularExpressions.Match> para extraer nombres y apellidos de una cadena y luego mostrar estos elementos en orden inverso.  
  
 La clase <xref:System.Text.RegularExpressions.Regex> se utiliza para construir una expresión regular que describe el formato actual de los datos.  Se supone que los dos nombres están separados por una coma y pueden utilizar cualquier cantidad de espacio en blanco alrededor de la coma.  El método <xref:System.Text.RegularExpressions.Match> se utiliza a continuación para analizar cada cadena.  Si funciona correctamente, los nombres y los apellidos se recuperan del objeto <xref:System.Text.RegularExpressions.Match> y se muestran.  
  
## Ejemplo  
  
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
  
## Vea también  
 [Expresiones regulares de .NET Framework](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)