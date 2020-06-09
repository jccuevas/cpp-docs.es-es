---
title: 'Controles ActiveX MFC: Pintar un control ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], painting
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
ms.openlocfilehash: a01a66402471b295a6e57af8af265c50685b4a1f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618222"
---
# <a name="mfc-activex-controls-painting-an-activex-control"></a>Controles ActiveX MFC: Pintar un control ActiveX

En este artículo se describe el proceso de dibujo de controles ActiveX y cómo se puede modificar el código de dibujo para optimizar el proceso. (Vea [optimizar el dibujo](optimizing-control-drawing.md) de controles para conocer las técnicas de optimización del dibujo al no tener controles restaurar individualmente los objetos GDI seleccionados anteriormente. Una vez que se han dibujado todos los controles, el contenedor puede restaurar automáticamente los objetos originales).

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información sobre las tecnologías modernas que reemplazan a ActiveX, vea [controles ActiveX](activex-controls.md).

Los ejemplos de este artículo son de un control creado por el Asistente para controles ActiveX MFC con la configuración predeterminada. Para obtener más información sobre cómo crear una aplicación de control de esqueleto mediante el Asistente para controles ActiveX MFC, vea el artículo [Asistente para controles ActiveX MFC](reference/mfc-activex-control-wizard.md).

Se tratan los temas siguientes:

