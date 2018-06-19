---
title: 'Cómo: utilizar expresiones regulares para buscar coincidencias simples (C++ / CLI) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- substrings, simple matches
- searching, exact substring matches
- strings [C++], exact substring matching
- regular expressions [C++], simple matching
- IsMatch method
ms.assetid: 4661f6f3-0f6d-48f2-abe4-cb4770bf9bd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a4b9f56419759080b20857d0eef3ba48f9c040ab
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33128285"
---
# <a name="how-to-use-regular-expressions-for-simple-matching-ccli"></a>Cómo: Utilizar expresiones regulares para buscar coincidencias simples (C++/CLI)
En el ejemplo de código siguiente se utiliza expresiones regulares para buscar coincidencias exactas de subcadenas. La búsqueda se realiza mediante el método estático <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> método, que toma dos cadenas como entrada. La primera es la cadena que se va a buscar y el segundo es el patrón que se va a buscar.  
  
## <a name="example"></a>Ejemplo  
  
```  
// regex_simple.cpp  
// compile with: /clr  
#using <System.dll>  
  
using namespace System;  
using namespace System::Text::RegularExpressions;  
  
int main()  
{  
   array<String^>^ sentence =   
   {  
      "cow over the moon",  
      "Betsy the Cow",  
      "cowering in the corner",  
      "no match here"  
   };  
  
   String^ matchStr = "cow";  
   for (int i=0; i<sentence->Length; i++)  
   {  
      Console::Write( "{0,24}", sentence[i] );  
      if ( Regex::IsMatch( sentence[i], matchStr,  
                     RegexOptions::IgnoreCase ) )  
         Console::WriteLine("  (match for '{0}' found)", matchStr);  
      else  
         Console::WriteLine("");  
   }  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Expresiones regulares de .NET Framework](/dotnet/standard/base-types/regular-expressions)   
 [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)