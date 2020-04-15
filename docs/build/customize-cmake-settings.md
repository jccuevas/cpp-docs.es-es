---
title: Personalización de la configuración de compilación de CMake en Visual Studio
ms.date: 08/20/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: c6bd1404799ccc9ad6b689646cd066849d48fca8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328679"
---
# <a name="customize-cmake-build-settings"></a>Personalización de la configuración de compilación de CMake

::: moniker range="vs-2019"

En Visual Studio 2019 y versiones posteriores, puede agregar configuraciones y personalizar sus opciones mediante el **Editor de configuración de CMake**. El editor está diseñado para ser una alternativa más sencilla a la edición manual del archivo *CMakeSettings.json,* pero si prefiere editar el archivo directamente, puede hacer clic en el vínculo **Editar JSON** en la parte superior derecha del editor.

Para abrir el editor, haga clic en el menú desplegable **Configuración** de la barra de herramientas y seleccione **Administrar configuraciones**.

![Lista desplegable de configuraciones de CMake](media/vs2019-cmake-manage-configurations.png)

Ahora puede ver el **Editor de configuración** con las configuraciones instaladas en la parte izquierda.

![Editor de configuración de CMake](media/cmake-settings-editor.png)

Visual Studio `x64-Debug` proporciona una configuración de forma predeterminada. Puede agregar configuraciones adicionales haciendo clic en el signo más verde. La configuración que se ve en el editor puede variar en función de la configuración seleccionada.

Las opciones que elija en el editor se escriben en un archivo denominado *CMakeSettings.json*. Este archivo proporciona argumentos de la línea de comandos y variables de entorno que se pasan a CMake al compilar los proyectos. Visual Studio nunca modifica *CMakeLists.txt* automáticamente; Mediante el uso de *CMakeSettings.json* puede personalizar la compilación a través de Visual Studio mientras deja los archivos de proyecto CMake intactos para que otros miembros de su equipo puedan consumirlos con cualquier herramienta que estén usando.

## <a name="cmake-general-settings"></a>Configuración general de CMake

Las opciones siguientes están disponibles en el encabezado **General**:

### <a name="configuration-name"></a>Nombre de la configuración

Se corresponde al valor **name**. Este nombre aparece en el menú desplegable de la configuración C++. Puede usar la macro `${name}` para crear otros valores de propiedad, como rutas de acceso.

### <a name="configuration-type"></a>Tipo de configuración

