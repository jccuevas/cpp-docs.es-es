---
title: Implementar, ejecutar y depurar el proyecto de Linux | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: dff1e9e03911f65dfcffcd078e0739224f73f4aa
ms.openlocfilehash: db868094a8f10ad05ed6f95bf8a4c8a29a2c941e
ms.lasthandoff: 02/24/2017

---

# <a name="deploy-run-and-debug-your-project"></a>Implementar, ejecutar y depurar el proyecto

Ahora que se ha creado el proyecto, tendrá que conectarse al equipo Linux, que es donde se compila, ejecuta y depura el código.

1. Establezca la arquitectura de destino remota mediante la lista desplegable estándar de Visual Studio, como se muestra: ![Arquitectura remota](media/architecture.png)

Hay varias formas de interactuar con el proyecto de Linux y de depurarlo.

* Las características tradicionales de Visual Studio, como los puntos de interrupción, las ventanas de inspección y pasar el mouse por encima de una variable, funcionarán según lo esperado, así que puede depurar como lo haría normalmente.
* Se puede abrir una ventana de consola de Linux especial con el elemento de menú **Depurar > Consola Linux**.

  ![Menú Consola Linux](media/consolemenu.png)

  Esta consola muestra cualquier salida de consola del equipo de destino y acepta entradas y las envía al equipo de destino.

  ![Ventana Consola Linux](media/consolewindow.png)

* Se pueden pasar argumentos de línea de comandos al ejecutable mediante el elemento **Argumentos de programa** de la página de propiedades **Depuración** del proyecto.
  
  ![Argumentos de programa](media/settings_programarguments.png)

* GDB se usa para depurar aplicaciones que se ejecutan en Linux.  Pero se puede ejecutar en dos modos diferentes, que pueden seleccionarse desde la opción **Modo de depuración** de la página de propiedades **Depuración** del proyecto:

  ![Opciones de GDB](media/settings_debugger.png)

  | Selección | Descripción
  | --------- | ---
  | gdbserver | GDB se ejecuta localmente, con lo que se conecta a gdbserver, que se ejecuta en el sistema remoto.  Tenga en cuenta que este es el único modo que admite la ventana Consola Linux. 
  | gdb       | el depurador de Visual Studio controla GDB en el sistema remoto, que es más compatible si la versión local de GDB no es compatible con la versión instalada en el equipo de destino

* Se pueden pasar opciones concretas del depurador a GDB mediante la entrada **Comandos adicionales del depurador**.  Por ejemplo, es posible que quiera pasar por alto las señales SIGILL (instrucciones no válidas).  Puede usar el comando **handle** para lograrlo.  al agregar lo siguiente a la entrada **Comandos adicionales del depurador** como se muestra arriba:

  ```handle SIGILL nostop noprint```

