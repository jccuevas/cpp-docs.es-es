---
title: Implementación de una aplicación de Visual C++ mediante un proyecto de instalación
ms.date: 04/25/2019
helpviewer_keywords:
- deployment for Visual C++
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
ms.openlocfilehash: 8a1242140154c5a0123d71b83983fae20cab5d7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374352"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>Tutorial: Implementar una aplicación de Visual C++ mediante un proyecto de instalación

Describe cómo usar un proyecto de instalación para implementar una aplicación de Visual C++.

## <a name="prerequisites"></a>Prerrequisitos

Necesitará los componentes siguientes para completar este tutorial:

- Un equipo con Visual Studio instalado.

- Un equipo adicional que no tenga las bibliotecas de Visual C++.

## <a name="create-the-setup-project"></a>Crear el proyecto de configuración

Las instrucciones para crear un proyecto de instalación varían en función de la versión de Visual Studio que haya instalado. Para ver la documentación de su versión preferida de Visual Studio, use el control Selector de **versiones.** Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker range="=vs-2019"

### <a name="to-create-the-project-in-visual-studio-2019"></a>Para crear el proyecto en Visual Studio 2019

1. En la barra de menús, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Crear nuevo proyecto**.

   ![Proyecto de aplicación MFC](media/vs2019-mfc-app-new-project.png "Nueva aplicación MFC")

1. En la parte superior `MFC` del cuadro de diálogo, escriba en el cuadro de búsqueda y, a continuación, elija **Mfc App** en la lista de resultados. Si no lo ve, deberá iniciar el programa Visual Studio Installer desde el menú Inicio de Windows y hacer clic en el icono de carga de trabajo Desarrollo de **escritorio C++.** En **Componentes individuales**, asegúrese de que el componente MFC está activado.

1. En la página siguiente, escriba un nombre para el proyecto y especifique la ubicación del proyecto si lo desea.

1. Haga clic en el botón **Crear** para crear el proyecto de cliente. Cuando aparezca el **Asistente para aplicaciones MFC,** acepte todos los valores predeterminados.

1. Cambie la configuración de la solución activa a **Liberar**. Desde el menú **Compilar**, seleccione **Administrador de configuración**. En el cuadro de diálogo **Administrador de configuración**, seleccione **Release** en la lista desplegable **Configuración de soluciones activas**. Haga clic en **Cerrar**.

1. Presione **Ctrl**+**Shift**+**B** para compilar la aplicación. O bien, en el menú **Compilar**, haga clic en **Compilar solución**. La compilación de la aplicación permite que el proyecto de instalación use la salida de este proyecto de aplicación MFC.

1. Si aún no lo ha hecho, descargue la extensión Proyectos de microsoft Visual Studio Installer. La extensión es gratis para desarrolladores de Visual Studio y agrega la funcionalidad de las plantillas de proyecto de instalación e implementación a Visual Studio. Cuando esté conectado a Internet, en Visual Studio, elija **Extensiones** > **administrar extensiones**. En el cuadro de diálogo **Extensiones y actualizaciones**, seleccione la pestaña **En línea** y escriba *Proyectos del instalador de Microsoft Visual Studio* en el cuadro de búsqueda. Presione **Entrar**, seleccione **Microsoft Visual Studio \<versión> Instalador De Projects**y haga clic en **Descargar**. Opte por ejecutar e instalar la extensión y, a continuación, reinicie Visual Studio.

   ![Proyecto de instalación de Visual Studio](media/vs2019-extension-dialog-installer-project.png "Asigne un nombre al proyecto cliente")

1. En la barra de menús de Visual Studio, seleccione **Archivo** > **Proyectos y soluciones recientes** y, después, elija la opción para volver a abrir el proyecto.

1. En la barra de menús, elija **Nuevo** > **New** > **proyecto** de archivo para abrir el cuadro de diálogo Crear un **nuevo proyecto.** En el cuadro de búsqueda, escriba "Setup" y, en la lista de resultados, elija **Proyecto de instalación**.

1. Escriba un nombre para el proyecto de instalación en el cuadro **Nombre**. En la lista desplegable **Solución**, seleccione **Agregar a la solución**. Haga clic en el botón **Aceptar** para crear el proyecto de instalación. Se abre una pestaña **Asistente de archivos (ProjectName)** en la ventana del editor.

::: moniker-end

::: moniker range="=vs-2017"

