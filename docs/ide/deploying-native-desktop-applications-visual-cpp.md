---
title: "Implementar aplicaciones de escritorio nativas (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "implementar aplicaciones [C++]"
  - "implementación de aplicaciones [C++]"
  - "Visual C++, implementación de aplicaciones"
  - "implementación de aplicaciones [C++], información sobre la implementación de aplicaciones"
  - "implementar aplicaciones [C++], información sobre la implementación de aplicaciones"
  - "distribuir aplicaciones [C++]"
ms.assetid: 37f1691e-d67c-41e4-926e-528a237a9bac
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementar aplicaciones de escritorio nativas (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La implementación es el proceso mediante el cual se distribuye una aplicación o un componente acabado para instalarse en otros equipos. La planeación de la implementación se inicia cuando se crea una aplicación en el equipo de un desarrollador. La implementación finaliza cuando se instala la aplicación y está preparada para ejecutarse en el equipo del usuario.  
  
 Visual Studio proporciona diferentes tecnologías para implementar aplicaciones Windows. Entre ellas se incluyen la implementación de [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)] y la implementación de Windows Installer.  
  
-   [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)] puede usarse para implementar aplicaciones de C\+\+ destinadas a common language runtime \(CLR\): ensamblados mixtos, puros y comprobables. Aunque se puede usar Windows Installer para implementar una aplicación administrada, se recomienda usar [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)] porque aprovecha las características de seguridad de .NET Framework, como la firma de manifiestos.[!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)] no admite la implementación de aplicaciones de C\+\+ nativas. Para obtener más información, vea [Implementación de ClickOnce para aplicaciones de Visual C\+\+](../ide/clickonce-deployment-for-visual-cpp-applications.md).  
  
-   La tecnología de Windows Installer puede usarse para implementar aplicaciones de C\+\+ nativas o aplicaciones de C\+\+ orientadas a CLR.  
  
 Los artículos de esta sección de la documentación explican cómo asegurarse de que una aplicación de Visual C\+\+ nativa se ejecute en cualquier equipo que proporciona una plataforma de destino admitida, cuyos archivos se deben incluir en un paquete de instalación, así como los métodos recomendados para redistribuir los componentes que dependen la aplicación.  
  
## En esta sección  
 [Implementación en Visual C\+\+](../ide/deployment-in-visual-cpp.md)  
  
 [Conceptos de implementación](../ide/deployment-concepts.md)  
  
 [Descripción de las dependencias de una aplicación de Visual C\+\+](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)  
  
 [Determinar qué archivos DLL se redistribuirán](../ide/determining-which-dlls-to-redistribute.md)  
  
 [Elegir un método de implementación](../ide/choosing-a-deployment-method.md)  
  
 [Redistribuir archivos de Visual C\+\+](../ide/redistributing-visual-cpp-files.md)  
  
 [Ejemplos de implementación](../ide/deployment-examples.md)  
  
 [Redistribuir aplicaciones cliente web](../ide/redistributing-web-client-applications.md)  
  
 [Implementación de ClickOnce para aplicaciones de Visual C\+\+](../ide/clickonce-deployment-for-visual-cpp-applications.md)  
  
 [Ejecutar una aplicación \/clr de C\+\+ en una versión anterior de Common Language Runtime](../ide/running-a-cpp-clr-application-on-a-previous-runtime-version.md)  
  
## Secciones relacionadas  
 [Compilar aplicaciones aisladas y ensamblados simultáneos de C\/C\+\+](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)  
  
 [Implementación](../Topic/Deploying%20the%20.NET%20Framework%20and%20Applications.md)  
  
 [Solución de problemas](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)