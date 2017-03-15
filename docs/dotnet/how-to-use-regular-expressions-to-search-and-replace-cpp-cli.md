---
title: "C&#243;mo: Utilizar expresiones regulares para buscar y reemplazar (C++/CLI) | Microsoft Docs"
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
  - "expresiones regulares [C++], buscar y reemplazar"
  - "Replace (método)"
  - "buscar y reemplazar"
ms.assetid: 12fe3e18-fe10-4b25-a221-19dc5eab3821
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Utilizar expresiones regulares para buscar y reemplazar (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El ejemplo de código siguiente muestra cómo se puede utilizar la clase de expresión regular <xref:System.Text.RegularExpressions.Regex> para efectuar operaciones de buscar y reemplazar.  Esto se consigue con el método <xref:System.Text.RegularExpressions.Regex.Replace%2A>.  La versión empleada toma dos cadenas como entrada: la cadena que se va a modificar y la que se va a insertar en lugar de las secciones \(si las hay\) que se corresponden con el modelo dado al objeto <xref:System.Text.RegularExpressions.Regex>.  
  
 Este código reemplaza todos los dígitos de una cadena por caracteres de subrayado \(\_\) y, a continuación, reemplaza aquéllos por una cadena vacía, con lo que se logra quitarlos eficazmente.  El mismo efecto se puede lograr en un solo paso, pero aquí se utilizan dos pasos a modo de demostración.  
  
## Ejemplo  
  
```  
// regex_replace.cpp  
// compile with: /clr  
#using <System.dll>  
using namespace System::Text::RegularExpressions;  
using namespace System;  
  
int main()  
{  
   String^ before = "The q43uick bro254wn f0ox ju4mped";  
   Console::WriteLine("original  : {0}", before);  
  
   Regex^ digitRegex = gcnew Regex("(?<digit>[0-9])");  
   String^ after = digitRegex->Replace(before, "_");  
   Console::WriteLine("1st regex : {0}", after);  
  
   Regex^ underbarRegex = gcnew Regex("_");  
   String^ after2 = underbarRegex->Replace(after, "");  
   Console::WriteLine("2nd regex : {0}", after2);  
  
   return 0;  
}  
```  
  
## Vea también  
 [Expresiones regulares de .NET Framework](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)