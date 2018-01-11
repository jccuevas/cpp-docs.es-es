---
title: 'Controles ActiveX MFC: Pintar un Control ActiveX | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], painting
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a2a2dc7b0cebbfaa6f6fe7dbe7dc69e5d4f80121
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-painting-an-activex-control"></a>Controles ActiveX MFC: Pintar un control ActiveX
Este artículo describe el proceso de dibujo del control ActiveX y cómo puede modificar el código para optimizar el proceso. (Consulte [optimizar el dibujo de controles](../mfc/optimizing-control-drawing.md) para conocer las técnicas optimizar el dibujo al no tener controles individualmente restauración objetos GDI previamente seleccionados. Después de han dibujado todos los controles, el contenedor puede restaurar automáticamente los objetos originales.)  
  
 En este artículo se trata de un control creado por el Asistente para controles de ActiveX de MFC con la configuración predeterminada. Para obtener más información acerca de cómo crear una aplicación de control de esqueleto mediante el Asistente para controles de ActiveX de MFC, vea el artículo [Asistente para controles ActiveX de MFC](../mfc/reference/mfc-activex-control-wizard.md).  
  
 Se tratan los temas siguientes:  
  
-   [El proceso general para pintar un control y el código creado por el Asistente para controles de ActiveX para admitir que se dibuje](#_core_the_painting_process_of_an_activex_control)  
  
-   [Cómo optimizar el proceso de dibujo](#_core_optimizing_your_paint_code)  
  
-   [Cómo dibujar el control usando metarchivos](#_core_painting_your_control_using_metafiles)  
  
##  <a name="_core_the_painting_process_of_an_activex_control"></a>El proceso de dibujo de un Control ActiveX  
 Cuando se muestran inicialmente o se vuelven a dibujar controles ActiveX, siguen un proceso similar de otras aplicaciones desarrolladas mediante MFC, con una diferencia importante: los controles ActiveX pueden estar en un activo o un estado inactivo.  
  
 Un control activo se representa en un contenedor de controles ActiveX mediante una ventana secundaria. Al igual que otras ventanas, es responsable de dibujar propio cuando un `WM_PAINT` recibirlo. La clase del control base, [COleControl](../mfc/reference/colecontrol-class.md), controla este mensaje en su `OnPaint` función. Esta implementación predeterminada llama el `OnDraw` función del control.  
  
 Un control inactivo se dibuja de manera diferente. Cuando el control está inactivo, su ventana es invisible o no existe, por lo que no puede recibir un mensaje de dibujo. En su lugar, el contenedor del control llama directamente el `OnDraw` función del control. Esto difiere del proceso de dibujo de un control activo en el que el `OnPaint` nunca se llama la función miembro.  
  
 Como se describe en los párrafos anteriores, ¿cómo se actualiza un control ActiveX depende del estado del control. Sin embargo, dado que el marco llama a la `OnDraw` función miembro en ambos casos, debe agregar la mayoría del código de dibujo en esta función miembro.  
  
 El `OnDraw` función miembro controla el dibujo del control. Cuando un control está inactivo, el contenedor del control llama `OnDraw`, pasando el contexto de dispositivo del contenedor del control y las coordenadas del área rectangular ocupada por el control.  
  
 El rectángulo pasado por el marco de trabajo para el `OnDraw` función miembro contiene el área ocupado por el control. Si el control está activo, la esquina superior izquierda es (0, 0) y el contexto de dispositivo que se pasa es para la ventana secundaria que contiene el control. Si el control está inactivo, la coordenada superior izquierda no es necesariamente (0, 0) y el contexto de dispositivo que se pasa es para el contenedor del control que contiene el control.  
  
> [!NOTE]
>  Es importante que las modificaciones realizadas en `OnDraw` no dependen punto superior izquierdo del rectángulo es igual a (0, 0) y que se dibuje sólo dentro del rectángulo pasado a `OnDraw`. Pueden producirse resultados inesperados si se dibuja fuera del área del rectángulo.  
  
 La implementación predeterminada proporcionada por el Asistente para controles de ActiveX de MFC en el archivo de implementación (. (CPP), se muestra a continuación, se dibuja el rectángulo con un pincel y rellena la elipse con el color de fondo actual.  
  
 [!code-cpp[NVC_MFC_AxUI#1](../mfc/codesnippet/cpp/mfc-activex-controls-painting-an-activex-control_1.cpp)]  
  
> [!NOTE]
>  Al dibujar un control, no debe realizar suposiciones sobre el estado del contexto de dispositivo que se pasa como el *pdc* parámetro para el `OnDraw` función. En ocasiones, el contexto de dispositivo proporcionado por la aplicación contenedora y no necesariamente se inicializarán al estado predeterminado. En particular, seleccione explícitamente los lápices, pinceles, colores, fuentes y otros recursos que depende su código de dibujo.  
  
##  <a name="_core_optimizing_your_paint_code"></a>Optimizar el código de dibujo  
 Después de que el control se dibuje correctamente, el siguiente paso es optimizar la `OnDraw` función.  
  
 La implementación predeterminada de dibujo de controles ActiveX pinta la zona de todo el control. Esto es suficiente para controles sencillos, pero en muchos casos volver a dibujarse el control sería más rápido si sólo la parte que sea necesario actualizar se vuelve a dibujar, en lugar de todo el control.  
  
 El `OnDraw` función proporciona un método sencillo de optimización pasando `rcInvalid`, el área rectangular del control que es necesario volver a dibujar. Utilice este área, suele ser menor que el área de todo el control, para acelerar el proceso de dibujo.  
  
##  <a name="_core_painting_your_control_using_metafiles"></a>Dibujar el Control usando metarchivos  
 En la mayoría de los casos la `pdc` parámetro para el `OnDraw` función apunta a un contexto de dispositivo de pantalla (DC). Sin embargo, al imprimir imágenes del control o durante una sesión de vista previa de impresión, el controlador de dominio que se recibió para la representación es un tipo especial denominado "DC de metarchivo". A diferencia de un DC de pantalla, que controla inmediatamente las solicitudes enviadas a él, un DC de metarchivo almacena las solicitudes que se reproducirá en un momento posterior. Algunas aplicaciones de contenedor también pueden elegir representar la imagen del control mediante un controlador de dominio en modo de diseño de metarchivo.  
  
 Metarchivo solicitudes de dibujo se puede realizar por el contenedor a través de dos funciones de interfaz: **IViewObject::Draw** (esta función también se puede llamar para dibujar no metarchivo) y **IDataObject:: GetData**. Cuando un metarchivo de controlador de dominio se pasa como uno de los parámetros, el marco de trabajo MFC realiza una llamada a [COleControl:: OnDrawMetafile](../mfc/reference/colecontrol-class.md#ondrawmetafile). Puesto que se trata de una función miembro virtual, reemplazar esta función en la clase de control para realizar cualquier procesamiento especial. Las llamadas de comportamiento predeterminado `COleControl::OnDraw`.  
  
 Para asegurarse de que el control se puede dibujar en contextos de dispositivo de pantalla y metarchivo, debe usar solo las funciones de miembro que se admiten en una pantalla y un DC de metarchivo. Tenga en cuenta que no se puede medir el sistema de coordenadas en píxeles.  
  
 Dado que la implementación predeterminada de `OnDrawMetafile` llama al control `OnDraw` funcione, use solo las funciones de miembro que son adecuadas para un metarchivo y un contexto de dispositivo de pantalla, a menos que invalide `OnDrawMetafile`. Las listas siguientes el subconjunto de `CDC` funciones miembro que pueden usarse en un metarchivo y un contexto de dispositivo de pantalla. Para obtener más información sobre estas funciones, vea la clase [CDC](../mfc/reference/cdc-class.md) en el *referencia de MFC*.  
  
|Arco|BibBlt|Cuerda|  
|---------|------------|-----------|  
|**Elipse**|**Escape**|`ExcludeClipRect`|  
|`ExtTextOut`|`FloodFill`|`IntersectClipRect`|  
|`LineTo`|`MoveTo`|`OffsetClipRgn`|  
|`OffsetViewportOrg`|`OffsetWindowOrg`|`PatBlt`|  
|`Pie`|**Polígono**|`Polyline`|  
|`PolyPolygon`|`RealizePalette`|`RestoreDC`|  
|`RoundRect`|`SaveDC`|`ScaleViewportExt`|  
|`ScaleWindowExt`|`SelectClipRgn`|`SelectObject`|  
|`SelectPalette`|`SetBkColor`|`SetBkMode`|  
|`SetMapMode`|`SetMapperFlags`|`SetPixel`|  
|`SetPolyFillMode`|`SetROP2`|`SetStretchBltMode`|  
|`SetTextColor`|`SetTextJustification`|`SetViewportExt`|  
|`SetViewportOrg`|`SetWindowExt`|`SetWindowORg`|  
|`StretchBlt`|`TextOut`||  
  
 Además `CDC` funciones miembro, hay muchas otras funciones que son compatibles en un DC de metarchivo. Puede tratarse de [CPalette:: AnimatePalette](../mfc/reference/cpalette-class.md#animatepalette), [CFont::CreateFontIndirect](../mfc/reference/cfont-class.md#createfontindirect)y tres funciones miembro de `CBrush`: [CreateBrushIndirect](../mfc/reference/cbrush-class.md#createbrushindirect), [CreateDIBPatternBrush](../mfc/reference/cbrush-class.md#createdibpatternbrush), y [CreatePatternBrush](../mfc/reference/cbrush-class.md#createpatternbrush).  
  
 Las funciones que no se registran en un metarchivo son: [DrawFocusRect](../mfc/reference/cdc-class.md#drawfocusrect), [DrawIcon](../mfc/reference/cdc-class.md#drawicon), [DrawText](../mfc/reference/cdc-class.md#drawtext), [ExcludeUpdateRgn](../mfc/reference/cdc-class.md#excludeupdatergn), [FillRect](../mfc/reference/cdc-class.md#fillrect), [FrameRect](../mfc/reference/cdc-class.md#framerect), [GrayString](../mfc/reference/cdc-class.md#graystring), [InvertRect](../mfc/reference/cdc-class.md#invertrect), [ScrollDC](../mfc/reference/cdc-class.md#scrolldc)y [TabbedTextOut](../mfc/reference/cdc-class.md#tabbedtextout). Dado que un DC de metarchivo no es realmente asociado con un dispositivo, no puede utilizar SetDIBits, GetDIBits y CreateDIBitmap con un DC de metarchivo. Puede usar SetDIBitsToDevice y StretchDIBits con un DC de metarchivo como destino. [CreateCompatibleDC](../mfc/reference/cdc-class.md#createcompatibledc), [CreateCompatibleBitmap](../mfc/reference/cbitmap-class.md#createcompatiblebitmap), y [CreateDiscardableBitmap](../mfc/reference/cbitmap-class.md#creatediscardablebitmap) no tienen sentido con un DC de metarchivo.  
  
 Otro punto a tener en cuenta cuando se utiliza un DC de metarchivo es que el sistema de coordenadas puede no medirse en píxeles. Por esta razón, todo el código de dibujo se debería ajustar para caber en el rectángulo pasado a `OnDraw` en el `rcBounds` parámetro. Esto evita que accidental dibujar fuera del control porque `rcBounds` representa el tamaño de la ventana del control.  
  
 Después de haber implementado la representación del metarchivo para el control, use Test Container para probar el metarchivo. Consulte [Probar propiedades y eventos con un contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md) para obtener información acerca de cómo acceder al contenedor de prueba.  
  
#### <a name="to-test-the-controls-metafile-using-test-container"></a>Para probar el metarchivo del control mediante Test Container  
  
1.  En el contenedor de prueba **editar** menú, haga clic en **Insertar nuevo Control**.  
  
2.  En el **Insertar nuevo Control** , seleccione el control y haga clic en **Aceptar**.  
  
     El control aparecerá en Test container.  
  
3.  En el **Control** menú, haga clic en **Dibujar metarchivo**.  
  
     Aparecerá una ventana independiente en el que se muestra el metarchivo. Puede cambiar el tamaño de esta ventana para ver cómo afecta el ajuste de escala a metarchivo del control. Puede cerrar esta ventana en cualquier momento.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

