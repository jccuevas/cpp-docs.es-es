---
title: Diseñar un cuadro de diálogo (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
- dialog boxes [C++], size
- dialog boxes [C++], positioning
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
ms.openlocfilehash: 4a879f6bb1cdcd4b4897e510fb21d04500dfd3f2
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742692"
---
# <a name="designing-a-dialog-box-c"></a>Diseñar un cuadro de diálogo (C++)

La ubicación y el tamaño de un cuadro de diálogo de C++ y la ubicación y tamaño de los controles dentro de ella, se miden en unidades de cuadro de diálogo. Los valores de los controles individuales y el cuadro de diálogo aparecen en la esquina inferior derecha de la barra cuando seleccionarlas de estado de Visual Studio.

Al diseñar un cuadro de diálogo, también puede simular y probar su comportamiento en tiempo de ejecución sin compilar el programa. En este modo, se puede:

- Escribir texto, seleccionar opciones de listas de cuadro combinado, activar y desactivar opciones y elegir comandos.

- Probar el orden de tabulación.

- Probar la agrupación de controles, como botones de radio y casillas.

- Probar los métodos abreviados de teclado para los controles del cuadro de diálogo.

   > [!NOTE]
   > Las conexiones con el código del cuadro de diálogo realizadas mediante asistentes no se incluyen en la simulación.

Cuando se prueba un cuadro de diálogo, normalmente se muestra en una ubicación relativa a la ventana principal del programa. Si ha configurado el cuadro de diálogo **Absolute Align** propiedad **True**, muestra el cuadro de diálogo en una posición relativa a la esquina superior izquierda de la pantalla.

Para obtener información acerca de cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index).

## <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>Para especificar la ubicación y tamaño de un cuadro de diálogo

Hay tres propiedades que se pueden establecer en el [ventana propiedades](/visualstudio/ide/reference/properties-window) para especificar dónde aparecerá un cuadro de diálogo en la pantalla. El **Center** propiedad es un valor booleano; si establece el valor en **True**, el cuadro de diálogo siempre aparecerá en el centro de la pantalla. Si se establece en **False**, a continuación, puede establecer el **XPos** y **YPos** las propiedades para definir explícitamente donde aparecerá el cuadro de diálogo en la pantalla. Las propiedades de posición son valores de desplazamiento de la esquina superior izquierda del área de visualización, que se define como `{X=0, Y=0}`. La posición también se basa en el **Absolute Align** propiedad: si **True**, las coordenadas son relativas a la pantalla; si **False**, las coordenadas son en relación con el cuadro de diálogo ventana del propietario.

## <a name="to-test-a-dialog-box"></a>Para probar un cuadro de diálogo

1. Cuando el **diálogo** editor es la ventana activa, en la barra de menús, elija **formato** > **Probar cuadro de diálogo**.

1. Para finalizar la simulación, presione **Esc**, o elija simplemente el **cerrar** botón en el cuadro de diálogo que está probando.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
[Editor de cuadros de diálogo](../windows/dialog-editor.md)<br/>
[Mostrar u ocultar la barra de herramientas del Editor de cuadros de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)