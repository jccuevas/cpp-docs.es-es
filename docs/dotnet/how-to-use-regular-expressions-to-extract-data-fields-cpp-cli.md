---
title: "C&#243;mo: Utilizar expresiones regulares para extraer campos de datos (C++/CLI) | Microsoft Docs"
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
  - "datos [C++], extraer de cadenas"
  - "cadenas con formato [C++]"
  - "expresiones regulares [C++], extraer campos de datos"
  - "cadenas [C++], extraer datos de"
ms.assetid: b581d9b6-630e-48fa-94fe-20b0f7b89b06
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Utilizar expresiones regulares para extraer campos de datos (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el ejemplo de código siguiente se muestra el uso de expresiones regulares para extraer los datos de una cadena con formato.  En el ejemplo de código siguiente se usa la clase <xref:System.Text.RegularExpressions.Regex> para especificar un modelo que corresponde a una dirección de correo electrónico.  Este modelo incluye identificadores de campo que pueden emplearse para recuperar partes del nombre de host y de usuario de cada dirección de correo electrónico.  La clase <xref:System.Text.RegularExpressions.Match> se utiliza para realizar la coincidencia de modelos.  Si la dirección de correo electrónico proporcionada es válida, se extraen y se muestran los nombres de usuario y de host.  
  
## Ejemplo  
  
```  
// Regex_extract.cpp  
// compile with: /clr  
#using <System.dll>  
  
using namespace System;  
using namespace System::Text::RegularExpressions;  
  
int main()  
{  
    array<String^>^ address=  
    {  
        "jay@southridgevideo.com",  
        "barry@adatum.com",  
        "treyresearch.net",  
        "karen@proseware.com"  
    };  
  
    Regex^ emailregex = gcnew Regex("(?<user>[^@]+)@(?<host>.+)");  
  
    for (int i=0; i<address->Length; i++)  
    {  
        Match^ m = emailregex->Match( address[i] );  
        Console::Write("\n{0,25}", address[i]);  
  
        if ( m->Success )   
        {  
            Console::Write("   User='{0}'",   
            m->Groups["user"]->Value);  
            Console::Write("   Host='{0}'",   
            m->Groups["host"]->Value);  
        }  
        else   
            Console::Write("   (invalid email address)");  
        }  
  
    Console::WriteLine("");  
    return 0;  
}  
```  
  
## Vea también  
 [Expresiones regulares de .NET Framework](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)