---
title: CStatusBarCtrl (clase)
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
- AFXCMN/CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::Create
- AFXCMN/CStatusBarCtrl::CreateEx
- AFXCMN/CStatusBarCtrl::DrawItem
- AFXCMN/CStatusBarCtrl::GetBorders
- AFXCMN/CStatusBarCtrl::GetIcon
- AFXCMN/CStatusBarCtrl::GetParts
- AFXCMN/CStatusBarCtrl::GetRect
- AFXCMN/CStatusBarCtrl::GetText
- AFXCMN/CStatusBarCtrl::GetTextLength
- AFXCMN/CStatusBarCtrl::GetTipText
- AFXCMN/CStatusBarCtrl::IsSimple
- AFXCMN/CStatusBarCtrl::SetBkColor
- AFXCMN/CStatusBarCtrl::SetIcon
- AFXCMN/CStatusBarCtrl::SetMinHeight
- AFXCMN/CStatusBarCtrl::SetParts
- AFXCMN/CStatusBarCtrl::SetSimple
- AFXCMN/CStatusBarCtrl::SetText
- AFXCMN/CStatusBarCtrl::SetTipText
helpviewer_keywords:
- CStatusBarCtrl [MFC], CStatusBarCtrl
- CStatusBarCtrl [MFC], Create
- CStatusBarCtrl [MFC], CreateEx
- CStatusBarCtrl [MFC], DrawItem
- CStatusBarCtrl [MFC], GetBorders
- CStatusBarCtrl [MFC], GetIcon
- CStatusBarCtrl [MFC], GetParts
- CStatusBarCtrl [MFC], GetRect
- CStatusBarCtrl [MFC], GetText
- CStatusBarCtrl [MFC], GetTextLength
- CStatusBarCtrl [MFC], GetTipText
- CStatusBarCtrl [MFC], IsSimple
- CStatusBarCtrl [MFC], SetBkColor
- CStatusBarCtrl [MFC], SetIcon
- CStatusBarCtrl [MFC], SetMinHeight
- CStatusBarCtrl [MFC], SetParts
- CStatusBarCtrl [MFC], SetSimple
- CStatusBarCtrl [MFC], SetText
- CStatusBarCtrl [MFC], SetTipText
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
ms.openlocfilehash: 8c33aa4d77eeeeca69e50dc63982ff4d7e8bd505
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426358"
---
# <a name="cstatusbarctrl-class"></a>CStatusBarCtrl (clase)

