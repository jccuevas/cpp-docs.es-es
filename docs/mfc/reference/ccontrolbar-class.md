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
ms.openlocfilehash: c2f8ea48bf9a1f015928650085b07198b152771a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754790"
---
# <a name="ccontrolbar-class"></a>CControlBar Class

La clase base para las clases de barra de control [CStatusBar](../../mfc/reference/cstatusbar-class.md), [CToolBar](../../mfc/reference/ctoolbar-class.md), [CDialogBar](../../mfc/reference/cdialogbar-class.md), [CReBar](../../mfc/reference/crebar-class.md)y [COleResizeBar](../../mfc/reference/coleresizebar-class.md).

## <a name="syntax"></a>Sintaxis

```
class CControlBar : public CWnd
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CControlBar::CControlBar](#ccontrolbar)|Construye un objeto `CControlBar`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CControlBar::CalcDynamicLayout](#calcdynamiclayout)|Devuelve el tamaño de una barra de control dinámica como un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.|
|[CControlBar::CalcFixedLayout](#calcfixedlayout)|Devuelve el tamaño de la barra de control como un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.|
|[CControlBar::CalcInsideRect](#calcinsiderect)|Devuelve las dimensiones actuales del área de la barra de controles, incluidos los bordes.|
|[CControlBar::DoPaint](#dopaint)|Representa los bordes y la barra de redimensionamiento de la barra de controles.|
|[CControlBar::DrawBorders](#drawborders)|Representa los bordes de la barra de controles.|
|[CControlBar::DrawGripper](#drawgripper)|Representa la barra de redimensionamiento de la barra de controles.|
|[CControlBar::EnableDocking](#enabledocking)|Permite que una barra de controles esté acoplada o flotante.|
|[CControlBar::GetBarStyle](#getbarstyle)|Recupera la configuración de estilo de la barra de controles.|
|[CControlBar::GetBorders](#getborders)|Recupera los valores de borde de la barra de controles.|
|[CControlBar::GetCount](#getcount)|Devuelve el número de elementos que no son HWND en la barra de control.|
|[CControlBar::GetDockingFrame](#getdockingframe)|Devuelve un puntero al marco al que está acoplada una barra de controles.|
|[CControlBar::IsFloating](#isfloating)|Devuelve un valor distinto de cero si la barra de controles en cuestión es una barra de controles flotante.|
|[CControlBar::OnUpdateCmdUI](#onupdatecmdui)|Llama a los controladores de la interfaz de usuario de comandos.|
|[CControlBar::SetBarStyle](#setbarstyle)|Modifica la configuración de estilo de la barra de controles.|
|[CControlBar::SetBorders](#setborders)|Establece los valores de borde de la barra de controles.|
|[CControlBar::SetInPlaceOwner](#setinplaceowner)|Cambia el propietario en contexto de una barra de controles.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CControlBar::m_bAutoDelete](#m_bautodelete)|Si es distinto de cero, el objeto `CControlBar` se elimina cuando se destruye la barra de controles de Windows.|
|[CControlBar::m_pInPlaceOwner](#m_pinplaceowner)|Propietario en contexto de la barra de controles.|

## <a name="remarks"></a>Observaciones

Una barra de controles es una ventana que suele estar alineada a la izquierda o a la derecha de una ventana de marco. Puede contener elementos secundarios que son controles basados en HWND, que son ventanas que generan y responden a mensajes de Windows, o elementos no basados en HWND, que no son ventanas y se administran mediante código de aplicación o código de marco de trabajo. Los cuadros de lista y los controles de edición son ejemplos de controles basados en HWND; Los paneles de barra de estado y los botones de mapa de bits son ejemplos de controles no basados en HWND.

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

## <a name="ccontrolbarcalcdynamiclayout"></a><a name="calcdynamiclayout"></a>CControlBar::CalcDynamicLayout

El marco de trabajo llama a esta función miembro para calcular las dimensiones de una barra de herramientas dinámica.

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>Parámetros

*nLongitud*<br/>
La dimensión solicitada de la barra de control, horizontal o vertical, dependiendo de *dwMode*.

*nMode*<br/>
Los siguientes indicadores predefinidos se utilizan para determinar el alto y el ancho de la barra de control dinámica. Utilice el operador OR (&#124;) bit a bit para combinar los indicadores.

|Indicadores del modo de diseño|Qué significa|
|-----------------------|-------------------|
|LM_STRETCH|Indica si la barra de control debe estirarse hasta el tamaño del marco. Establezca si la barra no es una barra de acoplamiento (no disponible para acoplamiento). No se establece cuando la barra está acoplada o flotante (disponible para acoplamiento). Si se establece, LM_STRETCH omite *nLength* y devuelve dimensiones basadas en el estado LM_HORZ. LM_STRETCH funciona de forma similar al parámetro *bStretch* utilizado en [CalcFixedLayout](#calcfixedlayout); ver que la función miembro para obtener más información sobre la relación entre el estiramiento y la orientación.|
|LM_HORZ|Indica que la barra está orientada horizontal o verticalmente. Establezca si la barra está orientada horizontalmente y si está orientada verticalmente, no se establece. LM_HORZ funciona de forma similar al parámetro *bHorz* utilizado en [CalcFixedLayout](#calcfixedlayout); ver que la función miembro para obtener más información sobre la relación entre el estiramiento y la orientación.|
|LM_MRUWIDTH|Anchura dinámica utilizada más recientemente. Ignora el parámetro *nLength* y utiliza el ancho utilizado más recientemente.|
|LM_HORZDOCK|Dimensiones acopladas horizontales. Ignora el parámetro *nLength* y devuelve el tamaño dinámico con el ancho más grande.|
|LM_VERTDOCK|Dimensiones verticales acopladas. Ignora el parámetro *nLength* y devuelve el tamaño dinámico con la altura más grande.|
|LM_LENGTHY|Establezca si *nLength* indica altura (dirección Y) en lugar de anchura.|
|LM_COMMIT|Restablece LM_MRUWIDTH al ancho actual de la barra de control flotante.|

### <a name="return-value"></a>Valor devuelto

El tamaño de la barra de control, en píxeles, de un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.

### <a name="remarks"></a>Observaciones

Invalide esta función miembro para proporcionar su `CControlBar`propio diseño dinámico en las clases que deriva de . Clases MFC `CControlBar`derivadas de , como [CToolbar](../../mfc/reference/ctoolbar-class.md), invalidar esta función miembro y proporcionar su propia implementación.

## <a name="ccontrolbarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CControlBar::CalcFixedLayout

Llame a esta función miembro para calcular el tamaño horizontal de una barra de control.

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parámetros

*bStretch*<br/>
Indica si la barra debe estirarse hasta el tamaño del marco. El parámetro *bStretch* es distinto de cero cuando la barra no es una barra de acoplamiento (no disponible para el acoplamiento) y es 0 cuando está acoplada o flotante (disponible para acoplamiento).

*bHorz*<br/>
Indica que la barra está orientada horizontal o verticalmente. El parámetro *bHorz* es distinto de cero si la barra está orientada horizontalmente y es 0 si está orientada verticalmente.

### <a name="return-value"></a>Valor devuelto

El tamaño de la barra `CSize` de control, en píxeles, de un objeto.

### <a name="remarks"></a>Observaciones

Las barras de control, como las barras de herramientas, pueden estirarse horizontal o verticalmente para acomodar los botones contenidos en la barra de control.

Si *bStretch* es TRUE, estire la cota a lo largo de la orientación proporcionada por *bHorz*. En otras palabras, si *bHorz* es FALSE, la barra de control se estira verticalmente. Si *bStretch* es FALSE, no se produce ningún estiramiento. En la tabla siguiente se muestran las posibles permutaciones y los estilos de barra de control resultantes de *bStretch* y *bHorz*.

|bStretch|bHorz|Estiramiento|Orientación|Acoplamiento/No acoplamiento|
|--------------|-----------|----------------|-----------------|--------------------------|
|TRUE|TRUE|Estiramiento horizontal|Orientado horizontalmente|No atracar|
|TRUE|FALSE|Estiramiento vertical|Orientado verticalmente|No atracar|
|FALSE|TRUE|No hay estiramiento disponible|Orientado horizontalmente|Acoplamiento|
|FALSE|FALSE|No hay estiramiento disponible|Orientado verticalmente|Acoplamiento|

## <a name="ccontrolbarcalcinsiderect"></a><a name="calcinsiderect"></a>CControlBar::CalcInsideRect

El marco de trabajo llama a esta función para calcular el área de cliente de la barra de control.

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
Contiene las dimensiones actuales de la barra de control; incluyendo las fronteras.

*bHorz*<br/>
Indica que la barra está orientada horizontal o verticalmente. El parámetro *bHorz* es distinto de cero si la barra está orientada horizontalmente y es 0 si está orientada verticalmente.

### <a name="remarks"></a>Observaciones

Esta función se llama antes de pintar la barra de control.

Reemplace esta función para personalizar la representación de los bordes y la barra de pinzamiento de la barra de control.

## <a name="ccontrolbarccontrolbar"></a><a name="ccontrolbar"></a>CControlBar::CControlBar

Construye un objeto `CControlBar`.

```
CControlBar();
```

## <a name="ccontrolbardopaint"></a><a name="dopaint"></a>CControlBar::DoPaint

Llamado por el marco de trabajo para representar los bordes y la barra de pinzamiento de la barra de control.

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Apunta al contexto del dispositivo que se utilizará para representar los bordes y el pinzamiento de la barra de control.

### <a name="remarks"></a>Observaciones

Reemplace esta función para personalizar el comportamiento del dibujo de la barra de control.

Otro método de personalización consiste en invalidar las `DrawBorders` funciones y `DrawGripper` agregar código de dibujo personalizado para los bordes y pinzamiento. Dado que el método `DoPaint` predeterminado llama a `DoPaint` estos métodos, no es necesaria una invalidación de.

## <a name="ccontrolbardrawborders"></a><a name="drawborders"></a>CControlBar::DrawBorders

Llamado por el marco de trabajo para representar los bordes de la barra de control.

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Señala el contexto del dispositivo que se utilizará para representar los bordes de la barra de control.

*Rect*<br/>
Objeto `CRect` que contiene las dimensiones de la barra de control.

### <a name="remarks"></a>Observaciones

Reemplace esta función para personalizar la apariencia de los bordes de la barra de control.

## <a name="ccontrolbardrawgripper"></a><a name="drawgripper"></a>CControlBar::DrawGripper

Llamado por el marco de trabajo para representar el pinzamiento de la barra de control.

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Apunta al contexto del dispositivo que se utilizará para representar el pinzamiento de la barra de control.

*Rect*<br/>
Objeto `CRect` que contiene las cotas de la pinza de la barra de control.

### <a name="remarks"></a>Observaciones

Reemplace esta función para personalizar la apariencia del pinzamiento de la barra de control.

## <a name="ccontrolbarenabledocking"></a><a name="enabledocking"></a>CControlBar::EnableDocking

Llame a esta función para permitir que se acopla una barra de control.

```cpp
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parámetros

