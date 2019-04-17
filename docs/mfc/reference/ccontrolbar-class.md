---
title: CControlBar Class
ms.date: 11/04/2016
f1_keywords:
- CControlBar
- AFXEXT/CControlBar
- AFXEXT/CControlBar::CControlBar
- AFXEXT/CControlBar::CalcDynamicLayout
- AFXEXT/CControlBar::CalcFixedLayout
- AFXEXT/CControlBar::CalcInsideRect
- AFXEXT/CControlBar::DoPaint
- AFXEXT/CControlBar::DrawBorders
- AFXEXT/CControlBar::DrawGripper
- AFXEXT/CControlBar::EnableDocking
- AFXEXT/CControlBar::GetBarStyle
- AFXEXT/CControlBar::GetBorders
- AFXEXT/CControlBar::GetCount
- AFXEXT/CControlBar::GetDockingFrame
- AFXEXT/CControlBar::IsFloating
- AFXEXT/CControlBar::OnUpdateCmdUI
- AFXEXT/CControlBar::SetBarStyle
- AFXEXT/CControlBar::SetBorders
- AFXEXT/CControlBar::SetInPlaceOwner
- AFXEXT/CControlBar::m_bAutoDelete
- AFXEXT/CControlBar::m_pInPlaceOwner
helpviewer_keywords:
- CControlBar [MFC], CControlBar
- CControlBar [MFC], CalcDynamicLayout
- CControlBar [MFC], CalcFixedLayout
- CControlBar [MFC], CalcInsideRect
- CControlBar [MFC], DoPaint
- CControlBar [MFC], DrawBorders
- CControlBar [MFC], DrawGripper
- CControlBar [MFC], EnableDocking
- CControlBar [MFC], GetBarStyle
- CControlBar [MFC], GetBorders
- CControlBar [MFC], GetCount
- CControlBar [MFC], GetDockingFrame
- CControlBar [MFC], IsFloating
- CControlBar [MFC], OnUpdateCmdUI
- CControlBar [MFC], SetBarStyle
- CControlBar [MFC], SetBorders
- CControlBar [MFC], SetInPlaceOwner
- CControlBar [MFC], m_bAutoDelete
- CControlBar [MFC], m_pInPlaceOwner
ms.assetid: 4d668c55-9b42-4838-97ac-cf2b3000b82c
ms.openlocfilehash: 41e40b3da7b4a294fe396a9d93f7c6a93593ff95
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58773247"
---
# <a name="ccontrolbar-class"></a>CControlBar Class

La clase base para las clases de barra de controles [CStatusBar](../../mfc/reference/cstatusbar-class.md), [CToolBar](../../mfc/reference/ctoolbar-class.md), [CDialogBar](../../mfc/reference/cdialogbar-class.md), [CReBar](../../mfc/reference/crebar-class.md), y [ COleResizeBar](../../mfc/reference/coleresizebar-class.md).

## <a name="syntax"></a>Sintaxis

