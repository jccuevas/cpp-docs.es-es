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
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426010"
---
# <a name="ccontrolbar-class"></a>CControlBar Class

La clase base para las clases de barra de control [CStatusBar](../../mfc/reference/cstatusbar-class.md), [CToolBar](../../mfc/reference/ctoolbar-class.md), [CDialogBar](../../mfc/reference/cdialogbar-class.md), [CReBar](../../mfc/reference/crebar-class.md)y [COleResizeBar](../../mfc/reference/coleresizebar-class.md).

## <a name="syntax"></a>Sintaxis

```
class CControlBar : public CWnd
```

## <a name="members"></a>Members

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CControlBar:: CControlBar](#ccontrolbar)|Construye un objeto `CControlBar`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CControlBar:: CalcDynamicLayout](#calcdynamiclayout)|Devuelve el tamaño de una barra de controles dinámica como un objeto [CSize](../../atl-mfc-shared/reference/csize-class.md) .|
|[CControlBar:: CalcFixedLayout](#calcfixedlayout)|Devuelve el tamaño de la barra de controles como un objeto [CSize](../../atl-mfc-shared/reference/csize-class.md) .|
|[CControlBar:: CalcInsideRect](#calcinsiderect)|Devuelve las dimensiones actuales del área de la barra de controles, incluidos los bordes.|
|[CControlBar::D oPaint](#dopaint)|Representa los bordes y la barra de redimensionamiento de la barra de controles.|
|[CControlBar::D rawBorders](#drawborders)|Representa los bordes de la barra de controles.|
|[CControlBar::D rawGripper](#drawgripper)|Representa la barra de redimensionamiento de la barra de controles.|
|[CControlBar:: EnableDocking](#enabledocking)|Permite que una barra de controles esté acoplada o flotante.|
|[CControlBar:: GetBarStyle](#getbarstyle)|Recupera la configuración de estilo de la barra de controles.|
|[CControlBar:: GetBorders](#getborders)|Recupera los valores de borde de la barra de controles.|
|[CControlBar:: GetCount](#getcount)|Devuelve el número de elementos no HWND en la barra de controles.|
|[CControlBar:: GetDockingFrame](#getdockingframe)|Devuelve un puntero al marco al que está acoplada una barra de controles.|
|[CControlBar:: IsFloating](#isfloating)|Devuelve un valor distinto de cero si la barra de controles en cuestión es una barra de controles flotante.|
|[CControlBar:: OnUpdateCmdUI](#onupdatecmdui)|Llama a los controladores de la interfaz de usuario de comandos.|
|[CControlBar:: SetBarStyle](#setbarstyle)|Modifica la configuración de estilo de la barra de controles.|
|[CControlBar:: SetBorders](#setborders)|Establece los valores de borde de la barra de controles.|
|[CControlBar:: SetInPlaceOwner](#setinplaceowner)|Cambia el propietario en contexto de una barra de controles.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CControlBar:: m_bAutoDelete](#m_bautodelete)|Si es distinto de cero, el objeto `CControlBar` se elimina cuando se destruye la barra de controles de Windows.|
|[CControlBar:: m_pInPlaceOwner](#m_pinplaceowner)|Propietario en contexto de la barra de controles.|

## <a name="remarks"></a>Observaciones

Una barra de controles es una ventana que suele estar alineada a la izquierda o a la derecha de una ventana de marco. Puede contener elementos secundarios que son controles basados en HWND, que son ventanas que generan y responden a mensajes de Windows, o elementos no basados en HWND, que no son de Windows y se administran mediante código de aplicación o código de marco. Los cuadros de lista y los controles de edición son ejemplos de controles basados en HWND; los paneles de barra de estado y los botones de mapa de bits son ejemplos de controles no basados en HWND.

Las ventanas de barra de controles suelen ser ventanas secundarias de una ventana de marco principal y suelen ser elementos relacionados de la vista del cliente o del cliente MDI de la ventana de marco. Un objeto `CControlBar` utiliza información acerca del rectángulo cliente de su ventana primaria para colocarse. Después informa a la ventana primaria de cuánto espacio queda sin asignar en el área cliente de la ventana primaria.

Para obtener más información sobre `CControlBar`, vea:

- [Barras de control](../../mfc/control-bars.md)

- [Nota técnica 31: barras de control](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext. h

##  <a name="calcdynamiclayout"></a>CControlBar:: CalcDynamicLayout

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
Se usan las siguientes marcas predefinidas para determinar el alto y el ancho de la barra de control dinámica. Use el operador bit a bit&#124;or () para combinar las marcas.

|Marcas de modo de diseño|Qué significa|
|-----------------------|-------------------|
|LM_STRETCH|Indica si la barra de control se debe ajustar al tamaño del marco. Se establece si la barra no es una barra de acoplamiento (no está disponible para el acoplamiento). No se establece cuando la barra está acoplada o flotante (está disponible para el acoplamiento). Si se establece, LM_STRETCH omite *nLength* y devuelve dimensiones basadas en el estado LM_HORZ. LM_STRETCH funciona de forma similar al parámetro *bStretch* que se usa en [CalcFixedLayout](#calcfixedlayout); Vea la función miembro para obtener más información sobre la relación entre la expansión y la orientación.|
|LM_HORZ|Indica que la barra está orientada horizontal o verticalmente. Establezca si la barra está orientada horizontalmente y si está orientada verticalmente, no se establece. LM_HORZ funciona de forma similar al parámetro *bHorz* que se usa en [CalcFixedLayout](#calcfixedlayout); Vea la función miembro para obtener más información sobre la relación entre la expansión y la orientación.|
|LM_MRUWIDTH|El ancho dinámico usado más recientemente. Omite el parámetro *nLength* y usa el ancho usado más recientemente.|
|LM_HORZDOCK|Dimensiones acopladas horizontalmente. Omite el parámetro *nLength* y devuelve el tamaño dinámico con el ancho más grande.|
|LM_VERTDOCK|Dimensiones acopladas verticales. Omite el parámetro *nLength* y devuelve el tamaño dinámico con el alto mayor.|
|LM_LENGTHY|Establezca si *nLength* indica el alto (dirección y) en lugar del ancho.|
|LM_COMMIT|Restablece LM_MRUWIDTH al ancho actual de la barra de control flotante.|

### <a name="return-value"></a>Valor devuelto

Tamaño de la barra de control, en píxeles, de un objeto [CSize](../../atl-mfc-shared/reference/csize-class.md) .

### <a name="remarks"></a>Observaciones

Invalide esta función miembro para proporcionar su propio diseño dinámico en las clases que deriva de `CControlBar`. Las clases MFC derivadas de `CControlBar`, como [CToolbar](../../mfc/reference/ctoolbar-class.md), invalidan esta función miembro y proporcionan su propia implementación.

##  <a name="calcfixedlayout"></a>CControlBar:: CalcFixedLayout

Llame a esta función miembro para calcular el tamaño horizontal de una barra de controles.

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parámetros

*bStretch*<br/>
Indica si la barra debe ajustarse al tamaño del marco. El parámetro *bStretch* es distinto de cero cuando la barra no es una barra de acoplamiento (no está disponible para el acoplamiento) y es 0 cuando está acoplada o flotante (está disponible para el acoplamiento).

*bHorz*<br/>
Indica que la barra está orientada horizontal o verticalmente. El parámetro *bHorz* es distinto de cero si la barra está orientada horizontalmente y es 0 si está orientada verticalmente.

### <a name="return-value"></a>Valor devuelto

Tamaño de la barra de control, en píxeles, de un objeto `CSize`.

### <a name="remarks"></a>Observaciones

Las barras de control, como las barras de herramientas, se pueden ajustar horizontal o verticalmente para alojar los botones contenidos en la barra de control.

Si *bStretch* es true, estire la dimensión a lo largo de la orientación proporcionada por *bHorz*. En otras palabras, si *bHorz* es false, la barra de control se ajusta verticalmente. Si *bStretch* es false, no se produce Stretch. En la tabla siguiente se muestran las posibles permutaciones y los estilos de barra de control resultantes de *bStretch* y *bHorz*.

|bStretch|bHorz|Ajuste|Orientación|Acoplamiento/no acoplamiento|
|--------------|-----------|----------------|-----------------|--------------------------|
|TRUE|TRUE|Ajuste horizontal|Orientada horizontalmente|Sin acoplamiento|
|TRUE|FALSE|Ajuste vertical|Orientada verticalmente|Sin acoplamiento|
|FALSE|TRUE|No hay ninguna ampliación disponible|Orientada horizontalmente|Docking|
|FALSE|FALSE|No hay ninguna ampliación disponible|Orientada verticalmente|Docking|

##  <a name="calcinsiderect"></a>CControlBar:: CalcInsideRect

El marco de trabajo llama a esta función para calcular el área cliente de la barra de control.

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
Contiene las dimensiones actuales de la barra de controles; incluir los bordes.

*bHorz*<br/>
Indica que la barra está orientada horizontal o verticalmente. El parámetro *bHorz* es distinto de cero si la barra está orientada horizontalmente y es 0 si está orientada verticalmente.

### <a name="remarks"></a>Observaciones

Se llama a esta función antes de que se dibuje la barra de control.

Invalide esta función para personalizar la representación de los bordes y la barra de redimensionamiento de la barra de controles.

##  <a name="ccontrolbar"></a>CControlBar:: CControlBar

Construye un objeto `CControlBar`.

```
CControlBar();
```

##  <a name="dopaint"></a>CControlBar::D oPaint

Lo llama el marco de trabajo para representar los bordes y la barra de redimensionamiento de la barra de controles.

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Apunta al contexto de dispositivo que se va a usar para representar los bordes y el agarrador de la barra de controles.

### <a name="remarks"></a>Observaciones

Invalide esta función para personalizar el comportamiento de dibujo de la barra de control.

Otro método de personalización consiste en invalidar las funciones `DrawBorders` y `DrawGripper` y agregar código de dibujo personalizado para los bordes y el agarrador. Dado que el método `DoPaint` predeterminado llama a estos métodos, no es necesario reemplazar `DoPaint`.

##  <a name="drawborders"></a>CControlBar::D rawBorders

Lo llama el marco de trabajo para representar los bordes de la barra de controles.

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Apunta al contexto de dispositivo que se va a usar para representar los bordes de la barra de controles.

*Rect*<br/>
`CRect` objeto que contiene las dimensiones de la barra de controles.

### <a name="remarks"></a>Observaciones

Invalide esta función para personalizar la apariencia de los bordes de la barra de control.

##  <a name="drawgripper"></a>CControlBar::D rawGripper

Lo llama el marco de trabajo para representar el agarrador de la barra de control.

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Apunta al contexto de dispositivo que se va a usar para representar el agarrador de la barra de control.

*Rect*<br/>
`CRect` objeto que contiene las dimensiones del control de redimensionamiento de la barra de controles.

### <a name="remarks"></a>Observaciones

Invalide esta función para personalizar la apariencia del agarrador de la barra de control.

##  <a name="enabledocking"></a>CControlBar:: EnableDocking

Llame a esta función para permitir el acoplamiento de una barra de control.

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parámetros

*dwDockStyle*<br/>
Especifica si la barra de control admite el acoplamiento y los lados de la ventana primaria a la que se puede acoplar la barra de control, si se admite. Puede ser uno o varios de los siguientes:

- CBRS_ALIGN_TOP permite el acoplamiento en la parte superior del área cliente.

- CBRS_ALIGN_BOTTOM permite el acoplamiento en la parte inferior del área cliente.

- CBRS_ALIGN_LEFT permite el acoplamiento en el lado izquierdo del área cliente.

- CBRS_ALIGN_RIGHT permite el acoplamiento en el lado derecho del área cliente.

- CBRS_ALIGN_ANY permite el acoplamiento en cualquier lado del área cliente.

- CBRS_FLOAT_MULTI permite que se floten varias barras de control en una sola ventana de marco reducido.

Si es 0 (es decir, indica que no hay marcas), la barra de control no se acoplará.

### <a name="remarks"></a>Observaciones

Los lados especificados deben coincidir con uno de los lados habilitados para el acoplamiento en la ventana de marco de destino o la barra de control no se puede acoplar a esa ventana de marco.

##  <a name="getbarstyle"></a>CControlBar:: GetBarStyle

Llame a esta función para determinar qué configuración de **CBRS_** (estilos de barra de control) está establecida actualmente para la barra de control.

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>Valor devuelto

La configuración actual del **CBRS_** (estilos de barra de control) de la barra de control. Consulte [CControlBar:: SetBarStyle](#setbarstyle) para obtener una lista completa de los estilos disponibles.

### <a name="remarks"></a>Observaciones

No controla los estilos de **WS_** (estilo de ventana).

##  <a name="getborders"></a>CControlBar:: GetBorders

Devuelve los valores de borde actuales de la barra de controles.

```
CRect GetBorders() const;
```

### <a name="return-value"></a>Valor devuelto

`CRect` objeto que contiene el ancho actual (en píxeles) de cada lado del objeto de barra de control. Por ejemplo, el valor del miembro *izquierdo* , del objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) , es el ancho del borde izquierdo.

##  <a name="getcount"></a>CControlBar:: GetCount

Devuelve el número de elementos no HWND en el objeto `CControlBar`.

```
int GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos no HWND en el objeto `CControlBar`. Esta función devuelve 0 para un objeto [CDialogBar](../../mfc/reference/cdialogbar-class.md) .

### <a name="remarks"></a>Observaciones

El tipo del elemento depende del objeto derivado: los paneles de los objetos [CStatusBar](../../mfc/reference/cstatusbar-class.md) y los botones y separadores de los objetos [CToolBar](../../mfc/reference/ctoolbar-class.md) .

##  <a name="getdockingframe"></a>CControlBar:: GetDockingFrame

Llame a esta función miembro para obtener un puntero a la ventana de marco actual a la que está acoplada la barra de control.

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a una ventana de marco si se realiza correctamente; de lo contrario, NULL.

Si la barra de control no está acoplada a una ventana de marco (es decir, si la barra de control es flotante), esta función devolverá un puntero a su [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)primario.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre las barras de control acoplables, vea [CControlBar:: EnableDocking](#enabledocking) y [CFrameWnd::D ockcontrolbar](../../mfc/reference/cframewnd-class.md#dockcontrolbar).

##  <a name="isfloating"></a>CControlBar:: IsFloating

Llame a esta función miembro para determinar si la barra de control es flotante o está acoplada.

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la barra de control es flotante; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Para cambiar el estado de una barra de control de acoplada a flotante, llame a [CFrameWnd:: FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar).

##  <a name="m_bautodelete"></a>CControlBar:: m_bAutoDelete

Si es distinto de cero, el objeto `CControlBar` se elimina cuando se destruye la barra de controles de Windows.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Observaciones

*m_bAutoDelete* es una variable pública de tipo bool.

Un objeto de barra de control normalmente se incrusta en un objeto de ventana de marco. En este caso, *m_bAutoDelete* es 0 porque el objeto de barra de control incrustado se destruye cuando se destruye la ventana de marco.

Establezca esta variable en un valor distinto de cero si asigna un objeto `CControlBar` en el montón y no tiene previsto llamar a **Delete**.

##  <a name="m_pinplaceowner"></a>CControlBar:: m_pInPlaceOwner

Propietario en contexto de la barra de controles.

```
CWnd* m_pInPlaceOwner;
```

##  <a name="onupdatecmdui"></a>CControlBar:: OnUpdateCmdUI

El marco de trabajo llama a esta función miembro para actualizar el estado de la barra de herramientas o de la barra de estado.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>Parámetros

*pTarget*<br/>
Apunta a la ventana de marco principal de la aplicación. Este puntero se usa para enrutar mensajes de actualización.

*bDisableIfNoHndler*<br/>
Marca que indica si un control que no tiene controlador de actualización se debe mostrar automáticamente como deshabilitado.

### <a name="remarks"></a>Observaciones

Para actualizar un botón o panel individual, use la macro ON_UPDATE_COMMAND_UI en el mapa de mensajes para establecer un controlador de actualización de forma adecuada. Consulte [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) para obtener más información sobre el uso de esta macro.

el marco de trabajo llama a `OnUpdateCmdUI` cuando la aplicación está inactiva. La ventana de marco que se va a actualizar debe ser una ventana secundaria, al menos indirectamente, de una ventana de marco visible. `OnUpdateCmdUI` es un reemplazable avanzado.

##  <a name="setbarstyle"></a>CControlBar:: SetBarStyle

Llame a esta función para establecer los estilos de **CBRS_** deseados para la barra de controles.

```
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Estilos deseados para la barra de control. Puede ser uno o varios de los siguientes:

- CBRS_ALIGN_TOP permite acoplar la barra de control en la parte superior del área de cliente de una ventana de marco.

- CBRS_ALIGN_BOTTOM permite acoplar la barra de control en la parte inferior del área cliente de una ventana de marco.

- CBRS_ALIGN_LEFT permite acoplar la barra de control en el lado izquierdo del área cliente de una ventana de marco.

- CBRS_ALIGN_RIGHT permite acoplar la barra de control en el lado derecho del área de cliente de una ventana de marco.

- CBRS_ALIGN_ANY permite acoplar la barra de control a cualquier lado del área de cliente de una ventana de marco.

- CBRS_BORDER_TOP hace que un borde se dibuje en el borde superior de la barra de control cuando sea visible.

- CBRS_BORDER_BOTTOM hace que un borde se dibuje en el borde inferior de la barra de control cuando sea visible.

- CBRS_BORDER_LEFT hace que un borde se dibuje en el borde izquierdo de la barra de control cuando sea visible.

- CBRS_BORDER_RIGHT hace que un borde se dibuje en el borde derecho de la barra de control cuando sea visible.

- CBRS_FLOAT_MULTI permite que se floten varias barras de control en una sola ventana de marco reducido.

- CBRS_TOOLTIPS hace que la información sobre herramientas se muestre en la barra de control.

- CBRS_FLYBY hace que el texto del mensaje se actualice al mismo tiempo que la información sobre herramientas.

- CBRS_GRIPPER hace que un agarrador, similar al que se usa en las bandas de un objeto `CReBar`, se dibuje para cualquier clase derivada de `CControlBar`.

### <a name="remarks"></a>Observaciones

No afecta a la configuración de **WS_** (estilo de ventana).

##  <a name="setborders"></a>CControlBar:: SetBorders

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
Ancho (en píxeles) del borde izquierdo de la barra de control.

*cyTop*<br/>
Alto (en píxeles) del borde superior de la barra de control.

*cxRight*<br/>
Ancho (en píxeles) del borde derecho de la barra de control.

*cyBottom*<br/>
Alto (en píxeles) del borde inferior de la barra de control.

*lpRect*<br/>
Un puntero a un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) que contiene el ancho actual (en píxeles) de cada borde del objeto de barra de control.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establecen los bordes superior e inferior de la barra de control en 5 píxeles y los bordes izquierdo y derecho en 2 píxeles:

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

##  <a name="setinplaceowner"></a>CControlBar:: SetInPlaceOwner

Cambia el propietario en contexto de una barra de controles.

```
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero a un objeto `CWnd` .

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CToolBar (clase)](../../mfc/reference/ctoolbar-class.md)<br/>
[CDialogBar (clase)](../../mfc/reference/cdialogbar-class.md)<br/>
[CStatusBar (clase)](../../mfc/reference/cstatusbar-class.md)<br/>
[CReBar (clase)](../../mfc/reference/crebar-class.md)
