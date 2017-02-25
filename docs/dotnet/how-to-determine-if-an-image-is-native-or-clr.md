---
title: "C&#243;mo: Determinar si una imagen es nativa o CLR | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr (opción del compilador) [C++], detectar el uso en la compilación"
  - "Common Language Runtime, /clr (opción del compilador)"
  - "Common Language Runtime, pruebas de imágenes"
  - "imágenes [C++], comprobación en CLR"
ms.assetid: 5a854822-6172-4b22-b236-320165412568
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# C&#243;mo: Determinar si una imagen es nativa o CLR
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una forma de determinar si una imagen se compiló para Common Language Runtime es usar **dumpbin** [\/CLRHEADER](../build/reference/clrheader.md).  
  
 También puede comprobar mediante programación si una imagen se compiló para Common Language Runtime.  Para obtener más información, vea [Cómo: Detectar la compilación de \/clr](../dotnet/how-to-detect-clr-compilation.md).  
  
## Ejemplo  
 En el siguiente ejemplo se determina si una imagen se compiló para ejecutarse en Common Language Runtime.  
  
```  
// detect_image_type.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::IO;  
  
enum class CompilationMode {Invalid, Native, CLR };  
  
static CompilationMode IsManaged(String^ filename) {  
   try {  
      array<Byte>^ data = gcnew array<Byte>(4096);  
      FileInfo^ file = gcnew FileInfo(filename);  
      Stream^ fin = file->Open(FileMode::Open, FileAccess::Read);  
      Int32 iRead = fin->Read(data, 0, 4096);  
      fin->Close();  
  
      // Verify this is a executable/dll  
      if ((data[1] << 8 | data[0]) != 0x5a4d)  
         return CompilationMode::Invalid;  
  
      // This will get the address for the WinNT header  
      Int32 iWinNTHdr = data[63]<<24 | data[62]<<16 | data[61] << 8 | data[60];  
  
      // Verify this is an NT address  
      if ((data[iWinNTHdr+3] << 24 | data[iWinNTHdr+2] << 16 | data[iWinNTHdr+1] << 8 | data[iWinNTHdr]) != 0x00004550)  
         return CompilationMode::Invalid;  
  
      Int32 iLightningAddr = iWinNTHdr + 24 + 208;  
      Int32 iSum = 0;  
      Int32 iTop = iLightningAddr + 8;  
  
      for (int i = iLightningAddr; i < iTop; ++i)  
         iSum |= data[i];  
  
      if (iSum == 0)  
         return CompilationMode::Native;  
      else  
         return CompilationMode::CLR;  
   }  
   catch(Exception ^e) {  
      throw(e);  
   }  
}  
  
int main() {  
   array<String^>^ args = Environment::GetCommandLineArgs();  
  
   if (args->Length < 2) {  
      Console::WriteLine("USAGE : detect_clr <assembly_name>\n");  
      return -1;  
   }  
  
   Console::WriteLine("{0} is compiled {1}", args[1], IsManaged(args[1]));  
}  
```  
  
## Vea también  
 [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)