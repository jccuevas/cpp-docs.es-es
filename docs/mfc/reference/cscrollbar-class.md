---
title: Clase CScrollBar | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CScrollBar
- AFXWIN/CScrollBar
- AFXWIN/CScrollBar::CScrollBar
- AFXWIN/CScrollBar::Create
- AFXWIN/CScrollBar::EnableScrollBar
- AFXWIN/CScrollBar::GetScrollBarInfo
- AFXWIN/CScrollBar::GetScrollInfo
- AFXWIN/CScrollBar::GetScrollLimit
- AFXWIN/CScrollBar::GetScrollPos
- AFXWIN/CScrollBar::GetScrollRange
- AFXWIN/CScrollBar::SetScrollInfo
- AFXWIN/CScrollBar::SetScrollPos
- AFXWIN/CScrollBar::SetScrollRange
- AFXWIN/CScrollBar::ShowScrollBar
dev_langs:
- C++
helpviewer_keywords:
- CScrollBar [MFC], CScrollBar
- CScrollBar [MFC], Create
- CScrollBar [MFC], EnableScrollBar
- CScrollBar [MFC], GetScrollBarInfo
- CScrollBar [MFC], GetScrollInfo
- CScrollBar [MFC], GetScrollLimit
- CScrollBar [MFC], GetScrollPos
- CScrollBar [MFC], GetScrollRange
- CScrollBar [MFC], SetScrollInfo
- CScrollBar [MFC], SetScrollPos
- CScrollBar [MFC], SetScrollRange
- CScrollBar [MFC], ShowScrollBar
ms.assetid: f3735ca5-73ea-46dc-918b-4d824c9fe47f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90f672cbeeee0c297e3d1deb6a6b5e83bffda3e8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372774"
---
# <a name="cscrollbar-class"></a>Clase CScrollBar
Proporciona la funcionalidad de un control de barra de desplazamiento de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CScrollBar : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CScrollBar::CScrollBar](#cscrollbar)|Construye un objeto `CScrollBar`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CScrollBar::Create](#create)|Crea la barra de desplazamiento de Windows y lo adjunta a la `CScrollBar` objeto.|  
|[CScrollBar::EnableScrollBar](#enablescrollbar)|Habilita o deshabilita una o ambas flechas de una barra de desplazamiento.|  
|[CScrollBar::GetScrollBarInfo](#getscrollbarinfo)|Recupera información sobre el desplazamiento de la barra usando un `SCROLLBARINFO` estructura.|  
|[CScrollBar::GetScrollInfo](#getscrollinfo)|Recupera información sobre la barra de desplazamiento.|  
|[CScrollBar::GetScrollLimit](#getscrolllimit)|Recupera el límite de la barra de desplazamiento|  
|[CScrollBar::GetScrollPos](#getscrollpos)|Recupera la posición actual de un cuadro de desplazamiento.|  
|[CScrollBar::GetScrollRange](#getscrollrange)|Recupera las posiciones actuales de la barra de desplazamiento mínimo y máximo de la barra de desplazamiento especificada.|  
|[CScrollBar::SetScrollInfo](#setscrollinfo)|Establece la información acerca de la barra de desplazamiento.|  
|[CScrollBar::SetScrollPos](#setscrollpos)|Establece la posición actual de un cuadro de desplazamiento.|  
|[CScrollBar::SetScrollRange](#setscrollrange)|Establece los valores de posición mínimo y máximo de la barra de desplazamiento especificada.|  
|[CScrollBar::ShowScrollBar](#showscrollbar)|Muestra u oculta una barra de desplazamiento.|  
  
## <a name="remarks"></a>Comentarios  
 Crear un control de barra de desplazamiento en dos pasos. En primer lugar, llame al constructor de `CScrollBar` para construir el `CScrollBar` de objeto y después llamar a la [crear](#create) función de miembro para crear el control de barra de desplazamiento de Windows y adjuntarlo a la `CScrollBar` objeto.  
  
 Si crea un `CScrollBar` objeto dentro de un cuadro de diálogo (a través de un recurso de cuadro de diálogo), el `CScrollBar` se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.  
  
 Si crea un `CScrollBar` de objeto dentro de una ventana, puede que también necesite destruirlo.  
  
 Si crea el `CScrollBar` del objeto en la pila, se destruye automáticamente. Si crea el `CScrollBar` objeto en el montón mediante el uso de la **nueva** función, se debe llamar a **eliminar** del objeto que se va a destruir cuando el usuario finalice la barra de desplazamiento de Windows.  
  
 Si asigna memoria en el `CScrollBar` objeto, invalide el `CScrollBar` destructor para deshacerse de las asignaciones.  
  
 Para obtener información relacionada sobre el uso de `CScrollBar`, consulte [controles](../../mfc/controls-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CScrollBar`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="create"></a>  CScrollBar::Create  
 Crea la barra de desplazamiento de Windows y lo adjunta a la `CScrollBar` objeto.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Especifica el desplazamiento estilo de barra. Aplicar cualquier combinación de [estilos de barra de desplazamiento](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles) a la barra de desplazamiento.  
  
 `rect`  
 Especifica el tamaño de la barra de desplazamiento y la posición. Puede ser un `RECT` estructura o un `CRect` objeto.  
  
 `pParentWnd`  
 Especifica el desplazamiento ventana de primaria de la barra, normalmente un `CDialog` objeto. No debe ser **NULL**.  
  
 `nID`  
 Id. de control de la barra de desplazamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Crear un `CScrollBar` objeto en dos pasos. En primer lugar, llame al constructor, que construye la `CScrollBar` objeto; a continuación, llamar a **crear**, que crea y se inicializa la barra de desplazamiento de Windows asociada y se adjunta a la `CScrollBar` objeto.  
  
 Aplique el siguiente [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) a una barra de desplazamiento:  
  
- **WS_CHILD** siempre  
  
- **WS_VISIBLE** normalmente  
  
- **WS_DISABLED** rara vez  
  
- **WS_GROUP** a controles de grupo  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]  
  
##  <a name="cscrollbar"></a>  CScrollBar::CScrollBar  
 Construye un objeto `CScrollBar`.  
  
```  
CScrollBar();
```  
  
### <a name="remarks"></a>Comentarios  
 Después de crear el objeto, llame a la **crear** función de miembro para crear e inicializar la barra de desplazamiento de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]  
  
##  <a name="enablescrollbar"></a>  CScrollBar::EnableScrollBar  
 Habilita o deshabilita una o ambas flechas de una barra de desplazamiento.  
  
```  
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```  
  
### <a name="parameters"></a>Parámetros  
 `nArrowFlags`  
 Especifica si se habilitan o deshabilitan las flechas de desplazamiento y las flechas están habilitadas o deshabilitadas. Este parámetro puede ser uno de los siguientes valores:  
  
- **ESB_ENABLE_BOTH** permite que ambas flechas de una barra de desplazamiento.  
  
- **ESB_DISABLE_LTUP** deshabilita la flecha izquierda de una barra de desplazamiento horizontal o la flecha arriba de una barra de desplazamiento vertical.  
  
- **ESB_DISABLE_RTDN** deshabilita la flecha derecha de una barra de desplazamiento horizontal o en la flecha abajo de una barra de desplazamiento vertical.  
  
- **ESB_DISABLE_BOTH** deshabilita ambas flechas de una barra de desplazamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si las flechas se habilitan o deshabilitan según lo especificado; en caso contrario, 0, lo que indica que las flechas ya están en el estado solicitado o que se produjo un error.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CScrollBar::SetScrollRange](#setscrollrange).  
  
##  <a name="getscrollbarinfo"></a>  CScrollBar::GetScrollBarInfo  
 Recupera la información que la **SCROLLBARINFO** estructura se mantiene sobre una barra de desplazamiento.  
  
```  
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *pScrollInfo*  
 Un puntero a la [SCROLLBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb787535) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la [SBM_SCROLLBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb787545) de mensajes, como se describe en el SDK de Windows.  
  
##  <a name="getscrollinfo"></a>  CScrollBar::GetScrollInfo  
 Recupera la información que la estructura `SCROLLINFO` mantiene sobre una barra de desplazamiento.  
  
```  
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,  
    UINT nMask = SIF_ALL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpScrollInfo`  
 Un puntero a un [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) estructura. Consulte el SDK de Windows para obtener más información acerca de esta estructura.  
  
 `nMask`  
 Especifica los parámetros de la barra de desplazamiento para recuperar. Un uso típico, SIF_ALL, especifica una combinación de SIF_PAGE, SIF_POS, SIF_TRACKPOS y SIF_RANGE. Consulte `SCROLLINFO` para obtener más información sobre los valores de nMask.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el mensaje recupera todos los valores, el valor devuelto es **TRUE**. En caso contrario, es **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 `GetScrollInfo` permite a las aplicaciones utilizar posiciones de desplazamiento de 32 bits.  
  
 El [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) estructura contiene información sobre una barra de desplazamiento, incluidos los valores mínimo y máximo de desplazamiento posiciones, el tamaño de página y la posición del cuadro de desplazamiento (control). Vea el `SCROLLINFO` tema de estructura en el SDK de Windows para obtener más información acerca de cómo cambiar los valores predeterminados de la estructura.  
  
 Controladores que indican la posición de la barra de desplazamiento, de mensaje de las ventanas de MFC [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) y [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll), proporcionar solo 16 bits de datos de posición. `GetScrollInfo` y `SetScrollInfo` proporcionar 32 bits de barra de datos de la posición de desplazamiento. Por lo tanto, una aplicación puede llamar a `GetScrollInfo` al procesar cualquiera `CWnd::OnHScroll` o `CWnd::OnVScroll` para obtener datos de posición de barra de desplazamiento de 32 bits.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).  
  
##  <a name="getscrolllimit"></a>  CScrollBar::GetScrollLimit  
 Recupera el valor máximo de la barra de desplazamiento de la posición de desplazamiento.  
  
```  
int GetScrollLimit();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Especifica la posición máxima de una barra de desplazamiento si se realiza correctamente; en caso contrario es 0.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).  
  
##  <a name="getscrollpos"></a>  CScrollBar::GetScrollPos  
 Recupera la posición actual de un cuadro de desplazamiento.  
  
```  
int GetScrollPos() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Especifica la posición actual del cuadro de desplazamiento si se realiza correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 La posición actual es un valor relativo que depende del intervalo de desplazamiento actual. Por ejemplo, si el intervalo de desplazamiento es de 100 a 200 y el cuadro de desplazamiento está en medio de la barra, la posición actual es 150.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).  
  
##  <a name="getscrollrange"></a>  CScrollBar::GetScrollRange  
 Copia las posiciones actuales de la barra de desplazamiento mínimo y máximo de la barra de desplazamiento especificada en las ubicaciones especificadas por `lpMinPos` y `lpMaxPos`.  
  
```  
void GetScrollRange(
    LPINT lpMinPos,  
    LPINT lpMaxPos) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpMinPos`  
 Señala a la variable de entero que se va a recibir la posición de mínimo.  
  
 `lpMaxPos`  
 Señala a la variable de entero que se va a recibir la posición máxima.  
  
### <a name="remarks"></a>Comentarios  
 El intervalo predeterminado para un control de barra de desplazamiento está vacío (ambos valores son 0).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).  
  
##  <a name="setscrollinfo"></a>  CScrollBar::SetScrollInfo  
 Establece la información que la `SCROLLINFO` estructura se mantiene sobre una barra de desplazamiento.  
  
```  
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpScrollInfo`  
 Un puntero a un [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) estructura.  
  
 `bRedraw`  
 Especifica si se debe volver a dibujar la barra de desplazamiento para reflejar la nueva información. Si `bRedraw` es **TRUE**, se vuelve a dibujar la barra de desplazamiento. Si es **FALSE**, no se vuelve a dibujar. Se vuelve a dibujar la barra de desplazamiento de forma predeterminada.  
  
### <a name="return-value"></a>Valor devuelto  
 Si tiene éxito, el valor devuelto es **TRUE**. En caso contrario, es **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Debe proporcionar los valores requeridos por la `SCROLLINFO` parámetros, incluidos los valores de marca de la estructura.  
  
 El `SCROLLINFO` estructura contiene información sobre una barra de desplazamiento, incluidos los valores mínimo y máximo de desplazamiento posiciones, el tamaño de página y la posición del cuadro de desplazamiento (control). Consulte la [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) tema de estructura en el SDK de Windows para obtener más información acerca de cómo cambiar los valores predeterminados de la estructura.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]  
  
##  <a name="setscrollpos"></a>  CScrollBar::SetScrollPos  
 Establece la posición actual de un cuadro de desplazamiento al especificado por `nPos` y, si se especifica, vuelve a dibujar la barra de desplazamiento para reflejar la nueva posición.  
  
```  
int SetScrollPos(
    int nPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `nPos`  
 Especifica la nueva posición del cuadro de desplazamiento. Debe estar dentro del intervalo de desplazamiento.  
  
 `bRedraw`  
 Especifica si se debe volver a dibujar la barra de desplazamiento para reflejar la nueva posición. Si `bRedraw` es **TRUE**, se vuelve a dibujar la barra de desplazamiento. Si es **FALSE**, no se vuelve a dibujar. Se vuelve a dibujar la barra de desplazamiento de forma predeterminada.  
  
### <a name="return-value"></a>Valor devuelto  
 Especifica la posición anterior del cuadro de desplazamiento si se realiza correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Establecer `bRedraw` a **FALSE** cada vez que una llamada subsiguiente a otra función para evitar la barra de desplazamiento que se vuelve a dibujarse dos veces dentro de un intervalo corto se volverá a dibujar la barra de desplazamiento.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CScrollBar::SetScrollRange](#setscrollrange).  
  
##  <a name="setscrollrange"></a>  CScrollBar::SetScrollRange  
 Establece los valores de posición mínimo y máximo de la barra de desplazamiento especificada.  
  
```  
void SetScrollRange(
    int nMinPos,  
    int nMaxPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `nMinPos`  
 Especifica la posición de desplazamiento mínimo.  
  
 `nMaxPos`  
 Especifica el máximo de la posición de desplazamiento.  
  
 `bRedraw`  
 Especifica si se debe volver a dibujar la barra de desplazamiento para reflejar el cambio. Si `bRedraw` es **TRUE**, se vuelve a dibujar la barra de desplazamiento; si **FALSE**, no se vuelve a dibujar. Se vuelve a dibujar de forma predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 Establecer `nMinPos` y `nMaxPos` en 0 para ocultar las barras de desplazamiento estándar.  
  
 No llame a esta función para ocultar una barra de desplazamiento al procesar un mensaje de notificación de la barra de desplazamiento.  
  
 Si una llamada a `SetScrollRange` sigue inmediatamente a una llamada a la `SetScrollPos` función miembro, establezca `bRedraw` en `SetScrollPos` en 0 para evitar que la barra de desplazamiento que se vuelve a dibujarse dos veces.  
  
 La diferencia entre los valores especificados por `nMinPos` y `nMaxPos` no debe ser superior a 32.767. El intervalo predeterminado para un control de barra de desplazamiento está vacío (ambos `nMinPos` y `nMaxPos` son 0).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]  
  
##  <a name="showscrollbar"></a>  CScrollBar::ShowScrollBar  
 Muestra u oculta una barra de desplazamiento.  
  
```  
void ShowScrollBar(BOOL bShow = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bShow`  
 Especifica si se muestra o se oculta la barra de desplazamiento. Si este parámetro es **TRUE**, se muestra la barra de desplazamiento; en caso contrario, está oculta.  
  
### <a name="remarks"></a>Comentarios  
 Una aplicación no debería llamar a esta función para ocultar una barra de desplazamiento al procesar un mensaje de notificación de la barra de desplazamiento.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CScrollBar::Create](#create).  
  
## <a name="see-also"></a>Vea también  
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Clase CButton](../../mfc/reference/cbutton-class.md)   
 [CComboBox (clase)](../../mfc/reference/ccombobox-class.md)   
 [Clase CEdit](../../mfc/reference/cedit-class.md)   
 [CListBox (clase)](../../mfc/reference/clistbox-class.md)   
 [Clase CStatic](../../mfc/reference/cstatic-class.md)   
 [CDialog (clase)](../../mfc/reference/cdialog-class.md)
