---
title: CRectTracker (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRectTracker
- AFXEXT/CRectTracker
- AFXEXT/CRectTracker::CRectTracker
- AFXEXT/CRectTracker::AdjustRect
- AFXEXT/CRectTracker::Draw
- AFXEXT/CRectTracker::DrawTrackerRect
- AFXEXT/CRectTracker::GetHandleMask
- AFXEXT/CRectTracker::GetTrueRect
- AFXEXT/CRectTracker::HitTest
- AFXEXT/CRectTracker::NormalizeHit
- AFXEXT/CRectTracker::OnChangedRect
- AFXEXT/CRectTracker::SetCursor
- AFXEXT/CRectTracker::Track
- AFXEXT/CRectTracker::TrackRubberBand
- AFXEXT/CRectTracker::m_nHandleSize
- AFXEXT/CRectTracker::m_nStyle
- AFXEXT/CRectTracker::m_rect
- AFXEXT/CRectTracker::m_sizeMin
dev_langs:
- C++
helpviewer_keywords:
- CRectTracker [MFC], CRectTracker
- CRectTracker [MFC], AdjustRect
- CRectTracker [MFC], Draw
- CRectTracker [MFC], DrawTrackerRect
- CRectTracker [MFC], GetHandleMask
- CRectTracker [MFC], GetTrueRect
- CRectTracker [MFC], HitTest
- CRectTracker [MFC], NormalizeHit
- CRectTracker [MFC], OnChangedRect
- CRectTracker [MFC], SetCursor
- CRectTracker [MFC], Track
- CRectTracker [MFC], TrackRubberBand
- CRectTracker [MFC], m_nHandleSize
- CRectTracker [MFC], m_nStyle
- CRectTracker [MFC], m_rect
- CRectTracker [MFC], m_sizeMin
ms.assetid: 99caa7f2-3c0d-4a42-bbee-e5d1d342d4ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eff57e1fde0af6e794c2c47db7d1e31daf545715
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375913"
---
# <a name="crecttracker-class"></a>CRectTracker (clase)
Permite que un elemento para mostrar, mover y cambiar el tamaño de distintas maneras.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CRectTracker  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRectTracker::CRectTracker](#crecttracker)|Construye un objeto `CRectTracker`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRectTracker::AdjustRect](#adjustrect)|Se llama cuando se cambia el tamaño del rectángulo.|  
|[CRectTracker::Draw](#draw)|Representa el rectángulo.|  
|[CRectTracker::DrawTrackerRect](#drawtrackerrect)|Llamado cuando se dibuja el borde de un `CRectTracker` objeto.|  
|[CRectTracker::GetHandleMask](#gethandlemask)|Se llama para obtener la máscara de una `CRectTracker` controladores de tamaño del elemento.|  
|[CRectTracker::GetTrueRect](#gettruerect)|Devuelve el ancho y alto del rectángulo, incluidos los controladores de tamaño.|  
|[CRectTracker:: HitTest](#hittest)|Devuelve la posición actual del cursor relacionados con el `CRectTracker` objeto.|  
|[CRectTracker::NormalizeHit](#normalizehit)|Normaliza un código de prueba de posicionamiento.|  
|[CRectTracker::OnChangedRect](#onchangedrect)|Se llama cuando se cambia el tamaño o mover el rectángulo.|  
|[CRectTracker:: SetCursor](#setcursor)|Establece el cursor, dependiendo de su posición en el rectángulo.|  
|[CRectTracker::Track](#track)|Permite al usuario manipular el rectángulo.|  
|[CRectTracker:: TrackRubberBand](#trackrubberband)|Permite al usuario "banda elástica" la selección.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRectTracker::m_nHandleSize](#m_nhandlesize)|Determina el tamaño de los controladores de tamaño.|  
|[CRectTracker::m_nStyle](#m_nstyle)|Style(s) actual de la herramienta de seguimiento.|  
|[CRectTracker::m_rect](#m_rect)|Obtener posición actual (en píxeles) del rectángulo.|  
|[CRectTracker::m_sizeMin](#m_sizemin)|Determina el alto y el ancho del rectángulo mínimo.|  
  
## <a name="remarks"></a>Comentarios  
 `CRectTracker` no tiene una clase base.  
  
 Aunque la `CRectTracker` clase está diseñada para permitir al usuario interactuar con elementos OLE mediante el uso de una interfaz gráfica, su uso no está restringido a aplicaciones habilitadas para OLE. Se puede utilizar en cualquier parte se requiere una interfaz de usuario de este tipo.  
  
 `CRectTracker` bordes pueden ser sólidos o líneas de puntos. El elemento puede tiene un borde sombreado o se superpone con un patrón sombreado para indicar los diferentes Estados del elemento. Puede colocar ocho controladores de tamaño en la parte externa o interna borde del elemento. (Para obtener una explicación de los controladores de tamaño, vea [GetHandleMask](#gethandlemask).) Por último, un `CRectTracker` le permite cambiar la orientación de un elemento durante el cambio de tamaño.  
  
 Usar `CRectTracker`, construir un `CRectTracker` de objetos y especificar qué estados de visualización se inicializan. A continuación, puede usar esta interfaz para proporcionar al usuario información visual sobre el estado actual del elemento OLE asociado con el `CRectTracker` objeto.  
  
 Para obtener más información sobre el uso de `CRectTracker`, vea el artículo [seguimiento](../../mfc/trackers.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CRectTracker`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxext.h  
  
##  <a name="adjustrect"></a>  CRectTracker::AdjustRect  
 Llamado por el marco de trabajo cuando se cambia el tamaño del rectángulo de seguimiento mediante el uso de un controlador de tamaño.  
  
```  
virtual void AdjustRect(
    int nHandle,  
    LPRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `nHandle`  
 Índice del controlador que se utiliza.  
  
 `lpRect`  
 Puntero al tamaño actual del rectángulo. (El tamaño de un rectángulo viene dado por su alto y ancho).  
  
### <a name="remarks"></a>Comentarios  
 El comportamiento predeterminado de esta función permite la orientación del rectángulo cambiar solamente cuando `Track` y `TrackRubberBand` se llama con invertir permitido.  
  
 Reemplace esta función para controlar el ajuste del rectángulo de seguimiento durante una operación de arrastre. Un método consiste en ajustar las coordenadas especificadas por `lpRect` antes de devolver.  
  
 Características especiales que no son directamente compatibles con `CRectTracker`, como complemento a la cuadrícula o keep--relación de aspecto, puede implementarse mediante el reemplazo de esta función.  
  
##  <a name="crecttracker"></a>  CRectTracker::CRectTracker  
 Crea e inicializa un `CRectTracker` objeto.  
  
```  
CRectTracker();

 
CRectTracker(
    LPCRECT lpSrcRect,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpSrcRect`  
 Las coordenadas del objeto de rectángulo.  
  
 `nStyle`  
 Especifica el estilo de la `CRectTracker` objeto. Se admiten los estilos siguientes:  
  
- **CRectTracker::solidLine** Use una línea sólida para el borde del rectángulo.  
  
- **CRectTracker::dottedLine** usar una línea de puntos para el borde del rectángulo.  
  
- **CRectTracker::hatchedBorder** usan un modelo sombreado para el borde del rectángulo.  
  
- **CRectTracker::resizeInside** controladores que se encuentran dentro del rectángulo de tamaño.  
  
- **CRectTracker::resizeOutside** controladores que se encuentran fuera del rectángulo de tamaño.  
  
- **CRectTracker::hatchInside** Hatched patrón cubre todo el rectángulo.  
  
### <a name="remarks"></a>Comentarios  
 El constructor predeterminado inicializa los `CRectTracker` objeto con los valores de `lpSrcRect` e inicializa otros tamaños a valores predeterminados del sistema. Si el objeto se crea sin parámetros, el `m_rect` y `m_nStyle` miembros de datos están sin inicializados.  
  
##  <a name="draw"></a>  CRectTracker::Draw  
 Llame a esta función para dibujar el rectángulo exterior líneas y región interna.  
  
```  
void Draw(CDC* pDC) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Puntero al contexto de dispositivo en el que se va a dibujar.  
  
### <a name="remarks"></a>Comentarios  
 El estilo de la herramienta de seguimiento determina cómo se realiza el dibujo. Vea el constructor de `CRectTracker` para obtener más información sobre los estilos disponibles.  
  
##  <a name="drawtrackerrect"></a>  CRectTracker::DrawTrackerRect  
 Lo llama el marco cuando cambia la posición de la herramienta de seguimiento mientras dentro de la `Track` o `TrackRubberBand` función miembro.  
  
```  
virtual void DrawTrackerRect(
    LPCRECT lpRect,  
    CWnd* pWndClipTo,  
    CDC* pDC,  
    CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Puntero a la `RECT` que contiene el rectángulo para dibujar.  
  
 `pWndClipTo`  
 Puntero a la ventana que usará en el rectángulo de recorte.  
  
 `pDC`  
 Puntero al contexto de dispositivo en el que se va a dibujar.  
  
 `pWnd`  
 Puntero a la ventana en la que se producirá el dibujo.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada realiza una llamada a `CDC::DrawFocusRect`, que dibuja un rectángulo con puntos.  
  
 Reemplace esta función para proporcionar comentarios diferente durante la operación de seguimiento.  
  
##  <a name="gethandlemask"></a>  CRectTracker::GetHandleMask  
 El marco de trabajo llama a esta función miembro para recuperar la máscara para controladores de tamaño de un rectángulo.  
  
```  
virtual UINT GetHandleMask() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La máscara de una `CRectTracker` controladores de tamaño del elemento.  
  
### <a name="remarks"></a>Comentarios  
 Los controladores de tamaño aparecen en los lados y las esquinas del rectángulo y permiten al usuario controlar la forma y tamaño del rectángulo.  
  
 Un rectángulo tiene 8 controladores de tamaño con el número 0-7. Cada controlador de cambio de tamaño se representa mediante un poco en la máscara; el valor de ese bit es 2 ^ *n*, donde *n* es el número de identificador de cambio de tamaño. Bits 0-3 corresponden a los controladores de tamaño de la esquina, comenzando en la parte superior izquierda mover hacia la derecha. Desde la parte superior agujas del reloj de controladores de tamaño de bits corresponden al lado de 4-7. La ilustración siguiente muestra el cambio de tamaño de un rectángulo controla y sus correspondientes cambiar el tamaño de los números de identificador y los valores:  
  
 ![Cambiar el tamaño de los números de identificador](../../mfc/reference/media/vc35dp1.gif "vc35dp1")  
  
 La implementación predeterminada de **GetHandleMask** devuelve la máscara de bits para que aparezcan los controladores de tamaño. Si el único bit está activado, se dibujará el controlador de tamaño correspondiente.  
  
 Reemplace esta función miembro para mostrar u ocultar que controladores de tamaño indicado.  
  
##  <a name="gettruerect"></a>  CRectTracker::GetTrueRect  
 Llame a esta función para recuperar las coordenadas del rectángulo.  
  
```  
void GetTrueRect(LPRECT lpTrueRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpTrueRect`  
 Puntero a la `RECT` coordina la estructura que contiene el dispositivo de la `CRectTracker` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Las dimensiones del rectángulo incluyen el alto y ancho de los controladores de tamaño situado en el borde exterior. Al volver, `lpTrueRect` siempre es un rectángulo normalizado en coordenadas de dispositivo.  
  
##  <a name="hittest"></a>  CRectTracker:: HitTest  
 Llame a esta función para averiguar si el usuario tomó un controlador de tamaño.  
  
```  
int HitTest(CPoint point) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `point`  
 El punto, en coordenadas de dispositivo, para probar.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto se basa en el tipo enumerado **CRectTracker::TrackerHit** y puede tener uno de los siguientes valores:  
  
- **CRectTracker::hitNothing** -1  
  
- **CRectTracker::hitTopLeft** 0  
  
- **CRectTracker::hitTopRight** 1  
  
- **CRectTracker::hitBottomRight** 2  
  
- **CRectTracker::hitBottomLeft** 3  
  
- **CRectTracker::hitTop** 4  
  
- **CRectTracker::hitRight** 5  
  
- **CRectTracker::hitBottom** 6  
  
- **CRectTracker::hitLeft** 7  
  
- **CRectTracker::hitMiddle** 8  
  
##  <a name="m_nhandlesize"></a>  CRectTracker::m_nHandleSize  
 El tamaño, en píxeles, de la `CRectTracker` controladores de tamaño.  
  
```  
int m_nHandleSize;  
```  
  
### <a name="remarks"></a>Comentarios  
 Se inicializa con el valor predeterminado del sistema.  
  
##  <a name="m_rect"></a>  CRectTracker::m_rect  
 La posición actual del rectángulo en coordenadas de cliente (píxeles).  
  
```  
CRect m_rect;  
```  
  
##  <a name="m_sizemin"></a>  CRectTracker::m_sizeMin  
 El tamaño mínimo del rectángulo.  
  
```  
CSize m_sizeMin;  
```  
  
### <a name="remarks"></a>Comentarios  
 Ambos valores predeterminados, **cx** y **cy**, se calculan a partir el valor predeterminado del sistema para el ancho del borde. Este miembro de datos se utiliza únicamente por el `AdjustRect` función miembro.  
  
##  <a name="m_nstyle"></a>  CRectTracker::m_nStyle  
 Estilo actual del rectángulo.  
  
```  
UINT m_nStyle;  
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [CRectTracker::CRectTracker](#crecttracker) para obtener una lista de los estilos posibles.  
  
##  <a name="normalizehit"></a>  CRectTracker::NormalizeHit  
 Llame a esta función para convertir un identificador potencialmente invertido.  
  
```  
int NormalizeHit(int nHandle) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nHandle`  
 Identificador seleccionado por el usuario.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del identificador normalizado.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `CRectTracker::Track` o `CRectTracker::TrackRubberBand` se llama con invertir permitido, es posible que el rectángulo que se invierte en el eje x, el eje y o ambos. Cuando esto sucede, `HitTest` devolverá identificadores que también se invierten en relación con el rectángulo. Esto no es apropiado para la información del cursor dibujo porque los comentarios depende de la posición de la pantalla del rectángulo, no la parte de la estructura de datos del rectángulo que se va a modificar.  
  
##  <a name="onchangedrect"></a>  CRectTracker::OnChangedRect  
 Lo llama el marco siempre que el rectángulo rastreador ha cambiado durante una llamada a `Track`.  
  
```  
virtual void OnChangedRect(const CRect& rectOld);
```  
  
### <a name="parameters"></a>Parámetros  
 *rectOld*  
 Contiene las coordenadas de dispositivo antiguo de la `CRectTracker` objeto.  
  
### <a name="remarks"></a>Comentarios  
 En el momento de esta función se invoca, todos los comentarios que se dibuja con `DrawTrackerRect` se ha quitado. La implementación predeterminada de esta función no hace nada.  
  
 Reemplace esta función cuando desea realizar ninguna acción después de que el rectángulo se ha cambiado de tamaño.  
  
##  <a name="setcursor"></a>  CRectTracker:: SetCursor  
 Llame a esta función para cambiar la forma del cursor mientras se encuentra sobre el `CRectTracker` región del objeto.  
  
```  
BOOL SetCursor(
    CWnd* pWnd,  
    UINT nHitTest) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Apunta a la ventana que contiene actualmente el cursor.  
  
 `nHitTest`  
 Resultados de la prueba de posicionamiento anterior, desde la `WM_SETCURSOR` mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el posicionamiento anterior era el rectángulo Rastreador; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función desde dentro de la función de la ventana que controla la `WM_SETCURSOR` mensaje (normalmente `OnSetCursor`).  
  
##  <a name="track"></a>  CRectTracker::Track  
 Llame a esta función para mostrar la interfaz de usuario para cambiar el tamaño del rectángulo.  
  
```  
BOOL Track(
    CWnd* pWnd,  
    CPoint point,  
    BOOL bAllowInvert = FALSE,  
    CWnd* pWndClipTo = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 El objeto de ventana que contiene el rectángulo.  
  
 `point`  
 Coordenadas de dispositivo de la actual posición del mouse respecto al área de cliente.  
  
 `bAllowInvert`  
 Si **TRUE**, el rectángulo puede ser invertido a lo largo del eje x o eje y; en caso contrario **FALSE**.  
  
 `pWndClipTo`  
 La ventana que las operaciones de dibujo se ajustarán a. Si **NULL**, `pWnd` se utiliza como el rectángulo de recorte.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se presiona la tecla ESC, se detiene el proceso de seguimiento, el rectángulo que se almacenan en la herramienta de seguimiento no se modifica y se devuelve 0. Si se confirma el cambio, si mueve el mouse y soltar el botón primario del mouse, la nueva posición o el tamaño se registra en el rectángulo de la herramienta de seguimiento y se devuelve es distinto de cero.  
  
### <a name="remarks"></a>Comentarios  
 Esto se suele llamar desde dentro de la función de la aplicación que controla el `WM_LBUTTONDOWN` mensaje (normalmente `OnLButtonDown`).  
  
 Esta función capturará el mouse hasta que el usuario suelta el botón primario del mouse, presione la tecla ESC o presiona el botón secundario del mouse. Cuando el usuario mueve el cursor del mouse, los comentarios se actualizan mediante una llamada a `DrawTrackerRect` y `OnChangedRect`.  
  
 Si `bAllowInvert` es **TRUE**, se puede invertir el rectángulo de seguimiento en el eje x o el eje y.  
  
##  <a name="trackrubberband"></a>  CRectTracker:: TrackRubberBand  
 Llame a esta función para realizar la selección de la banda de goma.  
  
```  
BOOL TrackRubberBand(
    CWnd* pWnd,  
    CPoint point,  
    BOOL bAllowInvert = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 El objeto de ventana que contiene el rectángulo.  
  
 `point`  
 Coordenadas de dispositivo de la actual posición del mouse respecto al área de cliente.  
  
 `bAllowInvert`  
 Si **es TRUE,** el rectángulo puede ser invertido a lo largo del eje x o eje y; en caso contrario **FALSE**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se ha movido el mouse y el rectángulo no está vacío; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente se llama desde dentro de la función de la aplicación que controla el `WM_LBUTTONDOWN` mensaje (normalmente `OnLButtonDown`).  
  
 Esta función capturará el mouse hasta que el usuario suelta el botón primario del mouse, presione la tecla ESC o presiona el botón secundario del mouse. Cuando el usuario mueve el cursor del mouse, los comentarios se actualizan mediante una llamada a `DrawTrackerRect` y `OnChangedRect`.  
  
 Seguimiento se realiza con una selección de tipo de banda de goma partir del identificador inferior derecha. Si se puede invertir, el rectángulo se puede cambiar arrastrando ya sea una y a la izquierda o hacia abajo y la derecha.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC TRACKER](../../visual-cpp-samples.md)   
 [Ejemplo MFC DRAWCLI](../../visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clase COleResizeBar](../../mfc/reference/coleresizebar-class.md)   
 [CRect (clase)](../../atl-mfc-shared/reference/crect-class.md)
