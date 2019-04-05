---
title: Configuración de sesiones de depuración de CMake en Visual Studio
ms.date: 03/21/2019
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 9899f99994935ec419fff400670644b7d78a190a
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035353"
---
# <a name="configure-cmake-debugging-sessions"></a>Configurar sesiones de depuración de CMake

Todos los destinos de CMake ejecutables se muestran en la lista desplegable **Elemento de inicio** en la barra de herramientas **General**. Para empezar una sesión de depuración, seleccione una e inicie el depurador.

![Lista desplegable Elemento de inicio de CMake](media/cmake-startup-item-dropdown.png "CMake startup item dropdown")

También puede iniciar una sesión de depuración desde los menús de CMake.

## <a name="customize-debugger-settings"></a>Personalización de la configuración del depurador

Para personalizar la configuración del depurador para cualquier destino de CMake ejecutable en el proyecto, haga clic con el botón derecho en el archivo CMakeLists.txt específico y seleccione **Configuración de depuración e inicio**. (O seleccione un destino en **vista de destinos** en **el Explorador de soluciones**.) Al seleccionar un destino de CMake en el submenú, un archivo denominado **launch.vs.json** se crea. Este archivo se ha rellenado previamente con información sobre el destino de CMake que ha seleccionado y permite especificar parámetros adicionales como argumentos de programa o el tipo de depurador. Hacer referencia a cualquier clave en un **CMakeSettings.json** de archivos, comience con `cmake.` en **launch.vs.json**. El ejemplo siguiente muestra un sencillo **launch.vs.json** archivo que usa el valor de la `remoteCopySources` clave en el **CMakeSettings.json** archivo para la configuración seleccionada actualmente:

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

Tan pronto como guarda el **launch.vs.json** archivo, se crea una entrada en el **seleccionen** desplegable con el nuevo nombre. Editando el **launch.vs.json** archivo, puede crear tantas configuraciones de depuración como sea necesario para cualquier número de destinos de CMake.

## <a name="support-for-cmakesettings-variables"></a>Compatibilidad con las variables de CMakeSettings

 **Launch.VS.JSON** admite variables que se declaran en **CMakeSettings.json** (ver abajo) y que se aplican a la configuración seleccionada actualmente. También tiene una clave denominada `currentDir`, que establece el directorio actual de la aplicación de inicio para un proyecto local:

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

La clave "cwd" establece el directorio actual de la aplicación al iniciar un proyecto remoto. El valor predeterminado es '${debugInfo.defaultWorkingDirectory}' que se evalúa como 

```cmd
/var/tmp/src/bfc6f7f4-4f0f-8b35-80d7-9198fa973fb9/Linux-Debug
```

## <a name="see-also"></a>Vea también

[Proyectos de CMake en Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Configuración de un proyecto de CMake de Linux](../linux/cmake-linux-project.md)<br/>
[Conexión al equipo remoto Linux](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Personalización de la configuración de compilación de CMake](customize-cmake-settings.md)<br/>
[Configurar sesiones de depuración de CMake](configure-cmake-debugging-sessions.md)<br/>
[Implementar, ejecutar y depurar el proyecto de Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Referencia de configuración predefinida de CMake](cmake-predefined-configuration-reference.md)<br/>
