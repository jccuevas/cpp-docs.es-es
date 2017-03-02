---
title: CRectTracker (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRectTracker
dev_langs:
- C++
helpviewer_keywords:
- displaying items
- CRectTracker class
- resizing items
ms.assetid: 99caa7f2-3c0d-4a42-bbee-e5d1d342d4ee
caps.latest.revision: 23
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
ms.openlocfilehash: 444eab5969339cf2a3d5797807eae3dcad32a694
ms.lasthandoff: 02/24/2017

---
# <a name="crecttracker-class"></a>CRectTracker (clase)
Permite que un elemento Mostrar, mover y cambiar el tamaño de distintas maneras.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CRectTracker  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRectTracker::CRectTracker](#crecttracker)|Construye un objeto `CRectTracker`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRectTracker::AdjustRect](#adjustrect)|Se llama cuando se cambia el tamaño del rectángulo.|  
|[CRectTracker::Draw](#draw)|Representa el rectángulo.|  
|[CRectTracker::DrawTrackerRect](#drawtrackerrect)|Llamado cuando se dibuja el borde de un `CRectTracker` objeto.|  
|[CRectTracker::GetHandleMask](#gethandlemask)|Se llama para obtener la máscara de una `CRectTracker`controladores de tamaño del elemento.|  
|[CRectTracker::GetTrueRect](#gettruerect)|Devuelve el ancho y alto del rectángulo, incluidos los controladores de tamaño.|  
|[CRectTracker:: HitTest](#hittest)|Devuelve la posición actual del cursor relacionados con el `CRectTracker` objeto.|  
|[CRectTracker::NormalizeHit](#normalizehit)|Normaliza un código de prueba de posicionamiento.|  
|[CRectTracker::OnChangedRect](#onchangedrect)|Se llama cuando se cambia de tamaño o mover el rectángulo.|  
|[CRectTracker:: SetCursor](#setcursor)|Establece el cursor, dependiendo de su posición sobre el rectángulo.|  
|[CRectTracker::Track](#track)|Permite al usuario manipular el rectángulo.|  
|[CRectTracker:: TrackRubberBand](#trackrubberband)|Permite al usuario "banda elástica" en la selección.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRectTracker::m_nHandleSize](#m_nhandlesize)|Determina el tamaño de los controladores de tamaño.|  
|[CRectTracker::m_nStyle](#m_nstyle)|Style(s) actual de la herramienta de seguimiento.|  
|[CRectTracker::m_rect](#m_rect)|Posición actual (en píxeles) del rectángulo.|  
|[CRectTracker::m_sizeMin](#m_sizemin)|Determina el alto y el ancho del rectángulo.|  
  
## <a name="remarks"></a>Comentarios  
 `CRectTracker`no tiene una clase base.  
  
 Aunque la `CRectTracker` clase está diseñada para permitir al usuario interactuar con elementos OLE mediante una interfaz gráfica, su uso no se limita a aplicaciones compatibles con OLE. Se puede utilizar cualquier interfaz de usuario es necesaria.  
  
 `CRectTracker`bordes pueden ser sólidos o líneas de puntos. El elemento puede con un borde sombreado o se superpone con un patrón sombreado para indicar los distintos Estados del elemento. Puede colocar ocho controladores de tamaño en el exterior o interior borde del elemento. (Para obtener una explicación de los controladores de tamaño, vea [GetHandleMask](#gethandlemask).) Por último, un `CRectTracker` le permite cambiar la orientación de un elemento de tamaño.  
  
 Usar `CRectTracker`, construir un `CRectTracker` de objetos y especificar qué estados de visualización se inicializan. A continuación, puede utilizar esta interfaz para proporcionar información visual al usuario sobre el estado actual del elemento OLE asociado con el `CRectTracker` objeto.  
  
 Para obtener más información sobre el uso de `CRectTracker`, vea el artículo [seguidores](../../mfc/trackers.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CRectTracker`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxext.h  
  
##  <a name="a-nameadjustrecta--crecttrackeradjustrect"></a><a name="adjustrect"></a>CRectTracker::AdjustRect  
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
 El comportamiento predeterminado de esta función permite la orientación del rectángulo cambiar sólo cuando `Track` y `TrackRubberBand` se llaman con invertir permitido.  
  
 Reemplazar esta función para controlar el ajuste del rectángulo de seguimiento durante una operación de arrastre. Un método consiste en ajustar las coordenadas especificadas por `lpRect` antes de devolver.  
  
 Características especiales que no son directamente compatibles con `CRectTracker`, como complemento a la cuadrícula o keep--relación de aspecto, puede implementarse por reemplazar esta función.  
  
##  <a name="a-namecrecttrackera--crecttrackercrecttracker"></a><a name="crecttracker"></a>CRectTracker::CRectTracker  
 Crea e inicializa un `CRectTracker` objeto.  
  
```  
CRectTracker();

 
CRectTracker(
    LPCRECT lpSrcRect,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpSrcRect`  
 Las coordenadas del objeto rectángulo.  
  
 `nStyle`  
 Especifica el estilo de la `CRectTracker` objeto. Se admiten los siguientes estilos:  
  
- **CRectTracker::solidLine** Use una línea sólida para el borde del rectángulo.  
  
- **CRectTracker::dottedLine** utilizar una línea de puntos para el borde del rectángulo.  
  
- **CRectTracker::hatchedBorder** usan un modelo sombreado del borde del rectángulo.  
  
- **CRectTracker::resizeInside** controladores que se encuentra dentro del rectángulo de tamaño.  
  
- **CRectTracker::resizeOutside** controladores ubicados fuera del rectángulo de tamaño.  
  
- **CRectTracker::hatchInside** Hatched patrón cubre todo el rectángulo.  
  
### <a name="remarks"></a>Comentarios  
 El constructor predeterminado inicializa los `CRectTracker` objeto con los valores de `lpSrcRect` e inicializa otros tamaños de los valores predeterminados del sistema. Si el objeto se crea sin parámetros, el `m_rect` y `m_nStyle` son sin inicializar miembros de datos.  
  
##  <a name="a-namedrawa--crecttrackerdraw"></a><a name="draw"></a>CRectTracker::Draw  
 Llame a esta función para dibujar el rectángulo exterior líneas y región interna.  
  
```  
void Draw(CDC* pDC) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Puntero al contexto de dispositivo en el que se va a dibujar.  
  
### <a name="remarks"></a>Comentarios  
 El estilo del rastreador determina cómo se realiza el dibujo. Vea el constructor de `CRectTracker` para obtener más información sobre los estilos disponibles.  
  
##  <a name="a-namedrawtrackerrecta--crecttrackerdrawtrackerrect"></a><a name="drawtrackerrect"></a>CRectTracker::DrawTrackerRect  
 Llamado por el marco cuando cambia la posición de la herramienta de seguimiento mientras dentro de la `Track` o `TrackRubberBand` función miembro.  
  
```  
virtual void DrawTrackerRect(
    LPCRECT lpRect,  
    CWnd* pWndClipTo,  
    CDC* pDC,  
    CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Puntero a la `RECT` que contiene el rectángulo que se va a dibujar.  
  
 `pWndClipTo`  
 Puntero a la ventana que se utilizará en el rectángulo de recorte.  
  
 `pDC`  
 Puntero al contexto de dispositivo en el que se va a dibujar.  
  
 `pWnd`  
 Puntero a la ventana en la que se producirá el dibujo.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada realiza una llamada a `CDC::DrawFocusRect`, que dibuja un rectángulo con puntos.  
  
 Reemplazar esta función para proporcionar comentarios diferente durante la operación de seguimiento.  
  
##  <a name="a-namegethandlemaska--crecttrackergethandlemask"></a><a name="gethandlemask"></a>CRectTracker::GetHandleMask  
 El marco de trabajo llama a esta función miembro para recuperar la máscara para controladores de tamaño de un rectángulo.  
  
```  
virtual UINT GetHandleMask() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La máscara de una `CRectTracker` controladores de tamaño del elemento.  
  
### <a name="remarks"></a>Comentarios  
 Los controladores de tamaño aparecen en los lados y las esquinas del rectángulo y permiten al usuario controlar la forma y tamaño del rectángulo.  
  
 Un rectángulo tiene controladores de tamaño 8 numerados de 0 a 7. Cada controlador de tamaño se representa mediante un poco en la máscara; el valor de ese bit es 2 ^ *n*, donde *n* es el número de identificador de cambio de tamaño. Bits 0 – 3 corresponden a los controladores de tamaño de esquina, comenzando en la parte superior izquierda de mover hacia la derecha. Desde la parte superior agujas de controladores de tamaño de bits corresponden al lado de 4 a 7. La siguiente ilustración muestra la controla el tamaño de un rectángulo y sus correspondientes cambiar el tamaño de los números de identificación y valores:  
  
 ![Cambiar el tamaño de los números de identificador](../../mfc/reference/media/vc35dp1.gif "vc35dp1")  
  
 La implementación predeterminada de **GetHandleMask** devuelve la máscara de bits para que aparezcan los manipuladores de cambio de tamaño. Si el único bit está activado, se dibuja el controlador de tamaño correspondiente.  
  
 Reemplace esta función miembro para mostrar u ocultar que controladores de tamaño indicado.  
  
##  <a name="a-namegettruerecta--crecttrackergettruerect"></a><a name="gettruerect"></a>CRectTracker::GetTrueRect  
 Llame a esta función para recuperar las coordenadas del rectángulo.  
  
```  
void GetTrueRect(LPRECT lpTrueRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpTrueRect`  
 Puntero a la `RECT` coordina la estructura que contiene el dispositivo de la `CRectTracker` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Las dimensiones del rectángulo incluyen el alto y ancho de los controladores de tamaño situado en el borde exterior. Al volver, `lpTrueRect` siempre es un rectángulo normalizado en coordenadas de dispositivo.  
  
##  <a name="a-namehittesta--crecttrackerhittest"></a><a name="hittest"></a>CRectTracker:: HitTest  
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
  
##  <a name="a-namemnhandlesizea--crecttrackermnhandlesize"></a><a name="m_nhandlesize"></a>CRectTracker::m_nHandleSize  
 El tamaño, en píxeles, de la `CRectTracker` controladores de tamaño.  
  
```  
int m_nHandleSize;  
```  
  
### <a name="remarks"></a>Comentarios  
 Se inicializa con el valor predeterminado del sistema.  
  
##  <a name="a-namemrecta--crecttrackermrect"></a><a name="m_rect"></a>CRectTracker::m_rect  
 La posición actual del rectángulo en coordenadas de cliente (píxeles).  
  
```  
CRect m_rect;  
```  
  
##  <a name="a-namemsizemina--crecttrackermsizemin"></a><a name="m_sizemin"></a>CRectTracker::m_sizeMin  
 El tamaño mínimo del rectángulo.  
  
```  
CSize m_sizeMin;  
```  
  
### <a name="remarks"></a>Comentarios  
 Los valores predeterminados, **cx** y **cy**, se calcula el valor del sistema predeterminado para el ancho del borde. Este miembro de datos se utiliza únicamente por el `AdjustRect` función miembro.  
  
##  <a name="a-namemnstylea--crecttrackermnstyle"></a><a name="m_nstyle"></a>CRectTracker::m_nStyle  
 Estilo actual del rectángulo.  
  
```  
UINT m_nStyle;  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [CRectTracker::CRectTracker](#crecttracker) para obtener una lista de los estilos posibles.  
  
##  <a name="a-namenormalizehita--crecttrackernormalizehit"></a><a name="normalizehit"></a>CRectTracker::NormalizeHit  
 Llame a esta función para convertir un identificador potencialmente invertido.  
  
```  
int NormalizeHit(int nHandle) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nHandle`  
 Identificador seleccionado por el usuario.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del controlador normalizado.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `CRectTracker::Track` o `CRectTracker::TrackRubberBand` se llama con invertir permitido, es posible que el rectángulo que se invierte en el eje x, el eje y o ambos. Cuando esto sucede, `HitTest` devolverá los identificadores que también se invierten en relación con el rectángulo. Esto es apropiado para la información del cursor dibujo porque los comentarios depende de la posición de la pantalla del rectángulo, no la parte de la estructura de datos del rectángulo que se va a modificar.  
  
##  <a name="a-nameonchangedrecta--crecttrackeronchangedrect"></a><a name="onchangedrect"></a>CRectTracker::OnChangedRect  
 Llamado por el marco, siempre que el rectángulo rastreador ha cambiado durante una llamada a `Track`.  
  
```  
virtual void OnChangedRect(const CRect& rectOld);
```  
  
### <a name="parameters"></a>Parámetros  
 *rectOld*  
 Contiene las coordenadas de dispositivo antiguo de la `CRectTracker` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se llama a esta función, todos los comentarios que se dibuja con `DrawTrackerRect` se ha quitado. La implementación predeterminada de esta función no hace nada.  
  
 Reemplace esta función si desea realizar cualquier acción después de que ha cambiado el tamaño del rectángulo.  
  
##  <a name="a-namesetcursora--crecttrackersetcursor"></a><a name="setcursor"></a>CRectTracker:: SetCursor  
 Llame a esta función para cambiar la forma del cursor mientras está sobre el `CRectTracker` región del objeto.  
  
```  
BOOL SetCursor(
    CWnd* pWnd,  
    UINT nHitTest) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Apunta a la ventana que contiene actualmente el cursor.  
  
 `nHitTest`  
 Resultados de la prueba de posicionamiento anterior desde el `WM_SETCURSOR` mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el resultado anterior era el rectángulo Rastreador; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función desde dentro de la función de la ventana que controla la `WM_SETCURSOR` mensaje (normalmente `OnSetCursor`).  
  
##  <a name="a-nametracka--crecttrackertrack"></a><a name="track"></a>CRectTracker::Track  
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
 Coordenadas de dispositivo de la posición actual del mouse relativa al área de cliente.  
  
 `bAllowInvert`  
 Si **TRUE**, el rectángulo puede ser invertido a lo largo del eje x o el eje y; en caso contrario **FALSE**.  
  
 `pWndClipTo`  
 La ventana de las operaciones de dibujo se ajustarán a. Si **NULL**, `pWnd` se utiliza como el rectángulo de recorte.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se presiona la tecla ESC, se detiene el proceso de seguimiento, el rectángulo que se almacenan en el rastreador no se modifica y se devuelve 0. Si se confirma el cambio, al mover el mouse y soltar el botón primario del mouse, la nueva posición o el tamaño se registra en el rectángulo de la herramienta de seguimiento y se devuelve es distinto de cero.  
  
### <a name="remarks"></a>Comentarios  
 Esto se suele llamar desde dentro de la función de la aplicación que controla el `WM_LBUTTONDOWN` mensaje (normalmente `OnLButtonDown`).  
  
 Esta función volverá a capturar el mouse hasta que el usuario suelta el botón primario del mouse, presione la tecla ESC o presiona el botón secundario del mouse. Cuando el usuario mueve el cursor del mouse, los comentarios se actualizan mediante una llamada a `DrawTrackerRect` y `OnChangedRect`.  
  
 Si `bAllowInvert` es **TRUE**, se puede invertir el rectángulo de seguimiento en el eje x o el eje y.  
  
##  <a name="a-nametrackrubberbanda--crecttrackertrackrubberband"></a><a name="trackrubberband"></a>CRectTracker:: TrackRubberBand  
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
 Coordenadas de dispositivo de la posición actual del mouse relativa al área de cliente.  
  
 `bAllowInvert`  
 Si **es TRUE,** el rectángulo puede ser invertido a lo largo del eje x o el eje y; en caso contrario **FALSE**.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se ha movido el mouse y el rectángulo no está vacío; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente se llama desde dentro de la función de la aplicación que controla el `WM_LBUTTONDOWN` mensaje (normalmente `OnLButtonDown`).  
  
 Esta función volverá a capturar el mouse hasta que el usuario suelta el botón primario del mouse, presione la tecla ESC o presiona el botón secundario del mouse. Cuando el usuario mueve el cursor del mouse, los comentarios se actualizan mediante una llamada a `DrawTrackerRect` y `OnChangedRect`.  
  
 Seguimiento se realiza con una selección de tipo de banda de goma desde el controlador inferior derecha. Si se puede invertir, el rectángulo puede ajustarse arrastrando ya sea de y a la izquierda o hacia abajo y la derecha.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC TRACKER](../../visual-cpp-samples.md)   
 [Ejemplo de MFC DRAWCLI](../../visual-cpp-samples.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase COleResizeBar](../../mfc/reference/coleresizebar-class.md)   
 [CRect (clase)](../../atl-mfc-shared/reference/crect-class.md)

