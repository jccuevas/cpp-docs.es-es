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
ms.openlocfilehash: 57d040a7efd87d384e0aaa6275593bc91f38cc86
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753036"
---
# <a name="cstatusbarctrl-class"></a>CStatusBarCtrl (clase)

Proporciona la funcionalidad del control de barra de estado común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CStatusBarCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStatusBarCtrl::CStatusBarCtrl](#cstatusbarctrl)|Construye un objeto `CStatusBarCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStatusBarCtrl::Crear](#create)|Crea un control de barra de `CStatusBarCtrl` estado y lo asocia a un objeto.|
|[CStatusBarCtrl::CreateEx](#createex)|Crea un control de barra de estado con los `CStatusBarCtrl` estilos extendidos de Windows especificados y lo asocia a un objeto.|
|[CStatusBarCtrl::DrawItem](#drawitem)|Se llama cuando cambia un aspecto visual de un control de barra de estado de dibujo por el propietario.|
|[CStatusBarCtrl::GetBorders](#getborders)|Recupera los anchos actuales de los bordes horizontal y vertical de un control de barra de estado.|
|[CStatusBarCtrl::GetIcon](#geticon)|Recupera el icono de una pieza (también conocido como panel) en el control de barra de estado actual.|
|[CStatusBarCtrl::GetParts](#getparts)|Recupera un recuento de las partes de un control de barra de estado.|
|[CStatusBarCtrl::GetRect](#getrect)|Recupera el rectángulo delimitador de una parte en un control de barra de estado.|
|[CStatusBarCtrl::GetText](#gettext)|Recupera el texto de la parte dada de un control de barra de estado.|
|[CStatusBarCtrl::GetTextLength](#gettextlength)|Recuperar la longitud, en caracteres, del texto de la parte dada de un control de barra de estado.|
|[CStatusBarCtrl::GetTipText](#gettiptext)|Recupera el texto de información sobre herramientas de un panel en una barra de estado.|
|[CStatusBarCtrl::IsSimple](#issimple)|Comprueba un control de ventana de estado para determinar si está en modo simple.|
|[CStatusBarCtrl::SetBkColor](#setbkcolor)|Establece el color de fondo en una barra de estado.|
|[CStatusBarCtrl::SetIcon](#seticon)|Establece el icono de un panel en una barra de estado.|
|[CStatusBarCtrl::SetMinHeight](#setminheight)|Establece la altura mínima del área de dibujo de un control de barra de estado.|
|[CStatusBarCtrl::SetParts](#setparts)|Establece el número de piezas en un control de barra de estado y la coordenada del borde derecho de cada pieza.|
|[CStatusBarCtrl::SetSimple](#setsimple)|Especifica si un control de barra de estado muestra texto simple `SetParts`o muestra todas las partes de control establecidas por una llamada anterior a .|
|[CStatusBarCtrl::SetText](#settext)|Establece el texto en un elemento determinado de un control de barra de estado.|
|[CStatusBarCtrl::SetTipText](#settiptext)|Establece el texto de información sobre herramientas de un panel en una barra de estado.|

## <a name="remarks"></a>Observaciones

Un "control de barra de estado" es una ventana horizontal, que normalmente se muestra en la parte inferior de una ventana primaria, en la que una aplicación puede mostrar varios tipos de información de estado. El control de barra de estado se puede dividir en partes para mostrar más de un tipo de información.

Este control (y, por lo tanto, la `CStatusBarCtrl` clase) solo está disponible para programas que se ejecutan en Windows 95/98 y Windows NT versión 3.51 y versiones posteriores.

Para obtener más `CStatusBarCtrl`información sobre el uso de , vea [Controles](../../mfc/controls-mfc.md) y uso de [CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatusBarCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

## <a name="cstatusbarctrlcreate"></a><a name="create"></a>CStatusBarCtrl::Crear

Crea un control de barra de `CStatusBarCtrl` estado y lo asocia a un objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de barra de estado. Aplique cualquier combinación de estilos de control de barra de estado enumerados en [Estilos](/windows/win32/Controls/common-control-styles) de control comunes en el Windows SDK. Este parámetro debe incluir el estilo WS_CHILD. También debe incluir el estilo WS_VISIBLE.

*Rect*<br/>
Especifica el tamaño y la posición del control de barra de estado. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](/windows/win32/api/windef/ns-windef-rect) estructura.

*pParentWnd*<br/>
Especifica la ventana primaria del control de `CDialog`barra de estado, normalmente un archivo . No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de barra de estado.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Se construye `CStatusBarCtrl` un en dos pasos. En primer lugar, llame `Create`al constructor y, a continuación, llame `CStatusBarCtrl` a , que crea el control de barra de estado y lo adjunta al objeto.

La posición predeterminada de una ventana de estado se encuentra en la parte inferior de la ventana primaria, pero puede especificar el estilo de CCS_TOP para que aparezca en la parte superior del área de cliente de la ventana primaria. Puede especificar el estilo de SBARS_SIZEGRIP para incluir un pinzamiento de tamaño en el extremo derecho de la ventana de estado. No se recomienda combinar los estilos CCS_TOP y SBARS_SIZEGRIP, ya que el pinzamiento de tamaño resultante no es funcional aunque el sistema lo dibuje en la ventana de estado.

Para crear una barra de estado con estilos de ventana `Create`extendidos, llame a [CStatusBarCtrl::CreateEx](#createex) en lugar de .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]

## <a name="cstatusbarctrlcreateex"></a><a name="createex"></a>CStatusBarCtrl::CreateEx

Crea un control (una ventana secundaria) `CStatusBarCtrl` y lo asocia con el objeto.

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
Especifica el estilo extendido del control que se está creando. Para obtener una lista de estilos de Windows extendidos, vea el *dwExStyle* parámetro para [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

*dwStyle*<br/>
Especifica el estilo del control de barra de estado. Aplique cualquier combinación de estilos de control de barra de estado enumerados en [Estilos](/windows/win32/Controls/common-control-styles) de control comunes en el Windows SDK. Este parámetro debe incluir el estilo WS_CHILD. También debe incluir el estilo WS_VISIBLE.

*Rect*<br/>
Una referencia a una estructura [RECT](/windows/win32/api/windef/ns-windef-rect) que describe el tamaño y la posición de la ventana que se va a crear, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario del control.

*nID*<br/>
Identificador de ventana secundaria del control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Se `CreateEx` usa en lugar de [Crear](#create) para aplicar estilos de Windows extendidos, especificados por el **prefacio**de estilo extendido de Windows WS_EX_ .

## <a name="cstatusbarctrlcstatusbarctrl"></a><a name="cstatusbarctrl"></a>CStatusBarCtrl::CStatusBarCtrl

Construye un objeto `CStatusBarCtrl`.

```
CStatusBarCtrl();
```

## <a name="cstatusbarctrldrawitem"></a><a name="drawitem"></a>CStatusBarCtrl::DrawItem

Llamado por el marco de trabajo cuando cambia un aspecto visual de un control de barra de estado de dibujo por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Puntero largo a una estructura [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) que contiene información sobre el tipo de dibujo necesario.

### <a name="remarks"></a>Observaciones

El `itemAction` miembro `DRAWITEMSTRUCT` de la estructura define la acción de dibujo que se va a realizar.

De forma predeterminada, esta función miembro no hace nada. Invalidar esta función miembro para implementar `CStatusBarCtrl` el dibujo para un objeto de dibujo del propietario.

La aplicación debe restaurar todos los objetos de interfaz de dispositivo gráfico (GDI) seleccionados para el contexto de presentación proporcionado en *lpDrawItemStruct* antes de que finalice esta función miembro.

## <a name="cstatusbarctrlgetborders"></a><a name="getborders"></a>CStatusBarCtrl::GetBorders

Recupera los anchos actuales del control de barra de estado de los bordes horizontaly vertical y del espacio entre rectángulos.

```
BOOL GetBorders(int* pBorders) const;

BOOL GetBorders(
    int& nHorz,
    int& nVert,
    int& nSpacing) const;
```

### <a name="parameters"></a>Parámetros

*pBorders*<br/>
Dirección de una matriz de enteros que tiene tres elementos. El primer elemento recibe el ancho del borde horizontal, el segundo recibe el ancho del borde vertical y el tercero recibe el ancho del borde entre rectángulos.

*nHorz*<br/>
Referencia a un entero que recibe el ancho del borde horizontal.

*nVert*<br/>
Referencia a un entero que recibe el ancho del borde vertical.

*nSpacing*<br/>
Referencia a un entero que recibe el ancho del borde entre rectángulos.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Estos bordes determinan el espaciado entre el borde exterior del control y los rectángulos dentro del control que contienen texto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]

## <a name="cstatusbarctrlgeticon"></a><a name="geticon"></a>CStatusBarCtrl::GetIcon

Recupera el icono de una pieza (también conocido como panel) en el control de barra de estado actual.

```
HICON GetIcon(int iPart) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*iPart*|[en] El índice de base cero de la pieza que contiene el icono que se va a recuperar. Si este parámetro es -1, se supone que la barra de estado es una barra de estado de modo simple.|

### <a name="return-value"></a>Valor devuelto

El identificador del icono si el método se realiza correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje SB_GETICON,](/windows/win32/Controls/sb-geticon) que se describe en el Windows SDK.

Un control de barra de estado consta de una fila de paneles de salida de texto, que también se conocen como partes. Para obtener más información acerca de la barra de estado, vea [Implementación](../../mfc/status-bar-implementation-in-mfc.md) de barra de estado en MFC y [Establecer el modo de un CStatusBarCtrl objeto](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).

### <a name="example"></a>Ejemplo

En el ejemplo de `m_statusBar`código siguiente se define una variable, , que se utiliza para tener acceso al control de barra de estado actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se copia un icono en dos paneles del control de barra de estado actual. En una sección anterior del ejemplo de código creamos un control de barra de estado con tres paneles y, a continuación, agregamos un icono al primer panel. En este ejemplo se recupera el icono del primer panel y, a continuación, se agrega al segundo y tercer panel.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]

## <a name="cstatusbarctrlgetparts"></a><a name="getparts"></a>CStatusBarCtrl::GetParts

Recupera un recuento de las partes de un control de barra de estado.

```
int GetParts(
    int nParts,
    int* pParts) const;
```

### <a name="parameters"></a>Parámetros

*nPartes*<br/>
Número de piezas para las que se van a recuperar coordenadas. Si este parámetro es mayor que el número de partes del control, el mensaje recupera las coordenadas solo para las piezas existentes.

*pParts*<br/>
Dirección de una matriz de enteros que tiene el mismo número de elementos que el número de partes especificadas por *nParts*. Cada elemento de la matriz recibe la coordenada de cliente del borde derecho de la parte correspondiente. Si un elemento se establece en - 1, la posición del borde derecho de esa pieza se extiende hasta el borde derecho de la barra de estado.

### <a name="return-value"></a>Valor devuelto

El número de partes en el control si se realiza correctamente, o cero en caso contrario.

### <a name="remarks"></a>Observaciones

Esta función miembro también recupera la coordenada del borde derecho del número dado de partes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]

## <a name="cstatusbarctrlgetrect"></a><a name="getrect"></a>CStatusBarCtrl::GetRect

Recupera el rectángulo delimitador de una parte en un control de barra de estado.

```
BOOL GetRect(
    int nPane,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*nPane*<br/>
El índice de base cero de la parte cuyo rectángulo delimitador se va a recuperar.

*lpRect*<br/>
Dirección de una estructura [RECT](/windows/win32/api/windef/ns-windef-rect) que recibe el rectángulo delimitador.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]

## <a name="cstatusbarctrlgettext"></a><a name="gettext"></a>CStatusBarCtrl::GetText

Recupera el texto de la parte dada de un control de barra de estado.

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
Dirección del búfer que recibe el texto. Este parámetro es una cadena terminada en null.

*nPane*<br/>
El índice de base cero de la pieza de la que se va a recuperar texto.

*pType*<br/>
Puntero a un entero que recibe la información de tipo. El tipo puede ser uno de estos valores:

- **0** El texto se dibuja con un borde que aparece más bajo que el plano de la barra de estado.

- SBT_NOBORDERS El texto se dibuja sin bordes.

- SBT_POPOUT El texto se dibuja con un borde para que aparezca más alto que el plano de la barra de estado.

- SBT_OWNERDRAW Si el texto tiene el tipo de dibujo SBT_OWNERDRAW, *pType* recibe este mensaje y devuelve el valor de 32 bits asociado al texto en lugar de la longitud y el tipo de operación.

### <a name="return-value"></a>Valor devuelto

La longitud, en caracteres, del texto o un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene el texto actual.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]

## <a name="cstatusbarctrlgettextlength"></a><a name="gettextlength"></a>CStatusBarCtrl::GetTextLength

Recupera la longitud, en caracteres, del texto de la parte dada de un control de barra de estado.

```
int GetTextLength(
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>Parámetros

*nPane*<br/>
El índice de base cero de la pieza de la que se va a recuperar texto.

*pType*<br/>
Puntero a un entero que recibe la información de tipo. El tipo puede ser uno de estos valores:

- **0** El texto se dibuja con un borde que aparece más bajo que el plano de la barra de estado.

- SBT_NOBORDERS El texto se dibuja sin bordes.

- SBT_OWNERDRAW El texto se dibuja mediante la ventana principal.

- SBT_POPOUT El texto se dibuja con un borde para que aparezca más alto que el plano de la barra de estado.

### <a name="return-value"></a>Valor devuelto

La longitud, en caracteres, del texto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]

## <a name="cstatusbarctrlgettiptext"></a><a name="gettiptext"></a>CStatusBarCtrl::GetTipText

Recupera el texto de información sobre herramientas de un panel en una barra de estado.

```
CString GetTipText(int nPane) const;
```

### <a name="parameters"></a>Parámetros

*nPane*<br/>
El índice de base cero del panel de la barra de estado para recibir el texto de información sobre herramientas.

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el texto que se usará en la información sobre herramientas.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje Win32 [SB_GETTIPTEXT](/windows/win32/Controls/sb-gettiptext), como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]

## <a name="cstatusbarctrlissimple"></a><a name="issimple"></a>CStatusBarCtrl::IsSimple

Comprueba un control de ventana de estado para determinar si está en modo simple.

```
BOOL IsSimple() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el control de ventana de estado está en modo simple; de lo contrario cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento de la [SB_ISSIMPLE](/windows/win32/Controls/sb-issimple)de mensaje de Win32 , como se describe en el Windows SDK.

## <a name="cstatusbarctrlsetbkcolor"></a><a name="setbkcolor"></a>CStatusBarCtrl::SetBkColor

Establece el color de fondo en una barra de estado.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parámetros

*Cr*<br/>
COLORREF que especifica el nuevo color de fondo. Especifique el valor de CLR_DEFAULT para que la barra de estado utilice su color de fondo predeterminado.

### <a name="return-value"></a>Valor devuelto

Un valor [COLORREF](/windows/win32/gdi/colorref) que representa el color de fondo predeterminado anterior.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [SB_SETBKCOLOR](/windows/win32/Controls/sb-setbkcolor), como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]

## <a name="cstatusbarctrlseticon"></a><a name="seticon"></a>CStatusBarCtrl::SetIcon

Establece el icono de un panel en una barra de estado.

```
BOOL SetIcon(
    int nPane,
    HICON hIcon);
```

### <a name="parameters"></a>Parámetros

*nPane*<br/>
El índice de base cero del panel que recibirá el icono. Si este parámetro es -1, se supone que la barra de estado es una barra de estado simple.

*hIcon*<br/>
Manipule el icono que se va a establecer. Si este valor es NULL, el icono se quita de la pieza.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje Win32 SB_SETICON](/windows/win32/Controls/sb-seticon), como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CStatusBarCtrl::SetBkColor](#setbkcolor).

## <a name="cstatusbarctrlsetminheight"></a><a name="setminheight"></a>CStatusBarCtrl::SetMinHeight

Establece la altura mínima del área de dibujo de un control de barra de estado.

```cpp
void SetMinHeight(int nMin);
```

### <a name="parameters"></a>Parámetros

*nMin*<br/>
Altura mínima, en píxeles, del control.

### <a name="remarks"></a>Observaciones

La altura mínima es la suma de *nMin* y el doble de ancho, en píxeles, del borde vertical del control de barra de estado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]

## <a name="cstatusbarctrlsetparts"></a><a name="setparts"></a>CStatusBarCtrl::SetParts

Establece el número de piezas en un control de barra de estado y la coordenada del borde derecho de cada pieza.

```
BOOL SetParts(
    int nParts,
    int* pWidths);
```

### <a name="parameters"></a>Parámetros

*nPartes*<br/>
Número de piezas que se han de configurar. El número de piezas no puede ser mayor que 255.

*pWidths*<br/>
Dirección de una matriz de enteros que tiene el mismo número de elementos que las partes especificadas por *nParts*. Cada elemento de la matriz especifica la posición, en coordenadas de cliente, del borde derecho de la parte correspondiente. Si un elemento es - 1, la posición del borde derecho de esa parte se extiende hasta el borde derecho del control.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]

## <a name="cstatusbarctrlsetsimple"></a><a name="setsimple"></a>CStatusBarCtrl::SetSimple

Especifica si un control de barra de estado muestra texto simple o muestra todas las partes de control establecidas por una llamada anterior a [SetParts](#setparts).

```
BOOL SetSimple(BOOL bSimple = TRUE);
```

### <a name="parameters"></a>Parámetros

*bSimple*<br/>
[en] Indicador de tipo de visualización. Si este parámetro es TRUE, el control muestra texto simple; si es FALSE, muestra varias partes.

### <a name="return-value"></a>Valor devuelto

Siempre devuelve 0.

### <a name="remarks"></a>Observaciones

Si la aplicación cambia el control de la barra de estado de no simple a simple, o viceversa, el sistema vuelve a dibujar inmediatamente el control.

## <a name="cstatusbarctrlsettext"></a><a name="settext"></a>CStatusBarCtrl::SetText

Establece el texto en un elemento determinado de un control de barra de estado.

```
BOOL SetText(
    LPCTSTR lpszText,
    int nPane,
    int nType);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
Dirección de una cadena terminada en null que especifica el texto que se debe establecer. Si *nType* es SBT_OWNERDRAW, *lpszText* representa 32 bits de datos.

*nPane*<br/>
El índice de base cero del elemento que se debe establecer. Si este valor es 255, se asume que el control de barra de estado es un control simple que solo contiene un elemento.

*nType*<br/>
Tipo de operación de dibujo. Consulte [SB_SETTEXT mensaje](/windows/win32/Controls/sb-settext) para obtener una lista de valores posibles.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El mensaje invalida la parte del control que ha cambiado, lo que hace que muestre el nuevo texto cuando el control recibe el mensaje WM_PAINT.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]

## <a name="cstatusbarctrlsettiptext"></a><a name="settiptext"></a>CStatusBarCtrl::SetTipText

Establece el texto de información sobre herramientas de un panel en una barra de estado.

```cpp
void SetTipText(
    int nPane,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Parámetros

*nPane*<br/>
El índice de base cero del panel de la barra de estado para recibir el texto de información sobre herramientas.

*pszTipText*<br/>
Puntero a una cadena que contiene el texto de información sobre herramientas.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/sb-settiptext)Win32 SB_SETTIPTEXT , como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]

## <a name="see-also"></a>Consulte también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)
