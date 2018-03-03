---
title: 'Tutorial: Implementar el programa (C++) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- deploying applications [C++], walkthroughs
- setup projects [C++]
- program deployments [C++]
- projects [C++], setup
- projects [C++], deploying programs
- application deployment [C++], walkthroughs
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ce59dc7b767c8ff8e988ac7a765d3bb5f1cdfffc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-deploying-your-program-c"></a>Tutorial: Implementar el programa (C++)
Ahora que ha creado la aplicación siguiendo el anteriormente tutoriales relacionados, que se enumeran en [mediante el IDE de Visual Studio para el desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md), el último paso consiste en crear un instalador para que otros usuarios puedan instalar el programa en sus equipos. Para ello, agregue un nuevo proyecto a la solución existente. El resultado de este nuevo proyecto es un archivo setup.exe que instalará la aplicación en otro equipo.  
  
 En este tutorial muestra cómo utilizar Windows Installer para implementar la aplicación. También puede utilizar ClickOnce para implementar una aplicación. Para obtener más información, vea [ClickOnce Deployment for Visual C++ Applications](../ide/clickonce-deployment-for-visual-cpp-applications.md). Para obtener más información acerca de la implementación en general, vea [implementar aplicaciones, servicios y componentes](/visualstudio/deployment/deploying-applications-services-and-components).  
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   En este tutorial se da por supuesto que conoce los fundamentos del lenguaje C++.  
  
-   También se supone que ha completado los tutoriales anteriores relacionados en la que se muestran en [mediante el IDE de Visual Studio para el desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
-   Este tutorial no se puede completar en las ediciones Express de Visual Studio.  
  
-   Si no lo ha hecho todavía, descargue InstallShield Limited Edition (ISLE), como se describe en los pasos especificados más adelante en este artículo. ISLE es gratis para desarrolladores de Visual Studio y reemplaza a la funcionalidad de las plantillas de proyecto de instalación e implementación en ediciones anteriores de Visual Studio.  
  
### <a name="to-install-the-isle-setup-and-deployment-project-template"></a>Para instalar la plantilla de proyecto de implementación y configuración de ISLE  
  
1.  Cuando esté conectado a Internet, en la barra de menús, elija **archivo**, **New**, **proyecto** para abrir el **nuevo proyecto** cuadro de diálogo.  
  
2.  En el panel izquierdo del cuadro de diálogo, expanda el **instalado**, **plantillas**, y **otros tipos de proyectos** nodos y, a continuación, seleccione **el programa de instalación e implementación**. En el panel central, seleccione **Habilitar InstallShield Limited Edition** y, a continuación, elija la **Aceptar** botón.  
  
3.  Siga las instrucciones para instalar InstallShield Limited Edition para Visual Studio (ISLE).  
  
4.  Después de haber descargado, instalado y activado ISLE, cierre Visual Studio y ábralo de nuevo.  
  
5.  En la barra de menús, elija **archivo**, **proyectos y soluciones recientes**y, a continuación, elija la **juego** solución para volver a abrirla.  
  
### <a name="to-create-a-setup-project-and-install-your-program"></a>Para crear un proyecto de instalación e instalar su programa  
  
1.  Cambie la configuración de soluciones activa a Lanzamiento. En la barra de menús, elija **Compilar**, **Administrador de configuración**. En el **Configuration Manager** cuadro de diálogo, en la **configuración de soluciones activas** lista desplegable, seleccione **versión**. Elija la **cerrar** botón para guardar la configuración.  
  
2.  En la barra de menús, elija **archivo**, **New**, **proyecto** para abrir el **nuevo proyecto** cuadro de diálogo.  
  
3.  En el panel izquierdo del cuadro de diálogo, expanda el **instalado**, **plantillas**, y **otros tipos de proyectos** nodos y, a continuación, seleccione **el programa de instalación e implementación**. En el panel central, seleccione **proyecto de InstallShield Limited Edition**.  
  
4.  Escriba un nombre para el proyecto de instalación en el **nombre** cuadro. En este ejemplo, escriba **Game Installer**. En el **solución** lista desplegable, seleccione **agregar a solución**. Elija la **Aceptar** botón para crear el proyecto de instalación. A **Asistente para proyectos (Game Installer)** ficha se abre en la ventana del editor.  
  
5.  En la parte inferior de la **Asistente para proyectos (Game Installer)** ficha, elija la **información de la aplicación** vínculo.  
  
6.  En el **información de la aplicación** página, especifique el nombre de su compañía como desea que aparezca en el programa de instalación. Puede usar su propio nombre de la empresa o para este ejemplo, utilice **Contoso**. Especifique el nombre de la aplicación; en este ejemplo, especifique **juego**. Especifique la dirección web de su empresa o para este ejemplo, utilice **http://www.contoso.com**.  
  
7.  En la parte inferior de la **Asistente para proyectos (Game Installer)** ficha, elija la **entrevista de la instalación** vínculo.  
  
8.  En el **entrevista de la instalación** página, en **¿desea que aparezca un cuadro de diálogo del contrato de licencia**, seleccione la **n** botón de opción. En **¿desea pedir a los usuarios escriban su nombre de la compañía y nombre de usuario**, seleccione la **n** botón de opción.  
  
9. En **el Explorador de soluciones**, expanda la **Game Installer** proyecto de equipo y expanda el **Organice la configuración** nodo y, a continuación, abra el **deinformaciónGeneral** página.  
  
10. En el **información General (Game Installer)** pestaña en la ventana del editor, especifique un **identificador del autor de etiqueta**, por ejemplo, **regid.2012-12.com.Contoso**.  
  
11. En **el Explorador de soluciones**, en la **Game Installer** proyecto de equipo y expanda el **especificar datos de la aplicación** nodo y, a continuación, abra el **archivos** página.  
  
12. En el **archivos (Game Installer)** pestaña en la ventana del editor, en **los archivos del equipo de origen**, abra el menú contextual para **resultado principal del juego** y elija **Copia**.  
  
13. Abrir un menú contextual en el espacio en el **nombre** columna en **archivos del equipo de destino**y elija **pegar**. Un nuevo elemento denominado **Game.Primary Output** aparece.  
  
14. En **el Explorador de soluciones**, en la **especificar datos de la aplicación** nodo, abra el **Redistributables** página.  
  
15. En el **redistribuibles (Game Installer)** ficha en la ventana del editor, seleccione la **Visual C++ 11.0 CRT (x86)** casilla de verificación.  
  
16. En la barra de menús, elija **generar**, **generar solución** para compilar el proyecto de juego y el proyecto de instalador de juego.  
  
17. En la carpeta de soluciones, busque el programa setup.exe compilado del proyecto de instalador de juego y después ejecútelo para instalar la aplicación de juego en el equipo. Puede copiar este archivo para instalar la aplicación y sus archivos de biblioteca necesarios en otro equipo.  
  
18. Puede establecer muchas opciones en el proyecto de instalación para satisfacer sus requisitos. Para obtener más información, en **el Explorador de soluciones**, en la **Game Installer** proyecto, abra el **Introducción** página y, a continuación, elija la tecla F1 para abrir la biblioteca de ayuda ISLE.  
  
## <a name="next-steps"></a>Pasos siguientes  
 **Anterior:** [Tutorial: depurar un proyecto (C++)](../ide/walkthrough-debugging-a-project-cpp.md)  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Compilación de programas de C/C++](../build/building-c-cpp-programs.md)  
 [Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)