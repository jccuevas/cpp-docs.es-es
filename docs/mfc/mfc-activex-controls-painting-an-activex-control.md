---
title: 'Controles ActiveX MFC: Pintar un control ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], painting
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
ms.openlocfilehash: fd98af90e86b6b98a856e633e50c5bf266cc466a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364579"
---
# <a name="mfc-activex-controls-painting-an-activex-control"></a>Controles ActiveX MFC: Pintar un control ActiveX

En este artículo se describe el proceso de pintura de control ActiveX y cómo puede modificar el código de pintura para optimizar el proceso. (Consulte [Optimización del dibujo](../mfc/optimizing-control-drawing.md) de control para obtener técnicas sobre cómo optimizar el dibujo al no tener controles que restaure individualmente los objetos GDI seleccionados anteriormente. Una vez dibujados todos los controles, el contenedor puede restaurar automáticamente los objetos originales.)

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe utilizarse para el nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que reemplazan a ActiveX, vea [Controles ActiveX](activex-controls.md).

Los ejemplos de este artículo proceden de un control creado por el Asistente para controles ActiveX de MFC con la configuración predeterminada. Para obtener más información sobre cómo crear una aplicación de control de esqueleto mediante el Asistente para controles ActiveX de MFC, vea el artículo [Asistente para controles ActiveX](../mfc/reference/mfc-activex-control-wizard.md)de MFC .

Se tratan los siguientes temas:

