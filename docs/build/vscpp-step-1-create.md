---
title: Cree un proyecto de aplicación de consola de C++ | Microsoft Docs
description: Crear una aplicación de consola Hola a todos en Visual C++
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: tutorial
ms.technology:
- cpp-tools
ms.devlang: C++
dev_langs:
- C++
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1dbd3c15aaf8d4702905ba1b8301b36cb9c1a2e0
ms.sourcegitcommit: 92c568e9466ffd7346a4120c478c9bdea61c8756
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2018
ms.locfileid: "47029559"
---
# <a name="create-a-c-console-app-project"></a>Cree un proyecto de aplicación de consola de C++

El habitual punto inicial para un programador de C++ es un "Hello, world!" aplicación que se ejecuta en la línea de comandos. Eso es lo que creará en Visual Studio en este paso.

## <a name="prerequisites"></a>Requisitos previos

- Hacer que Visual Studio con el desarrollo de escritorio con la carga de trabajo de C++ instalado y ejecutándose en el equipo. Si aún no está instalado, consulte [soporte de instalación de C++ en Visual Studio 2017](../build/vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Crear el proyecto de aplicación

Visual Studio usa *proyectos* para organizar el código de una aplicación y *soluciones* para organizar los proyectos. Un proyecto contiene todas las opciones, las configuraciones y reglas utilizadas para compilar sus aplicaciones y administra la relación entre todos los archivos del proyecto y todos los archivos externos. Para crear la aplicación, en primer lugar, creará un nuevo proyecto y solución.

1. En Visual Studio, abra el **archivo** menú y elija **nuevo > proyecto** para abrir el **nuevo proyecto** cuadro de diálogo.

   ![Abra el cuadro de diálogo nuevo proyecto](../build/media/vscpp-file-new-project.gif "abrir el cuadro de diálogo nuevo proyecto")

1. En el **nuevo proyecto** cuadro de diálogo, seleccione **instalado**, **Visual C++** si aún no está seleccionada y, a continuación, elija el **proyecto vacío** plantilla. En el **nombre** , introduzca *HelloWorld*. Elija **Aceptar** para crear el proyecto.

   ![Asigne un nombre y crear el nuevo proyecto](../build/media/vscpp-concierge-project-name-callouts.png "nombre y crear el nuevo proyecto")

Visual Studio crea un proyecto nuevo y vacío, listo para especializar para el tipo de aplicación que quiera para crear y agregar los archivos de código fuente. Haremos a continuación.

[Tenido un problema.](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>Convertir el proyecto en una aplicación de consola

Visual Studio puede crear todo tipo de aplicaciones y componentes de Windows y otras plataformas. El **proyecto vacío** plantilla no es específica acerca de qué tipo de aplicación crea. Para crear un *aplicación de consola*, uno que se ejecuta en una ventana de símbolo del sistema o de consola, debe indicar a Visual Studio para compilar la aplicación para utilizar el subsistema de consola.

1. En Visual Studio, abra el **proyecto** menú y elija **propiedades** para abrir el **páginas de propiedades HelloWorld** cuadro de diálogo.

1. En el **páginas de propiedades** cuadro de diálogo, en **propiedades de configuración**, seleccione **vinculador**, **sistema**y, a continuación, seleccione el cuadro de edición situado junto a el **subsistema** propiedad. En el menú desplegable que aparece, seleccione **consola (/ SUBSYSTEM: CONSOLE)**. Elija **Aceptar** para guardar los cambios.

   ![Abra el cuadro de diálogo páginas de propiedades](../build/media/vscpp-properties-linker-subsystem.gif "abrir el cuadro de diálogo páginas de propiedades")

Ahora conoce Visual Studio para compilar el proyecto se ejecute en una ventana de consola. A continuación, deberá agregar un archivo de código fuente y escriba el código de la aplicación.

[Tenido un problema.](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>Agregar un archivo de código fuente

1. En **el Explorador de soluciones**, seleccione el proyecto HelloWorld. En la barra de menús, elija **proyecto**, **Agregar nuevo elemento** para abrir el **Agregar nuevo elemento** cuadro de diálogo.

1. En el **Agregar nuevo elemento** cuadro de diálogo, seleccione **Visual C++** en **instalado** si no está ya seleccionado. En el panel central, seleccione **archivo C++ (.cpp)**. Cambiar el **nombre** a *HelloWorld.cpp*. Elija **agregar** para cerrar el cuadro de diálogo y crear el archivo.

   ![Agregar un archivo de código fuente para HelloWorld.cpp](../build/media/vscpp-add-new-item.gif "agregar un archivo de código fuente para HelloWorld.cpp")

Visual studio crea un archivo de código fuente nuevo y vacío y lo abre en una ventana del editor, preparada para entrar en el código fuente.

[Tenido un problema.](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>Agregue código al archivo de origen

1. Copie este código en la ventana del editor HelloWorld.cpp.

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   En la ventana del editor, el código debe tener el siguiente aspecto:

   ![Hola código del mundo en el editor](../build/media/vscpp-hello-world-editor.png "código Hello World en el editor")

Cuando el código tiene este aspecto en el editor, está listo para continuar con el paso siguiente y compilar la aplicación.

[Tenido un problema.](#add-a-source-code-file-issues)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Compilar y ejecutar un proyecto de C++](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>Guía de solución de problemas

Venir aquí para las soluciones a problemas comunes al crear su primer proyecto de C++.

### <a name="create-your-app-project-issues"></a>Crear la aplicación de problemas del proyecto

Si el **nuevo proyecto** no muestra el cuadro de diálogo un **Visual C++** entrada bajo **instalado**, probablemente la copia de Visual Studio no tiene el **Desktop desarrollo con C++** carga de trabajo instalada. Puede ejecutar el instalador directamente desde el **nuevo proyecto** cuadro de diálogo. Elija la **abrir Visual Studio Installer** vínculo para iniciar el programa de instalación de nuevo. Si el **User Account Control** diálogo solicita permisos, elija **Sí**. En el programa de instalación, asegúrese de que el **desarrollo de escritorio con C++** carga de trabajo está activada y elija **Aceptar** para actualizar la instalación de Visual Studio.

Si ya existe otro proyecto con el mismo nombre, elija otro nombre para el proyecto, o elimine el proyecto existente y vuelva a intentarlo. Para eliminar un proyecto existente, elimine la carpeta de solución (la carpeta que contiene el archivo helloworld.sln) en el Explorador de archivos.

[Volver atrás](#create-your-app-project).

### <a name="make-your-project-a-console-app-issues"></a>Convertir el proyecto en un problemas de aplicación de consola

Si no ve **vinculador** anuncie **propiedades de configuración**, elija **cancelar** para cerrar el **páginas de propiedades** cuadro de diálogo y, a continuación, Asegúrese de que el **HelloWorld** proyecto está seleccionado en **el Explorador de soluciones**, no la solución u otro archivo o carpeta, antes de que vuelva a intentarlo.

El control de lista desplegable no aparece en el **subsistema** cuadro de edición de propiedad hasta que haya seleccionado la propiedad. Puede seleccionar mediante el puntero, o puede presionar Tab para desplazarse por los controles de cuadro de diálogo hasta que **subsistema** está resaltado. Elija el control dropdown o presione ALT+flecha abajo para abrirlo.

[Volver](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>Agregar un problemas de archivos de código fuente

Es problema si asigna el archivo de código fuente a un nombre diferente. Sin embargo, no agregue más de un archivo de código fuente que contiene el mismo código a su proyecto.

Si agrega el tipo de archivo incorrecto al proyecto, por ejemplo, un archivo de encabezado, elimínelo y vuelva a intentarlo. Para eliminar el archivo, selecciónelo en **el Explorador de soluciones** y presione la tecla SUPR.

[Volver atrás](#add-a-source-code-file).

### <a name="add-code-to-the-source-file-issues"></a>Agregar código a los problemas de archivo de origen

Si accidentalmente ha cerrado la ventana de editor del archivo de código de origen, para abrirla de nuevo, haga doble clic en HelloWorld.cpp en el **el Explorador de soluciones** ventana.

Si aparece un subrayado ondulado rojo bajo cualquier elemento en el editor de código fuente, compruebe que el código coincide con el ejemplo de ortografía, puntuación y caso. Case es significativo en el código de C++.

[Volver atrás](#add-code-to-the-source-file).

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />