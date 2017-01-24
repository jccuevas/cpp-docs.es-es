---
title: "Comparaci&#243;n de caracter&#237;sticas mixta, pura y comprobable (C++/CLI) | Microsoft Docs"
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
  - "ensamblados mixtos [C++]"
  - "ensamblados mixtos [C++], puros"
  - "ensamblados mixtos [C++], seguro"
  - "ensamblados puros [C++]"
  - "MSIL puro [C++]"
  - "MSIL puro [C++], comparación entre mixto y seguro"
  - "MSIL puro [C++], mixtos"
  - "MSIL puro [C++], seguro"
  - "ensamblados seguros [C++]"
  - "ensamblados seguros [C++], mixtos"
  - "ensamblados seguros [C++], puros"
  - "ensamblados comprobables [C++]"
  - "ensamblados comprobables [C++], mixtos"
  - "ensamblados comprobables [C++], puros"
ms.assetid: 3f7a82ba-0e69-4927-ba0c-fbc3160e4394
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comparaci&#243;n de caracter&#237;sticas mixta, pura y comprobable (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se comparan las características entre los distintos modos de compilación de **\/clr**.  Para obtener más información, vea [\/clr \(Compilación de Common Language Runtime\)](../build/reference/clr-common-language-runtime-compilation.md).  
  
## Comparación de características  
  
|Característica|Mixta \(\/clr\)|Pura \(\/clr:pure\)|Segura \(\/clr:safe\)|Información relacionada|  
|--------------------|---------------------|-------------------------|---------------------------|-----------------------------|  
|Biblioteca de CRT|compatible|compatible||[Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)|  
|MFC\/ATL|compatible|||[Aplicaciones de escritorio de MFC](../mfc/mfc-desktop-applications.md) &#124; [Class Overview](../atl/atl-class-overview.md)|  
|Funciones no administradas|compatible|||[Ensamblados mixtos \(nativos y administrados\)](../dotnet/mixed-native-and-managed-assemblies.md)|  
|Datos no administrados|compatible|compatible||[Código puro y comprobable](../dotnet/pure-and-verifiable-code-cpp-cli.md)|  
|Invocable desde funciones no administradas|compatible|||[Cómo: Migrar a \/clr:pure](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)|  
|Compatibilidad con llamadas a funciones no administradas|compatible|Sólo funciones de estilo C|Sólo P\/Invoke|[Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)|  
|Compatibilidad con la reflexión|Sólo archivos DLL|compatible|compatible|[Reflexión](../dotnet/reflection-cpp-cli.md)|  
  
## Vea también  
 [Código puro y comprobable](../dotnet/pure-and-verifiable-code-cpp-cli.md)