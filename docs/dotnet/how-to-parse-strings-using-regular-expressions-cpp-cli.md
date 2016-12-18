---
title: "C&#243;mo: Analizar cadenas utilizando expresiones regulares (C++/CLI) | Microsoft Docs"
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
  - "ejemplos [C++], cadenas"
  - "analizar cadenas [C++]"
  - "expresiones regulares [C++], analizar cadenas"
  - "cadenas [C++], analizar"
ms.assetid: 5b0c7ca3-9bba-4389-a45c-6d373cff91b0
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Analizar cadenas utilizando expresiones regulares (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el siguiente ejemplo de código se muestra el análisis de una cadena sencilla mediante la clase <xref:System.Text.RegularExpressions.Regex> del espacio de nombres <xref:System.Text.RegularExpressions?displayProperty=fullName>.  Se crea una cadena que contiene varios tipos de descriptores de palabras.  A continuación, se analiza la cadena mediante las clases <xref:System.Text.RegularExpressions.Regex> y <xref:System.Text.RegularExpressions.Match>.  Después se muestra cada palabra en la frase individualmente.  
  
## Ejemplo  
  
```  
// regex_parse.cpp  
// compile with: /clr  
#using <system.dll>  
  
using namespace System;  
using namespace System::Text::RegularExpressions;  
  
int main( )  
{  
   int words = 0;  
   String^ pattern = "[a-zA-Z]*";  
   Console::WriteLine( "pattern : '{0}'", pattern );  
   Regex^ regex = gcnew Regex( pattern );  
  
   String^ line = "one\ttwo three:four,five six  seven";     
   Console::WriteLine( "text : '{0}'", line );  
   for( Match^ match = regex->Match( line );   
        match->Success; match = match->NextMatch( ) )   
   {  
      if( match->Value->Length > 0 )  
      {  
         words++;  
         Console::WriteLine( "{0}", match->Value );  
      }  
   }  
   Console::WriteLine( "Number of Words : {0}", words );  
  
   return 0;  
}  
```  
  
## Vea también  
 [Expresiones regulares de .NET Framework](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)