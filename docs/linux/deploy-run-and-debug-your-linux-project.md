---
title: Implementar, ejecutar y depurar el proyecto de Linux | Microsoft Docs
ms.custom: 
ms.date: 11/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 237b6f3dbca8d529362a545f67ee0db4f9770d8d
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2017
---
# <a name="deploy-run-and-debug-your-linux-project"></a>Implementar, ejecutar y depurar el proyecto de Linux

Una vez que ha creado un proyecto de Linux y se ha conectado a él mediante el [Administrador de conexiones de Linux](../linux/connect-to-your-remote-linux-computer.md), puede ejecutar y depurar el proyecto. Compile, ejecute y depure el código en el destino remoto.

Hay varias formas de interactuar con el proyecto de Linux y de depurarlo.

* Depure con las características tradicionales de Visual Studio, como son los puntos de interrupción, las ventanas Inspección y mantener el mouse sobre una variable. Con estos métodos, puede depurar como lo haría normalmente para otros tipos de proyecto.
* Vea la salida desde el equipo de destino en una ventana especial de la consola de Linux. También puede usar la consola para enviar la entrada al equipo de destino.

## <a name="debug-your-linux-project"></a>Depurar el proyecto de Linux

1. Seleccione el modo de depuración en la página de propiedades **Depuración**.

    GDB se usa para depurar aplicaciones que se ejecutan en Linux.  Pero se puede ejecutar en dos modos diferentes, que pueden seleccionarse desde la opción **Modo de depuración** de la página de propiedades **Depuración** del proyecto:

    ![Opciones de GDB](media/settings_debugger.png)

    - En modo **gdbserver**, GDB se ejecuta localmente, con lo que se conecta a gdbserver, que se ejecuta en el sistema remoto.  Tenga en cuenta que este es el único modo que admite la ventana Consola Linux.

    - En modo **gdb**, el depurador de Visual Studio controla GDB en el sistema remoto, que es más compatible si la versión local de GDB no es compatible con la versión instalada en el equipo de destino. |

    > [!NOTE] 
    > Si no es posible alcanzar puntos de interrupción en el modo de depuración gdbserver, pruebe el modo gdb. En primer lugar, gdb debe [instalarse](../linux/download-install-and-setup-the-linux-development-workload.md) en el destino remoto.

2. Seleccione el destino remoto a través de la barra de herramientas estándar **Depurar** de Visual Studio.

    Cuando el destino remoto está disponible, verá que aparece por nombre o dirección IP.

    ![Destino remoto](media/remote_target.png)

    Si aún no ha establecido conexión con el destino remoto, se le indicará que use el [administrador de conexiones de Linux](../linux/connect-to-your-remote-linux-computer.md) para conectarse al destino remoto.

    ![Arquitectura remota](media/architecture.png)

3. Establezca un punto de interrupción; para ello, haga clic en el margen interno izquierdo de una parte del código que sabe que se ejecutará.

    Un punto rojo aparece en la línea de código en la que estableció el punto de interrupción.

4. Presione **F5** (o **Depurar > Iniciar depuración**) para iniciar la depuración.

    Al iniciar la depuración, la aplicación se compila en el destino remoto antes de comenzar. Los posibles errores de compilación aparecerán en la ventana **Lista de errores**.

    Si no hay ningún error, la aplicación se iniciará y el depurador se detendrá en el punto de interrupción.

    ![Llegar a un punto de interrupción](media/hit_breakpoint.png)  

    Ahora, puede interactuar con la aplicación en su estado actual, ver variables y recorrer el código mediante las teclas de comando como **F10** o **F11**.

4. Si quiere usar la consola de Linux para interactuar con la aplicación, seleccione **Depurar > Consola de Linux**.

  ![Menú Consola Linux](media/consolemenu.png)

  Esta consola muestra cualquier salida de consola del equipo de destino y acepta entradas y las envía al equipo de destino.

  ![Ventana Consola Linux](media/consolewindow.png)

## <a name="configure-other-debugging-options"></a>Configurar otras opciones de depuración

* Se pueden pasar argumentos de línea de comandos al ejecutable mediante el elemento **Argumentos de programa** de la página de propiedades **Depuración** del proyecto.
  
  ![Argumentos de programa](media/settings_programarguments.png)

* Se pueden pasar opciones concretas del depurador a GDB mediante la entrada **Comandos adicionales del depurador**.  Por ejemplo, es posible que quiera pasar por alto las señales SIGILL (instrucciones no válidas).  Puede usar el comando **handle** para lograrlo.  al agregar lo siguiente a la entrada **Comandos adicionales del depurador** como se muestra arriba:

  ```handle SIGILL nostop noprint```

## <a name="see-also"></a>Vea también
[Propiedades de depuración de C++ (C++ para Linux)](../linux/prop-pages/debugging-linux.md).
