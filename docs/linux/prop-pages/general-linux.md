---
title: Propiedades generales (proyecto de C++ para Linux)
description: Describe las propiedades del proyecto de Linux que se pueden establecer en Visual Studio desde la página Propiedades generales.
ms.date: 01/14/2020
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
ms.openlocfilehash: 832f10ca2c95e40ff7ece23462105fa49014aa5d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "79446164"
---
# <a name="general-properties-linux-c"></a>Propiedades generales (C++ para Linux)

::: moniker range="vs-2015"

La compatibilidad con Linux está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range=">=vs-2017"

| Propiedad. | Descripción | Opciones |
|--|--|--|
| Directorio de salida | Especifica una ruta de acceso relativa al directorio de archivos de salida. Puede incluir variables de entorno. |
| Directorio intermedio | Especifica una ruta de acceso relativa al directorio de archivos intermedios. Puede incluir variables de entorno. |
| Nombre de destino | Especifica el nombre de archivo que este proyecto genera. |
| Extensión de destino | Especifica la extensión de archivo (por ejemplo, `.a`) que este proyecto genera. |
| Extensiones para eliminar al limpiar | Especificación de comodines delimitados por punto y coma para indicar qué archivos del directorio de archivos intermedios se deben eliminar al limpiar o recompilar. |
| Archivo de registro de compilación | Especifica el archivo de registro de compilación en el que se escribe cuando está habilitada la opción de registro de compilación. |
| Conjunto de herramientas de la plataforma | Especifica el conjunto de herramientas usado para compilar la configuración actual. Si no se establece, se utiliza el conjunto de herramientas predeterminado. |
| Máquina de compilación remota | Muestra la máquina o dispositivo de destino que debe usarse para la compilación, implementación y depuración remotas. Puede agregar o editar una conexión a una máquina de destino con **Herramientas** > **Opciones** > **Multiplataforma** > **Administrador de conexiones**.<br /> **Visual Studio 2019 versión 16.1** Puede especificar otro equipo para la depuración en la página [Depuración](debugging-linux.md). |
| Directorio raíz de la compilación remota | Especifica una ruta de acceso a un directorio de la máquina o el dispositivo remotos. |
| Directorio del proyecto de compilación remota | Especifica una ruta de acceso a un directorio de la máquina o el dispositivo remotos para el proyecto. |
| Directorio de implementación remota | **Visual Studio 2019 versión 16.1** Se especifica la ruta de acceso del directorio en el equipo o dispositivo remoto para implementar el proyecto. |
| Directorios incluidos en la copia remota | **Visual Studio 2019 versión 16.5** Una lista de directorios que se copiarán de forma recursiva desde el destino de Linux. Esta propiedad afecta a la copia remota de encabezados para IntelliSense, pero no a la compilación. Se puede usar cuando **IntelliSense usa los valores predeterminados del compilador** está establecido en false. Use **Directorios de inclusión adicionales** en la pestaña General de C/C++ para especificar directorios de inclusión adicionales que se usarán tanto para IntelliSense como para compilación. |
| Directorios excluidos de la copia remota | **Visual Studio 2019 versión 16.5** Una lista de directorios que *no* se copiarán desde el destino de Linux. Normalmente, esta propiedad se usa para quitar subdirectorios de los directorios de inclusión. |
| IntelliSense usa los valores predeterminados del compilador | **Visual Studio 2019 versión 16.5** Si se va a consultar al compilador al que hace referencia este proyecto sobre su lista predeterminada de ubicaciones de inclusión. Estas ubicaciones se agregan automáticamente a la lista de directorios remotos que se van a copiar. Establezca esta propiedad en false si el compilador no admite parámetros de tipo gcc. Los compiladores gcc y clang admiten consultas para los directorios de inclusión (por ejemplo, `g++ -x c++ -E -v -std=c++11`). |
| Tipo de configuración | Especifica el tipo de salida que genera esta configuración. | **Biblioteca dinámica (.so)**<br/><br/>**Biblioteca estática (.a)**<br/><br/>**Aplicación (.out)**<br/><br/>**Archivo Make** |
| Uso de STL | Especifica la biblioteca estándar de C++ que se usará para esta configuración. | **Standard C++ Library para GNU compartida**<br/><br/>**Standard C++ Library para GNU estática (-static)** |

::: moniker-end
