---
title: 'Tutorial: Implementación del programa (C++)'
ms.date: 09/14/2018
helpviewer_keywords:
- deploying applications [C++], walkthroughs
- setup projects [C++]
- program deployments [C++]
- projects [C++], setup
- projects [C++], deploying programs
- application deployment [C++], walkthroughs
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
ms.openlocfilehash: c202d4eae5e9115f847caefce18a8974a4388a04
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740452"
---
# <a name="walkthrough-deploying-your-program-c"></a>Tutorial: Implementación del programa (C++)

Ahora que ha creado la aplicación completando los tutoriales relacionados anteriores, que se enumeran en [Usar el IDE de Visual Studio para desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md), el último paso consiste en crear un instalador para que otros usuarios puedan instalar el programa en sus equipos. Para el instalador, agregue un nuevo proyecto a la solución existente. El resultado de este nuevo proyecto es un archivo setup.exe que instalará la aplicación en otro equipo.

En este tutorial se muestra cómo utilizar Windows Installer para implementar la aplicación. También puede utilizar ClickOnce para implementar una aplicación. Para obtener más información, vea [ClickOnce Deployment for Visual C++ Applications](../ide/clickonce-deployment-for-visual-cpp-applications.md). Para obtener más información sobre el desarrollo en general, vea [Implementar aplicaciones, servicios y componentes](/visualstudio/deployment/deploying-applications-services-and-components).

## <a name="prerequisites"></a>Requisitos previos

- En el tutorial se da por supuesto que conoce los fundamentos del lenguaje C++.

- También se presupone que ha completado los tutoriales relacionados anteriores que se enumeran en [Usar el IDE de Visual Studio para desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

- El tutorial no se puede completar en las ediciones Express de Visual Studio.

- Si aún no lo ha hecho, descargue la extensión de proyectos del instalador de Microsoft Visual Studio, como se describe en los siguientes pasos. La extensión es gratis para desarrolladores de Visual Studio y agrega la funcionalidad de las plantillas de proyecto de instalación e implementación a Visual Studio.

### <a name="to-install-the-visual-studio-setup-and-deployment-project-template"></a>Para instalar la plantilla de proyecto de implementación y configuración de Visual Studio

1. Cuando esté conectado a Internet, en Visual Studio, elija **Herramientas** > **Extensiones y actualizaciones**.

1. En **Extensiones y actualizaciones**, seleccione la pestaña **En línea** y escriba *Proyectos del instalador de Microsoft Visual Studio* en el cuadro de búsqueda. Presione **ENTRAR**, seleccione **Microsoft Visual Studio \<versión> Proyectos del instalador** y haga clic en **Descargar**.

1. Opte por instalar la extensión y, a continuación, reinicie Visual Studio.

1. En la barra de menús, seleccione **Archivo** > **Proyectos y soluciones recientes** y, después, elija la solución **Game** para volver a abrirla.

### <a name="to-create-a-setup-project-and-install-your-program"></a>Para crear un proyecto de instalación e instalar su programa

1. Cambie la configuración de soluciones activa a Lanzamiento. En la barra de menús, elija **Compilar** > **Administrador de configuración**. En el cuadro de diálogo **Administrador de configuración**, en la lista desplegable **Configuración de soluciones activas**, seleccione **Release**. Haga clic en el botón **Cerrar** para guardar la configuración.

1. En la barra de menús, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Nuevo proyecto**.

1. En el panel de la izquierda del cuadro de diálogo, expanda los nodos **Instalado** > **Otros tipos de proyectos** y después seleccione **Instalador de Visual Studio**. En el panel central, seleccione **Proyecto de instalación**.

1. Escriba un nombre para el proyecto de instalación en el cuadro **Nombre**. Para este ejemplo, escriba *Game Installer*. En la lista desplegable **Solución**, seleccione **Agregar a la solución**. Haga clic en el botón **Aceptar** para crear el proyecto de instalación. Se abrirá una pestaña **Asistente para archivos (Game Installer)** en la ventana del editor.

1. Haga clic con el botón derecho en el nodo **Carpeta de la aplicación** y seleccione **Agregar** > **Resultados del proyecto** para abrir el cuadro de diálogo **Agregar grupo de resultados del proyecto**.

1. En el cuadro de diálogo, seleccione **Resultado principal** y haga clic en **Aceptar**. Aparece un nuevo elemento denominado **Resultado principal de Game (activo)**.

1. Seleccione el elemento **Resultado principal de Game (activo)**, haga clic con el botón derecho y elija **Crear acceso directo al resultado principal de Game (activo)**. Aparece un nuevo elemento denominado **Acceso directo al resultado principal de Game (activo)**.

1. Cambie el nombre del elemento de acceso directo por *Game*, arrastrar y colocar el elemento en el nodo **Menú Programas del usuario** en el lado izquierdo de la ventana.

1. En el **Explorador de soluciones**, seleccione el proyecto **Game Installer** y elija **Ver** > **Ventana Propiedades** o presione **F4** para abrir la ventana **Propiedades**.

1. Especifique detalles adicionales como desee que aparezcan en el instalador.  Por ejemplo, use *Contoso* para **Fabricante**, *Game Installer* para **Nombre de producto** y *http\://www.contoso.com* para **Dirección URL de soporte**.

1. En la barra de menús, elija **Compilar** > **Administrador de configuración**. En la tabla **Proyecto**, en la columna **Compilar**, marque la casilla **Game Installer**. Haga clic en **Cerrar**.

1. En la barra de menús, seleccione **Compilar** > **Compilar solución** para compilar los proyectos Game y Game Installer.

1. En la carpeta de soluciones, busque el programa setup.exe compilado del proyecto de instalador de juego y después ejecútelo para instalar la aplicación de juego en el equipo. Puede copiar este archivo, y también el archivo GameInstaller.msi, para instalar la aplicación y sus archivos de biblioteca necesarios en otro equipo.

## <a name="next-steps"></a>Pasos siguientes

**Anterior:** [Tutorial: Depuración de un proyecto (C++)](../ide/walkthrough-debugging-a-project-cpp.md)<br/>

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Compilación de programas de C/C++](../build/building-c-cpp-programs.md)<br/>
[Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)<br/>
