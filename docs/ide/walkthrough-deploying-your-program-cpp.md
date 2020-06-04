---
title: 'Tutorial: Implementar el programa (C++)'
ms.date: 05/14/2019
helpviewer_keywords:
- deploying applications [C++], walkthroughs
- setup projects [C++]
- program deployments [C++]
- projects [C++], setup
- projects [C++], deploying programs
- application deployment [C++], walkthroughs
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
ms.openlocfilehash: eacbcef82f240589e71b59f80d8e19602ceda869
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365017"
---
# <a name="walkthrough-deploying-your-program-c"></a>Tutorial: Implementar el programa (C++)

Ahora que ha creado la aplicación completando los tutoriales relacionados anteriores, el último paso es crear un instalador para que otros usuarios puedan instalar el programa en sus equipos. Para el instalador, agregue un nuevo proyecto a la solución existente. El resultado de este nuevo proyecto es un archivo setup.exe que instalará la aplicación en otro equipo.

En este tutorial se muestra cómo utilizar Windows Installer para implementar la aplicación. También puede utilizar ClickOnce para implementar una aplicación. Para obtener más información, vea [ClickOnce Deployment for Visual C++ Applications](../windows/clickonce-deployment-for-visual-cpp-applications.md). Para obtener más información sobre el desarrollo en general, vea [Implementar aplicaciones, servicios y componentes](/visualstudio/deployment/deploying-applications-services-and-components).

## <a name="prerequisites"></a>Prerrequisitos

- En el tutorial se da por supuesto que conoce los fundamentos del lenguaje C++.

- También se presupone que ha completado los tutoriales relacionados anteriores que se enumeran en [Usar el IDE de Visual Studio para desarrollo de escritorio de C++](using-the-visual-studio-ide-for-cpp-desktop-development.md).

- El tutorial no se puede completar en las ediciones Express de Visual Studio.

## <a name="install-the-visual-studio-setup-and-deployment-project-template"></a>Instalar la plantilla de proyecto de implementación y configuración de Visual Studio

Los pasos descritos en esta sección varían según la versión de Visual Studio que tenga instalada. Para ver la documentación de su versión preferida de Visual Studio, use el control Selector de **versiones.** Se encuentra en la parte superior de la tabla de contenido de esta página.

<!-- markdownlint-disable MD034 -->

::: moniker range="vs-2019"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2019"></a>Para instalar la plantilla de proyecto de implementación y configuración de Visual Studio 2019

1. Si aún no lo ha hecho, descargue la extensión Proyectos de microsoft Visual Studio Installer. La extensión es gratis para desarrolladores de Visual Studio y agrega la funcionalidad de las plantillas de proyecto de instalación e implementación a Visual Studio. Cuando esté conectado a Internet, en Visual Studio, elija **Extensiones** > **administrar extensiones**. En el cuadro de diálogo **Extensiones y actualizaciones**, seleccione la pestaña **En línea** y escriba *Proyectos del instalador de Microsoft Visual Studio* en el cuadro de búsqueda. Presione **ENTRAR**, seleccione **Microsoft Visual Studio \<versión> Proyectos del instalador** y haga clic en **Descargar**. Opte por ejecutar e instalar la extensión y, a continuación, reinicie Visual Studio.

1. En la barra de menús de Visual Studio, seleccione **Archivo** > **Proyectos y soluciones recientes** y, después, elija la opción para volver a abrir el proyecto.

1. En la barra de menús, elija **Nuevo** > **New** > **proyecto** de archivo para abrir el cuadro de diálogo Crear un **nuevo proyecto.** En el cuadro de búsqueda, escriba "Setup" y, en la lista de resultados, elija **Proyecto de instalación**.

1. Escriba un nombre para el proyecto de instalación en el cuadro **Nombre**. En la lista desplegable **Solución**, seleccione **Agregar a la solución**. Haga clic en el botón **Aceptar** para crear el proyecto de instalación. Se abre una pestaña **Asistente de archivos (ProjectName)** en la ventana del editor.

1. Haga clic con el botón derecho en el nodo **Carpeta de la aplicación** y seleccione **Agregar** > **Resultados del proyecto** para abrir el cuadro de diálogo **Agregar grupo de resultados del proyecto**.

1. En el cuadro de diálogo, seleccione **Resultado principal** y haga clic en **Aceptar**. Aparece un nuevo elemento denominado **Resultado principal de Game (activo)**.

1. Seleccione el elemento **Resultado principal de Game (activo)**, haga clic con el botón derecho y elija **Crear acceso directo al resultado principal de Game (activo)**. Aparece un nuevo elemento denominado **Acceso directo al resultado principal de Game (activo)**.

1. Cambie el nombre del elemento de acceso directo por *Game*, arrastrar y colocar el elemento en el nodo **Menú Programas del usuario** en el lado izquierdo de la ventana.

1. En el **Explorador de soluciones**, seleccione el proyecto **Game Installer** y elija **Ver** > **Ventana Propiedades** o presione **F4** para abrir la ventana **Propiedades**.