*dwDockStyle*<br/>
Especifica si la barra de control admite el acoplamiento y los lados de su ventana primaria a los que se puede acoplar la barra de control, si se admite. Puede ser uno o más de los siguientes:

- CBRS_ALIGN_TOP Permite el acoplamiento en la parte superior del área de cliente.

- CBRS_ALIGN_BOTTOM Permite el acoplamiento en la parte inferior del área de cliente.

- CBRS_ALIGN_LEFT Permite el acoplamiento en el lado izquierdo del área de cliente.

- CBRS_ALIGN_RIGHT Permite el acoplamiento en el lado derecho del área de cliente.

- CBRS_ALIGN_ANY Permite el acoplamiento en cualquier lado del área de cliente.

- CBRS_FLOAT_MULTI Permite flotar varias barras de control en una sola ventana de marco pequeño.

Si 0 (es decir, que indica que no hay marcas), la barra de control no se acoplará.

### <a name="remarks"></a>Observaciones

Los lados especificados deben coincidir con uno de los lados habilitados para el acoplamiento en la ventana de marco de destino, o la barra de control no se puede acoplar a esa ventana de marco.

## <a name="ccontrolbargetbarstyle"></a><a name="getbarstyle"></a>CControlBar::GetBarStyle

Llame a esta función para determinar qué **CBRS_** (estilos de barra de control) se establece actualmente para la barra de control.

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>Valor devuelto

