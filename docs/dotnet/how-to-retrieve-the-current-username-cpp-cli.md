---
title: "C&#243;mo: Recuperar el nombre de usuario actual (C++/CLI) | Microsoft Docs"
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
  - "nombres de usuario actuales"
  - "nombres de usuario, recuperar"
  - "UserName (cadena)"
ms.assetid: 91679571-d029-41f5-b657-1460c81c608a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Recuperar el nombre de usuario actual (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el ejemplo de código siguiente se muestra la recuperación del nombre de usuario actual \(el nombre del usuario que ha iniciado sesión en Windows\).  El nombre se almacena en la cadena <xref:System.Environment.UserName%2A>, que está definida en el espacio de nombres <xref:System.Environment>.  
  
## Ejemplo  
  
```  
// username.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   Console::WriteLine("\nCurrent user: {0}", Environment::UserName);  
   return 0;  
}  
```  
  
## Vea también  
 [Operaciones de Windows](../dotnet/windows-operations-cpp-cli.md)   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)