---
title: "C&#243;mo: Convertir char * String en una matriz System::Byte | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "matrices [C++], caracteres"
  - "matrices de caracteres, convertir en matrices System::Byte"
  - "ejemplos [C++], matrices"
  - "ejemplos [C++], cadenas"
ms.assetid: de9bc4eb-773c-4796-a496-9b90ca986503
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Convertir char * String en una matriz System::Byte
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La manera más eficaz de convertir una cadena `char *` en una matriz <xref:System.Byte> es utilizando la clase <xref:System.Runtime.InteropServices.Marshal>.  
  
## Ejemplo  
  
```  
// convert_native_string_to_Byte_array.cpp  
// compile with: /clr  
#include <string.h>  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
int main() {  
   char buf[] = "Native String";  
   int len = strlen(buf);  
  
   array< Byte >^ byteArray = gcnew array< Byte >(len + 2);  
  
   // convert native pointer to System::IntPtr with C-Style cast  
   Marshal::Copy((IntPtr)buf,byteArray, 0, len);  
  
   for ( int i = byteArray->GetLowerBound(0); i <= byteArray->GetUpperBound(0); i++ ) {  
      char dc =  *(Byte^)   byteArray->GetValue(i);  
      Console::Write((Char)dc);  
   }  
  
   Console::WriteLine();  
}  
```  
  
```  
Native String  
```  
  
## Vea también  
 [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)