```
class CControlBar : public CWnd
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Name|Descripción|
|----------|-----------------|
|[CControlBar::CControlBar](#ccontrolbar)|Construye un objeto `CControlBar`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CControlBar::CalcDynamicLayout](#calcdynamiclayout)|Devuelve el tamaño de una barra de controles dinámica como un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.|
|[CControlBar::CalcFixedLayout](#calcfixedlayout)|Devuelve el tamaño de la barra de control como un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.|
|[CControlBar::CalcInsideRect](#calcinsiderect)|Devuelve las dimensiones actuales del área de la barra de controles, incluidos los bordes.|
|[CControlBar::DoPaint](#dopaint)|Representa los bordes y la barra de redimensionamiento de la barra de controles.|
|[CControlBar::DrawBorders](#drawborders)|Representa los bordes de la barra de controles.|
|[CControlBar::DrawGripper](#drawgripper)|Representa la barra de redimensionamiento de la barra de controles.|
|[CControlBar::EnableDocking](#enabledocking)|Permite que una barra de controles esté acoplada o flotante.|
|[CControlBar::GetBarStyle](#getbarstyle)|Recupera la configuración de estilo de la barra de controles.|
|[CControlBar::GetBorders](#getborders)|Recupera los valores de borde de la barra de controles.|
|[CControlBar::GetCount](#getcount)|Devuelve el número de elementos no HWND de la barra de control.|
|[CControlBar::GetDockingFrame](#getdockingframe)|Devuelve un puntero al marco al que está acoplada una barra de controles.|
|[CControlBar::IsFloating](#isfloating)|Devuelve un valor distinto de cero si la barra de controles en cuestión es una barra de controles flotante.|
|[CControlBar::OnUpdateCmdUI](#onupdatecmdui)|Llama a los controladores de la interfaz de usuario de comandos.|
|[CControlBar::SetBarStyle](#setbarstyle)|Modifica la configuración de estilo de la barra de controles.|
|[CControlBar::SetBorders](#setborders)|Establece los valores de borde de la barra de controles.|
|[CControlBar::SetInPlaceOwner](#setinplaceowner)|Cambia el propietario en contexto de una barra de controles.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CControlBar::m_bAutoDelete](#m_bautodelete)|Si es distinto de cero, el objeto `CControlBar` se elimina cuando se destruye la barra de controles de Windows.|
|[CControlBar::m_pInPlaceOwner](#m_pinplaceowner)|Propietario en contexto de la barra de controles.|

## <a name="remarks"></a>Comentarios

Una barra de controles es una ventana que suele estar alineada a la izquierda o a la derecha de una ventana de marco. Puede contener elementos secundarios que son controles basados en HWND, que son ventanas que generan y responden a los mensajes de Windows, o bien elementos no basados en HWND, que no son windows y administrados por el código de aplicación o código de framework. Cuadros de lista y los controles de edición son ejemplos de controles basados en HWND; paneles de la barra de estado y botones de mapa de bits son ejemplos de controles no basados en HWND.

Las ventanas de barra de controles suelen ser ventanas secundarias de una ventana de marco principal y suelen ser elementos relacionados de la vista del cliente o del cliente MDI de la ventana de marco. Un objeto `CControlBar` utiliza información acerca del rectángulo cliente de su ventana primaria para colocarse. Después informa a la ventana primaria de cuánto espacio queda sin asignar en el área cliente de la ventana primaria.

Para obtener más información sobre `CControlBar`, vea:

- [Barras de control](../../mfc/control-bars.md)

- [Nota técnica 31: Barras de control](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext.h

##  <a name="calcdynamiclayout"></a>  CControlBar::CalcDynamicLayout

El marco de trabajo llama a esta función miembro para calcular las dimensiones de una barra de herramientas dinámica.

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>Parámetros

*nLength*<br/>
La dimensión solicitada de la barra de control, ya sea horizontal o vertical, en función de *dwMode*.

*nMode*<br/>
Las marcas predefinidas siguientes se usan para determinar el alto y ancho de la barra de control dinámico. Utilice la operación bit a bit OR (&#124;) operador para combinar las marcas.

|Marcas de modo de diseño|Lo que significa|
|-----------------------|-------------------|
|LM_STRETCH|Indica si la barra de control se debe ajustar el tamaño del marco. Establece si la barra no es una barra de acoplamiento (no disponible para acoplar). No establecer cuando la barra es acoplada o flotante (disponible para acoplar). Si se establece, omite LM_STRETCH *nLength* y devuelve las dimensiones según el estado LM_HORZ. LM_STRETCH funciona de forma similar a la *bStretch* parámetro usado en [CalcFixedLayout](#calcfixedlayout); vea dicha función miembro para obtener más información sobre la relación entre expansión y orientación.|
|LM_HORZ|Indica que la barra está orientada horizontal o verticalmente. Establece si la barra es horizontal, y si está orientado verticalmente, no se establece. LM_HORZ funciona de forma similar a la *bHorz* parámetro usado en [CalcFixedLayout](#calcfixedlayout); vea dicha función miembro para obtener más información sobre la relación entre expansión y orientación.|
|LM_MRUWIDTH|Usados más recientemente ancho dinámico. Omite *nLength* parámetro y se usa el recordados ancho usados más recientemente.|
|LM_HORZDOCK|Horizontal había acoplada dimensiones. Omite *nLength* parámetro y devuelve el tamaño dinámico con el mayor ancho.|
|LM_VERTDOCK|Vertical había acoplada dimensiones. Omite *nLength* parámetro y devuelve el tamaño dinámico con el alto máximo.|
|LM_LENGTHY|Establezca si *nLength* indica alto (dirección del eje Y) en lugar de ancho.|
|LM_COMMIT|Restablece LM_MRUWIDTH ancho actual de la barra de control flotante.|

### <a name="return-value"></a>Valor devuelto

La barra de control de tamaño, en píxeles, de un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.

### <a name="remarks"></a>Comentarios

Reemplace esta función miembro para proporcionar su propio diseño dinámico en las clases que deriva de `CControlBar`. Las clases MFC derivadas de `CControlBar`, tales como [CToolbar](../../mfc/reference/ctoolbar-class.md), reemplace esta función miembro y proporcionar su propia implementación.

##  <a name="calcfixedlayout"></a>  CControlBar::CalcFixedLayout

Llame a esta función miembro para calcular el tamaño horizontal de una barra de controles.

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parámetros

*bStretch*<br/>
Indica si la barra se debe ajustar el tamaño del marco. El *bStretch* parámetro es distinto de cero cuando la barra no es una barra de acoplamiento (no disponible para acoplar) y es 0 si es acoplada o flotante (disponible para acoplar).

*bHorz*<br/>
Indica que la barra está orientada horizontal o verticalmente. El *bHorz* parámetro es distinto de cero si la barra es horizontal y es 0 si es una orientación vertical.

### <a name="return-value"></a>Valor devuelto

La barra de control de tamaño, en píxeles, de un `CSize` objeto.

### <a name="remarks"></a>Comentarios

Barras de control, como las barras de herramientas se pueden expandir horizontalmente o verticalmente dar cabida a los botones de contenidos en la barra de control.

Si *bStretch* es TRUE, ajustar la dimensión a lo largo de la orientación proporcionada por *bHorz*. En otras palabras, si *bHorz* es FALSE, la barra de control se expande verticalmente. Si *bStretch* es FALSE, se produce ningún stretch. La siguiente tabla muestra los estilos de barra de control resultante y permutaciones posibles de *bStretch* y *bHorz*.

|bStretch|bHorz|Ajuste|Orientación|Acoplamiento de acoplamiento o no.|
|--------------|-----------|----------------|-----------------|--------------------------|
|true|true|Ampliación horizontal|Horizontalmente orientada a servicios|No acoplamiento|
|true|false|Ampliación vertical|Orientan verticalmente|No acoplamiento|
|false|true|Sin estiramiento disponibles|Horizontalmente orientada a servicios|Acoplamiento|
|false|false|Sin estiramiento disponibles|Orientan verticalmente|Acoplamiento|

##  <a name="calcinsiderect"></a>  CControlBar::CalcInsideRect

El marco de trabajo llama a esta función para calcular el área cliente de la barra de control.

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
Contiene las dimensiones actuales de la barra de control. incluso los bordes.

*bHorz*<br/>
Indica que la barra está orientada horizontal o verticalmente. El *bHorz* parámetro es distinto de cero si la barra es horizontal y es 0 si es una orientación vertical.

### <a name="remarks"></a>Comentarios

Esta función se invoca antes de la barra de control se pinta.

Reemplace esta función para personalizar la representación de los bordes y la barra de controles de la barra de control.

##  <a name="ccontrolbar"></a>  CControlBar::CControlBar

Construye un objeto `CControlBar`.

```
CControlBar();
```

##  <a name="dopaint"></a>  CControlBar::DoPaint

Lo llama el marco de trabajo para representar los bordes y la barra de controles de la barra de control.

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Apunta al contexto de dispositivo que se usará para representar los bordes y la barra de redimensionamiento de la barra de control.

### <a name="remarks"></a>Comentarios

Reemplace esta función para personalizar el comportamiento de dibujo de la barra de control.

Otro método de personalización es reemplazar el `DrawBorders` y `DrawGripper` funciones y agregue el código de dibujo personalizado para los bordes y los controles. Dado que estos métodos son invocados por el valor predeterminado `DoPaint` método, una invalidación de `DoPaint` no es necesario.

##  <a name="drawborders"></a>  CControlBar::DrawBorders

Lo llama el marco de trabajo para representar los bordes de la barra de control.

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Apunta al contexto de dispositivo que se usará para representar los bordes de la barra de control.

*rect*<br/>
Un `CRect` objeto que contiene las dimensiones de la barra de control.

### <a name="remarks"></a>Comentarios

Reemplace esta función para personalizar la apariencia de los bordes de la barra de control.

##  <a name="drawgripper"></a>  CControlBar::DrawGripper

Lo llama el marco de trabajo para representar la barra de redimensionamiento de la barra de control.

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Apunta al contexto de dispositivo que se usará para representar a los controles de barra de control.

*rect*<br/>
Un `CRect` objeto que contiene las dimensiones de la barra de redimensionamiento de barra de control.

### <a name="remarks"></a>Comentarios

Reemplace esta función para personalizar la apariencia de la barra de redimensionamiento de barra de control.

##  <a name="enabledocking"></a>  CControlBar::EnableDocking

Llame a esta función para habilitar una barra de control quede acoplado.

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parámetros

*dwDockStyle*<br/>
Especifica si la barra de control admite el acoplamiento y los lados de su ventana primaria a la que se puede acoplar la barra de control, si es compatible. Puede ser uno o varios de los siguientes:

- CBRS_ALIGN_TOP permite acoplar en la parte superior del área cliente.

- CBRS_ALIGN_BOTTOM permite acoplar en la parte inferior del área de cliente.

- CBRS_ALIGN_LEFT permite acoplar en el lado izquierdo del área cliente.

- CBRS_ALIGN_RIGHT permite acoplar en el lado derecho del área de cliente.

- CBRS_ALIGN_ANY permite acoplar en cualquier lado del área de cliente.

- CBRS_FLOAT_MULTI permite varias barras de control a flotar en una ventana de marco reducido único.

Si es 0 (es decir, lo que indica ningún indicador), no se acoplará la barra de control.

### <a name="remarks"></a>Comentarios

Los lados especificados deben coincidir con uno de los lados habilitados para el acoplamiento en la ventana de marco de destino, o no se puede acoplar la barra de control a esa ventana de marco.

##  <a name="getbarstyle"></a>  CControlBar::GetBarStyle

Llame a esta función para determinar qué **CBRS_** configuración (estilos de barra de control) está establecidas actualmente para la barra de control.

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>Valor devuelto

Actual **CBRS_** (estilos de barra de control) configuración de la barra de control. Consulte [SetBarStyle](#setbarstyle) para una lista completa de los estilos disponibles.

### <a name="remarks"></a>Comentarios

No controla **WS_** (ventana) de estilos.

##  <a name="getborders"></a>  CControlBar::GetBorders

Devuelve los valores actuales de borde de la barra de control.

```
CRect GetBorders() const;
```

### <a name="return-value"></a>Valor devuelto

Un `CRect` objeto que contiene el ancho actual (en píxeles) de cada lado del objeto de barra de control. Por ejemplo, el valor de la *izquierdo* miembro, de [CRect](../../atl-mfc-shared/reference/crect-class.md) el objeto, es el ancho del borde izquierdo.

##  <a name="getcount"></a>  CControlBar::GetCount

Devuelve el número de elementos que no sean HWND en el `CControlBar` objeto.

```
int GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos que no sean HWND en el `CControlBar` objeto. Esta función devuelve 0 para un [CDialogBar](../../mfc/reference/cdialogbar-class.md) objeto.

