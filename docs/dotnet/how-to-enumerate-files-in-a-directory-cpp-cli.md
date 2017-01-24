---
title: "C&#243;mo: Enumerar archivos en un directorio (C++/CLI) | Microsoft Docs"
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
  - "directorios [C++], enumerar archivos"
  - "archivos [C++], enumerar archivos"
ms.assetid: ebfc2666-229f-4b94-a9a1-e8f1b5d946d6
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Enumerar archivos en un directorio (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el ejemplo de código siguiente se muestra cómo recuperar una lista de los archivos de un directorio.  Además, los subdirectorios están enumerados.  El ejemplo de código siguiente utiliza los métodos <xref:System.IO.Directory.GetFiles%2A> <xref:System.IO.Directory.GetFiles%2A> y <xref:System.IO.Directory.GetDirectories%2A> para mostrar el contenido del directorio C:\\Windows.  
  
## Ejemplo  
  
```  
// enum_files.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::IO;  
  
int main()  
{  
   String^ folder = "C:\\";  
   array<String^>^ dir = Directory::GetDirectories( folder );  
   Console::WriteLine("--== Directories inside '{0}' ==--", folder);  
   for (int i=0; i<dir->Length; i++)  
      Console::WriteLine(dir[i]);  
  
   array<String^>^ file = Directory::GetFiles( folder );  
   Console::WriteLine("--== Files inside '{0}' ==--", folder);  
   for (int i=0; i<file->Length; i++)  
      Console::WriteLine(file[i]);  
  
   return 0;  
}  
```  
  
## Vea también  
 [E\/S de archivos y secuencias](../Topic/File%20and%20Stream%20I-O.md)   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)