### <a name="to-create-the-project-in-visual-studio-2017"></a>Para crear el proyecto en Visual Studio 2017

1. Cree un nuevo proyecto. En el menú **Archivo** , seleccione **Nuevo**y haga clic en **Proyecto**.

1. Use el **Asistente para aplicaciones MFC** para crear una nueva solución de Visual Studio. Para buscar el asistente desde el cuadro de diálogo **Nuevo proyecto**, expanda el nodo **Visual C++**, seleccione **MFC**, seleccione **Aplicación MFC**, escriba un el nombre para el proyecto y, después, haga clic en **Aceptar**. Haga clic en **Finalizar**

   > [!NOTE]
   > Si falta el tipo **de aplicación MFC,** seleccione **Abrir instalador** de Visual Studio en el panel izquierdo del cuadro de diálogo **Nuevo proyecto.** Instale la opción que se encuentra en **Desarrollo para el escritorio con C++** en la sección de componentes **Opcional**, denominada **MFC de Visual C++ para x86 y x64**.

1. Cambie la configuración de la solución activa a **Liberar**. Desde el menú **Compilar**, seleccione **Administrador de configuración**. En el cuadro de diálogo **Administrador de configuración**, seleccione **Release** en la lista desplegable **Configuración de soluciones activas**. Haga clic en **Cerrar**.

1. Presione **Ctrl**+**Shift**+**B** para compilar la aplicación. O bien, en el menú **Compilar**, haga clic en **Compilar solución**. La compilación de la aplicación permite que el proyecto de instalación use la salida de este proyecto de aplicación MFC.

1. Si aún no lo ha hecho, descargue la extensión Proyectos de microsoft Visual Studio Installer. La extensión es gratis para desarrolladores de Visual Studio y agrega la funcionalidad de las plantillas de proyecto de instalación e implementación a Visual Studio. Cuando esté conectado a Internet, en Visual Studio, elija **Extensiones** > **y actualizaciones**de herramientas . En el cuadro de diálogo **Extensiones y actualizaciones**, seleccione la pestaña **En línea** y escriba *Proyectos del instalador de Microsoft Visual Studio* en el cuadro de búsqueda. Presione **Entrar**, seleccione **Microsoft Visual Studio \<versión> Instalador De Projects**y haga clic en **Descargar**. Opte por ejecutar e instalar la extensión y, a continuación, reinicie Visual Studio.

1. En la barra de menús, seleccione **Archivo** > **Proyectos y soluciones recientes** y, después, elija la opción para volver a abrir el proyecto.

1. En la barra de menús, elija **Nuevo** > **New** > **proyecto** de archivo para abrir el cuadro de diálogo **Nuevo proyecto.** A continuación, en el panel izquierdo del cuadro de diálogo, expanda los nodos **Instalado** > **otros tipos** de proyecto y seleccione Instalador de Visual **Studio**. En el panel central, seleccione **Proyecto de instalación**.

1. Escriba un nombre para el proyecto de instalación en el cuadro **Nombre**. En la lista desplegable **Solución**, seleccione **Agregar a la solución**. Haga clic en el botón **Aceptar** para crear el proyecto de instalación. Se abre una pestaña **Asistente de archivos (ProjectName)** en la ventana del editor.

::: moniker-end

::: moniker range="=vs-2015"

### <a name="to-create-the-project-in-visual-studio-2015"></a>Para crear el proyecto en Visual Studio 2015

1. Cree un nuevo proyecto. En el menú **Archivo** , seleccione **Nuevo**y haga clic en **Proyecto**.

1. Use el **Asistente para aplicaciones MFC** para crear una nueva solución de Visual Studio. Para buscar el asistente desde el cuadro de diálogo **Nuevo proyecto**, expanda el nodo **Visual C++**, seleccione **MFC**, seleccione **Aplicación MFC**, escriba un el nombre para el proyecto y, después, haga clic en **Aceptar**. Haga clic en **Finalizar**

   > [!NOTE]
   > Si falta el tipo **de aplicación MFC,** haga clic en el botón Inicio de Windows y escriba **Agregar quitar programas**. Abra el programa desde la lista de resultados y, a continuación, busque la instalación de Microsoft Visual Studio 2015 en la lista de programas instalados. Haga doble clic en ella y luego elija **Modificar** y seleccione el componente **Microsoft Foundation Classes** en **Visual C++**.

