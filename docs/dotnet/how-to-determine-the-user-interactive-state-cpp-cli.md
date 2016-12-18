---
title: "C&#243;mo: Determinar el estado de interacci&#243;n con el usuario (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "estado de interacción con el usuario"
  - "Visual C++, estado de interacción con el usuario"
ms.assetid: 9f52323e-38b8-4a41-9b1d-052012ad839b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Determinar el estado de interacci&#243;n con el usuario (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el ejemplo de código siguiente se muestra la forma de determinar si el código se ejecuta en un contexto de interacción con el usuario.  Si el valor de <xref:System.Environment.UserInteractive%2A> es false, el código se ejecuta como un proceso de servicio o desde una aplicación Web, en cuyo caso no se debe intentar la interacción con el usuario.  
  
## Ejemplo  
  
```  
// user_interactive.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   if ( Environment::UserInteractive )  
      Console::WriteLine("User interactive");  
   else  
      Console::WriteLine("Noninteractive");  
   return 0;  
}  
```  
  
## Vea también  
 [Operaciones de Windows](../dotnet/windows-operations-cpp-cli.md)   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)