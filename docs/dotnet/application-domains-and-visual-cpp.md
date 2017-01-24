---
title: "Dominios de aplicaci&#243;n y Visual C++ | Microsoft Docs"
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
  - "/clr (opción del compilador) [C++], dominios de la aplicación"
  - "dominios de aplicación [C++], C++"
  - "interoperabilidad [C++], dominios de la aplicación"
  - "interoperabilidad [C++], dominios de la aplicación"
  - "ensamblados mixtos [C++], dominios de la aplicación"
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Dominios de aplicaci&#243;n y Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si tiene una función virtual `__clrcall`, el vtable será por cada dominio de aplicación \(appdomain\).  Si crea un objeto en un appdomain, sólo podrá llamar a la función virtual desde dentro de dicho appdomain.  Todas las funciones definidas en los compilandos **\/clr:pure** utilizan la convención de llamada `__clrcall`.  Por consiguiente, todos los vtables definidos en los compilandos **\/clr:pure** serán por cada appdomain.  En el modo mixto \(**\/clr**\), tendrá vtables por cada proceso si el tipo no tiene funciones virtuales `__clrcall`.  
  
 Para obtener más información, vea  
  
-   [appdomain](../cpp/appdomain.md)  
  
-   [\_\_clrcall](../cpp/clrcall.md)  
  
-   [Cómo: Migrar a \/clr:pure](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)  
  
-   [proceso](../cpp/process.md)  
  
## Vea también  
 [Ensamblados mixtos \(nativos y administrados\)](../dotnet/mixed-native-and-managed-assemblies.md)