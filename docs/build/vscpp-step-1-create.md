---
title: Creación de un proyecto de aplicación de consola de C++
description: Cree una aplicación de consola de Hola mundo mediante Microsoft C++ en Visual Studio.
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 07e88da9a8a3712e1d37e319c29fd25aebce8ea7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749314"
---
# <a name="create-a-c-console-app-project"></a>Creación de un proyecto de aplicación de consola de C++

El punto de partida habitual para un programador de C++ es una aplicación "Hola mundo" que se ejecuta en la línea de comandos. Esto es lo que se va a crear en Visual Studio en este paso.

## <a name="prerequisites"></a>Requisitos previos

- Instalar y ejecutar Visual Studio con la carga de trabajo Desarrollo para el escritorio con C++ en el equipo. Si todavía no está instalada, vea [Instalar compatibilidad con C++ en Visual Studio](vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Creación del proyecto de aplicación

Visual Studio usa *proyectos* para organizar el código de una aplicación y *soluciones* para organizar los proyectos. Un proyecto contiene todas las opciones, las configuraciones y las reglas que se usan para compilar las aplicaciones. Administra la relación entre todos los archivos del proyecto y cualquier archivo externo. Para crear la aplicación, primero tendrá que crear un proyecto y una solución.

::: moniker range=">=vs-2019"

1. En Visual Studio, abra el menú **Archivo** y elija **Nuevo > Proyecto** para abrir el cuadro de diálogo **Crear un nuevo proyecto**. Seleccione la plantilla **Aplicación de la consola** que tiene las etiquetas **C++** , **Windows** y **Consola** y, después, elija **Siguiente**.

   ![Creación de un nuevo proyecto](media/vs2019-choose-console-app.png "Apertura del cuadro de diálogo Crear un nuevo proyecto")

1. En el cuadro de diálogo **Configurar el nuevo proyecto**, escriba *HelloWorld* en el cuadro de edición **Nombre del proyecto**. Elija **Crear** para crear el proyecto.

   ![Asignar un nombre y crear el nuevo proyecto](media/vs2019-configure-new-project-hello-world.png "Asignación de un nombre y creación de un proyecto nuevo")

   Visual Studio crea un proyecto nuevo. Está a punto para agregar y editar el código fuente. De forma predeterminada, la plantilla de la Aplicación de consola rellena el código fuente con una aplicación "Hola mundo":

   ![Proyecto Hola mundo en el IDE](media/vs2019-hello-world-code.png "Proyecto Hola mundo en el IDE")

   Cuando el código tiene este aspecto en el editor, está a punto para continuar con el paso siguiente y compilar la aplicación.

[He tenido un problema.](#create-your-app-project-issues)

::: moniker-end

::: moniker range="<=vs-2017"

1. En Visual Studio, abra el menú **Archivo** y elija **Nuevo > Proyecto** para abrir el cuadro de diálogo **Nuevo proyecto**.

   ![Apertura del cuadro de diálogo Nuevo proyecto](media/vscpp-file-new-project.gif "Apertura del cuadro de diálogo Nuevo proyecto")

1. En el cuadro de diálogo **Nuevo proyecto**, seleccione **Instalado > Visual C++** si aún no se ha seleccionado y luego elija la plantilla **Proyecto vacío**. En el campo **Nombre**, escriba *HelloWorld*. Elija **Aceptar** para crear el proyecto.

   ![Asignación de un nombre y creación del nuevo proyecto](media/vscpp-concierge-project-name-callouts.png "Asignación de un nombre y creación de un proyecto nuevo")

Visual Studio crea un proyecto nuevo vacío. Está a punto para que se especialice en el tipo de aplicación que quiere crear y para agregar los archivos de código fuente. Se hará a continuación.

[He tenido un problema.](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>Conversión del proyecto en una aplicación de consola

Visual Studio puede crear todo tipo de aplicaciones y componentes para Windows y otras plataformas. La plantilla **Proyecto vacío** no es específica sobre el tipo de aplicación que crea. Una *aplicación de consola* es una que se ejecuta en una consola o en una ventana del símbolo del sistema. Para crear una, debe indicar a Visual Studio que compile la aplicación para usar el subsistema de la consola.

1. En Visual Studio, abra el menú **Proyecto** y elija **Propiedades** para abrir el cuadro de diálogo **Páginas de propiedades de HelloWorld**.

1. En el cuadro de diálogo **Páginas de propiedades**, seleccione **Propiedades de configuración > Enlazador > Sistema** y, después, elija el cuadro de edición situado junto a la propiedad **Subsistema**. En el menú desplegable que aparece, seleccione **Consola (/SUBSYSTEM:CONSOLE)** . Elija **Aceptar** para guardar los cambios.

   ![Apertura del cuadro de diálogo Páginas de propiedades](media/vscpp-properties-linker-subsystem.gif "Apertura del cuadro de diálogo Páginas de propiedades")

Visual Studio ahora sabe compilar el proyecto para que se ejecute en una ventana de consola. Después, agregará un archivo de código fuente y escribirá el código para la aplicación.

[He tenido un problema.](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>Incorporación de un archivo de código fuente

1. En el **Explorador de soluciones**, seleccione el proyecto HelloWorld. En la barra de menús, elija **Proyecto**, **Agregar nuevo elemento** para abrir el cuadro de diálogo **Agregar nuevo elemento**.

1. En el cuadro de diálogo **Agregar nuevo elemento**, en **Instalado** seleccione **Visual C++** si aún no lo está. En el panel central, seleccione **Archivo de C++ (.cpp)** . Cambie el **Nombre** por *HelloWorld.cpp*. Elija **Agregar** para cerrar el cuadro de diálogo y crear el archivo.

   ![Incorporación de un archivo de código fuente HelloWorld.cpp](media/vscpp-add-new-item.gif "Incorporación de un archivo de código fuente HelloWorld.cpp")

Visual Studio crea un nuevo archivo de código fuente vacío y lo abre en una ventana del editor, lista para escribir el código fuente.

[He tenido un problema.](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>Incorporación de código al archivo de código fuente

1. Copie este código en la ventana del editor HelloWorld.cpp.

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   En la ventana del editor, el código debería tener un aspecto similar a este:

   ![Código de Hola mundo en el editor](media/vscpp-hello-world-editor.png "Código de Hola mundo en el editor")

Cuando el código tiene este aspecto en el editor, está a punto para continuar con el paso siguiente y compilar la aplicación.

[He tenido un problema.](#add-a-source-code-file-issues)

::: moniker-end

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Compilación y ejecución de un proyecto de C++](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>Guía de solución de problemas

Aquí puede encontrar soluciones a incidencias comunes al crear su primer proyecto de C++.

### <a name="create-your-app-project-issues"></a>Creación del proyecto de aplicación: incidencias

::: moniker range="vs-2019"

El cuadro de diálogo **Nuevo proyecto** debe mostrar una plantilla de **Aplicación de consola** que tenga las etiquetas **C++** , **Windows** y **Consola**. Si no se ve, se debe a dos causas posibles. Puede que se filtre de la lista o que no esté instalada. En primer lugar, active las listas desplegables de filtros en la parte superior de la lista de plantillas. Establézcalas en **C++** , **Windows** y **Consola**. La plantilla **Aplicación de consola** de C++ debe aparecer; en caso contrario, la carga de trabajo **Desarrollo para el escritorio con C++** no está instalada.

Para instalar **Desarrollo para el escritorio con C++** , se puede ejecutar el instalador directamente desde el cuadro de diálogo **Nuevo proyecto**. Elija el vínculo **Instalar más herramientas y características** situado en la parte inferior de la lista de plantillas para iniciar el instalador. Si el cuadro de diálogo **Control de cuentas de usuario** solicita permisos, elija **Sí**. En el instalador, asegúrese de que la carga de trabaja **Desarrollo para el escritorio con C++** está activada. Luego elija **Modificar** para actualizar la instalación de Visual Studio.

Si ya existe otro proyecto con el mismo nombre, elija otro nombre para el proyecto. También puede eliminar el proyecto existente e intentarlo de nuevo. Para eliminar un proyecto existente, elimine la carpeta de la solución (la carpeta que contiene el archivo *helloworld.sln*) en el Explorador de archivos.

[Volver](#create-your-app-project)

::: moniker-end

::: moniker range="vs-2017"

Si en el cuadro de diálogo **Nuevo proyecto** no se muestra una entrada de **Visual C++** en **Instalado**, es probable que su copia de Visual Studio no tenga instalada la carga de trabajo **Desarrollo para el escritorio con C++** . Puede ejecutar el instalador directamente desde el cuadro de diálogo **Nuevo proyecto**. Para iniciar el instalador de nuevo, elija el vínculo **Abrir el Instalador de Visual Studio**. Si el cuadro de diálogo **Control de cuentas de usuario** solicita permisos, elija **Sí**. Actualice el instalador en caso necesario. En el instalador, asegúrese de que la carga de trabajo **Desarrollo para el escritorio con C++** está activada y elija **Aceptar** para actualizar la instalación de Visual Studio.

::: moniker-end

::: moniker range="<=vs-2017"

Si ya existe otro proyecto con el mismo nombre, elija otro nombre para el proyecto. También puede eliminar el proyecto existente e intentarlo de nuevo. Para eliminar un proyecto existente, elimine la carpeta de la solución (la carpeta que contiene el archivo *helloworld.sln*) en el Explorador de archivos.

[Volver](#create-your-app-project)

### <a name="make-your-project-a-console-app-issues"></a>Conversión del proyecto en una aplicación de consola: incidencias

Si el **Enlazador** no aparece en **Propiedades de configuración**, elija **Cancelar** para cerrar el cuadro de diálogo **Páginas de propiedades**. Asegúrese de que el proyecto **HelloWorld** está seleccionado en **Explorador de soluciones** antes de intentarlo de nuevo. No seleccione la solución **HelloWorld**, u otro elemento, en **Explorador de soluciones**.

El control desplegable no aparece en el cuadro de edición de la propiedad **Subsistema** hasta que se selecciona la propiedad. Haga clic en el cuadro de edición para seleccionarla. También puede presionar **Pestaña** para desplazarse por los controles de cuadro de diálogo hasta que **Subsistema** esté resaltado. Elija el control desplegable o presione **Alt+Flecha abajo** para abrirlo.

[Volver](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>Incorporación de un archivo de código fuente: incidencias

Es correcto si asigna un nombre diferente al archivo de código fuente. Sin embargo, no agregue más de un archivo al proyecto que contenga el mismo código.

Si se ha agregado un tipo de archivo incorrecto al proyecto, como un archivo de encabezado, elimínelo e inténtelo de nuevo. Para eliminar el archivo, selecciónelo en **Explorador de soluciones**. Luego presione la tecla **Eliminar**.

[Volver](#add-a-source-code-file)

### <a name="add-code-to-the-source-file-issues"></a>Incorporación de código al archivo de código fuente: incidencias

Si se ha cerrado accidentalmente la ventana del editor de archivos de código fuente, puede volver a abrirla fácilmente. Para abrirla, haga doble clic en HelloWorld.cpp en la ventana del **Explorador de soluciones**.

Si aparecen subrayados ondulados de color rojo en cualquier elemento del editor de código fuente, compruebe que el código coincida con el ejemplo en ortografía, puntuación y mayúsculas y minúsculas. La distinción entre mayúsculas y minúsculas es significativo en el código de C++.

[Volver](#add-code-to-the-source-file)

::: moniker-end

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