- [Proceso general para dibujar un control y el código creado por el Asistente para controles ActiveX para permitir el dibujo](#_core_the_painting_process_of_an_activex_control)

- [Cómo optimizar el proceso de dibujo](#_core_optimizing_your_paint_code)

- [Cómo pintar el control mediante metaarchivos](#_core_painting_your_control_using_metafiles)

## <a name="the-painting-process-of-an-activex-control"></a><a name="_core_the_painting_process_of_an_activex_control"></a>El proceso de dibujo de un control ActiveX

Cuando los controles ActiveX se muestran o se vuelven a dibujar inicialmente, siguen un proceso de dibujo similar a otras aplicaciones desarrolladas con MFC, con una diferencia importante: los controles ActiveX pueden estar en un estado activo o inactivo.

Un control activo se representa en un contenedor de controles ActiveX mediante una ventana secundaria. Al igual que otras ventanas, es responsable de dibujarse cuando se recibe un mensaje de WM_PAINT. La clase base del control, [COleControl](reference/colecontrol-class.md), controla este mensaje en su `OnPaint` función. Esta implementación predeterminada llama a la `OnDraw` función del control.

Un control inactivo se dibuja de manera diferente. Cuando el control está inactivo, su ventana es invisible o no existe, por lo que no puede recibir un mensaje de dibujo. En su lugar, el contenedor de control llama directamente a la `OnDraw` función del control. Esto difiere del proceso de dibujo de un control activo en que `OnPaint` nunca se llama a la función miembro.

Tal y como se describe en los párrafos anteriores, el modo en que se actualiza un control ActiveX depende del estado del control. Sin embargo, dado que el marco de trabajo llama a la `OnDraw` función miembro en ambos casos, se agrega la mayoría del código de dibujo en esta función miembro.

La `OnDraw` función miembro controla el dibujo del control. Cuando un control está inactivo, el contenedor de control llama a `OnDraw` , pasando el contexto de dispositivo del contenedor de controles y las coordenadas del área rectangular ocupada por el control.

El rectángulo pasado por el marco de trabajo a la `OnDraw` función miembro contiene el área ocupada por el control. Si el control está activo, la esquina superior izquierda es (0,0) y el contexto de dispositivo que se pasa es para la ventana secundaria que contiene el control. Si el control está inactivo, la coordenada superior izquierda no es necesariamente (0,0) y el contexto de dispositivo pasado es para el contenedor de controles que contiene el control.

> [!NOTE]
> Es importante que las modificaciones realizadas en no `OnDraw` dependan del punto superior izquierdo del rectángulo que sea igual a (0,0) y que dibuje solo dentro del rectángulo pasado a `OnDraw` . Pueden producirse resultados inesperados si dibuja más allá del área del rectángulo.

Implementación predeterminada proporcionada por el Asistente para controles ActiveX MFC en el archivo de implementación del control (. CPP), que se muestra a continuación, pinta el rectángulo con un pincel blanco y rellena la elipse con el color de fondo actual.

[!code-cpp[NVC_MFC_AxUI#1](codesnippet/cpp/mfc-activex-controls-painting-an-activex-control_1.cpp)]

> [!NOTE]
> Al pintar un control, no debe realizar suposiciones sobre el estado del contexto de dispositivo que se pasa como parámetro de *PDC* a la `OnDraw` función. En ocasiones, la aplicación contenedora suministra el contexto del dispositivo y no se inicializará necesariamente con el estado predeterminado. En concreto, seleccione explícitamente los lápices, los pinceles, los colores, las fuentes y otros recursos de los que depende el código de dibujo.

## <a name="optimizing-your-paint-code"></a><a name="_core_optimizing_your_paint_code"></a>Optimizar el código de dibujo

Después de que el control se dibuje correctamente, el siguiente paso es optimizar la `OnDraw` función.

La implementación predeterminada del dibujo de controles ActiveX pinta todo el área de control. Esto es suficiente para los controles simples, pero en muchos casos volver a dibujar el control sería más rápido si solo se redibujó la parte que necesitaba la actualización, en lugar de todo el control.

La `OnDraw` función proporciona un método sencillo de optimización pasando *rcInvalid*, el área rectangular del control que necesita volver a dibujar. Use esta área, normalmente más pequeña que el área de control completa, para acelerar el proceso de dibujo.

## <a name="painting-your-control-using-metafiles"></a><a name="_core_painting_your_control_using_metafiles"></a>Dibujar el control mediante metaarchivos

En la mayoría de los casos, el parámetro *PDC* de la `OnDraw` función apunta a un contexto de dispositivo de pantalla (DC). Sin embargo, cuando se imprimen imágenes del control o durante una sesión de vista previa de impresión, el controlador de dominio recibido para su representación es un tipo especial denominado "metarchivo del DC". A diferencia de un controlador de dominio de pantalla, que controla inmediatamente las solicitudes que se le envían, un DC de metarchivo almacena las solicitudes que se van a reproducir en otro momento. Algunas aplicaciones contenedoras también pueden optar por representar la imagen de control mediante un DC de metarchivo en el modo de diseño.

El contenedor puede realizar solicitudes de dibujo de metarchivos mediante dos funciones de interfaz: `IViewObject::Draw` (también se puede llamar a esta función para dibujar sin metarchivos) y `IDataObject::GetData` . Cuando se pasa un DC de metarchivo como uno de los parámetros, el marco de trabajo de MFC realiza una llamada a [COleControl:: OnDrawMetafile](reference/colecontrol-class.md#ondrawmetafile). Dado que se trata de una función miembro virtual, invalide esta función en la clase del control para realizar cualquier procesamiento especial. El comportamiento predeterminado llama a `COleControl::OnDraw` .

Para asegurarse de que el control se puede dibujar en contextos de dispositivo de pantalla y de metarchivo, solo debe usar funciones miembro que se admitan en una pantalla y un DC de metarchivo. Tenga en cuenta que es posible que el sistema de coordenadas no se mida en píxeles.

Dado que la implementación predeterminada de `OnDrawMetafile` llama a la `OnDraw` función del control, use solo funciones miembro adecuadas para un metarchivo y un contexto de dispositivo de pantalla, a menos que invalide `OnDrawMetafile` . A continuación se enumera el subconjunto de `CDC` funciones miembro que se pueden usar en un metarchivo y en un contexto de dispositivo de pantalla. Para obtener más información sobre estas funciones, vea clase [CDC](reference/cdc-class.md) en la *referencia de MFC*.

|Arc|BibBlt|Chord|
|---------|------------|-----------|
|`Ellipse`|`Escape`|`ExcludeClipRect`|
|`ExtTextOut`|`FloodFill`|`IntersectClipRect`|
|`LineTo`|`MoveTo`|`OffsetClipRgn`|
|`OffsetViewportOrg`|`OffsetWindowOrg`|`PatBlt`|
|`Pie`|`Polygon`|`Polyline`|
|`PolyPolygon`|`RealizePalette`|`RestoreDC`|
|`RoundRect`|`SaveDC`|`ScaleViewportExt`|
|`ScaleWindowExt`|`SelectClipRgn`|`SelectObject`|
|`SelectPalette`|`SetBkColor`|`SetBkMode`|
|`SetMapMode`|`SetMapperFlags`|`SetPixel`|
|`SetPolyFillMode`|`SetROP2`|`SetStretchBltMode`|
|`SetTextColor`|`SetTextJustification`|`SetViewportExt`|
|`SetViewportOrg`|`SetWindowExt`|`SetWindowORg`|
|`StretchBlt`|`TextOut`||

Además de `CDC` las funciones miembro, hay otras funciones que son compatibles en un controlador de dominio de metarchivo. Entre estos se incluyen [CPalette:: AnimatePalette](reference/cpalette-class.md#animatepalette), [Cfont (:: CreateFontIndirect](reference/cfont-class.md#createfontindirect)y tres funciones miembro de `CBrush` : [CreateBrushIndirect](reference/cbrush-class.md#createbrushindirect), [CreateDIBPatternBrush](reference/cbrush-class.md#createdibpatternbrush)y [CreatePatternBrush](reference/cbrush-class.md#createpatternbrush).

Las funciones que no se registran en un metarchivo son: [DrawFocusRect](reference/cdc-class.md#drawfocusrect), [DrawIcon](reference/cdc-class.md#drawicon), [DrawText](reference/cdc-class.md#drawtext), [ExcludeUpdateRgn](reference/cdc-class.md#excludeupdatergn), [FillRect](reference/cdc-class.md#fillrect), [FrameRect](reference/cdc-class.md#framerect), [GrayString](reference/cdc-class.md#graystring), [InvertRect](reference/cdc-class.md#invertrect), [ScrollDC](reference/cdc-class.md#scrolldc)y [TabbedTextOut](reference/cdc-class.md#tabbedtextout). Dado que un DC de metarchivo no está asociado realmente a un dispositivo, no puede usar SetDIBits, GetDIBits y CreateDIBitmap con un DC de metarchivo. Puede usar SetDIBitsToDevice y StretchDIBits con un DC de metarchivo como destino. [CreateCompatibleDC](reference/cdc-class.md#createcompatibledc), [CreateCompatibleBitmap](reference/cbitmap-class.md#createcompatiblebitmap)y [CreateDiscardableBitmap](reference/cbitmap-class.md#creatediscardablebitmap) no son significativos con un DC de metarchivo.

Otro punto a tener en cuenta al usar un DC de metarchivo es que el sistema de coordenadas no se puede medir en píxeles. Por esta razón, todo el código de dibujo debe ajustarse para ajustarse al rectángulo pasado a `OnDraw` en el parámetro *rcBounds* . Esto evita el dibujo accidental fuera del control porque *rcBounds* representa el tamaño de la ventana del control.

Después de haber implementado la representación de metarchivos para el control, utilice el contenedor de prueba para probar el metarchivo. Consulte [Probar propiedades y eventos con un contenedor de prueba](testing-properties-and-events-with-test-container.md) para obtener información acerca de cómo acceder al contenedor de prueba.

#### <a name="to-test-the-controls-metafile-using-test-container"></a>Para probar el metarchivo del control mediante Test Container

1. En el menú **edición** del contenedor de pruebas, haga clic en **Insertar nuevo control**.

1. En el cuadro **Insertar nuevo control** , seleccione el control y haga clic en **Aceptar**.

   El control aparecerá en el contenedor de prueba.

1. En el menú **control** , haga clic en **dibujar metarchivo**.

   Aparece una ventana independiente en la que se muestra el metarchivo. Puede cambiar el tamaño de esta ventana para ver cómo afecta el escalado al metarchivo del control. Puede cerrar esta ventana en cualquier momento.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)
