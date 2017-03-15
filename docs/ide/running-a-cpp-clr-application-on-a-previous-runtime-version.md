---
title: "Ejecutar una aplicaci&#243;n /clr de C++ en una versi&#243;n anterior de Common Language Runtime | Microsoft Docs"
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
  - "app.config (archivos), versión especificada del motor en tiempo de ejecución"
  - "implementación de aplicaciones [C++], versión especificada del motor en tiempo de ejecución"
  - "aplicaciones [C++], versión especificada del motor en tiempo de ejecución"
  - "compatibilidad con versiones anteriores [C++], versión especificada del motor en tiempo de ejecución"
  - "Common Language Runtime [C++], versión especificada"
  - "compatibilidad [C++], versión especificada del motor en tiempo de ejecución"
  - "implementar aplicaciones [C++], versión especificada del motor en tiempo de ejecución"
  - "versiones [C++]"
ms.assetid: 940171b7-6937-4b14-8e87-c199e23f4f2e
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Ejecutar una aplicaci&#243;n /clr de C++ en una versi&#243;n anterior de Common Language Runtime
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

A menos que se especifique lo contrario, se compila una aplicación de Visual C\+\+ .NET Framework para ejecutarse en la versión de \(CLR\) de Common Language Runtime que el compilador utiliza para compilar la aplicación.  Sin embargo, es posible que una aplicación .exe compilado para una versión del runtime se ejecute en cualquier otra versión que proporciona la funcionalidad necesaria.  
  
 Para ello, especifique un archivo app.config que contiene información de versión del runtime en la etiqueta de `supportedRuntime` .  
  
 En tiempo de ejecución, el archivo debe tener un nombre con el formato *filename.ext*.config, donde es el nombre *filename.ext* del ejecutable que inició la aplicación, y debe estar en el mismo directorio que el ejecutable.  Por ejemplo, si la aplicación se denomina TestApp.exe, el archivo app.config se denominará TestApp.exe.config.  
  
 Si se especifica más de una versión del runtime y la aplicación se ejecuta en un equipo que tenga más de una versión instalada, utilizará la primera versión especificada en el archivo de configuración y está instalada.  
  
 Para obtener más información, vea [How to: Configure an App to Target a .NET Framework Version](http://msdn.microsoft.com/es-es/5247b307-89ca-417b-8dd0-e8f9bd2f4717).  
  
 Para ejecutar en la versión 1.0 o la versión 1.1 de CLR, una aplicación integrada con el compilador de Visual C\+\+ debe compilarse utilizando [\/clr:initialAppDomain](../build/reference/clr-common-language-runtime-compilation.md).  
  
## Vea también  
 [Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)