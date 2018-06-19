---
title: 'Cómo: analizar cadenas utilizando expresiones regulares (C++ / CLI) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parsing strings [C++]
- examples [C++], strings
- regular expressions [C++], parsing strings
- strings [C++], parsing
ms.assetid: 5b0c7ca3-9bba-4389-a45c-6d373cff91b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5940a59d7e9b4e68f289848523710594621e73d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33131103"
---
# <a name="how-to-parse-strings-using-regular-expressions-ccli"></a>Cómo: Analizar cadenas utilizando expresiones regulares (C++/CLI)
En el siguiente ejemplo de código se muestra el análisis de una cadena sencilla mediante la clase <xref:System.Text.RegularExpressions.Regex> del espacio de nombres <xref:System.Text.RegularExpressions?displayProperty=fullName>. Se crea una cadena que contiene varios tipos de descriptores de palabras. A continuación, se analiza la cadena mediante las clases <xref:System.Text.RegularExpressions.Regex> y <xref:System.Text.RegularExpressions.Match>. Finalmente, se muestran todas las palabras de la frase independientemente.  
  
## <a name="example"></a>Ejemplo  
  
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
  
## <a name="see-also"></a>Vea también  
 [Expresiones regulares de .NET Framework](/dotnet/standard/base-types/regular-expressions)   
 [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)