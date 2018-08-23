---
title: CReBarCtrl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CReBarCtrl
- AFXCMN/CReBarCtrl
- AFXCMN/CReBarCtrl::CReBarCtrl
- AFXCMN/CReBarCtrl::BeginDrag
- AFXCMN/CReBarCtrl::Create
- AFXCMN/CReBarCtrl::CreateEx
- AFXCMN/CReBarCtrl::DeleteBand
- AFXCMN/CReBarCtrl::DragMove
- AFXCMN/CReBarCtrl::EndDrag
- AFXCMN/CReBarCtrl::GetBandBorders
- AFXCMN/CReBarCtrl::GetBandCount
- AFXCMN/CReBarCtrl::GetBandInfo
- AFXCMN/CReBarCtrl::GetBandMargins
- AFXCMN/CReBarCtrl::GetBarHeight
- AFXCMN/CReBarCtrl::GetBarInfo
- AFXCMN/CReBarCtrl::GetBkColor
- AFXCMN/CReBarCtrl::GetColorScheme
- AFXCMN/CReBarCtrl::GetDropTarget
- AFXCMN/CReBarCtrl::GetExtendedStyle
- AFXCMN/CReBarCtrl::GetImageList
- AFXCMN/CReBarCtrl::GetPalette
- AFXCMN/CReBarCtrl::GetRect
- AFXCMN/CReBarCtrl::GetRowCount
- AFXCMN/CReBarCtrl::GetRowHeight
- AFXCMN/CReBarCtrl::GetTextColor
- AFXCMN/CReBarCtrl::GetToolTips
- AFXCMN/CReBarCtrl::HitTest
- AFXCMN/CReBarCtrl::IDToIndex
- AFXCMN/CReBarCtrl::InsertBand
- AFXCMN/CReBarCtrl::MaximizeBand
- AFXCMN/CReBarCtrl::MinimizeBand
- AFXCMN/CReBarCtrl::MoveBand
- AFXCMN/CReBarCtrl::PushChevron
- AFXCMN/CReBarCtrl::RestoreBand
- AFXCMN/CReBarCtrl::SetBandInfo
- AFXCMN/CReBarCtrl::SetBandWidth
- AFXCMN/CReBarCtrl::SetBarInfo
- AFXCMN/CReBarCtrl::SetBkColor
- AFXCMN/CReBarCtrl::SetColorScheme
- AFXCMN/CReBarCtrl::SetExtendedStyle
- AFXCMN/CReBarCtrl::SetImageList
- AFXCMN/CReBarCtrl::SetOwner
- AFXCMN/CReBarCtrl::SetPalette
- AFXCMN/CReBarCtrl::SetTextColor
- AFXCMN/CReBarCtrl::SetToolTips
- AFXCMN/CReBarCtrl::SetWindowTheme
- AFXCMN/CReBarCtrl::ShowBand
- AFXCMN/CReBarCtrl::SizeToRect
dev_langs:
- C++
helpviewer_keywords:
- CReBarCtrl [MFC], CReBarCtrl
- CReBarCtrl [MFC], BeginDrag
- CReBarCtrl [MFC], Create
- CReBarCtrl [MFC], CreateEx
- CReBarCtrl [MFC], DeleteBand
- CReBarCtrl [MFC], DragMove
- CReBarCtrl [MFC], EndDrag
- CReBarCtrl [MFC], GetBandBorders
- CReBarCtrl [MFC], GetBandCount
- CReBarCtrl [MFC], GetBandInfo
- CReBarCtrl [MFC], GetBandMargins
- CReBarCtrl [MFC], GetBarHeight
- CReBarCtrl [MFC], GetBarInfo
- CReBarCtrl [MFC], GetBkColor
- CReBarCtrl [MFC], GetColorScheme
- CReBarCtrl [MFC], GetDropTarget
- CReBarCtrl [MFC], GetExtendedStyle
- CReBarCtrl [MFC], GetImageList
- CReBarCtrl [MFC], GetPalette
- CReBarCtrl [MFC], GetRect
- CReBarCtrl [MFC], GetRowCount
- CReBarCtrl [MFC], GetRowHeight
- CReBarCtrl [MFC], GetTextColor
- CReBarCtrl [MFC], GetToolTips
- CReBarCtrl [MFC], HitTest
- CReBarCtrl [MFC], IDToIndex
- CReBarCtrl [MFC], InsertBand
- CReBarCtrl [MFC], MaximizeBand
- CReBarCtrl [MFC], MinimizeBand
- CReBarCtrl [MFC], MoveBand
- CReBarCtrl [MFC], PushChevron
- CReBarCtrl [MFC], RestoreBand
- CReBarCtrl [MFC], SetBandInfo
- CReBarCtrl [MFC], SetBandWidth
- CReBarCtrl [MFC], SetBarInfo
- CReBarCtrl [MFC], SetBkColor
- CReBarCtrl [MFC], SetColorScheme
- CReBarCtrl [MFC], SetExtendedStyle
- CReBarCtrl [MFC], SetImageList
- CReBarCtrl [MFC], SetOwner
- CReBarCtrl [MFC], SetPalette
- CReBarCtrl [MFC], SetTextColor
- CReBarCtrl [MFC], SetToolTips
- CReBarCtrl [MFC], SetWindowTheme
- CReBarCtrl [MFC], ShowBand
- CReBarCtrl [MFC], SizeToRect
ms.assetid: 154570d7-e48c-425d-8c7e-c64542bcb4cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ba3b93c1c45edabc86759a14f27309849d58553
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2018
ms.locfileid: "42541142"
---
# <a name="crebarctrl-class"></a>CReBarCtrl (clase)
Encapsula la funcionalidad de un control rebar, que es un contenedor para una ventana secundaria.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CReBarCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CReBarCtrl::CReBarCtrl](#crebarctrl)|Construye un objeto `CReBarCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CReBarCtrl::BeginDrag](#begindrag)|Coloca el control rebar en modo de arrastrar y colocar.|  
|[CReBarCtrl::Create](#create)|Crea el control rebar y lo adjunta a la `CReBarCtrl` objeto.|  
|[CReBarCtrl::CreateEx](#createex)|Crea un control rebar con los estilos extendidos de Windows especificados y lo adjunta a un `CReBarCtrl` objeto.|  
|[CReBarCtrl::DeleteBand](#deleteband)|Elimina una banda de un control rebar.|  
|[CReBarCtrl::DragMove](#dragmove)|Actualiza la posición de arrastre en el control rebar después de llamar a `BeginDrag`.|  
|[CReBarCtrl::EndDrag](#enddrag)|Finaliza la operación de arrastrar y colocar del control rebar.|  
|[CReBarCtrl::GetBandBorders](#getbandborders)|Recupera los bordes de una banda.|  
|[CReBarCtrl::GetBandCount](#getbandcount)|Recupera el recuento de bandas actualmente en el control rebar.|  
|[CReBarCtrl::GetBandInfo](#getbandinfo)|Recupera información sobre una banda especificada en un control rebar.|  
|[CReBarCtrl::GetBandMargins](#getbandmargins)|Recupera los márgenes de una banda.|  
|[CReBarCtrl::GetBarHeight](#getbarheight)|Recupera el alto del control rebar.|  
|[CReBarCtrl::GetBarInfo](#getbarinfo)|Recupera información sobre el control rebar y usa la lista de imágenes.|  
|[CReBarCtrl::GetBkColor](#getbkcolor)|Recupera el color de fondo predeterminado de un control rebar.|  
|[CReBarCtrl::GetColorScheme](#getcolorscheme)|Recupera el [COLORSCHEME](http://msdn.microsoft.com/library/windows/desktop/bb775502) estructura asociada con el control rebar.|  
|[CReBarCtrl::GetDropTarget](#getdroptarget)|Recupera un control rebar `IDropTarget` puntero de interfaz.|  
|[CReBarCtrl::GetExtendedStyle](#getextendedstyle)|Obtiene el estilo extendido del control rebar actual.|  
|[CReBarCtrl::GetImageList](#getimagelist)|Recupera la lista de imágenes asociada con un control rebar.|  
|[CReBarCtrl::GetPalette](#getpalette)|Recupera la paleta actual del control rebar.|  
|[CReBarCtrl::GetRect](#getrect)|Recupera el rectángulo delimitador de una banda determinada en un control rebar.|  
|[CReBarCtrl::GetRowCount](#getrowcount)|Recupera el número de filas de la banda en un control rebar.|  
|[CReBarCtrl::GetRowHeight](#getrowheight)|Recupera el alto de una fila especificada en un control rebar.|  
|[CReBarCtrl::GetTextColor](#gettextcolor)|Recupera el color de texto predeterminado de un control rebar.|  
|[CReBarCtrl::GetToolTips](#gettooltips)|Recupera el identificador de cualquier control de información sobre herramientas asociado al control rebar.|  
|[CReBarCtrl::HitTest](#hittest)|Determina qué parte de una banda rebar está en un momento dado en la pantalla, si no existe en ese momento una banda rebar.|  
|[CReBarCtrl::IDToIndex](#idtoindex)|Convierte un identificador (ID) de banda en un índice de banda en un control rebar.|  
|[CReBarCtrl:: InsertBand](#insertband)|Inserta una nueva banda en un control rebar.|  
|[CReBarCtrl::MaximizeBand](#maximizeband)|Cambia el tamaño de una banda en un control rebar a su tamaño máximo.|  
|[CReBarCtrl::MinimizeBand](#minimizeband)|Cambia el tamaño de una banda en un control rebar a su tamaño más pequeño.|  
|[CReBarCtrl::MoveBand](#moveband)|Mueve una banda de un índice a otra.|  
|[CReBarCtrl::PushChevron](#pushchevron)|Mediante programación, inserta un botón de contenido adicional.|  
|[CReBarCtrl::RestoreBand](#restoreband)|Cambia el tamaño de una banda en un control rebar a su tamaño ideal.|  
|[CReBarCtrl::SetBandInfo](#setbandinfo)|Establece las características de una banda existente en un control rebar.|  
|[CReBarCtrl::SetBandWidth](#setbandwidth)|Establece el ancho de la banda acoplado especificada en el control rebar actual.|  
|[CReBarCtrl::SetBarInfo](#setbarinfo)|Establece las características de un control rebar.|  
|[CReBarCtrl::SetBkColor](#setbkcolor)|Establece el color de fondo predeterminado de un control rebar.|  
|[CReBarCtrl::SetColorScheme](#setcolorscheme)|Establece la combinación de colores para los botones en un control rebar.|  
|[CReBarCtrl::SetExtendedStyle](#setextendedstyle)|Establece los estilos extendidos para el control rebar actual.|  
|[CReBarCtrl::SetImageList](#setimagelist)|Establece la lista de imágenes de un control rebar.|  
|[CReBarCtrl::SetOwner](#setowner)|Establece la ventana de propietario de un control rebar.|  
|[CReBarCtrl::SetPalette](#setpalette)|Establece la paleta actual del control rebar.|  
|[CReBarCtrl::SetTextColor](#settextcolor)|Establece el color de texto predeterminado de un control rebar.|  
|[CReBarCtrl::SetToolTips](#settooltips)|Asocia un control con el control rebar.|  
|[CReBarCtrl::SetWindowTheme](#setwindowtheme)|Establece el estilo visual del control rebar.|  
|[CReBarCtrl::ShowBand](#showband)|Muestra u oculta una banda determinada en un control rebar.|  
|[CReBarCtrl::SizeToRect](#sizetorect)|Ajusta un control rebar a un rectángulo especificado.|  
  
## <a name="remarks"></a>Comentarios  
 La aplicación en el que reside el control rebar asigna la ventana secundaria contenida por el control rebar para la banda rebar. La ventana secundaria es normalmente otro control común.  
  
 Los controles rebar contienen bandas de uno o más. Cada banda puede contener una combinación de una barra de controles, un mapa de bits, una etiqueta de texto y una ventana secundaria. La banda puede contener solo uno de cada uno de estos elementos.  
  
 El control rebar puede mostrar la ventana secundaria a través de un mapa de bits de fondo especificado. Todas las bandas de control rebar pueden cambiarse, excepto las que usan el estilo RBBS_FIXEDSIZE. Cambiar la posición o cambiar el tamaño de una banda de control rebar, el control rebar administra el tamaño y posición de la ventana secundaria que se asigna a la banda. Para cambiar el tamaño o cambiar el orden de bandas en el control, haga clic y arrastre la barra de controles de la banda.  
  
 La siguiente ilustración muestra un control rebar que tiene tres bandas:  
  
-   Banda 0 contiene un control de barra de herramientas plana y transparente.  
  
-   Banda 1 contiene dos botones transparente desplegable estándar y transparente.  
  
-   Banda 2 contiene un cuadro combinado y cuatro botones estándares.  
  
     ![Ejemplo de un menú Rebar](../../mfc/reference/media/vc4scc1.gif "vc4scc1")  
  
## <a name="rebar-control"></a>Control rebar  
 Compatibilidad con controles de rebar:  
  
-   Listas de imágenes.  
  
-   Control de mensajes.  
  
-   Funcionalidad de dibujo personalizado.  
  
-   Una variedad de estilos de control además de los estilos de ventana estándar. Para obtener una lista de estos estilos, consulte [estilos del Control Rebar](http://msdn.microsoft.com/library/windows/desktop/bb774377) en el SDK de Windows.  
  
 Para obtener más información, consulte [usar CReBarCtrl](../../mfc/using-crebarctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CReBarCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="begindrag"></a>  CReBarCtrl::BeginDrag  
 Implementa el comportamiento del mensaje de Win32 [RB_BEGINDRAG](http://msdn.microsoft.com/library/windows/desktop/bb774429), tal y como se describe en el SDK de Windows.  
  
```  
void BeginDrag(
    UINT uBand,  
    DWORD dwPos = (DWORD)-1);
```  
  
### <a name="parameters"></a>Parámetros  
 *uBand*  
 Índice de base cero de la banda que afectan la operación de arrastrar y colocar.  
  
 *dwPos*  
 Un valor DWORD que contiene la fecha inicial del mouse coordenadas. La coordenada horizontal está contenida en el LOWORD y la coordenada vertical se encuentra en el HIWORD. Si se pasa -1 (DWORD), el control rebar utilizará la posición del puntero del mouse de la última vez el subproceso del control denominado `GetMessage` o `PeekMessage`.  
  
##  <a name="create"></a>  CReBarCtrl::Create  
 Crea el control rebar y lo adjunta a la `CReBarCtrl` objeto.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwStyle*  
 Especifica la combinación de estilos del control rebar aplicado al control. Consulte [estilos del Control Rebar](http://msdn.microsoft.com/library/windows/desktop/bb774377) en el SDK de Windows para obtener una lista de estilos admitidos.  
  
 *Rect*  
 Una referencia a un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura, que es la posición y el tamaño del control rebar.  
  
 *pParentWnd*  
 Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que es la ventana primaria del control rebar. No debe ser NULL.  
  
 *nID*  
 Especifica el identificador de control. del control rebar  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el objeto se creó correctamente; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Crear un control rebar en dos pasos:  
  
1.  Llame a [CReBarCtrl](#crebarctrl) para construir un `CReBarCtrl` objeto.  
  
2.  Llame a esta función miembro, que crea el control rebar de Windows y lo adjunta a la `CReBarCtrl` objeto.  
  
 Cuando se llama a `Create`, se inicializan los controles comunes.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]  
  
##  <a name="createex"></a>  CReBarCtrl::CreateEx  
 Crea un control (una ventana secundaria) y lo asocia a la `CReBarCtrl` objeto.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwExStyle*  
 Especifica el estilo extendido del control que se está creando. Para obtener una lista de los estilos extendidos de Windows, consulte el *dwExStyle* parámetro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) en el SDK de Windows.  
  
 *dwStyle*  
 Especifica la combinación de estilos del control rebar aplicado al control. Para obtener una lista de estilos compatibles, consulte [estilos del Control Rebar](http://msdn.microsoft.com/library/windows/desktop/bb774377) en el SDK de Windows.  
  
 *Rect*  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que describe el tamaño y posición de la ventana que se creará, en coordenadas de cliente de *pParentWnd*.  
  
 *pParentWnd*  
 Un puntero a la ventana que es primario del control.  
  
 *nID*  
 Identificador de ventana secundaria. del control  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Use `CreateEx` en lugar de [crear](#create) para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.  
  
##  <a name="crebarctrl"></a>  CReBarCtrl::CReBarCtrl  
 Crea un objeto `CReBarCtrl`.  
  
```  
CReBarCtrl();
```  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CReBarCtrl::Create](#create).  
  
##  <a name="deleteband"></a>  CReBarCtrl::DeleteBand  
 Implementa el comportamiento del mensaje de Win32 [RB_DELETEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774431), tal y como se describe en el SDK de Windows.  
  
```  
BOOL DeleteBand(UINT uBand);
```  
  
### <a name="parameters"></a>Parámetros  
 *uBand*  
 Índice de base cero de la banda que se va a eliminar.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la banda se eliminó correctamente; en caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]  
  
##  <a name="dragmove"></a>  CReBarCtrl::DragMove  
 Implementa el comportamiento del mensaje de Win32 [RB_DRAGMOVE](/windows/desktop/Controls/rb-dragmove), tal y como se describe en el SDK de Windows.  
  
```  
void DragMove(DWORD dwPos = (DWORD)-1);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwPos*  
 Un valor DWORD que contiene las nuevas coordenadas del mouse. La coordenada horizontal está contenida en el LOWORD y la coordenada vertical se encuentra en el HIWORD. Si se pasa -1 (DWORD), el control rebar utilizará la posición del puntero del mouse de la última vez el subproceso del control denominado `GetMessage` o `PeekMessage`.  
  
##  <a name="enddrag"></a>  CReBarCtrl::EndDrag  
 Implementa el comportamiento del mensaje de Win32 [RB_ENDDRAG](http://msdn.microsoft.com/library/windows/desktop/bb774435), tal y como se describe en el SDK de Windows.  
  
```  
void EndDrag();
```  
  
##  <a name="getbandborders"></a>  CReBarCtrl::GetBandBorders  
 Implementa el comportamiento del mensaje de Win32 [RB_GETBANDBORDERS](http://msdn.microsoft.com/library/windows/desktop/bb774437), tal y como se describe en el SDK de Windows.  
  
```  
void GetBandBorders(
    UINT uBand,  
    LPRECT prc) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *uBand*  
 Índice de base cero de la banda para el que se recuperarán los bordes.  
  
 *República Popular China*  
 Un puntero a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que recibirá los bordes de la banda. Si el control rebar tiene el estilo RBS_BANDBORDERS, cada miembro de esta estructura recibirá el número de píxeles, en el lado correspondiente de la banda, que constituyen el borde. Si el control rebar no tiene el estilo RBS_BANDBORDERS, solo los miembros izquierdo de esta estructura reciben información válida. Para obtener una descripción de los estilos de control rebar, consulte [estilos del Control Rebar](http://msdn.microsoft.com/library/windows/desktop/bb774377) en el SDK de Windows.  
  
##  <a name="getbandcount"></a>  CReBarCtrl::GetBandCount  
 Implementa el comportamiento del mensaje de Win32 [RB_GETBANDCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb774439), tal y como se describe en el SDK de Windows.  
  
```  
UINT GetBandCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de bandas asignado al control.  
  
##  <a name="getbandinfo"></a>  CReBarCtrl::GetBandInfo  
 Implementa el comportamiento del mensaje de Win32 [RB_GETBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774451) tal como se describe en el SDK de Windows.  
  
```  
BOOL GetBandInfo(
    UINT uBand,  
    REBARBANDINFO* prbbi) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *uBand*  
 Índice de base cero de la banda para el que se recuperará la información.  
  
 *prbbi*  
 Un puntero a un [REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) estructura para recibir la información de banda. Debe establecer el `cbSize` miembro de esta estructura para `sizeof(REBARBANDINFO)` y establezca el `fMask` miembros a los elementos que van a recuperar antes de enviar este mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
##  <a name="getbandmargins"></a>  CReBarCtrl::GetBandMargins  
 Recupera los márgenes de la banda.  
  
```  
void GetBandMargins(PMARGINS pMargins);
```  
  
### <a name="parameters"></a>Parámetros  
 *pMargins*  
 Un puntero a un [márgenes](http://msdn.microsoft.com/library/windows/desktop/bb773244)estructura que recibirá la información.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la [RB_GETBANDMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb774453) del mensaje, como se describe en el SDK de Windows.  
  
##  <a name="getbarheight"></a>  CReBarCtrl::GetBarHeight  
 Recupera el alto de la barra de control rebar.  
  
```  
UINT GetBarHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Valor que representa el alto, en píxeles, del control.  
  
##  <a name="getbarinfo"></a>  CReBarCtrl::GetBarInfo  
 Implementa el comportamiento del mensaje de Win32 [RB_GETBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774457), tal y como se describe en el SDK de Windows.  
  
```  
BOOL GetBarInfo(REBARINFO* prbi) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *prbi*  
 Un puntero a un [REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395) estructura que recibirá la información de control rebar. Debe establecer el *cbSize* miembro de esta estructura para `sizeof(REBARINFO)` antes de enviar este mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
##  <a name="getbkcolor"></a>  CReBarCtrl::GetBkColor  
 Implementa el comportamiento del mensaje de Win32 [RB_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774459), tal y como se describe en el SDK de Windows.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor COLORREF que representan el color de fondo predeterminado actual.  
  
##  <a name="getcolorscheme"></a>  CReBarCtrl::GetColorScheme  
 Recupera el [COLORSCHEME](http://msdn.microsoft.com/library/windows/desktop/bb775502) estructura para el control rebar.  
  
```  
BOOL GetColorScheme(COLORSCHEME* lpcs);
```  
  
### <a name="parameters"></a>Parámetros  
 *LPC*  
 Un puntero a un [COLORSCHEME](http://msdn.microsoft.com/library/windows/desktop/bb775502) estructura, como se describe en el SDK de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El `COLORSCHEME` estructura incluye el color de resaltado del botón y el color de sombra del botón.  
  
##  <a name="getdroptarget"></a>  CReBarCtrl::GetDropTarget  
 Implementa el comportamiento del mensaje de Win32 [RB_GETDROPTARGET](http://msdn.microsoft.com/library/windows/desktop/bb774463), tal y como se describe en el SDK de Windows.  
  
```  
IDropTarget* GetDropTarget() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) interfaz.  
  
##  <a name="getextendedstyle"></a>  CReBarCtrl::GetExtendedStyle  
 Obtiene los estilos extendidos del control rebar actual.  
  
```  
DWORD GetExtendedStyle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una combinación bit a bit (OR) de marcas que indican los estilos extendidos. Las marcas posibles son RBS_EX_SPLITTER y RBS_EX_TRANSPARENT. Para obtener más información, consulte el *dwMask* parámetro de la [CReBarCtrl::SetExtendedStyle](#setextendedstyle) método.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [RB_GETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb774433) mensaje, que se describe en el SDK de Windows.  
  
##  <a name="getimagelist"></a>  CReBarCtrl::GetImageList  
 Obtiene el `CImageList` objeto asociado con un control rebar.  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto. Devuelve NULL si no se establece ninguna lista de imágenes para el control.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro usa la información de tamaño y la máscara almacenada en el [REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395) estructura, como se describe en el SDK de Windows.  
  
##  <a name="getpalette"></a>  CReBarCtrl::GetPalette  
 Recupera la paleta actual del control rebar.  
  
```  
CPalette* GetPalette() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CPalette](../../mfc/reference/cpalette-class.md) objeto que especifica la paleta actual del control rebar.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que esta función miembro utiliza un `CPalette` objeto como su valor devuelto, en lugar de un HPALETTE.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]  
  
##  <a name="getrect"></a>  CReBarCtrl::GetRect  
 Implementa el comportamiento del mensaje de Win32 [RB_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb774469), tal y como se describe en el SDK de Windows.  
  
```  
BOOL GetRect(
    UINT uBand,  
    LPRECT prc) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *uBand*  
 Índice de base cero de una banda en el control rebar.  
  
 *República Popular China*  
 Un puntero a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que recibirá los límites de la banda rebar.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]  
  
##  <a name="getrowcount"></a>  CReBarCtrl::GetRowCount  
 Implementa el comportamiento del mensaje de Win32 [RB_GETROWCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb774471), tal y como se describe en el SDK de Windows.  
  
```  
UINT GetRowCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor UINT que representa el número de filas de la banda en el control.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]  
  
##  <a name="getrowheight"></a>  CReBarCtrl::GetRowHeight  
 Implementa el comportamiento del mensaje de Win32 [RB_GETROWHEIGHT](http://msdn.microsoft.com/library/windows/desktop/bb774473), tal y como se describe en el SDK de Windows.  
  
```  
UINT GetRowHeight(UINT uRow) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *uRow*  
 Índice de base cero de la banda que tendrá su alto recuperado.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor UINT que representa el alto de fila, en píxeles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]  
  
##  <a name="gettextcolor"></a>  CReBarCtrl::GetTextColor  
 Implementa el comportamiento del mensaje de Win32 [RB_GETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774475), tal y como se describe en el SDK de Windows.  
  
```  
COLORREF GetTextColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor COLORREF que representan el color del texto predeterminada actual.  
  
##  <a name="gettooltips"></a>  CReBarCtrl::GetToolTips  
 Implementa el comportamiento del mensaje de Win32 [RB_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb774477), tal y como se describe en el SDK de Windows.  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que la implementación de MFC `GetToolTips` devuelve un puntero a un `CToolTipCtrl`, en lugar de un HWND.  
  
##  <a name="hittest"></a>  CReBarCtrl::HitTest  
 Implementa el comportamiento del mensaje de Win32 [RB_HITTEST](http://msdn.microsoft.com/library/windows/desktop/bb774494), tal y como se describe en el SDK de Windows.  
  
```  
int HitTest(RBHITTESTINFO* prbht);
```  
  
### <a name="parameters"></a>Parámetros  
 *prbht*  
 Un puntero a un [RBHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb774391) estructura. Antes de enviar el mensaje, el `pt` debe inicializarse un miembro de esta estructura para el punto que se probará en coordenadas de cliente.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de la banda en el punto especificado o -1 si ningún banda rebar estaba en el punto.  
  
##  <a name="idtoindex"></a>  CReBarCtrl::IDToIndex  
 Implementa el comportamiento del mensaje de Win32 [RB_IDTOINDEX](http://msdn.microsoft.com/library/windows/desktop/bb774496), tal y como se describe en el SDK de Windows.  
  
```  
int IDToIndex(UINT uBandID) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *uBandID*  
 El identificador definido por la aplicación de la banda especificada, se pasa en el `wID` miembro de la [REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) estructura cuando se inserta la banda.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice de base cero de banda si se realiza correctamente, o -1 en caso contrario. Si hay índices duplicados de banda, se devuelve la primera de ellas.  
  
##  <a name="insertband"></a>  CReBarCtrl:: InsertBand  
 Implementa el comportamiento del mensaje de Win32 [RB_INSERTBAND](http://msdn.microsoft.com/library/windows/desktop/bb774498), tal y como se describe en el SDK de Windows.  
  
```  
BOOL InsertBand(
    UINT uIndex,  
    REBARBANDINFO* prbbi);
```  
  
### <a name="parameters"></a>Parámetros  
 *uIndex*  
 Índice de base cero de la ubicación donde se insertará la banda. Si este parámetro se establece en -1, el control agregará la nueva banda en la última ubicación.  
  
 *prbbi*  
 Un puntero a un [REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) estructura que define la banda que se va a insertar. Debe establecer el *cbSize* miembro de esta estructura para `sizeof(REBARBANDINFO)` antes de llamar a esta función.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]  
  
##  <a name="maximizeband"></a>  CReBarCtrl::MaximizeBand  
 Cambia el tamaño de una banda en un control rebar a su tamaño máximo.  
  
```  
void MaximizeBand(UINT uBand);
```  
  
### <a name="parameters"></a>Parámetros  
 *uBand*  
 Índice de base cero de la banda maximizarse.  
  
### <a name="remarks"></a>Comentarios  
 Implementa el comportamiento del mensaje de Win32 [RB_MAXIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774500) con `fIdeal` establecido en 0, como se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]  
  
##  <a name="minimizeband"></a>  CReBarCtrl::MinimizeBand  
 Cambia el tamaño de una banda en un control rebar a su tamaño más pequeño.  
  
```  
void MinimizeBand(UINT uBand);
```  
  
### <a name="parameters"></a>Parámetros  
 *uBand*  
 Índice de base cero de la banda que se debe minimizar.  
  
### <a name="remarks"></a>Comentarios  
 Implementa el comportamiento del mensaje de Win32 [RB_MINIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774502), tal y como se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]  
  
##  <a name="moveband"></a>  CReBarCtrl::MoveBand  
 Implementa el comportamiento del mensaje de Win32 [RB_MOVEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774504), tal y como se describe en el SDK de Windows.  
  
```  
BOOL MoveBand(
    UINT uFrom,  
    UINT uTo);
```  
  
### <a name="parameters"></a>Parámetros  
 *uFrom*  
 Índice de base cero de la banda que se va a mover.  
  
 *Ocul*  
 Índice de base cero de la nueva posición de la banda. Este valor de parámetro nunca debe ser mayor que el número de bandas menos uno. Para obtener el número de bandas, llame a [GetBandCount](#getbandcount).  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
##  <a name="pushchevron"></a>  CReBarCtrl::PushChevron  
 Implementa el comportamiento del mensaje de Win32 [RB_PUSHCHEVRON](http://msdn.microsoft.com/library/windows/desktop/bb774506), tal y como se describe en el SDK de Windows.  
  
```  
void PushChevron(
    UINT uBand,  
    LPARAM lAppValue);
```  
  
### <a name="parameters"></a>Parámetros  
 *uBand*  
 Índice de base cero de la banda cuyo contenido adicional consiste en Insertar.  
  
 *lAppValue*  
 Una aplicación define el valor de 32 bits. Consulte *lAppValue* en [RB_PUSHCHEVRON](http://msdn.microsoft.com/library/windows/desktop/bb774506) en el SDK de Windows.  
  
##  <a name="restoreband"></a>  CReBarCtrl::RestoreBand  
 Cambia el tamaño de una banda en un control rebar a su tamaño ideal.  
  
```  
void RestoreBand(UINT uBand);
```  
  
### <a name="parameters"></a>Parámetros  
 *uBand*  
 Índice de base cero de la banda maximizarse.  
  
### <a name="remarks"></a>Comentarios  
 Implementa el comportamiento del mensaje de Win32 [RB_MAXIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774500) con `fIdeal` establecido en 1, como se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]  
  
##  <a name="setbandinfo"></a>  CReBarCtrl::SetBandInfo  
 Implementa el comportamiento del mensaje de Win32 [RB_SETBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774508), tal y como se describe en el SDK de Windows.  
  
```  
BOOL SetBandInfo(
    UINT uBand,  
    REBARBANDINFO* prbbi);
```  
  
### <a name="parameters"></a>Parámetros  
 *uBand*  
 Índice de base cero de la banda de la nueva configuración de recepción.  
  
 *prbbi*  
 Puntero a un [REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) estructura que define la banda que se va a insertar. Debe establecer el `cbSize` miembro de esta estructura para `sizeof(REBARBANDINFO)` antes de enviar este mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]  
  
##  <a name="setbandwidth"></a>  CReBarCtrl::SetBandWidth  
 Establece el ancho de la banda acoplado especificada en el control rebar actual.  
  
```  
BOOL SetBandWidth(
    UINT uBand,   
    int cxWidth);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] *uBand*|Índice de base cero de una banda rebar.|  
|[in] *cxWidth*|Nuevo ancho de banda de rebar, en píxeles.|  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el método se realiza correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [RB_SETBANDWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb774511) mensaje, que se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente define la variable, `m_rebar`, que se usa para tener acceso al control rebar actual. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se establece cada banda rebar tenga el mismo ancho.  
  
 [!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]  
  
##  <a name="setbarinfo"></a>  CReBarCtrl::SetBarInfo  
 Implementa el comportamiento del mensaje de Win32 [RB_SETBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774513), tal y como se describe en el SDK de Windows.  
  
```  
BOOL SetBarInfo(REBARINFO* prbi);
```  
  
### <a name="parameters"></a>Parámetros  
 *prbi*  
 Un puntero a un [REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395) estructura que contiene la información que se puede establecer. Debe establecer el `cbSize` miembro de esta estructura para `sizeof(REBARINFO)` antes de enviar este mensaje  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]  
  
##  <a name="setbkcolor"></a>  CReBarCtrl::SetBkColor  
 Implementa el comportamiento del mensaje de Win32 [RB_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774515), tal y como se describe en el SDK de Windows.  
  
```  
COLORREF SetBkColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parámetros  
 *CLR*  
 El valor COLORREF que representa el color de fondo predeterminado nuevo.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor que representa el color de fondo predeterminado anterior.  
  
### <a name="remarks"></a>Comentarios  
 Vea este tema para obtener más información acerca de cuándo se debe establecer el color de fondo y cómo establecer el valor predeterminado.  
  
##  <a name="setcolorscheme"></a>  CReBarCtrl::SetColorScheme  
 Establece la combinación de colores para los botones en un control rebar.  
  
```  
void SetColorScheme(const COLORSCHEME* lpcs);
```  
  
### <a name="parameters"></a>Parámetros  
 *LPC*  
 Un puntero a un [COLORSCHEME](http://msdn.microsoft.com/library/windows/desktop/bb775502) estructura, como se describe en el SDK de Windows.  
  
### <a name="remarks"></a>Comentarios  
 El `COLORSCHEME` estructura incluye el color de resaltado del botón y el color de sombra del botón.  
  
##  <a name="setextendedstyle"></a>  CReBarCtrl::SetExtendedStyle  
 Establece los estilos extendidos para el control rebar actual.  
  
```  
DWORD SetExtendedStyle(
    DWORD dwMask,   
    DWORD dwStyleEx);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] *dwMask*|Una combinación bit a bit (OR) de marcadores que especifican qué marcas en el *dwStyleEx* parámetro se aplica. Use uno o varios de los siguientes valores:<br /><br /> RBS_EX_SPLITTER: De forma predeterminada, se muestra el separador en la parte inferior en modo horizontal y a la derecha en el modo vertical.<br /><br /> RBS_EX_TRANSPARENT: Reenviar el [WM_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055) mensaje a la ventana primaria.|  
|[in] *dwStyleEx*|Una combinación bit a bit (OR) de marcadores que especifican los estilos que se va a aplicar. Para establecer un estilo, especifique la misma marca que se usa en el *dwMask* parámetro. Para restablecer un estilo, especifique cero binario.|  
  
### <a name="return-value"></a>Valor devuelto  
 El estilo extendido anterior.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [RB_SETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb774519) mensaje, que se describe en el SDK de Windows.  
  
##  <a name="setimagelist"></a>  CReBarCtrl::SetImageList  
 Asigna una lista de imágenes a un control rebar.  
  
```  
BOOL SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>Parámetros  
 *pImageList*  
 Un puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto que contiene la lista de imágenes que se asignará al control rebar.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
##  <a name="setowner"></a>  CReBarCtrl::SetOwner  
 Implementa el comportamiento del mensaje de Win32 [RB_SETPARENT](http://msdn.microsoft.com/library/windows/desktop/bb774522), tal y como se describe en el SDK de Windows.  
  
```  
CWnd* SetOwner(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 *conquistado*  
 Un puntero a un `CWnd` objeto va a establecer como propietario del control rebar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que es el propietario actual del control rebar.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que esta función miembro utiliza punteros a `CWnd` objetos para el propietario seleccionado y actual del control rebar, en lugar de identificadores a windows.  
  
> [!NOTE]
>  Esta función miembro no cambia al elemento primario real que se estableció cuando se creó el control; en su lugar envía mensajes de notificación a la ventana que especifique.  
  
##  <a name="setpalette"></a>  CReBarCtrl::SetPalette  
 Implementa el comportamiento del mensaje de Win32 [RB_SETPALETTE](http://msdn.microsoft.com/library/windows/desktop/bb774520), tal y como se describe en el SDK de Windows.  
  
```  
CPalette* SetPalette(HPALETTE hPal);
```  
  
### <a name="parameters"></a>Parámetros  
 *hPal*  
 Un HPALETTE que especifica la paleta nueva que va a usar el control rebar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CPalette](../../mfc/reference/cpalette-class.md) objeto que especifica la paleta anterior del control rebar.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que esta función miembro utiliza un `CPalette` objeto como su valor devuelto, en lugar de un HPALETTE.  
  
##  <a name="settextcolor"></a>  CReBarCtrl::SetTextColor  
 Implementa el comportamiento del mensaje de Win32 [RB_SETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774524), tal y como se describe en el SDK de Windows.  
  
```  
COLORREF SetTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parámetros  
 *CLR*  
 Un valor COLORREF que representa el nuevo texto de color el `CReBarCtrl` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 El [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) que representa el color del texto anterior del valor asociado a la `CReBarCtrl` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Se proporciona para permitir la flexibilidad de color del texto en un control rebar.  
  
##  <a name="settooltips"></a>  CReBarCtrl::SetToolTips  
 Asocia un control a un control rebar.  
  
```  
void SetToolTips(CToolTipCtrl* pToolTip);
```  
  
### <a name="parameters"></a>Parámetros  
 *pToolTip*  
 Un puntero a un [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objeto  
  
### <a name="remarks"></a>Comentarios  
 Debe destruir la `CToolTipCtrl` objeto cuando haya terminado con él.  
  
##  <a name="setwindowtheme"></a>  CReBarCtrl::SetWindowTheme  
 Establece el estilo visual del control rebar.  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>Parámetros  
 *pszSubAppName*  
 Un puntero a una cadena Unicode que contiene el estilo visual de rebar para establecer.  
  
### <a name="return-value"></a>Valor devuelto  
 No se utiliza el valor devuelto.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la [RB_SETWINDOWTHEME](http://msdn.microsoft.com/library/windows/desktop/bb774530) del mensaje, como se describe en el SDK de Windows.  
  
##  <a name="showband"></a>  CReBarCtrl::ShowBand  
 Implementa el comportamiento del mensaje de Win32 [RB_SHOWBAND](http://msdn.microsoft.com/library/windows/desktop/bb774532), tal y como se describe en el SDK de Windows.  
  
```  
BOOL ShowBand(
    UINT uBand,  
    BOOL fShow = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *uBand*  
 Índice de base cero de una banda en el control rebar.  
  
 *fShow*  
 Indica si la banda se debe mostrar u ocultar. Si este valor es TRUE, se mostrará la banda. En caso contrario, se ocultará la banda.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
##  <a name="sizetorect"></a>  CReBarCtrl::SizeToRect  
 Implementa el comportamiento del mensaje de Win32 [RB_SIZETORECT](http://msdn.microsoft.com/library/windows/desktop/bb774534), tal y como se describe en el SDK de Windows.  
  
```  
BOOL SizeToRect(CRect& rect);
```  
  
### <a name="parameters"></a>Parámetros  
 *Rect*  
 Una referencia a un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que especifica el rectángulo que debe ajustarse para el control rebar.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que esta función miembro utiliza un `CRect` objeto como parámetro, en lugar de un `RECT` estructura.  
  
## <a name="see-also"></a>Vea también  
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)


