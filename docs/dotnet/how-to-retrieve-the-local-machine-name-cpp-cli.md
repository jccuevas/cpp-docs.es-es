---
title: "C&#243;mo: Recuperar el nombre del equipo local (C++/CLI) | Microsoft Docs"
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
  - "nombre del equipo"
  - "nombre del equipo, recuperar"
  - "nombre de equipo, recuperar"
ms.assetid: 6c7acb9a-3f9b-43b2-a756-bd4fb859e697
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Recuperar el nombre del equipo local (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El ejemplo de código siguiente muestra la recuperación del nombre del equipo local \(el nombre del usuario tal y como aparece en la red\).  Esto se puede lograr obteniendo la cadena <xref:System.Environment.MachineName%2A>, que está defina en el espacio de nombres <xref:System.Environment>.  
  
## Ejemplo  
  
```  
// machine_name.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   Console::WriteLine("\nMachineName: {0}", Environment::MachineName);  
   return 0;  
}  
```  
  
## Vea también  
 [Operaciones de Windows](../dotnet/windows-operations-cpp-cli.md)   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)