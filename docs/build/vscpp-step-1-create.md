---
title: "Cree un proyecto de aplicación de consola de C++ | Documentos de Microsoft"
description: Instalar la compatibilidad de Visual Studio para Visual C++
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: get-started-article
ms.technology: devlang-C++
ms.devlang: C++
dev_langs: C++
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e44d9c097461b118cae72b47dff2ab15757aed64
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="create-a-c-console-app-project"></a>Cree un proyecto de aplicación de consola de C++

Punto de la partida habitual de un programador de C++ es un "Hello, world!" aplicación que se ejecuta en la línea de comandos. Es lo que creará en Visual Studio en este paso.

## <a name="prerequisites"></a>Requisitos previos

- Hacer que Visual Studio con el desarrollo de escritorio con cargas de trabajo de C++ instalados y ejecutándose en el equipo. Si aún no está instalado, consulte [compatibilidad instalar C++ en Visual Studio](../build/vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Crear el proyecto de aplicación

Visual Studio usa *proyectos* para organizar el código de una aplicación y *soluciones* para organizar los proyectos. Un proyecto contiene todas las opciones, las configuraciones y reglas que se usan para compilar las aplicaciones y administra la relación entre todos los archivos del proyecto y todos los archivos externos. Para crear la aplicación, en primer lugar, creará un nuevo proyecto y solución.

1. En Visual Studio, abra el **archivo** menú y elija **nuevo > proyecto** para abrir el **nuevo proyecto** cuadro de diálogo.

   ![Abra el cuadro de diálogo nuevo proyecto](../build/media/vscpp-file-new-project.gif "abrir el cuadro de diálogo nuevo proyecto")

1. En el **nuevo proyecto** cuadro de diálogo, seleccione **instalado**, **Visual C++** si aún no está seleccionada y, a continuación, elija la **proyecto vacío** plantilla. En el **nombre** , escriba *HelloWorld*. Elija **Aceptar** para crear el proyecto.

   ![Asigne un nombre y crear el nuevo proyecto](../build/media/vscpp-concierge-project-name-callouts.png "nombre y crear el nuevo proyecto")

Visual Studio crea un proyecto nuevo y vacío, listo para permitirle especializar para el tipo de aplicación que desee crear y agregar los archivos de código fuente. Deberá llevar a cabo ahora dicho componente.

[Produjo un problema.](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>Poner un proyecto a una aplicación de consola

Visual Studio puede crear todo tipo de aplicaciones y componentes para Windows y otras plataformas. El **proyecto vacío** plantilla no es específica acerca de qué tipo de aplicación crea. Para crear un *aplicación de consola*, uno que se ejecuta en una consola o una ventana de símbolo del sistema, debe indicar a Visual Studio para compilar la aplicación para utilizar el subsistema de consola.

1. En Visual Studio, abra el **proyecto** menú y elija **propiedades** para abrir el **páginas de propiedades de HelloWorld** cuadro de diálogo.

1. En el **páginas de propiedades** cuadro de diálogo, en **propiedades de configuración**, seleccione **vinculador**, **System**y, a continuación, elija el cuadro de edición junto a el **subsistema** propiedad. En el menú desplegable que aparece, seleccione **consola (/ SUBSYSTEM: CONSOLE)**. Elija **Aceptar** para guardar los cambios.

   ![Abra el cuadro de diálogo páginas de propiedades](../build/media/vscpp-properties-linker-subsystem.gif "abrir el cuadro de diálogo páginas de propiedades")

Ahora conoce Visual Studio para compilar el proyecto para ejecutarse en una ventana de consola. A continuación, se agregará un archivo de código fuente y escriba el código de la aplicación.

[Produjo un problema.](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>Agregar un archivo de código fuente

1. En **el Explorador de soluciones**, seleccione el proyecto HelloWorld. En la barra de menús, elija **proyecto**, **Agregar nuevo elemento** para abrir el **Agregar nuevo elemento** cuadro de diálogo.

1. En el **Agregar nuevo elemento** cuadro de diálogo, seleccione **Visual C++** en **instalado** si aún no está activada. En el panel central, seleccione **archivo C++ (.cpp)**. Cambiar el **nombre** a *HelloWorld.cpp*. Elija **agregar** para cerrar el cuadro de diálogo y crear el archivo.

   ![Agregar un archivo de código fuente para HelloWorld.cpp](../build/media/vscpp-add-new-item.gif "agregar un archivo de código fuente para HelloWorld.cpp")

Visual studio crea un archivo de código fuente nueva y vacía y abre en una ventana del editor, preparada para entrar en el código fuente.

[Produjo un problema.](#add-a-source-code-file-issues)

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

   ![Hola código World en el editor de](../build/media/vscpp-hello-world-editor.png "código de Hello World en el editor")

Cuando el código tiene este aspecto en el editor, está listo para continuar con el paso siguiente y compilar la aplicación.

[Produjo un problema.](#add-a-source-code-file-issues)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Compilar y ejecutar un proyecto de C++](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>Guía de solución de problemas

Venir aquí para las soluciones a problemas comunes al crear su primer proyecto de C++.

### <a name="create-your-app-project-issues"></a>Crear la aplicación de problemas del proyecto

Si el **nuevo proyecto** no muestra el cuadro de diálogo una **Visual C++** entrada bajo **instalado**, probablemente no tiene su copia de Visual Studio la **escritorio desarrollo con C++** instalada de la carga de trabajo. Puede ejecutar el programa de instalación directamente desde el **nuevo proyecto** cuadro de diálogo. Elija la **abrir Visual Studio Installer** vínculo para iniciar el programa de instalación de nuevo. Si el **User Account Control** diálogo solicita permisos, elija **Sí**. En el programa de instalación, asegúrese de que el **el desarrollo de escritorio con C++** carga de trabajo está activada y elija **Aceptar** para actualizar la instalación de Visual Studio.

Si ya existe otro proyecto con el mismo nombre, elija otro nombre para el proyecto, o elimine el proyecto existente y vuelva a intentarlo. Para eliminar un proyecto existente, elimine la carpeta de soluciones (la carpeta que contiene el archivo helloworld.sln) en el Explorador de archivos.

[Volver atrás](#create-your-app-project).

### <a name="make-your-project-a-console-app-issues"></a>Poner un proyecto a los problemas de una aplicación de consola

Si no ve **vinculador** aparecen en **propiedades de configuración**, elija **cancelar** para cerrar el **páginas de propiedades** cuadro de diálogo y, a continuación, Asegúrese de que el **HelloWorld** proyecto está seleccionado en **el Explorador de soluciones**, no la solución u otro archivo o carpeta, antes de volver a intentarlo.

El control de lista desplegable no aparece en la **subsistema** cuadro de edición de propiedad hasta que haya seleccionado la propiedad. Se puede seleccionar mediante el puntero, o puede presionar Tab para desplazarse por los controles de cuadro de diálogo hasta que **subsistema** se resalta. Elija el control de lista desplegable o presione ALT+flecha abajo para abrirlo.

[Volver](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>Agregar un problemas de archivos de código fuente

Es correcto si asigna el archivo de código fuente de un nombre diferente. Sin embargo, no agregue más de un archivo de código fuente que contiene el mismo código para el proyecto.

Si ha agregado el tipo incorrecto de archivo al proyecto, por ejemplo, un archivo de encabezado, elimínelo y vuelva a intentarlo. Para eliminar el archivo, selecciónelo en **el Explorador de soluciones** y presione la tecla SUPR.

[Volver atrás](#add-a-source-code-file).

### <a name="add-code-to-the-source-file-issues"></a>Agregue código a los problemas de archivo de origen

Si por accidente cierra la ventana de editor del archivo de código de origen, para abrirla de nuevo, haga doble clic en HelloWorld.cpp en el **el Explorador de soluciones** ventana.

Si aparece un subrayado ondulado rojo en nada en el editor de código fuente, compruebe que el código coincide con el ejemplo de ortografía y mayúsculas y signos de puntuación. Caso es significativo en el código de C++.

[Volver atrás](#add-code-to-the-source-file).

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />