---
title: Probar un cuadro de diálogo (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
ms.openlocfilehash: 101a2b556b2593953bfa6482f96d5b1aadc38d1c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625078"
---
# <a name="testing-a-dialog-box-c"></a>Probar un cuadro de diálogo (C++)

Cuando se está diseñando un cuadro de diálogo, se puede simular y probar su comportamiento en tiempo de ejecución sin compilar el programa. En este modo, se puede:

- Escribir texto, seleccionar opciones de listas de cuadro combinado, activar y desactivar opciones y elegir comandos.

- Probar el orden de tabulación.

- Probar la agrupación de controles, como botones de radio y casillas.

- Probar los métodos abreviados de teclado para los controles del cuadro de diálogo.

   > [!NOTE]
   > Las conexiones con el código del cuadro de diálogo realizadas mediante asistentes no se incluyen en la simulación.

Cuando se prueba un cuadro de diálogo, normalmente se muestra en una ubicación relativa a la ventana principal del programa. Si ha configurado el cuadro de diálogo **Absolute Align** propiedad **True**, muestra el cuadro de diálogo en una posición relativa a la esquina superior izquierda de la pantalla.

### <a name="to-test-a-dialog-box"></a>Para probar un cuadro de diálogo

1. Cuando el **diálogo** editor es la ventana activa, en la barra de menús, elija **formato** > **Probar cuadro de diálogo**.

2. Para finalizar la simulación, presione **Esc**, o elija simplemente el **cerrar** botón en el cuadro de diálogo que se está probando.

Para obtener información acerca de cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
[Editor de cuadros de diálogo](../windows/dialog-editor.md)<br/>
[Mostrar u ocultar la barra de herramientas del Editor de cuadros de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)