---
title: Implementar una aplicación de Visual C++ mediante un proyecto de instalación | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deployment for Visual C++
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 454507a3a3f33b43af0e50c25dab6703aa75a56b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "33332785"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>Tutorial: Implementar una aplicación de Visual C++ mediante un proyecto de instalación
Describe cómo usar un proyecto de instalación para implementar una aplicación de Visual C++.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Un equipo con [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] instalado.  
  
-   Un equipo adicional que no tenga las bibliotecas de Visual C++.  
  
### <a name="to-deploy-an-application-by-using-a-setup-project"></a>Para implementar una aplicación mediante un proyecto de instalación  
  
1.  Use **ApplicationWizard MFC** para crear una solución de Visual Studio. Para buscar el asistente desde el cuadro de diálogo **Nuevo proyecto**, expanda el nodo **Visual C++**, seleccione **MFC**, seleccione **Aplicación MFC**, escriba un el nombre para el proyecto y, después, haga clic en **Aceptar**.  
  
2.  Cambie la configuración de la solución activa a **Release**. Desde el menú **Compilar**, seleccione **Administrador de configuración**. En el cuadro de diálogo **Administrador de configuración**, seleccione **Release** en la lista desplegable **Configuración de soluciones activas**.  
  
3.  Presione F7 para compilar la aplicación. O bien, en el menú **Compilar**, haga clic en **Compilar solución**. Esto permite que el proyecto de instalación use la salida de este proyecto de aplicación MFC.  
  
4.  Si todavía no lo ha hecho, descargue InstallShield Limited Edition (ISLE), que es gratuito para los desarrolladores de Visual Studio y reemplaza la funcionalidad de las plantillas de proyecto en Visual Studio para la instalación e implementación. Cuando esté conectado a Internet, abra el cuadro de diálogo **Nuevo proyecto** seleccionando **Archivo**, **Nuevo**, **Proyecto** en la barra de menús, o bien haciendo clic con el botón derecho en la solución en el **Explorador de soluciones** y seleccionando **Agregar**, **Nuevo proyecto**. Expanda el nodo **Otros tipos de proyectos**, seleccione **Habilitar InstallShield Limited Edition** en el nodo **Instalación e implementación** y siga las instrucciones que aparecen. Después de haber descargado, instalado y activado InstallShield Limited Edition, cierre Visual Studio y ábralo de nuevo.  
  
5.  Vuelva a abrir el cuadro de diálogo **Nuevo proyecto**, expanda el nodo **Otros tipos de proyectos** y seleccione **Proyecto de InstallShield Limited Edition** en el nodo **InstallShield Limited Edition**.  
  
6.  Siga las instrucciones del nodo **Introducción** del proyecto de instalación creado por la plantilla InstallShield Limited Edition para agregar una referencia de salida al proyecto MFC de Visual Studio.  
  
7.  Compile el proyecto de instalación para crear el archivo de instalador (setup.exe). Para ello, haga clic con el botón derecho en el nodo del proyecto de instalación en el **Explorador de soluciones** y seleccione **Compilar**.  
  
     InstallShield Limited Edition crea el archivo de instalación en el árbol del proyecto de instalación (de forma predeterminada, puede estar ubicado en la subcarpeta Express\SingleImage\DiskImages\DISK1 del proyecto de instalación).  
  
8.  Ejecute el programa de instalación en un segundo equipo que no tenga las bibliotecas de Visual C++.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplos de implementación](../ide/deployment-examples.md)