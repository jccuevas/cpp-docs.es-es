---
title: "Cómo: analizar cadenas con el método Split (C++ / CLI) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- parsing strings [C++]
- examples [C++], strings
- regular expressions [C++], parsing strings
- Split method, parsing strings
- strings [C++], parsing
ms.assetid: d52d2539-5ebb-4716-86b3-07314dd7e4bd
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: be3443995966c5ce7b9c2fe4a156c8d6c79069d4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-parse-strings-using-the-split-method-ccli"></a>Cómo: Analizar cadenas con el método Split (C++/CLI)
En el ejemplo de código siguiente se muestra cómo utilizar el método <xref:System.String.Split%2A?displayProperty=fullName> para extraer todas las palabras de una cadena. Se construye una cadena que contiene varios tipos de perfiladores de palabras y, a continuación, se analiza llamando a <xref:System.String.Split%2A> con una lista de los perfiladores. Finalmente, se muestran todas las palabras de la frase independientemente.  
  
## <a name="example"></a>Ejemplo  
  
```  
// regex_split.cpp  
// compile with: /clr  
using namespace System;  
  
int main()  
{  
   String^ delimStr = " ,.:\t";  
   Console::WriteLine( "delimiter : '{0}'", delimStr );  
   array<Char>^ delimiter = delimStr->ToCharArray( );  
   array<String^>^ words;  
   String^ line = "one\ttwo three:four,five six seven";  
  
   Console::WriteLine( "text : '{0}'", line );  
   words = line->Split( delimiter );  
   Console::WriteLine( "Number of Words : {0}", words->Length );  
   for (int word=0; word<words->Length; word++)  
      Console::WriteLine( "{0}", words[word] );  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Expresiones regulares de .NET Framework](/dotnet/standard/base-types/regular-expressions)   
 [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)