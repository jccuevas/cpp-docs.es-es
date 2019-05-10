---
title: Personalización de la configuración de compilación de CMake en Visual Studio
ms.date: 04/25/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: 20ed066f71a5c8c3acb00ef5923fa5c9f16ac229
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877155"
---
# <a name="customize-cmake-build-settings"></a>Personalización de la configuración de compilación de CMake

::: moniker range="vs-2019"

En Visual Studio de 2019 y versiones posteriores, puede agregar configuraciones y personalizar su configuración mediante el **editor de configuración de CMake**. El editor está pensado para ser una alternativa más sencilla para editar manualmente el archivo CMakeSettings.json, pero si prefiere editar directamente el archivo, haga clic en el **editar JSON** vínculo en la esquina superior derecha del editor. 

Para abrir el editor, haga clic en el **configuración** desplegable en la barra de herramientas principal y elija **administrar configuraciones**.

![Lista desplegable de configuraciones de CMake](media/vs2019-cmake-manage-configurations.png)

Ahora puede ver el **Editor de configuración de** con las configuraciones instaladas a la izquierda. 

![Editor de configuración de CMake](media/cmake-settings-editor.png)

Visual Studio proporciona dos configuraciones de forma predeterminada: `x64-Debug` y `x86-Debug`. Puede agregar configuraciones adicionales, haga clic en el signo más verde. La configuración que se ve en el editor puede variar según la configuración seleccionada.

Las opciones que elija en el editor se escriben en un archivo denominado CMakeSettings.json. Este archivo proporciona argumentos de línea de comandos y variables de entorno que se pasan a CMake cuando se compilan los proyectos. Visual Studio modifica automáticamente; nunca CMakeLists.txt mediante el uso de CMakeSettings.json puede personalizar la compilación a través de Visual Studio mientras deja los archivos de proyecto CMake intacto para que otros miembros del equipo pueden consumirlos con herramientas que usan.

## <a name="cmake-general-settings"></a>Configuración General de CMake

Las siguientes opciones están disponibles en el **General** encabezado:

### <a name="configuration-name"></a>Nombre de configuración

Corresponde a la **nombre** configuración. Éste es el nombre que aparece en el C++ lista desplegable de configuración. Puede usar el `${name}` macro para crear otros valores de propiedad, como las rutas de acceso.


### <a name="configuration-type"></a>Tipo de configuración

Corresponde a la **configurationType** configuración. Define el tipo de configuración de compilación para el generador seleccionado. Los valores admitidos actualmente son "Debug", "MinSizeRel", "Release" y "RelWithDebInfo".

### <a name="toolset"></a>Conjunto de herramientas

Corresponde a la **inheritedEnvironments** configuración. Define el entorno de compilador que se usará para compilar la configuración seleccionada. Los valores admitidos dependen del tipo de configuración. Para crear un entorno personalizado, haga clic en el **editar JSON** vincular en la esquina superior derecha del editor de configuración y editar directamente el archivo CMakeSettings.json.

### <a name="cmake-toolchain-file"></a>Archivo de cadena de herramientas de CMake

Ruta de acceso al archivo de cadena de herramientas de CMake. Se pasará a CMake como "-DCMAKE_TOOLCHAIN_FILE = \<filepath >".

### <a name="build-root"></a>Raíz de compilación

Corresponde a **objeto buildRoot**. Se asigna a **-DCMAKE_BINARY_DIR** cambie y especifica dónde se creará la caché de CMake. Si la carpeta no existe, se creará.

## <a name="command-arguments"></a>Los argumentos de comandos

Las siguientes opciones están disponibles en el **argumentos de comandos** encabezado:

### <a name="cmake-command-arguments"></a>Argumentos de comando de CMake

Corresponde a **cmakeCommandArgs**. Especifica las opciones adicionales que van a pasar al CMake.exe.

### <a name="build-command-arguments"></a>Argumentos de comando de compilación

Corresponde a **buildCommandArgs**: especifica el sistema de compilación de modificadores de comandos adicionales que se pasan al subyacente. Por ejemplo, pasar -v cuando se usa el generador Ninja obliga a Ninja a dar como resultado líneas de comandos.


### <a name="ctest-command-arguments"></a>Argumentos de comando de CTest

Corresponde a**ctestCommandArgs**: especifica los modificadores de comandos adicionales para pasarlos a CTest al ejecutar pruebas.

## <a name="general-settings-for-remote-builds"></a>Configuración general para compilaciones remotas

Para las configuraciones, como Linux que usan compilaciones remotas, también están disponibles las siguientes opciones:

### <a name="rsync-command-arguments"></a>argumentos del comando rsync

Proporcione los argumentos de comando que se pasarán a rsync. 

## <a name="cmake-variables-and-cache"></a>Memoria caché y las variables de CMake

Estas opciones permiten establecer variables de CMake y guardarlos en CMakeSettings.json. Se pasarán a CMake en tiempo de compilación y reemplazará los valores pueden ser en el archivo CMakeLists.txt. Puede utilizar esta sección de la misma manera que puede usar el CMakeGUI para ver una lista de todas las variables de CMake disponibles para editar. Haga clic en el **guardar y generar la caché** botón para ver una lista de todas las variables de CMake disponibles para editar, incluidas las variables avanzadas (por el CMakeGUI). Puede filtrar la lista por nombre de variable. 

Corresponde a **variables**: contiene un par nombre-valor de variables de CMake se volverá a pasar como **-D** *_nombre_ =  _valor_* a CMake. Si las instrucciones de compilación del proyecto de CMake especifican la adición de las variables directamente al archivo de caché de CMake, en su lugar se recomienda agregarlas aquí.

