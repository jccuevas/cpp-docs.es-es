---
title: 'Controles ActiveX MFC: Pintar un Control ActiveX | Microsoft Docs'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], painting
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b14f562bd93bf023d540bf362dd2f9a881c2e441
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436798"
---
# <a name="mfc-activex-controls-painting-an-activex-control"></a>Controles ActiveX MFC: Pintar un control ActiveX

En este artículo se describe el proceso de dibujo del control ActiveX y cómo puede modificar el código para optimizar el proceso. (Consulte [optimizar el dibujo de controles](../mfc/optimizing-control-drawing.md) para conocer las técnicas optimizar el dibujo haciendo que los controles no individualmente restauración objetos GDI seleccionados anteriormente. Después de han dibujado todos los controles, el contenedor puede restaurar automáticamente los objetos originales.)

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no se recomienda para nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que sustituyen a ActiveX, vea [controles ActiveX](activex-controls.md).

Ejemplos de este artículo proceden de un control creado por el Asistente para controles de ActiveX de MFC con la configuración predeterminada. Para obtener más información sobre cómo crear una aplicación de esqueleto control mediante el Asistente para controles de ActiveX de MFC, vea el artículo [Asistente para controles ActiveX de MFC](../mfc/reference/mfc-activex-control-wizard.md).

Se tratan los siguientes temas:

