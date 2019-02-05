---
title: Ajustar el tamaño de controles
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.combo
helpviewer_keywords:
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
- Make Same Size command
- combo boxes, sizing
- list controls [C++], scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars [C++], displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars [C++], width
ms.assetid: 14ccba02-7171-463a-a121-7018cf1e2e5a
ms.openlocfilehash: a6381dcf1aeb9f73ac3b656229d9332df2a6a519
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742718"
---
# <a name="sizing-controls"></a>Ajustar el tamaño de controles

Use los controladores de tamaño para cambiar el tamaño de un control. Cuando el puntero se coloca en un controlador de tamaño, cambia la forma para indicar las instrucciones que aparecen en el que se puede cambiar el tamaño del control. Controladores de tamaño activos son sólidos; Si un controlador de tamaño está vacío, el control no puede cambiarse a lo largo de ese eje.

También puede cambiar el tamaño de un control ajustando el control a las guías o los márgenes o moviendo un control ajustado y guía fuera de otra.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-size-an-individual-control"></a>Para cambiar el tamaño de un control individual

1. Seleccione el control.

1. Arrastre los controladores de tamaño para cambiar el tamaño del control:

   - Controladores de tamaño en la parte superior y cambiar el tamaño horizontal o vertical.

   - Controladores de tamaño en las esquinas cambiar el tamaño horizontal y vertical.

   > [!TIP]
   > Puede cambiar el tamaño la unidad de control de un cuadro de diálogo (DLU) a la vez, mantenga presionada la **MAYÚS** clave y usar el **flecha derecha** y **flecha abajo** claves.

## <a name="to-automatically-size-a-control-to-fit-the-text-within-it"></a>Para cambiar automáticamente el tamaño de un control para ajustar el texto dentro de él

Elija **tamaño al contenido** desde el **formato** menú.

\- o -

Haga clic en el control y elija **tamaño al contenido** en el menú contextual.

## <a name="to-make-controls-the-same-width-height-or-size"></a>Para hacer que controla el mismo ancho, alto o tamaño

Puede cambiar el tamaño de un grupo de controles en función del tamaño del control principal.

1. [Seleccione los controles](../windows/selecting-multiple-controls.md) que desea cambiar el tamaño.

   El control seleccionado en primer lugar de la serie es el control dominante. El tamaño final de los controles en el grupo depende del tamaño del control principal. Para obtener más información sobre cómo seleccionar el control dominante, vea [especificar el Control dominante](../windows/specifying-the-dominant-control.md).

1. Desde el **formato** menú, elija **Igualar tamaño**, a continuación, elija uno de los siguientes comandos:

   - **Ambos**

   - **Height**

   - **Width**

## <a name="to-set-the-size-of-the-combo-box-and-its-drop-down-list"></a>Para establecer el tamaño combinado de la casilla y su lista desplegable

Puede ajustar el tamaño de un cuadro combinado cuando se agrega al cuadro de diálogo. También puede especificar el tamaño del cuadro de lista desplegable. Para obtener más información, consulte [agregar valores a un Control de cuadro combinado](../windows/adding-values-to-a-combo-box-control.md).

### <a name="to-size-a-combo-box"></a>Para cambiar el tamaño de un cuadro combinado

1. Seleccione el control de cuadro combinado en el cuadro de diálogo.

   Inicialmente, solo los controladores de tamaño de la derecha e izquierda están activos.

1. Use los controladores de tamaño para establecer el ancho del cuadro combinado.

También puede establecer el tamaño vertical de la parte desplegable del cuadro combinado.

### <a name="to-set-the-size-of-the-combo-box-drop-down-list"></a>Para establecer el tamaño combinado de la lista desplegable del cuadro

1. Seleccione el botón de flecha de lista desplegable situado a la derecha del cuadro combinado.

   ![Flecha de un cuadro combinado en un proyecto MFC](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   El contorno del control cambia para mostrar el tamaño del cuadro combinado con el área de la lista desplegable extendido.

1. Use el controlador de tamaño inferior para cambiar el tamaño inicial del área de la lista desplegable.

   ![Cuadro combinado&#45;ajuste de tamaño de cuadro en un proyecto MFC](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. Seleccione la flecha desplegable para cerrar la parte de la lista desplegable del cuadro combinado.

## <a name="to-set-the-width-of-a-horizontal-scroll-bar-and-make-it-appear"></a>Para establecer el ancho de una barra de desplazamiento horizontal y hacer que aparezca

Cuando se agrega un cuadro de lista con una barra de desplazamiento horizontal para un cuadro de diálogo mediante clases de MFC, la barra de desplazamiento no aparecerá automáticamente en la aplicación.

Establecer un ancho máximo para el elemento más amplio mediante una llamada a [CListBox:: SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) en el código.

   Establecer este valor, la barra de desplazamiento no aparecerá, incluso cuando los elementos del cuadro de lista son más amplio que el cuadro.
> [!NOTE]
> La barra de desplazamiento horizontal requiere MFC.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
[Controles](../mfc/controls-mfc.md)