## <a name="advanced-settings"></a>Configuración avanzada

### <a name="cmake-generator"></a>Generador de CMake

Corresponde a **generador**: se asigna a la CMake **- G** cambie y especifica el generador que se usará. Esta propiedad también se puede usar como una macro, `${generator}`, al crear otros valores de propiedad. En la actualidad, Visual Studio admite los generadores de CMake siguientes:

  - "Ninja"
  - "Unix archivos MAKE"
  - "Visual Studio 16 2019"
  - "Visual Studio 16 2019 Win64"
  - - "Visual Studio 16 2019 ARM"
  - "Visual Studio 15 2017"
  - "Visual Studio 15 2017 Win64"
  - "Visual Studio 15 2017 ARM"
  - "Visual Studio 14 2015"
  - "Visual Studio 14 2015 Win64"
  - "Visual Studio 14 2015 ARM"
  
  Como Ninja está diseñado para velocidades de compilación rápidas en lugar de flexibilidad y funcionamiento, se establece como el valor predeterminado. Pero es posible que algunos proyectos de CMake no se puedan generar correctamente mediante Ninja. Si esto ocurre, puede indicar a CMake que en su lugar genere un proyecto de Visual Studio.

### <a name="intellisense-mode"></a>Modo de IntelliSense

Para que IntelliSense preciso, establezca esta opción en el valor adecuado para su proyecto.

### <a name="install-directory"></a>Directorio de instalación

El directorio en el que CMake instala los destinos que se compila.

### <a name="cmake-executable"></a>Archivo ejecutable de CMake

La ruta de acceso completa al ejecutable CMake, incluidos el nombre de archivo y extensión. Para compilaciones remotas, especifique la ubicación de CMake en el equipo remoto.

Para las configuraciones, como Linux que usan compilaciones remotas, también están disponibles las siguientes opciones:

### <a name="remote-cmakeliststxt-root"></a>Raíz CMakeLists.txt remota

El directorio en el equipo remoto que contiene el archivo CMakeLists.txt de raíz.

### <a name="remote-install-root"></a>Raíz de instalación remota

El directorio en el equipo remoto en el que CMake instala los destinos.

### <a name="remote-copy-sources"></a>Orígenes de la copia remota

Especifica si se deben copiar los archivos de origen en la máquina remota y le permite especificar si se debe usar rsync o sftp. 

## <a name="directly-edit-cmakesettingsjson"></a>Editar directamente el archivo CMakeSettings.json

Puede editar directamente también `CMakeSettings.json` para crear configuraciones personalizadas. El **Editor de configuración de** tiene un **editar JSON** botón en la esquina superior derecha que se abre el archivo para editarlo. 

El ejemplo siguiente muestra un ejemplo de configuración, que puede usar como punto de partida:

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },

```

JSON IntelliSense le ayuda a editar el `CMakeSettings.json` archivo:

   ![IntelliSense de JSON para CMake](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

El editor de JSON también le informan cuando se elige la configuración incompatible.

Para obtener más información sobre cada una de las propiedades en el archivo, consulte [referencia de esquema de CMakeSettings.json](cmakesettings-reference.md).

::: moniker-end

::: moniker range="<=vs-2017"

Visual Studio 2017 proporciona varias configuraciones de CMake que definen cómo se invoca CMake.exe para crear la caché de CMake para un proyecto determinado. Para agregar una configuración nueva, haga clic en el menú desplegable Configuración de la barra de herramientas y seleccione **Administrar configuraciones**:

   ![Administrar configuraciones de CMake](media/cmake-manage-configurations.png)

Puede elegir una de las opciones de la lista de configuraciones predefinidas:

   ![Configuraciones predefinidas de CMake](media/cmake-configurations.png)

La primera vez que seleccione una configuración, Visual Studio creará un archivo `CMakeSettings.json` en la carpeta raíz del proyecto. Este archivo se usa para volver a crear el archivo de caché de CMake, por ejemplo después de una operación **Limpiar**. 

Para agregar una configuración adicional, haga clic con el botón derecho en `CMakeSettings.json` y elija **Agregar configuración**. 

   ![Agregar configuración de CMake](media/cmake-add-configuration.png "CMake Add Configuration")

También puede editar el archivo mediante el **Editor de configuración de CMake**. Haga clic con el botón derecho en `CMakeSettings.json` en el **Explorador de soluciones** y seleccione **Editar configuración de CMake**. También puede seleccionar **Administrar configuraciones** en la lista desplegable de configuraciones en la parte superior de la ventana del editor. 

Puede editar directamente también `CMakeSettings.json` crear configuraciones personalizadas en el ejemplo siguiente muestra un ejemplo de configuración, que puede usar como punto de partida:

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },

```

IntelliSense de JSON ayuda a editar el archivo `CMakeSettings.json`:

   ![IntelliSense de JSON para CMake](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

Para obtener más información sobre cada una de las propiedades en el archivo, consulte [referencia de esquema de CMakeSettings.json](cmakesettings-reference.md).

::: moniker-end

## <a name="see-also"></a>Vea también

[Proyectos de CMake en Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Configuración de un proyecto de CMake en Linux](../linux/cmake-linux-project.md)<br/>
[Conexión al equipo remoto de Linux](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Configuración de sesiones de depuración de CMake](configure-cmake-debugging-sessions.md)<br/>
[Implementación, ejecución y depuración del proyecto de Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Referencia de configuración predefinida de CMake](cmake-predefined-configuration-reference.md)<br/>