Proporciona la funcionalidad del control de barra de estado común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CStatusBarCtrl : public CWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStatusBarCtrl:: CStatusBarCtrl](#cstatusbarctrl)|Construye un objeto `CStatusBarCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStatusBarCtrl:: Create](#create)|Crea un control de barra de estado y lo adjunta a un objeto `CStatusBarCtrl`.|
|[CStatusBarCtrl:: CreateEx](#createex)|Crea un control de barra de estado con los estilos extendidos de Windows especificados y lo adjunta a un objeto `CStatusBarCtrl`.|
|[CStatusBarCtrl::D rawItem](#drawitem)|Se le llama cuando cambia el aspecto visual de un control de barra de estado de dibujo del propietario.|
|[CStatusBarCtrl:: GetBorders](#getborders)|Recupera los anchos actuales de los bordes horizontal y vertical de un control de barra de estado.|
|[CStatusBarCtrl:: GetIcon](#geticon)|Recupera el icono de un elemento (también conocido como panel) en el control de la barra de estado actual.|
|[CStatusBarCtrl:: GetParts](#getparts)|Recupera un recuento de los elementos de un control de barra de estado.|
|[CStatusBarCtrl:: GetRect](#getrect)|Recupera el rectángulo delimitador de un elemento de un control de barra de estado.|
|[CStatusBarCtrl:: GetText](#gettext)|Recupera el texto de la parte especificada de un control de barra de estado.|
|[CStatusBarCtrl:: GetTextLength](#gettextlength)|Recupera la longitud, en caracteres, del texto de la parte especificada de un control de barra de estado.|
|[CStatusBarCtrl:: GetTipText](#gettiptext)|Recupera el texto de información sobre herramientas de un panel en una barra de estado.|
|[CStatusBarCtrl:: IsSimple](#issimple)|Comprueba un control de ventana de estado para determinar si está en modo simple.|
|[CStatusBarCtrl:: SetBkColor](#setbkcolor)|Establece el color de fondo de una barra de estado.|
|[CStatusBarCtrl:: SetIcon](#seticon)|Establece el icono de un panel en una barra de estado.|
|[CStatusBarCtrl:: SetMinHeight](#setminheight)|Establece el alto mínimo del área de dibujo de un control de barra de estado.|
|[CStatusBarCtrl:: SetParts](#setparts)|Establece el número de elementos de un control de barra de estado y la coordenada del borde derecho de cada elemento.|
|[CStatusBarCtrl:: SetSimple](#setsimple)|Especifica si un control de barra de estado muestra texto simple o muestra todas las partes de control establecidas por una llamada anterior a `SetParts`.|
|[CStatusBarCtrl:: SetText](#settext)|Establece el texto en un elemento determinado de un control de barra de estado.|
|[CStatusBarCtrl:: SetTipText](#settiptext)|Establece el texto de información sobre herramientas para un panel en una barra de estado.|

## <a name="remarks"></a>Observaciones

Un "control de barra de estado" es una ventana horizontal que se muestra normalmente en la parte inferior de una ventana primaria, en la que una aplicación puede mostrar diversos tipos de información de estado. El control de barra de estado se puede dividir en partes para mostrar más de un tipo de información.

Este control (y, por tanto, la clase `CStatusBarCtrl`) solo está disponible para programas que se ejecutan en Windows 95/98 y Windows NT versión 3,51 y versiones posteriores.

Para obtener más información sobre el uso de `CStatusBarCtrl`, vea [controles](../../mfc/controls-mfc.md) y [usar CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatusBarCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="create"></a>CStatusBarCtrl:: Create

Crea un control de barra de estado y lo adjunta a un objeto `CStatusBarCtrl`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de barra de estado. Aplique cualquier combinación de estilos de control de barra de estado enumerada en [estilos de control comunes](/windows/win32/Controls/common-control-styles) en el Windows SDK. Este parámetro debe incluir el estilo de WS_CHILD. También debe incluir el estilo WS_VISIBLE.

*Rect*<br/>
Especifica el tamaño y la posición del control de la barra de estado. Puede ser un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) o una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) .

*pParentWnd*<br/>
Especifica la ventana primaria del control de barra de estado, normalmente una `CDialog`. No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de la barra de estado.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Una `CStatusBarCtrl` se crea en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a `Create`, que crea el control de barra de estado y lo adjunta al objeto `CStatusBarCtrl`.

La posición predeterminada de una ventana de estado está a lo largo de la parte inferior de la ventana primaria, pero puede especificar el estilo de CCS_TOP para que aparezca en la parte superior del área de cliente de la ventana primaria. Puede especificar el estilo de SBARS_SIZEGRIP para incluir un control de tamaño en el extremo derecho de la ventana de estado. No se recomienda combinar los estilos CCS_TOP y SBARS_SIZEGRIP, porque el control de tamaño resultante no es funcional, aunque el sistema lo dibuje en la ventana de estado.

Para crear una barra de estado con estilos de ventana extendidos, llame a [CStatusBarCtrl:: CreateEx](#createex) en lugar de a `Create`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]

##  <a name="createex"></a>CStatusBarCtrl:: CreateEx

Crea un control (una ventana secundaria) y lo asocia al objeto `CStatusBarCtrl`.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwExStyle*<br/>
Especifica el estilo extendido del control que se va a crear. Para obtener una lista de los estilos extendidos de Windows, consulte el parámetro *dwExStyle* para [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

*dwStyle*<br/>
Especifica el estilo del control de barra de estado. Aplique cualquier combinación de estilos de control de barra de estado enumerada en [estilos de control comunes](/windows/win32/Controls/common-control-styles) en el Windows SDK. Este parámetro debe incluir el estilo de WS_CHILD. También debe incluir el estilo WS_VISIBLE.

*Rect*<br/>
Referencia a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que describe el tamaño y la posición de la ventana que se va a crear, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario del control.

*nID*<br/>
IDENTIFICADOR de la ventana de elemento secundario del control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Use `CreateEx` en lugar de [Create](#create) para aplicar los estilos extendidos de Windows, especificados por el **WS_EX_** de prefacio de estilo extendido de Windows.

##  <a name="cstatusbarctrl"></a>CStatusBarCtrl:: CStatusBarCtrl

Construye un objeto `CStatusBarCtrl`.

```
CStatusBarCtrl();
```

##  <a name="drawitem"></a>CStatusBarCtrl::D rawItem

Lo llama el marco de trabajo cuando cambia el aspecto visual de un control de barra de estado de dibujo del propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Puntero largo a una estructura [drawitemstruct (](/windows/win32/api/winuser/ns-winuser-drawitemstruct) que contiene información sobre el tipo de dibujo necesario.

### <a name="remarks"></a>Observaciones

El miembro `itemAction` de la estructura `DRAWITEMSTRUCT` define la acción de dibujo que se va a realizar.

De forma predeterminada, esta función miembro no hace nada. Invalide esta función miembro para implementar el dibujo de un objeto de `CStatusBarCtrl` dibujado por el propietario.

La aplicación debe restaurar todos los objetos de la interfaz de dispositivo gráfico (GDI) seleccionados para el contexto de presentación proporcionado en *lpDrawItemStruct* antes de que esta función miembro finalice.

##  <a name="getborders"></a>CStatusBarCtrl:: GetBorders

Recupera el ancho actual del control de la barra de estado de los bordes horizontales y verticales y del espacio entre los rectángulos.

```
BOOL GetBorders(int* pBorders) const;

BOOL GetBorders(
    int& nHorz,
    int& nVert,
    int& nSpacing) const;
```

### <a name="parameters"></a>Parámetros

*pBorders*<br/>
Dirección de una matriz de enteros con tres elementos. El primer elemento recibe el ancho del borde horizontal, el segundo recibe el ancho del borde vertical y el tercero recibe el ancho del borde entre los rectángulos.

*nHorz*<br/>
Referencia a un entero que recibe el ancho del borde horizontal.

*nvertir*<br/>
Referencia a un entero que recibe el ancho del borde vertical.

*nSpacing*<br/>
Referencia a un entero que recibe el ancho del borde entre rectángulos.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Estos bordes determinan el espaciado entre el borde exterior del control y los rectángulos dentro del control que contienen texto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]

##  <a name="geticon"></a>CStatusBarCtrl:: GetIcon

Recupera el icono de un elemento (también conocido como panel) en el control de la barra de estado actual.

```
HICON GetIcon(int iPart) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*iPart*|de Índice de base cero del elemento que contiene el icono que se va a recuperar. Si este parámetro es-1, se supone que la barra de estado es una barra de estado de modo simple.|

### <a name="return-value"></a>Valor devuelto

Identificador del icono si el método se realiza correctamente; de lo contrario, es NULL.

### <a name="remarks"></a>Observaciones

Este método envía el mensaje de [SB_GETICON](/windows/win32/Controls/sb-geticon) , que se describe en el Windows SDK.

Un control de barra de estado se compone de una fila de paneles de salida de texto, que también se conocen como elementos. Para obtener más información sobre la barra de estado, vea implementación de la [barra de estado en MFC](../../mfc/status-bar-implementation-in-mfc.md) y [establecer el modo de un objeto CStatusBarCtrl](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define una variable, `m_statusBar`, que se usa para tener acceso al control de barra de estado actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se copia un icono en dos paneles del control de la barra de estado actual. En una sección anterior del ejemplo de código, creamos un control de barra de estado con tres paneles y, a continuación, agregamos un icono al primer panel. En este ejemplo se recupera el icono del primer panel y, a continuación, se agrega al segundo y tercer panel.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]

##  <a name="getparts"></a>CStatusBarCtrl:: GetParts

Recupera un recuento de los elementos de un control de barra de estado.

```
int GetParts(
    int nParts,
    int* pParts) const;
```

### <a name="parameters"></a>Parámetros

*nParts*<br/>
Número de elementos para los que se van a recuperar las coordenadas. Si este parámetro es mayor que el número de partes del control, el mensaje solo recupera las coordenadas de los elementos existentes.

*pParts*<br/>
Dirección de una matriz de enteros que tiene el mismo número de elementos que el número de partes especificado por *nParts*. Cada elemento de la matriz recibe la coordenada del cliente del borde derecho del elemento correspondiente. Si un elemento se establece en-1, la posición del borde derecho de esa parte se extiende hasta el borde derecho de la barra de estado.

### <a name="return-value"></a>Valor devuelto

El número de elementos del control si se realiza correctamente, o bien cero en caso contrario.

### <a name="remarks"></a>Observaciones

Esta función miembro también recupera la coordenada del borde derecho del número determinado de partes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]

##  <a name="getrect"></a>CStatusBarCtrl:: GetRect

Recupera el rectángulo delimitador de un elemento de un control de barra de estado.

```
BOOL GetRect(
    int nPane,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*nPane*<br/>
Índice de base cero de la parte cuyo rectángulo delimitador se va a recuperar.

*lpRect*<br/>
Dirección de una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que recibe el rectángulo delimitador.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]

##  <a name="gettext"></a>CStatusBarCtrl:: GetText

Recupera el texto de la parte especificada de un control de barra de estado.

```
CString GetText(
    int nPane,
    int* pType = NULL) const;

int GetText(
    LPCTSTR lpszText,
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
Dirección del búfer que recibe el texto. Este parámetro es una cadena terminada en NULL.

*nPane*<br/>
Índice de base cero del elemento del que se va a recuperar el texto.

*pType*<br/>
Puntero a un entero que recibe la información de tipo. El tipo puede ser uno de estos valores:

- **0** el texto se dibuja con un borde para que aparezca inferior al plano de la barra de estado.

- SBT_NOBORDERS el texto se dibuja sin bordes.

- SBT_POPOUT el texto se dibuja con un borde para que aparezca más arriba que el plano de la barra de estado.

- SBT_OWNERDRAW si el texto tiene el tipo de dibujo SBT_OWNERDRAW, *pType* recibe este mensaje y devuelve el valor de 32 bits asociado al texto en lugar de la longitud y el tipo de operación.

### <a name="return-value"></a>Valor devuelto

La longitud, en caracteres, del texto o un objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene el texto actual.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]

##  <a name="gettextlength"></a>CStatusBarCtrl:: GetTextLength

Recupera la longitud, en caracteres, del texto de la parte especificada de un control de barra de estado.

```
int GetTextLength(
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>Parámetros

*nPane*<br/>
Índice de base cero del elemento del que se va a recuperar el texto.

*pType*<br/>
Puntero a un entero que recibe la información de tipo. El tipo puede ser uno de estos valores:

- **0** el texto se dibuja con un borde para que aparezca inferior al plano de la barra de estado.

- SBT_NOBORDERS el texto se dibuja sin bordes.

- SBT_OWNERDRAW el texto se dibuja en la ventana primaria.

- SBT_POPOUT el texto se dibuja con un borde para que aparezca más arriba que el plano de la barra de estado.

### <a name="return-value"></a>Valor devuelto

La longitud, en caracteres, del texto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]

##  <a name="gettiptext"></a>CStatusBarCtrl:: GetTipText

Recupera el texto de información sobre herramientas de un panel en una barra de estado.

```
CString GetTipText(int nPane) const;
```

### <a name="parameters"></a>Parámetros

*nPane*<br/>
Índice de base cero del panel de la barra de estado para recibir el texto de información sobre herramientas.

### <a name="return-value"></a>Valor devuelto

Objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene el texto que se va a utilizar en la información sobre herramientas.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [SB_GETTIPTEXT](/windows/win32/Controls/sb-gettiptext)de mensajes de Win32, como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]

##  <a name="issimple"></a>CStatusBarCtrl:: IsSimple

Comprueba un control de ventana de estado para determinar si está en modo simple.

```
BOOL IsSimple() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el control de ventana de estado está en modo simple; de lo contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [SB_ISSIMPLE](/windows/win32/Controls/sb-issimple)de mensajes de Win32, como se describe en el Windows SDK.

##  <a name="setbkcolor"></a>CStatusBarCtrl:: SetBkColor

Establece el color de fondo de una barra de estado.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parámetros

*compra*<br/>
Valor COLORREF que especifica el nuevo color de fondo. Especifique el valor CLR_DEFAULT para que la barra de estado use su color de fondo predeterminado.

### <a name="return-value"></a>Valor devuelto

Valor de [COLORREF](/windows/win32/gdi/colorref) que representa el color de fondo predeterminado anterior.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [SB_SETBKCOLOR](/windows/win32/Controls/sb-setbkcolor)de mensajes de Win32, como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]

##  <a name="seticon"></a>CStatusBarCtrl:: SetIcon

Establece el icono de un panel en una barra de estado.

```
BOOL SetIcon(
    int nPane,
    HICON hIcon);
```

### <a name="parameters"></a>Parámetros

*nPane*<br/>
Índice de base cero del panel que recibirá el icono. Si este parámetro es-1, se supone que la barra de estado es una barra de estado simple.

*hIcon*<br/>
Identificador del icono que se va a establecer. Si este valor es NULL, el icono se quita del elemento.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [SB_SETICON](/windows/win32/Controls/sb-seticon)de mensajes de Win32, como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CStatusBarCtrl:: SetBkColor](#setbkcolor).

##  <a name="setminheight"></a>CStatusBarCtrl:: SetMinHeight

Establece el alto mínimo del área de dibujo de un control de barra de estado.

```
void SetMinHeight(int nMin);
```

### <a name="parameters"></a>Parámetros

*Nmín.*<br/>
Alto mínimo, en píxeles, del control.

### <a name="remarks"></a>Observaciones

El alto mínimo es la suma de *nmín.* y dos veces el ancho, en píxeles, del borde vertical del control de la barra de estado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]

##  <a name="setparts"></a>CStatusBarCtrl:: SetParts

Establece el número de elementos de un control de barra de estado y la coordenada del borde derecho de cada elemento.

```
BOOL SetParts(
    int nParts,
    int* pWidths);
```

### <a name="parameters"></a>Parámetros

*nParts*<br/>
Número de elementos que se van a establecer. El número de elementos no puede ser mayor que 255.

*pWidths*<br/>
Dirección de una matriz de enteros que tiene el mismo número de elementos que las partes especificadas por *nParts*. Cada elemento de la matriz especifica la posición, en coordenadas de cliente, del borde derecho de la parte correspondiente. Si un elemento es-1, la posición del borde derecho de esa parte se extiende hasta el borde derecho del control.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]

##  <a name="setsimple"></a>CStatusBarCtrl:: SetSimple

Especifica si un control de barra de estado muestra texto simple o muestra todas las partes del control establecidas por una llamada anterior a [SetParts](#setparts).

```
BOOL SetSimple(BOOL bSimple = TRUE);
```

### <a name="parameters"></a>Parámetros

*bSimple*<br/>
de Marca de tipo de presentación. Si este parámetro es TRUE, el control muestra texto simple; Si es FALSE, muestra varias partes.

### <a name="return-value"></a>Valor devuelto

Siempre devuelve 0.

### <a name="remarks"></a>Observaciones

Si la aplicación cambia el control de la barra de estado de no simple a simple, o viceversa, el sistema vuelve a dibujar inmediatamente el control.

##  <a name="settext"></a>CStatusBarCtrl:: SetText

Establece el texto en un elemento determinado de un control de barra de estado.

```
BOOL SetText(
    LPCTSTR lpszText,
    int nPane,
    int nType);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
Dirección de una cadena terminada en null que especifica el texto que se debe establecer. Si *ndeclaraciones* es SBT_OWNERDRAW, *lpszText* representa 32 bits de datos.

*nPane*<br/>
El índice de base cero del elemento que se debe establecer. Si este valor es 255, se asume que el control de barra de estado es un control simple que solo contiene un elemento.

*nType*<br/>
Tipo de operación de dibujo. Consulte [SB_SETTEXT mensaje](/windows/win32/Controls/sb-settext) para obtener una lista de valores posibles.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El mensaje invalida la parte del control que ha cambiado, lo que hace que muestre el nuevo texto cuando el control siguiente recibe el mensaje de WM_PAINT.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]

##  <a name="settiptext"></a>CStatusBarCtrl:: SetTipText

Establece el texto de información sobre herramientas para un panel en una barra de estado.

```
void SetTipText(
    int nPane,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Parámetros

*nPane*<br/>
Índice de base cero del panel de la barra de estado para recibir el texto de información sobre herramientas.

*pszTipText*<br/>
Puntero a una cadena que contiene el texto de la información sobre herramientas.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [SB_SETTIPTEXT](/windows/win32/Controls/sb-settiptext)de mensajes de Win32, como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]

## <a name="see-also"></a>Consulte también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl (clase)](../../mfc/reference/ctoolbarctrl-class.md)
