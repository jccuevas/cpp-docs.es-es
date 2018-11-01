---
title: Probar el Control DHTML ATL modificado
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, testing
- testing controls
- DHTML controls, testing
ms.assetid: 42316118-9433-410f-9d8a-0efcc1eff824
ms.openlocfilehash: f0fec3e2430fd5956e3cc48cd64532efee30926d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501678"
---
# <a name="testing-the-modified-atl-dhtml-control"></a>Probar el Control DHTML ATL modificado

Pruebe el nuevo control para ver cómo funciona ahora.

## <a name="to-build-and-test-the-modified-control"></a>Para compilar y probar el control modificado

1. Recompile el proyecto y ábralo en **Test Container**. Consulte [Probar propiedades y eventos con un contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md) para obtener información sobre cómo acceder a **Test Container**.

   El tamaño del control para mostrar todos los botones que agregó.

1. Examine los dos botones que insertó modificando el código HTML. Cada botón posee la etiqueta que identificó en [modificar el Control DHTML ATL](../atl/modifying-the-atl-dhtml-control.md): **actualizar** y **HelloHTML**.

1. Probar los dos nuevos botones para ver cómo funcionan.

Ahora los métodos que no forman parte de la interfaz de usuario de prueba.

1. Resalte el control, por lo que se activa el borde.

1. En el **Control** menú, haga clic en **invocar métodos**.

Los métodos en la lista con la etiqueta **nombre del método** son los métodos que puede llamar el contenedor: `MethodInvoked` y `GoToURL`. Todos los demás métodos se controlan mediante la interfaz de usuario.

1. Seleccione un método para invocar y haga clic en `Invoke` para mostrar el cuadro de mensaje del método o vaya a www.microsoft.com.

1. En el **invocar métodos** cuadro de diálogo, haga clic en **cerrar**.

Para obtener más información acerca de los distintos elementos y los archivos que componen un control DHTML ATL, vea [que identifican los elementos del proyecto de Control DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con controles DHTML](../atl/atl-support-for-dhtml-controls.md)
