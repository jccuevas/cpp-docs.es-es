---
title: "Elegir un m&#233;todo de implementaci&#243;n | Microsoft Docs"
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
  - "implementación de aplicaciones [C++], métodos"
  - "implementar aplicaciones [C++], métodos"
  - "DLL [C++], redistribuir"
  - "vinculación dinámica [C++]"
  - "bibliotecas [C++], problemas en la implementación de aplicaciones"
  - "manifiestos [C++]"
  - "redistribuir DLL"
  - "ensamblados simultáneos [C++]"
  - "vinculación estática [C++]"
ms.assetid: fd8eb956-f4a0-4ffb-b401-328c73e66986
caps.latest.revision: 35
caps.handback.revision: 35
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Elegir un m&#233;todo de implementaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

A menos que la aplicación de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] sea independiente y se pueda implementar mediante un comando de copia, se recomienda usar Windows Installer para la implementación.  Windows Installer admite la instalación, la reparación y la desinstalación, y también admite la actualización atómica de archivos, dependencias y entradas del Registro de una aplicación.  
  
> [!NOTE]
>  Aunque la implementación [ClickOnce](../Topic/ClickOnce%20Security%20and%20Deployment.md) de aplicaciones nativas de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] es posible en Visual Studio, requiere ciertos pasos adicionales.  Para obtener más información, vea [Implementación de ClickOnce para aplicaciones de Visual C\+\+](../ide/clickonce-deployment-for-visual-cpp-applications.md).  
  
## Las bibliotecas de Visual C\+\+ son archivos DLL compartidos  
 Puesto que el instalador de Visual Studio instala las bibliotecas de Visual C\+\+ en el directorio %windir%\\system32\\, cuando se desarrolla una aplicación de Visual C\+\+ que depende de ellas, se ejecuta de la forma esperada.  Sin embargo, para implementar la aplicación en equipos que quizás no tengan Visual Studio, se recomienda asegurarse de que las bibliotecas se instalan en esos equipos junto con la aplicación.  
  
## Redistribuir bibliotecas de Visual C\+\+  
 En las implementaciones, puede redistribuir cualquier versión de una biblioteca de Visual C\+\+ que está licencia de redistribución.  He aquí tres maneras de implementarlas:  
  
-   Implementación central mediante paquetes redistribuibles, lo que instala las bibliotecas de Visual C\+\+ como archivos DLL compartidos en %windir%\\system32\\. \(La instalación en esta carpeta requiere derechos de administrador\). Se puede crear un script o un programa de instalación que ejecute el paquete redistribuible antes de instalar la aplicación en el equipo de destino.  Hay disponibles paquetes redistribuibles para las plataformas x86, x64 y ARM \(VCRedist\_x86.exe, VCRedist\_x64.exe o VCRedist\_arm.exe\).  Visual Studio incluye estos paquetes en %ProgramFiles\(x86\)%\\Microsoft Visual Studio `version`\\VC\\Redist\\`locale ID`\\.  También se pueden descargar desde el [Centro de descarga de Microsoft](http://go.microsoft.com/fwlink/?LinkId=132793). \(En el Centro de descarga, busque el “paquete redistribuible de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] *Visual Studio version and update*” correspondiente a la aplicación.  Por ejemplo, si usó la actualización 4 de Visual Studio 2012 para compilar la aplicación, busque “paquete redistribuible de Visual C\+\+ 2012 actualización 4"\). Para obtener más información sobre cómo usar un paquete redistribuible, vea [Tutorial: Implementar una aplicación de Visual C\+\+ mediante el paquete redistribuible de Visual C\+\+](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).  
  
-   Implementación central mediante módulos de combinación, cada uno de los cuales instala una biblioteca concreta de Visual C\+\+ como un archivo DLL compartido en %windir%\\system32\\. \(La instalación en esta carpeta requiere derechos de administrador\). Los módulos de combinación forman parte del archivo instalador .msi de la aplicación.  Los módulos de combinación redistribuibles de Visual C\+\+ se incluyen en Visual Studio, en \\Archivos de programa \(x86\)\\Common Files\\Merge Modules\\.  Para obtener más información, vea [Redistribuir mediante módulos de combinación](../ide/redistributing-components-by-using-merge-modules.md).  
  
-   Implementación local, en la que se copian determinados archivos DLL de Visual C\+\+ de la instalación de Visual Studio, normalmente en \\Archivos de programa \(x86\)\\Microsoft Visual Studio`version`\\VC\\Redist\\`platform`\\`library`\\ y se instalan en equipos de destino en la misma carpeta que el archivo ejecutable de la aplicación.  Este método de implementación se puede usar para habilitar la instalación por parte de usuarios que no tienen derechos de administrador, o para las aplicaciones que se pueden ejecutar desde un recurso compartido de red.  
  
 Si una implementación emplea módulos de combinación redistribuibles y la instalación la realiza un usuario que no tiene derechos administrativos, los archivos DLL de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] no se instalan y la aplicación no se ejecuta.  Además, los instaladores de aplicaciones compilados con módulos de combinación que permiten la instalación por usuario instalan las bibliotecas en una ubicación compartida que afecta a todos los usuarios del sistema.  Se puede usar la implementación local para instalar los archivos DLL de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] necesarios en el directorio de la aplicación de un usuario determinado sin afectar por ello a otros usuarios o requerir derechos de administrador.  Esto puede crear problemas de mantenimiento, por lo no se recomienda realizar la implementación local de archivos DLL redistribuibles de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)].  
  
 La implementación incorrecta de las bibliotecas de Visual C\+\+ puede dar lugar a errores en tiempo de ejecución cuando se ejecuta una aplicación que depende de ellas.  Cuando el sistema operativo carga la aplicación, emplea el orden de búsqueda descrito en [LoadLibraryEx](http://go.microsoft.com/fwlink/?LinkId=132792).  
  
## La vinculación dinámica es mejor que la estática  
 Se recomienda evitar la vinculación estática cuando redistribuyen bibliotecas de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)].  Aunque la vinculación estática casi nunca mejora significativamente el rendimiento de una aplicación, casi siempre hace que el mantenimiento sea más costoso.  Por ejemplo, imagine una aplicación que está vinculada estáticamente a una biblioteca que se ha actualizado con mejoras de seguridad; la aplicación no puede beneficiarse de ellos a menos que se recompile y se vuelva a implementar.  En su lugar, se recomienda vincular dinámicamente las aplicaciones a las bibliotecas de las que dependen, de modo que las bibliotecas puedan actualizarse dondequiera que se implementen.  
  
## Vea también  
 [Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [Elegir una estrategia de implementación](http://msdn.microsoft.com/es-es/ecd632d8-063c-4028-b785-81bba045107b)   
 [Windows Installer Deployment Overview](http://msdn.microsoft.com/es-es/3ce4610a-b54f-404e-b650-42f4a55dfc3b)   
 [Seguridad e implementación ClickOnce](../Topic/ClickOnce%20Security%20and%20Deployment.md)   
 [Ejemplos de implementación](../ide/deployment-examples.md)