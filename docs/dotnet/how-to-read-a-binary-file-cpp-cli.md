---
title: 'Cómo: leer un archivo binario (C++ / CLI) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- files [C++], binary
- binary files, reading in C++
ms.assetid: 41ad9ad1-5cac-489c-874e-4bb3a649073a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8411971c8bca79d9cb1809481b5a6be61b052262
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-read-a-binary-file-ccli"></a>Cómo: Leer un archivo binario (C++/CLI)
En el ejemplo de código siguiente se muestra cómo leer datos binarios de un archivo, mediante el uso de dos clases de la <xref:System.IO?displayProperty=fullName> espacio de nombres: <xref:System.IO.FileStream> y <xref:System.IO.BinaryReader>. <xref:System.IO.FileStream> representa al propio archivo. <xref:System.IO.BinaryReader> Proporciona una interfaz a la secuencia que permite el acceso binario.  
  
 El ejemplo de código lee un archivo que se denomina data.bin y contiene enteros en formato binario. Para obtener información sobre este tipo de archivo, consulte [Cómo: escribir un archivo binario (C++ / CLI)](../dotnet/how-to-write-a-binary-file-cpp-cli.md).  
  
## <a name="example"></a>Ejemplo  
  
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
  
## <a name="see-also"></a>Vea también  
 [E/S de archivos y secuencias](http://msdn.microsoft.com/Library/4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2)   
 [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)