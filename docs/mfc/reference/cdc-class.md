---
title: CDC (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDC
dev_langs:
- C++
helpviewer_keywords:
- Windows [C++], device contexts
- Windows 95 [C++], screen coordinates
- device contexts [C++], CDC class
- screen coordinates in device contexts
- coordinates in Windows 95/98 [C++]
- Windows 98 [C++], screen coordinates
- CDC class
ms.assetid: 715b3334-cb2b-4c9c-8067-02eb7c66c8b2
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 80ccd3f8bed6bd74e22d4db5e176ee50528d3187
ms.lasthandoff: 02/24/2017

---
# <a name="cdc-class"></a>CDC (clase)
Define una clase de objetos en el contexto del dispositivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDC : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDC::CDC](#cdc)|Construye un objeto `CDC`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDC::AbortDoc](#abortdoc)|Finaliza el trabajo de impresión actual, borrar todo lo que la aplicación se ha escrito en el dispositivo desde la última llamada de la `StartDoc` función miembro.|  
|[CDC::AbortPath](#abortpath)|Cierra y descarta las rutas de acceso en el contexto de dispositivo.|  
|[CDC::AddMetaFileComment](#addmetafilecomment)|Copia el comentario de un búfer en un metarchivo de formato mejorado.|  
|[CDC::AlphaBlend](#alphablend)|Muestra los mapas de bits transparentes o semitransparentes píxeles.|  
|[CDC::AngleArc](#anglearc)|Dibuja un segmento de línea y un arco y mueve la posición actual hasta el punto final del arco.|  
|[CDC::ARC](#arc)|Dibuja un arco elíptico.|  
|[CDC::ArcTo](#arcto)|Dibuja un arco elíptico. Esta función es similar a `Arc`, excepto en que se actualiza la posición actual.|  
|[CDC::Attach](#attach)|Asocia un contexto de dispositivo de Windows a este `CDC` objeto.|  
|[CDC:: beginpath](#beginpath)|Abre un corchete de cierre de la ruta de acceso en el contexto de dispositivo.|  
|[CDC::BitBlt](#bitblt)|Copia un mapa de bits de un contexto de dispositivo especificado.|  
|[CDC::Chord](#chord)|Dibuja una cuerda (una figura cerrada limitada por la intersección de una elipse y un segmento de línea).|  
|[CDC::CloseFigure](#closefigure)|Cierra una figura abierta en una ruta de acceso.|  
|[CDC::CreateCompatibleDC](#createcompatibledc)|Crea un contexto de dispositivo de memoria que sea compatible con otro contexto de dispositivo. Puede usarla para preparar las imágenes en memoria.|  
|[CDC::CreateDC](#createdc)|Crea un contexto de dispositivo para un dispositivo específico.|  
|[CDC::CreateIC](#createic)|Crea un contexto de información para un dispositivo específico. Esto proporciona una forma rápida de obtener información sobre el dispositivo sin crear un contexto de dispositivo.|  
|[CDC::DeleteDC](#deletedc)|Elimina el contexto de dispositivo de Windows asociado a esta `CDC` objeto.|  
|[CDC::DeleteTempMap](#deletetempmap)|Llamado por el `CWinApp` controlador de tiempo de inactividad para eliminar cualquier temporal `CDC` objeto creado por `FromHandle`. También se desasocia del contexto de dispositivo.|  
|[CDC::Detach](#detach)|Desasocia el contexto de dispositivo de Windows desde este `CDC` objeto.|  
|[CDC::DPtoHIMETRIC](#dptohimetric)|Convierte las unidades de dispositivo en **HIMETRIC** unidades.|  
|[CDC::DPtoLP](#dptolp)|Convierte las unidades de dispositivo en unidades lógicas.|  
|[CDC::Draw3dRect](#draw3drect)|Dibuja un rectángulo tridimensional.|  
|[CDC::DrawDragRect](#drawdragrect)|Borra y vuelve a dibujar un rectángulo que se arrastra.|  
|[CDC::DrawEdge](#drawedge)|Dibuja los bordes de un rectángulo.|  
|[CDC::DrawEscape](#drawescape)|Accesos a funciones de una pantalla de vídeo que no están directamente disponibles a través de la interfaz de dispositivo gráfico (GDI) de dibujo.|  
|[CDC::DrawFocusRect](#drawfocusrect)|Dibuja un rectángulo en el estilo que se utiliza para indicar el foco.|  
|[CDC::DrawFrameControl](#drawframecontrol)|Dibuje un control de marco.|  
|[CDC::DrawIcon](#drawicon)|Dibuja un icono.|  
|[CDC::DrawState](#drawstate)|Muestra una imagen y se aplica un efecto visual para indicar un estado.|  
|[CDC:: DrawText](#drawtext)|Dibuja texto con formato en el rectángulo especificado.|  
|[CDC::DrawTextEx](#drawtextex)|Dibuja texto con formato en el rectángulo especificado mediante formatos adicionales.|  
|[CDC::Ellipse](#ellipse)|Dibuja una elipse.|  
|[CDC::EndDoc](#enddoc)|Finaliza un trabajo de impresión iniciado por el `StartDoc` función miembro.|  
|[CDC::EndPage](#endpage)|Informa al controlador de dispositivo que está finalizando una página.|  
|[CDC::EndPath](#endpath)|Cierra un corchete de cierre de la ruta de acceso y selecciona la ruta de acceso definida por el corchete de cierre en el contexto de dispositivo.|  
|[CDC:: EnumObjects](#enumobjects)|Enumera los lápices y pinceles disponibles en un contexto de dispositivo.|  
|[CDC::escape](#escape)|Permite que las aplicaciones tener acceso a funciones que no están disponibles directamente desde un dispositivo determinado a través de GDI. También permite el acceso a las funciones de escape de Windows. Escape de las llamadas realizadas por una aplicación se convierten y se envían al controlador de dispositivo.|  
|[CDC::ExcludeClipRect](#excludecliprect)|Crea una nueva región de recorte que consta de la región de recorte existente menos el rectángulo especificado.|  
|[CDC::ExcludeUpdateRgn](#excludeupdatergn)|Evita que el dibujo en áreas no válidos de una ventana mediante la exclusión de una región actualizada en la ventana de una región de recorte.|  
|[CDC::ExtFloodFill](#extfloodfill)|Rellena un área con el pincel actual. Proporciona más flexibilidad que la [CDC::FloodFill](#floodfill) función miembro.|  
|[CDC::ExtTextOut](#exttextout)|Escribe una cadena de caracteres dentro de una región rectangular con la fuente seleccionada actualmente.|  
|[CDC::FillPath](#fillpath)|Figuras abiertas en la ruta de acceso actual se cierra y rellena el interior de la ruta de acceso mediante el pincel actual y el modo de relleno de polígono.|  
|[CDC::fillRect](#fillrect)|Rellena un rectángulo con un pincel específico.|  
|[CDC::FillRgn](#fillrgn)|Rellena un área específica con el pincel especificado.|  
|[CDC::FillSolidRect](#fillsolidrect)|Rellena un rectángulo con un color sólido.|  
|[CDC::FlattenPath](#flattenpath)|Transforma las curvas en la ruta seleccionada en el contexto de dispositivo actual y cada curva se convierte en una secuencia de líneas.|  
|[CDC::FloodFill](#floodfill)|Rellena un área con el pincel actual.|  
|[FrameRect](#framerect)|Dibuja un borde alrededor de un rectángulo.|  
|[CDC::FrameRgn](#framergn)|Dibuja un borde alrededor de una región específica con un pincel.|  
|[CDC::FromHandle](#fromhandle)|Devuelve un puntero a un `CDC` objeto cuando se especifica un identificador para un contexto de dispositivo. Si no hay un objeto `CDC` asociado al identificador, se crea y asocia un objeto `CDC` temporal.|  
|[CDC::GetArcDirection](#getarcdirection)|Devuelve la dirección de arco actual para el contexto de dispositivo.|  
|[CDC::GetAspectRatioFilter](#getaspectratiofilter)|Recupera el valor para el filtro de relación de aspecto actual.|  
|[CDC::GetBkColor](#getbkcolor)|Recupera el color de fondo actual.|  
|[CDC::GetBkMode](#getbkmode)|Recupera el modo de segundo plano.|  
|[CDC::GetBoundsRect](#getboundsrect)|Devuelve el rectángulo delimitador acumulado actual para el contexto de dispositivo especificado.|  
|[CDC::GetBrushOrg](#getbrushorg)|Recupera el origen del pincel actual.|  
|[CDC::GetCharABCWidths](#getcharabcwidths)|Recupera el ancho, en unidades lógicas, de caracteres consecutivos de un intervalo determinado de la fuente actual.|  
|[CDC::GetCharABCWidthsI](#getcharabcwidthsi)|Recupera el ancho, en unidades lógicas, de los índices de glifo consecutivos en un intervalo especificado de la fuente TrueType actual.|  
|[CDC::GetCharacterPlacement](#getcharacterplacement)|Recupera varios tipos de información en una cadena de caracteres.|  
|[CDC::GetCharWidth](#getcharwidth)|Recupera el ancho de fracciones de caracteres consecutivos en un intervalo determinado de la fuente actual.|  
|[CDC::GetCharWidthI](#getcharwidthi)|Recupera el ancho, en coordenadas lógicas, de los índices de glifo consecutivos en un intervalo especificado de la fuente actual.|  
|[CDC::GetClipBox](#getclipbox)|Recupera las dimensiones del rectángulo delimitador tightest alrededor del límite de recorte actual.|  
|[CDC::GetColorAdjustment](#getcoloradjustment)|Recupera los valores de ajuste de color para el contexto de dispositivo.|  
|[CDC::GetCurrentBitmap](#getcurrentbitmap)|Devuelve un puntero a la seleccionada actualmente `CBitmap` objeto.|  
|[CDC::GetCurrentBrush](#getcurrentbrush)|Devuelve un puntero a la seleccionada actualmente `CBrush` objeto.|  
|[CDC::GetCurrentFont](#getcurrentfont)|Devuelve un puntero a la seleccionada actualmente `CFont` objeto.|  
|[CDC::GetCurrentPalette](#getcurrentpalette)|Devuelve un puntero a la seleccionada actualmente `CPalette` objeto.|  
|[CDC::GetCurrentPen](#getcurrentpen)|Devuelve un puntero a la seleccionada actualmente `CPen` objeto.|  
|[CDC::GetCurrentPosition](#getcurrentposition)|Recupera la posición actual del lápiz (en coordenadas lógicas).|  
|[CDC::GetDCBrushColor](#getdcbrushcolor)|Recupera el color de pincel actual.|  
|[CDC::GetDCPenColor](#getdcpencolor)|Recupera el color del lápiz actual.|  
|[CDC:: GetDeviceCaps](#getdevicecaps)|Recupera un tipo especificado de información específica del dispositivo acerca de las capacidades del dispositivo de presentación determinado.|  
|[CDC::GetFontData](#getfontdata)|Recupera información de métrica de fuente de un archivo de fuentes escalables. Se identifica la información para recuperar especificando un desplazamiento en el archivo de fuente y la longitud de la información que se devuelve.|  
|[CDC::GetFontLanguageInfo](#getfontlanguageinfo)|Devuelve información acerca de la fuente seleccionada actualmente para el contexto de presentación especificado.|  
|[CDC::GetGlyphOutline](#getglyphoutline)|Recupera la curva de contorno o mapa de bits de un carácter de esquema en la fuente actual.|  
|[CDC::GetGraphicsMode](#getgraphicsmode)|Recupera el modo de gráficos actual para el contexto de dispositivo especificado.|  
|[CDC::GetHalftoneBrush](#gethalftonebrush)|Recupera un pincel de medios tonos.|  
|[CDC::GetKerningPairs](#getkerningpairs)|Recupera el carácter interletraje de pares de la fuente que está seleccionado actualmente en el contexto de dispositivo especificado.|  
|[CDC::GetLayout](#getlayout)|Recupera el diseño de un contexto de dispositivo (DC). El diseño puede ser de izquierda a derecha (valor predeterminado) o de derecha a izquierda (reflejado).|  
|[CDC::GetMapMode](#getmapmode)|Recupera el modo de asignación actual.|  
|[CDC::GetMiterLimit](#getmiterlimit)|Devuelve el límite angular para el contexto de dispositivo.|  
|[CDC::GetNearestColor](#getnearestcolor)|Recupera el color lógico más cercano a un color especificado lógico que represente el dispositivo especificado.|  
|[CDC::GetOutlineTextMetrics](#getoutlinetextmetrics)|Recupera información de métrica de fuente para las fuentes TrueType.|  
|[CDC::GetOutputCharWidth](#getoutputcharwidth)|Recupera el ancho de caracteres individuales de un grupo de caracteres consecutivos de la fuente actual utilizando el contexto de dispositivo de salida.|  
|[CDC::GetOutputTabbedTextExtent](#getoutputtabbedtextextent)|Calcula el ancho y alto de una cadena de caracteres en el contexto de dispositivo de salida.|  
|[CDC::GetOutputTextExtent](#getoutputtextextent)|Calcula el ancho y alto de una línea de texto en el contexto de dispositivo de salida con la fuente actual para determinar las dimensiones.|  
|[CDC::GetOutputTextMetrics](#getoutputtextmetrics)|Recupera las métricas para la fuente actual desde el contexto de dispositivo de salida.|  
|[CDC::getPath](#getpath)|Recupera las coordenadas que definen los extremos de las líneas y los puntos de control de curvas que se encuentra en la ruta de acceso que se ha seleccionado en el contexto de dispositivo.|  
|[CDC::getPixel](#getpixel)|Recupera el valor de color RGB del píxel en el punto especificado.|  
|[CDC::GetPolyFillMode](#getpolyfillmode)|Recupera el modo de relleno de polígono actual.|  
|[CDC::GetROP2](#getrop2)|Recupera el modo de dibujo actual.|  
|[CDC::GetSafeHdc](#getsafehdc)|Devuelve [CDC::m_hDC](#m_hdc), el contexto de dispositivo de salida.|  
|[CDC::GetStretchBltMode](#getstretchbltmode)|Recupera el modo de ajuste de mapa de bits actual.|  
|[CDC::GetTabbedTextExtent](#gettabbedtextextent)|Calcula el ancho y alto de una cadena de caracteres en el contexto de dispositivo de atributo.|  
|[CDC::GetTextAlign](#gettextalign)|Recupera las marcas de alineación de texto.|  
|[CDC::GetTextCharacterExtra](#gettextcharacterextra)|Recupera el valor actual de la cantidad de espaciado entre caracteres en función.|  
|[CDC::GetTextColor](#gettextcolor)|Recupera el color de texto actual.|  
|[CDC::GetTextExtent](#gettextextent)|Calcula el ancho y alto de una línea de texto en el contexto de dispositivo de atributo utilizando la fuente actual para determinar las dimensiones.|  
|[CDC::GetTextExtentExPointI](#gettextextentexpointi)|Recupera el número de caracteres de una cadena especificada que se ajusten a un espacio determinado y rellena una matriz con la extensión del texto para cada uno de esos caracteres.|  
|[CDC::GetTextExtentPointI](#gettextextentpointi)|Recupera el ancho y alto de la matriz especificada de índices de glifo.|  
|[CDC::GetTextFace](#gettextface)|Copia el nombre de tipo de letra de la fuente actual en un búfer como una cadena terminada en null.|  
|[CDC::GetTextMetrics](#gettextmetrics)|Recupera las métricas para la fuente actual desde el contexto de dispositivo de atributo.|  
|[CDC::GetViewportExt](#getviewportext)|Recupera las extensiones x y y de la ventanilla.|  
|[CDC::GetViewportOrg](#getviewportorg)|Recupera las coordenadas x e y del origen de la ventanilla.|  
|[CDC::GetWindow](#getwindow)|Devuelve la ventana asociada con el contexto de dispositivo de presentación.|  
|[CDC::GetWindowExt](#getwindowext)|Recupera las extensiones x y y de la ventana asociada.|  
|[CDC::GetWindowOrg](#getwindoworg)|Recupera las coordenadas x e y del origen de la ventana asociada.|  
|[CDC::GetWorldTransform](#getworldtransform)|Recupera el espacio de mundo actual para la transformación de espacio en la página.|  
|[CDC::GradientFill](#gradientfill)|Rellena estructuras de triángulo y el rectángulo con un color gradating.|  
|[CDC:: graystring](#graystring)|Dibuja atenuado texto (gris) en la ubicación especificada.|  
|[CDC::HIMETRICtoDP](#himetrictodp)|Convierte **HIMETRIC** unidades en unidades del dispositivo.|  
|[CDC::HIMETRICtoLP](#himetrictolp)|Convierte **HIMETRIC** unidades en unidades lógicas.|  
|[CDC::IntersectClipRect](#intersectcliprect)|Crea una nueva región de recorte mediante la intersección de la región actual y un rectángulo.|  
|[CDC::InvertRect](#invertrect)|Invierte el contenido de un rectángulo.|  
|[CDC::InvertRgn](#invertrgn)|Invierte los colores de una región.|  
|[CDC::IsPrinting](#isprinting)|Determina si se está usando el contexto de dispositivo para la impresión.|  
|[CDC::LineTo](#lineto)|Dibuja una línea desde la posición actual hasta, pero no incluido un punto.|  
|[CDC::LPtoDP](#lptodp)|Convierte las unidades lógicas en unidades del dispositivo.|  
|[CDC::LPtoHIMETRIC](#lptohimetric)|Convierte las unidades lógicas en **HIMETRIC** unidades.|  
|[CDC::MaskBlt](#maskblt)|Combina los datos de color para los mapas de bits de origen y destino con la máscara determinada y la operación de trama.|  
|[CDC::ModifyWorldTransform](#modifyworldtransform)|Cambia la transformación universal para un contexto de dispositivo mediante el modo especificado.|  
|[CDC::MoveTo](#moveto)|Mueve la posición actual.|  
|[CDC::OffsetClipRgn](#offsetcliprgn)|Mueve la región de recorte del dispositivo determinado.|  
|[CDC::OffsetViewportOrg](#offsetviewportorg)|Modifica el origen de la ventanilla en relación con las coordenadas del área de visualización de origen actual.|  
|[CDC::OffsetWindowOrg](#offsetwindoworg)|Modifica el origen de la ventana con respecto a las coordenadas del origen de ventana actual.|  
|[CDC::PaintRgn](#paintrgn)|Rellena una región con el pincel seleccionado.|  
|[CDC::PatBlt](#patblt)|Crea un patrón de bits.|  
|[CDC::pie](#pie)|Dibuja una cuña en forma de gráfico circular.|  
|[CDC::PlayMetaFile](#playmetafile)|Reproduce el contenido del metarchivo especificado en el dispositivo especificado. La versión mejorada de `PlayMetaFile` muestra la imagen almacenada en el metarchivo de formato mejorado determinado. Metarchivo se puede reproducir en cualquier número de veces.|  
|[CDC::PlgBlt](#plgblt)|Realiza a una transferencia de bloque de bits de los bits de datos de color desde el rectángulo especificado en el contexto de dispositivo de origen al paralelogramo especificado en el contexto de dispositivo determinado.|  
|[CDC::PolyBezier](#polybezier)|Dibuja curvas spline Bzier uno o más. La posición actual no se utiliza ni se actualiza.|  
|[CDC::PolyBezierTo](#polybezierto)|Dibuja uno o más Bzier b-spline y mueve la posición actual hasta el punto final de la última spline Bzier.|  
|[CDC::PolyDraw](#polydraw)|Dibuja un conjunto de segmentos de líneas y curvas spline de Bzier. Esta función actualiza la posición actual.|  
|[CDC::Polygon](#polygon)|Dibuja un polígono que consta de dos o más puntos (vértices) conectados por líneas.|  
|[CDC::Polyline](#polyline)|Dibuja un conjunto de segmentos de línea que conecta los puntos especificados.|  
|[CDC::PolylineTo](#polylineto)|Dibuja una o varias líneas rectas y mueve la posición actual hasta el punto final de la última línea.|  
|[CDC::PolyPolygon](#polypolygon)|Crea dos o más de los polígonos que se rellenan con el modo de relleno de polígono actual. Los polígonos pueden ser separados o quizá se superpongan.|  
|[CDC::PolyPolyline](#polypolyline)|Dibuja varias series de segmentos de línea conectados. La posición actual no se utiliza ni se actualiza esta función.|  
|[CDC::PtVisible](#ptvisible)|Especifica si el punto especificado está dentro de la región de recorte.|  
|[CDC::RealizePalette](#realizepalette)|Entradas de la paleta de la paleta lógica actual se asigna a la paleta del sistema.|  
|[CDC::Rectangle](#rectangle)|Dibuja un rectángulo con el lápiz y la rellena con el pincel actual.|  
|[CDC::RectVisible](#rectvisible)|Determina si cualquier parte del rectángulo especificado está dentro de la región de recorte.|  
|[CDC::ReleaseAttribDC](#releaseattribdc)|Versiones `m_hAttribDC`, el contexto de dispositivo de atributo.|  
|[CDC::ReleaseOutputDC](#releaseoutputdc)|Versiones `m_hDC`, el contexto de dispositivo de salida.|  
|[CDC::ResetDC](#resetdc)|Las actualizaciones de la `m_hAttribDC` contexto de dispositivo.|  
|[CDC::RestoreDC](#restoredc)|Restaura el contexto de dispositivo a un estado anterior guardado con `SaveDC`.|  
|[CDC::RoundRect](#roundrect)|Dibuja un rectángulo con esquinas redondeadas con el lápiz y la rellena con el pincel actual.|  
|[CDC::SaveDC](#savedc)|Guarda el estado actual del contexto de dispositivo.|  
|[CDC::ScaleViewportExt](#scaleviewportext)|Modifica el alcance de la ventanilla en relación con los valores actuales.|  
|[CDC::ScaleWindowExt](#scalewindowext)|Modifica las extensiones de ventana en relación con los valores actuales.|  
|[CDC::ScrollDC](#scrolldc)|Desplaza un rectángulo de bits horizontal y verticalmente.|  
|[CDC::SelectClipPath](#selectclippath)|Selecciona la ruta de acceso actual como una región de recorte para el contexto de dispositivo, que combina la región nueva con una región de recorte existente utilizando el modo especificado.|  
|[CDC::SelectClipRgn](#selectcliprgn)|Combina la región determinada con la actual región de recorte mediante el modo especificado.|  
|[CDC::SelectObject](#selectobject)|Selecciona un objeto de dibujo GDI como un lápiz.|  
|[CDC::SelectPalette](#selectpalette)|Selecciona la paleta lógica.|  
|[CDC::SelectStockObject](#selectstockobject)|Selecciona uno de los lápices de stock predefinidas, pinceles o las fuentes proporcionadas por Windows.|  
|[CDC:: SETABORTPROC](#setabortproc)|Establece una función de devolución de llamada proporcionada por el programador que Windows se llama si se debe anular un trabajo de impresión.|  
|[CDC::SetArcDirection](#setarcdirection)|Establece la dirección que se utilizará para funciones de arco y el rectángulo de dibujo.|  
|[CDC::SetAttribDC](#setattribdc)|Conjuntos de `m_hAttribDC`, el contexto de dispositivo de atributo.|  
|[CDC::SetBkColor](#setbkcolor)|Establece el color de fondo actual.|  
|[CDC::SetBkMode](#setbkmode)|Establece el modo de segundo plano.|  
|[CDC::SetBoundsRect](#setboundsrect)|Controla la acumulación de información del rectángulo delimitador para el contexto de dispositivo especificado.|  
|[CDC::SetBrushOrg](#setbrushorg)|Especifica el origen para el siguiente pincel seleccionado en un contexto de dispositivo.|  
|[CDC::SetColorAdjustment](#setcoloradjustment)|Establece los valores de ajuste de color para el contexto de dispositivo con los valores especificados.|  
|[CDC::SetDCBrushColor](#setdcbrushcolor)|Establece el color de pincel actual.|  
|[CDC::SetDCPenColor](#setdcpencolor)|Establece el color del lápiz actual.|  
|[CDC::SetGraphicsMode](#setgraphicsmode)|Establece el modo de gráficos actual para el contexto de dispositivo especificado.|  
|[CDC::SetLayout](#setlayout)|Cambia el diseño de un contexto de dispositivo (DC).|  
|[CDC::SetMapMode](#setmapmode)|Establece el modo de asignación actual.|  
|[CDC::SetMapperFlags](#setmapperflags)|Modifica el algoritmo que el asignador de fuentes que se utiliza cuando se asigna las fuentes lógicas fuentes físicas.|  
|[CDC::SetMiterLimit](#setmiterlimit)|Establece el límite para la longitud de uniones angulares para el contexto de dispositivo.|  
|[CDC::SetOutputDC](#setoutputdc)|Conjuntos de `m_hDC`, el contexto de dispositivo de salida.|  
|[CDC::SetPixel](#setpixel)|Establece el píxel en el punto especificado para la aproximación más cercana del color especificado.|  
|[CDC::SetPixelV](#setpixelv)|Establece el píxel en las coordenadas especificadas para la aproximación más cercana del color especificado. `SetPixelV`es más rápido que `SetPixel` porque no se necesita devolver el valor de color del punto dibujado en realidad.|  
|[CDC::SetPolyFillMode](#setpolyfillmode)|Establece el modo de relleno de polígono.|  
|[CDC::SetROP2](#setrop2)|Establece el modo de dibujo actual.|  
|[CDC::SetStretchBltMode](#setstretchbltmode)|Establece el modo de ajuste de mapa de bits.|  
|[CDC::SetTextAlign](#settextalign)|Establece las marcas de alineación de texto.|  
|[CDC::SetTextCharacterExtra](#settextcharacterextra)|Establece la cantidad de espaciado entre caracteres en función.|  
|[CDC::SetTextColor](#settextcolor)|Establece el color del texto.|  
|[CDC::SetTextJustification](#settextjustification)|Agrega el espacio para los caracteres de salto en una cadena.|  
|[CDC::SetViewportExt](#setviewportext)|Establece las extensiones x y y de la ventanilla.|  
|[CDC::SetViewportOrg](#setviewportorg)|Establece el origen de la ventanilla.|  
|[CDC::SetWindowExt](#setwindowext)|Establece las extensiones x y y de la ventana asociada.|  
|[CDC::SetWindowOrg](#setwindoworg)|Establece el origen del contexto de dispositivo de la ventana.|  
|[CDC::SetWorldTransform](#setworldtransform)|Establece el espacio de mundo actual para la transformación de espacio en la página.|  
|[CDC::StartDoc](#startdoc)|Informa al controlador de dispositivo que se está iniciando un nuevo trabajo de impresión.|  
|[CDC::StartPage](#startpage)|Informa al controlador de dispositivo que se está iniciando una nueva página.|  
|[CDC::StretchBlt](#stretchblt)|Mueve un mapa de bits de un rectángulo de origen y un dispositivo en un rectángulo de destino, estirando o comprimiendo el mapa de bits si es necesario para ajustarse a las dimensiones del rectángulo de destino.|  
|[CDC::StrokeAndFillPath](#strokeandfillpath)|Cierra figuras abiertas en una ruta de acceso, surge el esquema de la ruta de acceso utilizando el lápiz actual y su interior se rellena con el pincel actual.|  
|[CDC::StrokePath](#strokepath)|Representa la ruta de acceso especificada mediante el lápiz actual.|  
|[CDC::TabbedTextOut](#tabbedtextout)|Escribe una cadena de caracteres en una ubicación especificada, expansión de fichas a los valores especificados en una matriz de posiciones de tabulación.|  
|[CDC:: TextOut](#textout)|Escribe una cadena de caracteres en una ubicación especificada con la fuente seleccionada actualmente.|  
|[CDC::TransparentBlt](#transparentblt)|Transfiere un bloque de bits de datos de color desde el contexto de dispositivo de origen especificado en un contexto de dispositivo de destino de representación un determinado color transparente en la transferencia.|  
|[CDC::UpdateColors](#updatecolors)|Actualizaciones del área cliente de contexto de dispositivo mediante la coincidencia actual colores en el área de cliente de la paleta del sistema píxel por píxel.|  
|[CDC::WidenPath](#widenpath)|Vuelve a definir la ruta de acceso actual como el área que se va a pintar si la ruta de acceso se traza con el lápiz actualmente seleccionado en el contexto de dispositivo.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDC::operator HDC](#operator_hdc)|Recupera el identificador del contexto de dispositivo.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDC::m_hAttribDC](#m_hattribdc)|El contexto de dispositivo de atributo usado por este `CDC` objeto.|  
|[CDC::m_hDC](#m_hdc)|El contexto de dispositivo de salida utilizado por este `CDC` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 La `CDC` objeto proporciona funciones miembro para trabajar con un contexto de dispositivo, como una pantalla o impresora, así como los miembros para trabajar con un contexto de presentación asociado al área de cliente de una ventana.  
  
 Realice todos los dibujos a través del miembro de las funciones de un `CDC` objeto. La clase proporciona funciones miembro para las operaciones de contexto de dispositivo, trabajar con la selección de objetos de (GDI) de la interfaz de dispositivo de gráficos con seguridad de tipos, de herramientas de dibujo y trabajar con colores y paletas. También proporciona funciones miembro para obtener y establecer atributos de dibujo de asignación, trabajar con la ventanilla, trabajar con la extensión de la ventana, convertir a coordenadas, trabajar con regiones, recorte, dibujar líneas y dibujar formas simples, elipses y polígonos. También se proporcionan funciones miembro para dibujar texto, trabajar con fuentes, utilizar secuencias de escape de impresora, desplazamiento y reproducción de metarchivos.  
  
 Para usar un `CDC` de objeto, crearlo y, a continuación, llamar a su funciones miembro que las funciones de Windows que usan contextos de dispositivo en paralelo.  
  
> [!NOTE]
>  En Windows 95 ó 98, todas las coordenadas de pantalla están limitadas a 16 bits. Por lo tanto, un `int` pasa a un `CDC` función miembro debe encontrarse en el intervalo de – 32768 a 32767.  
  
 Para usos específicos, la biblioteca Microsoft Foundation Class proporciona varias clases derivadas de `CDC` . `CPaintDC`encapsula las llamadas a `BeginPaint` y `EndPaint`. `CClientDC`administra un contexto de presentación asociado al área de cliente de una ventana. `CWindowDC`administra un contexto de presentación asociado a una ventana completa, incluido su marco y controles. `CMetaFileDC`asocia un metarchivo de un contexto de dispositivo.  
  
 `CDC`proporciona dos funciones miembro, [GetLayout](#getlayout) y [SetLayout](#setlayout), para invertir el diseño de un contexto de dispositivo que no hereda su diseño de una ventana. Es necesario para aplicaciones escritas para las referencias culturales, como el árabe o hebreo, donde el diseño de carácter no es el estándar europeo dicha orientación de derecha a izquierda.  
  
 `CDC`contiene dos contextos de dispositivo, [m_hDC](#m_hdc) y [m_hAttribDC](#m_hattribdc), que, durante la creación de un `CDC` de objetos, consulte el mismo dispositivo. `CDC`dirige todas las llamadas GDI de salida a `m_hDC` y atributo mayoría GDI llama a `m_hAttribDC`. (Un ejemplo de una llamada de atributo es `GetTextColor`, mientras que `SetTextColor` es una llamada de salida.)  
  
 Por ejemplo, el marco de trabajo utiliza estos contextos de dos dispositivo para implementar un `CMetaFileDC` objeto que envía resultados a un metarchivo al leer los atributos de un dispositivo físico. Vista previa de impresión se implementa en el marco de trabajo de manera similar. También puede utilizar los contextos de dispositivo de dos de forma similar en el código específico de la aplicación.  
  
 Hay ocasiones en que podría necesitar información de métrica del texto de la `m_hDC` y `m_hAttribDC` contextos de dispositivo. Los siguientes pares de funciones de proporcionan esta capacidad:  
  
|Utiliza m_hAttribDC|Utiliza m_hDC|  
|-----------------------|-----------------|  
|[GetTextExtent](#gettextextent)|[GetOutputTextExtent](#getoutputtextextent)|  
|[GetTabbedTextExtent](#gettabbedtextextent)|[GetOutputTabbedTextExtent](#getoutputtabbedtextextent)|  
|[GetTextMetrics](#gettextmetrics)|[GetOutputTextMetrics](#getoutputtextmetrics)|  
|[GetCharWidth](#getcharwidth)|[GetOutputCharWidth](#getoutputcharwidth)|  
  
 Para obtener más información sobre `CDC`, consulte [contextos de dispositivo](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDC`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="a-nameabortdoca--cdcabortdoc"></a><a name="abortdoc"></a>CDC::AbortDoc  
 Finaliza el trabajo de impresión actual y borra todo lo que la aplicación se ha escrito en el dispositivo desde la última llamada a la [StartDoc](#startdoc) función miembro.  
  
```  
int AbortDoc();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor mayor o igual a 0 si se realiza correctamente, o un valor negativo si se ha producido un error. La lista siguiente muestra los valores de error comunes y sus significados:  
  
- **SP_ERROR** error General.  
  
- **SP_OUTOFDISK** no hay suficiente espacio en disco está disponible actualmente para la puesta en y no hay más espacio volverá a estar disponible.  
  
- **SP_OUTOFMEMORY** no hay suficiente memoria disponible para la cola de impresión.  
  
- **SP_USERABORT** el usuario ha finalizado el trabajo a través del Administrador de impresión.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro reemplaza la `ABORTDOC` de escape de impresora.  
  
 **AbortDoc** debe usarse para terminar los siguientes:  
  
-   Operaciones de impresión que no se especifican una función de anulación mediante [ayudar a](#setabortproc).  
  
-   Operaciones de impresión que no hayan alcanzado su primer **NEWFRAME** o **NEXTBAND** llamada de escape.  
  
 Si una aplicación encuentra un error de impresión o cancelar la operación de impresión, no debe intentar finalizar la operación utilizando la [EndDoc](#enddoc) o **AbortDoc** funciones miembro de clase `CDC`. GDI finaliza automáticamente la operación antes de devolver el valor de error.  
  
 Si la aplicación muestra un cuadro de diálogo para permitir al usuario cancelar la operación de impresión, debe llamar a **AbortDoc** antes de destruir el cuadro de diálogo.  
  
 Si el Administrador de impresión se utilizó para iniciar el trabajo de impresión, la llamada a **AbortDoc** borra el trabajo completo de la cola de impresión, la impresora recibe nada. Si el Administrador de impresión no se utilizó para iniciar el trabajo de impresión, los datos que ha enviado a la impresora antes de **AbortDoc** se llamó. En este caso, el controlador de impresora habría restablecer la impresora (cuando sea posible) y cierra el trabajo de impresión.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CDC::StartDoc](#startdoc).  
  
##  <a name="a-nameabortpatha--cdcabortpath"></a><a name="abortpath"></a>CDC::AbortPath  
 Cierra y descarta las rutas de acceso en el contexto de dispositivo.  
  
```  
BOOL AbortPath();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si hay un corchete trazado abierto en el contexto de dispositivo, el corchete de cierre de la ruta de acceso se cierra y se descarta la ruta de acceso. Si hay un trayecto cerrado en el contexto de dispositivo, se descarta la ruta de acceso.  
  
##  <a name="a-nameaddmetafilecommenta--cdcaddmetafilecomment"></a><a name="addmetafilecomment"></a>CDC::AddMetaFileComment  
 Copia el comentario de un búfer en un metarchivo de formato mejorado.  
  
```  
BOOL AddMetaFileComment(
    UINT nDataSize,  
    const BYTE* pCommentData);
```  
  
### <a name="parameters"></a>Parámetros  
 *nDataSize*  
 Especifica la longitud del búfer de comentario, en bytes.  
  
 *pCommentData*  
 Señala al búfer que contiene el comentario.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Un comentario puede incluir cualquier información privada, por ejemplo, el origen de la imagen y la fecha en que se creó. Un comentario debe empezar con una firma de la aplicación, seguida de los datos. Comentarios no deben contener datos específicos de la posición. Datos específicos de la posición especifican la ubicación de un registro, y no deben incluirse porque se puede incrustar un metarchivo dentro de otro metarchivo. Esta función sólo puede usarse con metarchivos mejorados.  
  
##  <a name="a-namealphablenda--cdcalphablend"></a><a name="alphablend"></a>CDC::AlphaBlend  
 Llame a esta función miembro para mostrar mapas de bits transparentes o semitransparentes píxeles.  
  
```  
BOOL AlphaBlend(
    int xDest,  
    int yDest,  
    int nDestWidth,  
    int nDestHeight,  
    CDC* pSrcDC,  
    int xSrc,  
    int ySrc,  
    int nSrcWidth,  
    int nSrcHeight,  
    BLENDFUNCTION blend);
```  
  
### <a name="parameters"></a>Parámetros  
 `xDest`  
 Especifica la coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.  
  
 `yDest`  
 Especifica la coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.  
  
 `nDestWidth`  
 Especifica el ancho, en unidades lógicas, del rectángulo de destino.  
  
 `nDestHeight`  
 Especifica el alto, en unidades lógicas, del rectángulo de destino.  
  
 `pSrcDC`  
 Un puntero al contexto de dispositivo de origen.  
  
 `xSrc`  
 Especifica la coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.  
  
 `ySrc`  
 Especifica la coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.  
  
 `nSrcWidth`  
 Especifica el ancho, en unidades lógicas, del rectángulo de origen.  
  
 `nSrcHeight`  
 Especifica el alto, en unidades lógicas, del rectángulo de origen.  
  
 *Blend*  
 Especifica un [BLENDFUNCTION](http://msdn.microsoft.com/library/windows/desktop/dd183393) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si es correcto; en caso contrario **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [AlphaBlend](http://msdn.microsoft.com/library/windows/desktop/dd183351) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información.  
  
##  <a name="a-nameanglearca--cdcanglearc"></a><a name="anglearc"></a>CDC::AngleArc  
 Dibuja un segmento de línea y un arco.  
  
```  
BOOL AngleArc(
    int x,  
    int y,  
    int nRadius,  
    float fStartAngle,  
    float fSweepAngle);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada x lógica del centro del círculo.  
  
 *y*  
 Especifica la coordenada y lógica del centro del círculo.  
  
 *nRadius*  
 Especifica el radio del círculo en unidades lógicas. Este valor debe ser positivo.  
  
 *fStartAngle*  
 Especifica el ángulo inicial en grados con respecto al eje x.  
  
 *fSweepAngle*  
 Especifica el ángulo de barrido en grados en relación con el ángulo inicial.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El segmento de línea se dibuja desde la posición actual hasta el principio del arco. Se dibuja el arco a lo largo del perímetro de un círculo con el centro y el radio determinado. La longitud del arco está definida por los ángulos inicial y barrido determinados.  
  
 `AngleArc`Mueve la posición actual hasta el punto final del arco. Arco dibujado por esta función que parece estar elíptico, según el modo de asignación y transformación actual. Antes de dibujar el arco, esta función dibuja el segmento de línea desde la posición actual hasta el principio del arco. El arco se dibuja mediante la creación de un círculo imaginario del radio especificado alrededor del punto central especificado. El punto inicial del arco se determina mediante la medición a la izquierda desde el eje x del círculo en el número de grados del ángulo inicial. El punto final se encuentra de forma similar mediante la medición a la izquierda desde el punto de partida en el número de grados del ángulo de barrido.  
  
 Si el ángulo de barrido es mayor que 360 grados el arco se trazará varias veces. Esta función dibuja líneas con el lápiz. No se ha rellenado la ilustración.  
  
##  <a name="a-namearca--cdcarc"></a><a name="arc"></a>CDC::ARC  
 Dibuja un arco elíptico.  
  
```  
BOOL Arc(
    int x1,  
    int y1,  
    int x2,  
    int y2,  
    int x3,  
    int y3,  
    int x4,  
    int y4);

 
BOOL Arc(
    LPCRECT lpRect,  
    POINT ptStart,  
    POINT ptEnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `x1`  
 Especifica la coordenada x de la esquina superior izquierda del rectángulo delimitador (en unidades lógicas).  
  
 `y1`  
 Especifica la coordenada y de la esquina superior izquierda del rectángulo delimitador (en unidades lógicas).  
  
 `x2`  
 Especifica la coordenada x de la esquina inferior derecha del rectángulo delimitador (en unidades lógicas).  
  
 `y2`  
 Especifica la coordenada y de la esquina inferior derecha del rectángulo delimitador (en unidades lógicas).  
  
 *x3*  
 Especifica la coordenada x del punto que define el arco inicial del punto (en unidades lógicas). Este punto no debe encontrarse exactamente en el arco.  
  
 `y3`  
 Especifica la coordenada y del punto que define el arco inicial del punto (en unidades lógicas). Este punto no debe encontrarse exactamente en el arco.  
  
 `x4`  
 Especifica la coordenada x del punto que define el extremo del arco (en unidades lógicas). Este punto no debe encontrarse exactamente en el arco.  
  
 `y4`  
 Especifica la coordenada y del punto que define el extremo del arco (en unidades lógicas). Este punto no debe encontrarse exactamente en el arco.  
  
 `lpRect`  
 Especifica el rectángulo delimitador (en unidades lógicas). Puede pasarse un `LPRECT` o un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto para este parámetro.  
  
 `ptStart`  
 Especifica las coordenadas x e y del punto que define el arco inicial del punto (en unidades lógicas). Este punto no debe encontrarse exactamente en el arco. Puede pasarse un [punto](../../mfc/reference/point-structure1.md) estructura o un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto para este parámetro.  
  
 `ptEnd`  
 Especifica las coordenadas x e y del punto que define el punto de final del arco (en unidades lógicas). Este punto no debe encontrarse exactamente en el arco. Puede pasarse un **punto** estructura o un `CPoint` objeto para este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Arco dibujado utilizando la función es un segmento de la elipse definida por el rectángulo delimitador especificado.  
  
 El punto de partida real del arco es el punto en que un rayo dibujado desde el centro del rectángulo delimitador a través del punto inicial especificado corta a la elipse. El punto final real del arco es el punto en que un rayo dibujado desde el centro del rectángulo delimitador a través del punto final especificado corta a la elipse. El arco se dibuja en una dirección hacia la izquierda. Puesto que un arco no es una figura cerrada, no se rellena. El ancho y el alto del rectángulo deben ser mayores que 2 unidades y las unidades inferior a 32.767.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#29;](../../mfc/codesnippet/cpp/cdc-class_1.cpp)]  
  
##  <a name="a-namearctoa--cdcarcto"></a><a name="arcto"></a>CDC::ArcTo  
 Dibuja un arco elíptico.  
  
```  
BOOL ArcTo(
    int x1,  
    int y1,  
    int x2,  
    int y2,  
    int x3,  
    int y3,  
    int x4,  
    int y4);

 
BOOL ArcTo(
    LPCRECT lpRect,  
    POINT ptStart,  
    POINT ptEnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `x1`  
 Especifica la coordenada x de la esquina superior izquierda del rectángulo delimitador (en unidades lógicas).  
  
 `y1`  
 Especifica la coordenada y de la esquina superior izquierda del rectángulo delimitador (en unidades lógicas).  
  
 `x2`  
 Especifica la coordenada x de la esquina inferior derecha del rectángulo delimitador (en unidades lógicas).  
  
 `y2`  
 Especifica la coordenada y de la esquina inferior derecha del rectángulo delimitador (en unidades lógicas).  
  
 *x3*  
 Especifica la coordenada x del punto que define el arco inicial del punto (en unidades lógicas). Este punto no debe encontrarse exactamente en el arco.  
  
 `y3`  
 Especifica la coordenada y del punto que define el arco inicial del punto (en unidades lógicas). Este punto no debe encontrarse exactamente en el arco.  
  
 `x4`  
 Especifica la coordenada x del punto que define el extremo del arco (en unidades lógicas). Este punto no debe encontrarse exactamente en el arco.  
  
 `y4`  
 Especifica la coordenada y del punto que define el extremo del arco (en unidades lógicas). Este punto no debe encontrarse exactamente en el arco.  
  
 `lpRect`  
 Especifica el rectángulo delimitador (en unidades lógicas). Puede pasar un puntero a un [RECT](../../mfc/reference/rect-structure1.md) estructura de datos o un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto para este parámetro.  
  
 `ptStart`  
 Especifica las coordenadas x e y del punto que define el arco inicial del punto (en unidades lógicas). Este punto no debe encontrarse exactamente en el arco. Puede pasarse un [punto](../../mfc/reference/point-structure1.md) estructura de datos o un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto para este parámetro.  
  
 `ptEnd`  
 Especifica las coordenadas x e y del punto que define el punto de final del arco (en unidades lógicas). Este punto no debe encontrarse exactamente en el arco. Puede pasarse un **punto** estructura de datos o un `CPoint` objeto para este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es similar a `CDC::Arc`, excepto en que se actualiza la posición actual. Los puntos ( `x1`, `y1`) y ( `x2`, `y2`) especifican el rectángulo delimitador. Una elipse formada por el rectángulo delimitador especificado define la curva del arco. El arco extiende a la izquierda (la dirección predeterminada del arco) desde el punto donde corta la línea radial desde el centro del rectángulo delimitador para ( *x3*, `y3`). Los extremos del arco donde intersección con la línea radial desde el centro del rectángulo delimitador para ( `x4`, `y4`). Si el punto de partida y el punto final son iguales, se dibuja una elipse completa.  
  
 Se dibuja una línea desde la posición actual hasta el punto inicial del arco. Si se produce ningún error, se establece la posición actual hasta el punto final del arco. El arco se dibuja con el lápiz actual; no se rellena.  
  
##  <a name="a-nameattacha--cdcattach"></a><a name="attach"></a>CDC::Attach  
 Utilice esta función miembro para adjuntar un `hDC` a la `CDC` objeto.  
  
```  
BOOL Attach(HDC hDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `hDC`  
 Un contexto de dispositivo de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El `hDC` se almacena tanto en `m_hDC`, el contexto de dispositivo de salida y en `m_hAttribDC`, el contexto de dispositivo de atributo.  
  
##  <a name="a-namebeginpatha--cdcbeginpath"></a><a name="beginpath"></a>CDC:: beginpath  
 Abre un corchete de cierre de la ruta de acceso en el contexto de dispositivo.  
  
```  
BOOL BeginPath();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Después de un corchete de cierre de la ruta de acceso está abierto, una aplicación puede comenzar a llamar a funciones de dibujo de GDI para definir los puntos que se encuentran en la ruta de acceso. Una aplicación puede cerrar corchete de cierre de un trazado abierto llamando a la `EndPath` función miembro. Cuando una aplicación llama `BeginPath`, se descartan las rutas de acceso anteriores.  
  
 Consulte [BeginPath](http://msdn.microsoft.com/library/windows/desktop/dd183363) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una lista de las funciones de dibujos que definen los puntos en una ruta de acceso.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView Nº&30;](../../mfc/codesnippet/cpp/cdc-class_2.cpp)]  
  
##  <a name="a-namebitblta--cdcbitblt"></a><a name="bitblt"></a>CDC::BitBlt  
 Copia un mapa de bits desde el contexto de dispositivo de origen en el contexto del dispositivo actual.  
  
```  
BOOL BitBlt(
    int x,  
    int y,  
    int nWidth,  
    int nHeight,  
    CDC* pSrcDC,  
    int xSrc,  
    int ySrc,  
    DWORD dwRop);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada x lógica de la esquina superior izquierda del rectángulo de destino.  
  
 *y*  
 Especifica la coordenada y lógica de la esquina superior izquierda del rectángulo de destino.  
  
 `nWidth`  
 Especifica el ancho (en unidades lógicas) del mapa de bits de origen y el rectángulo de destino.  
  
 `nHeight`  
 Especifica el alto (en unidades lógicas) del mapa de bits de origen y el rectángulo de destino.  
  
 `pSrcDC`  
 Puntero a un `CDC` objeto que identifica el contexto de dispositivo desde el que se van a copiar el mapa de bits. Debe ser **NULL** si *dwRop* especifica una operación de trama que no incluya un origen.  
  
 `xSrc`  
 Especifica la coordenada x lógica de la esquina superior izquierda del mapa de bits de origen.  
  
 `ySrc`  
 Especifica la coordenada y lógica de la esquina superior izquierda del mapa de bits de origen.  
  
 *dwRop*  
 Especifica la operación de trama que se va a realizar. Los códigos de operación de trama definen cómo combina la GDI los colores en las operaciones de salida que implican un pincel actual, un mapa de bits de origen posibles y un mapa de bits de destino. Consulte [BitBlt](http://msdn.microsoft.com/library/windows/desktop/dd183370) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una lista de los códigos de operación de trama *dwRop* y sus descripciones  
  
 Para obtener una lista completa de códigos de operación de trama, consulte [códigos de operación de trama](http://msdn.microsoft.com/library/windows/desktop/dd162892) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Puede alinear la aplicación de windows o de áreas de cliente en límites de bytes para asegurarse de que el `BitBlt` operaciones que se producen en los rectángulos de alineación en bytes. (Establecer el **CS_BYTEALIGNWINDOW** o **CS_BYTEALIGNCLIENT** marcas al registrar las clases de ventana.)  
  
 `BitBlt`operaciones en rectángulos alineado por bytes son considerablemente más rápidas que `BitBlt` operaciones en los rectángulos que no son bytes alineados. Si desea especificar los estilos de clase, como la alineación de bytes para su propio contexto de dispositivo, tendrá que registrar una clase de ventana en lugar de depender de Microsoft Foundation classes para que lo haga por usted. Utilice la función global [AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass).  
  
 Transforma GDI `nWidth` y `nHeight`, una vez mediante el contexto de dispositivo de destino y una vez utilizando el contexto de dispositivo de origen. Si no coinciden con las extensiones resultantes, GDI utiliza Windows `StretchBlt` función para comprimir o expandir el mapa de bits de origen según sea necesario.  
  
 Si los mapas de bits de patrón, origen y destino no tienen el mismo formato de color, el `BitBlt` función convierte los mapas de bits de origen y de patrón para que coincida con el destino. Los colores de primer plano y fondo del mapa de bits de destino se utilizan en la conversión.  
  
 Cuando el `BitBlt` función convierte un mapa de bits monocromo a color, Establece los bits blancos (1) al color de fondo y los bits negros (0) para el color de primer plano. Se utilizan los colores de primer plano y de fondo del contexto de dispositivo de destino. Convertir color a monocromo, `BitBlt` establece los píxeles que coinciden con el color de fondo en blanco y todos los demás píxeles en negro. `BitBlt`utiliza los colores de primer plano y de fondo del contexto de dispositivo de color para convertir de color a monocromo.  
  
 Tenga en cuenta que no todos los contextos de dispositivo admiten `BitBlt`. Para comprobar si es compatible con un contexto de dispositivo determinado `BitBlt`, utilice el `GetDeviceCaps` miembro función y especificar el **RASTERCAPS** índice.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CDC::CreateCompatibleDC](#createcompatibledc).  
  
##  <a name="a-namecdca--cdccdc"></a><a name="cdc"></a>CDC::CDC  
 Construye un objeto `CDC`.  
  
```  
CDC();
```  
  
##  <a name="a-namechorda--cdcchord"></a><a name="chord"></a>CDC::Chord  
 Dibuja una cuerda (una figura cerrada limitada por la intersección de una elipse y un segmento de línea).  
  
```  
BOOL Chord(
    int x1,  
    int y1,  
    int x2,  
    int y2,  
    int x3,  
    int y3,  
    int x4,  
    int y4);

 
BOOL Chord(
    LPCRECT lpRect,  
    POINT ptStart,  
    POINT ptEnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `x1`  
 Especifica que la coordenada x de la esquina superior izquierda de la cuerda delimitador del rectángulo (en unidades lógicas).  
  
 `y1`  
 Especifica que la coordenada y de la esquina superior izquierda de la cuerda delimitador del rectángulo (en unidades lógicas).  
  
 `x2`  
 Especifica que la coordenada x de la esquina inferior derecha de la cuerda delimitador del rectángulo (en unidades lógicas).  
  
 `y2`  
 Especifica que la coordenada y de la esquina inferior derecha de la cuerda delimitador del rectángulo (en unidades lógicas).  
  
 *x3*  
 Especifica la coordenada x del punto que define la cuerda inicial del punto (en unidades lógicas).  
  
 `y3`  
 Especifica la coordenada y del punto que define la cuerda inicial del punto (en unidades lógicas).  
  
 `x4`  
 Especifica la coordenada x del punto que define el extremo de la cuerda (en unidades lógicas).  
  
 `y4`  
 Especifica la coordenada y del punto que define el extremo de la cuerda (en unidades lógicas).  
  
 `lpRect`  
 Especifica el rectángulo delimitador (en unidades lógicas). Puede pasarse un `LPRECT` o un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto para este parámetro.  
  
 `ptStart`  
 Especifica las coordenadas x e y del punto que define la cuerda inicial del punto (en unidades lógicas). Este punto no debe encontrarse exactamente en la cuerda. Puede pasarse un **punto** estructura o un `CPoint` objeto para este parámetro.  
  
 `ptEnd`  
 Especifica las coordenadas x e y del punto que define punto final de la cuerda (en unidades lógicas). Este punto no debe encontrarse exactamente en la cuerda. Puede pasarse un [punto](../../mfc/reference/point-structure1.md) estructura o un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto para este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El ( `x1`, `y1`) y ( `x2`, `y2`) parámetros especifican las esquinas superior izquierda e inferior derecha, respectivamente, de un rectángulo delimitador de la elipse que forma parte de la cuerda. El ( *x3*, `y3`) y ( `x4`, `y4`) los parámetros especifican los extremos de una línea que forma una intersección con la elipse. La cuerda es dibujada con el lápiz seleccionado y se rellena con el pincel seleccionado.  
  
 La figura dibujada por el `Chord` función extiende hasta, pero no incluye las coordenadas derecho e inferior. Esto significa que es el alto de la figura `y2` : `y1` y el ancho de la figura es `x2` : `x1`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#31;](../../mfc/codesnippet/cpp/cdc-class_3.cpp)]  
  
##  <a name="a-nameclosefigurea--cdcclosefigure"></a><a name="closefigure"></a>CDC::CloseFigure  
 Cierra una figura abierta en una ruta de acceso.  
  
```  
BOOL CloseFigure();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 La función cierra la figura dibujando una línea desde la posición actual hasta el primer punto de la figura (normalmente, el punto especificado por la llamada más reciente a la `MoveTo` función miembro) y conecta las líneas utilizando el estilo de unión de línea. Si se cierra una figura utilizando la `LineTo` función miembro en lugar de `CloseFigure`, extremos se utilizan para crear la esquina en lugar de una combinación. `CloseFigure`solo debe llamarse si hay un corchete trazado abierto en el contexto de dispositivo.  
  
 Una figura en una ruta de acceso está abierta, a menos que se cierre explícitamente mediante esta función. (Ilustración puede ser abierta incluso si el punto actual y el punto inicial de la ilustración son los mismos.) Las líneas o curvas que se agrega a la ruta de acceso después de `CloseFigure` inicia una nueva figura.  
  
##  <a name="a-namecreatecompatibledca--cdccreatecompatibledc"></a><a name="createcompatibledc"></a>CDC::CreateCompatibleDC  
 Crea un contexto de dispositivo de memoria que es compatible con el dispositivo especificado por `pDC`.  
  
```  
BOOL CreateCompatibleDC(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Puntero a un contexto de dispositivo. Si `pDC` es **NULL**, la función crea un contexto de dispositivo de memoria que sea compatible con la pantalla del sistema.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Un contexto de dispositivo de memoria es un bloque de memoria que representa una superficie de pantalla. Puede usar para preparar las imágenes en la memoria antes de copiarlos en la superficie del dispositivo real del dispositivo compatible.  
  
 Cuando se crea un contexto de dispositivo de memoria, GDI selecciona automáticamente un mapa de bits de stock monocromo de 1 por 1 para él. Funciones de salida GDI pueden utilizarse con un contexto de dispositivo de memoria solo si se creó un mapa de bits y seleccionada en ese contexto.  
  
 Esta función sólo puede usarse para crear contextos de dispositivo compatible con dispositivos que admiten operaciones de trama. Consulte la [CDC::BitBlt](#bitblt) función miembro para obtener información sobre las transferencias de bloque de bits entre contextos de dispositivo. Para determinar si un contexto de dispositivo admite operaciones de mapa de bits, consulte el **RC_BITBLT** capacidad de trama en la función miembro `CDC::GetDeviceCaps`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#32;](../../mfc/codesnippet/cpp/cdc-class_4.cpp)]  
  
##  <a name="a-namecreatedca--cdccreatedc"></a><a name="createdc"></a>CDC::CreateDC  
 Crea un contexto de dispositivo para el dispositivo especificado.  
  
```  
BOOL CreateDC(
    LPCTSTR lpszDriverName,  
    LPCTSTR lpszDeviceName,  
    LPCTSTR lpszOutput,  
    const void* lpInitData);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszDriverName`  
 Apunta a una cadena terminada en null que especifica el nombre de archivo (sin extensión) del controlador de dispositivo (por ejemplo, "EPSON"). También puede pasar un `CString` objeto para este parámetro.  
  
 `lpszDeviceName`  
 Apunta a una cadena terminada en null que especifica el nombre de dispositivo compatibles (por ejemplo, "EPSON FX-80"). El `lpszDeviceName` parámetro se usa si el módulo es compatible con más de un dispositivo. También puede pasar un `CString` objeto para este parámetro.  
  
 `lpszOutput`  
 Apunta a una cadena terminada en null que especifica el nombre de archivo o dispositivo para el medio físico de salida (puerto de salida o de archivo). También puede pasar un `CString` objeto para este parámetro.  
  
 `lpInitData`  
 Apunta a un `DEVMODE` estructura que contiene los datos de inicialización específica del dispositivo para el controlador de dispositivo. Windows **DocumentProperties** función recupera esta estructura rellenada para un dispositivo dado. El `lpInitData` parámetro debe ser **NULL** si el controlador de dispositivo es usar la inicialización predeterminada (si existe) especificada por el usuario a través del Panel de Control.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 La impresión. Archivo de encabezado H es necesaria si la [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) usa esta estructura.  
  
 Nombres de dispositivo seguir estas convenciones: un final puntos (:) se recomienda, pero es opcional. Windows elimina los dos puntos terminación para que se asigna un nombre de dispositivo que terminan con un signo de dos puntos en el mismo puerto que el mismo nombre sin dos puntos. Los nombres de controlador y el puerto no deben contener espacios iniciales ni finales. No se puede usar funciones de salida GDI con contextos de información.  
  
##  <a name="a-namecreateica--cdccreateic"></a><a name="createic"></a>CDC::CreateIC  
 Crea un contexto de información para el dispositivo especificado.  
  
```  
BOOL CreateIC(
    LPCTSTR lpszDriverName,  
    LPCTSTR lpszDeviceName,  
    LPCTSTR lpszOutput,  
    const void* lpInitData);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszDriverName`  
 Apunta a una cadena terminada en null que especifica el nombre de archivo (sin extensión) del controlador de dispositivo (por ejemplo, "EPSON"). Puede pasar un `CString` objeto para este parámetro.  
  
 `lpszDeviceName`  
 Apunta a una cadena terminada en null que especifica el nombre de dispositivo compatibles (por ejemplo, "EPSON FX-80"). El `lpszDeviceName` parámetro se usa si el módulo es compatible con más de un dispositivo. Puede pasar un `CString` objeto para este parámetro.  
  
 `lpszOutput`  
 Apunta a una cadena terminada en null que especifica el nombre de archivo o dispositivo para el medio físico de salida (archivo o puerto). Puede pasar un `CString` objeto para este parámetro.  
  
 `lpInitData`  
 Puntos de datos de inicialización específica del dispositivo para el controlador de dispositivo. El `lpInitData` parámetro debe ser **NULL** si el controlador de dispositivo es usar la inicialización predeterminada (si existe) especificada por el usuario a través del Panel de Control. Consulte `CreateDC` para el formato de datos para la inicialización específica del dispositivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El contexto de información proporciona una forma rápida de obtener información sobre el dispositivo sin crear un contexto de dispositivo.  
  
 Nombres de dispositivo seguir estas convenciones: un final puntos (:) se recomienda, pero es opcional. Windows elimina los dos puntos terminación para que se asigna un nombre de dispositivo que terminan con un signo de dos puntos en el mismo puerto que el mismo nombre sin dos puntos. Los nombres de controlador y el puerto no deben contener espacios iniciales ni finales. No se puede usar funciones de salida GDI con contextos de información.  
  
##  <a name="a-namedeletedca--cdcdeletedc"></a><a name="deletedc"></a>CDC::DeleteDC  
 En general, no llame a esta función; el destructor lo haga por usted.  
  
```  
BOOL DeleteDC();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se completó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El `DeleteDC` función miembro elimina los contextos de dispositivo de Windows que están asociados a `m_hDC` actual `CDC` objeto. Si este `CDC` objeto es el último contexto de dispositivo activo para un dispositivo dado, se notifica el dispositivo y se liberan todos los recursos de almacenamiento y del sistema utilizados por el dispositivo.  
  
 Una aplicación no debe llamar a `DeleteDC` si se han seleccionado los objetos en el contexto de dispositivo. Primero se deben seleccionar objetos fuera del contexto de dispositivo antes de eliminarlo.  
  
 Una aplicación no debe eliminar un contexto de dispositivo cuyo identificador se haya obtenido mediante una llamada a [CWnd::GetDC](../../mfc/reference/cwnd-class.md#getdc). En su lugar, debe llamar a [CWnd::ReleaseDC](../../mfc/reference/cwnd-class.md#releasedc) para liberar el contexto de dispositivo. El [CClientDC](../../mfc/reference/cclientdc-class.md) y [los objetos CWindowDC](../../mfc/reference/cwindowdc-class.md) se proporcionan clases para encapsular esta funcionalidad.  
  
 El `DeleteDC` función se suele utilizar para borrar contextos de dispositivo creados con [CreateDC](#createdc), [CreateIC](#createic), o [CreateCompatibleDC](#createcompatibledc).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPrintDialog::GetPrinterDC](../../mfc/reference/cprintdialog-class.md#getprinterdc).  
  
##  <a name="a-namedeletetempmapa--cdcdeletetempmap"></a><a name="deletetempmap"></a>CDC::DeleteTempMap  
 Llama de forma automática el `CWinApp` controlador de tiempo de inactividad, `DeleteTempMap` elimina cualquier temporal `CDC` objetos creados por `FromHandle`, pero no destruirá los identificadores de contexto de dispositivo ( `hDC`s) asociado temporalmente el `CDC` objetos.  
  
```  
static void PASCAL DeleteTempMap();
```  
  
##  <a name="a-namedetacha--cdcdetach"></a><a name="detach"></a>CDC::Detach  
 Llame a esta función para separar `m_hDC` (el contexto de dispositivo de salida) de la `CDC` objeto y establecer ambos `m_hDC` y `m_hAttribDC` a **NULL**.  
  
```  
HDC Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un contexto de dispositivo de Windows.  
  
##  <a name="a-namedptohimetrica--cdcdptohimetric"></a><a name="dptohimetric"></a>CDC::DPtoHIMETRIC  
 Use esta función cuando da **HIMETRIC** tamaños de OLE, convertir píxeles a **HIMETRIC**.  
  
```  
void DPtoHIMETRIC(LPSIZE lpSize) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpSize`  
 Apunta a un [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura o [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Si el modo de asignación del objeto de contexto de dispositivo es `MM_LOENGLISH`, `MM_HIENGLISH`, `MM_LOMETRIC`, o `MM_HIMETRIC`, la conversión se basa en el número de píxeles de pulgada físico. Si el modo de asignación es uno de los modos no restringidos (por ejemplo, `MM_TEXT`), la conversión se basa en el número de píxeles de la pulgada lógica.  
  
##  <a name="a-namedptolpa--cdcdptolp"></a><a name="dptolp"></a>CDC::DPtoLP  
 Convierte las unidades de dispositivo en unidades lógicas.  
  
```  
void DPtoLP(
    LPPOINT lpPoints,  
    int nCount = 1) const;  
  
void DPtoLP(LPRECT lpRect) const;
void DPtoLP(LPSIZE lpSize) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPoints`  
 Apunta a una matriz de [punto](../../mfc/reference/point-structure1.md) estructuras o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objetos.  
  
 `nCount`  
 El número de puntos de la matriz.  
  
 `lpRect`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura o [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto. Este parámetro se utiliza para el caso sencillo de convertir un rectángulo de puntos del dispositivo a puntos lógicos.  
  
 `lpSize`  
 Apunta a un [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura o [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 La función asigna las coordenadas de cada punto o dimensiones de tamaño, desde el sistema de coordenadas de dispositivo en el sistema de coordenadas lógicas del GDI. La conversión depende del modo de asignación actual y la configuración de los orígenes y las extensiones de ventana y el área de visualización del dispositivo.  
  
##  <a name="a-namedraw3drecta--cdcdraw3drect"></a><a name="draw3drect"></a>CDC::Draw3dRect  
 Llame a esta función miembro para dibujar un rectángulo tridimensional.  
  
```  
void Draw3dRect(
    LPCRECT lpRect,  
    COLORREF clrTopLeft,  
    COLORREF clrBottomRight);

 
void Draw3dRect(
    int x,  
    int y,  
    int cx,  
    int cy,  
    COLORREF clrTopLeft,  
    COLORREF clrBottomRight);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Especifica el rectángulo delimitador (en unidades lógicas). Puede pasar un puntero a un [RECT](../../mfc/reference/rect-structure1.md) estructura o un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto para este parámetro.  
  
 *clrTopLeft*  
 Especifica el color de los lados superiores e izquierdos del rectángulo tridimensional.  
  
 `clrBottomRight`  
 Especifica el color de la parte inferior y el lado derecho del rectángulo tridimensional.  
  
 *x*  
 Especifica la coordenada x lógica de la esquina superior izquierda del rectángulo tridimensional.  
  
 *y*  
 Especifica la coordenada y lógica de la esquina superior izquierda del rectángulo tridimensional.  
  
 CX  
 Especifica el ancho del rectángulo tridimensional.  
  
 CY  
 Especifica el alto del rectángulo tridimensional.  
  
### <a name="remarks"></a>Comentarios  
 El rectángulo se dibujarán con los lados superior e izquierdos en el color especificado por *clrTopLeft* y los lados inferior y derecho en el color especificado por `clrBottomRight`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView Nº&33;](../../mfc/codesnippet/cpp/cdc-class_5.cpp)]  
  
##  <a name="a-namedrawdragrecta--cdcdrawdragrect"></a><a name="drawdragrect"></a>CDC::DrawDragRect  
 Llame a esta función miembro varias veces para volver a dibujar un rectángulo de arrastre.  
  
```  
void DrawDragRect(
    LPCRECT lpRect,  
    SIZE size,  
    LPCRECT lpRectLast,  
    SIZE sizeLast,  
    CBrush* pBrush = NULL,  
    CBrush* pBrushLast = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura o un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que especifica las coordenadas lógicas del rectángulo, en este caso, la posición final del rectángulo que se va a dibujar.  
  
 `size`  
 Especifica el desplazamiento desde la esquina superior izquierda del borde exterior a la esquina superior izquierda del borde interno (es decir, el grosor del borde) de un rectángulo.  
  
 `lpRectLast`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura o un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que especifica las coordenadas lógicas de la posición de un rectángulo, en este caso, la posición original del rectángulo que se va a dibujar.  
  
 *sizeLast*  
 Especifica el desplazamiento desde la esquina superior izquierda del borde exterior a la esquina superior izquierda del borde interno (es decir, el grosor del borde) del rectángulo original que se va a dibujar.  
  
 `pBrush`  
 Puntero a un objeto brush. Establecer en **NULL** para utilizar el pincel de medios tonos de manera predeterminada.  
  
 *pBrushLast*  
 Puntero al último objeto pincel utilizado. Establecer en **NULL** para utilizar el pincel de medios tonos de manera predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 Llamar en un bucle, tal como muestra la posición del mouse, con el fin de proporcionar información visual. Cuando se llama a `DrawDragRect`, se borra el rectángulo anterior y se dibuja una nueva. Por ejemplo, como el usuario arrastra un rectángulo en la pantalla `DrawDragRect` se borran el rectángulo original y volver a dibujar una nueva en su nueva posición. De forma predeterminada, `DrawDragRect` dibuja el rectángulo con un pincel de semitonos para eliminar el parpadeo y para crear la apariencia de un rectángulo móvil sin problemas.  
  
 La primera vez que se llama a `DrawDragRect`, `lpRectLast` parámetro debería ser **NULL**.  
  
##  <a name="a-namedrawedgea--cdcdrawedge"></a><a name="drawedge"></a>CDC::DrawEdge  
 Llame a esta función miembro para dibujar los bordes de un rectángulo del tipo especificado y el estilo.  
  
```  
BOOL DrawEdge(
    LPRECT lpRect,  
    UINT nEdge,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Un puntero a un **RECT** estructura que contiene las coordenadas lógicas del rectángulo.  
  
 *nEdge*  
 Especifica el tipo de borde interior y exterior para dibujar. Este parámetro debe ser una combinación de un indicador del borde interior y un indicador del borde exterior. Consulte [DrawEdge](http://msdn.microsoft.com/library/windows/desktop/dd162477) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para una tabla de tipos del parámetro.  
  
 `nFlags`  
 Las marcas que especifican el tipo de borde que se va a dibujar. Consulte `DrawEdge` en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] de una tabla de los valores del parámetro. Para las líneas diagonales, el **BF_RECT** indicadores especifican el punto final del vector limitado por el parámetro de rectángulo.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
##  <a name="a-namedrawescapea--cdcdrawescape"></a><a name="drawescape"></a>CDC::DrawEscape  
 Accesos a funciones de una pantalla de vídeo que no están directamente disponibles a través de la interfaz de dispositivo gráfico (GDI) de dibujo.  
  
```  
int DrawEscape(
    int nEscape,  
    int nInputSize,  
    LPCSTR lpszInputData);
```  
  
### <a name="parameters"></a>Parámetros  
 `nEscape`  
 Especifica la función de escape que se realizará.  
  
 `nInputSize`  
 Especifica el número de bytes de datos que señala el `lpszInputData` parámetro.  
  
 `lpszInputData`  
 Señala a la estructura de entrada necesarios para el escape especificado.  
  
### <a name="return-value"></a>Valor devuelto  
 Especifica el resultado de la función. Mayor que cero si es correcta, excepto para la **QUERYESCSUPPORT** dibujar escape, la cual comprueba sólo; la implementación o cero si no se ha implementado el escape; o menor que cero si un error se produjo.  
  
### <a name="remarks"></a>Comentarios  
 Cuando una aplicación llama `DrawEscape`, los datos identificados por `nInputSize` y `lpszInputData` se pasa directamente al controlador de pantalla especificado.  
  
##  <a name="a-namedrawfocusrecta--cdcdrawfocusrect"></a><a name="drawfocusrect"></a>CDC::DrawFocusRect  
 Dibuja un rectángulo en el estilo que se utiliza para indicar que el rectángulo tiene el foco.  
  
```  
void DrawFocusRect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura o un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que especifica las coordenadas lógicas del rectángulo que se va a dibujar.  
  
### <a name="remarks"></a>Comentarios  
 Puesto que es una función booleana XOR, llamar a esta función una segunda vez con el mismo rectángulo quita el rectángulo de la pantalla. No se puede desplazar el rectángulo dibujado por esta función. Para desplazar un área que contiene un rectángulo dibujado por esta función, llamada `DrawFocusRect` para quitar el rectángulo de la pantalla, a continuación, desplazar el área y, a continuación, llame a `DrawFocusRect` para dibujar el rectángulo en la nueva posición.  
  
> [!CAUTION]
> `DrawFocusRect`funciona únicamente en `MM_TEXT` modo. En otros modos, esta función no dibuja el rectángulo de foco correctamente, pero no devuelve los valores de error.  
  
##  <a name="a-namedrawframecontrola--cdcdrawframecontrol"></a><a name="drawframecontrol"></a>CDC::DrawFrameControl  
 Llame a esta función miembro para dibujar un control del tipo especificado y el estilo de marco.  
  
```  
BOOL DrawFrameControl(
    LPRECT lpRect,  
    UINT nType,  
    UINT nState);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Un puntero a un **RECT** estructura que contiene las coordenadas lógicas del rectángulo.  
  
 `nType`  
 Especifica el tipo de control de marco para dibujar. Consulte la *uType* parámetro en [DrawFrameControl](http://msdn.microsoft.com/library/windows/desktop/dd162480) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una lista de los valores posibles de este parámetro.  
  
 `nState`  
 Especifica el estado inicial del control de marco. Puede ser uno o varios de los valores descritos para la *uState* parámetro en `DrawFrameControl` en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Utilice la `nState` valor **DFCS_ADJUSTRECT** para ajustar el rectángulo delimitador para excluir el borde alrededor del botón de inserción.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 En muchos casos, `nState` depende de la `nType` parámetro. En la lista siguiente muestra la relación entre los cuatro `nType` valores y `nState`:  
  
- **DFC_BUTTON**  
  
    - **DFCS_BUTTON3STATE** botón de tres Estados  
  
    - **DFCS_BUTTONCHECK** casilla de verificación  
  
    - **DFCS_BUTTONPUSH** botón de inserción  
  
    - **DFCS_BUTTONRADIO** botón de Radio  
  
    - **DFCS_BUTTONRADIOIMAGE** imagen de botón de radio (no cuadrados necesita imagen)  
  
    - **DFCS_BUTTONRADIOMASK** máscara de botón de radio (no cuadrados necesita máscara)  
  
- **DFC_CAPTION**  
  
    - **DFCS_CAPTIONCLOSE** botón Cerrar  
  
    - **DFCS_CAPTIONHELP** botón Ayuda  
  
    - **DFCS_CAPTIONMAX** botón Maximizar  
  
    - **DFCS_CAPTIONMIN** botón minimizar  
  
    - **DFCS_CAPTIONRESTORE** botón Restaurar  
  
- **DFC_MENU**  
  
    - **DFCS_MENUARROW** flecha de submenú  
  
    - **DFCS_MENUBULLET** viñeta  
  
    - **DFCS_MENUCHECK** marca de verificación  
  
- **DFC_SCROLL**  
  
    - **DFCS_SCROLLCOMBOBOX** barra de desplazamiento de cuadro combinado  
  
    - **DFCS_SCROLLDOWN** flecha de barra de desplazamiento hacia abajo  
  
    - **DFCS_SCROLLLEFT** flecha a la izquierda de la barra de desplazamiento  
  
    - **DFCS_SCROLLRIGHT** flecha derecha de la barra de desplazamiento  
  
    - **DFCS_SCROLLSIZEGRIP** control de tamaño en la esquina inferior derecha de la ventana  
  
    - **DFCS_SCROLLUP** flecha de barra de desplazamiento hacia arriba  
  
### <a name="example"></a>Ejemplo  
 Este código dibuja al redimensionamiento de tamaño en la esquina inferior derecha de la ventana. Es adecuado para el `OnPaint` controlador de un cuadro de diálogo sin estilos y no suele contener otros controles (por ejemplo, una barra de estado) que pueden dar un agarre de tamaño.  
  
 [!code-cpp[NVC_MFCDocView&#34;](../../mfc/codesnippet/cpp/cdc-class_6.cpp)]  
  
##  <a name="a-namedrawicona--cdcdrawicon"></a><a name="drawicon"></a>CDC::DrawIcon  
 Dibuja un icono en el dispositivo representado por el actual `CDC` objeto.  
  
```  
BOOL DrawIcon(
    int x,  
    int y,  
    HICON hIcon);

 
BOOL DrawIcon(
    POINT point,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada x lógica de la esquina superior izquierda del icono.  
  
 *y*  
 Especifica la coordenada y lógica de la esquina superior izquierda del icono.  
  
 `hIcon`  
 Identifica el identificador del icono que se va a dibujar.  
  
 `point`  
 Especifica las coordenadas x e y lógica de la esquina superior izquierda del icono. Puede pasar un [punto](../../mfc/reference/point-structure1.md) estructura o un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto para este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se completó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La función coloca la esquina superior izquierda del icono en la ubicación especificada por *x* y *y*. El modo de asignación actual del contexto de dispositivo depende de la ubicación.  
  
 El recurso de icono debe haya cargado anteriormente utilizando las funciones `CWinApp::LoadIcon`, `CWinApp::LoadStandardIcon`, o `CWinApp::LoadOEMIcon`. El `MM_TEXT` modo de asignación debe seleccionarse antes de poder usar esta función.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CWnd::IsIconic](../../mfc/reference/cwnd-class.md#isiconic).  
  
##  <a name="a-namedrawstatea--cdcdrawstate"></a><a name="drawstate"></a>CDC::DrawState  
 Llame a esta función miembro para mostrar una imagen y aplica un efecto visual para indicar un estado como un deshabilitado o predeterminado.  
  
> [!NOTE]
>  Para todos los `nFlag` Estados excepto **DSS_NORMAL**, la imagen se convierte en monocromática antes de aplica el efecto visual.  
  
```  
BOOL DrawState(
    CPoint pt,  
    CSize size,  
    HBITMAP hBitmap,  
    UINT nFlags,  
    HBRUSH hBrush = NULL);

 
BOOL DrawState(
    CPoint pt,  
    CSize size,  
    CBitmap* pBitmap,  
    UINT nFlags,  
    CBrush* pBrush = NULL);

 
BOOL DrawState(
    CPoint pt,  
    CSize size,  
    HICON hIcon,  
    UINT nFlags,  
    HBRUSH hBrush = NULL);

 
BOOL DrawState(
    CPoint pt,  
    CSize size,  
    HICON hIcon,  
    UINT nFlags,  
    CBrush* pBrush = NULL);

 
BOOL DrawState(
    CPoint pt,  
    CSize size,  
    LPCTSTR lpszText,  
    UINT nFlags,  
    BOOL bPrefixText = TRUE,  
    int nTextLen = 0,  
    HBRUSH hBrush = NULL);

 
BOOL DrawState(
    CPoint pt,  
    CSize size,  
    LPCTSTR lpszText,  
    UINT nFlags,  
    BOOL bPrefixText = TRUE,  
    int nTextLen = 0,  
    CBrush* pBrush = NULL);

 
BOOL DrawState(
    CPoint pt,  
    CSize size,  
    DRAWSTATEPROC lpDrawProc,  
    LPARAM lData,  
    UINT nFlags,  
    HBRUSH hBrush = NULL);

 
BOOL DrawState(
    CPoint pt,  
    CSize size,  
    DRAWSTATEPROC lpDrawProc,  
    LPARAM lData,  
    UINT nFlags,  
    CBrush* pBrush = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pt`  
 Especifica la ubicación de la imagen.  
  
 `size`  
 Especifica el tamaño de la imagen.  
  
 `hBitmap`  
 Identificador de un mapa de bits.  
  
 `nFlags`  
 Marcadores que especifican el tipo de imagen y el estado. Consulte [DrawState](http://msdn.microsoft.com/library/windows/desktop/dd162496) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para los posibles `nFlags` tipos y Estados.  
  
 `hBrush`  
 Identificador de un pincel.  
  
 `pBitmap`  
 Puntero a un objeto CBitmap.  
  
 `pBrush`  
 Puntero a un objeto CBrush.  
  
 `hIcon`  
 Identificador de un icono.  
  
 `lpszText`  
 Puntero al texto.  
  
 *bPrefixText*  
 Texto que puede contener una tecla de acceso del acelerador. El `lData` parámetro especifica la dirección de la cadena y el `nTextLen` parámetro especifica la longitud. Si `nTextLen` es 0, la cadena se supone que terminada en null.  
  
 `nTextLen`  
 Longitud de la cadena de texto que señala `lpszText`. Si `nTextLen` es 0, la cadena se supone que terminada en null.  
  
 *lpDrawProc*  
 Puntero a una función de devolución de llamada que se usa para representar una imagen. Este parámetro es necesario si la imagen se escribe en `nFlags` es **DST_COMPLEX**. Es opcional y puede ser **NULL** si el tipo de imagen es **DST_TEXT**. Para los demás tipos de imagen, se omite este parámetro. Para obtener más información acerca de la función de devolución de llamada, consulte la [DrawStateProc](http://msdn.microsoft.com/library/windows/desktop/dd162497) funcionan en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `lData`  
 Especifica información sobre la imagen. El significado de este parámetro depende del tipo de imagen.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
##  <a name="a-namedrawtexta--cdcdrawtext"></a><a name="drawtext"></a>CDC:: DrawText  
 Llame a esta función miembro para dar formato al texto en el rectángulo especificado. Para especificar opciones de formato adicionales, use [CDC::DrawTextEx](#drawtextex).  
  
```  
virtual int DrawText(
    LPCTSTR lpszString,  
    int nCount,  
    LPRECT lpRect,  
    UINT nFormat);

 
int DrawText(
    const CString& str,  
    LPRECT lpRect,  
    UINT nFormat);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszString`  
 Apunta a la cadena que se va a dibujar. Si `nCount` es -1, debe ser la cadena terminada en null.  
  
 `nCount`  
 Especifica el número de caracteres de la cadena. Si `nCount` es –&1;, a continuación, `lpszString` se supone que es un puntero largo a una cadena terminada en null y `DrawText` se calcula automáticamente el recuento de caracteres.  
  
 `lpRect`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura o [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que contiene el rectángulo (en coordenadas lógicas) en el que el texto consiste en dar formato.  
  
 `str`  
 Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene los caracteres especificados para dibujar.  
  
 `nFormat`  
 Especifica el método de dar formato al texto. Puede ser cualquier combinación de los valores descritos para la `uFormat` parámetro en [DrawText](http://msdn.microsoft.com/library/windows/desktop/dd162498) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. (combinar mediante el operador OR bit a bit):  
  
> [!NOTE]
>  Algunos `uFormat` combinaciones de marca para hacer que la cadena pasada a modificarse. Usando **DT_MODIFYSTRING** con cualquiera **DT_END_ELLIPSIS** o **DT_PATH_ELLIPSIS** puede provocar que la cadena que desea modificar, provocando una aserción en el `CString` invalidar. Los valores `DT_CALCRECT`, `DT_EXTERNALLEADING`, **DT_INTERNAL**, `DT_NOCLIP`, y `DT_NOPREFIX` no se puede usar con el `DT_TABSTOP` valor.  
  
### <a name="return-value"></a>Valor devuelto  
 El alto del texto si la función se realiza correctamente.  
  
### <a name="remarks"></a>Comentarios  
 Da formato a texto expandiendo tabulaciones en espacios apropiados, alinear texto a la izquierda, derecha o centro del rectángulo especificado, y dividir texto en líneas que encaje dentro del rectángulo especificado. El tipo de formato especificado por `nFormat`.  
  
 Esta función miembro utiliza la fuente seleccionada, el color de texto y color de fondo del contexto de dispositivo para dibujar el texto. A menos que la `DT_NOCLIP` utiliza formato, `DrawText` recorta el texto para que el texto no aparezcan fuera del rectángulo especificado. Todo el formato se supone que dispone de varias líneas, a menos que el `DT_SINGLELINE` tiene formato.  
  
 Si la fuente seleccionada es demasiado grande para el rectángulo especificado, el `DrawText` función miembro no intenta sustituir una fuente más pequeña.  
  
 Si el `DT_CALCRECT` se especifica el indicador, el rectángulo especificado por `lpRect` se actualizará para reflejar el ancho y alto necesarios para dibujar el texto.  
  
 Si el **TA_UPDATECP** se ha establecido la marca de alineación del texto (consulte [CDC::SetTextAlign](#settextalign)), `DrawText` mostrará texto empezando en la posición actual, en lugar de a la izquierda del rectángulo especificado. `DrawText`no se ajustará el texto cuando el **TA_UPDATECP** se ha establecido la marca (es decir, el `DT_WORDBREAK` marca no tiene ningún efecto).  
  
 Puede establecer el color del texto [CDC::SetTextColor](#settextcolor).  
  
##  <a name="a-namedrawtextexa--cdcdrawtextex"></a><a name="drawtextex"></a>CDC::DrawTextEx  
 Da formato al texto en el rectángulo especificado.  
  
```  
virtual int DrawTextEx(
    LPTSTR lpszString,  
    int nCount,  
    LPRECT lpRect,  
    UINT nFormat,
    LPDRAWTEXTPARAMS lpDTParams);

 
int DrawTextEx(
    const CString& str,  
    LPRECT lpRect,  
    UINT nFormat,
    LPDRAWTEXTPARAMS lpDTParams);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszString`  
 Apunta a la cadena que se va a dibujar. Si `nCount` es –&1;, la cadena debe ser terminadas en null.  
  
 `nCount`  
 Especifica el número de caracteres de la cadena. Si `nCount` es –&1;, a continuación, `lpszString` se supone que es un puntero largo a una cadena terminada en null y `DrawText` se calcula automáticamente el recuento de caracteres.  
  
 `lpRect`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura o [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que contiene el rectángulo (en coordenadas lógicas) en el que el texto consiste en dar formato.  
  
 `str`  
 Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene los caracteres especificados para dibujar.  
  
 `nFormat`  
 Especifica el método de dar formato al texto. Puede ser cualquier combinación de los valores descritos para la `uFormat` parámetro en [DrawText](http://msdn.microsoft.com/library/windows/desktop/dd162498) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. (Combinar con el bit a bit `OR` operador):  
  
> [!NOTE]
>  Algunos `uFormat` combinaciones de marca para hacer que la cadena pasada a modificarse. Usando **DT_MODIFYSTRING** con cualquiera **DT_END_ELLIPSIS** o **DT_PATH_ELLIPSIS** puede provocar que la cadena que desea modificar, provocando una aserción en el `CString` invalidar. Los valores `DT_CALCRECT`, `DT_EXTERNALLEADING`, **DT_INTERNAL**, `DT_NOCLIP`, y `DT_NOPREFIX` no se puede usar con el `DT_TABSTOP` valor.  
  
 `lpDTParams`  
 Puntero a un [DRAWTEXTPARAMS](http://msdn.microsoft.com/library/windows/desktop/dd162500) opciones de estructura que especifica el formato adicional. Este parámetro puede ser **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Da formato a texto expandiendo tabulaciones en espacios apropiados, alinear texto a la izquierda, derecha o centro del rectángulo especificado, y dividir texto en líneas que encaje dentro del rectángulo especificado. El tipo de formato especificado por `nFormat` y `lpDTParams`. Para obtener más información, consulte [CDC:: DrawText](#drawtext) y [DrawTextEx](http://msdn.microsoft.com/library/windows/desktop/dd162499) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Puede establecer el color del texto [CDC::SetTextColor](#settextcolor).  
  
##  <a name="a-nameellipsea--cdcellipse"></a><a name="ellipse"></a>CDC::Ellipse  
 Dibuja una elipse.  
  
```  
BOOL Ellipse(
    int x1,  
    int y1,  
    int x2,  
    int y2);  
  
BOOL Ellipse(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `x1`  
 Especifica la coordenada x lógica de la esquina superior izquierda del rectángulo delimitador de la elipse.  
  
 `y1`  
 Especifica la coordenada y lógica de la esquina superior izquierda del rectángulo delimitador de la elipse.  
  
 `x2`  
 Especifica la coordenada x lógica de la esquina inferior derecha del rectángulo delimitador de la elipse.  
  
 `y2`  
 Especifica la coordenada y lógica de la esquina inferior derecha del rectángulo delimitador de la elipse.  
  
 `lpRect`  
 Especifica el que rectángulo delimitador de la elipse. También puede pasar un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto para este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El centro de la elipse es el centro del rectángulo delimitador especificado por `x1`, `y1`, `x2`, y `y2`, o `lpRect`. La elipse se dibuja con el lápiz actual y su interior se rellena con el pincel actual.  
  
 La figura dibujada por esta función extiende hasta, pero no incluye las coordenadas derecho e inferior. Esto significa que es el alto de la figura `y2` : `y1` y el ancho de la figura es `x2` : `x1`.  
  
 Si el ancho o el alto del rectángulo delimitador es 0, no se dibuja ninguna elipse.  
  
##  <a name="a-nameenddoca--cdcenddoc"></a><a name="enddoc"></a>CDC::EndDoc  
 Finaliza un trabajo de impresión iniciado mediante una llamada a la [StartDoc](#startdoc) función miembro.  
  
```  
int EndDoc();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Mayor o igual a 0 si la función se realiza correctamente, o un valor negativo si se produjo un error.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro reemplaza la **ENDDOC** escape de impresora y se debe llamar inmediatamente después de finalizar un trabajo de impresión correcta.  
  
 Si una aplicación encuentra un error de impresión o cancelar la operación de impresión, no debe intentar finalizar la operación utilizando `EndDoc` o [AbortDoc](#abortdoc). GDI finaliza automáticamente la operación antes de devolver el valor de error.  
  
 Esta función no debe usarse dentro de metarchivos.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CDC::StartDoc](#startdoc).  
  
##  <a name="a-nameendpagea--cdcendpage"></a><a name="endpage"></a>CDC::EndPage  
 Informa al dispositivo que la aplicación ha terminado de escribir en una página.  
  
```  
int EndPage();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Mayor o igual a 0 si la función se realiza correctamente, o un valor negativo si se produjo un error.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se utiliza normalmente para dirigir el controlador de dispositivo para avanzar a una página nueva.  
  
 Esta función miembro reemplaza la **NEWFRAME** de escape de impresora. A diferencia de **NEWFRAME**, siempre se llama a esta función después de imprimir una página.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CDC::StartDoc](#startdoc).  
  
##  <a name="a-nameendpatha--cdcendpath"></a><a name="endpath"></a>CDC::EndPath  
 Cierra un corchete de cierre de la ruta de acceso y selecciona la ruta de acceso definida por el corchete de cierre en el contexto de dispositivo.  
  
```  
BOOL EndPath();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CDC:: beginpath](#beginpath).  
  
##  <a name="a-nameenumobjectsa--cdcenumobjects"></a><a name="enumobjects"></a>CDC:: EnumObjects  
 Enumera los lápices y pinceles disponibles en un contexto de dispositivo.  
  
```  
int EnumObjects(
    int nObjectType,  
    int (CALLBACK* lpfn)(
    LPVOID,
    LPARAM),  
    LPARAM lpData);
```  
  
### <a name="parameters"></a>Parámetros  
 *nObjectType*  
 Especifica el tipo de objeto. Puede tener los valores **OBJ_BRUSH** o **OBJ_PEN**.  
  
 `lpfn`  
 Es la dirección de la instancia del procedimiento de la función de devolución de llamada proporcionada por la aplicación. Consulte la sección "Comentarios".  
  
 `lpData`  
 Apunta a los datos proporcionados por la aplicación. Los datos se pasan a la función de devolución de llamada junto con la información de objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Especifica el último valor devuelto por la [función de devolución de llamada](../../mfc/reference/callback-function-for-cdc-enumobjects.md). Su significado es definido por el usuario.  
  
### <a name="remarks"></a>Comentarios  
 Para cada objeto de un tipo determinado, se llama la función de devolución de llamada que se pasa con la información de ese objeto. El sistema llama a la función de devolución de llamada hasta que no hay más objetos o la función de devolución de llamada devuelve 0.  
  
 Tenga en cuenta que las características nuevas de Microsoft Visual C++ permiten utilizar una función normal como pasa a la función para `EnumObjects`. La dirección se pasa a `EnumObjects` es un puntero a una función exportada con **exportar** y con la convención de llamada Pascal. En las aplicaciones en modo protegido, no es necesario crear esta función con la función MakeProcInstance de Windows o liberar la función después de su uso con la función de FreeProcInstance Windows.  
  
 También es necesario exportar el nombre de función en una **exportaciones** instrucción en el archivo de definición de módulo de la aplicación. Puede usar el **exportar** función modificador, como en  
  
 **EXPORTAR de devolución de llamada de int** AFunction **(LPSTR**, **LPSTR);**  
  
 Para hacer que el compilador emita el registro de exportación adecuados para la exportación por su nombre sin alias. Esto funciona para la mayoría de las necesidades. En algunos casos especiales, como exportar una función por ordinal o alias de la exportación, deberá utilizar un **exportaciones** instrucción en un archivo de definición de módulo.  
  
 Para compilar programas de Microsoft Foundation, normalmente utilizará el /GA y las opciones de compilador /GEs. No se utiliza la opción del compilador /Gw con Microsoft Foundation classes. (Si utiliza la función de Windows **MakeProcInstance**, deberá convertir explícitamente el puntero de función devuelto desde **FARPROC** al tipo necesario en esta API.) Interfaces de devolución de llamada registro ahora tienen seguridad de tipos (debe pasar un puntero a función que señala el tipo correcto de la función de devolución de llamada específica).  
  
 Tenga en cuenta que todas las funciones de devolución de llamada deben capturar las excepciones que Microsoft Foundation antes de volver a Windows, puesto que no se producirán excepciones en los límites de la devolución de llamada. Para obtener más información sobre las excepciones, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#35;](../../mfc/codesnippet/cpp/cdc-class_7.cpp)]  
  
##  <a name="a-nameescapea--cdcescape"></a><a name="escape"></a>CDC::escape  
 Esta función miembro es prácticamente obsoleta para la programación de Win32.  
  
```  
virtual int Escape(
    int nEscape,  
    int nCount,  
    LPCSTR lpszInData,  
    LPVOID lpOutData);

 
int Escape(
    int nEscape,  
    int nInputSize,  
    LPCSTR lpszInputData,  
    int nOutputSize,  
    LPSTR lpszOutputData);
```  
  
### <a name="parameters"></a>Parámetros  
 `nEscape`  
 Especifica la función de escape que se realizará.  
  
 Para obtener una lista completa de funciones de escape, vea [Escape](http://msdn.microsoft.com/library/windows/desktop/dd162701) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `nCount`  
 Especifica el número de bytes de los datos señalados por `lpszInData`.  
  
 `lpszInData`  
 Señala a la estructura de datos de entrada necesarios para este escape.  
  
 `lpOutData`  
 Señala a la estructura que se va a recibir la salida de este escape. El `lpOutData` parámetro es **NULL** si no se devuelve ningún dato.  
  
 `nInputSize`  
 Especifica el número de bytes de datos que señala el `lpszInputData` parámetro.  
  
 `lpszInputData`  
 Señala a la estructura de entrada necesarios para el escape especificado.  
  
 `nOutputSize`  
 Especifica el número de bytes de datos que señala el `lpszOutputData` parámetro.  
  
 `lpszOutputData`  
 Señala a la estructura que recibe la salida de este escape. Este parámetro debe ser **NULL** si no se devuelve ningún dato.  
  
### <a name="return-value"></a>Valor devuelto  
 Se devuelve un valor positivo si la función se realiza correctamente, excepto para la **QUERYESCSUPPORT** escape, que sólo se comprueba para la implementación. Devuelve cero si no se ha implementado el escape. Se devuelve un valor negativo si se produjo un error. Los valores de error comunes son los siguientes:  
  
- **SP_ERROR** error General.  
  
- **SP_OUTOFDISK** no hay suficiente espacio en disco está disponible actualmente para la puesta en y no hay más espacio volverá a estar disponible.  
  
- **SP_OUTOFMEMORY** no hay suficiente memoria disponible para la cola de impresión.  
  
- **SP_USERABORT** usuario finalizó el trabajo a través del Administrador de impresión.  
  
### <a name="remarks"></a>Comentarios  
 De la original escape de impresora, sólo **QUERYESCSUPPORT** es compatible con aplicaciones de Win32. Otros caracteres de escape de impresora están obsoletos y sólo se admiten por compatibilidad con aplicaciones de 16 bits.  
  
 Para la programación de Win32 `CDC` ahora proporciona seis funciones de miembro que sustituyen a sus secuencias de escape de impresora correspondiente:  
  
- [CDC::AbortDoc](#abortdoc)  
  
- [CDC::EndDoc](#enddoc)  
  
- [CDC::EndPage](#endpage)  
  
- [CDC:: SETABORTPROC](#setabortproc)  
  
- [CDC::StartDoc](#startdoc)  
  
- [CDC::StartPage](#startpage)  
  
 Además, [CDC:: GetDeviceCaps](#getdevicecaps) admite índices de Win32 que sustituyen a otras secuencias de escape de impresora. Consulte [GetDeviceCaps](http://msdn.microsoft.com/library/windows/desktop/dd144877) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información.  
  
 Esta función miembro permite que las aplicaciones tener acceso a funciones de un dispositivo concreto que no están directamente disponibles a través de GDI.  
  
 Si la aplicación utiliza los valores de escape predefinidos, utilice la primera versión. Si la aplicación define los valores de escape privada, utilice la segunda versión. Consulte [ExtEscape](http://msdn.microsoft.com/library/windows/desktop/dd162708) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información acerca de la segunda versión.  
  
##  <a name="a-nameexcludecliprecta--cdcexcludecliprect"></a><a name="excludecliprect"></a>CDC::ExcludeClipRect  
 Crea una nueva región de recorte que consta de la región de recorte existente menos el rectángulo especificado.  
  
```  
int ExcludeClipRect(
    int x1,  
    int y1,  
    int x2,  
    int y2);  
  
int ExcludeClipRect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `x1`  
 Especifica la coordenada x lógica de la esquina superior izquierda del rectángulo.  
  
 `y1`  
 Especifica la coordenada y lógica de la esquina superior izquierda del rectángulo.  
  
 `x2`  
 Especifica la coordenada x lógica de la esquina inferior derecha del rectángulo.  
  
 `y2`  
 Especifica la coordenada y lógica de la esquina inferior derecha del rectángulo.  
  
 `lpRect`  
 Especifica el rectángulo. También puede ser un `CRect` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Especifica el tipo de la nueva región recorte. Puede ser cualquiera de los siguientes valores:  
  
- **COMPLEXREGION** la región tiene bordes se superponen.  
  
- **ERROR** se ha creado ninguna región.  
  
- **NULLREGION** la región está vacía.  
  
- **SIMPLEREGION** la región no tiene bordes superpuestos.  
  
### <a name="remarks"></a>Comentarios  
 El ancho del rectángulo, especificado por el valor absoluto de `x2` : `x1`, no debe superar los 32.767 unidades. Este límite se aplica a la altura del rectángulo también.  
  
##  <a name="a-nameexcludeupdatergna--cdcexcludeupdatergn"></a><a name="excludeupdatergn"></a>CDC::ExcludeUpdateRgn  
 Impide el dibujo en áreas no válidas de una ventana de excluir una región actualizada en la ventana de la región de recorte asociada a la `CDC` objeto.  
  
```  
int ExcludeUpdateRgn(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Señala al objeto de ventana cuya ventana se está actualizando.  
  
### <a name="return-value"></a>Valor devuelto  
 El tipo de región excluido. Puede ser cualquiera de los siguientes valores:  
  
- **COMPLEXREGION** la región tiene bordes se superponen.  
  
- **ERROR** se ha creado ninguna región.  
  
- **NULLREGION** la región está vacía.  
  
- **SIMPLEREGION** la región no tiene bordes superpuestos.  
  
##  <a name="a-nameextfloodfilla--cdcextfloodfill"></a><a name="extfloodfill"></a>CDC::ExtFloodFill  
 Rellena un área de la superficie de pantalla con el pincel actual.  
  
```  
BOOL ExtFloodFill(
    int x,  
    int y,  
    COLORREF crColor,  
    UINT nFillType);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada x lógica del punto donde comienza el llenado.  
  
 *y*  
 Especifica la coordenada y lógica del punto donde comienza el llenado.  
  
 `crColor`  
 Especifica el color del límite o el área que se rellena. La interpretación de `crColor` depende del valor de `nFillType`.  
  
 `nFillType`  
 Especifica el tipo de relleno que se va a realizar. Debe ser uno de los siguientes valores:  
  
- **FLOODFILLBORDER** el área de relleno está limitado por el color especificado por `crColor`. Este estilo es idéntico para el llenado realizado por `FloodFill`.  
  
- **FLOODFILLSURFACE** el área de relleno se define mediante el color especificado por `crColor`. Rellenar continúa hacia afuera en todas las direcciones mientras se encuentra el color. Este estilo es útil para rellenar las áreas con límites de varios colores.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; en caso contrario, 0 si el llenado no se pudo completar, si el punto especificado tiene el límite de color especificado por `crColor` (si **FLOODFILLBORDER** se solicitó), si el punto especificado no tiene el color especificado por `crColor` (si **FLOODFILLSURFACE** se solicitó), o si el punto está fuera de la región de recorte.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro ofrece más flexibilidad que `FloodFill` ya que puede especificar un tipo de relleno en `nFillType`.  
  
 Si `nFillType` está establecido en **FLOODFILLBORDER**, se supone que el área completamente estar limitadas por el color especificado por `crColor`. La función comienza en el punto especificado por *x* y *y* y se rellena en todas las direcciones al límite de color.  
  
 Si `nFillType` está establecido en **FLOODFILLSURFACE**, la función comienza en el punto especificado por *x* y *y* y continúa en todas direcciones, llenando todas las áreas adyacentes que contienen el color especificado por `crColor`.  
  
 Sólo los contextos de dispositivo de memoria y los dispositivos que admiten la compatibilidad con la tecnología de pantalla de trama `ExtFloodFill`. Para obtener más información, consulte el [GetDeviceCaps](#getdevicecaps) función miembro.  
  
##  <a name="a-nameexttextouta--cdcexttextout"></a><a name="exttextout"></a>CDC::ExtTextOut  
 Llame a esta función miembro para escribir una cadena de caracteres dentro de una región rectangular con la fuente seleccionada actualmente.  
  
```  
virtual BOOL ExtTextOut(
    int x,  
    int y,  
    UINT nOptions,  
    LPCRECT lpRect,  
    LPCTSTR lpszString,  
    UINT nCount,  
    LPINT lpDxWidths);

 
BOOL ExtTextOut(
    int x,  
    int y,  
    UINT nOptions,  
    LPCRECT lpRect,  
    const CString& str,  
    LPINT lpDxWidths);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada x lógica de la celda de carácter para el primer carácter de la cadena especificada.  
  
 *y*  
 Especifica la coordenada y lógica de la parte superior de la celda de carácter para el primer carácter de la cadena especificada.  
  
 `nOptions`  
 Especifica el tipo de rectángulo. Este parámetro puede ser de uno, dos o ninguno de los siguientes valores:  
  
- **ETO_CLIPPED** especifica que el texto se recorta al rectángulo.  
  
- **ETO_OPAQUE** especifica que el color de fondo actual rellena el rectángulo. (Puede establecer y consultar el color de fondo actual con el [SetBkColor](#setbkcolor) y [función miembro GetBkColor](#getbkcolor) funciones miembro.)  
  
 `lpRect`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura que determina las dimensiones del rectángulo. Este parámetro puede ser **NULL**. También puede pasar un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto para este parámetro.  
  
 `lpszString`  
 Apunta a la cadena de caracteres especificada para dibujar. También puede pasar un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto para este parámetro.  
  
 `nCount`  
 Especifica el número de caracteres de la cadena.  
  
 `lpDxWidths`  
 Apunta a una matriz de valores que indican la distancia entre los orígenes de las celdas de carácter adyacentes. Por ejemplo, `lpDxWidths`[ **] unidades lógicas para separar los orígenes de celda de carácter ** y la celda de carácter ** + 1. Si `lpDxWidths` es **NULL**, `ExtTextOut` utiliza el espaciado predeterminado entre caracteres.  
  
 `str`  
 Un `CString` objeto que contiene los caracteres especificados para dibujar.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 La región rectangular que puede ser opaca (que se rellena con el color de fondo actual) y puede ser una región de recorte.  
  
 Si `nOptions` es 0 y `lpRect` es **NULL**, la función escribe texto en el contexto de dispositivo sin utilizar una región rectangular. De forma predeterminada, la función no usa ni actualiza la posición actual. Si una aplicación necesita actualizar la posición actual cuando llama a `ExtTextOut`, la aplicación puede llamar a la `CDC` función miembro [SetTextAlign](#settextalign) con `nFlags` establecido en **TA_UPDATECP**. Cuando se establece este marcador, Windows pasa por alto *x* y *y* en llamadas posteriores a `ExtTextOut` y utiliza la posición actual en su lugar. Cuando una aplicación usa **TA_UPDATECP** para actualizar la posición actual, `ExtTextOut` establece la posición actual hasta el final de la línea de texto anterior o a la posición especificada por el último elemento de la matriz señalada por `lpDxWidths`, lo que sea mayor.  
  
##  <a name="a-namefillpatha--cdcfillpath"></a><a name="fillpath"></a>CDC::FillPath  
 Figuras abiertas en la ruta de acceso actual se cierra y rellena el interior de la ruta de acceso mediante el pincel actual y el modo de relleno de polígono.  
  
```  
BOOL FillPath();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Después se rellena su interior, se descarta la ruta de acceso en el contexto del dispositivo.  
  
##  <a name="a-namefillrecta--cdcfillrect"></a><a name="fillrect"></a>CDC::fillRect  
 Llame a esta función miembro para rellenar un rectángulo con el pincel especificado.  
  
```  
void FillRect(
    LPCRECT lpRect,  
    CBrush* pBrush);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura que contiene las coordenadas lógicas del rectángulo que se va a rellenar. También puede pasar un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto para este parámetro.  
  
 `pBrush`  
 Identifica el pincel utilizado para rellenar el rectángulo.  
  
### <a name="remarks"></a>Comentarios  
 La función rellena el rectángulo completando, incluidos los bordes izquierdos y superior, pero no rellena los bordes derecho e inferior.  
  
 El pincel necesita al crearse utilizando la [CBrush](../../mfc/reference/cbrush-class.md) funciones miembro [CreateHatchBrush](../../mfc/reference/cbrush-class.md#createhatchbrush), [CreatePatternBrush](../../mfc/reference/cbrush-class.md#createpatternbrush), y [CreateSolidBrush](../../mfc/reference/cbrush-class.md#createsolidbrush), o recuperar el `GetStockObject` función de Windows.  
  
 Al rellenar el rectángulo especificado, `FillRect` no incluye los lados del rectángulo derecho e inferior. GDI rellena un rectángulo hasta, pero no incluye la fila de columna y la parte inferior derecha, independientemente del modo de asignación actual. `FillRect`Compara los valores de la **arriba**, **inferior**, **izquierdo**, y **derecho** miembros del rectángulo especificado. Si **inferior** es menor o igual a **arriba**, o si **derecho** es menor o igual a **izquierdo**, no se dibuja el rectángulo.  
  
 `FillRect`es similar a [CDC::FillSolidRect](#fillsolidrect); sin embargo, `FillRect` toma un pincel y, por tanto, se puede utilizar para rellenar un rectángulo con un color sólido, un color interpolado, pinceles de trama o un patrón. `FillSolidRect`utiliza sólo colores sólidos (indicado por un **COLORREF** parámetro). `FillRect`Normalmente es más lenta que `FillSolidRect`.  
  
##  <a name="a-namefillrgna--cdcfillrgn"></a><a name="fillrgn"></a>CDC::FillRgn  
 Rellena el área especificada por `pRgn` con el pincel especificado por `pBrush`.  
  
```  
BOOL FillRgn(
    CRgn* pRgn,  
    CBrush* pBrush);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRgn`  
 Puntero a la región que se debe rellenar. Las coordenadas de la región determinada se especifican en unidades lógicas.  
  
 `pBrush`  
 Identifica el pincel que se usará para rellenar la región.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El pincel debe crearse utilizando la `CBrush` funciones miembro `CreateHatchBrush`, `CreatePatternBrush`, `CreateSolidBrush`, o recuperarse por **GetStockObject**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRgn::CreateRoundRectRgn](../../mfc/reference/crgn-class.md#createroundrectrgn).  
  
##  <a name="a-namefillsolidrecta--cdcfillsolidrect"></a><a name="fillsolidrect"></a>CDC::FillSolidRect  
 Llame a esta función miembro para rellenar el rectángulo especificado con el color sólido especificado.  
  
```  
void FillSolidRect(
    LPCRECT lpRect,  
    COLORREF clr);

 
void FillSolidRect(
    int x,  
    int y,  
    int cx,  
    int cy,  
    COLORREF clr);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Especifica el rectángulo delimitador (en unidades lógicas). Puede pasar un puntero a un [RECT](../../mfc/reference/rect-structure1.md) estructura de datos o un `CRect` objeto para este parámetro.  
  
 `clr`Especifica el color que se usará para rellenar el rectángulo.  
  
 *x*  
 Especifica la coordenada x lógica de la esquina superior izquierda del rectángulo.  
  
 *y*  
 Especifica la coordenada y lógica de la esquina superior izquierda del rectángulo de destino.  
  
 `cx`  
 Especifica el ancho del rectángulo.  
  
 `cy`  
 Especifica el alto del rectángulo.  
  
### <a name="remarks"></a>Comentarios  
 `FillSolidRect`es muy similar a [CDC::FillRect](#fillrect); sin embargo, `FillSolidRect` utiliza sólo colores sólidos (indicado por el **COLORREF** parámetro), mientras que `FillRect` toma un pincel y, por tanto, se puede utilizar para rellenar un rectángulo con un color sólido, un color interpolado, pinceles de trama o un patrón. `FillSolidRect`Normalmente es más rápido que `FillRect`.  
  
> [!NOTE]
>  Cuando se llama a `FillSolidRect`, el color de fondo que se ha configurado previamente con [SetBkColor](#setbkcolor), se establece en el color indicado por `clr`.  
  
##  <a name="a-nameflattenpatha--cdcflattenpath"></a><a name="flattenpath"></a>CDC::FlattenPath  
 Transforma las curvas en la ruta seleccionada en el contexto de dispositivo actual y cada curva se convierte en una secuencia de líneas.  
  
```  
BOOL FlattenPath();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
##  <a name="a-namefloodfilla--cdcfloodfill"></a><a name="floodfill"></a>CDC::FloodFill  
 Rellena un área de la superficie de pantalla con el pincel actual.  
  
```  
BOOL FloodFill(
    int x,  
    int y,  
    COLORREF crColor);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada x lógica del punto donde comienza el llenado.  
  
 *y*  
 Especifica la coordenada y lógica del punto donde comienza el llenado.  
  
 `crColor`  
 Especifica el color del límite.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, se devuelve 0 si no se pudo completar el rellenado, el punto especificado tiene el color del límite especificado por `crColor`, o el punto está fuera de la región de recorte.  
  
### <a name="remarks"></a>Comentarios  
 El área se supone que se limite como especificado por `crColor`. El `FloodFill` función comienza en el punto especificado por *x* y *y* y continúa en todas las direcciones al límite de color.  
  
 Sólo los contextos de dispositivo de memoria y los dispositivos que admiten la compatibilidad con la tecnología de pantalla de trama del `FloodFill` función miembro. Para obtener información acerca de **RC_BITBLT** capacidad, consulte el `GetDeviceCaps` función miembro.  
  
 El `ExtFloodFill` función proporciona una funcionalidad similar pero mayor flexibilidad.  
  
##  <a name="a-nameframerecta--cdcframerect"></a><a name="framerect"></a>FrameRect  
 Dibuja un borde alrededor del rectángulo especificado por `lpRect`.  
  
```  
void FrameRect(
    LPCRECT lpRect,  
    CBrush* pBrush);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura o [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que contiene las coordenadas lógicas de las esquinas superior izquierda e inferior derecha del rectángulo. También puede pasar un `CRect` objeto para este parámetro.  
  
 `pBrush`  
 Identifica el pincel que se utilizará para el rectángulo de tramas.  
  
### <a name="remarks"></a>Comentarios  
 La función utiliza el pincel determinado para dibujar el borde. El ancho y el alto del borde es siempre 1 unidad lógica.  
  
 Si el rectángulo **inferior** coordenada es menor o igual a **arriba**, o si **derecho** es menor o igual a **izquierdo**, no se dibuja el rectángulo.  
  
 El borde dibujado por `FrameRect` está en la misma posición que un borde dibujado por el **rectángulo** función de miembro con las mismas coordenadas (si **rectángulo** utiliza un lápiz que es 1 unidad lógica amplia). No se rellena el interior del rectángulo mediante `FrameRect`.  
  
##  <a name="a-nameframergna--cdcframergn"></a><a name="framergn"></a>CDC::FrameRgn  
 Dibuja un borde alrededor de la región especificada por `pRgn` con el pincel especificado por `pBrush`.  
  
```  
BOOL FrameRgn(
    CRgn* pRgn,  
    CBrush* pBrush,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRgn`  
 Apunta a la `CRgn` objeto que identifica la región donde se incluyen en un borde. Las coordenadas de la región determinada se especifican en unidades lógicas.  
  
 `pBrush`  
 Apunta a la `CBrush` objeto que identifica el pincel que se utilizará para dibujar el borde.  
  
 `nWidth`  
 Especifica el ancho del borde de pinceladas vertical en unidades del dispositivo.  
  
 `nHeight`  
 Especifica el alto del borde de pinceladas horizontales en unidades del dispositivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRgn::CombineRgn](../../mfc/reference/crgn-class.md#combinergn).  
  
##  <a name="a-namefromhandlea--cdcfromhandle"></a><a name="fromhandle"></a>CDC::FromHandle  
 Devuelve un puntero a un `CDC` objeto cuando se especifica un identificador para un contexto de dispositivo.  
  
```  
static CDC* PASCAL FromHandle(HDC hDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `hDC`  
 Contiene un identificador de un contexto de dispositivo de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 El puntero puede ser temporal y no debe almacenarse más allá de su uso inmediato.  
  
### <a name="remarks"></a>Comentarios  
 Si no hay un objeto `CDC` asociado al identificador, se crea y asocia un objeto `CDC` temporal.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPrintDialog::GetPrinterDC](../../mfc/reference/cprintdialog-class.md#getprinterdc).  
  
##  <a name="a-namegetarcdirectiona--cdcgetarcdirection"></a><a name="getarcdirection"></a>CDC::GetArcDirection  
 Devuelve la dirección de arco actual para el contexto de dispositivo.  
  
```  
int GetArcDirection() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Especifica la dirección de arco actual, si se realiza correctamente. Siguiente es los valores de retorno válidos:  
  
- **AD_COUNTERCLOCKWISE** arcos y rectángulos dibujados a la izquierda.  
  
- **AD_CLOCKWISE** arcos y rectángulos dibujados hacia la derecha.  
  
 Si se produce un error, el valor devuelto es cero.  
  
### <a name="remarks"></a>Comentarios  
 Funciones de arco y rectángulo utilizan la dirección del arco.  
  
##  <a name="a-namegetaspectratiofiltera--cdcgetaspectratiofilter"></a><a name="getaspectratiofilter"></a>CDC::GetAspectRatioFilter  
 Recupera el valor para el filtro de relación de aspecto actual.  
  
```  
CSize GetAspectRatioFilter() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CSize` que representa la relación de aspecto utilizada por el filtro de relación de aspecto actual del objeto.  
  
### <a name="remarks"></a>Comentarios  
 La relación de aspecto es la relación formada por el ancho de píxel de un dispositivo y el alto. Información acerca de la relación de aspecto de un dispositivo se utiliza en la creación, selección y presentación de fuentes. Windows proporciona un filtro especial, el filtro de la relación de aspecto, seleccione fuentes diseñados para una relación de aspecto determinada de todas las fuentes disponibles. El filtro utiliza la proporción especificada por el `SetMapperFlags` función miembro.  
  
##  <a name="a-namegetbkcolora--cdcgetbkcolor"></a><a name="getbkcolor"></a>CDC::GetBkColor  
 Devuelve el color de fondo actual.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de color RGB.  
  
### <a name="remarks"></a>Comentarios  
 Si el modo de segundo plano es **OPACO**, el sistema utiliza el color de fondo para rellenar los huecos en líneas con estilo, los espacios entre las líneas de sombreado de pinceles y el fondo de las celdas de caracteres. El sistema también utiliza el color de fondo al convertir mapas de bits entre color y contextos de dispositivo monocromático.  
  
##  <a name="a-namegetbkmodea--cdcgetbkmode"></a><a name="getbkmode"></a>CDC::GetBkMode  
 Devuelve el modo de segundo plano.  
  
```  
int GetBkMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de fondo actual, que puede ser **OPACO** o **TRANSPARENTE**.  
  
### <a name="remarks"></a>Comentarios  
 El modo de segundo plano define si el sistema quita los colores de fondo existentes en la superficie de dibujo antes de dibujar el texto, pinceles de trama o cualquier estilo de lápiz que no es una línea sólida.  
  
##  <a name="a-namegetboundsrecta--cdcgetboundsrect"></a><a name="getboundsrect"></a>CDC::GetBoundsRect  
 Devuelve el rectángulo delimitador acumulado actual para el contexto de dispositivo especificado.  
  
```  
UINT GetBoundsRect(
    LPRECT lpRectBounds,  
    UINT flags);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRectBounds`  
 Señala a un búfer que recibirá el rectángulo delimitador actual. Se devuelve el rectángulo en coordenadas lógicas.  
  
 `flags`  
 Especifica si se puede borrar después de que se devuelve el rectángulo delimitador. Este parámetro debe ser cero o se establece en el valor siguiente:  
  
- **DCB_RESET** fuerza el rectángulo delimitador que se borre una vez que se devuelve.  
  
### <a name="return-value"></a>Valor devuelto  
 Especifica el estado actual del rectángulo delimitador si la función se realiza correctamente. Puede ser una combinación de los siguientes valores:  
  
- **DCB_ACCUMULATE** se está produciendo la acumulación del rectángulo de límite.  
  
- **DCB_RESET** rectángulo de selección está vacío.  
  
- **DCB_SET** rectángulo de selección no está vacía.  
  
- **DCB_ENABLE** acumulación de límite está activado.  
  
- **DCB_DISABLE** acumulación de límite está desactivada.  
  
##  <a name="a-namegetbrushorga--cdcgetbrushorg"></a><a name="getbrushorg"></a>CDC::GetBrushOrg  
 Recupera el origen (en unidades de dispositivo) del pincel seleccionado actualmente para el contexto de dispositivo.  
  
```  
CPoint GetBrushOrg() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El origen actual del pincel (en unidades de dispositivo) como un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Origen del pincel inicial está en (0,0) del área de cliente. El valor devuelto especifica este punto en unidades del dispositivo en relación con el origen de la ventana del escritorio.  
  
##  <a name="a-namegetcharacterplacementa--cdcgetcharacterplacement"></a><a name="getcharacterplacement"></a>CDC::GetCharacterPlacement  
 Recupera varios tipos de información en una cadena de caracteres.  
  
```  
DWORD GetCharacterPlacement(
    LPCTSTR lpString,  
    int nCount,  
    int nMaxExtent,  
    LPGCP_RESULTS lpResults,  
    DWORD dwFlags) const;  
  
DWORD GetCharacterPlacement(
    CString& str,  
    int nMaxExtent,  
    LPGCP_RESULTS lpResults,  
    DWORD dwFlags) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpString`  
 Puntero a la cadena de caracteres para procesar.  
  
 `nCount`  
 Especifica la longitud de la cadena. Para la versión ANSI, es un recuento de bytes y de la función Unicode es un recuento de palabras. Para obtener más información, consulte [GetCharacterPlacement](http://msdn.microsoft.com/library/windows/desktop/dd144860\(v=vs.85\).aspx).  
  
 `nMaxExtent`  
 Especifica la medida (en unidades lógicas) hasta que se procesa la cadena. Se omiten los caracteres que, si ha procesado, superaría esta extensión. Cálculos en las matrices de ordenación o glifo necesarios se aplican sólo a los caracteres incluidos. Este parámetro se usa únicamente si se especifica el valor GCP_MAXEXTENT en el `dwFlags` parámetro. Como la función procesa la cadena de entrada, cada carácter y su extensión se agrega a la salida, alcance y otras matrices sólo si la extensión total aún no supera el máximo. Una vez que se alcanza el límite, se detendrá el procesamiento.  
  
 lpResults  
 Puntero a un [GCP_Results](http://msdn.microsoft.com/library/windows/desktop/dd144842\(v=vs.85\).aspx) estructura que recibe los resultados de la función.  
  
 `dwFlags`  
 Especifica cómo procesar la cadena en las matrices necesarias. Este parámetro puede tener uno o varios de los valores enumeran en la `dwFlags` sección de la [GetCharacterPlacement](http://msdn.microsoft.com/library/windows/desktop/dd144860\(v=vs.85\).aspx) tema.  
  
 `str`  
 Un puntero a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto de proceso.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto es el ancho y alto de la cadena en unidades lógicas.  
  
 Si la función no se realiza correctamente, el valor devuelto es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la función [GetCharacterPlacement](http://msdn.microsoft.com/library/windows/desktop/dd144860\(v=vs.85\).aspx), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetcharabcwidthsa--cdcgetcharabcwidths"></a><a name="getcharabcwidths"></a>CDC::GetCharABCWidths  
 Recupera el ancho de caracteres consecutivos en un intervalo especificado de la fuente TrueType actual.  
  
```  
BOOL GetCharABCWidths(
    UINT nFirstChar,  
    UINT nLastChar,  
    LPABC lpabc) const;  
  
BOOL GetCharABCWidths(
    UINT nFirstChar,  
    UINT nLastChar,  
    LPABCFLOAT lpABCF) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nFirstChar`  
 Especifica el primer carácter del intervalo de caracteres de la fuente actual para el que se devuelve el ancho de un carácter.  
  
 `nLastChar`  
 Especifica el último carácter del intervalo de caracteres de la fuente actual para el que se devuelve el ancho de un carácter.  
  
 `lpabc`  
 Apunta a una matriz de [ABC](../../mfc/reference/abc-structure.md) estructuras que reciben el ancho de un carácter cuando se devuelve la función. Esta matriz debe contener al menos tantos **ABC** las estructuras como hay caracteres en el intervalo especificado por el `nFirstChar` y `nLastChar` parámetros.  
  
 *lpABCF*  
 Apunta a un búfer proporcionada por la aplicación con una matriz de [ABCFLOAT](../../mfc/reference/abcfloat-structure.md) estructuras para recibir el ancho de un carácter cuando se devuelve la función. Los anchos devueltos por esta función se encuentran en el formato de punto flotante de IEEE.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El ancho se devuelve en unidades lógicas. Esta función se realiza correctamente sólo con fuentes TrueType.  
  
 El rasterizador de TrueType proporciona el espaciado entre caracteres de "ABC" después de haber seleccionado un tamaño específico. Espaciado de "A" es la distancia que se agrega a la posición actual antes de colocar el glifo. Espaciado de "B" es el ancho de la parte negro del glifo. Espaciado de "C" se agrega a la posición actual para tener en cuenta el espacio en blanco a la derecha del glifo. El total avanzada ancho viene determinado por un + B + C.  
  
 Cuando el `GetCharABCWidths` función miembro recupera negativo "A" o "C" ancho de un carácter, ese carácter incluye underhangs o partes sobresalientes.  
  
 Para convertir los anchos ABC en unidades de diseño de fuente, una aplicación debe crear una fuente cuyo alto (como se especifica en el **lfHeight** miembro de la [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) estructura) es igual al valor almacenado en el **ntmSizeEM** miembro de la [NEWTEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd162741) estructura. (El valor de la **ntmSizeEM** miembro se puede recuperar mediante una llamada a la [EnumFontFamilies](http://msdn.microsoft.com/library/windows/desktop/dd162619) función de Windows.)  
  
 Se utilizan los anchos de ABC de carácter predeterminado para los caracteres que están fuera del intervalo de la fuente seleccionada actualmente.  
  
 Para recuperar el ancho de caracteres de fuentes TrueType, las aplicaciones deben utilizar el [GetCharWidth](http://msdn.microsoft.com/library/windows/desktop/dd144861) función de Windows.  
  
##  <a name="a-namegetcharabcwidthsia--cdcgetcharabcwidthsi"></a><a name="getcharabcwidthsi"></a>CDC::GetCharABCWidthsI  
 Recupera el ancho, en unidades lógicas, de los índices de glifo consecutivos en un intervalo especificado de la fuente TrueType actual.  
  
```  
BOOL GetCharABCWidthsI(
    UINT giFirst,  
    UINT cgi,  
    LPWORD pgi,  
    LPABC lpabc) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `giFirst`  
 Especifica el primer índice de glifo en el grupo de índices de glifo consecutivos de la fuente actual. Este parámetro sólo se utiliza si el `pgi` parámetro es **NULL**.  
  
 `cgi`  
 Especifica el número de índices de glifo.  
  
 `pgi`  
 Puntero a una matriz que contiene los índices de glifo. Si el valor es **NULL**, el `giFirst` parámetro se utiliza en su lugar. El `cgi` parámetro especifica el número de índices de glifo en esta matriz.  
  
 `lpabc`  
 Puntero a una matriz de [ABC](http://msdn.microsoft.com/library/windows/desktop/dd162454) estructuras recibir el ancho de un carácter. Esta matriz debe contener al menos tantos **ABC** las estructuras como hay índices de glifo especificadas por el `cgi` parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la función [GetCharABCWidthsI](http://msdn.microsoft.com/library/windows/desktop/dd144859), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetcharwidtha--cdcgetcharwidth"></a><a name="getcharwidth"></a>CDC::GetCharWidth  
 Recupera el ancho de caracteres individuales de un grupo de caracteres consecutivos de la fuente actual, mediante `m_hAttribDC`, el contexto de dispositivo de entrada.  
  
```  
BOOL GetCharWidth(
    UINT nFirstChar,  
    UINT nLastChar,  
    LPINT lpBuffer) const;  
  
BOOL GetCharWidth(
    UINT nFirstChar,  
    UINT nLastChar,  
    float* lpFloatBuffer) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nFirstChar`  
 Especifica el primer carácter de un grupo consecutivo de caracteres de la fuente actual.  
  
 `nLastChar`  
 Especifica el último carácter de un grupo consecutivo de caracteres de la fuente actual.  
  
 `lpBuffer`  
 Señala a un búfer que recibirá los valores de ancho de un grupo de caracteres consecutivos en la fuente actual.  
  
 *lpFloatBuffer*  
 Apunta a un búfer para recibir el ancho de un carácter. Los anchos devueltos están en el formato de punto flotante de IEEE de 32 bits. (El ancho se mide a lo largo de la línea de base de los caracteres).  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Por ejemplo, si `nFirstChar` identifica la letra 'a' y `nLastChar` identifica la letra 'z', la recupera de la función del ancho de todos los caracteres en minúsculas.  
  
 La función almacena los valores en el búfer señalado por `lpBuffer`. Este búfer debe ser suficientemente grande para contener todos los anchos. Es decir, debe haber al menos 26 entradas en el ejemplo dado.  
  
 Si no existe un carácter en el grupo de caracteres consecutivos en una fuente concreta, se le asignará el valor de ancho de carácter predeterminado.  
  
##  <a name="a-namegetcharwidthia--cdcgetcharwidthi"></a><a name="getcharwidthi"></a>CDC::GetCharWidthI  
 Recupera el ancho, en coordenadas lógicas, de los índices de glifo consecutivos en un intervalo especificado de la fuente actual.  
  
```  
BOOL GetCharWidthI(
    UINT giFirst,  
    UINT cgi,  
    LPWORD pgi,  
    LPINT lpBuffer) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `giFirst`  
 Especifica el primer índice de glifo en el grupo de índices de glifo consecutivos de la fuente actual. Este parámetro sólo se utiliza si el `pgi` parámetro es **NULL**.  
  
 `cgi`  
 Especifica el número de índices de glifo.  
  
 `pgi`  
 Puntero a una matriz que contiene los índices de glifo. Si el valor es **NULL**, el `giFirst` parámetro se utiliza en su lugar. El `cgi` parámetro especifica el número de índices de glifo en esta matriz.  
  
 `lpBuffer`  
 Puntero a un búfer que recibe el ancho.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la función [GetCharWidthI](http://msdn.microsoft.com/library/windows/desktop/dd144864), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetclipboxa--cdcgetclipbox"></a><a name="getclipbox"></a>CDC::GetClipBox  
 Recupera las dimensiones del rectángulo delimitador tightest alrededor del límite de recorte actual.  
  
```  
virtual int GetClipBox(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Apunta a la [RECT](../../mfc/reference/rect-structure1.md) estructura o [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que va a recibir las dimensiones del rectángulo.  
  
### <a name="return-value"></a>Valor devuelto  
 Tipo de región de recorte. Puede ser cualquiera de los siguientes valores:  
  
- **COMPLEXREGION** región de recorte tiene bordes se superponen.  
  
- **ERROR** contexto de dispositivo no es válido.  
  
- **NULLREGION** región de recorte está vacía.  
  
- **SIMPLEREGION** región de recorte no tiene bordes superpuestos.  
  
### <a name="remarks"></a>Comentarios  
 Las dimensiones se copian en el búfer señalado por `lpRect`.  
  
##  <a name="a-namegetcoloradjustmenta--cdcgetcoloradjustment"></a><a name="getcoloradjustment"></a>CDC::GetColorAdjustment  
 Recupera los valores de ajuste de color para el contexto de dispositivo.  
  
```  
BOOL GetColorAdjustment(LPCOLORADJUSTMENT lpColorAdjust) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpColorAdjust`  
 Apunta a un [COLORADJUSTMENT](../../mfc/reference/coloradjustment-structure.md) estructura de datos para recibir los valores de ajuste de color.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
##  <a name="a-namegetcurrentbitmapa--cdcgetcurrentbitmap"></a><a name="getcurrentbitmap"></a>CDC::GetCurrentBitmap  
 Devuelve un puntero a la seleccionada actualmente `CBitmap` objeto.  
  
```  
CBitmap* GetCurrentBitmap() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un `CBitmap` objeto, si es correcto; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro puede devolver objetos temporales.  
  
##  <a name="a-namegetcurrentbrusha--cdcgetcurrentbrush"></a><a name="getcurrentbrush"></a>CDC::GetCurrentBrush  
 Devuelve un puntero a la seleccionada actualmente `CBrush` objeto.  
  
```  
CBrush* GetCurrentBrush() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un `CBrush` objeto, si es correcto; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro puede devolver objetos temporales.  
  
##  <a name="a-namegetcurrentfonta--cdcgetcurrentfont"></a><a name="getcurrentfont"></a>CDC::GetCurrentFont  
 Devuelve un puntero a la seleccionada actualmente `CFont` objeto.  
  
```  
CFont* GetCurrentFont() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un `CFont` objeto, si es correcto; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro puede devolver objetos temporales.  
  
##  <a name="a-namegetcurrentpalettea--cdcgetcurrentpalette"></a><a name="getcurrentpalette"></a>CDC::GetCurrentPalette  
 Devuelve un puntero a la seleccionada actualmente `CPalette` objeto.  
  
```  
CPalette* GetCurrentPalette() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un `CPalette` objeto, si es correcto; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro puede devolver objetos temporales.  
  
##  <a name="a-namegetcurrentpena--cdcgetcurrentpen"></a><a name="getcurrentpen"></a>CDC::GetCurrentPen  
 Devuelve un puntero a la seleccionada actualmente `CPen` objeto.  
  
```  
CPen* GetCurrentPen() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un `CPen` objeto, si es correcto; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro puede devolver objetos temporales.  
  
##  <a name="a-namegetcurrentpositiona--cdcgetcurrentposition"></a><a name="getcurrentposition"></a>CDC::GetCurrentPosition  
 Recupera la posición actual (en coordenadas lógicas).  
  
```  
CPoint GetCurrentPosition() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La posición actual como un `CPoint` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Se puede establecer la posición actual con el `MoveTo` función miembro.  
  
##  <a name="a-namegetdcbrushcolora--cdcgetdcbrushcolor"></a><a name="getdcbrushcolor"></a>CDC::GetDCBrushColor  
 Recupera el color de pincel actual.  
  
```  
COLORREF GetDCBrushColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto es el [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor para el color de pincel actual.  
  
 Si se produce un error en la función, el valor devuelto es **CLR_INVALID**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la función [GetDCBrushColor](http://msdn.microsoft.com/library/windows/desktop/dd144872), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetdcpencolora--cdcgetdcpencolor"></a><a name="getdcpencolor"></a>CDC::GetDCPenColor  
 Recupera el color del lápiz actual.  
  
```  
COLORREF GetDCPenColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto es el [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor para el color del lápiz actual.  
  
 Si se produce un error en la función, el valor devuelto es **CLR_INVALID**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro usa la función de Win32 [GetDCPenColor](http://msdn.microsoft.com/library/windows/desktop/dd144875), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetdevicecapsa--cdcgetdevicecaps"></a><a name="getdevicecaps"></a>CDC:: GetDeviceCaps  
 Recupera una amplia gama de información específica del dispositivo sobre el dispositivo de pantalla.  
  
```  
int GetDeviceCaps(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el tipo de información que se devuelve. Consulte [GetDeviceCaps](http://msdn.microsoft.com/library/windows/desktop/dd144877) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una lista de valores.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de la función solicitada, si la función se realiza correctamente.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPrintDialog::GetDefaults](../../mfc/reference/cprintdialog-class.md#getdefaults).  
  
##  <a name="a-namegetfontdataa--cdcgetfontdata"></a><a name="getfontdata"></a>CDC::GetFontData  
 Recupera información de métrica de fuente de un archivo de fuentes escalables.  
  
```  
DWORD GetFontData(
    DWORD dwTable,  
    DWORD dwOffset,  
    LPVOID lpData,  
    DWORD cbData) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `dwTable`  
 Especifica el nombre de la tabla de métricas que se devuelve. Este parámetro puede ser una de las tablas de métrica documentadas en la especificación de archivos de fuentes TrueType, publicada por Microsoft Corporation. Si este parámetro es 0, la información se recupera comienza al principio del archivo fuente.  
  
 `dwOffset`  
 Especifica el desplazamiento desde el principio de la tabla en la que se va a empezar a recuperar información. Si este parámetro es 0, la información se recupera desde el inicio de la tabla especificada por el `dwTable` parámetro. Si este valor es mayor o igual que el tamaño de la tabla, `GetFontData` devuelve 0.  
  
 `lpData`  
 Señala a un búfer que recibirá la información de fuentes. Si este valor es **NULL**, la función devuelve el tamaño del búfer necesario para los datos de fuente especificados en la `dwTable` parámetro.  
  
 `cbData`  
 Especifica la longitud, en bytes, de la información que se va a recuperar. Si este parámetro es 0, `GetFontData` devuelve el tamaño de los datos especificados en el `dwTable` parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Especifica el número de bytes devuelto en el búfer señalado por `lpData` si la función se realiza correctamente; en caso contrario,-de&1;.  
  
### <a name="remarks"></a>Comentarios  
 Se identifica la información para recuperar especificando un desplazamiento en el archivo de fuente y la longitud de la información que se devuelve.  
  
 A veces, las aplicaciones pueden utilizar el `GetFontData` función miembro para guardar una fuente TrueType con un documento. Para ello, la aplicación determina si la fuente se puede incrustar y, a continuación, recupera el archivo fuente completa, si especifica 0 para el `dwTable`, `dwOffset`, y `cbData` parámetros.  
  
 Las aplicaciones pueden determinar si se puede incrustar una fuente comprobando la **otmfsType** miembro de la [OUTLINETEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd162755) estructura. Si el bit 1 del **otmfsType** está establecido, no se permite la incrustación de la fuente. Si el bit 1 está desactivado, se puede incrustar la fuente. Si se establece el bit 2, la incrustación es de solo lectura.  
  
 Si una aplicación intenta usar esta función para recuperar la información de una fuente TrueType no, la `GetFontData` función miembro devuelve –&1;.  
  
##  <a name="a-namegetfontlanguageinfoa--cdcgetfontlanguageinfo"></a><a name="getfontlanguageinfo"></a>CDC::GetFontLanguageInfo  
 Devuelve información acerca de la fuente seleccionada actualmente para el contexto de presentación especificado.  
  
```  
DWORD GetFontLanguageInfo() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto identifica las características de la fuente seleccionada actualmente. Para obtener una lista completa de los valores posibles, consulte [GetFontLanguageInfo](http://msdn.microsoft.com/library/windows/desktop/dd144886).  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la función [GetFontLanguageInfo](http://msdn.microsoft.com/library/windows/desktop/dd144886), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetglyphoutlinea--cdcgetglyphoutline"></a><a name="getglyphoutline"></a>CDC::GetGlyphOutline  
 Recupera la curva de contorno o mapa de bits de un carácter de esquema en la fuente actual.  
  
```  
DWORD GetGlyphOutline(
    UINT nChar,  
    UINT nFormat,  
    LPGLYPHMETRICS lpgm,  
    DWORD cbBuffer,  
    LPVOID lpBuffer,  
    const MAT2* lpmat2) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nChar`  
 Especifica el carácter que es devolverá información.  
  
 `nFormat`  
 Especifica el formato en el que la función es devolver información. Puede ser uno de los siguientes valores, o 0:  
  
|Valor|Significado|  
|-----------|-------------|  
|**GGO_BITMAP**|Devuelve el mapa de bits de glifo. Cuando se devuelve la función, el búfer señalado por `lpBuffer` contiene un mapa de bits de 1 bit por píxel cuyas filas se inicie en los límites de palabra doble.|  
|**GGO_NATIVE**|Devuelve la curva de puntos de datos en formato nativo de rasterizador, con las unidades del dispositivo. Cuando se especifica este valor, cualquier transformación especificada en `lpmat2` se omite.|  
  
 Cuando el valor de `nFormat` es 0, la función rellena un [GLYPHMETRICS](http://msdn.microsoft.com/library/windows/desktop/dd144955) estructura pero no devuelve datos de contorno del glifo.  
  
 *lpgm*  
 Apunta a un **GLYPHMETRICS** estructura que describe la colocación del glifo en la celda de carácter.  
  
 `cbBuffer`  
 Especifica el tamaño del búfer en la que la función copia la información sobre el carácter de esquema. Si este valor es 0 y el `nFormat` parámetro sea el **GGO_BITMAP** o **GGO_NATIVE** valores, la función devuelve el tamaño necesario del búfer.  
  
 `lpBuffer`  
 Señala a un búfer en la que la función copia la información sobre el carácter de esquema. Si `nFormat` especifica la **GGO_NATIVE** valor, la información se copia en el formulario de **TTPOLYGONHEADER** y **TTPOLYCURVE** estructuras. Si este valor es **NULL** y `nFormat` sea la **GGO_BITMAP** o **GGO_NATIVE** valor, la función devuelve el tamaño necesario del búfer.  
  
 `lpmat2`  
 Apunta a un [MAT2](http://msdn.microsoft.com/library/windows/desktop/dd145048) estructura que contiene una matriz de transformación para el carácter. Este parámetro no puede ser **NULL**, incluso si la **GGO_NATIVE** valor especificado para `nFormat`.  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño, en bytes, del búfer necesario para la información recuperada si `cbBuffer` es 0 o `lpBuffer` es **NULL**. De lo contrario, es un valor positivo si la función se realiza correctamente, o -1 si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Una aplicación puede girar caracteres recuperados en formato de mapa de bits especificando una matriz de transformación de 2 por 2 en la estructura que señala `lpmat2`.  
  
 Un contorno de glifo se devuelve como una serie de perfiles. Cada contorno se define por un [TTPOLYGONHEADER](http://msdn.microsoft.com/library/windows/desktop/dd145158) estructura seguido tantos **TTPOLYCURVE** estructuras como sea necesario para describirlo. Todos los puntos que se devuelven como [POINTFX](http://msdn.microsoft.com/library/windows/desktop/dd162806) estructuras y representan la posición absoluta, no relativas movimientos. El punto de partida determinado por la **pfxStart** miembro de la [TTPOLYGONHEADER](http://msdn.microsoft.com/library/windows/desktop/dd145158) estructura es el punto en el que comienza el contorno de un perfil. El [TTPOLYCURVE](http://msdn.microsoft.com/library/windows/desktop/dd145157) estructuras siguientes pueden ser registros polyline o registros de curva spline. Registros de polilínea son una serie de puntos; las líneas dibujadas entre los puntos de describan el contorno del carácter. Los registros de spline representan las curvas cuadráticas usa TrueType (es decir, cuadrática como b-spline).  
  
##  <a name="a-namegetgraphicsmodea--cdcgetgraphicsmode"></a><a name="getgraphicsmode"></a>CDC::GetGraphicsMode  
 Recupera el modo de gráficos actual para el contexto de dispositivo especificado.  
  
```  
int GetGraphicsMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el modo de gráficos actual en caso de éxito. Para obtener una lista de los valores que puede devolver este método, consulte [GetGraphicsMode](http://msdn.microsoft.com/library/windows/desktop/dd144892).  
  
 Devuelve 0 en caso de error.  
  
 Para obtener información de error extendida, llame a [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Comentarios  
 Este método ajusta la función GDI de Windows [GetGraphicsMode](http://msdn.microsoft.com/library/windows/desktop/dd144892).  
  
##  <a name="a-namegethalftonebrusha--cdcgethalftonebrush"></a><a name="gethalftonebrush"></a>CDC::GetHalftoneBrush  
 Llame a esta función miembro para recuperar un pincel de medios tonos.  
  
```  
static CBrush* PASCAL GetHalftoneBrush();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CBrush` objeto si se realiza correctamente; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Un pincel de semitonos muestra píxeles que también son los colores de primer plano y fondo para crear un patrón interpolado. El siguiente es un ejemplo de un patrón interpolado creado por un pincel de medios tonos.  
  
 ![Detalle de un trazo del lápiz interpolado](../../mfc/reference/media/vc318s1.gif "vc318s1")  
  
##  <a name="a-namegetkerningpairsa--cdcgetkerningpairs"></a><a name="getkerningpairs"></a>CDC::GetKerningPairs  
 Recupera el carácter interletraje de pares de la fuente que está seleccionado actualmente en el contexto de dispositivo especificado.  
  
```  
int GetKerningPairs(
    int nPairs,  
    LPKERNINGPAIR lpkrnpair) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nPairs`  
 Especifica el número de [KERNINGPAIR](http://msdn.microsoft.com/library/windows/desktop/dd145024) señala estructuras `lpkrnpair`. La función no realizará la copia más pares de interletraje de los especificados por `nPairs`.  
  
 `lpkrnpair`  
 Apunta a una matriz de **KERNINGPAIR** estructuras que reciben el interletraje de pares cuando vuelve la función. Esta matriz debe contener al menos tantas estructuras especificado por `nPairs`. Si este parámetro es **NULL**, la función devuelve el número total de pares de la fuente de ajuste.  
  
### <a name="return-value"></a>Valor devuelto  
 Especifica el número de pares recuperados de ajuste o el número total de interletraje pares en la fuente, si la función se realiza correctamente. Devuelve cero si se produce un error en la función o no hay ningún par interletraje para la fuente.  
  
##  <a name="a-namegetlayouta--cdcgetlayout"></a><a name="getlayout"></a>CDC::GetLayout  
 Llame a esta función miembro para determinar el diseño del texto y gráficos para un contexto de dispositivo, como una impresora o un metarchivo.  
  
```  
DWORD GetLayout() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el diseño de marcas para el contexto de dispositivo actual. De lo contrario, **GDI_ERROR**. Para obtener información de error extendida, llame a [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360). Para obtener una lista de las marcas de diseño, vea [CDC::SetLayout](#setlayout).  
  
### <a name="remarks"></a>Comentarios  
 El diseño predeterminado es de izquierda a derecha.  
  
##  <a name="a-namegetmapmodea--cdcgetmapmode"></a><a name="getmapmode"></a>CDC::GetMapMode  
 Recupera el modo de asignación actual.  
  
```  
int GetMapMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de asignación.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener una descripción de los modos de asignación, consulte el `SetMapMode` función miembro.  
  
> [!NOTE]
>  Si se llama a [SetLayout](#setlayout) para cambiar el controlador de dominio para el diseño de derecha a izquierda, **SetLayout** cambia automáticamente el modo de asignación a `MM_ISOTROPIC`. Por lo tanto, cualquier llamada subsiguiente a `GetMapMode` devolverá `MM_ISOTROPIC`.  
  
##  <a name="a-namegetmiterlimita--cdcgetmiterlimit"></a><a name="getmiterlimit"></a>CDC::GetMiterLimit  
 Devuelve el límite angular para el contexto de dispositivo.  
  
```  
float GetMiterLimit() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El límite angular se usa al dibujar líneas geométricas que tienen ángulo combinaciones.  
  
##  <a name="a-namegetnearestcolora--cdcgetnearestcolor"></a><a name="getnearestcolor"></a>CDC::GetNearestColor  
 Devuelve el color sólido que mejor coincida con un color lógico especificado.  
  
```  
COLORREF GetNearestColor(COLORREF crColor) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `crColor`  
 Especifica el color que se debe coincidir.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de color RGB (rojo, verde, azul) que define el sólido de color más cercana a la `crColor` valor que represente el dispositivo.  
  
### <a name="remarks"></a>Comentarios  
 El dispositivo especificado debe ser capaz de representar este color.  
  
##  <a name="a-namegetoutlinetextmetricsa--cdcgetoutlinetextmetrics"></a><a name="getoutlinetextmetrics"></a>CDC::GetOutlineTextMetrics  
 Recupera información de métrica para las fuentes TrueType.  
  
```  
UINT GetOutlineTextMetrics(
    UINT cbData,  
    LPOUTLINETEXTMETRIC lpotm) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpotm`  
 Apunta a una matriz de [OUTLINETEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd162755) estructuras. Si este parámetro es **NULL**, la función devuelve el tamaño del búfer necesario para los datos métricos recuperados.  
  
 `cbData`  
 Especifica el tamaño, en bytes, del búfer al que se devuelve información.  
  
 `lpotm`  
 Apunta a una **OUTLINETEXTMETRIC** estructura. Si este parámetro es **NULL**, la función devuelve el tamaño del búfer necesario para la información recuperada de métrica.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El [OUTLINETEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd162755) estructura contiene la mayor parte de la información de métrica de fuente proporcionada con el formato TrueType, incluido un [TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132) estructura. Los últimos cuatro miembros de la **OUTLINETEXTMETRIC** estructura son punteros a cadenas. Las aplicaciones deben asignar espacio para estas cadenas además del espacio necesario para los demás miembros. Porque no hay ningún límite impuesto por el sistema para el tamaño de las cadenas, es el método más sencillo de asignar memoria recuperar el tamaño necesario especificando **NULL** de `lpotm` en la primera llamada a la `GetOutlineTextMetrics` (función).  
  
##  <a name="a-namegetoutputcharwidtha--cdcgetoutputcharwidth"></a><a name="getoutputcharwidth"></a>CDC::GetOutputCharWidth  
 Utiliza el contexto de dispositivo de salida, `m_hDC`y recupera el ancho de caracteres individuales de un grupo de caracteres consecutivos de la fuente actual.  
  
```  
BOOL GetOutputCharWidth(
    UINT nFirstChar,  
    UINT nLastChar,  
    LPINT lpBuffer) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nFirstChar`  
 Especifica el primer carácter de un grupo consecutivo de caracteres de la fuente actual.  
  
 `nLastChar`  
 Especifica el último carácter de un grupo consecutivo de caracteres de la fuente actual.  
  
 `lpBuffer`  
 Señala a un búfer que recibirá los valores de ancho de un grupo de caracteres consecutivos en la fuente actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Por ejemplo, si `nFirstChar` identifica la letra 'a' y `nLastChar` identifica la letra 'z', la recupera de la función del ancho de todos los caracteres en minúsculas.  
  
 La función almacena los valores en el búfer señalado por `lpBuffer`. Este búfer debe ser lo suficientemente grande como para contener todos los anchos; es decir, debe haber al menos 26 entradas en el ejemplo dado.  
  
 Si no existe un carácter en el grupo de caracteres consecutivos en una fuente concreta, se le asignará el valor de ancho de carácter predeterminado.  
  
##  <a name="a-namegetoutputtabbedtextextenta--cdcgetoutputtabbedtextextent"></a><a name="getoutputtabbedtextextent"></a>CDC::GetOutputTabbedTextExtent  
 Llame a esta función miembro para calcular el ancho y alto de una cadena de caracteres con [m_hDC](#m_hdc), el contexto de dispositivo de salida.  
  
```  
CSize GetOutputTabbedTextExtent(
    LPCTSTR lpszString,  
    int nCount,  
    int nTabPositions,  
    LPINT lpnTabStopPositions) const;  
  
CSize GetOutputTabbedTextExtent(
    const CString& str,  
    int nTabPositions,  
    LPINT lpnTabStopPositions) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszString`  
 Apunta a una cadena de caracteres que se va medir. También puede pasar un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto para este parámetro.  
  
 `nCount`  
 Especifica el número de caracteres de la cadena. Si `nCount` es –&1;, se calcula la longitud.  
  
 `nTabPositions`  
 Especifica el número de posiciones de tabulación en la matriz señalada por `lpnTabStopPositions`.  
  
 `lpnTabStopPositions`  
 Apunta a una matriz de enteros que contiene las posiciones de tabulación en unidades lógicas. Las tabulaciones deben estar ordenadas en sentido ascendente; el menor valor de x debe ser el primer elemento de la matriz. No se permiten las tabulaciones hacia atrás.  
  
 `str`  
 Un `CString` objeto que contiene los caracteres especificados que se va medir.  
  
### <a name="return-value"></a>Valor devuelto  
 Las dimensiones de la cadena (en unidades lógicas) en un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Si la cadena contiene uno o más caracteres de tabulación, el ancho de la cadena se basa en las posiciones de tabulación especificadas por `lpnTabStopPositions`. La función utiliza la fuente seleccionada actualmente para calcular las dimensiones de la cadena.  
  
 La región de recorte actual no separa el ancho y alto devuelto por la `GetOutputTabbedTextExtent` (función).  
  
 Puesto que algunos dispositivos no incluya caracteres en matrices de celdas normal (es decir, ajustar el espacio entre los caracteres), la suma de las extensiones de los caracteres de una cadena no puede ser igual que el alcance de la cadena.  
  
 Si `nTabPositions` es 0 y `lpnTabStopPositions` es **NULL**, las fichas se expanden hasta ocho ancho promedio de los caracteres. Si `nTabPositions` es 1, la distancia especificada por el primer valor de la matriz que separará las tabulaciones `lpnTabStopPositions` puntos. Si `lpnTabStopPositions` apunta a más de un solo valor, se establece una tabulación para cada valor de la matriz, hasta el número especificado por `nTabPositions`.  
  
##  <a name="a-namegetoutputtextextenta--cdcgetoutputtextextent"></a><a name="getoutputtextextent"></a>CDC::GetOutputTextExtent  
 Llame a esta función miembro para usar el contexto de dispositivo de salida, [m_hDC](#m_hdc)y calcular el ancho y alto de una línea de texto, con la fuente actual.  
  
```  
CSize GetOutputTextExtent(
    LPCTSTR lpszString,  
    int nCount) const;  
  
CSize GetOutputTextExtent(const CString& str) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszString`  
 Apunta a una cadena de caracteres. También puede pasar un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto para este parámetro.  
  
 `nCount`  
 Especifica el número de caracteres de la cadena. Si `nCount` es –&1;, se calcula la longitud.  
  
 `str`  
 Un `CString` objeto que contiene los caracteres especificados que se va medir.  
  
### <a name="return-value"></a>Valor devuelto  
 Las dimensiones de la cadena (en unidades lógicas) devueltas en una [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 La región de recorte actual no afecta a la anchura y altura devuelto por `GetOutputTextExtent`.  
  
 Puesto que algunos dispositivos no incluya caracteres en matrices de celdas normal (es decir, llevar a cabo el interletraje), la suma de las extensiones de los caracteres de una cadena no puede ser igual que el alcance de la cadena.  
  
##  <a name="a-namegetoutputtextmetricsa--cdcgetoutputtextmetrics"></a><a name="getoutputtextmetrics"></a>CDC::GetOutputTextMetrics  
 Recupera las métricas para la fuente actual mediante `m_hDC`, el contexto de dispositivo de salida.  
  
```  
BOOL GetOutputTextMetrics(LPTEXTMETRIC lpMetrics) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpMetrics`  
 Apunta a la [TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132) estructura que recibe las métricas.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
##  <a name="a-namegetpatha--cdcgetpath"></a><a name="getpath"></a>CDC::getPath  
 Recupera las coordenadas que definen los extremos de las líneas y los puntos de control de curvas que se encuentra en la ruta de acceso que se ha seleccionado en el contexto de dispositivo.  
  
```  
int GetPath(
    LPPOINT lpPoints,  
    LPBYTE lpTypes,  
    int nCount) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPoints`  
 Apunta a una matriz de [punto](../../mfc/reference/point-structure1.md) estructuras de datos o `CPoint` se colocan los objetos en los extremos de línea y la curva de puntos de control.  
  
 `lpTypes`  
 Apunta a una matriz de bytes donde se colocan los tipos de vértice. Los valores son uno de los siguientes:  
  
- **PT_MOVETO** especifica que el punto correspondiente en `lpPoints` inicia una figura separada.  
  
- **PT_LINETO** especifica que el punto anterior y el correspondiente punto de `lpPoints` son los extremos de una línea.  
  
- **PT_BEZIERTO** especifica que el punto correspondiente en `lpPoints` es un punto de control o el punto final de una curva de Bzier.  
  
 **PT_BEZIERTO** se producen siempre tipos de conjuntos de tres. El punto inmediatamente anterior a la ruta de acceso define el punto inicial de la curva de Bzier. Los dos primeros **PT_BEZIERTO** puntos son los puntos de control y el tercero **PT_BEZIERTO** punto es el punto final (si codificado).  
  
     Un **PT_LINETO** o **PT_BEZIERTO** tipo puede combinarse con el marcador siguiente (usando el operador bit a bit `OR`) para indicar que el punto correspondiente es el último punto de una figura y que la figura debe cerrarse:  
  
- **PT_CLOSEFIGURE** especifica que la figura se cierra automáticamente después de la línea correspondiente o se dibuja la curva. La figura se cierra dibujando una línea desde el extremo de línea o curva en el punto correspondiente al último **PT_MOVETO**.  
  
 `nCount`  
 Especifica el número total de [punto](../../mfc/reference/point-structure1.md) estructuras de datos que se pueden colocar en el `lpPoints` matriz. Este valor debe ser el mismo que el número de bytes que se puede colocar en el `lpTypes` matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el `nCount` parámetro es distinto de cero, el número de puntos que se enumeran. Si `nCount` es 0, el número total de puntos en la ruta de acceso (y `GetPath` escribe nada en los búferes). Si `nCount` es distinto de cero y menor que el número de puntos en la ruta de acceso, el valor devuelto es -1.  
  
### <a name="remarks"></a>Comentarios  
 El contexto de dispositivo debe contener un trayecto cerrado. Los puntos de la ruta de acceso se devuelven en coordenadas lógicas. Puntos se almacenan en la ruta de acceso en coordenadas de dispositivo, por lo que `GetPath` cambia los puntos de coordenadas de dispositivo a coordenadas lógicas mediante el inverso de la transformación actual. El `FlattenPath` función miembro se puede llamar antes `GetPath`, para convertir todas las curvas en la ruta de acceso en segmentos de línea.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CDC:: beginpath](#beginpath).  
  
##  <a name="a-namegetpixela--cdcgetpixel"></a><a name="getpixel"></a>CDC::getPixel  
 Recupera el valor de color RGB del píxel en el punto especificado por *x* y *y*.  
  
```  
COLORREF GetPixel(
    int x,  
    int y) const;  
  
COLORREF GetPixel(POINT point) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada x lógica del punto se van a examinar.  
  
 *y*  
 Especifica la coordenada y lógica del punto se van a examinar.  
  
 `point`  
 Especifica las coordenadas x e y lógica del punto se van a examinar.  
  
### <a name="return-value"></a>Valor devuelto  
 Para la versión de la función, un valor de color RGB del color del punto determinado. Si las coordenadas no especifican un punto en la región de recorte es –&1;.  
  
### <a name="remarks"></a>Comentarios  
 El punto debe estar en la región de recorte. Si el punto no está en la región de recorte, la función no tiene ningún efecto y devuelve –&1;.  
  
 No todos los dispositivos admiten la **GetPixel** (función). Para obtener más información, consulte el **RC_BITBLT** capacidad de trama en el [GetDeviceCaps](#getdevicecaps) función miembro.  
  
 El **GetPixel** función miembro tiene dos formas. La primera toma dos valores de coordenadas; el segundo acepta una [punto](../../mfc/reference/point-structure1.md) estructura o un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto.  
  
##  <a name="a-namegetpolyfillmodea--cdcgetpolyfillmode"></a><a name="getpolyfillmode"></a>CDC::GetPolyFillMode  
 Recupera el modo de relleno de polígono actual.  
  
```  
int GetPolyFillMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de relleno de polígono actual, **alternativo** o **DEVANADO**, si la función se realiza correctamente.  
  
### <a name="remarks"></a>Comentarios  
 Consulte la `SetPolyFillMode` función miembro para una descripción de los modos de llenado de polígono.  
  
##  <a name="a-namegetrop2a--cdcgetrop2"></a><a name="getrop2"></a>CDC::GetROP2  
 Recupera el modo de dibujo actual.  
  
```  
int GetROP2() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de dibujo. Para obtener una lista de los valores de modo de dibujo, consulte el `SetROP2` función miembro.  
  
### <a name="remarks"></a>Comentarios  
 El modo de dibujo especifica cómo se combinan los colores del lápiz y el interior de los objetos rellenos con el color ya en la superficie de presentación.  
  
##  <a name="a-namegetsafehdca--cdcgetsafehdc"></a><a name="getsafehdc"></a>CDC::GetSafeHdc  
 Llame a esta función miembro para obtener [m_hDC](#m_hdc), el contexto de dispositivo de salida.  
  
```  
HDC GetSafeHdc() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de contexto de dispositivo.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro también funciona con punteros null.  
  
##  <a name="a-namegetstretchbltmodea--cdcgetstretchbltmode"></a><a name="getstretchbltmode"></a>CDC::GetStretchBltMode  
 Recupera el modo de ajuste de mapa de bits actual.  
  
```  
int GetStretchBltMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto especifica el modo de ajuste de mapa de bits actual: **STRETCH_ANDSCANS**, **STRETCH_DELETESCANS**, o **STRETCH_ORSCANS** : si la función se realiza correctamente.  
  
### <a name="remarks"></a>Comentarios  
 El modo de ajuste de mapa de bits define cómo se quita la información de mapas de bits que se estira o comprime el `StretchBlt` función miembro.  
  
 El **STRETCH_ANDSCANS** y **STRETCH_ORSCANS** modos normalmente se utilizan para conservar los píxeles de primer plano de los mapas de bits monocromo. El **STRETCH_DELETESCANS** modo se suele usar para conservar el color en los mapas de bits de color.  
  
##  <a name="a-namegettabbedtextextenta--cdcgettabbedtextextent"></a><a name="gettabbedtextextent"></a>CDC::GetTabbedTextExtent  
 Llame a esta función miembro para calcular el ancho y alto de una cadena de caracteres con [m_hAttribDC](#m_hattribdc), el contexto de dispositivo de atributo.  
  
```  
CSize GetTabbedTextExtent(
    LPCTSTR lpszString,  
    int nCount,  
    int nTabPositions,  
    LPINT lpnTabStopPositions) const;  
  
CSize GetTabbedTextExtent(
    const CString& str,  
    int nTabPositions,  
    LPINT lpnTabStopPositions) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszString`  
 Apunta a una cadena de caracteres. También puede pasar un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto para este parámetro.  
  
 `nCount`  
 Especifica el número de caracteres de la cadena. Si `nCount` es –&1;, se calcula la longitud.  
  
 `nTabPositions`  
 Especifica el número de posiciones de tabulación en la matriz señalada por `lpnTabStopPositions`.  
  
 `lpnTabStopPositions`  
 Apunta a una matriz de enteros que contiene las posiciones de tabulación en unidades lógicas. Las tabulaciones deben estar ordenadas en sentido ascendente; el menor valor de x debe ser el primer elemento de la matriz. No se permiten las tabulaciones hacia atrás.  
  
 `str`  
 Un `CString` objeto que contiene los caracteres especificados para dibujar.  
  
### <a name="return-value"></a>Valor devuelto  
 Las dimensiones de la cadena (en unidades lógicas) en un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Si la cadena contiene uno o más caracteres de tabulación, el ancho de la cadena se basa en las posiciones de tabulación especificadas por `lpnTabStopPositions`. La función utiliza la fuente seleccionada actualmente para calcular las dimensiones de la cadena.  
  
 La región de recorte actual no separa el ancho y alto devuelto por la `GetTabbedTextExtent` (función).  
  
 Puesto que algunos dispositivos no incluya caracteres en matrices de celdas normal (es decir, ajustar el espacio entre los caracteres), la suma de las extensiones de los caracteres de una cadena no puede ser igual que el alcance de la cadena.  
  
 Si `nTabPositions` es 0 y `lpnTabStopPositions` es **NULL**, las fichas se expanden hasta ocho veces el promedio ancho de caracteres. Si `nTabPositions` es 1, la distancia especificada por el primer valor de la matriz que separará las tabulaciones `lpnTabStopPositions` puntos. Si `lpnTabStopPositions` apunta a más de un solo valor, se establece una tabulación para cada valor de la matriz, hasta el número especificado por `nTabPositions`.  
  
##  <a name="a-namegettextaligna--cdcgettextalign"></a><a name="gettextalign"></a>CDC::GetTextAlign  
 Recupera el estado de las marcas de alineación de texto para el contexto de dispositivo.  
  
```  
UINT GetTextAlign() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El estado de las marcas de alineación de texto. El valor devuelto es uno o varios de los siguientes valores:  
  
- **TA_BASELINE** especifica la alineación del eje x y la línea de base de la fuente elegida dentro del rectángulo delimitador.  
  
- **TA_BOTTOM** especifica la alineación del eje x y la parte inferior del rectángulo delimitador.  
  
- **TA_CENTER** especifica la alineación del eje y y el centro del rectángulo delimitador.  
  
- **TA_LEFT** especifica la alineación del eje y y el lado izquierdo del rectángulo delimitador.  
  
- **TA_NOUPDATECP** especifica que no se actualiza la posición actual.  
  
- **TA_RIGHT** especifica la alineación del eje y y el lado derecho del rectángulo delimitador.  
  
- **TA_TOP** especifica la alineación del eje x y la parte superior del rectángulo delimitador.  
  
- **TA_UPDATECP** especifica que se actualiza la posición actual.  
  
### <a name="remarks"></a>Comentarios  
 Los indicadores de alineación de texto determinan cómo la `TextOut` y `ExtTextOut` funciones miembro alinean una cadena de texto en relación con el punto de partida de la cadena. Las marcas de alineación de texto no son necesariamente único bit marcas y pueden ser iguales a 0. Para comprobar si se estableció un marcador, una aplicación debe seguir estos pasos:  
  
1.  El operador OR bit a bit se aplican a la marca y sus marcadores relacionados, agrupados como sigue:  
  
    - **TA_LEFT**, **TA_CENTER**, y **TA_RIGHT**  
  
    - **TA_BASELINE**, **TA_BOTTOM**, y **TA_TOP**  
  
    - **TA_NOUPDATECP** y **TA_UPDATECP**  
  
2.  Aplicar el bit a bit- y operador para el resultado y el valor devuelto de `GetTextAlign`.  
  
3.  Probar la igualdad de este resultado y la marca.  
  
##  <a name="a-namegettextcharacterextraa--cdcgettextcharacterextra"></a><a name="gettextcharacterextra"></a>CDC::GetTextCharacterExtra  
 Recupera el valor actual de la cantidad de espaciado entre caracteres en función.  
  
```  
int GetTextCharacterExtra() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La cantidad de espaciado de caracteres en función.  
  
### <a name="remarks"></a>Comentarios  
 GDI agrega este espacio a cada carácter, incluido el carácter de salto, cuando escribe una línea de texto en el contexto de dispositivo.  
  
 El valor predeterminado para la cantidad de espaciado entre caracteres en función es 0.  
  
##  <a name="a-namegettextcolora--cdcgettextcolor"></a><a name="gettextcolor"></a>CDC::GetTextColor  
 Recupera el color de texto actual.  
  
```  
COLORREF GetTextColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El color de texto actual como un valor de color RGB.  
  
### <a name="remarks"></a>Comentarios  
 El color del texto es el color de primer plano de caracteres dibujados con las funciones de miembro de la salida de texto GDI [TextOut](#textout), [ExtTextOut](#exttextout), y [TabbedTextOut](#tabbedtextout).  
  
##  <a name="a-namegettextextenta--cdcgettextextent"></a><a name="gettextextent"></a>CDC::GetTextExtent  
 Llame a esta función miembro para calcular el ancho y alto de una línea de texto con la fuente actual para determinar las dimensiones.  
  
```  
CSize GetTextExtent(
    LPCTSTR lpszString,  
    int nCount) const;  
  
CSize GetTextExtent(const CString& str) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszString`  
 Apunta a una cadena de caracteres. También puede pasar un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto para este parámetro.  
  
 `nCount`  
 Especifica el número de caracteres de la cadena.  
  
 `str`  
 Un `CString` objeto que contiene los caracteres especificados.  
  
### <a name="return-value"></a>Valor devuelto  
 Las dimensiones de la cadena (en unidades lógicas) en un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 La información se recupera de [m_hAttribDC](#m_hattribdc), el contexto de dispositivo de atributo.  
  
 De forma predeterminada, `GetTextExtent` supone el texto para el que se recupera de la dimensión se establece a lo largo de una línea horizontal (es decir, el escape es 0). Si crea una fuente especificando un escape distinto de cero, debe convertir el ángulo del texto explícitamente para obtener las dimensiones de la cadena.  
  
 La región de recorte actual no afecta a la anchura y altura devuelto por `GetTextExtent`.  
  
 Puesto que algunos dispositivos no incluya caracteres en matrices de celdas normal (es decir, llevar a cabo el interletraje), la suma de las extensiones de los caracteres de una cadena no puede ser igual que el alcance de la cadena.  
  
##  <a name="a-namegettextextentexpointia--cdcgettextextentexpointi"></a><a name="gettextextentexpointi"></a>CDC::GetTextExtentExPointI  
 Recupera el número de caracteres de una cadena especificada que se ajusten a un espacio determinado y rellena una matriz con la extensión del texto para cada uno de esos caracteres.  
  
```  
BOOL GetTextExtentExPointI(
    LPWORD pgiIn,  
    int cgi,  
    int nMaxExtent,  
    LPINT lpnFit,  
    LPINT alpDx,  
    LPSIZE lpSize) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pgiIn`  
 Un puntero a una matriz de índices de glifo de las extensiones son va a recuperar.  
  
 `cgi`  
 Especifica el número de glifos en la matriz señalada por `pgiIn`.  
  
 `nMaxExtent`  
 Especifica el ancho máximo permitido, en unidades lógicas, de la cadena con formato.  
  
 `lpnFit`  
 Un puntero a un entero que recibe un recuento del número máximo de caracteres que cabrán en el espacio especificado por `nMaxExtent`. Cuando `lpnFit` es **NULL**, `nMaxExtent` se omite.  
  
 *alpDx*  
 Puntero a una matriz de enteros que recibe las extensiones de glifo parcial. Cada elemento de la matriz proporciona la distancia, en unidades lógicas, entre el comienzo de la matriz de índices de glifo y uno de los glifos que cabe en el espacio especificado por `nMaxExtent`. Aunque esta matriz debe tener al menos tantos elementos como los índices de glifo especificados por `cgi`, la función rellena la matriz con extensiones sólo para los índices de glifo tal como se especifican mediante `lpnFit`. Si *lpnDx* es **NULL**, la función no calcula el ancho de la cadena parcial.  
  
 `lpSize`  
 Puntero a un [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura que recibe las dimensiones de la matriz de índices de glifo, en unidades lógicas. Este valor no puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la función [GetTextExtentExPointI](http://msdn.microsoft.com/library/windows/desktop/dd144936), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegettextextentpointia--cdcgettextextentpointi"></a><a name="gettextextentpointi"></a>CDC::GetTextExtentPointI  
 Recupera el ancho y alto de la matriz especificada de índices de glifo.  
  
```  
BOOL GetTextExtentPointI(
    LPWORD pgiIn,  
    int cgi,  
    LPSIZE lpSize) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pgiIn`  
 Un puntero a una matriz de índices de glifo de las extensiones son va a recuperar.  
  
 `cgi`  
 Especifica el número de glifos en la matriz señalada por `pgiIn`.  
  
 `lpSize`  
 Puntero a un [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura que recibe las dimensiones de la matriz de índices de glifo, en unidades lógicas. Este valor no puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la función [GetTextExtentPointI](http://msdn.microsoft.com/library/windows/desktop/dd144939), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegettextfacea--cdcgettextface"></a><a name="gettextface"></a>CDC::GetTextFace  
 Llame a esta función miembro para copiar el nombre de tipo de letra de la fuente actual en un búfer.  
  
```  
int GetTextFace(
    int nCount,  
    LPTSTR lpszFacename) const;  
  
int GetTextFace(CString& rString) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nCount`  
 Especifica el tamaño del búfer (en bytes). Si el nombre de tipo de letra es mayor que el número de bytes especificado por este parámetro, el nombre se trunca.  
  
 *lpszFacename*  
 Puntos en el búfer para el nombre de tipo de letra.  
  
 `rString`  
 Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de bytes copiados en el búfer, sin incluir el carácter nulo de terminación. Es 0 si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 El nombre de tipo de letra se copia como una cadena terminada en null.  
  
##  <a name="a-namegettextmetricsa--cdcgettextmetrics"></a><a name="gettextmetrics"></a>CDC::GetTextMetrics  
 Recupera las métricas para la fuente actual utilizando el contexto de dispositivo de atributo.  
  
```  
BOOL GetTextMetrics(LPTEXTMETRIC lpMetrics) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpMetrics`  
 Apunta a la [TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132) estructura que recibe las métricas.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
##  <a name="a-namegetviewportexta--cdcgetviewportext"></a><a name="getviewportext"></a>CDC::GetViewportExt  
 Recupera las extensiones x y y de la ventanilla del contexto de dispositivo.  
  
```  
CSize GetViewportExt() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El x - y y-extensiones (en unidades de dispositivo) como un `CSize` objeto.  
  
##  <a name="a-namegetviewportorga--cdcgetviewportorg"></a><a name="getviewportorg"></a>CDC::GetViewportOrg  
 Recupera las coordenadas x e y del origen de la ventanilla asociado al contexto de dispositivo.  
  
```  
CPoint GetViewportOrg() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El origen de la ventanilla (en coordenadas de dispositivo) como un `CPoint` objeto.  
  
##  <a name="a-namegetwindowa--cdcgetwindow"></a><a name="getwindow"></a>CDC::GetWindow  
 Devuelve la ventana asociada con el contexto de dispositivo de presentación.  
  
```  
CWnd* GetWindow() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un `CWnd` objeto si se realiza correctamente; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Se trata de una función avanzada. Por ejemplo, esta función miembro no puede devolver la ventana de vista al imprimir o en vista previa de impresión. Siempre devuelve la ventana de salida. Funciones de salida que utiliza el controlador de dominio determinado se dibujan en esta ventana.  
  
##  <a name="a-namegetwindowexta--cdcgetwindowext"></a><a name="getwindowext"></a>CDC::GetWindowExt  
 Recupera las extensiones x y y de la ventana asociada al contexto de dispositivo.  
  
```  
CSize GetWindowExt() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El x - y y-extensiones (en unidades lógicas) como un `CSize` objeto.  
  
##  <a name="a-namegetwindoworga--cdcgetwindoworg"></a><a name="getwindoworg"></a>CDC::GetWindowOrg  
 Recupera las coordenadas x e y del origen de la ventana asociada al contexto de dispositivo.  
  
```  
CPoint GetWindowOrg() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El origen de la ventana (en coordenadas lógicas) como un `CPoint` objeto.  
  
##  <a name="a-namegetworldtransforma--cdcgetworldtransform"></a><a name="getworldtransform"></a>CDC::GetWorldTransform  
 Recupera el espacio de mundo actual para la transformación de espacio en la página.  
  
```  
BOOL GetWorldTransform(XFORM& rXform) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `rXform`  
 Hacer referencia a un [XFORM](http://msdn.microsoft.com/library/windows/desktop/dd145228) estructura que recibe el espacio mundo actual para la transformación de espacio en la página.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor distinto de cero en caso de éxito.  
  
 Devuelve 0 en caso de error.  
  
 Para obtener información de error extendida, llame a [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Comentarios  
 Este método ajusta la función GDI de Windows [GetWorldTransform](http://msdn.microsoft.com/library/windows/desktop/dd144953).  
  
##  <a name="a-namegradientfilla--cdcgradientfill"></a><a name="gradientfill"></a>CDC::GradientFill  
 Llame a esta función miembro para rellenar las estructuras de triángulo y el rectángulo con el color que se desvanece suavemente de un lado a otro.  
  
```  
BOOL GradientFill(
    TRIVERTEX* pVertices,  
    ULONG nVertices,  
    void* pMesh,  
    ULONG nMeshElements,  
    DWORD dwMode);
```  
  
### <a name="parameters"></a>Parámetros  
 *pVertices*  
 Puntero a una matriz de [TRIVERTEX](http://msdn.microsoft.com/library/windows/desktop/dd145142) estructuras que definen un vértice del triángulo, cada uno.  
  
 *nVertices*  
 El número de vértices.  
  
 `pMesh`  
 Matriz de [GRADIENT_TRIANGL](http://msdn.microsoft.com/library/windows/desktop/dd144959) en modo de triángulo o una matriz de estructuras de [GRADIENT_RECT](http://msdn.microsoft.com/library/windows/desktop/dd144958) estructuras en modo de rectángulo.  
  
 *nMeshElements*  
 El número de elementos (triángulos o rectángulos) en `pMesh`.  
  
 `dwMode`  
 Especifica el modo de relleno de degradado. Para obtener una lista de valores posibles, consulte [GradientFill](http://msdn.microsoft.com/library/windows/desktop/dd144957) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si es correcto; en caso contrario **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte `GradientFill` en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegraystringa--cdcgraystring"></a><a name="graystring"></a>CDC:: graystring  
 Dibuja atenuado texto (gris) en la ubicación especificada por escribir el texto en un mapa de bits de memoria, atenuar el mapa de bits y, a continuación, copia el mapa de bits a la pantalla.  
  
```  
virtual BOOL GrayString(
    CBrush* pBrush,  
    BOOL (CALLBACK* lpfnOutput)(
    HDC,
    LPARAM,
    int),  
    LPARAM lpData,  
    int nCount,  
    int x,  
    int y,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 `pBrush`  
 Identifica el pincel que se usará para la atenuación (gris).  
  
 `lpfnOutput`  
 Especifica la dirección de la instancia del procedimiento de la función de devolución de llamada proporcionada por la aplicación que se dibujará la cadena. Para obtener más información, vea la descripción de las ventanas **OutputFunc** [función de devolución de llamada](../../mfc/reference/callback-function-for-cdc-graystring.md). Si este parámetro es **NULL**, el sistema utiliza Windows `TextOut` función para dibujar la cadena y `lpData` se supone que es un puntero largo a la cadena de caracteres que se generen.  
  
 `lpData`  
 Especifica un puntero a los datos que se pasan a la función de salida lejano. Si `lpfnOutput` es **NULL**, `lpData` debe ser un puntero largo a la cadena de salida.  
  
 `nCount`  
 Especifica el número de caracteres de salida. Si este parámetro es 0, `GrayString` calcula la longitud de la cadena (suponiendo que `lpData` es un puntero a la cadena). Si `nCount` es – 1 y la función señalada por `lpfnOutput` devuelve 0, la imagen se muestran pero no están atenuados.  
  
 *x*  
 Especifica la coordenada x lógica de la posición inicial del rectángulo que rodea la cadena.  
  
 *y*  
 Especifica la coordenada y lógica de la posición inicial del rectángulo que rodea la cadena.  
  
 `nWidth`  
 Especifica el ancho (en unidades lógicas) del rectángulo que rodea la cadena. Si `nWidth` es 0, `GrayString` calcula el ancho del área, suponiendo que `lpData` es un puntero a la cadena.  
  
 `nHeight`  
 Especifica el alto (en unidades lógicas) del rectángulo que rodea la cadena. Si `nHeight` es 0, `GrayString` calcula el alto del área, suponiendo que `lpData` es un puntero a la cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se dibuja la cadena, o 0 si el `TextOut` función o la función de salida proporcionada por la aplicación devuelve 0, o si no hay suficiente memoria para crear un mapa de bits de memoria atenuación.  
  
### <a name="remarks"></a>Comentarios  
 La función atenúa el texto sin tener en cuenta el pincel seleccionado y el fondo. El `GrayString` función miembro utiliza la fuente seleccionada actualmente. El `MM_TEXT` debe seleccionar el modo de asignación antes de utilizar esta función.  
  
 Una aplicación puede dibujar atenuadas cadenas (gris) en dispositivos compatibles con un color gris sólido sin llamar a la `GrayString` función miembro. El color del sistema **COLOR_GRAYTEXT** es el color gris sólido sistema utilizado para dibujar el texto deshabilitado. La aplicación puede llamar a la **GetSysColor** función de Windows para recuperar el valor de color de **COLOR_GRAYTEXT**. Si el color es distinto de 0 (negro), la aplicación puede llamar a la `SetTextColor` la función miembro para establecer el color del texto en el valor de color y, a continuación, dibuja la cadena directamente. Si el color recuperado es negro, la aplicación debe llamar a `GrayString` para atenuar (gris) el texto.  
  
 Si `lpfnOutput` es **NULL**, GDI utiliza Windows [TextOut](http://msdn.microsoft.com/library/windows/desktop/dd145133) función, y `lpData` se supone que es un puntero al carácter se generen lejano. Si no puede controlar los caracteres que se generen los `TextOut` función miembro (por ejemplo, la cadena se almacena como un mapa de bits), la aplicación debe proporcionar su propia función de salida.  
  
 Tenga en cuenta que todas las funciones de devolución de llamada deben capturar las excepciones que Microsoft Foundation antes de volver a Windows, puesto que no se producirán excepciones en los límites de la devolución de llamada. Para obtener más información sobre las excepciones, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).  
  
 La función de devolución de llamada pasada al `GrayString` debe utilizar el `__stdcall` convención de llamada y debe exportarse con `__declspec`.  
  
 Cuando el marco de trabajo está en modo de vista previa, una llamada a la `GrayString` función miembro se traduce en un `TextOut` llamada y la función de devolución de llamada no se llama.  
  
##  <a name="a-namehimetrictodpa--cdchimetrictodp"></a><a name="himetrictodp"></a>CDC::HIMETRICtoDP  
 Use esta función cuando se convierten **HIMETRIC** tamaños de OLE a píxeles.  
  
```  
void HIMETRICtoDP(LPSIZE lpSize) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpSize`  
 Apunta a un [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura o [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Si el modo de asignación del objeto de contexto de dispositivo es `MM_LOENGLISH`, `MM_HIENGLISH`, `MM_LOMETRIC` o `MM_HIMETRIC`, la conversión se basa en el número de píxeles de pulgada físico. Si el modo de asignación es uno de los modos no restringidos (por ejemplo, `MM_TEXT`), la conversión se basa en el número de píxeles de la pulgada lógica.  
  
##  <a name="a-namehimetrictolpa--cdchimetrictolp"></a><a name="himetrictolp"></a>CDC::HIMETRICtoLP  
 Llame a esta función para convertir **HIMETRIC** unidades en unidades lógicas.  
  
```  
void HIMETRICtoLP(LPSIZE lpSize) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpSize`  
 Apunta a un [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura o [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Use esta función cuando se obtiene **HIMETRIC** tamaños de OLE y desea convertirlos a modo de asignación natural de la aplicación.  
  
 La conversión se realiza por convertir primero la **HIMETRIC** unidades en píxeles y, a continuación, convertir estas unidades en unidades lógicas mediante unidades de asignación actual del contexto de dispositivo. Tenga en cuenta que las extensiones de ventana y el área de visualización del dispositivo afectará al resultado.  
  
##  <a name="a-nameintersectcliprecta--cdcintersectcliprect"></a><a name="intersectcliprect"></a>CDC::IntersectClipRect  
 Se crea una nueva región de recorte mediante la intersección de la región actual y el rectángulo especificado por `x1`, `y1`, `x2`, y `y2`.  
  
```  
int IntersectClipRect(
    int x1,  
    int y1,  
    int x2,  
    int y2);  
  
int IntersectClipRect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `x1`  
 Especifica la coordenada x lógica de la esquina superior izquierda del rectángulo.  
  
 `y1`  
 Especifica la coordenada y lógica de la esquina superior izquierda del rectángulo.  
  
 `x2`  
 Especifica la coordenada x lógica de la esquina inferior derecha del rectángulo.  
  
 `y2`  
 Especifica la coordenada y lógica de la esquina inferior derecha del rectángulo.  
  
 `lpRect`  
 Especifica el rectángulo. Puede pasarse un `CRect` objeto o un puntero a un `RECT` estructura para este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Tipo de la nueva región recorte. Puede ser cualquiera de los siguientes valores:  
  
- **COMPLEXREGION** nueva región de recorte tiene bordes se superponen.  
  
- **ERROR** contexto de dispositivo no es válido.  
  
- **NULLREGION** nueva región de recorte está vacía.  
  
- **SIMPLEREGION** nueva región de recorte no tiene bordes superpuestos.  
  
### <a name="remarks"></a>Comentarios  
 GDI recorta todos los resultados posteriores para que quepa en el nuevo límite. El ancho y el alto no deben superar los 32.767.  
  
##  <a name="a-nameinvertrecta--cdcinvertrect"></a><a name="invertrect"></a>CDC::InvertRect  
 Invierte el contenido del rectángulo especificado.  
  
```  
void InvertRect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Apunta a un `RECT` que contiene las coordenadas lógicas del rectángulo que se invierte. También puede pasar un `CRect` objeto para este parámetro.  
  
### <a name="remarks"></a>Comentarios  
 Inversión es un valor lógico no se voltea los bits de cada píxel y operación. En las pantallas monocromáticas, la función realiza píxeles blancos negro y negro píxeles blancos. En la muestra de color, la inversión depende de cómo se generan los colores de la pantalla. Llamar a `InvertRect` dos veces con el mismo rectángulo restaura la visualización a los colores anteriores.  
  
 Si el rectángulo está vacío, se dibuja nada.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#36;](../../mfc/codesnippet/cpp/cdc-class_8.cpp)]  
  
##  <a name="a-nameinvertrgna--cdcinvertrgn"></a><a name="invertrgn"></a>CDC::InvertRgn  
 Invierte los colores de la región especificada por `pRgn`.  
  
```  
BOOL InvertRgn(CRgn* pRgn);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRgn`  
 Identifica la región donde se invierte. Las coordenadas de la región se especifican en unidades lógicas.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 En las pantallas monocromáticas, la función realiza píxeles blancos negro y negro píxeles blancos. En la muestra de color, la inversión depende de cómo se generan los colores de la pantalla.  
  
##  <a name="a-nameisprintinga--cdcisprinting"></a><a name="isprinting"></a>CDC::IsPrinting  
 Determina si se está usando el contexto de dispositivo para la impresión.  
  
```  
BOOL IsPrinting() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la `CDC` objeto es una impresora DC; en caso contrario, 0.  
  
##  <a name="a-namelinetoa--cdclineto"></a><a name="lineto"></a>CDC::LineTo  
 Dibuja una línea desde la posición actual hasta, pero no incluido el punto especificado por *x* y *y* (o `point`).  
  
```  
BOOL LineTo(
    int x,  
    int y);  
  
BOOL LineTo(POINT point);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada x lógica del extremo de la línea.  
  
 *y*  
 Especifica la coordenada y lógica del extremo de la línea.  
  
 `point`  
 Especifica el extremo de la línea. Puede pasarse un **punto** estructura o un `CPoint` objeto para este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la línea se dibuja; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La línea se dibuja con el lápiz seleccionado. La posición actual se establece en *x*, *y* o `point`.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRect::CenterPoint](../../atl-mfc-shared/reference/crect-class.md#centerpoint).  
  
##  <a name="a-namelptodpa--cdclptodp"></a><a name="lptodp"></a>CDC::LPtoDP  
 Convierte las unidades lógicas en unidades del dispositivo.  
  
```  
void LPtoDP(
    LPPOINT lpPoints,  
    int nCount = 1) const;  
  
void LPtoDP(LPRECT lpRect) const;
void LPtoDP(LPSIZE lpSize) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPoints`  
 Apunta a una matriz de puntos. Cada punto de la matriz es un [punto](../../mfc/reference/point-structure1.md) estructura o un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto.  
  
 `nCount`  
 El número de puntos de la matriz.  
  
 `lpRect`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura o un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto. Este parámetro se utiliza para el caso común de asignación de un rectángulo de coordenadas lógicas a unidades del dispositivo.  
  
 `lpSize`  
 Apunta a un [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura o un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 La función asigna las coordenadas de cada punto o dimensiones de tamaño, desde el sistema de coordenadas lógico de GDI en un sistema de coordenadas de dispositivo. La conversión depende del modo de asignación actual y la configuración de los orígenes y las extensiones de ventana y el área de visualización del dispositivo.  
  
 Las coordenadas x e y de los puntos son enteros con signo de 2 bytes en el intervalo de -32.768 a 32.767. En casos donde el modo de asignación, se crearán en valores mayores que estos límites, el sistema establece los valores de -32.768 y 32.767, respectivamente.  
  
##  <a name="a-namelptohimetrica--cdclptohimetric"></a><a name="lptohimetric"></a>CDC::LPtoHIMETRIC  
 Llame a esta función para convertir las unidades lógicas en **HIMETRIC** unidades.  
  
```  
void LPtoHIMETRIC(LPSIZE lpSize) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpSize`  
 Apunta a un **tamaño** estructura o un `CSize` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Use esta función cuando da **HIMETRIC** tamaños de OLE, conversión de modo de asignación natural de la aplicación. Tenga en cuenta que las extensiones de ventana y el área de visualización del dispositivo afectará al resultado.  
  
 La conversión se realiza primero las unidades lógicas convirtiéndose en píxeles, con las unidades de asignación actual del contexto de dispositivo y, a continuación, convertir estas unidades en **HIMETRIC** unidades.  
  
##  <a name="a-namemhattribdca--cdcmhattribdc"></a><a name="m_hattribdc"></a>CDC::m_hAttribDC  
 El contexto de dispositivo de atributo para este `CDC` objeto.  
  
```  
HDC m_hAttribDC;  
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este contexto de dispositivo es igual a `m_hDC`. En general, `CDC` llamadas GDI que solicitan información de contexto de dispositivo se dirigen a `m_hAttribDC`. Consulte la [CDC](../../mfc/reference/cdc-class.md) clase descripción para obtener más información sobre el uso de estos contextos de dos dispositivo.  
  
##  <a name="a-namemhdca--cdcmhdc"></a><a name="m_hdc"></a>CDC::m_hDC  
 El contexto de dispositivo de salida para este `CDC` objeto.  
  
```  
HDC m_hDC;  
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `m_hDC` es igual a `m_hAttribDC`, otro contexto de dispositivo ajustado por `CDC`. En general, `CDC` llamadas GDI que creación una salida que se vaya a la `m_hDC` el contexto de dispositivo. Puede inicializar `m_hDC` y `m_hAttribDC` para que apunte a distintos dispositivos. Consulte la [CDC](../../mfc/reference/cdc-class.md) clase descripción para obtener más información sobre el uso de estos contextos de dos dispositivo.  
  
##  <a name="a-namemaskblta--cdcmaskblt"></a><a name="maskblt"></a>CDC::MaskBlt  
 Combina los datos de color para los mapas de bits de origen y destino con la máscara determinada y la operación de trama.  
  
```  
BOOL MaskBlt(
    int x,  
    int y,  
    int nWidth,  
    int nHeight,  
    CDC* pSrcDC,  
    int xSrc,  
    int ySrc,  
    CBitmap& maskBitmap,  
    int xMask,  
    int yMask,  
    DWORD dwRop);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada x lógica de la esquina superior izquierda del rectángulo de destino.  
  
 *y*  
 Especifica la coordenada y lógica de la esquina superior izquierda del rectángulo de destino.  
  
 `nWidth`  
 Especifica el ancho, en unidades lógicas, del mapa de bits de origen y el rectángulo de destino.  
  
 `nHeight`  
 Especifica el alto, en unidades lógicas, del mapa de bits de origen y el rectángulo de destino.  
  
 `pSrcDC`  
 Identifica el contexto de dispositivo desde el que el mapa de bits es va a copiar. Debe ser cero si el *dwRop* parámetro especifica una operación de trama que no incluya un origen.  
  
 `xSrc`  
 Especifica la coordenada x lógica de la esquina superior izquierda del mapa de bits de origen.  
  
 `ySrc`  
 Especifica la coordenada y lógica de la esquina superior izquierda del mapa de bits de origen.  
  
 `maskBitmap`  
 Identifica el mapa de bits de máscara monocromática combinado con el mapa de bits de color en el contexto de dispositivo de origen.  
  
 `xMask`  
 Especifica el desplazamiento horizontal de píxel del mapa de bits de la máscara especificada por el `maskBitmap` parámetro.  
  
 `yMask`  
 Especifica el desplazamiento vertical de píxel del mapa de bits de la máscara especificada por el `maskBitmap` parámetro.  
  
 *dwRop*  
 Especifica el primer y segundo plano códigos de operación de trama ternario, que usa la función para controlar la combinación de datos de origen y destino. El código de operación de trama de fondo se almacena en el byte alto de la palabra alta de este valor; el código de operación de trama de primer plano se almacena en el byte bajo de la palabra alta de este valor; la palabra baja de este valor se omite y debe ser cero. La macro **MAKEROP4** crea dichas combinaciones de primer y segundo plano de los códigos de operación de trama. Vea la sección Comentarios para obtener una explicación del primer y segundo plano en el contexto de esta función. Consulte la `BitBlt` función miembro para obtener una lista de códigos de operación de trama comunes.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Un valor de 1 en la máscara especificada por `maskBitmap` indica que el código de operación de trama de primer plano especificado por *dwRop* debe aplicarse en esa ubicación. Un valor de 0 en la máscara indica que el código de operación de trama de fondo especificado por *dwRop* debe aplicarse en esa ubicación. Si las operaciones de mapa de bits requieren un origen, el rectángulo de máscara debe cubrir el rectángulo de origen. Si no es así, se producirá un error en la función. Si las operaciones de mapa de bits no requieren un origen, el rectángulo de máscara debe cubrir el rectángulo de destino. Si no es así, se producirá un error en la función.  
  
 Si una transformación de rotación o distorsión está en vigor para el contexto de dispositivo de origen cuando se llama a esta función, se produce un error. Sin embargo, se permiten otros tipos de transformaciones.  
  
 Si difieren de los formatos de color de la fuente, el patrón y mapas de bits de destino, esta función convierte el patrón de formato de origen o ambos, para que coincida con el formato de destino. Si el mapa de bits de máscara no es un mapa de bits monocromo, se produce un error. Cuando se está grabando un metarchivo mejorado, se produce un error (y la función devuelve 0) si el contexto de dispositivo de origen identifica un contexto de dispositivo de metarchivo mejorado. No todos los dispositivos admiten `MaskBlt`. Una aplicación debe llamar a `GetDeviceCaps` para determinar si un dispositivo admite esta función. Si no se proporciona ningún mapa de bits de máscara, esta función se comporta exactamente como `BitBlt`, utilizando el código de operación de trama de primer plano. Desplaza el píxel del mapa de mapa de bits de máscara en el punto (0,0) en el mapa de bits del contexto de dispositivo de origen. Esto es útil para casos en que un mapa de bits de máscara contiene un conjunto de máscaras; una aplicación puede aplicar fácilmente cualquiera de ellos a una tarea de fusión de color de máscara ajustando los desplazamientos de píxel y tamaños de rectángulo se envían a `MaskBlt`.  
  
##  <a name="a-namemodifyworldtransforma--cdcmodifyworldtransform"></a><a name="modifyworldtransform"></a>CDC::ModifyWorldTransform  
 Cambia la transformación universal para un contexto de dispositivo mediante el modo especificado.  
  
```  
BOOL ModifyWorldTransform(
    const XFORM& rXform,  
    DWORD iMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `rXform`  
 Hacer referencia a un [XFORM](http://msdn.microsoft.com/library/windows/desktop/dd145228) estructura que se utiliza para modificar la transformación universal para el contexto de dispositivo especificado.  
  
 `iMode`  
 Especifica cómo los datos de transformación modifica la transformación del mundo actual. Para obtener una lista de los valores de este parámetro puede tomar, vea [ModifyWorldTransform](http://msdn.microsoft.com/library/windows/desktop/dd145060).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor distinto de cero en caso de éxito.  
  
 Devuelve 0 en caso de error.  
  
 Para obtener información de error extendida, llame a [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Comentarios  
 Este método ajusta la función GDI de Windows [ModifyWorldTransform](http://msdn.microsoft.com/library/windows/desktop/dd145060).  
  
##  <a name="a-namemovetoa--cdcmoveto"></a><a name="moveto"></a>CDC::MoveTo  
 Mueve la posición actual hasta el punto especificado por *x* y *y* (o `point`).  
  
```  
CPoint MoveTo(
    int x,  
    int y);  
  
CPoint MoveTo(POINT point);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada x lógica de la nueva posición.  
  
 *y*  
 Especifica la coordenada y lógica de la nueva posición.  
  
 `point`  
 Especifica la nueva posición. Puede pasarse un **punto** estructura o un `CPoint` objeto para este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Las coordenadas x e y de la posición anterior como un `CPoint` objeto.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRect::CenterPoint](../../atl-mfc-shared/reference/crect-class.md#centerpoint).  
  
##  <a name="a-nameoffsetcliprgna--cdcoffsetcliprgn"></a><a name="offsetcliprgn"></a>CDC::OffsetClipRgn  
 Mueve la región de recorte del contexto de dispositivo de los desplazamientos indicados.  
  
```  
int OffsetClipRgn(
    int x,  
    int y);  
  
int OffsetClipRgn(SIZE size);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica el número de unidades lógicas para moverse hacia la izquierda o derecha.  
  
 *y*  
 Especifica el número de unidades lógicas para subir o Bajar.  
  
 `size`  
 Especifica la cantidad de desplazamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 Tipo de la nueva región. Puede ser cualquiera de los siguientes valores:  
  
- **COMPLEXREGION** región de recorte tiene bordes se superponen.  
  
- **ERROR** contexto de dispositivo no es válido.  
  
- **NULLREGION** región de recorte está vacía.  
  
- **SIMPLEREGION** región de recorte no tiene bordes superpuestos.  
  
### <a name="remarks"></a>Comentarios  
 La función mueve a la región *x* unidades a lo largo del eje x y *y* unidades a lo largo del eje y.  
  
##  <a name="a-nameoffsetviewportorga--cdcoffsetviewportorg"></a><a name="offsetviewportorg"></a>CDC::OffsetViewportOrg  
 Modifica las coordenadas de la ventanilla del origen de la relación con las coordenadas de la ventanilla de origen actual.  
  
```  
virtual CPoint OffsetViewportOrg(
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 `nWidth`  
 Especifica el número de unidades de dispositivo para agregar a la coordenada x del origen actual.  
  
 `nHeight`  
 Especifica el número de unidades de dispositivo para agregar a la coordenada y del origen actual.  
  
### <a name="return-value"></a>Valor devuelto  
 El origen anterior de ventanilla (en coordenadas de dispositivo) como un `CPoint` objeto.  
  
##  <a name="a-nameoffsetwindoworga--cdcoffsetwindoworg"></a><a name="offsetwindoworg"></a>CDC::OffsetWindowOrg  
 Modifica las coordenadas de la ventana del origen de la relación con las coordenadas del origen de ventana actual.  
  
```  
CPoint OffsetWindowOrg(
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 `nWidth`  
 Especifica el número de unidades lógicas para agregar a la coordenada x del origen actual.  
  
 `nHeight`  
 Especifica el número de unidades lógicas para agregar a la coordenada y del origen actual.  
  
### <a name="return-value"></a>Valor devuelto  
 El origen de ventana anterior (en coordenadas lógicas) como un `CPoint` objeto.  
  
##  <a name="a-nameoperatorhdca--cdcoperator-hdc"></a><a name="operator_hdc"></a>CDC::operator HDC  
 Utilice este operador para recuperar el identificador de contexto de dispositivo de la `CDC` objeto.  
  
```  
operator HDC() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el identificador del objeto de contexto de dispositivo; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Puede utilizar el controlador para llamar directamente a las API de Windows.  
  
##  <a name="a-namepaintrgna--cdcpaintrgn"></a><a name="paintrgn"></a>CDC::PaintRgn  
 Rellena el área especificada por `pRgn` con el pincel actual.  
  
```  
BOOL PaintRgn(CRgn* pRgn);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRgn`  
 Identifica la región que se debe rellenar. Las coordenadas de la región determinada se especifican en unidades lógicas.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
##  <a name="a-namepatblta--cdcpatblt"></a><a name="patblt"></a>CDC::PatBlt  
 Crea un patrón de bits en el dispositivo.  
  
```  
BOOL PatBlt(
    int x,  
    int y,  
    int nWidth,  
    int nHeight,  
    DWORD dwRop);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada x lógica de la esquina superior izquierda del rectángulo que se va a recibir el patrón.  
  
 *y*  
 Especifica la coordenada y lógica de la esquina superior izquierda del rectángulo que se va a recibir el patrón.  
  
 `nWidth`  
 Especifica el ancho (en unidades lógicas) del rectángulo que se va a recibir el patrón.  
  
 `nHeight`  
 Especifica el alto (en unidades lógicas) del rectángulo que se va a recibir el patrón.  
  
 *dwRop*  
 Especifica el código de operación de trama. Códigos de operación de trama (ROPs) definen cómo combina GDI los colores en las operaciones de salida que implican un pincel actual, un mapa de bits de origen posibles y un mapa de bits de destino. Este parámetro puede ser uno de los siguientes valores:  
  
- **PATCOPY** patrón copias en el mapa de bits de destino.  
  
- **PATINVERT** mapa de bits de destino de combina con patrón mediante el operador booleano XOR.  
  
- **DSTINVERT** invierte el mapa de bits de destino.  
  
- **BLACKNESS** pone en negro toda la salida.  
  
- **WHITENESS** pone en blanco toda la salida.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El patrón es una combinación de pincel seleccionado y el modelo ya en el dispositivo. El código de operación de trama especificado por *dwRop* define cómo se pueden combinar los patrones. Las operaciones de trama para esta función son un subconjunto limitado de los códigos de operación de trama ternario 256 completa; en concreto, no se puede usar un código de operación de trama que se hace referencia a un origen.  
  
 No todos los contextos de dispositivo admiten el `PatBlt` (función). Para determinar si un contexto de dispositivo admite `PatBlt`, llame a la `GetDeviceCaps` función miembro con el **RASTERCAPS** indizar y compruebe el valor devuelto para la **RC_BITBLT** marca.  
  
##  <a name="a-namepiea--cdcpie"></a><a name="pie"></a>CDC::pie  
 Dibuja una cuña en forma de gráfico circular dibujando un arco elíptico cuyo centro y dos extremos están unidos por líneas.  
  
```  
BOOL Pie(
    int x1,  
    int y1,  
    int x2,  
    int y2,  
    int x3,  
    int y3,  
    int x4,  
    int y4);

 
BOOL Pie(
    LPCRECT lpRect,
    POINT ptStart,
    POINT ptEnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `x1`  
 Especifica la coordenada x de la esquina superior izquierda del rectángulo delimitador (en unidades lógicas).  
  
 `y1`  
 Especifica la coordenada y de la esquina superior izquierda del rectángulo delimitador (en unidades lógicas).  
  
 `x2`  
 Especifica la coordenada x de la esquina inferior derecha del rectángulo delimitador (en unidades lógicas).  
  
 `y2`  
 Especifica la coordenada y de la esquina inferior derecha del rectángulo delimitador (en unidades lógicas).  
  
 *x3*  
 Especifica la coordenada x del punto de partida del arco (en unidades lógicas). Este punto no debe encontrarse exactamente en el arco.  
  
 `y3`  
 Especifica la coordenada y del punto de partida del arco (en unidades lógicas). Este punto no debe encontrarse exactamente en el arco.  
  
 `x4`  
 Especifica la coordenada x del punto final del arco (en unidades lógicas). Este punto no debe encontrarse exactamente en el arco.  
  
 `y4`  
 Especifica la coordenada y del punto final del arco (en unidades lógicas). Este punto no debe encontrarse exactamente en el arco.  
  
 `lpRect`  
 Especifica el rectángulo delimitador. Puede pasarse un `CRect` objeto o un puntero a un `RECT` estructura para este parámetro.  
  
 `ptStart`  
 Especifica el punto inicial del arco. Este punto no debe encontrarse exactamente en el arco. Puede pasarse un [punto](../../mfc/reference/point-structure1.md) estructura o un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto para este parámetro.  
  
 `ptEnd`  
 Especifica el punto final del arco. Este punto no debe encontrarse exactamente en el arco. Puede pasarse un **punto** estructura o un `CPoint` objeto para este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El centro del arco es el centro del rectángulo delimitador especificado por `x1`, `y1`, `x2`, y `y2` (o `lpRect`). El inicio y puntos finales de arco se especifican mediante *x3*, `y3`, `x4`, y `y4` (o `ptStart` y `ptEnd`).  
  
 El arco se dibuja con el lápiz seleccionado, mueva en una dirección hacia la izquierda. Dos líneas adicionales se extraen de cada extremo al centro del arco. El área en forma de gráfico circular se rellena con el pincel actual. Si *x3* es igual a `x4` y `y3` es igual a `y4`, el resultado es una elipse con una sola línea desde el centro de la elipse hasta el punto ( *x3*, `y3`) o ( `x4`, `y4`).  
  
 La figura dibujada por esta función extiende hasta, pero no incluye las coordenadas derecho e inferior. Esto significa que es el alto de la figura `y2` : `y1` y el ancho de la figura es `x2` : `x1`. El ancho y el alto del rectángulo delimitador deben ser mayores que 2 unidades y las unidades inferior a 32.767.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#37;](../../mfc/codesnippet/cpp/cdc-class_9.cpp)]  
  
##  <a name="a-nameplaymetafilea--cdcplaymetafile"></a><a name="playmetafile"></a>CDC::PlayMetaFile  
 Reproduce el contenido del metarchivo especificado en el contexto de dispositivo.  
  
```  
BOOL PlayMetaFile(HMETAFILE hMF);

 
BOOL PlayMetaFile(
    HENHMETAFILE hEnhMetaFile,  
    LPCRECT lpBounds);
```  
  
### <a name="parameters"></a>Parámetros  
 *hMF*  
 Identifica el metarchivo para reproducirse.  
  
 *hEnhMetaFile*  
 Identifica el metarchivo mejorado.  
  
 `lpBounds`  
 Apunta a un `RECT` estructura o un `CRect` objeto que contiene las coordenadas del rectángulo delimitador que se utiliza para mostrar la imagen. Las coordenadas se especifican en unidades lógicas.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Metarchivo se puede reproducir en cualquier número de veces.  
  
 La segunda versión de `PlayMetaFile` muestra la imagen almacenada en el metarchivo de formato mejorado determinado. Cuando una aplicación llama a la segunda versión de `PlayMetaFile`, Windows utiliza el marco de imagen en el encabezado del metarchivo mejorado para asignar la imagen en el rectángulo que apunta el `lpBounds` parámetro. (Esta imagen se puede recorta o girar estableciendo la transformación universal en el dispositivo de salida antes de llamar a `PlayMetaFile`.) Puntos a lo largo de los bordes del rectángulo se incluyen en la imagen. Puede recortarse una imagen de metarchivo mejorado mediante la definición de la región de recorte en el dispositivo de salida antes de reproducir el metarchivo mejorado.  
  
 Si un metarchivo mejorado contiene una paleta opcional, una aplicación puede obtener colores coherentes estableciendo una paleta de colores en el dispositivo de salida antes de llamar a la segunda versión de `PlayMetaFile`. Para recuperar la paleta opcional, use la **GetEnhMetaFilePaletteEntries** función de Windows. Un metarchivo mejorado se puede incrustar en un metarchivo mejorado recién creado mediante una llamada a la segunda versión de `PlayMetaFile` y reproducción de metarchivo mejorado de origen en el contexto de dispositivo para el nuevo metarchivo mejorado.  
  
 Los Estados del contexto de dispositivo de salida se conservan mediante esta función. Esta función elimina cualquier objeto creado pero no se eliminan del metarchivo mejorado. Para detener esta función, una aplicación puede llamar a la **CancelDC** función de Windows desde otro subproceso para finalizar la operación. En este caso, la función devuelve cero.  
  
##  <a name="a-nameplgblta--cdcplgblt"></a><a name="plgblt"></a>CDC::PlgBlt  
 Realiza a una transferencia de bloque de bits de los bits de datos de color desde el rectángulo especificado en el contexto de dispositivo de origen al paralelogramo especificado en el contexto de dispositivo determinado.  
  
```  
BOOL PlgBlt(
    LPPOINT lpPoint,  
    CDC* pSrcDC,  
    int xSrc,  
    int ySrc,  
    int nWidth,  
    int nHeight,  
    CBitmap& maskBitmap,  
    int xMask,  
    int yMask);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPoint`  
 Apunta a una matriz de tres puntos en el espacio lógico que identifica tres esquinas paralelogramo de destino. La esquina superior izquierda del rectángulo de origen se asigna al primer punto en la esquina inferior izquierda hasta el tercer punto, la esquina superior derecha hasta el segundo punto de la matriz y esta matriz. La esquina inferior derecha del rectángulo de origen se asigna hasta el cuarto punto implícito en el paralelogramo.  
  
 `pSrcDC`  
 Identifica el contexto de dispositivo de origen.  
  
 `xSrc`  
 Especifica la coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.  
  
 `ySrc`  
 Especifica la coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de origen.  
  
 `nWidth`  
 Especifica el ancho, en unidades lógicas, del rectángulo de origen.  
  
 `nHeight`  
 Especifica el alto, en unidades lógicas, del rectángulo de origen.  
  
 `maskBitmap`  
 Identifica un mapa de bits monocromo opcional que se utiliza para enmascarar los colores del rectángulo de origen.  
  
 `xMask`  
 Especifica la coordenada x de la esquina superior izquierda del mapa de bits monocromático.  
  
 `yMask`  
 Especifica la coordenada y de la esquina superior izquierda del mapa de bits monocromático.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si el identificador de la máscara de bits dado identifica un mapa de bits monocromático válido, la función utiliza este mapa de bits para enmascarar los bits de datos de color del rectángulo de origen.  
  
 Cuarto vértice del paralelogramo (D) se define por el tratamiento de los primeros tres puntos (A, B y C) como vectores y computación D = B + C - A.  
  
 Si existe la máscara de bits, un valor de 1 en la máscara indica que el color de píxel de origen debe copiarse en el destino. Un valor de 0 en la máscara indica que es el color de píxel de destino no pueden ser modificados.  
  
 Si el rectángulo de máscara es menor que los rectángulos de origen y destino, la función replica el patrón de máscara.  
  
 Se permiten las transformaciones de escala, traslación y reflexión en el contexto de dispositivo de origen; Sin embargo, las transformaciones de giro y recorte no lo son. Si el mapa de bits de máscara no es un mapa de bits monocromo, se produce un error. El modo de ajuste para el contexto de dispositivo de destino se utiliza para determinar cómo estirar o comprimir los píxeles, si es necesario. Cuando se está grabando un metarchivo mejorado, se produce un error si el contexto de dispositivo de origen identifica un contexto de dispositivo de metarchivo mejorado.  
  
 Las coordenadas de destino se transforman según el contexto de dispositivo de destino; las coordenadas de origen se transforman según el contexto de dispositivo de origen. Si la transformación de origen tiene un giro o un recorte, se devuelve un error. Si los rectángulos de origen y destino no tienen el mismo formato de color, `PlgBlt` convierte el rectángulo de origen para que coincidan con el rectángulo de destino. No todos los dispositivos admiten `PlgBlt`. Para obtener más información, vea la descripción de la **RC_BITBLT** capacidad de trama en el `CDC::GetDeviceCaps` función miembro.  
  
 Si los contextos de dispositivo de origen y destino representan dispositivos incompatibles, `PlgBlt` devuelve un error.  
  
##  <a name="a-namepolybeziera--cdcpolybezier"></a><a name="polybezier"></a>CDC::PolyBezier  
 Dibuja curvas spline Bzier uno o más.  
  
```  
BOOL PolyBezier(
    const POINT* lpPoints,  
    int nCount);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPoints`  
 Apunta a una matriz de [punto](../../mfc/reference/point-structure1.md) estructuras de datos que contienen los extremos y puntos de control de la spline(s).  
  
 `nCount`  
 Especifica el número de puntos en el `lpPoints` matriz. Este valor debe ser uno más de tres veces el número de curvas spline para dibujar, porque cada spline Bzier requiere la spline inicial, dos puntos de control y un extremo requiere un punto de inicio adicional.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función dibuja curvas spline cúbica Bzier utilizando los extremos y los puntos de control especificados por el `lpPoints` parámetro. La primera curva spline se dibuja desde el primer punto hasta el cuarto punto mediante el segundo y tercer puntos como puntos de control. Cada spline posterior de la secuencia necesita exactamente tres puntos más: el punto final de la curva spline anterior se utiliza como punto de partida, los dos puntos de la secuencia son puntos de control y el tercero es el punto final.  
  
 La posición actual no se utiliza ni se actualiza el `PolyBezier` (función). No se ha rellenado la ilustración. Esta función dibuja líneas con el lápiz.  
  
##  <a name="a-namepolybeziertoa--cdcpolybezierto"></a><a name="polybezierto"></a>CDC::PolyBezierTo  
 Dibuja curvas spline Bzier uno o más.  
  
```  
BOOL PolyBezierTo(
    const POINT* lpPoints,  
    int nCount);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPoints`  
 Apunta a una matriz de [punto](../../mfc/reference/point-structure1.md) estructuras de datos que contiene los extremos y control de puntos.  
  
 `nCount`  
 Especifica el número de puntos en el `lpPoints` matriz. Este valor debe ser tres veces el número de curvas spline para dibujar, porque cada spline Bzier requiere dos puntos de control y un punto final.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función dibuja curvas spline Bzier cúbica utilizando los puntos de control especificados por el `lpPoints` parámetro. La primera curva spline se dibuja desde la posición actual hasta el tercer punto mediante el uso de los primeros dos puntos como puntos de control. Para cada spline posterior, la función necesita exactamente tres puntos más y usa el punto final de la curva spline anterior como punto de partida para la siguiente. `PolyBezierTo`Mueve la posición actual hasta el punto final de la última spline Bzier. No se ha rellenado la ilustración. Esta función dibuja líneas con el lápiz.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CDC:: beginpath](#beginpath).  
  
##  <a name="a-namepolydrawa--cdcpolydraw"></a><a name="polydraw"></a>CDC::PolyDraw  
 Dibuja un conjunto de segmentos de líneas y curvas spline de Bzier.  
  
```  
BOOL PolyDraw(
    const POINT* lpPoints,  
    const BYTE* lpTypes,  
    int nCount);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPoints`  
 Apunta a una matriz de [punto](../../mfc/reference/point-structure1.md) estructuras de datos que contiene los extremos para cada segmento y los extremos de línea y puntos para cada spline Bzier de control.  
  
 `lpTypes`  
 Apunta a una matriz que especifica cómo cada punto en el `lpPoints` se utiliza la matriz. Valores pueden ser uno de los siguientes:  
  
- **PT_MOVETO** especifica que este punto inicia una figura separada. Este punto se convierte en la nueva posición actual.  
  
- **PT_LINETO** especifica que una línea se dibuja desde la posición actual hasta este punto, que se convierte en la nueva posición actual.  
  
- **PT_BEZIERTO** especifica que este punto es un punto de control o un punto final de una curva spline de Bzier.  
  
 **PT_BEZIERTO** se producen siempre tipos de conjuntos de tres. La posición actual define el punto de partida para la spline Bzier. Los dos primeros **PT_BEZIERTO** puntos son los puntos de control y el tercero **PT_BEZIERTO** punto es el punto final. El punto final se convierte en la nueva posición actual. Si no hay tres consecutivos **PT_BEZIERTO** puntos, produce un error.  
  
     Un **PT_LINETO** o **PT_BEZIERTO** se puede combinar con las constantes de tipo mediante el operador bit a bit o se cierra indicar que el punto correspondiente es el último punto de una figura y la ilustración:  
  
- **PT_CLOSEFIGURE** especifica que la figura se cierra automáticamente después de la **PT_LINETO** o **PT_BEZIERTO** tipo de este punto. Se dibuja una línea desde este punto para la última **PT_MOVETO** o `MoveTo` de punto.  
  
     Este indicador se combina con la **PT_LINETO** tipo de una línea o con el **PT_BEZIERTO** tipo de final de una curva spline Bzier, mediante el uso de bit a bit `OR` operador. Se establece la posición actual hasta el punto final de la línea de cierre.  
  
 `nCount`  
 Especifica el número total de puntos en el `lpPoints` de matriz, el mismo que el número de bytes en el `lpTypes` matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función puede utilizarse para dibujar ilustraciones separados en lugar de llamadas consecutivas para `CDC::MoveTo`, `CDC::LineTo`, y `CDC::PolyBezierTo` funciones miembro. Las líneas y curvas spline se dibuja con el lápiz actual y no se han rellenado las cifras. Si hay una ruta de acceso activa iniciado mediante una llamada a la `CDC::BeginPath` función miembro, `PolyDraw` agrega a la ruta de acceso. Los puntos incluidos en el `lpPoints` matriz y en `lpTypes` indican si cada punto forma parte de un `CDC::MoveTo`, `CDC::LineTo`, o un **CDC::BezierTo** operación. También es posible cerrar cifras. Esta función actualiza la posición actual.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CDC:: beginpath](#beginpath).  
  
##  <a name="a-namepolygona--cdcpolygon"></a><a name="polygon"></a>CDC::Polygon  
 Dibuja un polígono que consta de dos o más puntos (vértices) conectados por líneas, con el lápiz.  
  
```  
BOOL Polygon(
    LPPOINT lpPoints,  
    int nCount);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPoints`  
 Apunta a una matriz de puntos que especifica los vértices del polígono. Cada punto de la matriz es un **punto** estructura o un `CPoint` objeto.  
  
 `nCount`  
 Especifica el número de vértices de la matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El sistema cierra el polígono automáticamente, si es necesario, dibujando una línea desde el último vértice al primero.  
  
 El modo de relleno de polígono actual se puede recuperar o establecer mediante el `GetPolyFillMode` y `SetPolyFillMode` funciones miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#38;](../../mfc/codesnippet/cpp/cdc-class_10.cpp)]  
  
##  <a name="a-namepolylinea--cdcpolyline"></a><a name="polyline"></a>CDC::Polyline  
 Dibuja un conjunto de segmentos de línea que conecta los puntos especificados por `lpPoints`.  
  
```  
BOOL Polyline(
    LPPOINT lpPoints,  
    int nCount);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPoints`  
 Apunta a una matriz de **punto** estructuras o `CPoint` objetos que se va a estar conectado.  
  
 `nCount`  
 Especifica el número de puntos de la matriz. Este valor debe ser al menos 2.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Las líneas se dibujan desde el primer punto a través de los puntos posteriores con el lápiz. A diferencia de la `LineTo` función miembro, el `Polyline` función no usa ni actualiza la posición actual.  
  
 Para obtener más información, consulte [PolyLine](http://msdn.microsoft.com/library/windows/desktop/dd162815) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namepolylinetoa--cdcpolylineto"></a><a name="polylineto"></a>CDC::PolylineTo  
 Dibuja una o varias líneas rectas.  
  
```  
BOOL PolylineTo(
    const POINT* lpPoints,  
    int nCount);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPoints`  
 Apunta a una matriz de [punto](../../mfc/reference/point-structure1.md) estructuras de datos que contiene los vértices de la línea.  
  
 `nCount`  
 Especifica el número de puntos de la matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Se dibuja una línea desde la posición actual hasta el primer punto especificado por el `lpPoints` parámetro utilizando el lápiz actual. Para cada línea adicional, la función dibuja desde el punto final de la línea anterior en el siguiente punto especificado por `lpPoints`. `PolylineTo`Mueve la posición actual hasta el punto final de la última línea. Si los segmentos de línea dibujados por esta función forman una figura cerrada, no se rellena en la ilustración.  
  
##  <a name="a-namepolypolygona--cdcpolypolygon"></a><a name="polypolygon"></a>CDC::PolyPolygon  
 Crea dos o más de los polígonos que se rellenan con el modo de relleno de polígono actual.  
  
```  
BOOL PolyPolygon(
    LPPOINT lpPoints,  
    LPINT lpPolyCounts,  
    int nCount);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPoints`  
 Apunta a una matriz de **punto** estructuras o `CPoint` objetos que definen los vértices de los polígonos.  
  
 `lpPolyCounts`  
 Apunta a una matriz de enteros, cada uno de los cuales especifica el número de puntos en uno de los polígonos de la `lpPoints` matriz.  
  
 `nCount`  
 El número de entradas en la `lpPolyCounts` matriz. Este número especifica el número de polígonos para dibujar. Este valor debe ser al menos 2.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Los polígonos pueden no contiguos o superpuestos.  
  
 Cada polígono especificado en una llamada a la `PolyPolygon` función debe cerrarse. A diferencia de los polígonos creados por la **polígono** función miembro, los polígonos creados por `PolyPolygon` no se cierran automáticamente.  
  
 La función crea dos o varios polígonos. Para crear un polígono, una aplicación debe utilizar el **polígono** función miembro.  
  
 El modo de relleno de polígono actual se puede recuperar o establecer mediante el `GetPolyFillMode` y `SetPolyFillMode` funciones miembro.  
  
##  <a name="a-namepolypolylinea--cdcpolypolyline"></a><a name="polypolyline"></a>CDC::PolyPolyline  
 Dibuja varias series de segmentos de línea conectados.  
  
```  
BOOL PolyPolyline(
    const POINT* lpPoints,  
    const DWORD* lpPolyPoints,  
    int nCount);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPoints`  
 Apunta a una matriz de estructuras que contiene los vértices de las polilíneas. Las polilíneas se especifican de forma consecutiva.  
  
 `lpPolyPoints`  
 Apunta a una matriz de variables que especifica el número de puntos en el `lpPoints` matriz para el polígono correspondiente. Cada entrada debe ser mayor o igual a 2.  
  
 `nCount`  
 Especifica el número total de recuentos en los `lpPolyPoints` matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Los segmentos de línea se dibujan con el lápiz. No se han rellenado las cifras formadas por los segmentos. La posición actual no se utiliza ni se actualiza esta función.  
  
##  <a name="a-nameptvisiblea--cdcptvisible"></a><a name="ptvisible"></a>CDC::PtVisible  
 Determina si el punto especificado está dentro de la región de recorte del contexto de dispositivo.  
  
```  
virtual BOOL PtVisible(
    int x,  
    int y) const;  
  
BOOL PtVisible(POINT point) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada x lógica del punto.  
  
 *y*  
 Especifica la coordenada y lógica del punto.  
  
 `point`  
 Especifica el punto de comprobación en coordenadas lógicas. Puede pasarse un **punto** estructura o un `CPoint` objeto para este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el punto especificado está dentro de la región de recorte en caso contrario, 0.  
  
##  <a name="a-namequeryaborta--cdcqueryabort"></a><a name="queryabort"></a>CDC:: QueryAbort  
 Llama a la función de anulación instalada por el [ayudar a](#setabortproc) función miembro de una aplicación de impresión y consultas si se debe finalizar la impresión.  
  
```  
BOOL QueryAbort() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto es distinto de cero si la impresión debe continuar o si no hay ningún procedimiento de anulación. Es 0 si se debe finalizar el trabajo de impresión. El valor devuelto es proporcionado por la función de anulación.  
  
##  <a name="a-namerealizepalettea--cdcrealizepalette"></a><a name="realizepalette"></a>CDC::RealizePalette  
 Asigna las entradas de la paleta lógica actual a la paleta del sistema.  
  
```  
UINT RealizePalette();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Indica cuántas entradas en la paleta lógica se asignaron a diferentes entradas de la paleta del sistema. Representa el número de entradas que esta función se reasigna para alojar los cambios en la paleta del sistema desde la última se logró la paleta lógica.  
  
### <a name="remarks"></a>Comentarios  
 Una paleta de colores lógica actúa como un búfer entre aplicaciones con uso intensivo de color y el sistema, lo que una aplicación utilice según sea necesario sin interferir con su propio número de colores muestra colores o con colores que se muestran por otras ventanas.  
  
 Cuando una ventana tiene el foco de entrada y llama `RealizePalette`, Windows garantiza que la ventana muestra todos los colores solicitados, hasta el número máximo disponible simultáneamente en la pantalla. Windows también muestra los colores que no se encuentra en la paleta de la ventana comparando los colores disponibles.  
  
 Además, Windows coincide con los colores solicitados por las ventanas inactivas que llame a la función tan cerca como sea posible para los colores disponibles. Esto reduce significativamente los cambios no deseados en los colores que se muestran en las ventanas inactivas.  
  
##  <a name="a-namerectanglea--cdcrectangle"></a><a name="rectangle"></a>CDC::Rectangle  
 Dibuja un rectángulo con el lápiz.  
  
```  
BOOL Rectangle(
    int x1,  
    int y1,  
    int x2,  
    int y2);  
  
BOOL Rectangle(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `x1`  
 Especifica la coordenada x de la esquina superior izquierda del rectángulo (en unidades lógicas).  
  
 `y1`  
 Especifica la coordenada y de la esquina superior izquierda del rectángulo (en unidades lógicas).  
  
 `x2`  
 Especifica la coordenada x de la esquina inferior derecha del rectángulo (en unidades lógicas).  
  
 `y2`  
 Especifica la coordenada y de la esquina inferior derecha del rectángulo (en unidades lógicas).  
  
 `lpRect`  
 Especifica el rectángulo en unidades lógicas. Puede pasarse un `CRect` objeto o un puntero a un `RECT` estructura para este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El interior del rectángulo se rellena con el pincel actual.  
  
 El rectángulo se extiende hasta, pero no incluye las coordenadas derecho e inferior. Esto significa que el alto del rectángulo es `y2` : `y1` y el ancho del rectángulo es `x2` : `x1`. El ancho y el alto de un rectángulo deben ser mayores que 2 unidades y las unidades inferior a 32.767.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#39;](../../mfc/codesnippet/cpp/cdc-class_11.cpp)]  
  
##  <a name="a-namerectvisiblea--cdcrectvisible"></a><a name="rectvisible"></a>CDC::RectVisible  
 Determina si cualquier parte del rectángulo especificado está dentro de la región de recorte del contexto de presentación.  
  
```  
virtual BOOL RectVisible(LPCRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Apunta a un `RECT` estructura o un `CRect` objeto que contiene las coordenadas lógicas del rectángulo especificado.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si alguna parte del rectángulo especificado está dentro de la región de recorte en caso contrario, 0.  
  
##  <a name="a-namereleaseattribdca--cdcreleaseattribdc"></a><a name="releaseattribdc"></a>CDC::ReleaseAttribDC  
 Llame a esta función miembro para establecer `m_hAttribDC` a **NULL**.  
  
```  
virtual void ReleaseAttribDC();
```  
  
### <a name="remarks"></a>Comentarios  
 Esto no provoca un **separar** que se produzca. Solo el contexto de dispositivo de salida se adjunta a la `CDC` objeto y sólo se pueden separar.  
  
##  <a name="a-namereleaseoutputdca--cdcreleaseoutputdc"></a><a name="releaseoutputdc"></a>CDC::ReleaseOutputDC  
 Llame a esta función miembro para establecer el `m_hDC` miembro **NULL**.  
  
```  
virtual void ReleaseOutputDC();
```  
  
### <a name="remarks"></a>Comentarios  
 No se puede llamar a esta función miembro cuando se adjunta al contexto de dispositivo de salida a la `CDC` objeto. Utilice la **separar** función miembro para desasociar el contexto de dispositivo de salida.  
  
##  <a name="a-nameresetdca--cdcresetdc"></a><a name="resetdc"></a>CDC::ResetDC  
 Llame a esta función miembro para actualizar el contexto de dispositivo ajustado por el `CDC` objeto.  
  
```  
BOOL ResetDC(const DEVMODE* lpDevMode);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpDevMode*  
 Un puntero a un Windows `DEVMODE` estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El contexto de dispositivo se actualiza desde la información especificada en las ventanas `DEVMODE` estructura. Esta función miembro sólo restablece el contexto de dispositivo de atributo.  
  
 Una aplicación normalmente utilizará el `ResetDC` función de miembro cuando procesa una ventana de un `WM_DEVMODECHANGE` mensaje. También puede utilizar esta función miembro para cambiar la orientación del papel o las bandejas de papel mientras se imprime un documento.  
  
 No se puede utilizar esta función miembro para cambiar el nombre del controlador, el nombre de dispositivo o puerto de salida. Cuando el usuario cambia la conexión de puerto o el nombre del dispositivo, debe eliminar el contexto de dispositivo original y crear un nuevo contexto de dispositivo con la nueva información.  
  
 Antes de llamar a esta función miembro, debe asegurarse de que se han seleccionado todos los objetos (que no sean objetos de stock) que hubiera seleccionado en el contexto de dispositivo de salida.  
  
##  <a name="a-namerestoredca--cdcrestoredc"></a><a name="restoredc"></a>CDC::RestoreDC  
 Restaura el contexto de dispositivo al estado anterior identificado por `nSavedDC`.  
  
```  
virtual BOOL RestoreDC(int nSavedDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `nSavedDC`  
 Especifica el contexto de dispositivo que se restaure. Puede ser un valor devuelto por un método `SaveDC` llamada de función. Si `nSavedDC` es -1, el último guardado se restaura el contexto de dispositivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se ha restaurado el contexto especificado; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 `RestoreDC`restaura el contexto de dispositivo extrayendo la información de estado de una pila creada mediante llamadas anteriores a la `SaveDC` función miembro.  
  
 La pila puede contener la información de estado para varios contextos de dispositivo. Si el contexto especificado por `nSavedDC` no está en la parte superior de la pila, `RestoreDC` elimina toda la información de estado entre el contexto de dispositivo especificado por `nSavedDC` y la parte superior de la pila. Se pierde la información eliminada.  
  
##  <a name="a-nameroundrecta--cdcroundrect"></a><a name="roundrect"></a>CDC::RoundRect  
 Dibuja un rectángulo con esquinas redondeadas con el lápiz.  
  
```  
BOOL RoundRect(
    int x1,  
    int y1,  
    int x2,  
    int y2,  
    int x3,  
    int y3);

 
BOOL RoundRect(
    LPCRECT lpRect,
    POINT point);
```  
  
### <a name="parameters"></a>Parámetros  
 `x1`  
 Especifica la coordenada x de la esquina superior izquierda del rectángulo (en unidades lógicas).  
  
 `y1`  
 Especifica la coordenada y de la esquina superior izquierda del rectángulo (en unidades lógicas).  
  
 `x2`  
 Especifica la coordenada x de la esquina inferior derecha del rectángulo (en unidades lógicas).  
  
 `y2`  
 Especifica la coordenada y de la esquina inferior derecha del rectángulo (en unidades lógicas).  
  
 *x3*  
 Especifica el ancho de la elipse que se utiliza para dibujar las esquinas redondeadas (en unidades lógicas).  
  
 `y3`  
 Especifica el alto de la elipse que se utiliza para dibujar las esquinas redondeadas (en unidades lógicas).  
  
 `lpRect`  
 Especifica el rectángulo delimitador en unidades lógicas. Puede pasarse un `CRect` objeto o un puntero a un `RECT` estructura para este parámetro.  
  
 `point`  
 La coordenada x de `point` especifica el ancho de la elipse para dibujar las esquinas redondeadas (en unidades lógicas). La coordenada y de `point` especifica el alto de la elipse para dibujar las esquinas redondeadas (en unidades lógicas). Puede pasarse un **punto** estructura o un `CPoint` objeto para este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El interior del rectángulo se rellena con el pincel actual.  
  
 La figura de que esta función dibuja extiende hasta, pero no incluye las coordenadas derecho e inferior. Esto significa que es el alto de la figura `y2` : `y1` y el ancho de la figura es `x2` : `x1`. El alto y el ancho del rectángulo delimitador deben ser mayores que 2 unidades y las unidades inferior a 32.767.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView Nº&40;](../../mfc/codesnippet/cpp/cdc-class_12.cpp)]  
  
##  <a name="a-namesavedca--cdcsavedc"></a><a name="savedc"></a>CDC::SaveDC  
 Guarda el estado actual del contexto de dispositivo mediante la copia de la información de estado (como la región de recorte, los objetos seleccionados y modo de asignación) a una pila de contexto mantenida por Windows.  
  
```  
virtual int SaveDC();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Entero que identifica el contexto de dispositivo guardado. Es 0 si se produce un error. Esto devuelve el valor puede utilizarse para restaurar el contexto de dispositivo llamando a `RestoreDC`.  
  
### <a name="remarks"></a>Comentarios  
 Más adelante puede restaurarse utilizando el contexto de dispositivo guardado `RestoreDC`.  
  
 `SaveDC`Puede usar cualquier número de veces para guardar cualquier número de Estados de contexto de dispositivo.  
  
##  <a name="a-namescaleviewportexta--cdcscaleviewportext"></a><a name="scaleviewportext"></a>CDC::ScaleViewportExt  
 Modifica las extensiones del área de visualización en relación con los valores actuales.  
  
```  
virtual CSize ScaleViewportExt(
    int xNum,  
    int xDenom,  
    int yNum,  
    int yDenom);
```  
  
### <a name="parameters"></a>Parámetros  
 `xNum`  
 Especifica la cantidad por la que se va a multiplicar la extensión x actual.  
  
 `xDenom`  
 Especifica la cantidad por la que se va a dividir el resultado de multiplicar la extensión x actual por el valor de la `xNum` parámetro.  
  
 `yNum`  
 Especifica la cantidad por la que se va a multiplicar la extensión y actual.  
  
 `yDenom`  
 Especifica la cantidad por la que se va a dividir el resultado de multiplicar la extensión y actual por el valor de la `yNum` parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Las extensiones de ventanilla anterior (en unidades de dispositivo) como un `CSize` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Las fórmulas se escriben como sigue:  
  
 `xNewVE = ( xOldVE * xNum ) / xDenom`  
  
 `yNewVE = ( yOldVE * yNum ) / yDenom`  
  
 Las nuevas extensiones de la ventanilla se calculan multiplicando las extensiones actuales por el numerador determinado y, a continuación, dividiendo el denominador determinado.  
  
##  <a name="a-namescalewindowexta--cdcscalewindowext"></a><a name="scalewindowext"></a>CDC::ScaleWindowExt  
 Modifica las extensiones de ventana en relación con los valores actuales.  
  
```  
virtual CSize ScaleWindowExt(
    int xNum,  
    int xDenom,  
    int yNum,  
    int yDenom);
```  
  
### <a name="parameters"></a>Parámetros  
 `xNum`  
 Especifica la cantidad por la que se va a multiplicar la extensión x actual.  
  
 `xDenom`  
 Especifica la cantidad por la que se va a dividir el resultado de multiplicar la extensión x actual por el valor de la `xNum` parámetro.  
  
 `yNum`  
 Especifica la cantidad por la que se va a multiplicar la extensión y actual.  
  
 `yDenom`  
 Especifica la cantidad por la que se va a dividir el resultado de multiplicar la extensión y actual por el valor de la `yNum` parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Las extensiones de ventana anterior (en unidades lógicas) como un `CSize` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Las fórmulas se escriben como sigue:  
  
 `xNewWE = ( xOldWE * xNum ) / xDenom`  
  
 `yNewWE = ( yOldWE * yNum ) / yDenom`  
  
 Las nuevas extensiones de ventana se calculan multiplicando las extensiones actuales por el numerador determinado y, a continuación, dividiendo el denominador determinado.  
  
##  <a name="a-namescrolldca--cdcscrolldc"></a><a name="scrolldc"></a>CDC::ScrollDC  
 Desplaza un rectángulo de bits horizontal y verticalmente.  
  
```  
BOOL ScrollDC(
    int dx,  
    int dy,  
    LPCRECT lpRectScroll,  
    LPCRECT lpRectClip,  
    CRgn* pRgnUpdate,  
    LPRECT lpRectUpdate);
```  
  
### <a name="parameters"></a>Parámetros  
 `dx`  
 Especifica el número de unidades de desplazamiento horizontal.  
  
 *dy*  
 Especifica el número de unidades de desplazamiento vertical.  
  
 `lpRectScroll`  
 Apunta a la `RECT` estructura o `CRect` objeto que contiene las coordenadas del rectángulo de desplazamiento.  
  
 `lpRectClip`  
 Apunta a la `RECT` estructura o `CRect` objeto que contiene las coordenadas del rectángulo de recorte. Cuando este rectángulo es menor que el original uno señala `lpRectScroll`, desplazar el sólo en el rectángulo más pequeño.  
  
 `pRgnUpdate`  
 Identifica la región detectada por el proceso de desplazamiento. El `ScrollDC` función define esta región; no es necesariamente un rectángulo.  
  
 `lpRectUpdate`  
 Apunta a la `RECT` estructura o `CRect` objeto que recibe las coordenadas del rectángulo que delimita la región desplazable de la actualización. Este es el área rectangular más grande que requiere la actualización de la pantalla. Los valores de la estructura o el objeto cuando la función devuelve están en coordenadas de cliente, independientemente del modo de asignación para el contexto de dispositivo determinado.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se ejecuta el desplazamiento; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si `lpRectUpdate` es **NULL**, Windows no calcula el rectángulo de actualización. Si ambos `pRgnUpdate` y `lpRectUpdate` son **NULL**, Windows no puede computar la región de actualización. Si `pRgnUpdate` no **NULL**, Windows asume que contiene un puntero válido a la región detectado por el proceso de desplazamiento (definida por el `ScrollDC` función miembro). La región de actualización devuelve en `lpRectUpdate` puede pasarse a `CWnd::InvalidateRgn` si es necesario.  
  
 Una aplicación debe utilizar el `ScrollWindow` función miembro de clase `CWnd` cuando es necesario desplazar el área de cliente de una ventana. De lo contrario, debe utilizar `ScrollDC`.  
  
##  <a name="a-nameselectclippatha--cdcselectclippath"></a><a name="selectclippath"></a>CDC::SelectClipPath  
 Selecciona la ruta de acceso actual como una región de recorte para el contexto de dispositivo, que combina la región nueva con una región de recorte existente utilizando el modo especificado.  
  
```  
BOOL SelectClipPath(int nMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `nMode`  
 Especifica la forma de usar la ruta de acceso. Se permiten los valores siguientes:  
  
- **RGN_AND** la nueva región de recorte incluye la intersección (las áreas superpuestas) de la región de recorte actual y la ruta de acceso actual.  
  
- **RGN_COPY** la nueva región de recorte es la ruta de acceso actual.  
  
- **RGN_DIFF** la nueva región de recorte incluye las áreas de la región de recorte actual y se excluyen los de la ruta de acceso actual.  
  
- **RGN_OR** la nueva región de recorte incluye la unión (áreas combinadas) de la región de recorte actual y la ruta de acceso actual.  
  
- **RGN_XOR** la nueva región de recorte incluye la unión de la región de recorte actual y la ruta de acceso actual, pero sin las áreas superpuestas.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El contexto de dispositivo identificado debe contener un trayecto cerrado.  
  
##  <a name="a-nameselectcliprgna--cdcselectcliprgn"></a><a name="selectcliprgn"></a>CDC::SelectClipRgn  
 Selecciona la región como región de recorte actual para el contexto de dispositivo.  
  
```  
int SelectClipRgn(CRgn* pRgn);

 
int SelectClipRgn(
    CRgn* pRgn,  
    int nMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRgn`  
 Identifica la región que va a seleccionar.  
  
-   Para la primera versión de esta función, si este valor es **NULL**, toda el área cliente está seleccionado y aún se recorta el resultado a la ventana.  
  
-   Para la segunda versión de esta función, este identificador puede ser **NULL** sólo cuando el **RGN_COPY** se especifica el modo.  
  
 `nMode`  
 Especifica que se realice la operación. Debe ser uno de los siguientes valores:  
  
- **RGN_AND** la nueva región de recorte combina las áreas superpuestas de la región de recorte actual y la región indicada por `pRgn`.  
  
- **RGN_COPY** la nueva región de recorte es una copia de la región indicada por `pRgn`. Ésta es una función es idéntica a la primera versión de `SelectClipRgn`. Si la región identificada por `pRgn` es **NULL**, la nueva región de recorte se convierte en la región de recorte de forma predeterminada (región null).  
  
- **RGN_DIFF** la nueva región de recorte combina las áreas de la región de recorte actual con esas áreas que se excluye de la región identificada por `pRgn`.  
  
- **RGN_OR** la nueva región de recorte combina la región de recorte actual y la región indicada por `pRgn`.  
  
- **RGN_XOR** la nueva región de recorte combina la región de recorte actual y la región indicada por `pRgn` pero excluye las áreas superpuestas.  
  
### <a name="return-value"></a>Valor devuelto  
 Tipo de región. Puede ser cualquiera de los siguientes valores:  
  
- **COMPLEXREGION** nueva región de recorte tiene bordes se superponen.  
  
- **ERROR** contexto de dispositivo o la región no es válido.  
  
- **NULLREGION** nueva región de recorte está vacía.  
  
- **SIMPLEREGION** nueva región de recorte no tiene bordes superpuestos.  
  
### <a name="remarks"></a>Comentarios  
 Se utiliza sólo una copia de la región seleccionada. Se puede seleccionar la región de sí mismo para cualquier número de otros contextos de dispositivo, o se puede eliminar.  
  
 La función supone que las coordenadas de la región determinada se especifican en unidades del dispositivo. Algunos dispositivos de impresora admiten la salida de texto con una resolución mayor que la salida de gráficos a fin de conservar la precisión necesaria para expresar las métricas de texto. Estos dispositivos informes unidades del dispositivo en una resolución mayor, es decir, en unidades de texto. Estos dispositivos, a continuación, escalación coordenadas de los gráficos para que varias informe asignación de unidades de dispositivo a sólo 1 unidad de gráfico. Siempre debe llamar a la `SelectClipRgn` funcionar con unidades de texto.  
  
 Pueden usar aplicaciones que deben realizar el escalado de objetos gráficos en el GDI la **GETSCALINGFACTOR** de escape de impresora para determinar el factor de escala. Este factor de escala afecta a recorte. Si se usa una región de recorte de gráficos, GDI divide las coordenadas por el factor de escala. Si se utiliza la región de recorte de texto, GDI no realiza ningún ajuste de escala. Un factor de escala de 1 hace que las coordenadas que se divide por 2. un factor de escala de 2 hace que las coordenadas que se divide por 4; y así sucesivamente.  
  
##  <a name="a-nameselectobjecta--cdcselectobject"></a><a name="selectobject"></a>CDC::SelectObject  
 Selecciona un objeto en el contexto de dispositivo.  
  
```  
CPen* SelectObject(CPen* pPen);  
CBrush* SelectObject(CBrush* pBrush);  
virtual CFont* SelectObject(CFont* pFont);  
CBitmap* SelectObject(CBitmap* pBitmap);  
int SelectObject(CRgn* pRgn);  
CGdiObject* SelectObject(CGdiObject* pObject);
```  
  
### <a name="parameters"></a>Parámetros  
 *pPen*  
 Un puntero a un [CPen](../../mfc/reference/cpen-class.md) objeto que va a seleccionar.  
  
 `pBrush`  
 Un puntero a un [CBrush](../../mfc/reference/cbrush-class.md) objeto que va a seleccionar.  
  
 `pFont`  
 Un puntero a un [CFont](../../mfc/reference/cfont-class.md) objeto que va a seleccionar.  
  
 `pBitmap`  
 Un puntero a un [CBitmap](../../mfc/reference/cbitmap-class.md) objeto que va a seleccionar.  
  
 `pRgn`  
 Un puntero a un [CRgn](../../mfc/reference/crgn-class.md) objeto que va a seleccionar.  
  
 `pObject`  
 Un puntero a un [CGdiObject](../../mfc/reference/cgdiobject-class.md) objeto que va a seleccionar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al objeto que se va a reemplazar. Se trata de un puntero a un objeto de una de las clases derivadas de `CGdiObject`, como `CPen`, según la versión de la función que se utiliza. El valor devuelto es **NULL** si se produce un error. Esta función puede devolver un puntero a un objeto temporal. Este objeto temporal sólo es válido durante el procesamiento de un mensaje de Windows. Para obtener más información, consulta `CGdiObject::FromHandle`.  
  
 La versión de la función miembro que toma un parámetro de región realiza la misma tarea que el `SelectClipRgn` función miembro. El valor devuelto puede ser cualquiera de las siguientes acciones:  
  
- **COMPLEXREGION** nueva región de recorte tiene bordes se superponen.  
  
- **ERROR** contexto de dispositivo o la región no es válido.  
  
- **NULLREGION** nueva región de recorte está vacía.  
  
- **SIMPLEREGION** nueva región de recorte no tiene bordes superpuestos.  
  
### <a name="remarks"></a>Comentarios  
 Clase `CDC` proporciona cinco versiones especializadas para determinados tipos de objetos GDI, incluidos lápices, pinceles, fuentes, mapas de bits y regiones. El objeto recién seleccionado reemplaza el objeto anterior del mismo tipo. Por ejemplo, si `pObject` de la versión general de `SelectObject` apunta a un [CPen](../../mfc/reference/cpen-class.md) de objeto, la función sustituye el lápiz actual con el lápiz especificado por `pObject`.  
  
 Una aplicación sólo podrá seleccionar un mapa de bits en contextos de dispositivo de memoria y en el contexto de dispositivo de solo memoria a la vez. El formato del mapa de bits debe ser compatible con el contexto de dispositivo o monocromático Si no lo está, `SelectObject` devuelve un error.  
  
 Windows 3.1 y versiones posteriores, el `SelectObject` función devuelve el mismo valor si se utiliza en un metarchivo o no. En versiones anteriores de Windows, `SelectObject` devuelve un valor distinto de cero para el éxito y 0 para el error cuando se utiliza en un metarchivo.  
  
##  <a name="a-nameselectpalettea--cdcselectpalette"></a><a name="selectpalette"></a>CDC::SelectPalette  
 Selecciona la paleta lógica especificada por `pPalette` como el objeto de la paleta seleccionada del contexto de dispositivo.  
  
```  
CPalette* SelectPalette(
    CPalette* pPalette,  
    BOOL bForceBackground);
```  
  
### <a name="parameters"></a>Parámetros  
 `pPalette`  
 Identifica la paleta lógica que va a seleccionar. Esta paleta ya debe haber sido creada con el `CPalette` función miembro [CreatePalette](../../mfc/reference/cpalette-class.md#createpalette).  
  
 `bForceBackground`  
 Especifica si se fuerza la paleta lógica sea una paleta de fondo. Si `bForceBackground` es distinto de cero, la paleta seleccionada es siempre una paleta de fondo, independientemente de si la ventana tiene el foco de entrada. Si `bForceBackground` es 0 y el contexto de dispositivo está conectado a una ventana, la paleta lógica es una paleta de primer plano cuando la ventana tiene el foco de entrada.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CPalette` objeto que identifica la paleta lógica reemplazada por la paleta especificada por `pPalette`. Es **NULL** si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 La nueva paleta se convierte en el objeto de paleta usa GDI para colores de control que se muestran en el contexto de dispositivo y reemplaza la paleta anterior.  
  
 Una aplicación puede seleccionar una paleta lógica en más de un contexto de dispositivo. Sin embargo, los cambios en una paleta lógica afectará a todos los contextos de dispositivo para el que está seleccionada. Si una aplicación selecciona una paleta en más de un contexto de dispositivo, los contextos de dispositivo deben pertenecer al mismo dispositivo físico.  
  
##  <a name="a-nameselectstockobjecta--cdcselectstockobject"></a><a name="selectstockobject"></a>CDC::SelectStockObject  
 Selecciona un [CGdiObject](../../mfc/reference/cgdiobject-class.md) objeto que corresponde a uno de los lápices de acciones predefinidas, pinceles o las fuentes.  
  
```  
virtual CGdiObject* SelectStockObject(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Especifica el tipo de objeto de acción deseada. Puede ser uno de los siguientes valores:  
  
- **BLACK_BRUSH** pincel en negro.  
  
- **DKGRAY_BRUSH** pincel gris oscuro.  
  
- **GRAY_BRUSH** pincel de color gris.  
  
- **HOLLOW_BRUSH** hueco pincel.  
  
- **LTGRAY_BRUSH** poca pincel gris.  
  
- **NULL_BRUSH** Null pincel.  
  
- **WHITE_BRUSH** pincel en blanco.  
  
- **BLACK_PEN** pluma de color negro.  
  
- **NULL_PEN** lápiz es Null.  
  
- **WHITE_PEN** pluma blanco.  
  
- **ANSI_FIXED_FONT** fuente de sistema fijo de ANSI.  
  
- **ANSI_VAR_FONT** fuente de sistema variable ANSI.  
  
- **DEVICE_DEFAULT_FONT** fuente dependiente del dispositivo.  
  
- **OEM_FIXED_FONT** fuente fija de OEM dependiente.  
  
- **SYSTEM_FONT** la fuente del sistema. De forma predeterminada, Windows utiliza la fuente del sistema para dibujar los menús, controles de cuadro de diálogo y otro texto. Es mejor, sin embargo, no se basan en SYSTEM_FONT para obtener la fuente utilizada por las ventanas y cuadros de diálogo. En su lugar, use la `SystemParametersInfo` función con el parámetro SPI_GETNONCLIENTMETRICS para recuperar la fuente actual. `SystemParametersInfo`Tenga en cuenta que el tema actual y proporciona información de fuentes para títulos, menús y cuadros de diálogo de mensaje.  
  
- **SYSTEM_FIXED_FONT** la fuente de ancho fijo que se usa en Windows antes de la versión 3.0. Este objeto está disponible para compatibilidad con versiones anteriores de Windows.  
  
- **DEFAULT_PALETTE** paleta de colores predeterminada. Esta paleta consta de los 20 colores estáticos en la paleta del sistema.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `CGdiObject` objeto que se ha reemplazado si la función se realiza correctamente. Es el objeto real al que señala un [CPen](../../mfc/reference/cpen-class.md), [CBrush](../../mfc/reference/cbrush-class.md), o [CFont](../../mfc/reference/cfont-class.md) objeto. Si la llamada se realiza correctamente, el valor devuelto es **NULL**.  
  
##  <a name="a-namesetabortproca--cdcsetabortproc"></a><a name="setabortproc"></a>CDC:: SETABORTPROC  
 Instala el procedimiento de anulación para el trabajo de impresión.  
  
```  
int SetAbortProc(BOOL (CALLBACK* lpfn)(HDC, int));
```  
  
### <a name="parameters"></a>Parámetros  
 `lpfn`  
 Puntero a la función de anulación para instalar como procedimiento de anulación. Para obtener más información acerca de la función de devolución de llamada, consulte [función de devolución de llamada para CDC:: SETABORTPROC](../../mfc/reference/callback-function-for-cdc-setabortproc.md).  
  
### <a name="return-value"></a>Valor devuelto  
 Especifica el resultado de la `SetAbortProc` (función). Algunos de los valores siguientes son más probables que otros, pero todos son posibles.  
  
- **SP_ERROR** error General.  
  
- **SP_OUTOFDISK** no hay suficiente espacio en disco está disponible actualmente para la puesta en y no hay más espacio volverá a estar disponible.  
  
- **SP_OUTOFMEMORY** no hay suficiente memoria disponible para la cola de impresión.  
  
- **SP_USERABORT** usuario finalizó el trabajo a través del Administrador de impresión.  
  
### <a name="remarks"></a>Comentarios  
 Si una aplicación es permitir que el trabajo de impresión se canceló durante la puesta en cola, debe establecer la función de anulación antes de inicia el trabajo de impresión con la [StartDoc](#startdoc) función miembro. El Administrador de impresión llama a la función de anulación durante la puesta en cola para permitir que la aplicación para cancelar el trabajo de impresión o para procesar las condiciones de falta de espacio en disco. Si no se establece ninguna función de anulación, se producirá un error en el trabajo de impresión si no hay suficiente espacio en disco para la cola de impresión.  
  
 Tenga en cuenta que las características de Microsoft Visual C++ simplifican la creación de la función de devolución de llamada pasada a `SetAbortProc`. Pasa la dirección a la `EnumObjects` función miembro es un puntero a una función exportada con **__declspec (dllexport)** y con el `__stdcall` convención de llamada.  
  
 También es necesario exportar el nombre de función en una **exportaciones** instrucción en el archivo de definición de módulo de la aplicación. Puede usar el **exportar** función modificador, como en  
  
 **EXPORTACIÓN de devolución de llamada BOOL** AFunction ( **HDC**, `int` **);**  
  
 Para hacer que el compilador emita el registro de exportación adecuados para la exportación por su nombre sin alias. Esto funciona para la mayoría de las necesidades. En algunos casos especiales, como exportar una función por ordinal o alias de la exportación, deberá utilizar un **exportaciones** instrucción en un archivo de definición de módulo.  
  
 Interfaces de devolución de llamada registro ahora tienen seguridad de tipos (debe pasar un puntero a función que señala el tipo correcto de la función de devolución de llamada específica).  
  
 Tenga en cuenta que todas las funciones de devolución de llamada deben capturar las excepciones que Microsoft Foundation antes de volver a Windows, puesto que no se producirán excepciones en los límites de la devolución de llamada. Para obtener más información sobre las excepciones, vea el artículo [excepciones](../../mfc/exception-handling-in-mfc.md).  
  
##  <a name="a-namesetarcdirectiona--cdcsetarcdirection"></a><a name="setarcdirection"></a>CDC::SetArcDirection  
 Establece la dirección que se utilizará para funciones de arco y el rectángulo de dibujo.  
  
```  
int SetArcDirection(int nArcDirection);
```  
  
### <a name="parameters"></a>Parámetros  
 *nArcDirection*  
 Especifica la nueva dirección del arco. Este parámetro puede ser cualquiera de los siguientes valores:  
  
- **AD_COUNTERCLOCKWISE** cifras dibujadas a la izquierda.  
  
- **AD_CLOCKWISE** cifras dibujadas hacia la derecha.  
  
### <a name="return-value"></a>Valor devuelto  
 Especifica la dirección de arco anterior, si es correcto; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La dirección predeterminada es a la izquierda. El `SetArcDirection` función especifica la dirección en la que lo siguiente funciones de dibujo:  
  
|Arco|Circular|  
|---------|---------|  
|`ArcTo`|**Rectángulo**|  
|`Chord`|`RoundRect`|  
|**Elipse**||  
  
##  <a name="a-namesetattribdca--cdcsetattribdc"></a><a name="setattribdc"></a>CDC::SetAttribDC  
 Llame a esta función para establecer el contexto de dispositivo de atributo `m_hAttribDC`.  
  
```  
virtual void SetAttribDC(HDC hDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `hDC`  
 Un contexto de dispositivo de Windows.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro no asocia el contexto de dispositivo para la `CDC` objeto. Solo el contexto de dispositivo de salida se adjunta a un `CDC` objeto.  
  
##  <a name="a-namesetbkcolora--cdcsetbkcolor"></a><a name="setbkcolor"></a>CDC::SetBkColor  
 Establece el color de fondo actual con el color especificado.  
  
```  
virtual COLORREF SetBkColor(COLORREF crColor);
```  
  
### <a name="parameters"></a>Parámetros  
 `crColor`  
 Especifica el nuevo color de fondo.  
  
### <a name="return-value"></a>Valor devuelto  
 El color de fondo anterior como un valor de color RGB. Si se produce un error, el valor devuelto es 0 x 80000000.  
  
### <a name="remarks"></a>Comentarios  
 Si el modo de segundo plano es **OPACO**, el sistema utiliza el color de fondo para rellenar los huecos en líneas con estilo, los espacios entre las líneas de sombreado de pinceles y el fondo de las celdas de caracteres. El sistema también utiliza el color de fondo al convertir mapas de bits entre color y contextos de dispositivo monocromático.  
  
 Si el dispositivo no puede mostrar el color especificado, el sistema establece el color de fondo al color físico más cercano.  
  
##  <a name="a-namesetbkmodea--cdcsetbkmode"></a><a name="setbkmode"></a>CDC::SetBkMode  
 Establece el modo de segundo plano.  
  
```  
int SetBkMode(int nBkMode);
```  
  
### <a name="parameters"></a>Parámetros  
 *nBkMode*  
 Especifica el modo de establecerse. Este parámetro puede ser cualquiera de los siguientes valores:  
  
- **OPACO** fondo se llena con el color de fondo actual antes del texto, el pincel sombreada, o se dibuja el lápiz. Este es el modo de fondo predeterminado.  
  
- **TRANSPARENTE** fondo no se modifica antes de dibujar.  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de segundo plano anterior.  
  
### <a name="remarks"></a>Comentarios  
 El modo de segundo plano define si el sistema quita los colores de fondo existentes en la superficie de dibujo antes de dibujar el texto, pinceles de trama o cualquier estilo de lápiz que no es una línea sólida.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CWnd::OnCtlColor](../../mfc/reference/cwnd-class.md#onctlcolor).  
  
##  <a name="a-namesetboundsrecta--cdcsetboundsrect"></a><a name="setboundsrect"></a>CDC::SetBoundsRect  
 Controla la acumulación de información del rectángulo delimitador para el contexto de dispositivo especificado.  
  
```  
UINT SetBoundsRect(
    LPCRECT lpRectBounds,  
    UINT flags);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRectBounds`  
 Apunta a un `RECT` estructura o `CRect` objeto que se usa para establecer el rectángulo delimitador. Dimensiones del rectángulo se proporcionan en coordenadas lógicas. Este parámetro puede ser **NULL**.  
  
 `flags`  
 Especifica cómo se combinan el nuevo rectángulo con el rectángulo acumulado. Este parámetro puede ser una combinación de los siguientes valores:  
  
- **DCB_ACCUMULATE** agregue el rectángulo especificado por `lpRectBounds` al rectángulo delimitador (mediante una operación de unión de rectángulo).  
  
- **DCB_DISABLE** desactivar la acumulación de límites.  
  
- **DCB_ENABLE** activar acumulación de límites. (El valor predeterminado de acumulación de límites está deshabilitado).  
  
### <a name="return-value"></a>Valor devuelto  
 El estado actual del rectángulo, si la función se realiza correctamente. Como `flags`, el valor devuelto puede ser una combinación de **DCB_** valores:  
  
- **DCB_ACCUMULATE** el rectángulo delimitador no está vacío. Este valor siempre se establecerá.  
  
- **DCB_DISABLE** acumulación límites está desactivada.  
  
- **DCB_ENABLE** acumulación límites está activado.  
  
### <a name="remarks"></a>Comentarios  
 Windows puede mantener un rectángulo delimitador para todas las operaciones de dibujos. Este rectángulo se puede consultar y restablecer la aplicación. Los límites de dibujos son útiles para invalidar las memorias caché de mapa de bits.  
  
##  <a name="a-namesetbrushorga--cdcsetbrushorg"></a><a name="setbrushorg"></a>CDC::SetBrushOrg  
 Especifica el origen que GDI asignará al pincel siguiente que selecciona la aplicación en el contexto de dispositivo.  
  
```  
CPoint SetBrushOrg(
    int x,  
    int y);  
  
CPoint SetBrushOrg(POINT point);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada x (en unidades de dispositivo) del nuevo origen. Este valor debe ser en el intervalo 0 – 7.  
  
 *y*  
 Especifica la coordenada y (en unidades de dispositivo) del nuevo origen. Este valor debe ser en el intervalo 0 – 7.  
  
 `point`  
 Especifica las coordenadas x e y del nuevo origen. Cada valor debe ser en el intervalo 0 – 7. Puede pasarse un **punto** estructura o un `CPoint` objeto para este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 El origen anterior del pincel en unidades del dispositivo.  
  
### <a name="remarks"></a>Comentarios  
 Coordina el valor predeterminado para el origen del pincel son (0, 0). Para modificar el origen de un pincel, llame a la `UnrealizeObject` funcionar para la `CBrush` objeto, llame a `SetBrushOrg`y, a continuación, llame a la `SelectObject` función miembro para seleccionar el pincel en el contexto de dispositivo.  
  
 No utilice `SetBrushOrg` con material `CBrush` objetos.  
  
##  <a name="a-namesetcoloradjustmenta--cdcsetcoloradjustment"></a><a name="setcoloradjustment"></a>CDC::SetColorAdjustment  
 Establece los valores de ajuste de color para el contexto de dispositivo con los valores especificados.  
  
```  
BOOL SetColorAdjustment(const COLORADJUSTMENT* lpColorAdjust);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpColorAdjust`  
 Apunta a un [COLORADJUSTMENT](../../mfc/reference/coloradjustment-structure.md) estructura de datos que contiene los valores de ajuste de color.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Los valores de ajuste de color se utilizan para ajustar el color de la entrada del mapa de bits de origen para las llamadas a la `CDC::StretchBlt` función miembro cuando **SEMITONOS** modo está establecido.  
  
##  <a name="a-namesetdcbrushcolora--cdcsetdcbrushcolor"></a><a name="setdcbrushcolor"></a>CDC::SetDCBrushColor  
 Establece el color de pincel de dispositivo (DC) del contexto actual en el valor de color especificado.  
  
```  
COLORREF SetDCBrushColor(COLORREF crColor);
```  
  
### <a name="parameters"></a>Parámetros  
 `crColor`  
 Especifica el nuevo color de pincel.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto especifica el color de pincel DC anterior como un `COLORREF` valor.  
  
 Si se produce un error en la función, el valor devuelto es `CLR_INVALID`.  
  
### <a name="remarks"></a>Comentarios  
 Este método emula la funcionalidad de la función [SetDCBrushColor](http://msdn.microsoft.com/library/windows/desktop/dd162969), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namesetdcpencolora--cdcsetdcpencolor"></a><a name="setdcpencolor"></a>CDC::SetDCPenColor  
 Establece el color del lápiz de contexto de dispositivo actual en el valor de color especificado.  
  
```  
COLORREF SetDCPenColor(COLORREF crColor);
```  
  
### <a name="parameters"></a>Parámetros  
 `crColor`  
 Especifica el nuevo color del lápiz.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro usa la función de Win32 [SetDCPenColor](http://msdn.microsoft.com/library/windows/desktop/dd162970), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namesetgraphicsmodea--cdcsetgraphicsmode"></a><a name="setgraphicsmode"></a>CDC::SetGraphicsMode  
 Establece el modo de gráficos para el contexto de dispositivo especificado.  
  
```  
int SetGraphicsMode(int iMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `iMode`  
 Especifica el modo de gráficos. Para obtener una lista de los valores de este parámetro puede tomar, vea [SetGraphicsMode](http://msdn.microsoft.com/library/windows/desktop/dd162977).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el modo gráfico anterior en caso de éxito.  
  
 Devuelve 0 en caso de error. Para obtener información de error extendida, llame a [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Comentarios  
 Este método ajusta la función GDI de Windows [SetGraphicsMode](http://msdn.microsoft.com/library/windows/desktop/dd162977).  
  
##  <a name="a-namesetlayouta--cdcsetlayout"></a><a name="setlayout"></a>CDC::SetLayout  
 Llame a esta función miembro para cambiar el diseño del texto y gráficos para un contexto de dispositivo a la derecha a izquierda, el diseño estándar para las referencias culturales como el árabe y hebreo.  
  
```  
DWORD SetLayout(DWORD dwLayout);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwLayout`  
 Indicadores de control de diseño de contexto de dispositivo y el mapa de bits. Puede ser una combinación de los valores siguientes.  
  
|Valor|Significado|  
|-----------|-------------|  
|LAYOUT_BITMAPORIENTATIONPRESERVED|Deshabilita cualquier reflexión para las llamadas a [CDC::BitBlt](#bitblt) y [CDC::StretchBlt](#stretchblt).|  
|LAYOUT_RTL|Establece el diseño horizontal predeterminado de derecha a izquierda.|  
|LAYOUT_LTR|Establece el diseño predeterminado para ser de izquierda a derecha.|  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el diseño anterior del contexto de dispositivo.  
  
 Si no lo consigue, **GDI_ERROR**. Para obtener información de error extendida, llame a [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, no se llama **SetLayout** de una ventana. En su lugar, puede controlar el diseño de derecha a izquierda en una ventana estableciendo la [estilos de ventana extendidos](../../mfc/reference/extended-window-styles.md) como **WS_EX_RTLREADING**. Un contexto de dispositivo, como una impresora o un metarchivo no hereda este diseño. La única manera de establecer el contexto de dispositivo para un diseño de derecha a izquierda es mediante una llamada a **SetLayout**.  
  
 Si se llama a **SetLayout (LAYOUT_RTL** ), **SetLayout** cambia automáticamente el modo de asignación a `MM_ISOTROPIC`. Como resultado, una llamada subsiguiente a [GetMapMode](#getmapmode) devolverá **MM_ISOTROPIC** en lugar de `MM_TEXT`.  
  
 En algunos casos, como con muchos de los mapas de bits, puede conservar el diseño de izquierda a derecha. En estos casos, se presenta la imagen mediante una llamada a `BitBlt` o `StretchBlt`, a continuación, establezca el indicador de control de mapa de bits para `dwLayout` a **LAYOUT_BITMAPORIENTATIONPRESERVED**.  
  
 Una vez que cambie el diseño con el **LAYOUT_RTL** marca marcadores que especifican normalmente derecha o izquierda se invierten. Para evitar confusiones, puede definir nombres alternativos para los indicadores estándares. Para obtener una lista de nombres de marca alternativas sugeridas, vea [SetLayout](http://msdn.microsoft.com/library/windows/desktop/dd162979) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namesetmapmodea--cdcsetmapmode"></a><a name="setmapmode"></a>CDC::SetMapMode  
 Establece el modo de asignación.  
  
```  
virtual int SetMapMode(int nMapMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `nMapMode`  
 Especifica el nuevo modo de asignación. Puede ser cualquiera de los siguientes valores:  
  
- `MM_ANISOTROPIC`Las unidades lógicas se convierten en unidades arbitrarias con ejes de escalados de forma arbitraria. Establecer el modo de asignación en `MM_ANISOTROPIC` no cambia la configuración actual de la ventana o área de visualización. Para cambiar las unidades, orientación y ajuste de escala, llame a la [SetWindowExt](#setwindowext) y [SetViewportExt](#setviewportext) funciones miembro.  
  
- `MM_HIENGLISH`Cada unidad lógica se convierte en 0,001 pulgadas. Positivo x situada a la derecha; positivo y está activo.  
  
- `MM_HIMETRIC`Cada unidad lógica se convierte en 0,01 milímetros. Positivo x situada a la derecha; positivo y está activo.  
  
- `MM_ISOTROPIC`Las unidades lógicas se convierten en unidades arbitrarias con igualmente los ejes de escala; es decir, 1 unidad en el eje x es igual a 1 unidad en el eje y. Utilice la `SetWindowExt` y `SetViewportExt` funciones miembro para especificar las unidades deseadas y la orientación de los ejes. GDI realiza ajustes según sea necesario para asegurarse de que x e y unidades siguen siendo el mismo tamaño.  
  
- `MM_LOENGLISH`Cada unidad lógica se convierte en 0,01 pulgadas. Positivo x situada a la derecha; positivo y está activo.  
  
- `MM_LOMETRIC`Cada unidad lógica se convierte en 0,1 milímetros. Positivo x situada a la derecha; positivo y está activo.  
  
- `MM_TEXT`Cada unidad lógica se convierte en píxeles del 1 dispositivo. Positivo x situada a la derecha; positivo y está inactivo.  
  
- `MM_TWIPS`Cada unidad lógica se convierte en 1/20 de un punto. (Como un punto es 1/72 de pulgada, un twip es 1/1440 de pulgada). Positivo x situada a la derecha; positivo y está activo.  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de asignación anterior.  
  
### <a name="remarks"></a>Comentarios  
 El modo de asignación define la unidad de medida utilizada para convertir las unidades lógicas en unidades del dispositivo; También define la orientación de los dispositivos ejes x e. GDI utiliza el modo de asignación para convertir de coordenadas lógicas en las coordenadas de dispositivo adecuado. El `MM_TEXT` modo permite que las aplicaciones funcionan en píxeles del dispositivo, donde 1 unidad es igual a 1 píxel. El tamaño físico de un píxel varía de un dispositivo a otro.  
  
 El `MM_HIENGLISH`, `MM_HIMETRIC`, `MM_LOENGLISH`, `MM_LOMETRIC`, y `MM_TWIPS` modos son útiles para las aplicaciones que se deben dibujar en unidades significativas físicamente (por ejemplo, pulgadas o milímetros). El `MM_ISOTROPIC` modo garantiza una proporción 1:1, lo que resulta útil cuando es importante conservar la forma exacta de una imagen. El `MM_ANISOTROPIC` modo permite las coordenadas x e y para ajustarse de forma independiente.  
  
> [!NOTE]
>  Si se llama a [SetLayout](#setlayout) para cambiar el controlador de dominio (contexto de dispositivo) al diseño de derecha a izquierda, **SetLayout** cambia automáticamente el modo de asignación a `MM_ISOTROPIC`.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc).  
  
##  <a name="a-namesetmapperflagsa--cdcsetmapperflags"></a><a name="setmapperflags"></a>CDC::SetMapperFlags  
 Cambia el método utilizado por el asignador de fuentes cuando convierte una fuente lógica a una fuente física.  
  
```  
DWORD SetMapperFlags(DWORD dwFlag);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwFlag`  
 Especifica si el asignador de fuentes intenta hacer coincidir alto del aspecto de la fuente y el ancho en el dispositivo. Cuando este valor es **ASPECT_FILTERING**, el asignador selecciona sólo las fuentes cuyo aspecto de x y y aspecto coinciden exactamente con los del dispositivo especificado.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor anterior de la marca de asignador de fuentes.  
  
### <a name="remarks"></a>Comentarios  
 Una aplicación puede utilizar `SetMapperFlags` para hacer que el asignador de fuentes intentar elegir sólo una fuente física que coincida exactamente con la relación de aspecto del dispositivo especificado.  
  
 Puede usar una aplicación que usa sólo las fuentes de trama del `SetMapperFlags` función para asegurarse de que la fuente seleccionada por el asignador de fuentes es atractivo y legible en el dispositivo especificado. Las aplicaciones que utilicen escalables () fuentes TrueType normalmente no usan `SetMapperFlags`.  
  
 Si no hay ninguna fuente física tiene una relación de aspecto que coincida con la especificación de la fuente lógica, GDI elige una nueva relación de aspecto y selecciona una fuente que coincide con esta nueva relación de aspecto.  
  
##  <a name="a-namesetmiterlimita--cdcsetmiterlimit"></a><a name="setmiterlimit"></a>CDC::SetMiterLimit  
 Establece el límite para la longitud de uniones angulares para el contexto de dispositivo.  
  
```  
BOOL SetMiterLimit(float fMiterLimit);
```  
  
### <a name="parameters"></a>Parámetros  
 *fMiterLimit*  
 Especifica el nuevo límite angular para el contexto de dispositivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 La longitud del ángulo se define como la distancia desde la intersección de las paredes de la línea en el interior de la unión y la intersección de las paredes de la línea en la parte exterior de la combinación. El límite del ángulo es la máxima proporción permitida entre la longitud del ángulo con el ancho de línea. El límite en ángulo predeterminado es 10.0.  
  
##  <a name="a-namesetoutputdca--cdcsetoutputdc"></a><a name="setoutputdc"></a>CDC::SetOutputDC  
 Llame a esta función miembro para establecer el contexto de dispositivo de salida, `m_hDC`.  
  
```  
virtual void SetOutputDC(HDC hDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `hDC`  
 Un contexto de dispositivo de Windows.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro sólo puede llamarse cuando un contexto de dispositivo no se ha asociado a la `CDC` objeto. Esta función miembro establece `m_hDC` pero no se asocia el contexto de dispositivo para la `CDC` objeto.  
  
##  <a name="a-namesetpixela--cdcsetpixel"></a><a name="setpixel"></a>CDC::SetPixel  
 Establece el píxel en el punto especificado para la aproximación más cercana del color especificado por `crColor`.  
  
```  
COLORREF SetPixel(
    int x,  
    int y,  
    COLORREF crColor);

 
COLORREF SetPixel(
    POINT point,  
    COLORREF crColor);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada x lógica del punto a establecerse.  
  
 *y*  
 Especifica la coordenada y lógica del punto a establecerse.  
  
 `crColor`  
 Un **COLORREF** valor RGB que especifica el color utilizado para pintar el punto. Consulte [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una descripción de este valor.  
  
 `point`  
 Especifica las coordenadas x e y lógica del punto a establecerse. Puede pasarse un **punto** estructura o un `CPoint` objeto para este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor RGB del color que realmente se pinta el punto. Este valor puede ser diferente del especificado por `crColor` si se usa una aproximación de ese color. Si se produce un error en la función (si el punto está fuera de la región de recorte), el valor devuelto será –&1;.  
  
### <a name="remarks"></a>Comentarios  
 El punto debe estar en la región de recorte. Si el punto no está en la región de recorte, la función no hace nada.  
  
 No todos los dispositivos admiten la función `SetPixel`. Para determinar si un dispositivo admite `SetPixel`, llame a la `GetDeviceCaps` función miembro con el **RASTERCAPS** de índice y comprobar el valor devuelto para la **RC_BITBLT** marca.  
  
##  <a name="a-namesetpixelva--cdcsetpixelv"></a><a name="setpixelv"></a>CDC::SetPixelV  
 Establece el píxel en las coordenadas especificadas para la aproximación más cercana del color especificado.  
  
```  
BOOL SetPixelV(
    int x,  
    int y,  
    COLORREF crColor);

 
BOOL SetPixelV(
    POINT point,  
    COLORREF crColor);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada x, en unidades lógicas, del punto a establecerse.  
  
 *y*  
 Especifica la coordenada y, en unidades lógicas, del punto a establecerse.  
  
 `crColor`  
 Especifica el color que se utiliza para pintar el punto.  
  
 `point`  
 Especifica las coordenadas x e y lógica del punto a establecerse. Puede pasarse un [punto](../../mfc/reference/point-structure1.md) estructura de datos o un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto para este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El punto debe estar en la región de recorte y la parte visible de la superficie del dispositivo. No todos los dispositivos admiten la función de miembro. Para obtener más información, consulte el **RC_BITBLT** capacidad en el `CDC::GetDeviceCaps` función miembro. `SetPixelV`es más rápido que `SetPixel` porque no se necesita devolver el valor de color del punto dibujado en realidad.  
  
##  <a name="a-namesetpolyfillmodea--cdcsetpolyfillmode"></a><a name="setpolyfillmode"></a>CDC::SetPolyFillMode  
 Establece el modo de relleno de polígono.  
  
```  
int SetPolyFillMode(int nPolyFillMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `nPolyFillMode`  
 Especifica el nuevo modo de relleno. Este valor puede ser **alternativo** o **DEVANADO**. El modo predeterminado establecido en Windows es **alternativo**.  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de relleno anterior, si es correcto; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el modo de relleno de polígono es **alternativo**, el sistema rellena el área entre los lados de un polígono pares e impares en cada línea de exploración. Es decir, el sistema rellena el área entre la primera y segunda parte, entre el lado tercero y cuarto y así sucesivamente. Este modo es el valor predeterminado.  
  
 Cuando el modo de relleno de polígono es **DEVANADO**, el sistema usa la dirección en la que se dibuja una figura para determinar si se debe rellenar un área. Cada segmento de línea de un polígono se dibuja en un hacia la derecha o una dirección a la izquierda. Siempre que una línea imaginaria de un área cerrada al exterior de una figura pasa a través de un segmento de línea de las agujas del reloj, se incrementa un recuento. Cuando la línea pasa a través de un segmento de línea a la izquierda, el recuento es reducido. El área se rellena si el recuento es distinto de cero cuando llega a la línea de la parte exterior de la figura.  
  
##  <a name="a-namesetrop2a--cdcsetrop2"></a><a name="setrop2"></a>CDC::SetROP2  
 Establece el modo de dibujo actual.  
  
```  
int SetROP2(int nDrawMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `nDrawMode`  
 Especifica el modo de dibujo nuevo. Puede ser cualquiera de los siguientes valores:  
  
- **R2_BLACK** píxeles siempre es negro.  
  
- **R2_WHITE** píxeles siempre es blanco.  
  
- **R2_NOP** píxel permanece sin cambios.  
  
- **R2_NOT** píxel es el inverso del color de pantalla.  
  
- **R2_COPYPEN** píxel es el color del lápiz.  
  
- **R2_NOTCOPYPEN** píxel es el inverso del color de la pluma.  
  
- **R2_MERGEPENNOT** píxel es una combinación del color del lápiz y el inverso del color de pantalla (final del píxel = (no pantalla píxel) o lápiz).  
  
- **R2_MASKPENNOT** píxel es una combinación de los colores comunes a la pluma y el inverso de la pantalla (final del píxel = (no píxel de la pantalla) y lápiz).  
  
- **R2_MERGENOTPEN** píxel es una combinación de colores de la pantalla y el inverso del color de lápiz (final del píxel = (no lápiz) o una pantalla de píxeles).  
  
- **R2_MASKNOTPEN** píxel es una combinación de los colores comunes a la pantalla y el inverso del lápiz (final del píxel = (no lápiz) y píxeles de pantalla).  
  
- **R2_MERGEPEN** píxel es una combinación de color de la pluma y el color de pantalla (final del píxel = píxel de pantalla o de lápiz).  
  
- **R2_NOTMERGEPEN** píxel es el inverso de la **R2_MERGEPEN** color (final del píxel = no (pen píxeles de pantalla de OR)).  
  
- **R2_MASKPEN** píxel es una combinación de los colores comunes a la pluma y la pantalla (final del píxel = lápiz y píxeles de pantalla).  
  
- **R2_NOTMASKPEN** píxel es el inverso de la **R2_MASKPEN** color (final del píxel = no (pen píxel de la pantalla y)).  
  
- **R2_XORPEN** píxel es una combinación de los colores que están en el lápiz o en la pantalla, pero no en ambos (final del píxel = píxel de pantalla de lápiz XOR).  
  
- **R2_NOTXORPEN** píxel es el inverso de la **R2_XORPEN** color (final del píxel = no (píxel de pantalla de lápiz XOR)).  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de dibujo anterior.  
  
 Puede ser cualquiera de los valores especificados en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 El modo de dibujo especifica cómo se combinan los colores del lápiz y el interior de los objetos rellenos con el color ya en la superficie de presentación.  
  
 Es el modo de dibujo para dispositivos de trama. no se aplica a dispositivos de vector. Modos de dibujo son códigos de operación de trama binario que representa todas las posibles combinaciones de dos variables, mediante los operadores binarios AND, OR y XOR (OR exclusivo) y la operación unaria no booleanas.  
  
##  <a name="a-namesetstretchbltmodea--cdcsetstretchbltmode"></a><a name="setstretchbltmode"></a>CDC::SetStretchBltMode  
 Establece el modo de ajuste de mapa de bits para el `StretchBlt` función miembro.  
  
```  
int SetStretchBltMode(int nStretchMode);
```  
  
### <a name="parameters"></a>Parámetros  
 *nStretchMode*  
 Especifica el modo de ajuste. Puede ser cualquiera de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**BLACKONWHITE**|Realiza una operación Boolean y con los valores de color para los píxeles se eliminaron y existentes. Si el mapa de bits es un mapa de bits monocromo, este modo conserva píxeles negros a costa de píxeles blancos.|  
|**COLORONCOLOR**|Elimina los píxeles. Este modo elimina se eliminaron todas las líneas de píxeles sin intentar conservar su información.|  
|**MEDIOS TONOS**|Asigna los píxeles del rectángulo de origen en bloques de píxeles en el rectángulo de destino. El color medio sobre el bloque de destino de píxeles aproxima el color de los píxeles de origen.|  
||Después de establecer el **SEMITONOS** ajuste modo, una aplicación debe llamar a la función de Win32 [SetBrushOrgEx](http://msdn.microsoft.com/library/windows/desktop/dd162967) para establecer el origen del pincel. Si se produce un error al hacerlo, se produce el error de alineación de pincel.|  
|**STRETCH_ANDSCANS**|**Windows 95 ó 98**: igual que **BLACKONWHITE**|  
|**STRETCH_DELETESCANS**|**Windows 95 ó 98**: igual que **COLORONCOLOR**|  
|**STRETCH_HALFTONE**|**Windows 95 ó 98**: igual que **SEMITONOS**.|  
|**STRETCH_ORSCANS**|**Windows 95 ó 98**: igual que **WHITEONBLACK**|  
|**WHITEONBLACK**|Realiza una operación Boolean o con los valores de color para los píxeles se eliminaron y existentes. Si el mapa de bits es un mapa de bits monocromo, este modo conserva píxeles blancos a costa de píxeles negros.|  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de ajuste anterior. Puede ser **STRETCH_ANDSCANS**, **STRETCH_DELETESCANS**, o **STRETCH_ORSCANS**.  
  
### <a name="remarks"></a>Comentarios  
 El modo de ajuste de mapa de bits define cómo se quita la información de mapas de bits que se comprimen mediante la función.  
  
 El **BLACKONWHITE** ( **STRETCH_ANDSCANS**) y **WHITEONBLACK** ( **STRETCH_ORSCANS**) modos normalmente se utilizan para conservar los píxeles de primer plano de los mapas de bits monocromo. El **COLORONCOLOR** ( **STRETCH_DELETESCANS**) modo se suele usar para conservar el color en los mapas de bits de color.  
  
 El **SEMITONOS** modo requiere más procesamiento de la imagen de origen que los otros tres modos; es más lenta que los demás, pero genera imágenes de alta calidad. Tenga en cuenta también que **SetBrushOrgEx** debe llamarse después de establecer el **SEMITONOS** modo para evitar el error de alineación de pincel.  
  
 Modos de ajuste adicionales también pueden estar disponibles dependiendo de las capacidades del controlador del dispositivo.  
  
##  <a name="a-namesettextaligna--cdcsettextalign"></a><a name="settextalign"></a>CDC::SetTextAlign  
 Establece las marcas de alineación de texto.  
  
```  
UINT SetTextAlign(UINT nFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 `nFlags`  
 Especifica las marcas de alineación de texto. Los indicadores especifican la relación entre un punto y un rectángulo que delimita el texto. Puede ser el punto de la posición actual o coordenadas especificadas por una función de salida de texto. El rectángulo que delimita el texto está definido por las celdas de carácter adyacentes en la cadena de texto. El `nFlags` del parámetro puede ser uno o más indicadores de las tres categorías siguientes. Elija solo una marca en cada categoría. La primera categoría afecta a la alineación de texto en la dirección x:  
  
- **TA_CENTER** alinea el punto con el centro horizontal del rectángulo delimitador.  
  
- **TA_LEFT** alinea el punto con el lado izquierdo del rectángulo delimitador. Ésta es la configuración predeterminada.  
  
- **TA_RIGHT** alinea el punto con el lado derecho del rectángulo delimitador.  
  
 La segunda categoría afecta a la alineación de texto en la dirección y:  
  
- **TA_BASELINE** alinea el punto con la línea de base de la fuente elegida.  
  
- **TA_BOTTOM** alinea el punto de la parte inferior del rectángulo delimitador.  
  
- **TA_TOP** alinea el punto de la parte superior del rectángulo delimitador. Ésta es la configuración predeterminada.  
  
 La tercera categoría determina si la posición actual se actualiza cuando se escribe el texto:  
  
- **TA_NOUPDATECP** no actualiza la posición actual después de cada llamada a una función de salida de texto. Ésta es la configuración predeterminada.  
  
- **TA_UPDATECP** actualiza la posición x actual después de cada llamada a una función de salida de texto. Es la nueva posición en el lado derecho del rectángulo delimitador para el texto. Cuando se establece este marcador, las coordenadas especificadas en las llamadas a la `TextOut` función miembro se omiten.  
  
### <a name="return-value"></a>Valor devuelto  
 La alineación del texto configuración anterior, si se realiza correctamente. El byte de orden inferior contiene la configuración horizontal y el byte de orden superior contiene el valor vertical; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El `TextOut` y `ExtTextOut` funciones miembro utilizan estas marcas al colocar una cadena de texto en una pantalla o un dispositivo. Los indicadores especifican la relación entre un punto específico y un rectángulo que delimita el texto. Las coordenadas de este punto se pasan como parámetros a la `TextOut` función miembro. El rectángulo que delimita el texto está formado por las celdas de carácter adyacentes en la cadena de texto.  
  
##  <a name="a-namesettextcharacterextraa--cdcsettextcharacterextra"></a><a name="settextcharacterextra"></a>CDC::SetTextCharacterExtra  
 Establece la cantidad de espaciado entre caracteres en función.  
  
```  
int SetTextCharacterExtra(int nCharExtra);
```  
  
### <a name="parameters"></a>Parámetros  
 `nCharExtra`  
 Especifica la cantidad de espacio adicional (en unidades lógicas) que se agrega a cada carácter. Si el modo de asignación actual no es `MM_TEXT`, `nCharExtra` se transforma y se redondean al píxel más próximo.  
  
### <a name="return-value"></a>Valor devuelto  
 La cantidad del espaciado de caracteres en función anterior.  
  
### <a name="remarks"></a>Comentarios  
 GDI agrega este espacio a cada carácter, incluido el carácter de salto, cuando escribe una línea de texto en el contexto de dispositivo. El valor predeterminado para la cantidad de espaciado entre caracteres en función es 0.  
  
##  <a name="a-namesettextcolora--cdcsettextcolor"></a><a name="settextcolor"></a>CDC::SetTextColor  
 Establece el color del texto en el color especificado.  
  
```  
virtual COLORREF SetTextColor(COLORREF crColor);
```  
  
### <a name="parameters"></a>Parámetros  
 `crColor`  
 Especifica el color del texto como un valor de color RGB.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor RGB del color de texto anterior.  
  
### <a name="remarks"></a>Comentarios  
 Al escribir texto en este contexto de dispositivo y también al convertir mapas de bits entre color y monocromo contextos de dispositivo, el sistema usará el color del texto.  
  
 Si el dispositivo no puede representar el color especificado, el sistema establece el color del texto en color físico más cercano. El color de fondo de un carácter especificado por el `SetBkColor` y `SetBkMode` funciones miembro.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CWnd::OnCtlColor](../../mfc/reference/cwnd-class.md#onctlcolor).  
  
##  <a name="a-namesettextjustificationa--cdcsettextjustification"></a><a name="settextjustification"></a>CDC::SetTextJustification  
 Agrega el espacio para los caracteres de salto en una cadena.  
  
```  
int SetTextJustification(
    int nBreakExtra,  
    int nBreakCount);
```  
  
### <a name="parameters"></a>Parámetros  
 `nBreakExtra`  
 Especifica el espacio total adicional que se agregarán a la línea de texto (en unidades lógicas). Si el modo de asignación actual no es `MM_TEXT`, se convierte en el modo de asignación actual y se redondea a la unidad de dispositivo más cercana al valor especificado por este parámetro.  
  
 *nBreakCount*  
 Especifica el número de caracteres de salto en la línea.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno si la función se realiza correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Una aplicación puede utilizar el `GetTextMetrics` caracteres de salto de las funciones miembro para recuperar una fuente.  
  
 Después de la `SetTextJustification` llama la función miembro, una llamada a una función de salida de texto (como `TextOut`) distribuye el espacio adicional especificado forma equitativa entre el número especificado de caracteres de salto. El carácter de salto normalmente es el carácter de espacio (ASCII 32), pero puede definirse mediante una fuente como otros caracteres.  
  
 La función miembro `GetTextExtent` se suele utilizar con `SetTextJustification`. `GetTextExtent`calcula el ancho de una línea determinada antes de alineación. Una aplicación puede determinar la cantidad de espacio para especificar en el `nBreakExtra` parámetro restando el valor devuelto por `GetTextExtent` desde el ancho de la cadena después de alineación.  
  
 El `SetTextJustification` función puede usarse para alinear una línea que contiene varias series de distintas fuentes. En este caso, la línea debe crearse por etapas alinear y escribiendo cada ejecución por separado.  
  
 Dado que pueden producirse errores de redondeo durante la alineación, el sistema mantiene un término de error de ejecución que define el error actual. Cuando se alinean en una línea que contiene varias ejecuciones, `GetTextExtent` utiliza automáticamente este término de error cuando calcula el alcance de la próxima ejecución. Esto permite que la función de salida de texto combinar el error en la ejecución nuevo.  
  
 Después de cada línea se ha alineado, debe borrar este término de error para evitar que incorporarse a la línea siguiente. El término puede eliminarse mediante una llamada a `SetTextJustification` con `nBreakExtra` establecido en 0.  
  
##  <a name="a-namesetviewportexta--cdcsetviewportext"></a><a name="setviewportext"></a>CDC::SetViewportExt  
 Establece las extensiones x y y de la ventanilla del contexto de dispositivo.  
  
```  
virtual CSize SetViewportExt(
    int cx,  
    int cy);  
  
CSize SetViewportExt(SIZE size);
```  
  
### <a name="parameters"></a>Parámetros  
 `cx`  
 Especifica la extensión de x de la ventanilla (en unidades de dispositivo).  
  
 `cy`  
 Especifica la extensión y de la ventanilla (en unidades de dispositivo).  
  
 `size`  
 Especifica las extensiones x y y de la ventanilla (en unidades de dispositivo).  
  
### <a name="return-value"></a>Valor devuelto  
 Las extensiones anteriores de la ventanilla como un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto. Cuando se produce un error, las coordenadas x e y de devuelto `CSize` objeto se establecen en 0.  
  
### <a name="remarks"></a>Comentarios  
 La ventanilla, junto con la ventana de contexto de dispositivo define cómo GDI asigna puntos en el sistema de coordenadas lógicas a los puntos en el sistema de coordenadas de dispositivo real. En otras palabras, definen cómo GDI convierte a coordenadas lógicas a coordenadas de dispositivo.  
  
 Cuando se establecen los siguientes modos de asignación, se llama a `SetWindowExt` y `SetViewportExt` se pasan por alto:  
  
|MM_HIENGLISH|MM_LOMETRIC|  
|-------------------|------------------|  
|`MM_HIMETRIC`|`MM_TEXT`|  
|`MM_LOENGLISH`|`MM_TWIPS`|  
  
 Cuando `MM_ISOTROPIC` se establece el modo, una aplicación debe llamar a la `SetWindowExt` función de miembro antes de llamar a `SetViewportExt`.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc).  
  
##  <a name="a-namesetviewportorga--cdcsetviewportorg"></a><a name="setviewportorg"></a>CDC::SetViewportOrg  
 Establece el origen de la ventanilla del contexto de dispositivo.  
  
```  
virtual CPoint SetViewportOrg(
    int x,  
    int y);  
  
CPoint SetViewportOrg(POINT point);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada x (en unidades de dispositivo) del origen de la ventanilla. El valor debe estar dentro del intervalo del sistema de coordenadas de dispositivo.  
  
 *y*  
 Especifica la coordenada y (en unidades de dispositivo) del origen de la ventanilla. El valor debe estar dentro del intervalo del sistema de coordenadas de dispositivo.  
  
 `point`  
 Especifica el origen de la ventanilla. Los valores deben estar dentro del intervalo del sistema de coordenadas de dispositivo. Puede pasarse un **punto** estructura o un `CPoint` objeto para este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 El origen anterior de la ventanilla (en coordenadas de dispositivo) como un `CPoint` objeto.  
  
### <a name="remarks"></a>Comentarios  
 La ventanilla, junto con la ventana de contexto de dispositivo define cómo GDI asigna puntos en el sistema de coordenadas lógicas a los puntos en el sistema de coordenadas de dispositivo real. En otras palabras, definen cómo GDI convierte a coordenadas lógicas a coordenadas de dispositivo.  
  
 El origen de la ventanilla marca el punto en el sistema de coordenadas de dispositivo al que asigna el origen de la ventana, un punto en el sistema de coordenadas lógico especificado por GDI la **SetWindowOrg** función miembro. GDI asigna todos los demás puntos siguiendo el mismo proceso que se necesitan para asignar el origen de la ventana para el origen de la ventanilla. Por ejemplo, todos los puntos de un círculo alrededor del punto en el origen de la ventana será un círculo alrededor del punto en el origen de la ventanilla. De forma similar, todos los puntos de una línea que pasa por el origen de la ventana será una línea que pasa por el origen de la ventanilla.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc).  
  
##  <a name="a-namesetwindowexta--cdcsetwindowext"></a><a name="setwindowext"></a>CDC::SetWindowExt  
 Establece las extensiones x y y de la ventana asociada al contexto de dispositivo.  
  
```  
virtual CSize SetWindowExt(
    int cx,  
    int cy);  
  
CSize SetWindowExt(SIZE size);
```  
  
### <a name="parameters"></a>Parámetros  
 `cx`  
 Especifica la x extensión (en unidades lógicas) de la ventana.  
  
 `cy`  
 Especifica la y extensión (en unidades lógicas) de la ventana.  
  
 `size`  
 Especifica el x - y y-extensiones (en unidades lógicas) de la ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 Las extensiones anteriores de la ventana (en unidades lógicas) como un `CSize` objeto. Si se produce un error, las coordenadas x e y de devuelto `CSize` objeto se establecen en 0.  
  
### <a name="remarks"></a>Comentarios  
 La ventana, junto con la ventanilla de contexto de dispositivo define cómo GDI asigna puntos en el sistema de coordenadas lógicas a los puntos en el sistema de coordenadas de dispositivo.  
  
 Cuando se establecen los siguientes modos de asignación, se llama a `SetWindowExt` y `SetViewportExt` se pasan por alto las funciones:  
  
- `MM_HIENGLISH`  
  
- `MM_HIMETRIC`  
  
- `MM_LOENGLISH`  
  
- `MM_LOMETRIC`  
  
- `MM_TEXT`  
  
- `MM_TWIPS`  
  
 Cuando `MM_ISOTROPIC` se establece el modo, una aplicación debe llamar a la `SetWindowExt` función miembro antes de llamar a `SetViewportExt`.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc).  
  
##  <a name="a-namesetwindoworga--cdcsetwindoworg"></a><a name="setwindoworg"></a>CDC::SetWindowOrg  
 Establece el origen del contexto de dispositivo de la ventana.  
  
```  
CPoint SetWindowOrg(
    int x,  
    int y);  
  
CPoint SetWindowOrg(POINT point);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada x lógica del nuevo origen de la ventana.  
  
 *y*  
 Especifica la coordenada y lógica del nuevo origen de la ventana.  
  
 `point`  
 Especifica las coordenadas lógicas del nuevo origen de la ventana. Puede pasarse un **punto** estructura o un `CPoint` objeto para este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 El origen anterior de la ventana como un `CPoint` objeto.  
  
### <a name="remarks"></a>Comentarios  
 La ventana, junto con la ventanilla de contexto de dispositivo define cómo GDI asigna puntos en el sistema de coordenadas lógicas a los puntos en el sistema de coordenadas de dispositivo.  
  
 El origen de la ventana marca el punto en el sistema de coordenadas lógico desde la que GDI asigna el origen de la ventanilla, un punto en el sistema de coordenadas de dispositivo especificado por el **SetWindowOrg** (función). GDI asigna todos los demás puntos siguiendo el mismo proceso que se necesitan para asignar el origen de la ventana para el origen de la ventanilla. Por ejemplo, todos los puntos de un círculo alrededor del punto en el origen de la ventana será un círculo alrededor del punto en el origen de la ventanilla. De forma similar, todos los puntos de una línea que pasa por el origen de la ventana será una línea que pasa por el origen de la ventanilla.  
  
##  <a name="a-namesetworldtransforma--cdcsetworldtransform"></a><a name="setworldtransform"></a>CDC::SetWorldTransform  
 Establece una transformación lineal bidimensional entre espacio universal y espacio de páginas para el contexto de dispositivo especificado. Esta transformación puede utilizarse para escalar, girar, sesgar o traducir el resultado de gráficos.  
  
```  
BOOL SetWorldTransform(const XFORM& rXform);
```  
  
### <a name="parameters"></a>Parámetros  
 `rXform`  
 Hacer referencia a un [XFORM](http://msdn.microsoft.com/library/windows/desktop/dd145228) estructura que contiene los datos de transformación.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor distinto de cero en caso de éxito.  
  
 Devuelve 0 en caso de error.  
  
 Para obtener información de error extendida, llame a [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Comentarios  
 Este método ajusta la función GDI de Windows [SetWorldTransform](http://msdn.microsoft.com/library/windows/desktop/dd145104).  
  
##  <a name="a-namestartdoca--cdcstartdoc"></a><a name="startdoc"></a>CDC::StartDoc  
 Informa al controlador de dispositivo que se está iniciando un nuevo trabajo de impresión y que todas las `StartPage` y `EndPage` llamadas deben poner en cola en el mismo trabajo hasta un `EndDoc` se produce la llamada.  
  
```  
int StartDoc(LPDOCINFO lpDocInfo);  
int StartDoc(LPCTSTR lpszDocName);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpDocInfo*  
 Apunta a un [DOCINFO](http://msdn.microsoft.com/library/windows/desktop/dd183574) estructura que contiene el nombre de archivo del documento y el nombre del archivo de salida.  
  
 *lpszDocName*  
 Puntero a una cadena que contiene el nombre de archivo del documento.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto es mayor que cero. Este valor es el identificador de trabajo de impresión del documento.  
  
 Si se produce un error en la función, el valor devuelto es menor o igual que cero.  
  
### <a name="remarks"></a>Comentarios  
 Esto garantiza que los documentos más de una página no están intercalados con otros trabajos.  
  
 Para las versiones 3.1 y versiones posteriores de Windows, esta función reemplaza la **STARTDOC** escape de impresora. El uso de esta función garantiza que los documentos que contienen más de una página no se intercalan con otros trabajos de impresión.  
  
 `StartDoc`no debe usarse dentro de metarchivos.  
  
### <a name="example"></a>Ejemplo  
 Este fragmento de código obtiene la impresora predeterminada, abre un trabajo de impresión y pone en cola una página con "¡Hello, World!" en él. Dado el texto impreso por este código no se ajusta a las unidades lógicas de la impresora, el texto de salida puede ser en dichas letras pequeño que el resultado es ilegible. Escalado de las funciones, como CDC `SetMapMode`, `SetViewportOrg`, y `SetWindowExt`, se puede usar para corregir la escala.  
  
 [!code-cpp[NVC_MFCDocView nº&41;](../../mfc/codesnippet/cpp/cdc-class_13.cpp)]  
  
##  <a name="a-namestartpagea--cdcstartpage"></a><a name="startpage"></a>CDC::StartPage  
 Llame a esta función miembro para preparar el controlador de impresora para recibir datos.  
  
```  
int StartPage();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Mayor o igual a 0 si la función se realiza correctamente, o un valor negativo si se produjo un error.  
  
### <a name="remarks"></a>Comentarios  
 `StartPage`reemplaza el **NEWFRAME** y **BANDINFO** establece secuencias de escape.  
  
 Para obtener información general de la secuencia de llamadas de impresión, consulte la [StartDoc](#startdoc) función miembro.  
  
 El sistema deshabilita el `ResetDC` función miembro entre las llamadas a `StartPage` y `EndPage`.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CDC::StartDoc](#startdoc).  
  
##  <a name="a-namestretchblta--cdcstretchblt"></a><a name="stretchblt"></a>CDC::StretchBlt  
 Copia un mapa de bits de un rectángulo de origen en un rectángulo de destino, estirando o comprimiendo el mapa de bits si es necesario para ajustarse a las dimensiones del rectángulo de destino.  
  
```  
BOOL StretchBlt(
    int x,  
    int y,  
    int nWidth,  
    int nHeight,  
    CDC* pSrcDC,  
    int xSrc,  
    int ySrc,  
    int nSrcWidth,  
    int nSrcHeight,  
    DWORD dwRop);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada X (en unidades lógicas) de la esquina superior izquierda del rectángulo de destino.  
  
 *y*  
 Especifica la coordenada Y (en unidades lógicas) de la esquina superior izquierda del rectángulo de destino.  
  
 `nWidth`  
 Especifica el ancho (en unidades lógicas) del rectángulo de destino.  
  
 `nHeight`  
 Especifica el alto (en unidades lógicas) del rectángulo de destino.  
  
 `pSrcDC`  
 Especifica el contexto de dispositivo de origen.  
  
 `xSrc`  
 Especifica la coordenada X (en unidades lógicas) de la esquina superior izquierda del rectángulo de origen.  
  
 `ySrc`  
 Especifica la coordenada Y (en unidades lógicas) de la esquina superior izquierda del rectángulo de origen.  
  
 `nSrcWidth`  
 Especifica el ancho (en unidades lógicas) del rectángulo de origen.  
  
 `nSrcHeight`  
 Especifica el alto (en unidades lógicas) del rectángulo de origen.  
  
 *dwRop*  
 Especifica la operación de trama que se va a realizar. Los códigos de operación de trama definen cómo combina GDI los colores en las operaciones de salida que implican un pincel actual, un posible mapa de bits de origen y un mapa de bits de destino. Este parámetro puede tener uno de los valores siguientes:  
  
- **BLACKNESS** pone en negro toda la salida.  
  
- **DSTINVERT** invierte el mapa de bits de destino.  
  
- **MERGECOPY** combina el patrón y el mapa de bits de origen mediante el operador booleano AND.  
  
- **MERGEPAINT** combina el mapa de bits de origen invertido con el mapa de bits de destino mediante el operador booleano OR.  
  
- **NOTSRCCOPY** copia el mapa de bits de origen invertido al destino.  
  
- **NOTSRCERASE** invierte el resultado de combinar los mapas de bits de origen y de destino mediante el operador booleano OR.  
  
- **PATCOPY** copia el patrón al mapa de bits de destino.  
  
- **PATINVERT** combina el mapa de bits de destino con el patrón mediante el operador booleano XOR.  
  
- **PATPAINT** combina el mapa de bits de origen invertido con el patrón mediante el operador booleano OR. Combina el resultado de esta operación con el mapa de bits de destino mediante el operador booleano OR.  
  
- **SRCAND** combina píxeles de los mapas de bits de origen y de destino mediante el operador booleano AND.  
  
- **SRCCOPY** copia el mapa de bits de origen en el mapa de bits de destino.  
  
- **SRCERASE** invierte el mapa de bits de destino y combina el resultado con el mapa de bits de origen mediante el operador booleano AND.  
  
- **SRCINVERT** combina píxeles de los mapas de bits de origen y de destino mediante el operador booleano XOR.  
  
- **SRCPAINT** combina píxeles de los mapas de bits de origen y de destino mediante el operador booleano OR.  
  
- **WHITENESS** pone en blanco toda la salida.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se dibuja el mapa de bits; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 La función emplea el modo de ajuste del contexto de dispositivo de destino (establecido por `SetStretchBltMode`) para determinar cómo estirar o comprimir el mapa de bits.  
  
 La función `StretchBlt` mueve el mapa de bits del dispositivo de origen especificado por `pSrcDC` al dispositivo de destino representado por el objeto de contexto de dispositivo a cuya función miembro se llama. Los parámetros `xSrc`, `ySrc`, `nSrcWidth` y `nSrcHeight` definen la esquina superior izquierda y las dimensiones del rectángulo de origen. El *x*, *y*, `nWidth`, y `nHeight` parámetros proporcionan la esquina superior izquierda y las dimensiones del rectángulo de destino. La operación de trama especificada por *dwRop* define cómo se combinan el mapa de bits de origen y los bits instalado en el dispositivo de destino.  
  
 La función `StretchBlt` crea una imagen reflejada de un mapa de bits si los signos de los parámetros `nSrcWidth` y `nWidth` o `nSrcHeight` y `nHeight` son distintos. Si `nSrcWidth` y `nWidth` tienen signos diferentes, la función crea una imagen reflejada del mapa de bits a lo largo del eje X. Si `nSrcHeight` y `nHeight` tienen signos diferentes, la función crea una imagen reflejada del mapa de bits a lo largo del eje Y.  
  
 La función `StretchBlt` estira o comprime el mapa de bits de origen en memoria y después copia el resultado al destino. Si se va a combinar un patrón con el resultado, no se combina hasta que el mapa de bits de origen estirado no se copia al destino. Si se usa un pincel, es el pincel seleccionado en el contexto de dispositivo de destino. Las coordenadas de destino se transforman según el contexto de dispositivo de destino; las coordenadas de origen se transforman según el contexto de dispositivo de origen.  
  
 Si los mapas de bits de destino, origen y patrón no tienen el mismo formato de color, `StretchBlt` convierte los mapas de bits de origen y de patrón para que coincidan con los mapas de bits de destino. En la conversión se usan los colores de primer plano y de fondo del contexto de dispositivo de destino.  
  
 Si `StretchBlt` debe convertir un mapa de bits monocromo a color, establece los bits blancos (1) al color de fondo y los bits negros (0) al color de primer plano. Para convertir de color a monocromo, establece en blanco (1) los píxeles que coinciden con el color de fondo y establece en negro (0) todos los demás píxeles. Se usan los colores de primer plano y de fondo del contexto de dispositivo con color.  
  
 No todos los dispositivos admiten la función `StretchBlt`. Para determinar si un dispositivo admite `StretchBlt`, llame a la `GetDeviceCaps` función miembro con el **RASTERCAPS** de índice y comprobar el valor devuelto para la **RC_STRETCHBLT** marca.  
  
##  <a name="a-namestrokeandfillpatha--cdcstrokeandfillpath"></a><a name="strokeandfillpath"></a>CDC::StrokeAndFillPath  
 Cierra figuras abiertas en una ruta de acceso, trazos del contorno de la ruta de acceso utilizando el lápiz actual y su interior se rellena con el pincel actual.  
  
```  
BOOL StrokeAndFillPath();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El contexto de dispositivo debe contener un trayecto cerrado. El `StrokeAndFillPath` función miembro tiene el mismo efecto que cerrar todas las figuras abiertas en la ruta de acceso y trazado y rellenar la ruta de acceso por separado, salvo que la región de rellenada no superpondrán el incluso si región trazadas el lápiz está amplia.  
  
##  <a name="a-namestrokepatha--cdcstrokepath"></a><a name="strokepath"></a>CDC::StrokePath  
 Representa la ruta de acceso especificada mediante el lápiz actual.  
  
```  
BOOL StrokePath();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El contexto de dispositivo debe contener un trayecto cerrado.  
  
##  <a name="a-nametabbedtextouta--cdctabbedtextout"></a><a name="tabbedtextout"></a>CDC::TabbedTextOut  
 Llame a esta función miembro para escribir una cadena de caracteres en la ubicación especificada, expansión de fichas a los valores especificados en la matriz de posiciones de tabulación.  
  
```  
virtual CSize TabbedTextOut(
    int x,  
    int y,  
    LPCTSTR lpszString,  
    int nCount,  
    int nTabPositions,  
    LPINT lpnTabStopPositions,  
    int nTabOrigin);

 
CSize TabbedTextOut(
    int x,  
    int y,  
    const CString& str,  
    int nTabPositions,  
    LPINT lpnTabStopPositions,  
    int nTabOrigin);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada x lógica del punto inicial de la cadena.  
  
 *y*  
 Especifica la coordenada y lógica del punto inicial de la cadena.  
  
 `lpszString`  
 Puntos de la cadena de caracteres para dibujar. Puede pasar un puntero a una matriz de caracteres o un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto para este parámetro.  
  
 `nCount`  
 Especifica el número de caracteres de la cadena. Si `nCount` es –&1;, se calcula la longitud.  
  
 `nTabPositions`  
 Especifica el número de valores de la matriz de posiciones de tabulación.  
  
 `lpnTabStopPositions`  
 Apunta a una matriz que contiene las posiciones de tabulación (en unidades lógicas). Las tabulaciones deben estar ordenadas en sentido ascendente; el menor valor de x debe ser el primer elemento de la matriz.  
  
 `nTabOrigin`  
 Especifica la coordenada x de la posición inicial desde la que se expanden las fichas (en unidades lógicas).  
  
 `str`  
 Un `CString` objeto que contiene los caracteres especificados.  
  
### <a name="return-value"></a>Valor devuelto  
 Las dimensiones de la cadena (en unidades lógicas) como un `CSize` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Se escribe texto en la fuente seleccionada actualmente. Si `nTabPositions` es 0 y `lpnTabStopPositions` es **NULL**, las fichas se expanden hasta ocho veces el promedio ancho de caracteres.  
  
 Si `nTabPositions` es 1, la ficha se detiene se separan con la distancia especificada por el primer valor de la `lpnTabStopPositions` matriz. Si el `lpnTabStopPositions` matriz contiene más de un valor, se establece una tabulación para cada valor de la matriz, hasta el número especificado por `nTabPositions`. El `nTabOrigin` parámetro permite que una aplicación llame a la `TabbedTextOut` función varias veces para una sola línea. Si la aplicación llama más de una vez a la función con el `nTabOrigin` establecida en el mismo valor cada vez, la función expande todas las pestañas con respecto a la posición especificada por `nTabOrigin`.  
  
 De forma predeterminada, la función no usa ni actualiza la posición actual. Si una aplicación necesita actualizar la posición actual cuando llama a la función, la aplicación puede llamar a la [SetTextAlign](#settextalign) función miembro con `nFlags` establecido en **TA_UPDATECP**. Cuando se establece este marcador, Windows pasa por alto la *x* y *y* parámetros en llamadas posteriores a `TabbedTextOut`, utilizando la posición actual en su lugar.  
  
##  <a name="a-nametextouta--cdctextout"></a><a name="textout"></a>CDC:: TextOut  
 Escribe una cadena de caracteres en la ubicación especificada usando la fuente seleccionada actualmente.  
  
```  
virtual BOOL TextOut(
    int x,  
    int y,  
    LPCTSTR lpszString,  
    int nCount);

 
BOOL TextOut(
    int x,
    int y,
    const CString& str);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la coordenada X lógica del punto inicial del texto.  
  
 *y*  
 Especifica la coordenada Y lógica del punto inicial del texto.  
  
 `lpszString`  
 Apunta a la cadena de caracteres que se va a dibujar.  
  
 `nCount`  
 Especifica el número de caracteres de la cadena.  
  
 `str`  
 Objeto `CString` que contiene los caracteres que se van a dibujar.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Los orígenes de los caracteres están en la esquina superior izquierda de la celda de caracteres. De forma predeterminada, la función no usa ni actualiza la posición actual.  
  
 Si una aplicación necesita actualizar la posición actual cuando llama a `TextOut`, la aplicación puede llamar a la `SetTextAlign` función miembro con `nFlags` establecido en **TA_UPDATECP**. Cuando se establece este marcador, Windows pasa por alto la *x* y *y* parámetros en llamadas posteriores a `TextOut`, utilizando la posición actual en su lugar.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CDC:: beginpath](#beginpath).  
  
##  <a name="a-nametransparentblta--cdctransparentblt"></a><a name="transparentblt"></a>CDC::TransparentBlt  
 Llame a esta función miembro para transferir un bloque de bits de los datos de color, que se corresponde con un rectángulo de píxeles desde el contexto de dispositivo de origen especificado en un contexto de dispositivo de destino.  
  
```  
BOOL TransparentBlt(
    int xDest,  
    int yDest,
    int nDestWidth,
    int nDestHeight,  
    CDC* pSrcDC,  
    int xSrc,  
    int ySrc,  
    int nSrcWidth,  
    int nSrcHeight,  
    UINT clrTransparent);
```  
  
### <a name="parameters"></a>Parámetros  
 `xDest`  
 Especifica la coordenada x, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.  
  
 `yDest`  
 Especifica la coordenada y, en unidades lógicas, de la esquina superior izquierda del rectángulo de destino.  
  
 `nDestWidth`  
 Especifica el ancho, en unidades lógicas, del rectángulo de destino.  
  
 `nDestHeight`  
 Especifica el alto, en unidades lógicas, del rectángulo de destino.  
  
 `pSrcDC`  
 Puntero al contexto de dispositivo de origen.  
  
 `xSrc`  
 Especifica la coordenada x, en unidades lógicas, del rectángulo de origen.  
  
 `ySrc`  
 Especifica la coordenada y, en unidades lógicas, del rectángulo de origen.  
  
 `nSrcWidth`  
 Especifica el ancho, en unidades lógicas, del rectángulo de origen.  
  
 `nSrcHeight`  
 Especifica el alto, en unidades lógicas, del rectángulo de origen.  
  
 `clrTransparent`  
 El color RGB del mapa de bits de origen a tratar como transparente.  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si es correcto; en caso contrario **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 `TransparentBlt`permite la transparencia; es decir, el color RGB indicado por `clrTransparent` se procesa transparente para la transferencia.  
  
 Para obtener más información, consulte [TransparentBlt](http://msdn.microsoft.com/library/windows/desktop/dd145141) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameupdatecolorsa--cdcupdatecolors"></a><a name="updatecolors"></a>CDC::UpdateColors  
 Actualizaciones del área cliente de contexto de dispositivo mediante la coincidencia actual colores en el área de cliente de la paleta del sistema píxel por píxel.  
  
```  
void UpdateColors();
```  
  
### <a name="remarks"></a>Comentarios  
 Puede llamar una ventana inactiva con una paleta lógica producida `UpdateColors` como una alternativa a volver a dibujar su área cliente cuando cambia la paleta del sistema.  
  
 Para obtener más información acerca del uso de paletas de colores, consulte [UpdateColors](http://msdn.microsoft.com/library/windows/desktop/dd145166) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 El `UpdateColors` función miembro normalmente las actualizaciones de un área de cliente más rápido que volver a dibujar el área. Sin embargo, como la función realiza la conversión de colores según el color de cada píxel antes de cambia la paleta del sistema, cada llamada a esta función da como resultado la pérdida de precisión del color.  
  
##  <a name="a-namewidenpatha--cdcwidenpath"></a><a name="widenpath"></a>CDC::WidenPath  
 Vuelve a definir la ruta de acceso actual como el área que se va a pintar si la ruta de acceso se traza con el lápiz actualmente seleccionado en el contexto de dispositivo.  
  
```  
BOOL WidenPath();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es correcta sólo si el lápiz actual es un lápiz geométrico creado por la segunda versión de `CreatePen` función miembro, o si el lápiz se crea con la primera versión de `CreatePen` y tiene un ancho, en unidades del dispositivo, de mayor que 1. El contexto de dispositivo debe contener un trayecto cerrado. Las curvas de Bzier en la ruta de acceso se convierten en secuencias de líneas rectas aproximar las curvas ampliadas. Por lo tanto, no hay curvas Bzier permanecen en la ruta de acceso después de `WidenPath` se llama.  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CPaintDC (clase)](../../mfc/reference/cpaintdc-class.md)   
 [Clase de los objetos CWindowDC](../../mfc/reference/cwindowdc-class.md)   
 [CClientDC (clase)](../../mfc/reference/cclientdc-class.md)   
 [CMetaFileDC (clase)](../../mfc/reference/cmetafiledc-class.md)

