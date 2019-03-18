---
title: Configuración de sesiones de depuración de CMake en Visual Studio
ms.date: 03/05/2019
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 9a4dd009544a4590c336697ba2162eec45718869
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827925"
---
# <a name="configure-cmake-debugging-sessions"></a>Configurar sesiones de depuración de CMake

Todos los destinos de CMake ejecutables se muestran en la lista desplegable **Elemento de inicio** en la barra de herramientas **General**. Para empezar una sesión de depuración, seleccione una e inicie el depurador.

![Lista desplegable Elemento de inicio de CMake](media/cmake-startup-item-dropdown.png "CMake startup item dropdown")

También puede iniciar una sesión de depuración desde los menús de CMake.

## <a name="customize-debugger-settings"></a>Personalización de la configuración del depurador

Para personalizar la configuración del depurador para cualquier destino de CMake ejecutable en el proyecto, haga clic con el botón derecho en el archivo CMakeLists.txt específico y seleccione **Configuración de depuración e inicio**. Al seleccionar un destino de CMake en el submenú, se crea un archivo denominado `launch.vs.json`. Este archivo se ha rellenado previamente con información sobre el destino de CMake que ha seleccionado y permite especificar parámetros adicionales como argumentos de programa o el tipo de depurador. Para hacer referencia a cualquier clave en un archivo `CMakeSettings.json`, debe anteponer `cmake.` en `launch.vs.json`. En el ejemplo siguiente se muestra un archivo `launch.vs.json` simple que extrae el valor de la clave `remoteCopySources` en el archivo `CMakeSettings.json` para la configuración seleccionada actualmente:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "name": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "args": ["${cmake.remoteCopySources}"]
    }
  ]
}
```

Al guardar el archivo `launch.vs.json`, se crea una entrada en la lista desplegable **Elemento de inicio** con el nombre nuevo. Si se modifica el archivo `launch.vs.json`, se pueden crear tantas configuraciones de depuración como sea necesario para cualquier número de destinos de CMake.

## <a name="support-for-cmakesettings-variables"></a>Compatibilidad con las variables de CMakeSettings

 `Launch.vs.json` es compatible con las variables que se declaran en `CMakeSettings.json` (ver a continuación) y que se aplican a la configuración seleccionada actualmente. También tiene una clave denominada `currentDir`, que establece el directorio actual de la aplicación de inicio:

```json
{
  "type": "default",
  "project": "CMakeLists.txt",
  "projectTarget": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "name": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "currentDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}"
}
```

Al ejecutar la aplicación, el valor de `currentDir` es similar al siguiente:

```cmd
C:\Users\satyan\7f14809a-2626-873e-952e-cdf038211175\
```
## <a name="see-also"></a>Vea también

[Proyectos de CMake en Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Configuración de un proyecto de CMake en Linux](../linux/cmake-linux-project.md)<br/>
[Conexión al equipo remoto de Linux](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Personalización de la configuración de compilación de CMake](customize-cmake-settings.md)<br/>
[Configuración de sesiones de depuración de CMake](configure-cmake-debugging-sessions.md)<br/>
[Implementación, ejecución y depuración del proyecto de Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Referencia de configuración predefinida de CMake](cmake-predefined-configuration-reference.md)<br/>