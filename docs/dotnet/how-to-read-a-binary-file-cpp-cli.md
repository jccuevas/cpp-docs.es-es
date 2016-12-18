---
title: "C&#243;mo: Leer un archivo binario (C++/CLI) | Microsoft Docs"
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
  - "archivos binarios, leer en C++"
  - "archivos [C++], binaria"
ms.assetid: 41ad9ad1-5cac-489c-874e-4bb3a649073a
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Leer un archivo binario (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El ejemplo de código siguiente muestra cómo leer datos binarios de un archivo, utilizando dos clases del espacio de nombres <xref:System.IO?displayProperty=fullName>: <xref:System.IO.FileStream> y <xref:System.IO.BinaryReader>.  La clase <xref:System.IO.FileStream> representa al propio archivo.  La clase <xref:System.IO.BinaryReader> proporciona una interfaz a la secuencia que permite el acceso binario.  
  
 El ejemplo de código lee un archivo denominado data.bin y contiene enteros en formato binario.  Para obtener información sobre este tipo de archivo, vea [Cómo: Escribir un archivo binario](../dotnet/how-to-write-a-binary-file-cpp-cli.md).  
  
## Ejemplo  
  
```  
// binary_read.cpp  
// compile with: /clr  
#using<system.dll>  
using namespace System;  
using namespace System::IO;  
  
int main()   
{  
   String^ fileName = "data.bin";  
   try  
   {  
      FileStream^ fs = gcnew FileStream(fileName, FileMode::Open);  
      BinaryReader^ br = gcnew BinaryReader(fs);  
  
      Console::WriteLine("contents of {0}:", fileName);  
      while (br->BaseStream->Position < br->BaseStream->Length)  
         Console::WriteLine(br->ReadInt32().ToString());  
  
      fs->Close( );  
   }  
   catch (Exception^ e)  
   {  
      if (dynamic_cast<FileNotFoundException^>(e))  
         Console::WriteLine("File '{0}' not found", fileName);  
      else  
         Console::WriteLine("Exception: ({0})", e);  
      return -1;  
   }  
   return 0;  
}  
```  
  
## Vea también  
 [E\/S de archivos y secuencias](../Topic/File%20and%20Stream%20I-O.md)   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)