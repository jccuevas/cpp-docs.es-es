---
title: "Controles ActiveX MFC: Pintar un control ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX en MFC, optimizar"
  - "controles ActiveX en MFC, dibujar"
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Controles ActiveX MFC: Pintar un control ActiveX
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe el proceso de dibujo del control ActiveX y cómo modificar código de dibujo para optimizar el proceso. \(Vea [Optimizar el gráfico de Control](../mfc/optimizing-control-drawing.md) para las técnicas de cómo optimizar el gráfico no tener controles restablecen individualmente los objetos seleccionado anteriormente GDI.  Después de que todos los controles se han dibujen, el contenedor puede automáticamente restablecer los objetos originales.\)  
  
 Los ejemplos de este caso son de un control creado por el asistente para controles ActiveX MFC con la configuración predeterminada.  Para obtener más información sobre cómo crear una aplicación básica del control mediante el asistente para controles ActiveX MFC, vea el artículo [Asistente para controles ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md).  
  
 Se tratan los siguientes temas:  
  
-   [El proceso general para pintar un control y el código creados por el asistente para controles ActiveX para admitir la representación](#_core_the_painting_process_of_an_activex_control)  
  
-   [Cómo optimizar el proceso de dibujo](#_core_optimizing_your_paint_code)  
  
-   [Cómo pintar el control mediante metarchivos](#_core_painting_your_control_using_metafiles)  
  
##  <a name="_core_the_painting_process_of_an_activex_control"></a> El proceso de Painting de un control ActiveX  
 Cuando los controles ActiveX se muestran o se rediseñados inicialmente, siguen un proceso de dibujo similar a otras aplicaciones desarrolladas con MFC, con una diferencia importante: Los controles ActiveX pueden estar en un activo o un estado inactivo.  
  
 Un control activo se representa en un contenedor de controles ActiveX por una ventana secundaria.  Como otras ventanas, es responsable de pintarse cuando se recibe un mensaje de `WM_PAINT` .  La clase base de controles, [COleControl](../mfc/reference/colecontrol-class.md), controla este mensaje en la función de `OnPaint` .  Esta implementación predeterminada llama a la función de `OnDraw` del control.  
  
 Un control inactivo se pinta de manera diferente.  Cuando el control está inactivo, la ventana no está visible o inexistente, por lo que no puede recibir un mensaje de dibujo.  En su lugar, el contenedor del control llama directamente la función de `OnDraw` del control.  Esto difiere del proceso de dibujo de un control activo en que la función miembro de `OnPaint` nunca se denomina.  
  
 Como se describe en los párrafos anteriores, cómo se actualiza un control ActiveX depende del estado del control.  Sin embargo, dado que el marco de trabajo llama a la función miembro de `OnDraw` en ambos casos, se agrega al código de dibujo en esta función miembro.  
  
 Los identificadores de la función miembro de `OnDraw` controlan paint.  Cuando un control está inactivo, el contenedor del control llama a `OnDraw`, pasando el contexto de dispositivo del contenedor del control y las coordenadas del área rectangular ocupada por el control.  
  
 El último rectángulo por el marco a la función miembro de `OnDraw` contiene el área ocupada por el control.  Si el control está activo, la esquina superior izquierda es \(0, 0\) y el contexto del último dispositivo corresponde a la ventana secundaria que contiene el control.  Si el control está inactivo, la coordenada superior izquierda no es necesariamente \(0, 0\) y el contexto del último dispositivo es para el contenedor del control que contiene el control.  
  
> [!NOTE]
>  Es importante que las modificaciones a `OnDraw` no dependen del punto superior izquierda del rectángulo que es igual a \(0, 0\) y que se dibuja desde dentro del rectángulo pasado a `OnDraw`.  Pueden producirse resultados inesperados si dibuja más allá del área del rectángulo.  
  
 La implementación predeterminada proporcionada por el asistente para controles ActiveX MFC en el archivo de implementación del control \(.CPP\), mostrado abajo, pinta el rectángulo con un pincel blanco y rellena la elipse con el color de fondo actual.  
  
 [!code-cpp[NVC_MFC_AxUI#1](../mfc/codesnippet/CPP/mfc-activex-controls-painting-an-activex-control_1.cpp)]  
  
> [!NOTE]
>  Al pintar un control, no debe realizar suposiciones sobre el estado del contexto de dispositivo que se pasa como parámetro de *pdc* a la función de `OnDraw` .  El contexto de dispositivo proporcionado ocasionalmente por la aplicación contenedora y no se inicializará necesariamente con estado predeterminado.  En particular, explícitamente seleccione lápices, los pinceles, los colores, fuentes, y otros recursos de los que el código de dibujo depende.  
  
##  <a name="_core_optimizing_your_paint_code"></a> Optimizar el código de dibujo  
 Después de que el control se está pintando correctamente, el paso siguiente es optimizar la función de `OnDraw` .  
  
 La implementación predeterminada del control ActiveX que pinta se dibuja el área de control completa.  Esto es suficiente para controles sencillos pero, en muchos casos la repintura de control sería más rápida si sólo la parte que la actualización necesario se repintado, en lugar de todo el control.  
  
 La función de `OnDraw` proporciona un método fácil de optimización pasando `rcInvalid`, el área rectangular del control que necesite volver a dibujar.  Use esta área, normalmente menor que el área de control completa, acelerar el proceso de dibujo.  
  
##  <a name="_core_painting_your_control_using_metafiles"></a> Representación del Control mediante metarchivos  
 En la mayoría de los casos el parámetro de `pdc` a los puntos de la función de `OnDraw` a un contexto \(DC\) de dispositivo de pantalla.  Sin embargo, al imprimir las imágenes del control o durante una sesión de vista previa de impresión, elementos TITLE. recibida para representar es un tipo especial denominado una “TITLE. metafile”.  A diferencia de una TITLE. de presentación, que inmediatamente administra las solicitudes le envió, una TITLE. metafile almacenan solicitudes para reproducirla en un momento posterior.  Algunas aplicaciones contenedoras pueden elegir para generar la imagen del control mediante una TITLE. metafile cuando en modo de diseño.  
  
 Las solicitudes del gráfico de metarchivo se pueden hacer por el contenedor con dos funciones de interfaz: **IViewObject::Draw** \(esta función también se puede llamar para el gráfico de no metarchivo\) y **IDataObject::GetData**.  Cuando un metarchivo DC se pasa como uno de los parámetros, el marco de trabajo de MFC realiza una llamada a [COleControl::OnDrawMetafile](../Topic/COleControl::OnDrawMetafile.md).  Dado que se trata de una función miembro virtual, invalide esta función en la clase de control para realizar cualquier procesamiento especial.  El comportamiento predeterminado llama `COleControl::OnDraw`.  
  
 Para asegurarse de que el control se puede dibujar en pantalla y los contextos de dispositivo de metarchivo, debe utilizar sólo las funciones miembro que se admiten en una pantalla y un metarchivo DC.  Tenga en cuenta que el sistema de coordenadas no se puede medir en píxeles.  
  
 Dado que la implementación predeterminada de `OnDrawMetafile` llama a la función de `OnDraw` de control, utilice sólo las funciones miembro adecuados para un metarchivo y un contexto de dispositivo de pantalla, a menos que se invalide `OnDrawMetafile`.  A continuación se enumeran el subconjunto de funciones miembro de `CDC` que se pueden usar en un metarchivo y un contexto de dispositivo de pantalla.  Para obtener más información sobre estas funciones, vea la clase [CDC](../mfc/reference/cdc-class.md) en *la referencia de MFC*.  
  
|Arco|BibBlt|Acorde|  
|----------|------------|------------|  
|**Elipse**|**Escape**|`ExcludeClipRect`|  
|`ExtTextOut`|`FloodFill`|`IntersectClipRect`|  
|`LineTo`|`MoveTo`|`OffsetClipRgn`|  
|`OffsetViewportOrg`|`OffsetWindowOrg`|`PatBlt`|  
|`Pie`|**Polygon**|`Polyline`|  
|`PolyPolygon`|`RealizePalette`|`RestoreDC`|  
|`RoundRect`|`SaveDC`|`ScaleViewportExt`|  
|`ScaleWindowExt`|`SelectClipRgn`|`SelectObject`|  
|`SelectPalette`|`SetBkColor`|`SetBkMode`|  
|`SetMapMode`|`SetMapperFlags`|`SetPixel`|  
|`SetPolyFillMode`|`SetROP2`|`SetStretchBltMode`|  
|`SetTextColor`|`SetTextJustification`|`SetViewportExt`|  
|`SetViewportOrg`|`SetWindowExt`|`SetWindowORg`|  
|`StretchBlt`|`TextOut`||  
  
 Además de las funciones miembro de `CDC` , hay otras funciones que son compatibles en un metarchivo DC.  Estos incluyen [CPalette::AnimatePalette](../Topic/CPalette::AnimatePalette.md), [CFont::CreateFontIndirect](../Topic/CFont::CreateFontIndirect.md), y funciones con tres miembros de `CBrush`: [CreateBrushIndirect](../Topic/CBrush::CreateBrushIndirect.md), [CreateDIBPatternBrush](../Topic/CBrush::CreateDIBPatternBrush.md), y [CreatePatternBrush](../Topic/CBrush::CreatePatternBrush.md).  
  
 Funciones que no se registra en un metarchivo es: [DrawFocusRect](../Topic/CDC::DrawFocusRect.md), [DrawIcon](../Topic/CDC::DrawIcon.md), [DrawText](../Topic/CDC::DrawText.md), [ExcludeUpdateRgn](../Topic/CDC::ExcludeUpdateRgn.md), [FillRect](../Topic/CDC::FillRect.md), [FrameRect](../Topic/CDC::FrameRect.md), [GrayString](../Topic/CDC::GrayString.md), [InvertRect](../Topic/CDC::InvertRect.md), [ScrollDC](../Topic/CDC::ScrollDC.md), y [TabbedTextOut](../Topic/CDC::TabbedTextOut.md).  Dado que un metarchivo DC no se asocia realmente un dispositivo, no puede utilizar SetDIBits, GetDIBits, y CreateDIBitmap con un metarchivo DC.  Puede utilizar SetDIBitsToDevice y StretchDIBits con un metarchivo DC como destino.  [CreateCompatibleDC](../Topic/CDC::CreateCompatibleDC.md), [CreateCompatibleBitmap](../Topic/CBitmap::CreateCompatibleBitmap.md), y [CreateDiscardableBitmap](../Topic/CBitmap::CreateDiscardableBitmap.md) no son significativos con un metarchivo DC.  
  
 Otro punto para ver cuando se utiliza un metarchivo DC es que el sistema de coordenadas no se puede medir en píxeles.  Por esta razón, el código de dibujo se debe ajustar para ajustarse al último rectángulo a `OnDraw` en el parámetro de `rcBounds` .  Esto evita la representación accidental fuera del control porque `rcBounds` representa el tamaño de la ventana de control.  
  
 Después de haber implementado la representación metafile para el control, contenedor de prueba de uso para probar el metarchivo.  Vea [Probar propiedades y eventos con Test Container](../mfc/testing-properties-and-events-with-test-container.md) para obtener información sobre cómo tener acceso a Test Container.  
  
#### Para probar el metarchivo de control mediante el contenedor de prueba  
  
1.  En el menú de **edición** del contenedor de prueba, haga clic en **Insert New Control**.  
  
2.  En el cuadro de **Insert New Control** , seleccione el control y haga clic en **Aceptar**.  
  
     El control aparecerá en test container.  
  
3.  En el menú de **Control** , haga clic en **Draw Metafile**.  
  
     Una ventana independiente aparece en la que se muestra el metarchivo.  Puede cambiar el tamaño de esta ventana para ver cómo el escalar afecta al metarchivo del control.  Puede cerrar esta ventana en cualquier momento.  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)