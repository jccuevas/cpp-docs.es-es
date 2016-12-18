---
title: "Redistribuir controles | Microsoft Docs"
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
  - "controles ActiveX [C++], redistribuir"
  - "controles redistribuibles"
ms.assetid: 32d03b95-d328-4f10-ad9b-f3ebbe03339d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Redistribuir controles
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ .NET proporciona controles ActiveX que se pueden utilizar en las aplicaciones. A continuación, los controles se pueden redistribuir junto con las aplicaciones. En el cuadro de diálogo **Insertar control ActiveX**, al resaltar un control se mostrará el archivo .ocx o .dll correspondiente.  
  
 Si desea ver una lista de controles ActiveX redistribuibles suministrados con Visual C\+\+, vea Archivos de programa\\Microsoft Visual Studio .NET 2003\\redist.txt en el disco 2 de los CD\-ROM del producto Visual C\+\+ .NET; se pueden redistribuir todos los archivos .ocx de la carpeta Win\\System.  
  
 En [Controles ActiveX de MFC: distribuir controles ActiveX](../../mfc/mfc-activex-controls-distributing-activex-controls.md) se explica la forma de instalar y registrar los controles ActiveX redistribuibles.  
  
 En [Proyectos de módulo de combinación](http://msdn.microsoft.com/es-es/e92e4f85-fba5-45ee-a432-892a956daeb9) se explica cómo controla la implementación de Visual Studio .NET la redistribución de archivos mediante módulos de combinación.  
  
 En [Redistribuir archivos de compatibilidad con bases de datos](../../ide/redistributing-database-support-files.md) se analiza cómo redistribuir los archivos de compatibilidad para las tecnologías de base de datos disponibles en el SDK de Microsoft Data Access.  
  
 Si en la aplicación se utiliza un control ActiveX que conecta con una base de datos, se deben llevar a cabo los siguientes procedimientos:  
  
-   **DCOM para Windows.** Se debe ejecutar Dcom98.exe o Dcom95.exe en cualquier equipo que ejecute versiones de Windows anteriores a Windows 2000. \(Dcom98.exe es específicamente para Windows 98; Dcom95.exe es específicamente para Windows 95\).  
  
-   **SDK de MDAC 2.8.** El SDK de Microsoft Data Access 2.8 se debe instalar en el equipo de destino. Puede descargarlo de [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=205525](http://go.microsoft.com/fwlink/?LinkId=205525).  
  
-   **Programa de redistribución de MDAC 2.8.** El SDK de MDAC 2.8 se ha diseñado para su uso con el programa de redistribución de MDAC 2.8 \(MDAC\_TYP.EXE\). Puede descargar MDAC\_TYP.EXE de [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=164412](http://go.microsoft.com/fwlink/?LinkId=164412).  
  
-   **Replicar el DSN.** También debe replicarse el nombre del origen de datos en el equipo de destino. Esto se puede hacer mediante programación con funciones como [ConfigDSN](https://msdn.microsoft.com/en-us/library/ms709275.aspx).  
  
## Notas importantes acerca de la redistribución de componentes  
  
-   **Redistribuir componentes DAO.** Microsoft recomienda usar Jet 4.0 SP3 \(versión 2927.04\) o posterior. Jet 4.0 SP3 se distribuye con Windows 2000 y Windows Me. Con esta versión de Jet, se reduce el número de versiones que se deben probar en la aplicación.  
  
     Windows XP se distribuye con una versión actualizada del Service Pack de Jet no incluida en versiones anteriores de Windows. Al probar la aplicación en Windows XP, se prueba automáticamente la versión de Jet distribuida con Windows XP. Antes de publicar las aplicaciones DAO, debe probar ambas versiones de Jet 4.0.  
  
     La única diferencia consiste en que la versión de Windows XP soluciona los problemas encontrados desde el lanzamiento de Windows 2000. Si los usuarios de la aplicación no encuentran problemas, no hay necesidad de actualizar a una versión posterior a Jet 4.0 SP3.  
  
-   **Problemas conocidos con controles ActiveX.** Hay un problema conocido relacionado con la creación dinámica de instancias de controles ActiveX redistribuibles en equipos en los que no esté instalado Visual C\+\+, tal como se describe en el artículo de Knowledge Base "PRB: Error de la creación dinámica de controles redistribuibles" \(Q151804\). Encontrará artículos de Knowledge Base en el CD\-ROM de MSDN Library o en [http:\/\/support.microsoft.com](http://support.microsoft.com). Además hay otro problema conocido que ocurre al colocar algunos controles ActiveX en un cuadro de diálogo; aparece un cuadro de mensaje que notifica que el control requiere una licencia en tiempo de diseño, tal como se describe en el artículo de Knowledge Base "PRB: Se requiere una licencia de diseño para los controles Microsoft ActiveX" \(Q155059\). Encontrará artículos de Knowledge Base en el CD\-ROM de MSDN Library o en [http:\/\/support.microsoft.com](http://support.microsoft.com).  
  
-   **Controles de Visual Studio con licencia.** Los propietarios de licencias de Visual Studio pueden redistribuir controles ActiveX adicionales específicos para otras herramientas de desarrollo de Visual Studio. Por ejemplo, el control Chart se distribuye con Visual Basic, que a su vez se distribuye con Visual Studio. Por tanto, si utiliza Visual C\+\+ como parte de una licencia de Visual Studio, puede redistribuir el control Chart. Sin embargo, si solo adquirió Visual C\+\+, no tendrá ninguna licencia para redistribuir el control.  
  
## Vea también  
 [Utilizar controles ActiveX](../../data/ado-rdo/using-activex-controls.md)   
 [Controles ActiveX MFC: Distribuir controles ActiveX](../../mfc/mfc-activex-controls-distributing-activex-controls.md)