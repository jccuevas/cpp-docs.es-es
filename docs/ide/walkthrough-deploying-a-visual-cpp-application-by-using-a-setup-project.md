---
title: Implementar una aplicación de Visual C++ mediante un proyecto de instalación | Documentos de Microsoft
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
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>Tutorial: Implementar una aplicación de Visual C++ mediante un proyecto de instalación
Describe cómo usar un proyecto de instalación para implementar una aplicación de Visual C++.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Un equipo con [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] instalado.  
  
-   Un equipo adicional que no tenga las bibliotecas de Visual C++.  
  
### <a name="to-deploy-an-application-by-using-a-setup-project"></a>Para implementar una aplicación mediante un proyecto de instalación  
  
1.  Use la **ApplicationWizard MFC** para crear una nueva solución de Visual Studio. Para buscar el asistente desde el **nuevo proyecto** cuadro de diálogo, expanda el **Visual C++** nodo, seleccione **MFC**, seleccione **aplicación MFC**, escriba un el nombre para el proyecto y, a continuación, haga clic en **Aceptar**.  
  
2.  Cambie la configuración de soluciones activas a **versión**. Desde el **generar** menú, seleccione **Configuration Manager**. Desde el **Configuration Manager** cuadro de diálogo, seleccione **versión** desde el **configuración de soluciones activas** cuadro de lista desplegable.  
  
3.  Presione la tecla F7 para compilar la aplicación. O bien, en la **generar** menú, haga clic en **generar solución**. Esto permite que el proyecto de instalación usar el resultado de este proyecto de aplicación MFC.  
  
4.  Si aún no lo ha hecho, descargue InstallShield Limited Edition (ISLE), que es gratuito para desarrolladores de Visual Studio y reemplaza la funcionalidad de las plantillas de proyecto en Visual Studio para el programa de instalación e implementación. Cuando esté conectado a Internet, abra el **nuevo proyecto** cuadro de diálogo Elegir **archivo**, **New**, **proyecto** en la barra de menús, o por con el botón secundario en la solución de **el Explorador de soluciones** y elegir **agregar**, **nuevo proyecto**. Expanda el **otros tipos de proyectos** nodo, elija **Habilitar InstallShield Limited Edition** en el **el programa de instalación e implementación** nodo y siga las instrucciones que aparecen. Una vez que ha descargado, instalado y activado InstallShield Limited Edition, cierre Visual Studio y vuelva a abrirlo.  
  
5.  Abra la **nuevo proyecto** cuadro de diálogo nuevo, expanda la **otros tipos de proyectos** nodo y elija **proyecto de InstallShield Limited Edition** en el  **InstallShield Limited Edition** nodo.  
  
6.  Siga las instrucciones en el **Introducción** nodo del proyecto de instalación creado por la plantilla de InstallShield Limited Edition para agregar una referencia de salida a un proyecto MFC de Visual Studio.  
  
7.  Compile el proyecto de instalación para crear el archivo de instalador (setup.exe). Para ello, haga clic en el nodo del proyecto de instalación **el Explorador de soluciones** y seleccione **generar**.  
  
     InstallShield Limited Edition crea el archivo de instalación en el árbol de proyecto de instalación (de forma predeterminada, que puede estar ubicado en la subcarpeta Express\SingleImage\DiskImages\DISK1 del proyecto de instalación).  
  
8.  Ejecute el programa de instalación en un segundo equipo que no tenga las bibliotecas de Visual C++.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplos de implementación](../ide/deployment-examples.md)