1. Especifique detalles adicionales como desee que aparezcan en el instalador.  Por ejemplo, use *Contoso* para **Manufacturer**, *Game Installer* para Product **Name**y *https\://www.contoso.com* for **SupportUrl**.

1. En la barra de menús, elija **Build** > **Configuration Manager**. En la tabla **Proyecto**, en la columna **Compilar**, marque la casilla **Game Installer**. Haga clic en **Cerrar**.

1. En la barra de menús, seleccione **Compilar** > **Compilar solución** para compilar los proyectos Game y Game Installer.

1. En la carpeta de soluciones, busque el programa setup.exe compilado del proyecto de instalador de juego y después ejecútelo para instalar la aplicación de juego en el equipo. Puede copiar este archivo, y también el archivo GameInstaller.msi, para instalar la aplicación y sus archivos de biblioteca necesarios en otro equipo.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2017-and-earlier"></a>Para instalar la plantilla de proyecto de implementación y configuración de Visual Studio 2017 y versiones anteriores

1. Cuando esté conectado a Internet, en Visual Studio, elija **Herramientas** > **Extensiones y actualizaciones**.

1. En **Extensiones y actualizaciones**, seleccione la pestaña **En línea** y escriba *Proyectos del instalador de Microsoft Visual Studio* en el cuadro de búsqueda. Presione **ENTRAR**, seleccione **Microsoft Visual Studio \<versión> Proyectos del instalador** y haga clic en **Descargar**.

1. Opte por instalar la extensión y, a continuación, reinicie Visual Studio.

1. En la barra de menús, seleccione **Archivo** > **Proyectos y soluciones recientes** y, después, elija la solución **Game** para volver a abrirla.

### <a name="to-create-a-setup-project-and-install-your-program"></a>Para crear un proyecto de instalación e instalar su programa

1. Cambie la configuración de soluciones activa a Lanzamiento. En la barra de menús, elija **Build** > **Configuration Manager**. En el cuadro de diálogo **Administrador de configuración**, en la lista desplegable **Configuración de soluciones activas**, seleccione **Release**. Haga clic en el botón **Cerrar** para guardar la configuración.

1. En la barra de menús, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Nuevo proyecto**.

1. En el panel izquierdo del cuadro de diálogo, expanda los nodos **Instalado** > **otros tipos** de proyecto y, a continuación, seleccione Instalador de Visual **Studio**. En el panel central, seleccione **Proyecto de instalación**.

1. Escriba un nombre para el proyecto de instalación en el cuadro **Nombre**. Para este ejemplo, escriba *Game Installer*. En la lista desplegable **Solución**, seleccione **Agregar a la solución**. Haga clic en el botón **Aceptar** para crear el proyecto de instalación. Se abrirá una pestaña **Asistente para archivos (Game Installer)** en la ventana del editor.

1. Haga clic con el botón derecho en el nodo **Carpeta de la aplicación** y seleccione **Agregar** > **Resultados del proyecto** para abrir el cuadro de diálogo **Agregar grupo de resultados del proyecto**.

1. En el cuadro de diálogo, seleccione **Resultado principal** y haga clic en **Aceptar**. Aparece un nuevo elemento denominado **Resultado principal de Game (activo)**.

1. Seleccione el elemento **Resultado principal de Game (activo)**, haga clic con el botón derecho y elija **Crear acceso directo al resultado principal de Game (activo)**. Aparece un nuevo elemento denominado **Acceso directo al resultado principal de Game (activo)**.

1. Cambie el nombre del elemento de acceso directo por *Game*, arrastrar y colocar el elemento en el nodo **Menú Programas del usuario** en el lado izquierdo de la ventana.

1. En el **Explorador de soluciones**, seleccione el proyecto **Game Installer** y elija **Ver** > **Ventana Propiedades** o presione **F4** para abrir la ventana **Propiedades**.

1. Especifique detalles adicionales como desee que aparezcan en el instalador.  Por ejemplo, use *Contoso* para **Manufacturer**, *Game Installer* para Product **Name**y *https\://www.contoso.com* for **SupportUrl**.

1. En la barra de menús, elija **Build** > **Configuration Manager**. En la tabla **Proyecto**, en la columna **Compilar**, marque la casilla **Game Installer**. Haga clic en **Cerrar**.

1. En la barra de menús, seleccione **Compilar** > **Compilar solución** para compilar los proyectos Game y Game Installer.

1. En la carpeta de soluciones, busque el programa setup.exe compilado del proyecto de instalador de juego y después ejecútelo para instalar la aplicación de juego en el equipo. Puede copiar este archivo, y también el archivo GameInstaller.msi, para instalar la aplicación y sus archivos de biblioteca necesarios en otro equipo.

::: moniker-end

## <a name="next-steps"></a>Pasos siguientes

**Anterior:** [Tutorial: Depurar un proyecto (C++)](walkthrough-debugging-a-project-cpp.md)

## <a name="see-also"></a>Consulte también

[Referencia del idioma C++](../cpp/cpp-language-reference.md)<br/>
[Proyectos y sistemas de compilación](../build/projects-and-build-systems-cpp.md)<br/>
[Implementar aplicaciones de escritorio](../windows/deploying-native-desktop-applications-visual-cpp.md)<br/>
