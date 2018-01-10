---
title: Clase CRenderTarget | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRenderTarget
- AFXRENDERTARGET/CRenderTarget
- AFXRENDERTARGET/CRenderTarget::CRenderTarget
- AFXRENDERTARGET/CRenderTarget::Attach
- AFXRENDERTARGET/CRenderTarget::BeginDraw
- AFXRENDERTARGET/CRenderTarget::Clear
- AFXRENDERTARGET/CRenderTarget::COLORREF_TO_D2DCOLOR
- AFXRENDERTARGET/CRenderTarget::CreateCompatibleRenderTarget
- AFXRENDERTARGET/CRenderTarget::Destroy
- AFXRENDERTARGET/CRenderTarget::Detach
- AFXRENDERTARGET/CRenderTarget::DrawBitmap
- AFXRENDERTARGET/CRenderTarget::DrawEllipse
- AFXRENDERTARGET/CRenderTarget::DrawGeometry
- AFXRENDERTARGET/CRenderTarget::DrawGlyphRun
- AFXRENDERTARGET/CRenderTarget::DrawLine
- AFXRENDERTARGET/CRenderTarget::DrawRectangle
- AFXRENDERTARGET/CRenderTarget::DrawRoundedRectangle
- AFXRENDERTARGET/CRenderTarget::DrawText
- AFXRENDERTARGET/CRenderTarget::DrawTextLayout
- AFXRENDERTARGET/CRenderTarget::EndDraw
- AFXRENDERTARGET/CRenderTarget::FillEllipse
- AFXRENDERTARGET/CRenderTarget::FillGeometry
- AFXRENDERTARGET/CRenderTarget::FillMesh
- AFXRENDERTARGET/CRenderTarget::FillOpacityMask
- AFXRENDERTARGET/CRenderTarget::FillRectangle
- AFXRENDERTARGET/CRenderTarget::FillRoundedRectangle
- AFXRENDERTARGET/CRenderTarget::Flush
- AFXRENDERTARGET/CRenderTarget::GetAntialiasMode
- AFXRENDERTARGET/CRenderTarget::GetDpi
- AFXRENDERTARGET/CRenderTarget::GetMaximumBitmapSize
- AFXRENDERTARGET/CRenderTarget::GetPixelFormat
- AFXRENDERTARGET/CRenderTarget::GetPixelSize
- AFXRENDERTARGET/CRenderTarget::GetRenderTarget
- AFXRENDERTARGET/CRenderTarget::GetSize
- AFXRENDERTARGET/CRenderTarget::GetTags
- AFXRENDERTARGET/CRenderTarget::GetTextAntialiasMode
- AFXRENDERTARGET/CRenderTarget::GetTextRenderingParams
- AFXRENDERTARGET/CRenderTarget::GetTransform
- AFXRENDERTARGET/CRenderTarget::IsSupported
- AFXRENDERTARGET/CRenderTarget::IsValid
- AFXRENDERTARGET/CRenderTarget::PopAxisAlignedClip
- AFXRENDERTARGET/CRenderTarget::PopLayer
- AFXRENDERTARGET/CRenderTarget::PushAxisAlignedClip
- AFXRENDERTARGET/CRenderTarget::PushLayer
- AFXRENDERTARGET/CRenderTarget::RestoreDrawingState
- AFXRENDERTARGET/CRenderTarget::SaveDrawingState
- AFXRENDERTARGET/CRenderTarget::SetAntialiasMode
- AFXRENDERTARGET/CRenderTarget::SetDpi
- AFXRENDERTARGET/CRenderTarget::SetTags
- AFXRENDERTARGET/CRenderTarget::SetTextAntialiasMode
- AFXRENDERTARGET/CRenderTarget::SetTextRenderingParams
- AFXRENDERTARGET/CRenderTarget::SetTransform
- AFXRENDERTARGET/CRenderTarget::VerifyResource
- AFXRENDERTARGET/CRenderTarget::m_lstResources
- AFXRENDERTARGET/CRenderTarget::m_pRenderTarget
- AFXRENDERTARGET/CRenderTarget::m_pTextFormatDefault
dev_langs: C++
helpviewer_keywords:
- CRenderTarget [MFC], CRenderTarget
- CRenderTarget [MFC], Attach
- CRenderTarget [MFC], BeginDraw
- CRenderTarget [MFC], Clear
- CRenderTarget [MFC], COLORREF_TO_D2DCOLOR
- CRenderTarget [MFC], CreateCompatibleRenderTarget
- CRenderTarget [MFC], Destroy
- CRenderTarget [MFC], Detach
- CRenderTarget [MFC], DrawBitmap
- CRenderTarget [MFC], DrawEllipse
- CRenderTarget [MFC], DrawGeometry
- CRenderTarget [MFC], DrawGlyphRun
- CRenderTarget [MFC], DrawLine
- CRenderTarget [MFC], DrawRectangle
- CRenderTarget [MFC], DrawRoundedRectangle
- CRenderTarget [MFC], DrawText
- CRenderTarget [MFC], DrawTextLayout
- CRenderTarget [MFC], EndDraw
- CRenderTarget [MFC], FillEllipse
- CRenderTarget [MFC], FillGeometry
- CRenderTarget [MFC], FillMesh
- CRenderTarget [MFC], FillOpacityMask
- CRenderTarget [MFC], FillRectangle
- CRenderTarget [MFC], FillRoundedRectangle
- CRenderTarget [MFC], Flush
- CRenderTarget [MFC], GetAntialiasMode
- CRenderTarget [MFC], GetDpi
- CRenderTarget [MFC], GetMaximumBitmapSize
- CRenderTarget [MFC], GetPixelFormat
- CRenderTarget [MFC], GetPixelSize
- CRenderTarget [MFC], GetRenderTarget
- CRenderTarget [MFC], GetSize
- CRenderTarget [MFC], GetTags
- CRenderTarget [MFC], GetTextAntialiasMode
- CRenderTarget [MFC], GetTextRenderingParams
- CRenderTarget [MFC], GetTransform
- CRenderTarget [MFC], IsSupported
- CRenderTarget [MFC], IsValid
- CRenderTarget [MFC], PopAxisAlignedClip
- CRenderTarget [MFC], PopLayer
- CRenderTarget [MFC], PushAxisAlignedClip
- CRenderTarget [MFC], PushLayer
- CRenderTarget [MFC], RestoreDrawingState
- CRenderTarget [MFC], SaveDrawingState
- CRenderTarget [MFC], SetAntialiasMode
- CRenderTarget [MFC], SetDpi
- CRenderTarget [MFC], SetTags
- CRenderTarget [MFC], SetTextAntialiasMode
- CRenderTarget [MFC], SetTextRenderingParams
- CRenderTarget [MFC], SetTransform
- CRenderTarget [MFC], VerifyResource
- CRenderTarget [MFC], m_lstResources
- CRenderTarget [MFC], m_pRenderTarget
- CRenderTarget [MFC], m_pTextFormatDefault
ms.assetid: 30d1607d-68d3-4d14-ac36-fdbd0ef903a1
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a52a2add3306aaf684f9a48a06d1add229205233
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="crendertarget-class"></a>Clase CRenderTarget
Un contenedor para ID2D1RenderTarget.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CRenderTarget : public CObject;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRenderTarget::CRenderTarget](#crendertarget)|Construye un objeto CRenderTarget.|  
|[CRenderTarget:: ~ CRenderTarget](#crendertarget__~crendertarget)|Destructor. Se llama cuando se destruye un objeto de destino de representación.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRenderTarget::Attach](#attach)|Adjunta existente representar la interfaz de destino para el objeto|  
|[CRenderTarget::BeginDraw](#begindraw)|Inicia el dibujo en este destino de representación.|  
|[CRenderTarget::Clear](#clear)|Borra el área de dibujo al color especificado.|  
|[CRenderTarget::COLORREF_TO_D2DCOLOR](#colorref_to_d2dcolor)|Convierte valores de color y alfa GDI en el objeto D2D1_COLOR_F.|  
|[CRenderTarget::CreateCompatibleRenderTarget](#createcompatiblerendertarget)|Crea un nuevo destino de representación de mapa de bits para su uso durante intermedio dibujo fuera de la pantalla que es compatible con el destino de representación actual.|  
|[CRenderTarget::Destroy](#destroy)|Elimina uno o más recursos|  
|[CRenderTarget::Detach](#detach)|Separa la interfaz de destino de representación del objeto|  
|[CRenderTarget::DrawBitmap](#drawbitmap)|Dibuja el texto con formato que describe el objeto IDWriteTextLayout especificado.|  
|[CRenderTarget::DrawEllipse](#drawellipse)|Dibuja el contorno de la elipse especificada usando el estilo de trazo especificados.|  
|[CRenderTarget::DrawGeometry](#drawgeometry)|Dibuja el contorno de la geometría especificada usando el estilo de trazo especificados.|  
|[CRenderTarget::DrawGlyphRun](#drawglyphrun)|Dibuja los glifos especificados.|  
|[CRenderTarget::DrawLine](#drawline)|Dibuja una línea entre los puntos especificados utilizando el estilo de trazo especificados.|  
|[CRenderTarget::DrawRectangle](#drawrectangle)|Dibuja el contorno de un rectángulo que tiene el estilo de trazo y las dimensiones especificadas.|  
|[CRenderTarget::DrawRoundedRectangle](#drawroundedrectangle)|Dibuja el contorno del rectángulo redondeado especificado utilizando el estilo de trazo especificados.|  
|[CRenderTarget::DrawText](#drawtext)|Dibuja el texto especificado con la información de formato proporcionada por un objeto IDWriteTextFormat.|  
|[CRenderTarget::DrawTextLayout](#drawtextlayout)|Dibuja el texto con formato que describe el objeto IDWriteTextLayout especificado.|  
|[CRenderTarget::EndDraw](#enddraw)|Finaliza las operaciones de dibujo en el destino de representación e indica las etiquetas asociadas y el estado de error actual.|  
|[CRenderTarget::FillEllipse](#fillellipse)|Pinta el interior de la elipse especificada.|  
|[CRenderTarget::FillGeometry](#fillgeometry)|Pinta el interior de la geometría especificada.|  
|[CRenderTarget::FillMesh](#fillmesh)|Pinta el interior de la malla especificado.|  
|[CRenderTarget::FillOpacityMask](#fillopacitymask)|Se aplica la máscara de opacidad descrita por el mapa de bits especificado en un pincel y utiliza ese pincel para pintar una región de destino de representación.|  
|[CRenderTarget::FillRectangle](#fillrectangle)|Pinta el interior del rectángulo especificado.|  
|[CRenderTarget::FillRoundedRectangle](#fillroundedrectangle)|Pinta el interior del rectángulo redondeado especificado.|  
|[CRenderTarget::Flush](#flush)|Ejecuta todos los comandos de dibujo pendientes.|  
|[CRenderTarget::GetAntialiasMode](#getantialiasmode)|Recupera el modo de suavizado de contorno actual para las operaciones de dibujo sin texto.|  
|[CRenderTarget::GetDpi](#getdpi)|Devuelve la representación de los puntos de destino por pulgada (PPP)|  
|[CRenderTarget::GetMaximumBitmapSize](#getmaximumbitmapsize)|Obtiene el tamaño máximo, en unidades de dependiente de dispositivo (píxeles), de cualquier dimensión de un mapa de bits compatible con el destino de representación|  
|[CRenderTarget::GetPixelFormat](#getpixelformat)|Recupera el modo de alfa y formato de píxel del destino de representación|  
|[CRenderTarget::GetPixelSize](#getpixelsize)|Devuelve el tamaño del destino de representación en píxeles del dispositivo|  
|[CRenderTarget::GetRenderTarget](#getrendertarget)|Interfaz de ID2D1RenderTarget devuelve|  
|[CRenderTarget::GetSize](#getsize)|Devuelve el tamaño del destino de representación en píxeles independientes del dispositivo|  
|[CRenderTarget::GetTags](#gettags)|Obtiene la etiqueta para operaciones de dibujo subsiguientes.|  
|[CRenderTarget::GetTextAntialiasMode](#gettextantialiasmode)|Obtiene el modo actual de suavizado de contorno para texto y las operaciones de dibujo del glifo.|  
|[CRenderTarget::GetTextRenderingParams](#gettextrenderingparams)|Recupera las opciones de representación de texto actual del destino de representación.|  
|[CRenderTarget::GetTransform](#gettransform)|Aplica la transformación especificada en el destino de representación, reemplazando la transformación existente. Todas las operaciones de dibujo subsiguientes se producen en el espacio transformado.|  
|[CRenderTarget::IsSupported](#issupported)|Indica si el destino de representación admite las propiedades especificadas|  
|[CRenderTarget::IsValid](#isvalid)|Comprobaciones de validez de los recursos|  
|[CRenderTarget::PopAxisAlignedClip](#popaxisalignedclip)|Quita el último clip alineado con el eje del destino de representación. Después de que se llama a este método, el clip ya no se aplica a las operaciones de dibujo subsiguientes.|  
|[CRenderTarget::PopLayer](#poplayer)|Detiene la redirección de las operaciones de dibujo a la capa que se especifica mediante la última PushLayer llamar.|  
|[CRenderTarget::PushAxisAlignedClip](#pushaxisalignedclip)|Quita el último clip alineado con el eje del destino de representación. Después de que se llama a este método, el clip ya no se aplica a las operaciones de dibujo subsiguientes.|  
|[CRenderTarget::PushLayer](#pushlayer)|Agrega la capa especificada en el destino de representación para que lo recibe todas las operaciones de dibujo subsiguientes hasta que se llama PopLayer.|  
|[CRenderTarget::RestoreDrawingState](#restoredrawingstate)|Establece el estado de dibujo del destino de representación para el ID2D1DrawingStateBlock especificado.|  
|[CRenderTarget::SaveDrawingState](#savedrawingstate)|Guarda el estado de dibujo actual en el ID2D1DrawingStateBlock especificado.|  
|[CRenderTarget::SetAntialiasMode](#setantialiasmode)|Establece el modo de suavizado de contorno del destino de representación. El modo de suavizado de contorno se aplica a todas las operaciones de dibujo subsiguientes, sin incluir texto y las operaciones de dibujo del glifo.|  
|[CRenderTarget::SetDpi](#setdpi)|Establece los puntos por pulgada (PPP) del destino de representación.|  
|[CRenderTarget::SetTags](#settags)|Especifica una etiqueta para operaciones de dibujo subsiguientes.|  
|[CRenderTarget::SetTextAntialiasMode](#settextantialiasmode)|Especifica el modo de suavizado de contorno para texto posterior y las operaciones de dibujo del glifo.|  
|[CRenderTarget::SetTextRenderingParams](#settextrenderingparams)|Especifica las opciones de representación de texto que se aplicará a todo el texto posterior y las operaciones de dibujo del glifo.|  
|[CRenderTarget::SetTransform](#settransform)|Sobrecargado. Aplica la transformación especificada en el destino de representación, reemplazando la transformación existente. Todas las operaciones de dibujo subsiguientes se producen en el espacio transformado.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRenderTarget::VerifyResource](#verifyresource)|Comprueba la validez del objeto de CD2DResource; crea el objeto si aún no existe.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRenderTarget::operator ID2D1RenderTarget *](#operator_id2d1rendertarget_star)|Interfaz de ID2D1RenderTarget devuelve|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CRenderTarget::m_lstResources](#m_lstresources)|Una lista de punteros a objetos CD2DResource.|  
|[CRenderTarget::m_pRenderTarget](#m_prendertarget)|Un puntero a un objeto ID2D1RenderTarget.|  
|[CRenderTarget::m_pTextFormatDefault](#m_ptextformatdefault)|Un puntero al objeto CD2DTextFormat que contiene un formato de texto predeterminado.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="_dtorcrendertarget"></a>CRenderTarget:: ~ CRenderTarget  
 Destructor. Se llama cuando se destruye un objeto de destino de representación.  
  
```  
virtual ~CRenderTarget();
```  
  
##  <a name="attach"></a>CRenderTarget::Attach  
 Adjunta existente representar la interfaz de destino para el objeto  
  
```  
void Attach(ID2D1RenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRenderTarget`  
 Interfaz de destino de representación existente. No puede ser NULL  
  
##  <a name="begindraw"></a>CRenderTarget::BeginDraw  
 Inicia el dibujo en este destino de representación.  
  
```  
void BeginDraw();
```  
  
##  <a name="clear"></a>CRenderTarget::Clear  
 Borra el área de dibujo al color especificado.  
  
```  
void Clear(D2D1_COLOR_F color);
```  
  
### <a name="parameters"></a>Parámetros  
 `color`  
 El color al que se borra el área de dibujo.  
  
##  <a name="colorref_to_d2dcolor"></a>CRenderTarget::COLORREF_TO_D2DCOLOR  
 Convierte valores de color y alfa GDI en el objeto D2D1_COLOR_F.  
  
```  
static D2D1_COLOR_F COLORREF_TO_D2DCOLOR(
    COLORREF color,  
    int nAlpha = 255);
```  
  
### <a name="parameters"></a>Parámetros  
 `color`  
 Valor RGB.  
  
 `nAlpha`  
  
### <a name="return-value"></a>Valor devuelto  
 Valor de D2D1_COLOR_F.  
  
##  <a name="createcompatiblerendertarget"></a>CRenderTarget::CreateCompatibleRenderTarget  
 Crea un nuevo destino de representación de mapa de bits para su uso durante intermedio dibujo fuera de la pantalla que es compatible con el destino de representación actual.  
  
```  
BOOL CreateCompatibleRenderTarget(
    CBitmapRenderTarget& bitmapTarget,  
    CD2DSizeF sizeDesired = CD2DSizeF(0., 0.), 
    CD2DSizeU sizePixelDesired = CD2DSizeU(0, 0), 
    D2D1_PIXEL_FORMAT* desiredFormat = NULL,  
    D2D1_COMPATIBLE_RENDER_TARGET_OPTIONS options = D2D1_COMPATIBLE_RENDER_TARGET_OPTIONS_NONE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bitmapTarget`  
 Cuando este método vuelve, contiene la dirección de un puntero a un nuevo destino de representación de mapa de bits. Este parámetro se pasa sin inicializar.  
  
 `sizeDesired`  
 El tamaño deseado del destino de representación nueva en los píxeles independientes del dispositivo si debe ser diferente del original de destino de representación, o NULL. Para obtener más información, vea la sección Comentarios.  
  
 `sizePixelDesired`  
 El tamaño deseado del destino de representación nueva en píxeles si debe ser diferente del original destino de representación, o NULL. Para obtener más información, vea la sección Comentarios.  
  
 `desiredFormat`  
 El formato de píxeles deseados y el modo alfa del nuevo destino de representación, o NULL. Si el formato de píxeles se establece en DXGI_FORMAT_UNKNOWN o si este parámetro es null, el nuevo destino de representación utiliza el mismo formato de píxel como destino de representación de la versión original. Si el modo alfa es D2D1_ALPHA_MODE_UNKNOWN o este parámetro es NULL, el modo alfa nuevo destino de representación predeterminado D2D1_ALPHA_MODE_PREMULTIPLIED. Para obtener información acerca de los formatos de píxel admitidos, vea formatos de píxel admitidos y modos de alfa.  
  
 `options`  
 Un valor que especifica si el nuevo destino de representación debe ser compatible con GDI.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE.  
  
##  <a name="crendertarget"></a>CRenderTarget::CRenderTarget  
 Construye un objeto CRenderTarget.  
  
```  
CRenderTarget();
```  
  
##  <a name="destroy"></a>CRenderTarget::Destroy  
 Elimina uno o más recursos  
  
```  
BOOL Destroy(BOOL bDeleteResources = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bDeleteResources`  
 Si bDeleteResources es TRUE, se destruirán automáticamente todos los recursos ubicados en m_lstResources.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE  
  
##  <a name="detach"></a>CRenderTarget::Detach  
 Separa la interfaz de destino de representación del objeto  
  
```  
ID2D1RenderTarget* Detach ();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a desasociar representar la interfaz de destino.  
  
##  <a name="drawbitmap"></a>CRenderTarget::DrawBitmap  
 Dibuja el texto con formato que describe el objeto IDWriteTextLayout especificado.  
  
```  
void DrawBitmap(
    CD2DBitmap* pBitmap,  
    const CD2DRectF& rectDest,  
    float fOpacity = 1.0,  
    D2D1_BITMAP_INTERPOLATION_MODE interpolationMode = D2D1_BITMAP_INTERPOLATION_MODE_LINEAR,  
    const CD2DRectF* pRectSrc = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pBitmap`  
 El mapa de bits para representar.  
  
 `rectDest`  
 El tamaño y la posición, en píxeles independientes del dispositivo en el espacio de coordenadas del destino de representación, del área a la que se dibuja el mapa de bits. Si el rectángulo no está bien ordenado, sin nada dibujado, pero el destino de representación no pase a un estado de error.  
  
 `fOpacity`  
 Un valor entre 0,0 f y 1.0f, ambos inclusive, que especifica un valor de opacidad para aplicar al mapa de bits; Este valor se multiplica por los valores alfabéticos de contenido del mapa de bits.  
  
 `interpolationMode`  
 El modo de interpolación para usar si el mapa de bits es escalar o girar la operación de dibujo.  
  
 `pRectSrc`  
 El tamaño y la posición, en píxeles independientes del dispositivo en el espacio de coordenadas del mapa de bits, del área de mapa de bits para dibujar.  
  
##  <a name="drawellipse"></a>CRenderTarget::DrawEllipse  
 Dibuja el contorno de la elipse especificada usando el estilo de trazo especificados.  
  
```  
void DrawEllipse(
    const CD2DEllipse& ellipse,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `ellipse`  
 La posición y el radio de la elipse para dibujar, en píxeles independientes del dispositivo.  
  
 `pBrush`  
 Pincel usado para dibujar el contorno de la elipse.  
  
 `fStrokeWidth`  
 El grosor del trazo de la elipse. El trazo se centra en el esquema de la elipse.  
  
 `strokeStyle`  
 El estilo de trazo para aplicar al esquema de la elipse, o NULL para pintar un trazo sólido.  
  
##  <a name="drawgeometry"></a>CRenderTarget::DrawGeometry  
 Dibuja el contorno de la geometría especificada usando el estilo de trazo especificados.  
  
```  
void DrawGeometry(
    CD2DGeometry* pGeometry,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pGeometry`  
 La geometría que se va a dibujar.  
  
 `pBrush`  
 El pincel que se usa para pintar el trazo de la geometría.  
  
 `fStrokeWidth`  
 El grosor del trazo de la geometría. El trazo se centra en el esquema de la geometría.  
  
 `strokeStyle`  
 El estilo de trazo para aplicar al esquema de la geometría, o NULL para pintar un trazo sólido.  
  
##  <a name="drawglyphrun"></a>CRenderTarget::DrawGlyphRun  
 Dibuja los glifos especificados.  
  
```  
void DrawGlyphRun(
    const CD2DPointF& ptBaseLineOrigin,  
    const DWRITE_GLYPH_RUN& glyphRun,  
    CD2DBrush* pForegroundBrush,  
    DWRITE_MEASURING_MODE measuringMode = DWRITE_MEASURING_MODE_NATURAL);
```  
  
### <a name="parameters"></a>Parámetros  
 `ptBaseLineOrigin`  
 El origen, en píxeles independientes del dispositivo, de línea de base de los glifos.  
  
 `glyphRun`  
 Los glifos para representar.  
  
 `pForegroundBrush`  
 Pincel usado para dibujar los glifos especificados.  
  
 `measuringMode`  
 Un valor que indica cómo se usan las métricas de glifo para medir el texto cuando se formatea. El valor predeterminado es DWRITE_MEASURING_MODE_NATURAL.  
  
##  <a name="drawline"></a>CRenderTarget::DrawLine  
 Dibuja una línea entre los puntos especificados utilizando el estilo de trazo especificados.  
  
```  
void DrawLine(
    const CD2DPointF& ptFrom,  
    const CD2DPointF& ptTo,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `ptFrom`  
 El punto inicial de la línea, en píxeles independientes del dispositivo.  
  
 `ptTo`  
 El punto final de la línea, en píxeles independientes del dispositivo.  
  
 `pBrush`  
 El pincel que se usa para pintar el trazo de la línea.  
  
 `fStrokeWidth`  
 Un valor mayor o igual que 0,0 f que especifica el ancho del trazo. Si no se especifica este parámetro, el valor predeterminado es 1, 0f. El trazo se centra en la línea.  
  
 `strokeStyle`  
 El estilo del trazo en paint, o NULL para dibujar una línea sólida.  
  
##  <a name="drawrectangle"></a>CRenderTarget::DrawRectangle  
 Dibuja el contorno de un rectángulo que tiene el estilo de trazo y las dimensiones especificadas.  
  
```  
void DrawRectangle(
    const CD2DRectF& rect,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `rect`  
 Las dimensiones del rectángulo va a dibujar, en píxeles independientes del dispositivo  
  
 `pBrush`  
 El pincel que se usa para pintar el trazo del rectángulo  
  
 `fStrokeWidth`  
 Un valor mayor o igual que 0,0 f que especifica el ancho del trazo del rectángulo. El trazo se centra en el esquema del rectángulo.  
  
 `strokeStyle`  
 El estilo del trazo en paint, o NULL para pintar un trazo sólido.  
  
##  <a name="drawroundedrectangle"></a>CRenderTarget::DrawRoundedRectangle  
 Dibuja el contorno del rectángulo redondeado especificado utilizando el estilo de trazo especificados.  
  
```  
void DrawRoundedRectangle(
    const CD2DRoundedRect& rectRounded,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `rectRounded`  
 Las dimensiones del rectángulo redondeado para dibujar, en píxeles independientes del dispositivo.  
  
 `pBrush`  
 Pincel usado para dibujar el contorno del rectángulo redondeado.  
  
 `fStrokeWidth`  
 Ancho del trazo del rectángulo redondeado. El trazo se centra en el esquema del rectángulo redondeado. El valor predeterminado es 1, 0f.  
  
 `strokeStyle`  
 El estilo de trazo el rectángulo redondeado, o NULL para pintar un trazo sólido. El valor predeterminado es NULL.  
  
##  <a name="drawtext"></a>CRenderTarget::DrawText  
 Dibuja el texto especificado con la información de formato proporcionada por un objeto IDWriteTextFormat.  
  
```  
void DrawText(
    const CString& strText,  
    const CD2DRectF& rect,  
    CD2DBrush* pForegroundBrush,  
    CD2DTextFormat* textFormat = NULL,  
    D2D1_DRAW_TEXT_OPTIONS options = D2D1_DRAW_TEXT_OPTIONS_NONE,  
    DWRITE_MEASURING_MODE measuringMode = DWRITE_MEASURING_MODE_NATURAL);
```  
  
### <a name="parameters"></a>Parámetros  
 `strText`  
 Un puntero a una matriz de caracteres Unicode para dibujar.  
  
 `rect`  
 El tamaño y la posición del área en la que se dibuja el texto.  
  
 `pForegroundBrush`  
 Pincel usado para dibujar el texto.  
  
 `textFormat`  
 Un objeto que describe el formato detalles del texto para dibujar, como la fuente, el tamaño de fuente y la dirección del flujo.  
  
 `options`  
 Un valor que indica si se debe ajustar el texto a los límites de píxeles y si debe recortarse el texto en el rectángulo de diseño. El valor predeterminado es D2D1_DRAW_TEXT_OPTIONS_NONE, que indica que el texto se debe ajustar a los límites de píxeles y no debe recortarse al rectángulo de diseño.  
  
 `measuringMode`  
 Un valor que indica cómo se usan las métricas de glifo para medir el texto cuando se formatea. El valor predeterminado es DWRITE_MEASURING_MODE_NATURAL.  
  
##  <a name="drawtextlayout"></a>CRenderTarget::DrawTextLayout  
 Dibuja el texto con formato que describe el objeto IDWriteTextLayout especificado.  
  
```  
void DrawTextLayout(
    const CD2DPointF& ptOrigin,  
    CD2DTextLayout* textLayout,  
    CD2DBrush* pBrushForeground,  
    D2D1_DRAW_TEXT_OPTIONS options = D2D1_DRAW_TEXT_OPTIONS_NONE);
```  
  
### <a name="parameters"></a>Parámetros  
 `ptOrigin`  
 El punto, que se describe en píxeles independientes del dispositivo, en el que se dibuja la esquina superior izquierda del texto descrito por textLayout.  
  
 `textLayout`  
 El texto con formato para dibujar. Se omiten los efectos de dibujo que no heredan de ID2D1Resource. Si hay efectos de dibujo que heredan de ID2D1Resource que no sean pinceles, este método produce un error y el destino de representación se coloca en un estado de error.  
  
 `pBrushForeground`  
 El pincel utilizado para pintar cualquier texto textLayout que no tiene todavía un pincel asociado a él como un efecto de dibujo (especificado mediante el método IDWriteTextLayout::SetDrawingEffect).  
  
 `options`  
 Un valor que indica si se debe ajustar el texto a los límites de píxeles y si debe recortarse el texto en el rectángulo de diseño. El valor predeterminado es D2D1_DRAW_TEXT_OPTIONS_NONE, que indica que el texto se debe ajustar a los límites de píxeles y no debe recortarse al rectángulo de diseño.  
  
##  <a name="enddraw"></a>CRenderTarget::EndDraw  
 Finaliza las operaciones de dibujo en el destino de representación e indica las etiquetas asociadas y el estado de error actual.  
  
```  
HRESULT EndDraw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se realiza correctamente, devuelve S_OK. En caso contrario, devuelve un código de error HRESULT.  
  
##  <a name="fillellipse"></a>CRenderTarget::FillEllipse  
 Pinta el interior de la elipse especificada.  
  
```  
void FillEllipse(
    const CD2DEllipse& ellipse,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>Parámetros  
 `ellipse`  
 La posición y el radio, en píxeles independientes del dispositivo, de la elipse para pintar.  
  
 `pBrush`  
 El pincel que se usa para pintar el interior de la elipse.  
  
##  <a name="fillgeometry"></a>CRenderTarget::FillGeometry  
 Pinta el interior de la geometría especificada.  
  
```  
void FillGeometry(
    CD2DGeometry* pGeometry,  
    CD2DBrush* pBrush,  
    CD2DBrush* pOpacityBrush = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pGeometry`  
 La geometría para pintar.  
  
 `pBrush`  
 El pincel que se usa para pintar la geometría 's interior.  
  
 `pOpacityBrush`  
 La máscara de opacidad para aplicar a la geometría; NULL para ninguna máscara de opacidad. Si se especifica una máscara de opacidad (el parámetro opacityBrush), pincel debe ser un ID2D1BitmapBrush que tiene sus modos de x y y ampliar establecidos en D2D1_EXTEND_MODE_CLAMP. Para obtener más información, vea la sección Comentarios.  
  
##  <a name="fillmesh"></a>CRenderTarget::FillMesh  
 Pinta el interior de la malla especificado.  
  
```  
void FillMesh(
    CD2DMesh* pMesh,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>Parámetros  
 `pMesh`  
 La malla para pintar.  
  
 `pBrush`  
 El pincel utilizado para pintar la malla.  
  
##  <a name="fillopacitymask"></a>CRenderTarget::FillOpacityMask  
 Se aplica la máscara de opacidad descrita por el mapa de bits especificado en un pincel y utiliza ese pincel para pintar una región de destino de representación.  
  
```  
void FillOpacityMask(
    CD2DBitmap* pOpacityMask,  
    CD2DBrush* pBrush,  
    D2D1_OPACITY_MASK_CONTENT content,  
    const CD2DRectF& rectDest,  
    const CD2DRectF& rectSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `pOpacityMask`  
 La posición y el radio, en píxeles independientes del dispositivo, de la elipse para pintar.  
  
 `pBrush`  
 El pincel utilizado para pintar la región de destino de representación especificada por destinationRectangle.  
  
 `content`  
 El tipo de contenido que contiene la máscara de opacidad. El valor se utiliza para determinar el espacio de color en el que se mezcla la máscara de opacidad.  
  
 `rectDest`  
 La región de destino de representación para pintar, en píxeles independientes del dispositivo.  
  
 `rectSrc`  
 La región del mapa de bits que se usará como la máscara de opacidad, en píxeles independientes del dispositivo.  
  
##  <a name="fillrectangle"></a>CRenderTarget::FillRectangle  
 Pinta el interior del rectángulo especificado.  
  
```  
void FillRectangle(
    const CD2DRectF& rect,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>Parámetros  
 `rect`  
 La dimensión del rectángulo va a pintar, en píxeles independientes del dispositivo.  
  
 `pBrush`  
 El pincel utilizado para dibujar el rectángulo de 's interior.  
  
##  <a name="fillroundedrectangle"></a>CRenderTarget::FillRoundedRectangle  
 Pinta el interior del rectángulo redondeado especificado.  
  
```  
void FillRoundedRectangle(
    const CD2DRoundedRect& rectRounded,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>Parámetros  
 `rectRounded`  
 Las dimensiones del rectángulo redondeado para pintar, en píxeles independientes del dispositivo.  
  
 `pBrush`  
 El pincel que se usa para pintar el interior del rectángulo redondeado.  
  
##  <a name="flush"></a>CRenderTarget::Flush  
 Ejecuta todos los comandos de dibujo pendientes.  
  
```  
void Flush(
    D2D1_TAG* tag1 = NULL,  
    D2D1_TAG* tag2 = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `tag1`  
 Contiene la etiqueta para las operaciones que ha causado errores o 0 si no hubiera ningún error de dibujo. Este parámetro se pasa sin inicializar.  
  
 `tag2`  
 Contiene la etiqueta para las operaciones que ha causado errores o 0 si no hubiera ningún error de dibujo. Este parámetro se pasa sin inicializar.  
  
##  <a name="getantialiasmode"></a>CRenderTarget::GetAntialiasMode  
 Recupera el modo de suavizado de contorno actual para las operaciones de dibujo sin texto.  
  
```  
D2D1_ANTIALIAS_MODE GetAntialiasMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Modo de suavizado de contorno actual para las operaciones de dibujo no de texto.  
  
##  <a name="getdpi"></a>CRenderTarget::GetDpi  
 Devuelve la representación de los puntos de destino por pulgada (PPP)  
  
```  
CD2DSizeF GetDpi() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntos de destino de representación por pulgada (PPP).  
  
##  <a name="getmaximumbitmapsize"></a>CRenderTarget::GetMaximumBitmapSize  
 Obtiene el tamaño máximo, en unidades de dependiente de dispositivo (píxeles), de cualquier dimensión de un mapa de bits compatible con el destino de representación  
  
```  
UINT32 GetMaximumBitmapSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño máximo, en píxeles, de cualquier dimensión de un mapa de bits compatible con el destino de representación  
  
##  <a name="getpixelformat"></a>CRenderTarget::GetPixelFormat  
 Recupera el modo de alfa y formato de píxel del destino de representación  
  
```  
D2D1_PIXEL_FORMAT GetPixelFormat() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de alfa y formato de píxel del destino de representación  
  
##  <a name="getpixelsize"></a>CRenderTarget::GetPixelSize  
 Devuelve el tamaño del destino de representación en píxeles del dispositivo  
  
```  
CD2DSizeU GetPixelSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño del destino de representación, en píxeles del dispositivo  
  
##  <a name="getrendertarget"></a>CRenderTarget::GetRenderTarget  
 Interfaz de ID2D1RenderTarget devuelve  
  
```  
ID2D1RenderTarget* GetRenderTarget();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1RenderTarget o NULL si el objeto todavía no está inicializado.  
  
##  <a name="getsize"></a>CRenderTarget::GetSize  
 Devuelve el tamaño del destino de representación en píxeles independientes del dispositivo  
  
```  
CD2DSizeF GetSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño actual del destino de representación, en píxeles independientes del dispositivo  
  
##  <a name="gettags"></a>CRenderTarget::GetTags  
 Obtiene la etiqueta para operaciones de dibujo subsiguientes.  
  
```  
void GetTags(
    D2D1_TAG* tag1 = NULL,  
    D2D1_TAG* tag2 = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `tag1`  
 Contiene la primera etiqueta para operaciones de dibujo subsiguientes. Este parámetro se pasa sin inicializar. Si se especifica NULL, no se recupera ningún valor para este parámetro.  
  
 `tag2`  
 Contiene la segunda etiqueta para operaciones de dibujo subsiguientes. Este parámetro se pasa sin inicializar. Si se especifica NULL, no se recupera ningún valor para este parámetro.  
  
##  <a name="gettextantialiasmode"></a>CRenderTarget::GetTextAntialiasMode  
 Obtiene el modo actual de suavizado de contorno para texto y las operaciones de dibujo del glifo.  
  
```  
D2D1_TEXT_ANTIALIAS_MODE GetTextAntialiasMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Modo actual de suavizado de contorno para texto y las operaciones de dibujo del glifo.  
  
##  <a name="gettextrenderingparams"></a>CRenderTarget::GetTextRenderingParams  
 Recupera las opciones de representación de texto actual del destino de representación.  
  
```  
void GetTextRenderingParams(IDWriteRenderingParams** textRenderingParams);
```  
  
### <a name="parameters"></a>Parámetros  
 `textRenderingParams`  
 Cuando este método vuelve, textRenderingParamscontains la dirección de un puntero para el destino de representación actual de la opciones de representación de texto.  
  
##  <a name="gettransform"></a>CRenderTarget::GetTransform  
 Aplica la transformación especificada en el destino de representación, reemplazando la transformación existente. Todas las operaciones de dibujo subsiguientes se producen en el espacio transformado.  
  
```  
void GetTransform(D2D1_MATRIX_3X2_F* transform);
```  
  
### <a name="parameters"></a>Parámetros  
 `transform`  
 Transformación que se aplicará en el destino de representación.  
  
##  <a name="issupported"></a>CRenderTarget::IsSupported  
 Indica si el destino de representación admite las propiedades especificadas  
  
```  
BOOL IsSupported(const D2D1_RENDER_TARGET_PROPERTIES& renderTargetProperties) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `renderTargetProperties`  
 Las propiedades de destino de representación para probar  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si las propiedades de destino de representación especificados son compatibles con este objetivo de presentación; en caso contrario, FALSE  
  
##  <a name="isvalid"></a>CRenderTarget::IsValid  
 Comprobaciones de validez de los recursos  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el recurso es válida; en caso contrario, FALSE.  
  
##  <a name="m_lstresources"></a>CRenderTarget::m_lstResources  
 Una lista de punteros a objetos CD2DResource.  
  
```  
CObList m_lstResources;  
```  
  
##  <a name="m_prendertarget"></a>CRenderTarget::m_pRenderTarget  
 Un puntero a un objeto ID2D1RenderTarget.  
  
```  
ID2D1RenderTarget* m_pRenderTarget;  
```  
  
##  <a name="m_ptextformatdefault"></a>CRenderTarget::m_pTextFormatDefault  
 Un puntero al objeto CD2DTextFormat que contiene un formato de texto predeterminado.  
  
```  
CD2DTextFormat* m_pTextFormatDefault;  
```  
  
##  <a name="operator_id2d1rendertarget_star"></a>CRenderTarget::operator ID2D1RenderTarget *  
 Interfaz de ID2D1RenderTarget devuelve  
  
```  
operator ID2D1RenderTarget*();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1RenderTarget o NULL si el objeto todavía no está inicializado.  
  
##  <a name="popaxisalignedclip"></a>CRenderTarget::PopAxisAlignedClip  
 Quita el último clip alineado con el eje del destino de representación. Después de que se llama a este método, el clip ya no se aplica a las operaciones de dibujo subsiguientes.  
  
```  
void PopAxisAlignedClip();
```  
  
##  <a name="poplayer"></a>CRenderTarget::PopLayer  
 Detiene la redirección de las operaciones de dibujo a la capa que se especifica mediante la última PushLayer llamar.  
  
```  
void PopLayer();
```  
  
##  <a name="pushaxisalignedclip"></a>CRenderTarget::PushAxisAlignedClip  
 Quita el último clip alineado con el eje del destino de representación. Después de que se llama a este método, el clip ya no se aplica a las operaciones de dibujo subsiguientes.  
  
```  
void PushAxisAlignedClip(
    const CD2DRectF& rectClip,  
    D2D1_ANTIALIAS_MODE mode = D2D1_ANTIALIAS_MODE_PER_PRIMITIVE);
```  
  
### <a name="parameters"></a>Parámetros  
 `rectClip`  
 El tamaño y la posición del área de recorte, en píxeles independientes del dispositivo.  
  
 `mode`  
 El modo de suavizado de contorno que se utiliza para dibujar los bordes del clip Rect que tiene límites de subpíxeles y combinar el clip con el contenido de la escena. La combinación se realiza una vez cuando se llama al método PopAxisAlignedClip y no se aplica a cada primitiva dentro de la capa.  
  
##  <a name="pushlayer"></a>CRenderTarget::PushLayer  
 Agrega la capa especificada en el destino de representación para que lo recibe todas las operaciones de dibujo subsiguientes hasta que se llama PopLayer.  
  
```  
void PushLayer(
    const D2D1_LAYER_PARAMETERS& layerParameters,  
    CD2DLayer& layer);
```  
  
### <a name="parameters"></a>Parámetros  
 `layerParameters`  
 Los límites de contenido, máscara geométrica, opacidad, máscara de opacidad y opciones de suavizado de contorno de la capa.  
  
 `layer`  
 La capa que recibe las operaciones de dibujo subsiguientes.  
  
##  <a name="restoredrawingstate"></a>CRenderTarget::RestoreDrawingState  
 Establece el estado de dibujo del destino de representación para el ID2D1DrawingStateBlock especificado.  
  
```  
void RestoreDrawingState(ID2D1DrawingStateBlock& drawingStateBlock);
```  
  
### <a name="parameters"></a>Parámetros  
 `drawingStateBlock`  
 El nuevo estado de dibujo el destino de representación.  
  
##  <a name="savedrawingstate"></a>CRenderTarget::SaveDrawingState  
 Guarda el estado de dibujo actual en el ID2D1DrawingStateBlock especificado.  
  
```  
void SaveDrawingState(ID2D1DrawingStateBlock& drawingStateBlock) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `drawingStateBlock`  
 Cuando este método vuelve, contiene el estado de dibujo actual del destino de representación. Este parámetro debe inicializarse antes de pasarlo al método.  
  
##  <a name="setantialiasmode"></a>CRenderTarget::SetAntialiasMode  
 Establece el modo de suavizado de contorno del destino de representación. El modo de suavizado de contorno se aplica a todas las operaciones de dibujo subsiguientes, sin incluir texto y las operaciones de dibujo del glifo.  
  
```  
void SetAntialiasMode(D2D1_ANTIALIAS_MODE antialiasMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `antialiasMode`  
 El modo de suavizado de contorno para futuras operaciones de dibujo.  
  
##  <a name="setdpi"></a>CRenderTarget::SetDpi  
 Establece los puntos por pulgada (PPP) del destino de representación.  
  
```  
void SetDpi(const CD2DSizeF& sizeDPI);
```  
  
### <a name="parameters"></a>Parámetros  
 `sizeDPI`  
 Un valor mayor o igual a cero que especifica el horizontal/verticalDPI del destino de representación.  
  
##  <a name="settags"></a>CRenderTarget::SetTags  
 Especifica una etiqueta para operaciones de dibujo subsiguientes.  
  
```  
void SetTags(
    D2D1_TAG tag1,  
    D2D1_TAG tag2);
```  
  
### <a name="parameters"></a>Parámetros  
 `tag1`  
 Una etiqueta para aplicar a las operaciones de dibujo subsiguientes.  
  
 `tag2`  
 Una etiqueta para aplicar a las operaciones de dibujo subsiguientes.  
  
##  <a name="settextantialiasmode"></a>CRenderTarget::SetTextAntialiasMode  
 Especifica el modo de suavizado de contorno para texto posterior y las operaciones de dibujo del glifo.  
  
```  
void SetTextAntialiasMode(D2D1_TEXT_ANTIALIAS_MODE textAntialiasMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `textAntialiasMode`  
 El modo de suavizado de contorno para texto posterior y las operaciones de dibujo del glifo.  
  
##  <a name="settextrenderingparams"></a>CRenderTarget::SetTextRenderingParams  
 Especifica las opciones de representación de texto que se aplicará a todo el texto posterior y las operaciones de dibujo del glifo.  
  
```  
void SetTextRenderingParams(IDWriteRenderingParams* textRenderingParams = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `textRenderingParams`  
 Las opciones de representación de texto que se aplicará a todo el texto posterior y glifo dibujo operaciones; Es NULL para borrar las opciones de representación de texto actual.  
  
##  <a name="settransform"></a>CRenderTarget::SetTransform  
 Aplica la transformación especificada en el destino de representación, reemplazando la transformación existente. Todas las operaciones de dibujo subsiguientes se producen en el espacio transformado.  
  
```  
void SetTransform(const D2D1_MATRIX_3X2_F* transform);  
void SetTransform(const D2D1_MATRIX_3X2_F& transform);
```  
  
### <a name="parameters"></a>Parámetros  
 `transform`  
 Transformación que se aplicará en el destino de representación.  
  
##  <a name="verifyresource"></a>CRenderTarget::VerifyResource  
 Comprueba la validez del objeto de CD2DResource; crea el objeto si aún no existe.  
  
```  
BOOL VerifyResource(CD2DResource* pResource);
```  
  
### <a name="parameters"></a>Parámetros  
 `pResource`  
 Puntero al objeto CD2DResource.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE es el objeto si es válido; en caso contrario, FALSE.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)
