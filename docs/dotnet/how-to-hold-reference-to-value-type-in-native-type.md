---
title: "C&#243;mo: Mantener la referencia a un tipo de valor en un tipo nativo | Microsoft Docs"
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
  - "referencia a un tipo de valor en un tipo nativo"
  - "referencia a tipo de valor en tipo nativo"
ms.assetid: 1eabf8be-7d4f-4339-9027-48d5c4244483
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# C&#243;mo: Mantener la referencia a un tipo de valor en un tipo nativo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Utilice `gcroot` en el tipo al que se le ha aplicado la conversión boxing para mantener una referencia a un tipo de valor en un tipo nativo.  
  
## Ejemplo  
  
```  
// reference_to_value_in_native.cpp  
// compile with: /clr  
#using <mscorlib.dll>  
#include <vcclr.h>   
  
using namespace System;   
  
public value struct V {  
   String ^str;  
};  
  
class Native {  
public:  
   gcroot< V^ > v_handle;  
};  
  
int main() {  
   Native native;  
   V v;  
   native.v_handle = v;  
   native.v_handle->str = "Hello";  
   Console::WriteLine("String in V: {0}", native.v_handle->str);  
}  
```  
  
  **Cadena en V: Hello**   
## Vea también  
 [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)