1. Cambie la configuración de la solución activa a **Liberar**. En el menú **Generar,** seleccione **Configuration Manager**. En el cuadro de diálogo **Administrador de configuración**, seleccione **Release** en la lista desplegable **Configuración de soluciones activas**. Haga clic en **Cerrar**.

1. Presione **Ctrl**+**Shift**+**B** para compilar la aplicación. O bien, en el menú **Compilar**, haga clic en **Compilar solución**. La compilación de la aplicación permite que el proyecto de instalación use la salida de este proyecto de aplicación MFC.

1. Si aún no lo ha hecho, descargue la extensión Proyectos de microsoft Visual Studio Installer. La extensión es gratis para desarrolladores de Visual Studio y agrega la funcionalidad de las plantillas de proyecto de instalación e implementación a Visual Studio. Cuando esté conectado a Internet, en Visual Studio, elija **Extensiones** > **y actualizaciones**de herramientas . En el cuadro de diálogo **Extensiones y actualizaciones**, seleccione la pestaña **En línea** y escriba *Proyectos del instalador de Microsoft Visual Studio* en el cuadro de búsqueda. Presione **Entrar**, seleccione **Microsoft Visual Studio \<versión> Instalador De Projects**y haga clic en **Descargar**. Opte por ejecutar e instalar la extensión y, a continuación, reinicie Visual Studio.

1. En la barra de menús, seleccione **Archivo** > **Proyectos y soluciones recientes** y, después, elija la opción para volver a abrir el proyecto.

1. En la barra de menús, elija **Nuevo** > **New** > **proyecto** de archivo para abrir el cuadro de diálogo **Nuevo proyecto.** A continuación, en el panel izquierdo del cuadro de diálogo, expanda los nodos **Instalado** > **otros tipos** de proyecto y seleccione Instalador de Visual **Studio**. En el panel central, seleccione **Proyecto de instalación**.

1. Escriba un nombre para el proyecto de instalación en el cuadro **Nombre**. En la lista desplegable **Solución**, seleccione **Agregar a la solución**. Haga clic en el botón **Aceptar** para crear el proyecto de instalación. Se abre una pestaña **Asistente de archivos (ProjectName)** en la ventana del editor.

::: moniker-end

## <a name="add-items-to-the-project"></a>Agregar elementos al proyecto

1. Haga clic con el botón derecho en el nodo **Carpeta de la aplicación** y seleccione **Agregar** > **Resultados del proyecto** para abrir el cuadro de diálogo **Agregar grupo de resultados del proyecto**. En el cuadro de diálogo, seleccione **Resultado principal** y haga clic en **Aceptar**. Aparece un nuevo elemento denominado **Resultado principal de ProjectName (activo)**.

1. Haga clic con el botón derecho en el nodo **Carpeta de la aplicación** y seleccione **Agregar** > **Ensamblado** para abrir el cuadro de diálogo **Seleccionar componente**. Seleccione y agregue todos los archivos DLL necesarios para el programa, según se describe en el artículo [Determinar qué archivos DLL se redistribuirán](determining-which-dlls-to-redistribute.md).

1. Seleccione el elemento **Resultado principal de ProjectName (activo)**, haga clic con el botón derecho y elija **Crear acceso directo al resultado principal de ProjectName (activo)**. Aparece un nuevo elemento denominado **Acceso directo al resultado principal de ProjectName (activo)**. Puede cambiar el nombre del elemento de acceso directo, arrastrar y colocar el elemento en el nodo **Menú Programas del usuario** en el lado izquierdo de la ventana.

1. En la barra de menús, elija **Build** > **Configuration Manager**. En la tabla **Proyecto**, en la columna **Compilar**, marque la casilla del proyecto de implementación. Haga clic en **Cerrar**.

1. En la barra de menús, elija **Compilar** > **solución de compilación** para compilar el proyecto MFC y el proyecto de implementación.

1. En la carpeta de soluciones, busque el programa setup.exe que se creó a partir del proyecto de implementación. Puede copiar este archivo, y también el archivo .msi, para instalar la aplicación y sus archivos de biblioteca necesarios en otro equipo. Ejecute el programa de instalación en un segundo equipo que no tenga las bibliotecas de Visual C++.

## <a name="see-also"></a>Consulte también

[Ejemplos de despliegue](deployment-examples.md)<br/>
