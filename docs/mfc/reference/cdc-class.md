---
title: "CDC (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDC (clase)"
  - "coordinates in Windows 95/98 [C++]"
  - "device contexts [C++], CDC (clase)"
  - "screen coordinates in device contexts"
  - "Windows [C++], device contexts"
  - "Windows 95 [C++], coordenadas de pantalla"
  - "Windows 98 [C++], coordenadas de pantalla"
ms.assetid: 715b3334-cb2b-4c9c-8067-02eb7c66c8b2
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDC (clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Define una clase de objetos de dispositivo\-contexto.  
  
## Sintaxis  
  
```  
class CDC : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDC::CDC](../Topic/CDC::CDC.md)|Crea un objeto `CDC`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDC::AbortDoc](../Topic/CDC::AbortDoc.md)|Finaliza el trabajo de impresión actual, borrando todo que la aplicación ha escrito en el dispositivo desde la última llamada de la función miembro de `StartDoc` .|  
|[CDC::AbortPath](../Topic/CDC::AbortPath.md)|Cierre y descarta cualquier ruta en el contexto del dispositivo.|  
|[CDC::AddMetaFileComment](../Topic/CDC::AddMetaFileComment.md)|Copia el comentario de un búfer en un metarchivo especificado de ampliar\-formato.|  
|[CDC::AlphaBlend](../Topic/CDC::AlphaBlend.md)|Muestra los mapas de bits que tienen píxeles transparentes o semitransparentes.|  
|[CDC::AngleArc](../Topic/CDC::AngleArc.md)|Dibuja un segmento de línea y un arco, y mueve la posición actual al extremo del arco.|  
|[CDC::Arc](../Topic/CDC::Arc.md)|Dibuja un arco elíptico.|  
|[CDC::ArcTo](../Topic/CDC::ArcTo.md)|Dibuja un arco elíptico.  Esta función es similar a `Arc`, salvo que se actualiza la posición actual.|  
|[CDC::Attach](../Topic/CDC::Attach.md)|Asocia un contexto de dispositivo de Windows a este objeto de `CDC` .|  
|[CDC::BeginPath](../Topic/CDC::BeginPath.md)|Abra un corchete de ruta en el contexto del dispositivo.|  
|[CDC::BitBlt](../Topic/CDC::BitBlt.md)|Copia un mapa de bits de un contexto especificado del dispositivo.|  
|[CDC::Chord](../Topic/CDC::Chord.md)|Dibuja un acorde \(una figura cerrada limitada por la intersección de una elipse y un segmento de línea\).|  
|[CDC::CloseFigure](../Topic/CDC::CloseFigure.md)|Cierra una figura abierta en una ruta.|  
|[CDC::CreateCompatibleDC](../Topic/CDC::CreateCompatibleDC.md)|Crea un contexto de memoria\-dispositivo compatible con otro contexto de dispositivo.  Puede utilizarlo para preparar las imágenes en memoria.|  
|[CDC::CreateDC](../Topic/CDC::CreateDC.md)|Crea un contexto para un dispositivo concreto.|  
|[CDC::CreateIC](../Topic/CDC::CreateIC.md)|Crear un contexto de información para un dispositivo concreto.  Esto proporciona una manera rápida de obtener información sobre el dispositivo sin crear un contexto de dispositivo.|  
|[CDC::DeleteDC](../Topic/CDC::DeleteDC.md)|Elimina el contexto de dispositivo de Windows asociado a este objeto de `CDC` .|  
|[CDC::DeleteTempMap](../Topic/CDC::DeleteTempMap.md)|Invoca el controlador de tiempo de inactividad de `CWinApp` para eliminar cualquier objeto temporal de `CDC` creado por `FromHandle`.  También desasocia el contexto del dispositivo.|  
|[CDC::Detach](../Topic/CDC::Detach.md)|Desasocia el contexto de dispositivo de Windows de este objeto de `CDC` .|  
|[CDC::DPtoHIMETRIC](../Topic/CDC::DPtoHIMETRIC.md)|Convierte unidades en unidades de **HIMETRIC** .|  
|[CDC::DPtoLP](../Topic/CDC::DPtoLP.md)|Convierte unidades en unidades lógicas.|  
|[CDC::Draw3dRect](../Topic/CDC::Draw3dRect.md)|Dibuja un rectángulo tridimensional.|  
|[CDC::DrawDragRect](../Topic/CDC::DrawDragRect.md)|Borra y rediseña un rectángulo mientras se arrastra.|  
|[CDC::DrawEdge](../Topic/CDC::DrawEdge.md)|Dibuja los bordes de un rectángulo.|  
|[CDC::DrawEscape](../Topic/CDC::DrawEscape.md)|Tiene acceso a la funcionalidad de dibujo de una reproducción de vídeo que no son directamente a través de la interfaz de dispositivo \(GDI\) gráfico.|  
|[CDC::DrawFocusRect](../Topic/CDC::DrawFocusRect.md)|Dibuja un rectángulo con el estilo usado para indicar el foco.|  
|[CDC::DrawFrameControl](../Topic/CDC::DrawFrameControl.md)|Dibuje un control textbox.|  
|[CDC::DrawIcon](../Topic/CDC::DrawIcon.md)|Dibuja un icono.|  
|[CDC::DrawState](../Topic/CDC::DrawState.md)|Muestra una imagen y aplica un efecto visual para indicar un estado.|  
|[CDC::DrawText](../Topic/CDC::DrawText.md)|Dibuja el texto con formato en el rectángulo especificado.|  
|[CDC::DrawTextEx](../Topic/CDC::DrawTextEx.md)|Dibuja el texto con formato en el rectángulo especificado con formatos adicionales.|  
|[CDC::Ellipse](../Topic/CDC::Ellipse.md)|Dibuja una elipse.|  
|[CDC::EndDoc](../Topic/CDC::EndDoc.md)|Finaliza un trabajo de impresión iniciado por la función miembro de `StartDoc` .|  
|[CDC::EndPage](../Topic/CDC::EndPage.md)|Informa al controlador de dispositivo que una página está finalizando.|  
|[CDC::EndPath](../Topic/CDC::EndPath.md)|Cierra un corchete de ruta y selecciona la ruta definido por el corchete en el contexto del dispositivo.|  
|[CDC::EnumObjects](../Topic/CDC::EnumObjects.md)|Enumera los lápices y pinceles disponibles en un contexto de dispositivo.|  
|[CDC::Escape](../Topic/CDC::Escape.md)|Permite a las aplicaciones para tener acceso a los servicios que no son directamente disponibles de un dispositivo determinado con GDI.  También permite el acceso a las funciones de escape de Windows.  Las llamadas de escape realizadas por una aplicación se traducen y se envían a controladores de dispositivos.|  
|[CDC::ExcludeClipRect](../Topic/CDC::ExcludeClipRect.md)|Crea una nueva región de recorte que consta de la zona de recorte existente menos el rectángulo especificado.|  
|[CDC::ExcludeUpdateRgn](../Topic/CDC::ExcludeUpdateRgn.md)|Evita el gráfico de áreas no válidas de una ventana excluyendo una región actualizada en la ventana de una zona de recorte.|  
|[CDC::ExtFloodFill](../Topic/CDC::ExtFloodFill.md)|Rellena un área con el pincel actual.  Proporciona más flexibilidad que la función miembro de [CDC::FloodFill](../Topic/CDC::FloodFill.md) .|  
|[CDC::ExtTextOut](../Topic/CDC::ExtTextOut.md)|Escribe una cadena de caracteres dentro de un área rectangular con la fuente seleccionado actualmente.|  
|[CDC::FillPath](../Topic/CDC::FillPath.md)|Cierre las figuras abiertas en la ruta de acceso actual y rellenan el interior de la ruta de acceso con el modo actual de pincel y de polígono\-relleno.|  
|[CDC::FillRect](../Topic/CDC::FillRect.md)|Rellena un rectángulo determinado mediante un pincel concreto.|  
|[CDC::FillRgn](../Topic/CDC::FillRgn.md)|Rellena una región concreta con el pincel especificado.|  
|[CDC::FillSolidRect](../Topic/CDC::FillSolidRect.md)|rellena un rectángulo con un color sólido.|  
|[CDC::FlattenPath](../Topic/CDC::FlattenPath.md)|Transforma cualquier curva en la ruta seleccionada en el contexto actual del dispositivo, y activa cada curva en una secuencia de líneas.|  
|[CDC::FloodFill](../Topic/CDC::FloodFill.md)|Rellena un área con el pincel actual.|  
|[CDC::FrameRect](../Topic/CDC::FrameRect.md)|Dibuja un borde alrededor de un rectángulo.|  
|[CDC::FrameRgn](../Topic/CDC::FrameRgn.md)|Dibuja un borde alrededor de una región concreta utilizando un pincel.|  
|[CDC::FromHandle](../Topic/CDC::FromHandle.md)|Devuelve un puntero a un objeto de `CDC` cuando se le asigna un identificador a un contexto de dispositivo.  Si un objeto de `CDC` no se asocia al identificador, se crea y se adjunta un objeto temporal de `CDC` .|  
|[CDC::GetArcDirection](../Topic/CDC::GetArcDirection.md)|Devuelve la dirección actual del arco para el contexto del dispositivo.|  
|[CDC::GetAspectRatioFilter](../Topic/CDC::GetAspectRatioFilter.md)|Recupera el valor del filtro actual de la relación de aspecto.|  
|[CDC::GetBkColor](../Topic/CDC::GetBkColor.md)|recupera el color de fondo actual.|  
|[CDC::GetBkMode](../Topic/CDC::GetBkMode.md)|Recupera el modo de fondo.|  
|[CDC::GetBoundsRect](../Topic/CDC::GetBoundsRect.md)|Devuelve el rectángulo delimitador pendiente actual para el contexto especificado del dispositivo.|  
|[CDC::GetBrushOrg](../Topic/CDC::GetBrushOrg.md)|Recupera el origen del pincel actual.|  
|[CDC::GetCharABCWidths](../Topic/CDC::GetCharABCWidths.md)|Recupera los anchos, en unidades lógicas, caracteres consecutivos en un intervalo determinado de la fuente actual.|  
|[CDC::GetCharABCWidthsI](../Topic/CDC::GetCharABCWidthsI.md)|Recupera los anchos, en unidades lógicas, de índices consecutivos de glifo en un intervalo especificado de fuentes TrueType actual.|  
|[CDC::GetCharacterPlacement](../Topic/CDC::GetCharacterPlacement.md)|Recupera distintos tipos de información en una cadena de caracteres.|  
|[CDC::GetCharWidth](../Topic/CDC::GetCharWidth.md)|Recupera los anchos en fracciones de caracteres consecutivos en un intervalo determinado de la fuente actual.|  
|[CDC::GetCharWidthI](../Topic/CDC::GetCharWidthI.md)|Recupera los anchos, en coordenadas lógicas, de los índices consecutivos de glifo en un intervalo especificado de la fuente actual.|  
|[CDC::GetClipBox](../Topic/CDC::GetClipBox.md)|Recupera las dimensiones del rectángulo delimitador más estricto sobre el límite actual de recorte.|  
|[CDC::GetColorAdjustment](../Topic/CDC::GetColorAdjustment.md)|Recupera los valores de ajuste de color para el contexto del dispositivo.|  
|[CDC::GetCurrentBitmap](../Topic/CDC::GetCurrentBitmap.md)|Devuelve un puntero al objeto seleccionado actualmente de `CBitmap` .|  
|[CDC::GetCurrentBrush](../Topic/CDC::GetCurrentBrush.md)|Devuelve un puntero al objeto seleccionado actualmente de `CBrush` .|  
|[CDC::GetCurrentFont](../Topic/CDC::GetCurrentFont.md)|Devuelve un puntero al objeto seleccionado actualmente de `CFont` .|  
|[CDC::GetCurrentPalette](../Topic/CDC::GetCurrentPalette.md)|Devuelve un puntero al objeto seleccionado actualmente de `CPalette` .|  
|[CDC::GetCurrentPen](../Topic/CDC::GetCurrentPen.md)|Devuelve un puntero al objeto seleccionado actualmente de `CPen` .|  
|[CDC::GetCurrentPosition](../Topic/CDC::GetCurrentPosition.md)|Recupera la posición actual del lápiz \(en coordenadas lógicas\).|  
|[CDC::GetDCBrushColor](../Topic/CDC::GetDCBrushColor.md)|Recupera el pincel actual color.|  
|[CDC::GetDCPenColor](../Topic/CDC::GetDCPenColor.md)|Recupera el color del lápiz actual.|  
|[CDC::GetDeviceCaps](../Topic/CDC::GetDeviceCaps.md)|Recupera una clase especificada de información específica del dispositivo sobre las capacidades de un dispositivo de pantalla especificado.|  
|[CDC::GetFontData](../Topic/CDC::GetFontData.md)|Recupera información de medida de un archivo de fuente escalable.  Información a recuperar se identifica especificando un desplazamiento en el archivo de fuente y la longitud de la información para devolver.|  
|[CDC::GetFontLanguageInfo](../Topic/CDC::GetFontLanguageInfo.md)|Devuelve información sobre la fuente seleccionado para el contexto especificado de la pantalla.|  
|[CDC::GetGlyphOutline](../Topic/CDC::GetGlyphOutline.md)|Recupera la curva o mapa de bits de esquema por un carácter de contorno en la fuente actual.|  
|[CDC::GetGraphicsMode](../Topic/CDC::GetGraphicsMode.md)|Recupera el modo de gráficos actual para el contexto especificado del dispositivo.|  
|[CDC::GetHalftoneBrush](../Topic/CDC::GetHalftoneBrush.md)|Recupera un pincel de semitono.|  
|[CDC::GetKerningPairs](../Topic/CDC::GetKerningPairs.md)|Recupera el carácter que interletra pares para la fuente que está actualmente seleccionado en el contexto especificado del dispositivo.|  
|[CDC::GetLayout](../Topic/CDC::GetLayout.md)|Recupera el diseño de un contexto de dispositivo \(DC\).  El diseño puede ser de izquierda a derecha \(valor predeterminado\) o de derecha a izquierda \(reflejado\).|  
|[CDC::GetMapMode](../Topic/CDC::GetMapMode.md)|Recupera el modo actual de asignación.|  
|[CDC::GetMiterLimit](../Topic/CDC::GetMiterLimit.md)|Devuelve el límite del ángulo del contexto del dispositivo.|  
|[CDC::GetNearestColor](../Topic/CDC::GetNearestColor.md)|Recupera el color lógico más próximo al color lógico especificado que el dispositivo dado puede representar.|  
|[CDC::GetOutlineTextMetrics](../Topic/CDC::GetOutlineTextMetrics.md)|Recupera la información de la medida de fuentes para las fuentes truetype.|  
|[CDC::GetOutputCharWidth](../Topic/CDC::GetOutputCharWidth.md)|Recupera los anchos de caracteres individuales de un grupo consecutivo de caracteres de la fuente actual utilizando el contexto del dispositivo de salida.|  
|[CDC::GetOutputTabbedTextExtent](../Topic/CDC::GetOutputTabbedTextExtent.md)|Calcula el ancho y el alto de una cadena de caracteres en el contexto del dispositivo de salida.|  
|[CDC::GetOutputTextExtent](../Topic/CDC::GetOutputTextExtent.md)|Calcula el ancho y el alto de una línea de texto en el contexto del dispositivo de salida con la fuente actual para determinar las dimensiones.|  
|[CDC::GetOutputTextMetrics](../Topic/CDC::GetOutputTextMetrics.md)|Recupera las métricas para la fuente actual del contexto del dispositivo de salida.|  
|[CDC::GetPath](../Topic/CDC::GetPath.md)|Recupera las coordenadas que definen los extremos de líneas y los puntos de control de curvas encontrados en la ruta que selecciona en el contexto del dispositivo.|  
|[CDC::GetPixel](../Topic/CDC::GetPixel.md)|Recupera el valor de color RGB de píxel en el punto especificado.|  
|[CDC::GetPolyFillMode](../Topic/CDC::GetPolyFillMode.md)|Recupera el modo actual de polígono\-relleno.|  
|[CDC::GetROP2](../Topic/CDC::GetROP2.md)|Recupera el modo actual del gráfico.|  
|[CDC::GetSafeHdc](../Topic/CDC::GetSafeHdc.md)|Devuelve [CDC::m\_hDC](../Topic/CDC::m_hDC.md), el contexto del dispositivo de salida.|  
|[CDC::GetStretchBltMode](../Topic/CDC::GetStretchBltMode.md)|Recupera el modo mapa de bits\-que ajusta actual.|  
|[CDC::GetTabbedTextExtent](../Topic/CDC::GetTabbedTextExtent.md)|Calcula el ancho y el alto de una cadena de caracteres en el contexto de dispositivo del atributo.|  
|[CDC::GetTextAlign](../Topic/CDC::GetTextAlign.md)|recupera los indicadores de alineación de texto.|  
|[CDC::GetTextCharacterExtra](../Topic/CDC::GetTextCharacterExtra.md)|Recupera el valor actual de la cantidad de espacio de intercharacter.|  
|[CDC::GetTextColor](../Topic/CDC::GetTextColor.md)|Recupera el color del texto actual.|  
|[CDC::GetTextExtent](../Topic/CDC::GetTextExtent.md)|Calcula el ancho y el alto de una línea de texto en el contexto del dispositivo de atributo utilizando la fuente actual para determinar las dimensiones.|  
|[CDC::GetTextExtentExPointI](../Topic/CDC::GetTextExtentExPointI.md)|Recupera el número de caracteres de una cadena especificada que se ajusta a un espacio especificado y rellena una matriz con la extensión de texto para cada uno de esos caracteres.|  
|[CDC::GetTextExtentPointI](../Topic/CDC::GetTextExtentPointI.md)|Recupera el ancho y alto de matriz de índices de glifo.|  
|[CDC::GetTextFace](../Topic/CDC::GetTextFace.md)|Copia el nombre de tipo de letra de la fuente actual en un búfer como cadena terminada en null.|  
|[CDC::GetTextMetrics](../Topic/CDC::GetTextMetrics.md)|Recupera las métricas para la fuente actual del contexto de dispositivo del atributo.|  
|[CDC::GetViewportExt](../Topic/CDC::GetViewportExt.md)|Recupera el x y las y\-extensiones de la ventanilla.|  
|[CDC::GetViewportOrg](../Topic/CDC::GetViewportOrg.md)|Recupera las coordenadas x e y del origen de la ventanilla.|  
|[CDC::GetWindow](../Topic/CDC::GetWindow.md)|Devuelve la ventana asociada al contexto del dispositivo de pantalla.|  
|[CDC::GetWindowExt](../Topic/CDC::GetWindowExt.md)|Recupera el x y las y\-extensiones de la ventana asociada.|  
|[CDC::GetWindowOrg](../Topic/CDC::GetWindowOrg.md)|Recupera las coordenadas x e y del origen de la ventana asociada.|  
|[CDC::GetWorldTransform](../Topic/CDC::GetWorldTransform.md)|Recupera la transformación actual de página\-espacio de mundo\-espacio.|  
|[CDC::GradientFill](../Topic/CDC::GradientFill.md)|Rellena las estructuras del rectángulo y de triángulos con color gradating.|  
|[CDC::GrayString](../Topic/CDC::GrayString.md)|Texto \(atenuado\) atenuado de dibuja en la ubicación especificada.|  
|[CDC::HIMETRICtoDP](../Topic/CDC::HIMETRICtoDP.md)|convierte las unidades de **HIMETRIC** en unidades.|  
|[CDC::HIMETRICtoLP](../Topic/CDC::HIMETRICtoLP.md)|Convierte las unidades de **HIMETRIC** en unidades lógicas.|  
|[CDC::IntersectClipRect](../Topic/CDC::IntersectClipRect.md)|Crea una nueva región de recorte formando la intersección de la región actual y un rectángulo.|  
|[CDC::InvertRect](../Topic/CDC::InvertRect.md)|Invierte el contenido de un rectángulo.|  
|[CDC::InvertRgn](../Topic/CDC::InvertRgn.md)|Invierte los colores de una región.|  
|[CDC::IsPrinting](../Topic/CDC::IsPrinting.md)|Determina si el contexto de dispositivo se utiliza para imprimir.|  
|[CDC::LineTo](../Topic/CDC::LineTo.md)|Dibuja una línea de la posición actual hasta, pero no incluidas, un punto.|  
|[CDC::LPtoDP](../Topic/CDC::LPtoDP.md)|Convierte las unidades lógicas de unidades.|  
|[CDC::LPtoHIMETRIC](../Topic/CDC::LPtoHIMETRIC.md)|Convierte las unidades lógicas de unidades de **HIMETRIC** .|  
|[CDC::MaskBlt](../Topic/CDC::MaskBlt.md)|Combina los datos de color de mapas de bits de origen y de destino utilizando la operación especificada de máscara y la trama.|  
|[CDC::ModifyWorldTransform](../Topic/CDC::ModifyWorldTransform.md)|Cambia la transformación universal para un contexto de dispositivo mediante el modo especificado.|  
|[CDC::MoveTo](../Topic/CDC::MoveTo.md)|Mueve la posición actual.|  
|[CDC::OffsetClipRgn](../Topic/CDC::OffsetClipRgn.md)|Mueve la del dispositivo dado.|  
|[CDC::OffsetViewportOrg](../Topic/CDC::OffsetViewportOrg.md)|Modifica el origen de la ventanilla en relación con las coordenadas del origen actual de la ventanilla.|  
|[CDC::OffsetWindowOrg](../Topic/CDC::OffsetWindowOrg.md)|Modifica el origen de ventana en relación con las coordenadas del origen de ventana actual.|  
|[CDC::PaintRgn](../Topic/CDC::PaintRgn.md)|Rellena una región con el pincel seleccionado.|  
|[CDC::PatBlt](../Topic/CDC::PatBlt.md)|Crear una configuración de bits.|  
|[CDC::Pie](../Topic/CDC::Pie.md)|Dibuja una cuña empanada\-formada.|  
|[CDC::PlayMetaFile](../Topic/CDC::PlayMetaFile.md)|Reproduce el contenido de metarchivo especificado en el dispositivo especificado.  La versión mejorada de `PlayMetaFile` muestra la imagen almacenada en el metarchivo especificado de ampliar\-formato.  El metarchivo se puede reproducir cualquier número de veces.|  
|[CDC::PlgBlt](../Topic/CDC::PlgBlt.md)|Realiza una transferencia de bloque de bits de los bits de los datos de color del rectángulo especificado en el contexto del dispositivo de origen al paralelogramo especificado en el contexto determinado del dispositivo.|  
|[CDC::PolyBezier](../Topic/CDC::PolyBezier.md)|Dibuja una o varias curvas spline de Bzier.  Se utiliza ni se actualiza la posición actual ni.|  
|[CDC::PolyBezierTo](../Topic/CDC::PolyBezierTo.md)|Dibuja una o varias curvas spline de Bzier, y mueve la posición actual al punto final de la curva spline última de Bzier.|  
|[CDC::PolyDraw](../Topic/CDC::PolyDraw.md)|Dibuja un conjunto de segmentos de líneas y curvas spline de Bzier.  Esta función actualiza la posición actual.|  
|[CDC::Polygon](../Topic/CDC::Polygon.md)|Dibuja un polígono dos que constan de o más señala \(los vértices\) conectados por líneas.|  
|[CDC::Polyline](../Topic/CDC::Polyline.md)|Dibuja un conjunto de segmentos de línea que conectan los puntos especificados.|  
|[CDC::PolylineTo](../Topic/CDC::PolylineTo.md)|Dibuja una o más líneas rectas y mueve la posición actual al punto final de la última línea.|  
|[CDC::PolyPolygon](../Topic/CDC::PolyPolygon.md)|Cree dos o más polígonos que se rellenan mediante el modo actual de polígono\-relleno.  Los polígonos pueden ser disjuntos o se pueden superponer.|  
|[CDC::PolyPolyline](../Topic/CDC::PolyPolyline.md)|Dibuja la serie múltiple de segmentos de línea conectados.  La posición actual no se utiliza ni actualizado por esta función.|  
|[CDC::PtVisible](../Topic/CDC::PtVisible.md)|Especifica si el punto especificado está dentro de la zona de recorte.|  
|[CDC::RealizePalette](../Topic/CDC::RealizePalette.md)|Asigna entradas de la paleta de la paleta lógica actual a la tabla del sistema.|  
|[CDC::Rectangle](../Topic/CDC::Rectangle.md)|Dibuja un rectángulo utilizando el lápiz actual y lo rellena con el pincel actual.|  
|[CDC::RectVisible](../Topic/CDC::RectVisible.md)|Determina si cualquier parte del rectángulo especificado se encuentra dentro de la zona de recorte.|  
|[CDC::ReleaseAttribDC](../Topic/CDC::ReleaseAttribDC.md)|Libera `m_hAttribDC`, el contexto de dispositivo del atributo.|  
|[CDC::ReleaseOutputDC](../Topic/CDC::ReleaseOutputDC.md)|Libera `m_hDC`, el contexto del dispositivo de salida.|  
|[CDC::ResetDC](../Topic/CDC::ResetDC.md)|Actualiza el contexto del dispositivo de `m_hAttribDC` .|  
|[CDC::RestoreDC](../Topic/CDC::RestoreDC.md)|Restablece el contexto del dispositivo a un estado anterior guardado con `SaveDC`.|  
|[CDC::RoundRect](../Topic/CDC::RoundRect.md)|Dibuja un rectángulo con esquinas redondeadas mediante el lápiz actual y rellenas mediante el pincel actual.|  
|[CDC::SaveDC](../Topic/CDC::SaveDC.md)|Guarda el estado actual del contexto del dispositivo.|  
|[CDC::ScaleViewportExt](../Topic/CDC::ScaleViewportExt.md)|Modifica la extensión de ventanilla en relación con los valores actuales.|  
|[CDC::ScaleWindowExt](../Topic/CDC::ScaleWindowExt.md)|Modifica las extensiones de ventana en relación con los valores actuales.|  
|[CDC::ScrollDC](../Topic/CDC::ScrollDC.md)|Desplaza un rectángulo de bits horizontal y verticalmente.|  
|[CDC::SelectClipPath](../Topic/CDC::SelectClipPath.md)|Selecciona la ruta actual como zona de recorte para el contexto de dispositivo, combinando la nueva región con cualquier zona de recorte existente utilizando el modo especificado.|  
|[CDC::SelectClipRgn](../Topic/CDC::SelectClipRgn.md)|Combina la región determinada a la zona de recorte actual utilizando el modo especificado.|  
|[CDC::SelectObject](../Topic/CDC::SelectObject.md)|Seleccione un objeto de dibujo de GDI como un lápiz.|  
|[CDC::SelectPalette](../Topic/CDC::SelectPalette.md)|selecciona la paleta lógica.|  
|[CDC::SelectStockObject](../Topic/CDC::SelectStockObject.md)|Selecciona una de lápices, de los pinceles, o de fuentes comunes predefinidos proporcionadas por Windows.|  
|[CDC::SetAbortProc](../Topic/CDC::SetAbortProc.md)|Establece una función de devolución de llamada programador\-proporcionada que Windows llame a si un trabajo de impresión debe estar anulado.|  
|[CDC::SetArcDirection](../Topic/CDC::SetArcDirection.md)|Establece la dirección del gráfico que se utilizará para el arco y el rectángulo funciona.|  
|[CDC::SetAttribDC](../Topic/CDC::SetAttribDC.md)|Establece `m_hAttribDC`, el contexto de dispositivo del atributo.|  
|[CDC::SetBkColor](../Topic/CDC::SetBkColor.md)|establece el color de fondo actual.|  
|[CDC::SetBkMode](../Topic/CDC::SetBkMode.md)|Establece el modo de fondo.|  
|[CDC::SetBoundsRect](../Topic/CDC::SetBoundsRect.md)|Controla la acumulación de información del rectángulo delimitador para el contexto especificado del dispositivo.|  
|[CDC::SetBrushOrg](../Topic/CDC::SetBrushOrg.md)|Especifica el origen del pincel siguiente seleccionado en un contexto de dispositivo.|  
|[CDC::SetColorAdjustment](../Topic/CDC::SetColorAdjustment.md)|Establece los valores de ajuste de color para el contexto de dispositivo mediante los valores especificados.|  
|[CDC::SetDCBrushColor](../Topic/CDC::SetDCBrushColor.md)|Establece el pincel actual color.|  
|[CDC::SetDCPenColor](../Topic/CDC::SetDCPenColor.md)|Establece el color del lápiz actual.|  
|[CDC::SetGraphicsMode](../Topic/CDC::SetGraphicsMode.md)|Establece el modo de gráficos actual para el contexto especificado del dispositivo.|  
|[CDC::SetLayout](../Topic/CDC::SetLayout.md)|Cambia el diseño de un contexto de dispositivo \(DC\).|  
|[CDC::SetMapMode](../Topic/CDC::SetMapMode.md)|Establece el modo actual de asignación.|  
|[CDC::SetMapperFlags](../Topic/CDC::SetMapperFlags.md)|Modifica el algoritmo que el asignador de la fuente utiliza cuando asigna fuentes lógicas fuentes físicas.|  
|[CDC::SetMiterLimit](../Topic/CDC::SetMiterLimit.md)|Establece el límite de la longitud del ángulo combinaciones para el contexto del dispositivo.|  
|[CDC::SetOutputDC](../Topic/CDC::SetOutputDC.md)|Establece `m_hDC`, el contexto del dispositivo de salida.|  
|[CDC::SetPixel](../Topic/CDC::SetPixel.md)|Establece el píxel en el punto especificado a la aproximación más parecida al color especificado.|  
|[CDC::SetPixelV](../Topic/CDC::SetPixelV.md)|Establece el píxel en las coordenadas especificadas a la aproximación más parecida al color especificado.  `SetPixelV` es más rápido que `SetPixel` porque no debe devolver el valor de color de punto pintado realmente.|  
|[CDC::SetPolyFillMode](../Topic/CDC::SetPolyFillMode.md)|Establece el modo de polígono\-relleno.|  
|[CDC::SetROP2](../Topic/CDC::SetROP2.md)|Establece el modo actual del gráfico.|  
|[CDC::SetStretchBltMode](../Topic/CDC::SetStretchBltMode.md)|Establece el modo mapa de bits\-que ajusta.|  
|[CDC::SetTextAlign](../Topic/CDC::SetTextAlign.md)|establece los indicadores de alineación de texto.|  
|[CDC::SetTextCharacterExtra](../Topic/CDC::SetTextCharacterExtra.md)|Establece la cantidad de espacio de intercharacter.|  
|[CDC::SetTextColor](../Topic/CDC::SetTextColor.md)|Establece el color de texto.|  
|[CDC::SetTextJustification](../Topic/CDC::SetTextJustification.md)|Agregue el espacio a caracteres de interrupción en una cadena.|  
|[CDC::SetViewportExt](../Topic/CDC::SetViewportExt.md)|Establece el x y las y\-extensiones de la ventanilla.|  
|[CDC::SetViewportOrg](../Topic/CDC::SetViewportOrg.md)|Establece el origen de la ventanilla.|  
|[CDC::SetWindowExt](../Topic/CDC::SetWindowExt.md)|Establece el x y las y\-extensiones de la ventana asociada.|  
|[CDC::SetWindowOrg](../Topic/CDC::SetWindowOrg.md)|Establece el origen de ventana de contexto del dispositivo.|  
|[CDC::SetWorldTransform](../Topic/CDC::SetWorldTransform.md)|Establece la transformación actual de página\-espacio de mundo\-espacio.|  
|[CDC::StartDoc](../Topic/CDC::StartDoc.md)|Informa al controlador de dispositivo que un nuevo trabajo de impresión se está iniciando.|  
|[CDC::StartPage](../Topic/CDC::StartPage.md)|Informa al controlador de dispositivo que una nueva página está iniciando.|  
|[CDC::StretchBlt](../Topic/CDC::StretchBlt.md)|Mueve un mapa de bits de un rectángulo de origen y el dispositivo a un rectángulo de destino, estirando o comprima el mapa de bits en caso necesario para ajustarse a las dimensiones del rectángulo de destino.|  
|[CDC::StrokeAndFillPath](../Topic/CDC::StrokeAndFillPath.md)|Cierre las figuras abierto en una ruta, pulso el contorno de la ruta de acceso con el lápiz actual, y rellene la interior mediante el pincel actual.|  
|[CDC::StrokePath](../Topic/CDC::StrokePath.md)|Representa la ruta de acceso especificada utilizando el lápiz actual.|  
|[CDC::TabbedTextOut](../Topic/CDC::TabbedTextOut.md)|Escribe una cadena de caracteres en una ubicación especificada, pestañas que expanda con los valores especificados en una matriz de posiciones de la interrupción de tabulación.|  
|[CDC::TextOut](../Topic/CDC::TextOut.md)|Escribe una cadena de caracteres en una ubicación especificada mediante la fuente seleccionado actualmente.|  
|[CDC::TransparentBlt](../Topic/CDC::TransparentBlt.md)|Transfiere un bloque de bits de los datos de color de contexto especificado del dispositivo de origen en un contexto del dispositivo de destino, genera un transparente en el color especificado en la transferencia.|  
|[CDC::UpdateColors](../Topic/CDC::UpdateColors.md)|Actualiza el área cliente del contexto de dispositivo coincidir los colores actuales en el área cliente a la tabla del sistema de por píxel.|  
|[CDC::WidenPath](../Topic/CDC::WidenPath.md)|Vuelve a definir la ruta actual como el área que se pinta si la ruta se frotada bastará con el lápiz seleccionado actualmente en el contexto del dispositivo.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDC::operator HDC](../Topic/CDC::operator%20HDC.md)|Recupera el identificador de contexto del dispositivo.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDC::m\_hAttribDC](../Topic/CDC::m_hAttribDC.md)|El contexto de atributo\-dispositivo utilizado por este objeto de `CDC` .|  
|[CDC::m\_hDC](../Topic/CDC::m_hDC.md)|El contexto del dispositivo de salida utilizado por este objeto de `CDC` .|  
  
## Comentarios  
 El objeto de `CDC` proporciona funciones miembro para trabajar con un contexto de dispositivo, como una pantalla o una impresora, así como los miembros para trabajar con un contexto de presentación asociado al área cliente de una ventana.  
  
 Haga todo el gráfico con las funciones miembro de un objeto de `CDC` .  La clase proporciona funciones miembro para las operaciones de dispositivo\-contexto, trabajando con las herramientas de dibujo, la selección con seguridad de tipos de objeto de la \(GDI\) interfaz de dispositivo gráfico, y trabajando con colores y paletas.  También proporciona funciones miembro para los atributos del gráfico a recoger y de valor, asignación, ejecute la ventanilla, ejecute con la extensión de la ventana, convertir las coordenadas, trabajando con las regiones, recorte, las líneas del gráfico, y las formas simples de dibujo, elipses, y los polígonos.  Las funciones miembro también se proporcionan para dibujar texto, trabajando fuentes, con escape de impresora, el desplazamiento, y reproducir metarchivos.  
  
 Para utilizar un objeto de `CDC` , construyalo, y llame a su miembro funciona que las funciones Windows en paralelo que utilizan contextos de dispositivo.  
  
> [!NOTE]
>  En Windows 95 \/98, todas las coordenadas de la pantalla se limitan a 16 bits.  Por consiguiente, `int` pasado a una función miembro de `CDC` debe mentir en el intervalo de – 32768 a 32767.  
  
 Para uso concreto, la biblioteca Microsoft Foundation Class proporciona varias clases derivadas de `CDC` .  `CPaintDC` encapsula llamadas a `BeginPaint` y a `EndPaint`.  `CClientDC` administra un contexto de presentación asociado al área cliente de una ventana.  `CWindowDC` administra un contexto de presentación asociado a una ventana completa, incluido el cuadro y controles.  `CMetaFileDC` asocia un contexto de dispositivo a un metarchivo.  
  
 `CDC` proporciona dos funciones miembro, [GetLayout](../Topic/CDC::GetLayout.md) y [SetLayout](../Topic/CDC::SetLayout.md), para invertir el diseño de un contexto de dispositivo, que no hereda el diseño de una ventana.  Este tipo de derecha a izquierda orientación es necesaria para las aplicaciones escritas para las referencias culturales, como el árabe o hebreo, donde no es estándar el diseño de caracteres europea.  
  
 `CDC` contiene dos contextos de dispositivo, [m\_hDC](../Topic/CDC::m_hDC.md) y [m\_hAttribDC](../Topic/CDC::m_hAttribDC.md), que, en la creación de un objeto de `CDC` , el mismo dispositivo.  `CDC` dirige todo el para generar las llamadas de GDI a `m_hDC` y la mayoría de las llamadas de GDI de atributo a `m_hAttribDC`.  \(Un ejemplo de una llamada del atributo es `GetTextColor`, mientras que `SetTextColor` es una llamada de salida.\)  
  
 Por ejemplo, el marco de trabajo usa estos contextos de dos dispositivos para implementar un objeto de `CMetaFileDC` enviar la salida a un metarchivo mientras lee atributos de un dispositivo físico.  la vista previa de impresión se implementa en el marco de manera similar.  También puede utilizar los dos contextos de dispositivo de forma similar en el código específico de la aplicación.  
  
 Hay ocasiones en que puede necesitar información texto\-métrica de los contextos de dispositivo de `m_hDC` y de `m_hAttribDC` .  Los siguientes pares de funciones proporcionan esta capacidad:  
  
|utiliza el m\_hAttribDC|utiliza el m\_hDC|  
|-----------------------------|-----------------------|  
|[GetTextExtent](../Topic/CDC::GetTextExtent.md)|[GetOutputTextExtent](../Topic/CDC::GetOutputTextExtent.md)|  
|[GetTabbedTextExtent](../Topic/CDC::GetTabbedTextExtent.md)|[GetOutputTabbedTextExtent](../Topic/CDC::GetOutputTabbedTextExtent.md)|  
|[GetTextMetrics](../Topic/CDC::GetTextMetrics.md)|[GetOutputTextMetrics](../Topic/CDC::GetOutputTextMetrics.md)|  
|[GetCharWidth](../Topic/CDC::GetCharWidth.md)|[GetOutputCharWidth](../Topic/CDC::GetOutputCharWidth.md)|  
  
 Para obtener más información sobre `CDC`, vea [Contextos de dispositivo](../../mfc/device-contexts.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDC`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CPaintDC Class](../../mfc/reference/cpaintdc-class.md)   
 [CWindowDC Class](../../mfc/reference/cwindowdc-class.md)   
 [CClientDC Class](../../mfc/reference/cclientdc-class.md)   
 [CMetaFileDC Class](../../mfc/reference/cmetafiledc-class.md)