---
title: Creación de un proyecto de aplicación de consola de C++
description: Cree una aplicación de consola Hello World con Microsoft C++ en Visual Studio.
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 07e88da9a8a3712e1d37e319c29fd25aebce8ea7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749314"
---
# <a name="create-a-c-console-app-project"></a>Creación de un proyecto de aplicación de consola de C++

El punto de partida habitual para un programador de C++ es una aplicación "Hola mundo" que se ejecuta en la línea de comandos. Eso es lo que creará en Visual Studio en este paso.

## <a name="prerequisites"></a>Prerrequisitos

- Instalar y ejecutar Visual Studio con la carga de trabajo Desarrollo para el escritorio con C++ en el equipo. Si todavía no está instalada, vea [Instalar compatibilidad con C++ en Visual Studio](vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Creación del proyecto de aplicación

Visual Studio usa *proyectos* para organizar el código de una aplicación y *soluciones* para organizar los proyectos. Un proyecto contiene todas las opciones, las configuraciones y las reglas que se usan para compilar las aplicaciones. Administra la relación entre todos los archivos del proyecto y los archivos externos. Para crear la aplicación, primero tendrá que crear un proyecto y una solución.

::: moniker range=">=vs-2019"

1. En Visual Studio, abra **el** archivo menú y elija nuevo **> proyecto** para abrir el crear un **nuevo proyecto** cuadro de diálogo. Seleccione la plantilla Aplicación de **consola** que tiene etiquetas **C++,** **Windows**y **Consola** y, a continuación, elija **Siguiente**.

   ![Creación de un nuevo proyecto](media/vs2019-choose-console-app.png "Abra el cuadro de diálogo Crear un nuevo proyecto")

1. En el cuadro de diálogo Configurar el **nuevo proyecto,** escriba *HelloWorld* en el cuadro de edición Nombre del **proyecto.** Elija **Create (Crear)** para crear el proyecto.

   ![Nombre y cree el nuevo proyecto](media/vs2019-configure-new-project-hello-world.png "Nombre y cree el nuevo proyecto")

   Visual Studio crea un nuevo proyecto. Está listo para agregar y editar el código fuente. De forma predeterminada, la plantilla Aplicación de consola rellena el código fuente con una aplicación "Hello World":

   ![Proyecto Hello World en el IDE](media/vs2019-hello-world-code.png "Proyecto Hello World en el IDE")

   Cuando el código tiene este aspecto en el editor, estará listo para continuar con el paso siguiente y compilar la aplicación.

[He tenido un problema.](#create-your-app-project-issues)

::: moniker-end

::: moniker range="<=vs-2017"

1. En Visual Studio, abra **el** archivo menú y elija nuevo **> proyecto** para abrir el **nuevo proyecto** cuadro de diálogo.

   ![Apertura del cuadro de diálogo Nuevo proyecto](media/vscpp-file-new-project.gif "Apertura del cuadro de diálogo Nuevo proyecto")

1. En el cuadro de diálogo **Nuevo proyecto,** seleccione **Instalado > Visual C++** si aún no está seleccionado y, a continuación, elija la plantilla **Proyecto vacío.** En el campo **Nombre,** escriba *HelloWorld*. Elija **Aceptar** para crear el proyecto.

   ![Nombre y cree el nuevo proyecto](media/vscpp-concierge-project-name-callouts.png "Nombre y cree el nuevo proyecto")

Visual Studio crea un nuevo proyecto vacío. Está listo para que usted pueda especializarse para el tipo de aplicación que desea crear y para agregar sus archivos de código fuente. Se hará a continuación.

[He tenido un problema.](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>Convierte tu proyecto en una aplicación de consola

Visual Studio puede crear todo tipo de aplicaciones y componentes para Windows y otras plataformas. La plantilla **Proyecto vacío** no es específica sobre el tipo de aplicación que crea. Una aplicación de *consola* es una que se ejecuta en una consola o una ventana del símbolo del sistema. Para crear uno, debe indicar a Visual Studio que compile la aplicación para usar el subsistema de consola.

1. En Visual Studio, abra el menú **Proyecto** y elija **Propiedades** para abrir el cuadro de diálogo Páginas de **propiedades HelloWorld.**

1. En el cuadro de diálogo **Páginas** de propiedades, seleccione **Propiedades de configuración > Vinculador > sistema**y, a continuación, elija el cuadro de edición situado junto a la propiedad **Subsistema.** En el menú desplegable que aparece, seleccione **Consola (/SUBSYSTEM:CONSOLE)**. Elija **Aceptar** para guardar los cambios.

   ![Abra el cuadro de diálogo Páginas de propiedades](media/vscpp-properties-linker-subsystem.gif "Abra el cuadro de diálogo Páginas de propiedades")

Visual Studio ahora sabe compilar el proyecto para que se ejecute en una ventana de consola. A continuación, agregará un archivo de código fuente e introducirá el código de la aplicación.

[He tenido un problema.](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>Agregar un archivo de código fuente

1. En **el Explorador de soluciones**, seleccione el proyecto HelloWorld. En la barra de menús, elija **Proyecto**, **Agregar nuevo elemento** para abrir el cuadro de diálogo Agregar nuevo **elemento.**

1. En el cuadro de diálogo **Agregar nuevo elemento,** seleccione **Visual C++** en **Instalado** si aún no está seleccionado. En el panel central, seleccione **Archivo C++ (.cpp)**. Cambie el **nombre** a *HelloWorld.cpp*. Elija **Agregar** para cerrar el cuadro de diálogo y crear el archivo.

   ![Agregue un archivo de origen para HelloWorld.cpp](media/vscpp-add-new-item.gif "Agregue un archivo de origen para HelloWorld.cpp")

Visual studio crea un nuevo archivo de código fuente vacío y lo abre en una ventana del editor, listo para escribir el código fuente.

[He tenido un problema.](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>Agregar código al archivo fuente

1. Copie este código en la ventana del editor HelloWorld.cpp.

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   El código debe tener este aspecto en la ventana del editor:

   ![Hello World code en editor](media/vscpp-hello-world-editor.png "Hello World code en editor")

Cuando el código tiene este aspecto en el editor, estará listo para continuar con el paso siguiente y compilar la aplicación.

[He tenido un problema.](#add-a-source-code-file-issues)

::: moniker-end

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Construir y ejecutar un proyecto C++](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>Guía de solución de problemas

Venga aquí para encontrar soluciones a problemas comunes cuando cree su primer proyecto C++.

### <a name="create-your-app-project-issues"></a>Crear el proyecto de aplicación: problemas

::: moniker range="vs-2019"

El cuadro de diálogo **Nuevo proyecto** debe mostrar una plantilla de aplicación de **consola** que tenga etiquetas **C++,** **Windows**y **Consola.** Si no lo ves, hay dos causas posibles. Es posible que se filtre fuera de la lista o que no esté instalado. En primer lugar, compruebe los menús desplegables de filtro en la parte superior de la lista de plantillas. Establézcalos en **C++,** **Windows**y **Consola**. Debería aparecer la plantilla **de aplicación** de consola C++; de lo contrario, el desarrollo de escritorio con carga de trabajo **C++** no está instalado.

Para instalar el desarrollo de **escritorio con C++,** puede ejecutar el instalador directamente desde el cuadro de diálogo **Nuevo proyecto.** Elija el vínculo **Instalar más herramientas y características** en la parte inferior de la lista de plantillas para iniciar el instalador. Si el cuadro de diálogo **Control de cuentas** de usuario solicita permisos, elija **Sí**. En el instalador, asegúrese de que la carga de trabajo Desarrollo de **escritorio con C++** esté activada. A continuación, elija **Modify** para actualizar la instalación de Visual Studio.

Si ya existe otro proyecto con el mismo nombre, elija otro nombre para el proyecto. O bien, elimine el proyecto existente e inténtelo de nuevo. Para eliminar un proyecto existente, elimine la carpeta de la solución (la carpeta que contiene el archivo *helloworld.sln)* en el Explorador de archivos.

[Vuelva](#create-your-app-project).

::: moniker-end

::: moniker range="vs-2017"

Si el cuadro de diálogo **Nuevo proyecto** no muestra una entrada de **Visual C++** en **Instalado**, es probable que la copia de Visual Studio no tenga instalada la carga de trabajo Desarrollo de escritorio con Carga de trabajo **C++.** Puede ejecutar el instalador directamente desde el cuadro de diálogo **Nuevo proyecto.** Elija el vínculo **Abrir el instalador** de Visual Studio para iniciar el instalador de nuevo. Si el cuadro de diálogo **Control de cuentas** de usuario solicita permisos, elija **Sí**. Actualice el instalador si es necesario. En el instalador, asegúrese de que la carga de trabajo Desarrollo de **escritorio con C++** está activada y elija **Aceptar** para actualizar la instalación de Visual Studio.

::: moniker-end

::: moniker range="<=vs-2017"

Si ya existe otro proyecto con el mismo nombre, elija otro nombre para el proyecto. O bien, elimine el proyecto existente e inténtelo de nuevo. Para eliminar un proyecto existente, elimine la carpeta de la solución (la carpeta que contiene el archivo *helloworld.sln)* en el Explorador de archivos.

[Vuelva](#create-your-app-project).

### <a name="make-your-project-a-console-app-issues"></a>Convierte tu proyecto en una aplicación de consola: problemas

Si no ve **vinculador** en **Propiedades de configuración**, elija **Cancelar** para cerrar el cuadro de diálogo **Páginas** de propiedades. Asegúrese de que el proyecto **HelloWorld** está seleccionado en el **Explorador** de soluciones antes de intentarlo de nuevo. No seleccione la solución **HelloWorld** u otro elemento en el Explorador de **soluciones**.

El control desplegable no aparece en el cuadro de edición de la propiedad **SubSystem** hasta que seleccione la propiedad. Haga clic en el cuadro de edición para seleccionarlo. O bien, puede presionar **Tab** para desplazarse por los controles de cuadro de diálogo hasta que se resalte **SubSystem.** Elija el control desplegable o pulse **Alt+Abajo** para abrirlo.

[Volver](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>Añadir un archivo de código fuente: problemas

Está bien si le das al archivo de código fuente un nombre diferente. Sin embargo, no agregue más de un archivo que contenga el mismo código al proyecto.

Si ha agregado el tipo de archivo incorrecto al proyecto, como un archivo de encabezado, elimínelo e inténtelo de nuevo. Para eliminar el archivo, selecciónelo en el Explorador de **soluciones**. A continuación, pulse la tecla **Suprimir.**

[Vuelva](#add-a-source-code-file).

### <a name="add-code-to-the-source-file-issues"></a>Agregar código al archivo fuente: problemas

Si accidentalmente cerró la ventana del editor de archivos de código fuente, puede abrirla fácilmente de nuevo. Para abrirlo, haga doble clic en HelloWorld.cpp en la ventana **Explorador** de soluciones.

Si las ondulaciones rojas aparecen debajo de cualquier elemento en el editor de código fuente, compruebe que el código coincide con el ejemplo de ortografía, puntuación y mayúsculas y minúsculas. El caso es significativo en el código C++.

[Vuelva](#add-code-to-the-source-file).

::: moniker-end

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
