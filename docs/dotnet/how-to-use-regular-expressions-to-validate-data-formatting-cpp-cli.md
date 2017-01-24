---
title: "C&#243;mo: Utilizar expresiones regulares para validar el formato de los datos (C++/CLI) | Microsoft Docs"
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
  - "datos [C++], aplicar formato"
  - "expresiones regulares [C++], validar el formato de los datos"
  - "cadenas [C++], aplicar formato"
ms.assetid: 225775c3-3efc-4734-bde2-1fdf73e3d397
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Utilizar expresiones regulares para validar el formato de los datos (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el siguiente ejemplo de código se muestra la forma de utilizar expresiones regulares para comprobar el formato de una cadena  En el siguiente ejemplo de código, la cadena debería contener un número de teléfono válido.  En el siguiente ejemplo de código se utiliza la cadena "\\d{3}\-\\d{3}\-\\d{4}" para indicar que cada campo representa un número de teléfono válido.  La "d" de esta cadena indica un dígito y el argumento situado a continuación de cada "d" indica el número de dígitos que deben estar presentes.  En este caso, el número debe estar separado por guiones.  
  
## Ejemplo  
  
```  
// regex_validate.cpp  
// compile with: /clr  
#using <System.dll>  
  
using namespace System;  
using namespace Text::RegularExpressions;  
  
int main()  
{  
   array<String^>^ number =   
   {  
      "123-456-7890",   
      "444-234-22450",   
      "690-203-6578",   
      "146-893-232",  
      "146-839-2322",  
      "4007-295-1111",   
      "407-295-1111",   
      "407-2-5555",   
   };  
  
   String^ regStr = "^\\d{3}-\\d{3}-\\d{4}$";  
  
   for ( int i = 0; i < number->Length; i++ )  
   {  
      Console::Write( "{0,14}", number[i] );  
  
      if ( Regex::IsMatch( number[i], regStr ) )  
         Console::WriteLine(" - valid");  
      else  
         Console::WriteLine(" - invalid");  
   }  
   return 0;  
}  
```  
  
## Vea también  
 [Expresiones regulares de .NET Framework](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)