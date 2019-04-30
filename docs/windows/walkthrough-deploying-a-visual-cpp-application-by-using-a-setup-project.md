---
title: Implementación de una aplicación de Visual C++ mediante un proyecto de instalación
ms.date: 09/17/2018
helpviewer_keywords:
- deployment for Visual C++
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
ms.openlocfilehash: e2d83d45f1369e250b24708edd17f4004e030a17
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387817"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>Tutorial: Implementación de una aplicación de Visual C++ mediante un proyecto de instalación

Describe cómo usar un proyecto de instalación para implementar una aplicación de Visual C++.

## <a name="prerequisites"></a>Requisitos previos

Necesita los componentes siguientes para completar este tutorial:

- Un equipo con Visual Studio instalado.

- Un equipo adicional que no tenga las bibliotecas de Visual C++.

### <a name="to-deploy-an-application-by-using-a-setup-project"></a>Para implementar una aplicación mediante un proyecto de instalación

1. Cree un nuevo proyecto. En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.

1. Use **ApplicationWizard MFC** para crear una solución de Visual Studio. Para buscar el asistente desde el cuadro de diálogo **Nuevo proyecto**, expanda el nodo **Visual C++**, seleccione **MFC**, seleccione **Aplicación MFC**, escriba un el nombre para el proyecto y, después, haga clic en **Aceptar**. Haga clic en **Finalizar**.

   > [!NOTE]
   > Si falta el tipo **Aplicación MFC**:<br/>
   > **Visual Studio 2017**: seleccione **Abrir el Instalador de Visual Studio** en el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**. Instale la opción que se encuentra en **Desarrollo para el escritorio con C++** en la sección de componentes **Opcional**, denominada **MFC de Visual C++ para x86 y x64**.<br/>
   > **Visual Studio 2015**: haga clic en el botón Inicio de Windows y escriba **Agregar o quitar programas**. Abra el programa desde la lista de resultados y, a continuación, busque la instalación de Microsoft Visual Studio 2015 en la lista de programas instalados. Haga doble clic en ella y luego elija **Modificar** y seleccione el componente **Microsoft Foundation Classes** en **Visual C++**.

1. Cambie la configuración de la solución activa a **Release**. Desde el menú **Compilar**, seleccione **Administrador de configuración**. En el cuadro de diálogo **Administrador de configuración**, seleccione **Release** en la lista desplegable **Configuración de soluciones activas**. Haga clic en **Cerrar**.

1. Presione **Ctrl**+**Mayús**+**B** para compilar la aplicación. O bien, en el menú **Compilar**, haga clic en **Compilar solución**. La compilación de la aplicación permite que el proyecto de instalación use la salida de este proyecto de aplicación MFC.

1. Si aún no lo ha hecho, descargue la extensión de proyectos del instalador de Microsoft Visual Studio. La extensión es gratis para desarrolladores de Visual Studio y agrega la funcionalidad de las plantillas de proyecto de instalación e implementación a Visual Studio. Cuando esté conectado a Internet, en Visual Studio, elija **Herramientas** > **Extensiones y actualizaciones**. En el cuadro de diálogo **Extensiones y actualizaciones**, seleccione la pestaña **En línea** y escriba *Proyectos del instalador de Microsoft Visual Studio* en el cuadro de búsqueda. Presione **ENTRAR**, seleccione **Microsoft Visual Studio \<versión> Proyectos del instalador** y haga clic en **Descargar**. Opte por ejecutar e instalar la extensión y, a continuación, reinicie Visual Studio.

1. En la barra de menús, seleccione **Archivo** > **Proyectos y soluciones recientes** y, después, elija la opción para volver a abrir el proyecto.

1. En la barra de menús, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Nuevo proyecto**. En el panel de la izquierda del cuadro de diálogo, expanda los nodos **Instalado** > **Otros tipos de proyectos** y después seleccione **Instalador de Visual Studio**. En el panel central, seleccione **Proyecto de instalación**.

1. Escriba un nombre para el proyecto de instalación en el cuadro **Nombre**. En la lista desplegable **Solución**, seleccione **Agregar a la solución**. Haga clic en el botón **Aceptar** para crear el proyecto de instalación. Se abre una pestaña **Asistente de archivos (ProjectName)** en la ventana del editor.

1. Haga clic con el botón derecho en el nodo **Carpeta de la aplicación** y seleccione **Agregar** > **Resultados del proyecto** para abrir el cuadro de diálogo **Agregar grupo de resultados del proyecto**. En el cuadro de diálogo, seleccione **Resultado principal** y haga clic en **Aceptar**. Aparece un nuevo elemento denominado **Resultado principal de ProjectName (activo)**.

1. Haga clic con el botón derecho en el nodo **Carpeta de la aplicación** y seleccione **Agregar** > **Ensamblado** para abrir el cuadro de diálogo **Seleccionar componente**. Seleccione y agregue todos los archivos DLL necesarios para el programa, según se describe en el artículo [Determinar qué archivos DLL se redistribuirán](determining-which-dlls-to-redistribute.md).

1. Seleccione el elemento **Resultado principal de ProjectName (activo)**, haga clic con el botón derecho y elija **Crear acceso directo al resultado principal de ProjectName (activo)**. Aparece un nuevo elemento denominado **Acceso directo al resultado principal de ProjectName (activo)**. Puede cambiar el nombre del elemento de acceso directo, arrastrar y colocar el elemento en el nodo **Menú Programas del usuario** en el lado izquierdo de la ventana.

1. En la barra de menús, elija **Compilar** > **Administrador de configuración**. En la tabla **Proyecto**, en la columna **Compilar**, marque la casilla del proyecto de implementación. Haga clic en **Cerrar**.

1. En la barra de menús, seleccione **Compilar** > **Compilar solución** para compilar el proyecto MFC y el proyecto de implementación.

1. En la carpeta de soluciones, busque el programa setup.exe que se creó a partir del proyecto de implementación. Puede copiar este archivo, y también el archivo .msi, para instalar la aplicación y sus archivos de biblioteca necesarios en otro equipo. Ejecute el programa de instalación en un segundo equipo que no tenga las bibliotecas de Visual C++.

## <a name="see-also"></a>Vea también

[Ejemplos de implementación](deployment-examples.md)<br/>