Los parámetros actuales **de CBRS_** (estilos de barra de control) de la barra de control. Consulte [CControlBar::SetBarStyle](#setbarstyle) para obtener la lista completa de estilos disponibles.

### <a name="remarks"></a>Observaciones

No controla **WS_** estilos (estilo de ventana).

## <a name="ccontrolbargetborders"></a><a name="getborders"></a>CControlBar::GetBorders

Devuelve los valores de borde actuales de la barra de control.

```
CRect GetBorders() const;
```

### <a name="return-value"></a>Valor devuelto

Objeto `CRect` que contiene el ancho actual (en píxeles) de cada lado del objeto de barra de control. Por ejemplo, el valor del miembro *izquierdo,* de [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto, es el ancho del borde izquierdo.

## <a name="ccontrolbargetcount"></a><a name="getcount"></a>CControlBar::GetCount

Devuelve el número de elementos `CControlBar` que no son HWND en el objeto.

```
int GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos que `CControlBar` no son HWND en el objeto. Esta función devuelve 0 para un [CDialogBar](../../mfc/reference/cdialogbar-class.md) objeto.

### <a name="remarks"></a>Observaciones

El tipo del elemento depende del objeto derivado: paneles para [CStatusBar](../../mfc/reference/cstatusbar-class.md) objetos y botones y separadores para [CToolBar](../../mfc/reference/ctoolbar-class.md) objetos.

## <a name="ccontrolbargetdockingframe"></a><a name="getdockingframe"></a>CControlBar::GetDockingFrame

Llame a esta función miembro para obtener un puntero a la ventana de marco actual a la que está acoplada la barra de control.

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a una ventana de marco si se realiza correctamente; NULL.

Si la barra de control no está acoplada a una ventana de marco (es decir, si la barra de control está flotante), esta función devolverá un puntero a su elemento primario [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md).

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de las barras de control acoplables, vea [CControlBar::EnableDocking](#enabledocking) y [CFrameWnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar).

## <a name="ccontrolbarisfloating"></a><a name="isfloating"></a>CControlBar::IsFloating

Llame a esta función miembro para determinar si la barra de control es flotante o acoplada.

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la barra de control está flotante; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Para cambiar el estado de una barra de control de acoplada a flotante, llame a [CFrameWnd::FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar).

## <a name="ccontrolbarm_bautodelete"></a><a name="m_bautodelete"></a>CControlBar::m_bAutoDelete

Si es distinto de cero, el objeto `CControlBar` se elimina cuando se destruye la barra de controles de Windows.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Observaciones

*m_bAutoDelete* es una variable pública de tipo BOOL.

Normalmente, un objeto de barra de control se incrusta en un objeto de ventana de marco. En este caso, *m_bAutoDelete* es 0 porque el objeto de barra de control incrustado se destruye cuando se destruye la ventana de marco.

Establezca esta variable en un valor `CControlBar` distinto de cero si asigna un objeto en el montón y no tiene previsto llamar a **delete**.

## <a name="ccontrolbarm_pinplaceowner"></a><a name="m_pinplaceowner"></a>CControlBar::m_pInPlaceOwner

Propietario en contexto de la barra de controles.

```
CWnd* m_pInPlaceOwner;
```

## <a name="ccontrolbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CControlBar::OnUpdateCmdUI

El marco de trabajo llama a esta función miembro para actualizar el estado de la barra de herramientas o la barra de estado.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>Parámetros

*pTarget*<br/>
Apunta a la ventana de marco principal de la aplicación. Este puntero se utiliza para enrutar mensajes de actualización.

*bDisableIfNoHndler*<br/>
Marcador que indica si un control que no tiene ningún controlador de actualización debe mostrarse automáticamente como deshabilitado.

### <a name="remarks"></a>Observaciones

Para actualizar un botón o panel individual, use la macro ON_UPDATE_COMMAND_UI del mapa de mensajes para establecer un controlador de actualizaciones de forma adecuada. Consulte [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) para obtener más información sobre el uso de esta macro.

`OnUpdateCmdUI`es llamado por el marco de trabajo cuando la aplicación está inactiva. La ventana de marco que se va a actualizar debe ser una ventana secundaria, al menos indirectamente, de una ventana de marco visible. `OnUpdateCmdUI`es un avanzado reemplazable.

## <a name="ccontrolbarsetbarstyle"></a><a name="setbarstyle"></a>CControlBar::SetBarStyle

Llame a esta función para establecer los estilos **de CBRS_** deseados para la barra de control.

```cpp
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Los estilos deseados para la barra de control. Puede ser uno o más de los siguientes:

- CBRS_ALIGN_TOP Permite que la barra de control se acopla a la parte superior del área de cliente de una ventana de marco.

- CBRS_ALIGN_BOTTOM Permite que la barra de control se acopla a la parte inferior del área de cliente de una ventana de marco.

- CBRS_ALIGN_LEFT Permite que la barra de control se acopla al lado izquierdo del área de cliente de una ventana de marco.

- CBRS_ALIGN_RIGHT Permite que la barra de control se acopla al lado derecho del área de cliente de una ventana de marco.

- CBRS_ALIGN_ANY Permite que la barra de control se acopla a cualquier lado del área de cliente de una ventana de marco.

- CBRS_BORDER_TOP Hace que se dibuje un borde en el borde superior de la barra de control cuando sería visible.

- CBRS_BORDER_BOTTOM Hace que se dibuje un borde en el borde inferior de la barra de control cuando sería visible.

- CBRS_BORDER_LEFT Hace que se dibuje un borde en el borde izquierdo de la barra de control cuando sería visible.

- CBRS_BORDER_RIGHT Hace que un borde se dibuje en el borde derecho de la barra de control cuando sería visible.

- CBRS_FLOAT_MULTI Permite flotar varias barras de control en una sola ventana de marco pequeño.

- CBRS_TOOLTIPS Hace que se muestren las sugerencias de herramientas para la barra de control.

- CBRS_FLYBY Hace que el texto del mensaje se actualice al mismo tiempo que las sugerencias de herramientas.

- CBRS_GRIPPER Hace que un pinzamiento, similar `CReBar` a la utilizada `CControlBar`en las bandas de un objeto, se dibuje para cualquier clase derivada.

### <a name="remarks"></a>Observaciones

No afecta a la **configuración de WS_** (estilo de ventana).

## <a name="ccontrolbarsetborders"></a><a name="setborders"></a>CControlBar::SetBorders

Llame a esta función para establecer el tamaño de los bordes de la barra de control.

```cpp
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
La altura (en píxeles) del borde superior de la barra de control.

*cxRight*<br/>
El ancho (en píxeles) del borde derecho de la barra de control.

*cyBottom*<br/>
La altura (en píxeles) del borde inferior de la barra de control.

*lpRect*<br/>
Puntero a un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que contiene el ancho actual (en píxeles) de cada borde del objeto de barra de control.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establecen los bordes superior e inferior de la barra de control en 5 píxeles y los bordes izquierdo y derecho en 2 píxeles:

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

## <a name="ccontrolbarsetinplaceowner"></a><a name="setinplaceowner"></a>CControlBar::SetInPlaceOwner

Cambia el propietario en contexto de una barra de controles.

```cpp
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero a un objeto `CWnd` .

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Vea también

[CTRLBARS de ejemplo de MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CToolBar (clase)](../../mfc/reference/ctoolbar-class.md)<br/>
[Clase CDialogBar](../../mfc/reference/cdialogbar-class.md)<br/>
[Clase CStatusBar](../../mfc/reference/cstatusbar-class.md)<br/>
[Clase CReBar](../../mfc/reference/crebar-class.md)