- [El proceso general para pintar un control y el código creado por el Asistente para controles de ActiveX para admitir la pintura](#_core_the_painting_process_of_an_activex_control)

- [Cómo optimizar el proceso de dibujo](#_core_optimizing_your_paint_code)

- [Cómo dibujar el control usando metarchivos](#_core_painting_your_control_using_metafiles)

##  <a name="_core_the_painting_process_of_an_activex_control"></a> El proceso de dibujo de un Control ActiveX

Cuando se muestran inicialmente o se vuelven a dibujar controles ActiveX, sigue un proceso similar a otras aplicaciones desarrolladas mediante MFC, con una diferencia importante: los controles ActiveX pueden ser un activo o en un estado inactivo.

Se representa un control activo en un contenedor de controles ActiveX mediante una ventana secundaria. Al igual que otras ventanas, es responsable de dibujarse a sí misma cuando se recibe un mensaje WM_PAINT. La clase del control base, [COleControl](../mfc/reference/colecontrol-class.md), controla este mensaje en su `OnPaint` función. Esta implementación predeterminada llama el `OnDraw` función de su control.

Se dibuja un control inactivo de manera diferente. Cuando el control esté inactivo, su ventana es invisible o no existe, por lo que no puede recibir un mensaje de dibujo. En su lugar, el contenedor del control llama directamente el `OnDraw` función del control. Esto difiere del proceso de dibujo de un control activo en el que el `OnPaint` nunca se llama a la función miembro.

Como se describe en los párrafos anteriores, cómo se actualiza un control ActiveX depende del estado del control. Sin embargo, dado que el marco llama a la `OnDraw` función miembro en ambos casos, agrega la mayor parte de su código de dibujo en esta función miembro.

El `OnDraw` función miembro controla el dibujo del control. Cuando un control está inactivo, el contenedor del control llama `OnDraw`, pasando el contexto de dispositivo del contenedor del control y las coordenadas del área rectangular ocupada por el control.

El rectángulo que se pasó el marco de trabajo para el `OnDraw` función miembro contiene el área ocupado por el control. Si el control está activo, la esquina superior izquierda es (0, 0) y el contexto de dispositivo que se pasa es para la ventana secundaria que contiene el control. Si el control está inactivo, la coordenada superior izquierda no es necesariamente (0, 0) y pasarlo el contexto de dispositivo para el contenedor del control que contiene el control.

> [!NOTE]
>  Es importante que las modificaciones realizadas en `OnDraw` no dependen punto superior izquierdo del rectángulo en el es igual a (0, 0) y que dibuja solo dentro del rectángulo pasado a `OnDraw`. Pueden producirse resultados inesperados si se dibuja fuera del área del rectángulo.

La implementación predeterminada proporcionada por el Asistente para controles de ActiveX de MFC en el archivo de implementación (. (CPP), se muestra a continuación, dibuja el rectángulo con un pincel y rellena la elipse con el color de fondo actual.

[!code-cpp[NVC_MFC_AxUI#1](../mfc/codesnippet/cpp/mfc-activex-controls-painting-an-activex-control_1.cpp)]

> [!NOTE]
>  Al pintar un control, no debe realizar suposiciones sobre el estado del contexto del dispositivo que se pasa como el *pdc* parámetro para el `OnDraw` función. En ocasiones, el contexto de dispositivo proporcionado por la aplicación de contenedor y no necesariamente se inicializarán en el estado predeterminado. En particular, seleccione explícitamente los lápices, pinceles, colores, fuentes y otros recursos que depende el código de dibujo.

##  <a name="_core_optimizing_your_paint_code"></a> Optimización del código de dibujo

Después de que el control se dibuje correctamente, el paso siguiente consiste en optimizar el `OnDraw` función.

La implementación predeterminada de dibujo de controles ActiveX pinta el área de todo el control. Esto es suficiente para controles sencillos, pero en muchos casos volver a dibujarse el control sería más rápido si solo se vuelva a dibujar la parte que había que actualizar, en lugar de todo el control.

El `OnDraw` función proporciona un método sencillo de optimización pasando *rcInvalid*, el área rectangular del control que se debe volver a dibujar. Use esta área, suele ser menor que el área de control todo, para acelerar el proceso de dibujo.

##  <a name="_core_painting_your_control_using_metafiles"></a> Dibujar el Control usando metarchivos

En la mayoría de los casos la *pdc* parámetro para el `OnDraw` función apunta a un contexto de dispositivo de pantalla (DC). Sin embargo, al imprimir imágenes del control o durante una sesión de vista previa de impresión, el controlador de dominio que se recibió para la representación es un tipo especial denominado "metarchivo DC". A diferencia de una pantalla de controlador de dominio, que controla inmediatamente las solicitudes enviadas a ella, un DC de metarchivo almacena las solicitudes que se reproducirá en un momento posterior. Algunas aplicaciones de contenedor también puede representar la imagen del control mediante un controlador de dominio en el modo de diseño del metarchivo.

Metarchivo solicitudes de dibujo se puede realizar por el contenedor a través de dos funciones de interfaz: `IViewObject::Draw` (también se puede llamar esta función para que no sean metarchivo de dibujo) y `IDataObject::GetData`. Cuando un metarchivo DC se pasa como uno de los parámetros, el marco de trabajo MFC realiza una llamada a [COleControl:: OnDrawMetafile](../mfc/reference/colecontrol-class.md#ondrawmetafile). Se trata de una función miembro virtual, reemplace esta función en la clase de control para realizar cualquier procesamiento especial. Las llamadas del comportamiento predeterminado `COleControl::OnDraw`.

Para asegurarse de que se puede dibujar el control en la pantalla y metarchivo contextos de dispositivo, debe usar solo las funciones de miembro que se admiten en una pantalla y un DC de metarchivo. Tenga en cuenta que el sistema de coordenadas no es posible que se mide en píxeles.

Dado que la implementación predeterminada de `OnDrawMetafile` llama al control `OnDraw` función, utilice solo funciones miembro que son adecuadas para un metarchivo y un contexto de dispositivo de pantalla, a menos que reemplace `OnDrawMetafile`. La siguiente muestra el subconjunto de `CDC` funciones miembro que se pueden usar en un metarchivo y un contexto de dispositivo de pantalla. Para obtener más información sobre estas funciones, vea la clase [CDC](../mfc/reference/cdc-class.md) en el *referencia de MFC*.

|Arco|BibBlt|Cuerda|
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

Además `CDC` funciones miembro, hay muchas otras funciones que son compatibles en un DC de metarchivo. Estos incluyen [CPalette:: AnimatePalette](../mfc/reference/cpalette-class.md#animatepalette), [CFont::CreateFontIndirect](../mfc/reference/cfont-class.md#createfontindirect)y tres funciones miembro de `CBrush`: [CreateBrushIndirect](../mfc/reference/cbrush-class.md#createbrushindirect), [CreateDIBPatternBrush](../mfc/reference/cbrush-class.md#createdibpatternbrush), y [CreatePatternBrush](../mfc/reference/cbrush-class.md#createpatternbrush).

Las funciones que no se registran en un metarchivo son: [DrawFocusRect](../mfc/reference/cdc-class.md#drawfocusrect), [DrawIcon](../mfc/reference/cdc-class.md#drawicon), [DrawText](../mfc/reference/cdc-class.md#drawtext), [ExcludeUpdateRgn](../mfc/reference/cdc-class.md#excludeupdatergn), [FillRect](../mfc/reference/cdc-class.md#fillrect), [FrameRect](../mfc/reference/cdc-class.md#framerect), [GrayString](../mfc/reference/cdc-class.md#graystring), [InvertRect](../mfc/reference/cdc-class.md#invertrect), [ScrollDC](../mfc/reference/cdc-class.md#scrolldc)y [TabbedTextOut](../mfc/reference/cdc-class.md#tabbedtextout). Dado que un DC de metarchivo no es realmente asociado con un dispositivo, no puede utilizar SetDIBits, GetDIBits y CreateDIBitmap con un DC de metarchivo. Puede usar SetDIBitsToDevice y StretchDIBits con un DC de metarchivo como destino. [CreateCompatibleDC](../mfc/reference/cdc-class.md#createcompatibledc), [CreateCompatibleBitmap](../mfc/reference/cbitmap-class.md#createcompatiblebitmap), y [CreateDiscardableBitmap](../mfc/reference/cbitmap-class.md#creatediscardablebitmap) no son significativos con un DC de metarchivo.

Otro aspecto a tener en cuenta cuando se usa un DC de metarchivo es que el sistema de coordenadas no es posible que se mide en píxeles. Por este motivo, todo el código de dibujo se debería ajustar para que quepa en el rectángulo pasado a `OnDraw` en el *rcBounds* parámetro. Esto evita que dibujar fuera del control porque *rcBounds* representa el tamaño de la ventana del control.

Después de haber implementado la representación del metarchivo del control, utilice Test Container para probar el metarchivo. Consulte [Probar propiedades y eventos con un contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md) para obtener información acerca de cómo acceder al contenedor de prueba.

#### <a name="to-test-the-controls-metafile-using-test-container"></a>Para probar el metarchivo del control con el contenedor de prueba

1. En el contenedor de prueba **editar** menú, haga clic en **Insertar nuevo Control**.

1. En el **Insertar nuevo Control** , seleccione el control y haga clic en **Aceptar**.

     El control aparecerá en el contenedor de prueba.

1. En el **Control** menú, haga clic en **dibujar metarchivos**.

     Aparecerá una ventana independiente en el que se muestra el metarchivo. Puede cambiar el tamaño de esta ventana para ver cómo afecta al metarchivo del control. Puede cerrar esta ventana en cualquier momento.

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

