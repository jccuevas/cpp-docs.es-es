---
title: "Implementaci&#243;n de ClickOnce para aplicaciones de Visual C++ | Microsoft Docs"
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
  - "implementar aplicaciones [C++], ClickOnce"
  - "implementación de aplicaciones de [C++], ClickOnce"
  - "implementación de ClickOnce [C++], aplicaciones de C++"
ms.assetid: 9988c546-0936-452c-932f-9c76daa42157
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Implementaci&#243;n de ClickOnce para aplicaciones de Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] proporciona dos tecnologías diferentes para implementar aplicaciones Windows: implementación ClickOnce o implementación [Windows Installer](http://msdn.microsoft.com/library/cc185688).  
  
## Implementación de ClickOnce en C\+\+  
 El entorno de desarrollo de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] no admite directamente la implementación de proyectos de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] con [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)], pero existen herramientas que pueden utilizarlo.  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] sí admite [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)] en los entornos de desarrollo de [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)] y [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)].  Si el proyecto de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] es una dependencia de un proyecto de [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)], puede publicar la aplicación \(incluidas sus dependencias\) mediante la implementación de [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)] desde el entorno de desarrollo de [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)].  
  
 Para implementar una aplicación de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] mediante [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)], primero deberá compilar un [Manifiesto de aplicación ClickOnce](../Topic/ClickOnce%20Application%20Manifest.md) y un [Manifiesto de la implementación ClickOnce](../Topic/ClickOnce%20Deployment%20Manifest.md) usando la [Mage.exe \(Herramienta de generación y edición de manifiestos\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md) o su versión de interfaz gráfica de usuario \(para obtener más información, vea [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)\).  
  
 Utilice primero Mage.exe para compilar el manifiesto de aplicación; el archivo resultante tendrá la extensión .manifest.  A continuación, utilice Mage.exe para compilar el manifiesto de implementación; el archivo resultante tendrá la extensión .application.  Por último, firme los manifiestos.  
  
 El manifiesto de aplicación debe especificar el procesador de destino \(**x86**, **x64** o **ARM**\).  Vea [Implementar requisitos previos de aplicaciones de 64 bits](../Topic/Deploying%20Prerequisites%20for%2064-bit%20Applications.md) para obtener información sobre estas opciones.  
  
 A su vez, el nombre de la aplicación y de los manifiestos de implementación debe ser diferente del nombre de la aplicación de C\+\+.  Esto evita el conflicto entre el manifiesto de aplicación creado por Mage.exe y el manifiesto externo que forma parte de la aplicación de C\+\+.  
  
 La implementación necesitará la instalación de las bibliotecas de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] de las que dependa la aplicación.  Para determinar las dependencias de una aplicación determinada, puede utilizar depends.exe o la utilidad DUMPBIN con la opción \/DEPENDENTS.  Para obtener más información sobre las dependencias, vea [Descripción de las dependencias de una aplicación de Visual C\+\+](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md).  Podría tener que ejecutar VCRedist.exe; esta utilidad instala las bibliotecas de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] en el equipo de destino.  
  
 También puede que deba compilar un arranque \(instalador de requisitos previos\) para que la aplicación implemente componentes de requisito previo; para obtener información sobre la secuencia de inicio, vea [Crear paquetes de arranque](../Topic/Creating%20Bootstrapper%20Packages.md).  
  
 Para una descripción más detallada de la tecnología, vea [Seguridad e implementación ClickOnce](../Topic/ClickOnce%20Security%20and%20Deployment.md).  Para obtener un ejemplo detallado de la implementación de [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)], vea [Tutorial: Implementar manualmente una aplicación ClickOnce](../Topic/Walkthrough:%20Manually%20Deploying%20a%20ClickOnce%20Application.md).  
  
## Vea también  
 [Mage.exe \(Herramienta de generación y edición de manifiestos\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)   
 [Makecert.exe \(Certificate Creation Tool\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md)   
 [Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [Implementar aplicaciones, servicios y componentes](../Topic/Deploying%20Applications,%20Services,%20and%20Components.md)   
 [Windows Installer Deployment](http://msdn.microsoft.com/es-es/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Seguridad e implementación ClickOnce](../Topic/ClickOnce%20Security%20and%20Deployment.md)   
 [Crear paquetes de arranque](../Topic/Creating%20Bootstrapper%20Packages.md)   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)