---
title: "Manifest Resources | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "manifest resources"
  - "resources [Visual Studio], manifest"
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Manifest Resources
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los recursos de manifiesto son archivos XML que describen las dependencias que utiliza una aplicación. Por ejemplo, en Visual Studio, el archivo de manifiesto generado por el asistente de MFC define cuál de los archivos DLL de controles comunes de Windows debe usar la aplicación, si la versión 5.0 o la 6.0:  
  
```  
<description>Your app description here</description> <dependency> <dependentAssembly> <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="X86" publicKeyToken="6595b64144ccf1df" language="*" /> </dependentAssembly> </dependency>   
```  
  
 Para una aplicación de Windows XP o Windows Vista, el recurso de manifiesto no solo especifica que la aplicación usa la versión más reciente de los controles comunes de Windows \(la 0, tal como se indica anteriormente\), sino que también es compatible con el [control Syslink](http://msdn.microsoft.com/library/windows/desktop/bb760706).  
  
 Para ver la información de versión y tipo contenida en un recurso del manifiesto, puede abrir el archivo en un visor de XML o en el [editor de texto](http://msdn.microsoft.com/es-es/508e1f18-99d5-48ad-b5ad-d011b21c6ab1) de Visual Studio. Para obtener más información, vea el tema sobre cómo [abrir un recurso del manifiesto en el editor de texto de Visual Studio](../Topic/How%20to:%20Open%20a%20Manifest%20Resource.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Limitaciones  
 Solo puede tener un recurso de manifiesto por módulo.  
  
## Requisitos  
 Win32  
  
## Vea también  
 [Controles](../mfc/controls-mfc.md)   
 [Working with Resource Files](../mfc/working-with-resource-files.md)