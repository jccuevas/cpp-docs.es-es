---
title: "C&#243;mo: Especificar un par&#225;metro out | Microsoft Docs"
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
  - "parámetros de la función"
  - "out (parámetros)"
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# C&#243;mo: Especificar un par&#225;metro out
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este ejemplo se muestra la forma de especificar que el parámetro de una función es un parámetro out y la forma de llamar a dicha función desde un programa de C\#.  
  
 Para especificar un parámetro out en Visual C\+\+ se utiliza <xref:System.Runtime.InteropServices.OutAttribute>.  
  
## Ejemplo  
 La primera parte de este ejemplo es un archivo DLL de Visual C\+\+ con un tipo que contiene una función con un parámetro out.  
  
```  
// cpp_out_param.cpp  
// compile with: /LD /clr:safe  
using namespace System;  
public value struct TestStruct {  
   static void Test([Runtime::InteropServices::Out] String^ %s) {  
      s = "a string";  
   }  
};  
```  
  
## Ejemplo  
 Éste es un cliente de C\# que utiliza el componente de Visual C\+\+ creado en el ejemplo anterior.  
  
```  
// cpp_out_param_2.cs  
// compile with: /reference:cpp_out_param.dll  
using System;  
class TestClass {  
   public static void Main() {  
      String t;  
      TestStruct.Test(out t);  
      System.Console.WriteLine(t);  
   }  
}  
```  
  
  **cadena**   
## Vea también  
 [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)