Se corresponde al valor **configurationType**. Define el tipo de configuración de compilación para el generador seleccionado. Los valores admitidos actualmente son "Debug", "MinSizeRel", "Release" y "RelWithDebInfo". Se asigna a [CMAKE_BUILD_TYPE](https://cmake.org/cmake/help/latest/variable/CMAKE_BUILD_TYPE.html).

### <a name="toolset"></a>Conjunto de herramientas

Se corresponde al valor **inheritedEnvironments**. Define el entorno del compilador que se usa para compilar la configuración seleccionada. Los valores admitidos dependen del tipo de configuración. Para crear un entorno personalizado, elija el vínculo **Editar JSON** en la esquina superior derecha del editor De configuración y edite el archivo *CMakeSettings.json* directamente.

### <a name="cmake-toolchain-file"></a>Archivo de cadena de herramientas de CMake

Ruta al archivo de cadena de [herramientas CMake](https://cmake.org/cmake/help/latest/variable/CMAKE_TOOLCHAIN_FILE.html). Esta ruta de acceso se pasa \<a CMake como "-DCMAKE_TOOLCHAIN_FILE - ruta de archivo>". Los archivos de cadena de herramientas especifican ubicaciones de compiladores y utilidades de cadena de herramientas, así como otra información relacionada con la plataforma de destino y el compilador. De forma predeterminada, Visual Studio usa el archivo de cadena de [herramientas vcpkg](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md#cmake) si esta configuración no está especificada.

### <a name="build-root"></a>Raíz de la compilación

Se corresponde a **buildRoot**. Se asigna a [CMAKE_BINARY_DIR](https://cmake.org/cmake/help/v3.15/variable/CMAKE_BINARY_DIR.html)y especifica dónde crear la caché de CMake. La carpeta especificada se crea si no existe.

## <a name="command-arguments"></a>Argumentos de comandos

Las opciones siguientes están disponibles en el encabezado **Argumentos de comandos**:

### <a name="cmake-command-arguments"></a>Argumentos de comandos de CMake

Se corresponde a **cmakeCommandArgs**. Especifica las opciones de línea de [comandos](https://cmake.org/cmake/help/latest/manual/cmake.1.html) adicionales que se pasan a CMake.exe.

### <a name="build-command-arguments"></a>Argumentos de comandos de compilación

Corresponde a **buildCommandArgs**. Especifica modificadores adicionales para pasar al sistema de compilación subyacente. Por ejemplo, `-v` pasar cuando se utiliza el generador Ninja fuerza Ninja a la salida de líneas de comandos.

### <a name="ctest-command-arguments"></a>Argumentos de comandos de CTest

Corresponde a **ctestCommandArgs**. Especifica opciones de línea de [comandos](https://cmake.org/cmake/help/v3.15/manual/ctest.1.html) adicionales para pasar a CTest al ejecutar pruebas.

## <a name="general-settings-for-remote-builds"></a>Configuración general para compilaciones remotas

Para las configuraciones como Linux en las que se usan compilaciones remotas, también están disponibles las opciones siguientes:

### <a name="rsync-command-arguments"></a>Argumentos de comandos de rsync

Opciones adicionales de línea de comandos pasadas a [rsync,](https://download.samba.org/pub/rsync/rsync.html)una herramienta de copia de archivos rápida y versátil.

## <a name="cmake-variables-and-cache"></a>Caché y variables de CMake

Esta configuración le permite establecer variables CMake y guardarlas en *CMakeSettings.json*. Se pasan a CMake en tiempo de compilación e invalidan los valores que se encuentran en el archivo *CMakeLists.txt.* Puede usar esta sección de la misma manera que usaría CMakeGUI para ver una lista de todas las variables de CMake disponibles para editar. Haga clic en el botón **Guardar y generar caché** para ver una lista de todas las variables de CMake disponibles para editar, incluidas las variables avanzadas (según CMakeGUI). Puede filtrar la lista por nombre de variable.

Corresponde a **variables**. Contiene un par nombre-valor de variables CMake pasadas como valor de * _nombre_=* **-D** a CMake. Si las instrucciones de compilación del proyecto CMake especifican la adición de variables directamente al archivo de caché de CMake, se recomienda agregarlas aquí en su lugar.

## <a name="advanced-settings"></a>Configuración avanzada

### <a name="cmake-generator"></a>Generador de CMake

Corresponde al **generador**. Se asigna al modificador CMake **-G** y especifica el [generador CMake](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) que se va a utilizar. Esta propiedad también se puede usar como una macro, `${generator}`, al crear otros valores de propiedad. En la actualidad, Visual Studio admite los generadores de CMake siguientes:

- "Ninja"
- "Archivos Make Unix"
- "Visual Studio 16 2019"
- "Visual Studio 16 2019 Win64"
- "Visual Studio 16 2019 ARM"
- "Visual Studio 15 2017"
- "Visual Studio 15 2017 Win64"
- "Visual Studio 15 2017 ARM"
- "Visual Studio 14 2015"
- "Visual Studio 14 2015 Win64"
- "Visual Studio 14 2015 ARM"
  
Debido a que Ninja está diseñado para velocidades de construcción rápidas en lugar de flexibilidad y función, se establece como el valor predeterminado. Pero es posible que algunos proyectos de CMake no se puedan generar correctamente mediante Ninja. Si esto ocurre, puede indicar a CMake que genere un proyecto de Visual Studio en su lugar.

### <a name="intellisense-mode"></a>Modo IntelliSense

El modo IntelliSense utilizado por el motor de IntelliSense. Si no se selecciona ningún modo, Visual Studio heredará del conjunto de herramientas especificado.  

### <a name="install-directory"></a>Directorio de instalación

El directorio en el que CMake instala destinos. Mapas a [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html).

### <a name="cmake-executable"></a>Ejecutable de CMake

La ruta de acceso completa al ejecutable del programa CMake, incluido el nombre de archivo y la extensión. Le permite usar una versión personalizada de CMake con Visual Studio. Para las compilaciones remotas, especifique la ubicación de CMake en el equipo remoto.

Para las configuraciones como Linux en las que se usan compilaciones remotas, también están disponibles las opciones siguientes:

### <a name="remote-cmakeliststxt-root"></a>CMakeLists.txt raíz remoto

El directorio del equipo remoto que contiene el archivo *cMakeLists.txt* raíz.

### <a name="remote-install-root"></a>Raíz de instalación remota

El directorio del equipo remoto en el que CMake instala los destinos. Mapas a [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html).

### <a name="remote-copy-sources"></a>Copiar orígenes en remoto

Especifica si se van a copiar los archivos de origen en el equipo remoto y se le permite especificar si se debe utilizar rsync o sftp.

## <a name="directly-edit-cmakesettingsjson"></a>Modificación directa del archivo CMakeSettings.json

También puede editar directamente *CMakeSettings.json* para crear configuraciones personalizadas. El **Editor de configuración** tiene un botón **Editar JSON** en la esquina superior derecha que abre el archivo para la edición.

En el ejemplo siguiente se muestra un ejemplo de configuración, que se puede usar como punto de partida:

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

JSON IntelliSense le ayuda a editar el archivo *CMakeSettings.json:*

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

El editor JSON también le informa cuando elige una configuración incompatible.

Para más información sobre cada una de las propiedades del archivo, vea [Referencia del esquema de CMakeSettings.json](cmakesettings-reference.md).

::: moniker-end

::: moniker range="<=vs-2017"

Visual Studio 2017 proporciona varias configuraciones de CMake que definen cómo se invoca CMake.exe para crear una caché de CMake para un proyecto determinado. Para agregar una configuración nueva, haga clic en el menú desplegable Configuración de la barra de herramientas y seleccione **Administrar configuraciones**:

   ![Administrar configuraciones de CMake](media/cmake-manage-configurations.png)

Puede elegir una de las opciones de la lista de configuraciones predefinidas:

   ![Configuraciones predefinidas de CMake](media/cmake-configurations.png)

La primera vez que seleccione una configuración, Visual Studio crea un archivo *CMakeSettings.json* en la carpeta raíz del proyecto. Este archivo se usa para volver a crear el archivo de caché de CMake, por ejemplo después de una operación **Limpiar**.

Para agregar una configuración adicional, haga clic con el botón derecho en *CMakeSettings.json* y elija **Agregar configuración**.

   ![Configuración de CMake Add](media/cmake-add-configuration.png "CMake Add Configuration")

También puede editar el archivo mediante el **Editor de configuración de CMake**. Haga clic con el botón derecho en *CMakeSettings.json* en el **Explorador** de soluciones y elija Editar configuración de **CMake**. También puede seleccionar **Administrar configuraciones** en la lista desplegable de configuraciones en la parte superior de la ventana del editor.

También puede editar directamente *CMakeSettings.json* para crear configuraciones personalizadas. En el ejemplo siguiente se muestra un ejemplo de configuración, que se puede usar como punto de partida:

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

JSON IntelliSense le ayuda a editar el archivo *CMakeSettings.json:*

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

Para más información sobre cada una de las propiedades del archivo, vea [Referencia del esquema de CMakeSettings.json](cmakesettings-reference.md).

::: moniker-end

## <a name="see-also"></a>Consulte también

[Proyectos de CMake en Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Configuración de un proyecto de CMake en Linux](../linux/cmake-linux-project.md)<br/>
[Conexión al equipo remoto Linux](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Configuración de sesiones de depuración de CMake](configure-cmake-debugging-sessions.md)<br/>
[Implementación, ejecución y depuración del proyecto de Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Referencia de configuración predefinida de CMake](cmake-predefined-configuration-reference.md)
