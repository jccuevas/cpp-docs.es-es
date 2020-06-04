---
title: Referencia de ConnectionManager
ms.date: 01/17/2020
f1_keywords:
- ConnectionManager
helpviewer_keywords:
- ConnectionManager program
ms.openlocfilehash: 1c6236cedba88714e9918dd2c096b5e78d2f08ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "77258038"
---
# <a name="connectionmanager-reference"></a>Referencia de ConnectionManager

::: moniker range="<=vs-2017"

ConnectionManager.exe está disponible en Visual Studio 2019, versión 16.5 y posteriores.

::: moniker-end

::: moniker range="vs-2019"

ConnectionManager.exe es una utilidad de línea de comandos para administrar conexiones de desarrollo remotas fuera de Visual Studio. Resulta útil para tareas como el aprovisionamiento de una nueva máquina de desarrollo. O bien, úsela para configurar Visual Studio para la integración continua. Puede usarla en una ventana Símbolo del sistema para desarrolladores. Para obtener más información sobre la ventana Símbolo del sistema para desarrolladores, consulte [Uso del conjunto de herramientas de Microsoft C++ desde la línea de comandos](../build/building-on-the-command-line.md).

ConnectionManager.exe está disponible en Visual Studio 2019, versión 16.5 y posteriores. Formar parte de la carga de trabajo **Desarrollo de Linux con C++** del Instalador de Visual Studio. También se instala automáticamente cuando se elige el componente **Administrador de conexiones de** en el instalador. Se instala en *%VCIDEInstallDir%\\Linux\\bin\\ConnectionManagerExe\\ConnectionManager.exe*.

La funcionalidad de ConnectionManager.exe también está disponible en Visual Studio. Para administrar las conexiones de desarrollo remotas en el IDE, en la barra de menús elija **Herramientas** > **Opciones** para abrir el cuadro de diálogo Opciones. En el cuadro de diálogo Opciones, seleccione **Multiplataforma** > **Administrador de conexiones**.

## <a name="syntax"></a>Sintaxis

> **ConnectionManager.exe** *command* \[*arguments*] \[*options*]

### <a name="commands-and-arguments"></a>Comandos y argumentos

- **add** *user\@host* \[ **--port** *port*] \[ **--password** *password*] \[ **--privatekey** *privatekey_file*]

  Autentica y agrega una nueva conexión. De forma predeterminada, usa el puerto 22 y la autenticación de contraseña. (Se le pedirá que escriba una contraseña). Use ambas opciones **--password** y **--privatekey** para especificar una contraseña para una clave privada.

- **remove** \[*connection_id* \| *user\@host* \[ **--port** *port*]]

  Quita una conexión. Si no se especifica ningún argumento, se le pedirá que especifique la conexión que desea quitar.

- **remove-all**

  Quita todas las conexiones almacenadas.

- **lista**

  Muestra información e identificadores de todas las conexiones almacenadas.

- **help**

  Muestra una pantalla de ayuda.

- **version**

  Muestra información de la versión.

### <a name="options"></a>Opciones

- **-q**, **--quiet**

  Impide la salida a `stdout` o `stderr`.

- **--no-prompt**

  Genera un error en lugar de un mensaje, cuando corresponde.

- **--no-verify**

  Agregue o modifique una conexión sin autenticación.

- **--file** *filename*

  Lea la información de conexión del *nombre de archivo* proporcionado.

- **--no-telemetry**

  Deshabilite el envío de datos de uso a Microsoft. Los datos de uso se recopilan y se devuelven a Microsoft a menos que se pase la marca **--no-telemetry**.  

- **-n**, **--dry-run**

  Realiza un simulacro del comando.

- **-p**

  Igual que **--password**.

- **-i**

  Igual que **--privatekey**.

## <a name="examples"></a>Ejemplos

Este comando agrega una conexión para un usuario denominado "user" en localhost. La conexión usa un archivo de clave para la autenticación, que se encuentra en *%USERPROFILE%\.ssh\id_rsa*.

```cmd
ConnectionManager.exe add user@127.0.0.1 --privatekey "%USERPROFILE%\.ssh\id_rsa"
```

Este comando quita la conexión con el identificador 1975957870 de la lista de conexiones.

```cmd
ConnectionManager.exe remove 1975957870
```

## <a name="see-also"></a>Vea también

[Conexión al sistema Linux de destino en Visual Studio](connect-to-your-remote-linux-computer.md)

::: moniker-end