### <a name="remarks"></a>Comentarios

El tipo del elemento depende el objeto derivado: paneles para [CStatusBar](../../mfc/reference/cstatusbar-class.md) objetos y los botones y separadores para [CToolBar](../../mfc/reference/ctoolbar-class.md) objetos.

##  <a name="getdockingframe"></a>  CControlBar::GetDockingFrame

Llame a esta función miembro para obtener un puntero a la ventana de marco actual a la que se acopla la barra de control.

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a una ventana de marco si se realiza correctamente; en caso contrario, es NULL.

Si no se acopla la barra de control a una ventana de marco (es decir, si la barra de control es flotante), esta función devuelve un puntero a su elemento primario [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md).

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de las barras de control acoplable, consulte [CControlBar:: EnableDocking](#enabledocking) y [CFrameWnd:: DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar).

##  <a name="isfloating"></a>  CControlBar::IsFloating

Llame a esta función miembro para determinar si la barra de controles está acoplado o flotante.

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la barra de control es flotante; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Para cambiar el estado de una barra de control de acoplada a flotante, llame a [CFrameWnd:: FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar).

##  <a name="m_bautodelete"></a>  CControlBar::m_bAutoDelete

Si es distinto de cero, el objeto `CControlBar` se elimina cuando se destruye la barra de controles de Windows.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Comentarios

*m_bAutoDelete* es una variable pública de tipo BOOL.

Normalmente, un objeto de barra de controles está incrustado en un objeto de ventana de marco. En este caso, *m_bAutoDelete* es 0 porque el objeto de barra de control incrustado se destruye cuando se destruye la ventana de marco.

Establecer esta variable en un valor distinto de cero si asigna un `CControlBar` objeto en el montón y no tiene previsto llamar a **eliminar**.

##  <a name="m_pinplaceowner"></a>  CControlBar::m_pInPlaceOwner

Propietario en contexto de la barra de controles.

```
CWnd* m_pInPlaceOwner;
```

##  <a name="onupdatecmdui"></a>  CControlBar::OnUpdateCmdUI

Esta función miembro se llama el marco de trabajo para actualizar el estado de la barra de herramientas o barra de estado.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>Parámetros

*pTarget*<br/>
Apunta a la ventana de marco principal de la aplicación. Este puntero se utiliza para enrutar los mensajes de actualización.

*bDisableIfNoHndler*<br/>
Marca que indica si se debe mostrar un control que no tiene ningún controlador de actualización automáticamente como deshabilitado.

### <a name="remarks"></a>Comentarios

Para actualizar un botón individual o un panel, utilice la macro ON_UPDATE_COMMAND_UI en el mapa de mensajes para establecer un controlador de actualización de forma adecuada. Consulte [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) para obtener más información sobre el uso de esta macro.

`OnUpdateCmdUI` se llama el marco de trabajo cuando la aplicación está inactiva. La ventana de marco para actualizarse debe ser una ventana secundaria, al menos indirectamente, de una ventana de marco visible. `OnUpdateCmdUI` es un avanzado que se puede invalidar.

##  <a name="setbarstyle"></a>  CControlBar::SetBarStyle

Llame a esta función para establecer el deseado **CBRS_** estilos para la barra de control.

```
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Los estilos que desee para la barra de control. Puede ser uno o varios de los siguientes:

- CBRS_ALIGN_TOP permite que la barra de control quede acoplado a la parte superior del área de cliente de una ventana de marco.

- CBRS_ALIGN_BOTTOM permite que la barra de control quede acoplado a la parte inferior del área de cliente de una ventana de marco.

- CBRS_ALIGN_LEFT permite que la barra de control se acopla al lado izquierdo del área cliente de una ventana de marco.

- CBRS_ALIGN_RIGHT permite que la barra de control se acopla a la derecha del área de cliente de una ventana de marco.

- CBRS_ALIGN_ANY permite que la barra de control se acopla a cualquier lado del área de cliente de una ventana de marco.

- CBRS_BORDER_TOP hace que un borde que se va a dibujar el borde superior del control de la barra que sería visible.

- CBRS_BORDER_BOTTOM hace que un borde que se va a dibujar en el borde inferior del control de la barra que sería visible.

- CBRS_BORDER_LEFT hace que un borde que se va a dibujar en el borde izquierdo del control de la barra que sería visible.

- CBRS_BORDER_RIGHT hace que un borde que se va a dibujar el borde derecho del control de la barra que sería visible.

- CBRS_FLOAT_MULTI permite varias barras de control a flotar en una ventana de marco reducido único.

- CBRS_TOOLTIPS hace que el información sobre herramientas que se mostrará en la barra de control.

- Texto del mensaje provoca CBRS_FLYBY actualizarse al mismo tiempo como información sobre herramientas.

- CBRS_GRIPPER hace que un agarrador, similar al usado en bandas en un `CReBar` objeto va a dibujar para cualquier `CControlBar`-clase derivada.

### <a name="remarks"></a>Comentarios

No afecta a la **WS_** configuración (estilo de ventana).

##  <a name="setborders"></a>  CControlBar::SetBorders

Llame a esta función para establecer el tamaño de los bordes de la barra de control.

```
void SetBorders(
    int cxLeft = 0,
    int cyTop = 0,
    int cxRight = 0,
    int cyBottom = 0);

void SetBorders(LPCRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*cxLeft*<br/>
El ancho (en píxeles) del borde izquierdo de la barra de control.

*cyTop*<br/>
El alto (en píxeles) del borde superior de la barra de control.

*cxRight*<br/>
El ancho (en píxeles) del borde derecho de la barra de control.

*cyBottom*<br/>
El alto (en píxeles) del borde inferior de la barra de control.

*lpRect*<br/>
Un puntero a un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que contiene el ancho actual (en píxeles) de cada borde del objeto de barra de control.

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente establece los bordes superior e inferior de la barra de control para 5 píxeles y los bordes izquierdos y derecho a 2 píxeles:

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

##  <a name="setinplaceowner"></a>  CControlBar::SetInPlaceOwner

Cambia el propietario en contexto de una barra de controles.

```
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero a un objeto `CWnd` .

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[CTRLBARS de ejemplo](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CToolBar (clase)](../../mfc/reference/ctoolbar-class.md)<br/>
[CDialogBar (clase)](../../mfc/reference/cdialogbar-class.md)<br/>
[CStatusBar (clase)](../../mfc/reference/cstatusbar-class.md)<br/>
[CReBar (clase)](../../mfc/reference/crebar-class.md)
