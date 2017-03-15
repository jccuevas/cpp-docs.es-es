---
title: "C&#243;mo: Escribir un archivo de texto (C++/CLI) | Microsoft Docs"
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
  - "archivos [C++], texto"
  - "archivos de texto, escribir en C++"
ms.assetid: 39ecdba6-84e0-485c-a202-84cf6d7b8d4a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Escribir un archivo de texto (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el siguiente ejemplo de código se muestra cómo crear un archivo de texto y cómo escribir texto en el mismo utilizando la clase <xref:System.IO.StreamWriter>, que se define en el espacio de nombres <xref:System.IO>.  El constructor <xref:System.IO.StreamWriter> toma el nombre del archivo que se va a crear.  Si ya existe el archivo, se sobrescribe \(a menos que pase True como segundo argumento al constructor <xref:System.IO.StringWriter>\).  
  
 Después, se almacena el archivo mediante las funciones <xref:System.IO.StreamWriter.Write%2A> y <xref:System.IO.TextWriter.WriteLine%2A>.  
  
## Ejemplo  
  
```  
// text_write.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::IO;  
  
int main()   
{  
   String^ fileName = "textfile.txt";  
  
   StreamWriter^ sw = gcnew StreamWriter(fileName);  
   sw->WriteLine("A text file is born!");  
   sw->Write("You can use WriteLine");  
   sw->WriteLine("...or just Write");  
   sw->WriteLine("and do {0} output too.", "formatted");  
   sw->WriteLine("You can also send non-text objects:");  
   sw->WriteLine(DateTime::Now);  
   sw->Close();  
   Console::WriteLine("a new file ('{0}') has been written", fileName);  
  
   return 0;  
}  
```  
  
## Vea también  
 [E\/S de archivos y secuencias](../Topic/File%20and%20Stream%20I-O.md)   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)