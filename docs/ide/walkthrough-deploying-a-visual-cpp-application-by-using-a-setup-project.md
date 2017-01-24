---
title: "Tutorial: Implementar una aplicaci&#243;n de Visual C++ mediante un proyecto de instalaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "implementación para Visual C++"
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tutorial: Implementar una aplicaci&#243;n de Visual C++ mediante un proyecto de instalaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe cómo usar un proyecto de instalación para implementar una aplicación de Visual C\+\+.  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Un equipo con [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] instalado.  
  
-   Un equipo adicional que no disponga de las bibliotecas de Visual C\+\+.  
  
### Para implementar una aplicación mediante un proyecto de instalación  
  
1.  Use el **Asistente para  aplicaciones MFC** para crear una nueva solución de Visual Studio.  Para encontrar el asistente, en el cuadro de diálogo **Nuevo proyecto**, expanda el nodo **Visual C\+\+**, seleccione **MFC**, seleccione **Aplicación MFC**, escriba un nombre para el proyecto y, a continuación, haga clic en **Aceptar**.  
  
2.  Cambie la configuración de soluciones activa a **Lanzamiento**.  En el menú **Compilación**, seleccione **Administrador de configuración**.  En el cuadro de diálogo **Administrador de configuración**, seleccione **Lanzamiento** en el cuadro de lista desplegable **Configuración de soluciones activas**.  
  
3.  Presione F7 para compilar la aplicación.  O bien, en el menú **Compilar**, haga clic en **Compilar solución**.  Esto permite al proyecto de instalación usar la salida de este proyecto de aplicación MFC.  
  
4.  Si no ha hecho aún así, installshield limited edition de descarga \(ISLE\), que está disponible para los desarrolladores de Visual Studio que reemplaza la funcionalidad de las plantillas de proyecto de Visual Studio para la configuración y la implementación.  Si está conectado a internet, abra el cuadro de diálogo **Nuevo proyecto** eligiendo **Archivo**, **Nuevo**, **Proyecto** en la barra de menús, o haciendo clic con el botón secundario en la solución en **Explorador de soluciones** y elija **Agregar**, **Nuevo proyecto…**.  Expanda el nodo **Otros tipos de proyectos** , elija **habilitar installshield limited edition** en el nodo **Instalación e implementación** , y siga las instrucciones que aparecen.  Una vez descargado, instala y activa edición de InstallShield Limited, cierre Visual Studio y la abra de nuevo.  
  
5.  Abra el cuadro de diálogo **Nuevo proyecto** de nuevo, expanda el nodo **Otros tipos de proyectos** , y elegir **Proyecto de InstallShield Limited edition** en el nodo **Edición de InstallShield Limited** .  
  
6.  Siga las instrucciones del nodo **Introducción** del proyecto de instalación creado por la plantilla de installshield limited edition para agregar una referencia de salida al proyecto de Visual Studio MFC.  
  
7.  Compile el proyecto de instalación para crear el archivo de instalación de \(setup.exe\).  Para ello, haga clic con el botón secundario en el proyecto de instalación en **Explorador de soluciones** y **Compilación**seleccione.  
  
     InstallShield Limited edition crea el archivo de instalación en el árbol de proyecto de instalación \(de forma predeterminada, se encuentra en el Express \\SingleImage\\DiskImages\\DISK 1 subcarpeta del proyecto de instalación\).  
  
8.  Ejecute el programa de instalación en un segundo equipo que no tenga las bibliotecas de Visual C\+\+.  
  
## Vea también  
 [Ejemplos de implementación](../ide/deployment-examples.md)