- [El proceso general para pintar un control y el código creado por el Asistente de control ActiveX para admitir la pintura](#_core_the_painting_process_of_an_activex_control)

- [Cómo optimizar el proceso de pintura](#_core_optimizing_your_paint_code)

- [Cómo pintar el control usando metarchivos](#_core_painting_your_control_using_metafiles)

## <a name="the-painting-process-of-an-activex-control"></a><a name="_core_the_painting_process_of_an_activex_control"></a>El proceso de pintura de un control ActiveX

Cuando los controles ActiveX se muestran inicialmente o se vuelven a dibujar, siguen un proceso de pintura similar a otras aplicaciones desarrolladas con MFC, con una distinción importante: los controles ActiveX pueden estar en un estado activo o inactivo.

Un control activo se representa en un contenedor de controles ActiveX mediante una ventana secundaria. Al igual que otras ventanas, es responsable de pintarse a sí mismo cuando se recibe un mensaje WM_PAINT. La clase base del control, [COleControl](../mfc/reference/colecontrol-class.md), `OnPaint` controla este mensaje en su función. Esta implementación `OnDraw` predeterminada llama a la función del control.

Un control inactivo se pinta de forma diferente. Cuando el control está inactivo, su ventana es invisible o inexistente, por lo que no puede recibir un mensaje de pintura. En su lugar, el `OnDraw` contenedor de control llama directamente a la función del control. Esto difiere del proceso de pintura de `OnPaint` un control activo en que nunca se llama a la función miembro.

Como se describe en los párrafos anteriores, cómo se actualiza un control ActiveX depende del estado del control. Sin embargo, dado `OnDraw` que el marco de trabajo llama a la función miembro en ambos casos, se agrega la mayoría del código de pintura en esta función miembro.

La `OnDraw` función miembro controla la pintura de control. Cuando un control está inactivo, `OnDraw`el contenedor de control llama a , pasando el contexto del dispositivo del contenedor de control y las coordenadas del área rectangular ocupada por el control.

El rectángulo pasado por `OnDraw` el marco de trabajo a la función miembro contiene el área ocupada por el control. Si el control está activo, la esquina superior izquierda es (0, 0) y el contexto del dispositivo pasado es para la ventana secundaria que contiene el control. Si el control está inactivo, la coordenada superior izquierda no es necesariamente (0, 0) y el contexto del dispositivo pasado es para el contenedor de control que contiene el control.

> [!NOTE]
> Es importante que las `OnDraw` modificaciones no dependan de que el punto superior izquierdo del rectángulo sea igual a `OnDraw`(0, 0) y que dibuje solo dentro del rectángulo pasado a . Pueden producirse resultados inesperados si dibuja más allá del área del rectángulo.

La implementación predeterminada proporcionada por el Asistente para controles ActiveX de MFC en el archivo de implementación del control (. CPP), que se muestra a continuación, pinta el rectángulo con un pincel blanco y rellena la elipse con el color de fondo actual.

[!code-cpp[NVC_MFC_AxUI#1](../mfc/codesnippet/cpp/mfc-activex-controls-painting-an-activex-control_1.cpp)]

> [!NOTE]
> Al pintar un control, no debe realizar suposiciones sobre el estado *pdc* del contexto `OnDraw` del dispositivo que se pasa como parámetro pdc a la función. Ocasionalmente, la aplicación contenedora proporciona el contexto del dispositivo y no se inicializará necesariamente en el estado predeterminado. En particular, seleccione explícitamente los rotuladores, pinceles, colores, fuentes y otros recursos de los que depende el código de dibujo.

## <a name="optimizing-your-paint-code"></a><a name="_core_optimizing_your_paint_code"></a>Optimización del código de pintura

Después de que el control se está pintando correctamente, el siguiente paso es optimizar la `OnDraw` función.

La implementación predeterminada de la pintura de control ActiveX pinta todo el área de control. Esto es suficiente para controles simples, pero en muchos casos volver a pintar el control sería más rápido si solo se volvió a pintar la parte que necesitaba actualización, en lugar de todo el control.

La `OnDraw` función proporciona un método fácil de optimización pasando *rcInvalid*, el área rectangular del control que necesita redibujar. Utilice esta área, generalmente más pequeña que toda el área de control, para acelerar el proceso de pintura.

## <a name="painting-your-control-using-metafiles"></a><a name="_core_painting_your_control_using_metafiles"></a>Pintar el control con metarchivos

En la *pdc* mayoría de `OnDraw` los casos, el parámetro pdc de la función apunta a un contexto de dispositivo de pantalla (DC). Sin embargo, al imprimir imágenes del control o durante una sesión de vista previa de impresión, el controlador de dominio recibido para la representación es un tipo especial denominado "metaarchivo DC". A diferencia de un controlador de dominio de pantalla, que controla inmediatamente las solicitudes que se le envían, un controlador de dominio de metarchivo almacena las solicitudes que se reproducirán más adelante. Algunas aplicaciones de contenedor también pueden optar por representar la imagen de control mediante un controlador de dominio de metarchivo cuando está en modo de diseño.

El contenedor puede realizar solicitudes de dibujo de `IViewObject::Draw` metarchivo a través de dos funciones `IDataObject::GetData`de interfaz: (esta función también se puede llamar para el dibujo que no sea de metarchivo) y . Cuando se pasa un controlador de dominio de metarchivo como uno de los parámetros, el marco MFC realiza una llamada a [COleControl::OnDrawMetafile](../mfc/reference/colecontrol-class.md#ondrawmetafile). Dado que se trata de una función miembro virtual, invalide esta función en la clase de control para realizar cualquier procesamiento especial. El comportamiento `COleControl::OnDraw`predeterminado llama a .

Para asegurarse de que el control se puede dibujar en contextos de dispositivo de pantalla y metarchivo, debe usar solo funciones miembro que se admiten en una pantalla y un controlador de dominio de metarchivo. Tenga en cuenta que es posible que el sistema de coordenadas no se mida en píxeles.

Dado que la `OnDrawMetafile` implementación predeterminada `OnDraw` de llama a la función del control, utilice solo las `OnDrawMetafile`funciones miembro que son adecuadas para un metarchivo y un contexto de dispositivo de pantalla, a menos que invalide . A continuación se `CDC` enumera el subconjunto de funciones miembro que se pueden usar en un metarchivo y en un contexto de dispositivo de pantalla. Para obtener más información sobre estas funciones, vea la clase [CDC](../mfc/reference/cdc-class.md) en la *referencia de MFC*.

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

Además `CDC` de las funciones miembro, hay varias otras funciones que son compatibles en un controlador de dominio de metarchivo. Estos incluyen [CPalette::AnimatePalette](../mfc/reference/cpalette-class.md#animatepalette), [CFont::CreateFontIndirect](../mfc/reference/cfont-class.md#createfontindirect)y `CBrush`tres funciones miembro de : [CreateBrushIndirect](../mfc/reference/cbrush-class.md#createbrushindirect), [CreateDIBPatternBrush](../mfc/reference/cbrush-class.md#createdibpatternbrush)y [CreatePatternBrush](../mfc/reference/cbrush-class.md#createpatternbrush).

Las funciones que no se registran en un metarchivo son: [DrawFocusRect](../mfc/reference/cdc-class.md#drawfocusrect), [DrawIcon](../mfc/reference/cdc-class.md#drawicon), [DrawText](../mfc/reference/cdc-class.md#drawtext), [ExcludeUpdateRgn](../mfc/reference/cdc-class.md#excludeupdatergn), [FillRect](../mfc/reference/cdc-class.md#fillrect), [FrameRect](../mfc/reference/cdc-class.md#framerect), [GrayString](../mfc/reference/cdc-class.md#graystring), [InvertRect](../mfc/reference/cdc-class.md#invertrect), [ScrollDC](../mfc/reference/cdc-class.md#scrolldc)y [TabbedTextOut](../mfc/reference/cdc-class.md#tabbedtextout). Dado que un controlador de dominio de metarchivo no está asociado realmente a un dispositivo, no puede usar SetDIBits, GetDIBits y CreateDIBitmap con un controlador de dominio de metarchivo. Puede usar SetDIBitsToDevice y StretchDIBits con un controlador de dominio de metarchivo como destino. [CreateCompatibleDC](../mfc/reference/cdc-class.md#createcompatibledc), [CreateCompatibleBitmap](../mfc/reference/cbitmap-class.md#createcompatiblebitmap)y [CreateDiscardableBitmap](../mfc/reference/cbitmap-class.md#creatediscardablebitmap) no son significativos con un controlador de dominio de metarchivo.

Otro punto a tener en cuenta al utilizar un controlador de dominio de metarchivo es que el sistema de coordenadas no se puede medir en píxeles. Por este motivo, todo el código de dibujo debe `OnDraw` ajustarse para que quepa en el rectángulo al que se pasa en el parámetro *rcBounds.* Esto evita la pintura accidental fuera del control porque *rcBounds* representa el tamaño de la ventana del control.

Después de implementar la representación de metarchivo para el control, use contenedor de pruebas para probar el metarchivo. Consulte [Probar propiedades y eventos con un contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md) para obtener información acerca de cómo acceder al contenedor de prueba.

#### <a name="to-test-the-controls-metafile-using-test-container"></a>Para probar el metarchivo del control mediante contenedor de pruebas

1. En el menú **Editar** del contenedor de pruebas, haga clic en **Insertar nuevo control**.

1. En el cuadro **Insertar nuevo control,** seleccione el control y haga clic en **Aceptar**.

   El control aparecerá en contenedor de prueba.

1. En el menú **Control,** haga clic en **Dibujar metaarchivo**.

   Aparece una ventana independiente en la que se muestra el metarchivo. Puede cambiar el tamaño de esta ventana para ver cómo afecta el escalado al metarchivo del control. Puede cerrar esta ventana en cualquier momento.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)
