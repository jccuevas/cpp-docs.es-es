---
title: "C&#243;mo: Escribir un archivo binario (C++/CLI) | Microsoft Docs"
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
  - "archivos binarios, escribir en C++"
  - "archivos [C++], binaria"
ms.assetid: 35d97ee6-fc7e-4c36-be18-8bbb3b44b3ae
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Escribir un archivo binario (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el siguiente ejemplo de código se muestra cómo escribir datos binarios en un archivo.  Se usan dos clases del espacio de nombres <xref:System.IO>: <xref:System.IO.FileStream> y <xref:System.IO.BinaryWriter>.  La clase <xref:System.IO.FileStream> representa al propio archivo, mientras que la clase <xref:System.IO.BinaryWriter> proporciona una interfaz a la secuencia que permite el acceso binario.  
  
 En el siguiente ejemplo de código se escribe un archivo que contiene enteros en formato binario.  Este archivo puede leerse con el código de [Cómo: Leer un archivo binario](../dotnet/how-to-read-a-binary-file-cpp-cli.md).  
  
## Ejemplo  
  
```  
// binary_write.cpp  
// compile with: /clr  
#using<system.dll>  
using namespace System;  
using namespace System::IO;  
  
int main()  
{  
   array<Int32>^ data = {1, 2, 3, 10000};  
  
   FileStream^ fs = gcnew FileStream("data.bin", FileMode::Create);  
   BinaryWriter^ w = gcnew BinaryWriter(fs);  
  
   try   
   {  
      Console::WriteLine("writing data to file:");  
      for (int i=0; i<data->Length; i++)  
      {  
         Console::WriteLine(data[i]);  
         w->Write(data[i]);  
      }  
   }  
   catch (Exception^)   
   {  
     Console::WriteLine("data could not be written");  
     fs->Close();  
     return -1;  
   }  
  
   fs->Close();  
   return 0;  
}  
```  
  
## Vea también  
 [E\/S de archivos y secuencias](../Topic/File%20and%20Stream%20I-O.md)   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)