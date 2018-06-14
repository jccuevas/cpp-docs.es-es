---
title: 'Tutorial: Implementar el programa (C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1753c63673b9dd083e2b690788801bd467938c3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335541"
---
# <a name="walkthrough-deploying-your-program-c"></a>Tutorial: Implementar el programa (C++)
Ahora que ha creado la aplicación completando los tutoriales relacionados anteriores, que se enumeran en [Usar el IDE de Visual Studio para desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md), el último paso consiste en crear un instalador para que otros usuarios puedan instalar el programa en sus equipos. Para ello, agregue un nuevo proyecto a la solución existente. El resultado de este nuevo proyecto es un archivo setup.exe que instalará la aplicación en otro equipo.  
  
 En este tutorial muestra cómo utilizar Windows Installer para implementar la aplicación. También puede utilizar ClickOnce para implementar una aplicación. Para obtener más información, vea [ClickOnce Deployment for Visual C++ Applications](../ide/clickonce-deployment-for-visual-cpp-applications.md). Para obtener más información sobre el desarrollo en general, vea [Implementar aplicaciones, servicios y componentes](/visualstudio/deployment/deploying-applications-services-and-components).  
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   En este tutorial se da por supuesto que conoce los fundamentos del lenguaje C++.  
  
-   También se presupone que ha completado los tutoriales relacionados anteriores que se enumeran en [Usar el IDE de Visual Studio para desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
-   Este tutorial no se puede completar en las ediciones Express de Visual Studio.  
  
-   Si no lo ha hecho todavía, descargue InstallShield Limited Edition (ISLE), como se describe en los pasos especificados más adelante en este artículo. ISLE es gratis para desarrolladores de Visual Studio y reemplaza a la funcionalidad de las plantillas de proyecto de instalación e implementación en ediciones anteriores de Visual Studio.  
  
### <a name="to-install-the-isle-setup-and-deployment-project-template"></a>Para instalar la plantilla de proyecto de implementación y configuración de ISLE  
  
1.  Si está conectado a Internet, en la barra de menús, seleccione **Archivo**, **Nuevo**, **Proyecto** para abrir el cuadro de diálogo **Nuevo proyecto**.  
  
2.  En el panel de la izquierda del cuadro de diálogo, expanda los nodos **Instalado**, **Plantillas** y **Otros tipos de proyectos**, y después seleccione **Instalación e implementación**. En el panel central, seleccione **Habilitar InstallShield Limited Edition** y, después, haga clic en el botón **Aceptar**.  
  
3.  Siga las instrucciones para instalar InstallShield Limited Edition para Visual Studio (ISLE).  
  
4.  Después de haber descargado, instalado y activado ISLE, cierre Visual Studio y ábralo de nuevo.  
  
5.  En la barra de menús, seleccione **Archivo**, **Proyectos y soluciones recientes** y, después, elija la solución **Game** para volver a abrirla.  
  
### <a name="to-create-a-setup-project-and-install-your-program"></a>Para crear un proyecto de instalación e instalar su programa  
  
1.  Cambie la configuración de soluciones activa a Lanzamiento. En la barra de menús, elija **Compilar**, **Administrador de configuración**. En el cuadro de diálogo **Administrador de configuración**, en la lista desplegable **Configuración de soluciones activas**, seleccione **Release**. Haga clic en el botón **Cerrar** para guardar la configuración.  
  
2.  En la barra de menús, seleccione **Archivo**, **Nuevo**, **Proyecto** para abrir el cuadro de diálogo **Nuevo proyecto**.  
  
3.  En el panel de la izquierda del cuadro de diálogo, expanda los nodos **Instalado**, **Plantillas** y **Otros tipos de proyectos**, y después seleccione **Instalación e implementación**. En el panel central, seleccione **Proyecto de InstallShield Limited Edition**.  
  
4.  Escriba un nombre para el proyecto de instalación en el cuadro **Nombre**. Para este ejemplo, escriba **Game Installer**. En la lista desplegable **Solución**, seleccione **Agregar a la solución**. Haga clic en el botón **Aceptar** para crear el proyecto de instalación. Se abrirá una pestaña **Asistente para proyectos (Game Installer)** en la ventana del editor.  
  
5.  En la parte inferior de la pestaña **Asistente para proyectos (Game Installer)**, haga clic en el vínculo **Información de la aplicación**.  
  
6.  En la página de **Información de la aplicación**, especifique el nombre de la empresa como quiera que aparezca en el instalador. Puede usar el nombre de su empresa, o bien **Contoso** para este ejemplo. Especifique el nombre de la aplicación; en este ejemplo, especifique **Game**. Especifique la dirección web de la empresa, o bien para este ejemplo, use **http://www.contoso.com**.  
  
7.  En la parte inferior de la pestaña **Asistente para proyectos (Game Installer)**, haga clic en el vínculo **Entrevista de la instalación**.  
  
8.  En la página **Entrevista de la instalación**, en **Desea mostrar un cuadro de diálogo del contrato de licencia**, haga clic en el botón de opción **No**. Cuando se le pregunte si **quiere pedir a los usuarios escribir el nombre de la organización y nombre de usuario**, haga clic en el botón de opción **No**.  
  
9. En el **Explorador de soluciones**, expanda el proyecto **Game Installer**, expanda el nodo **Organizar la configuración** y abra la página **Información general**.  
  
10. En la pestaña **Información general (Game Installer)** en la ventana del editor, especifique un **Identificador del Autor de la etiqueta**, por ejemplo, **regid.2012-12.com.Contoso**.  
  
11. En el **Explorador de soluciones**, bajo el proyecto **Game Installer**, expanda el nodo **Especificar los datos de aplicación** y abra la página **Archivos**.  
  
12. En la pestaña **Archivos (Game Installer)** en la ventana del editor, en **Archivos de equipo de origen**, abra el menú contextual para **Salida principal de Game** y seleccione **Copiar**.  
  
13. Abra un menú contextual en el espacio bajo la columna **Nombre** en **Archivos de equipo de destino**, y seleccione **Pegar**. Aparecerá un elemento nuevo denominado **Game.Primary Output**.  
  
14. En el **Explorador de soluciones**, bajo el nodo **Especificar los datos de aplicación**, abra la página **Redistribuibles**.  
  
15. En la pestaña **Redistribuibles (Game Installer)** en la ventana del editor, active la casilla **Visual C++ 11.0 CRT (x86)**.  
  
16. En la barra de menús, seleccione **Compilar**, **Compilar solución** para compilar los proyectos Game y Game Installer.  
  
17. En la carpeta de soluciones, busque el programa setup.exe compilado del proyecto de instalador de juego y después ejecútelo para instalar la aplicación de juego en el equipo. Puede copiar este archivo para instalar la aplicación y sus archivos de biblioteca necesarios en otro equipo.  
  
18. Puede establecer muchas opciones en el proyecto de instalación para satisfacer sus requisitos. Para obtener más información, en el **Explorador de soluciones**, en el proyecto **Game Installer**, abra la página **Introducción** y, después, presione la tecla F1 para abrir la biblioteca de ayuda de ISLE.  
  
## <a name="next-steps"></a>Pasos siguientes  
 **Anterior:** [Tutorial: Depurar un proyecto (C++)](../ide/walkthrough-debugging-a-project-cpp.md)  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Compilación de programas de C/C++](../build/building-c-cpp-programs.md)  
 [Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)