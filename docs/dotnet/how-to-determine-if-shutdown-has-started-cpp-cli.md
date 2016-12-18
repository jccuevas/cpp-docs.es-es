---
title: "C&#243;mo: Determinar si se ha iniciado el cierre del sistema (C++/CLI) | Microsoft Docs"
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
  - ".NET Framework, cierre"
  - "aplicaciones [C++], cierre"
  - "cierre"
  - "terminación"
ms.assetid: a8d39731-dea8-4f0a-96b7-2a5de09b21d7
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Determinar si se ha iniciado el cierre del sistema (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el ejemplo de código siguiente se muestra la forma de determinar si está finalizando actualmente la aplicación o .NET Framework.  Esto es útil para el acceso a los elementos estáticos de .NET Framework porque, durante el cierre, estas construcciones son finalizadas por el sistema y no se pueden utilizar de forma fiable.  Si comprueba primero la propiedad <xref:System.Environment.HasShutdownStarted%2A>, puede evitar posibles errores por la ausencia de acceso a estos elementos.  
  
## Ejemplo  
  
```  
// check_shutdown.cpp  
// compile with: /clr  
using namespace System;  
int main()   
{  
   if (Environment::HasShutdownStarted)  
      Console::WriteLine("Shutting down.");  
   else  
      Console::WriteLine("Not shutting down.");  
   return 0;  
}  
```  
  
## Vea también  
 [Operaciones de Windows](../dotnet/windows-operations-cpp-cli.md)   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)