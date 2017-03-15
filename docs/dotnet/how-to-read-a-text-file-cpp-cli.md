---
title: "C&#243;mo: Leer un archivo de texto (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "leer archivos de texto"
  - "archivos de texto, leer"
ms.assetid: 80551c01-d769-4b6d-8db7-fd53bde21b62
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Leer un archivo de texto (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el siguiente ejemplo de código se muestra cómo abrir y leer un archivo de texto una línea cada vez, utilizando la clase <xref:System.IO.StreamReader>, que se define en el espacio de nombres <xref:System.IO?displayProperty=fullName>.  Se utiliza una instancia de esta clase para abrir un archivo de texto y, a continuación, se usa el método <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName> para recuperar cada línea.  
  
 Este ejemplo de código lee un archivo denominado textfile.txt y contiene el texto.  Para obtener información sobre este tipo de archivo, vea [Cómo: Escribir un archivo de texto](../dotnet/how-to-write-a-text-file-cpp-cli.md).  
  
## Ejemplo  
  
```  
// text_read.cpp  
// compile with: /clr  
#using<system.dll>  
using namespace System;  
using namespace System::IO;  
  
int main()  
{  
   String^ fileName = "textfile.txt";  
   try   
   {  
      Console::WriteLine("trying to open file {0}...", fileName);  
      StreamReader^ din = File::OpenText(fileName);  
  
      String^ str;  
      int count = 0;  
      while ((str = din->ReadLine()) != nullptr)   
      {  
         count++;  
         Console::WriteLine("line {0}: {1}", count, str );  
      }  
   }  
   catch (Exception^ e)  
   {  
      if (dynamic_cast<FileNotFoundException^>(e))  
         Console::WriteLine("file '{0}' not found", fileName);  
      else  
         Console::WriteLine("problem reading file '{0}'", fileName);  
   }  
  
   return 0;  
}  
```  
  
## Vea también  
 [E\/S de archivos y secuencias](../Topic/File%20and%20Stream%20I-O.md)   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)