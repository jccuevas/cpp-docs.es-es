---
title: Configuración de proyectos de Linux para usar AddressSanitizer
description: Se describe cómo configurar un proyecto C++ de Linux en Visual Studio para usar AddressSanitizer.
ms.date: 06/07/2019
ms.openlocfilehash: 2415e8971614de35f046b699ce99c3822faf9372
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2019
ms.locfileid: "66824175"
---
# <a name="configure-linux-projects-to-use-address-sanitizer"></a>Configuración de proyectos de Linux para usar AddressSanitizer

En Visual Studio 2019 versión 16.1, la compatibilidad con AddressSanitizer (ASan) está integrada en los proyectos de Linux. ASan se puede habilitar tanto para proyectos de Linux basados en MSBuild como para proyectos de CMake. Funciona en sistemas Linux remotos y en el subsistema de Windows para Linux (WSL).

## <a name="about-asan"></a>Acerca de ASan

ASan es un detector de errores de memoria en tiempo de ejecución de C /C++ que encuentra los siguientes errores:

- Uso tras liberación (referencia de puntero pendiente)
- Desbordamiento de búfer de montón
- Desbordamiento de búfer de pila
- Uso tras devolución
- Uso tras ámbito
- Errores de orden de inicialización

Cuando ASan detecta un error, detiene la ejecución inmediatamente. Si se ejecuta un programa habilitado para ASan en el depurador, aparece un mensaje que describe el tipo de error, la dirección de memoria y la ubicación en el archivo de origen donde el error en cuestión se ha producido:

   ![Mensaje de error de ASan](media/asan-error.png)

La salida de ASan completa (incluido dónde se ha asignado o desasignado la memoria dañada) también se puede ver en el panel Depurar de la ventana de salida.

## <a name="enable-asan-for-msbuild-based-linux-projects"></a>Habilitar ASan para proyectos de Linux basados en MSBuild

Para habilitar ASan para proyectos de Linux basados en MSBuild, haga clic con el botón derecho en el **Explorador de soluciones** y seleccione **Propiedades**. Luego, vaya a **Propiedades de configuración** > **C/C++**  > **Instancias de Sanitizer**. ASan se habilita mediante marcas de compilador y enlazador, y requiere que el proyecto se vuelva a compilar para que funcione.

![Habilitar ASan para un proyecto de MSBuild](media/msbuild-asan-prop-page.png)

Se pueden pasar marcas de tiempo de ejecución de ASan opcionales; para ello, vaya a **Propiedades de configuración** > **Depuración** > **Marcas de entorno de ejecución de AddressSanitizer**. Haga clic en la flecha abajo para agregar o quitar marcas.

![Configurar marcas de tiempo de ejecución de ASan](media/msbuild-asan-runtime-flags.png)

## <a name="enable-asan-for-visual-studio-cmake-projects"></a>Habilitar ASan para proyectos de CMake de Visual Studio

Para habilitar ASan para CMake, haga clic con el botón derecho en el archivo CMakeLists.txt en el **Explorador de soluciones** y seleccione **Configuración de CMake para proyecto**.

Asegúrese de haber seleccionado una configuración de Linux (por ejemplo, **Linux-Debug**) en el panel izquierdo del cuadro de diálogo:

![Configuración Linux-Debug](media/linux-debug-configuration.png)

Las opciones de ASan están en **General**. Especifique las marcas de tiempo de ejecución de ASan (con el formato "marca=valor") separadas por punto y coma.

![Configuración Linux-Debug](media/cmake-settings-asan-options.png)

## <a name="install-the-asan-debug-symbols"></a>Instalar los símbolos de depuración ASan

Para habilitar los diagnósticos de ASan, hay que instalar los símbolos de depuración correspondientes (libasan-dbg) en el equipo Linux remoto o en la instalación de WSL. La versión de libasan-dbg que se cargue dependerá de la versión de GCC instalada en el equipo Linux:

|**Versión de ASan**|**Versión de GCC**|
| --- | --- |
|libasan0|gcc-4.8|
|libasan2|gcc-5|
|libasan3|gcc-6|
|libasan4|gcc-7|
|libasan5|gcc-8|

Para averiguar qué versión de GCC tiene, use este comando:

```bash
gcc --version
```

Para ver la versión de libasan-dbg que necesita, ejecute el programa y, a continuación, examine el panel **Depurar** de la ventana **Salida**. La versión de ASan que se cargue corresponde a la versión de libasan-dbg que se necesita en el equipo Linux. Puede usar **Ctrl+F** para buscar "libasan" en la ventana. Por ejemplo, si tiene libasan4, verá una línea similar a la siguiente:

```Output
Loaded '/usr/lib/x86_64-linux-gnu/libasan.so.4'. Symbols loaded.
```

Puede instalar los bits de depuración ASan en distribuciones de Linux que usen apt con el siguiente comando. Este comando instala la versión 4:

```bash
sudo apt-get install libasan4-dbg
```

Si ASan está habilitado, Visual Studio le pedirá en la parte superior del panel **Depurar** de la ventana **Salida** que instale los símbolos de depuración de ASan.
