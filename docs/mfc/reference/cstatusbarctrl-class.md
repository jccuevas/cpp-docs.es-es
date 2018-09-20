---
title: CStatusBarCtrl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0dc416c47634de522a20f81d7240cc1ea5797551
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392065"
---
# <a name="cstatusbarctrl-class"></a>CStatusBarCtrl (clase)

Proporciona la funcionalidad del control de barra de estado común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CStatusBarCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CStatusBarCtrl::CStatusBarCtrl](#cstatusbarctrl)|Construye un objeto `CStatusBarCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CStatusBarCtrl::Create](#create)|Crea un control de barra de estado y la conecta a un `CStatusBarCtrl` objeto.|
|[CStatusBarCtrl::CreateEx](#createex)|Crea un control de barra de estado con los estilos extendidos de Windows especificados y lo adjunta a un `CStatusBarCtrl` objeto.|
|[CStatusBarCtrl::DrawItem](#drawitem)|Se llama cuando un aspecto visual de un cambios de control dibujado por el propietario de la barra de estado.|
|[CStatusBarCtrl::GetBorders](#getborders)|Recupera el ancho actual de los bordes horizontales y verticales de un control de barra de estado.|
|[CStatusBarCtrl::GetIcon](#geticon)|Recupera el icono de un elemento (también conocido como un panel) en el control de barra de estado actual.|
|[CStatusBarCtrl::GetParts](#getparts)|Recupera un recuento de las partes de un control de barra de estado.|
|[CStatusBarCtrl::GetRect](#getrect)|Recupera el rectángulo delimitador de un elemento en un control de barra de estado.|
|[CStatusBarCtrl:: GetText](#gettext)|Recupera el texto de un elemento determinado de un control de barra de estado.|
|[CStatusBarCtrl:: Gettextlength](#gettextlength)|Recuperar la longitud, en caracteres, del texto de un elemento determinado de un control de barra de estado.|
|[CStatusBarCtrl:: GetTipText](#gettiptext)|Recupera el texto de información sobre herramientas para un panel en una barra de estado.|
|[CStatusBarCtrl::IsSimple](#issimple)|Comprueba un control de ventana de estado para determinar si se trata en el modo simple.|
|[CStatusBarCtrl::SetBkColor](#setbkcolor)|Establece el color de fondo de una barra de estado.|
|[CStatusBarCtrl::SetIcon](#seticon)|Establece el icono para un panel en una barra de estado.|
|[CStatusBarCtrl::SetMinHeight](#setminheight)|Establece el alto mínimo de estado de un área de dibujo del control de barra.|
|[CStatusBarCtrl::SetParts](#setparts)|Establece el número de elementos en un control y la coordenada del borde derecho de cada parte de la barra de estado.|
|[CStatusBarCtrl::SetSimple](#setsimple)|Especifica si un control de barra de estado muestra el texto simple o todos los elementos del control establecidos por una llamada anterior a `SetParts`.|
|[CStatusBarCtrl::SetText](#settext)|Establece el texto en un elemento determinado de un control de barra de estado.|
|[CStatusBarCtrl:: SetTipText](#settiptext)|Establece el texto de información sobre herramientas para un panel en una barra de estado.|

## <a name="remarks"></a>Comentarios

Un "control de barra de estado" es una ventana horizontal, que habitualmente se muestra en la parte inferior de una ventana primaria, en el que una aplicación puede mostrar varios tipos de información de estado. El control de barra de estado puede dividirse en partes para mostrar más de un tipo de información.

Este control (y, por tanto, la `CStatusBarCtrl` clase) está disponible solo para programas que se ejecutan en Windows 95/98 y Windows NT versión 3.51 y versiones posteriores.

Para obtener más información sobre el uso de `CStatusBarCtrl`, consulte [controles](../../mfc/controls-mfc.md) y [utilizando CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatusBarCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="create"></a>  CStatusBarCtrl::Create

Crea un control de barra de estado y la conecta a un `CStatusBarCtrl` objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de barra de estado. Aplicar cualquier combinación de los estilos de control que aparece en la barra de estado [estilos de Control comunes](/windows/desktop/Controls/common-control-styles) en el SDK de Windows. Este parámetro debe incluir el estilo WS_CHILD. También debe incluir el estilo WS_VISIBLE.

*Rect*<br/>
Especifica el tamaño y la posición del control de barra de estado. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) estructura.

*pParentWnd*<br/>
Especifica el estado de la barra de la ventana primaria de control, normalmente un `CDialog`. No debe ser NULL.

*nID*<br/>
Especifica el identificador. del control de barra de estado

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Construir un `CStatusBarCtrl` en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a `Create`, que crea el control de barra de estado y la conecta a la `CStatusBarCtrl` objeto.

La posición predeterminada de una ventana de estado es a lo largo de la parte inferior de la ventana primaria, pero puede especificar el estilo CCS_TOP para que aparezca en la parte superior del área de cliente de la ventana primaria. Puede especificar el estilo SBARS_SIZEGRIP para incluir un control de tamaño en el extremo derecho de la ventana de estado. No se recomienda combinar los estilos CCS_TOP y SBARS_SIZEGRIP, porque el control de tamaño resultante no es funcional, aunque el sistema lo dibuja en la ventana de estado.

Para crear una barra de estado con los estilos de ventana extendidos, llame a [CStatusBarCtrl::CreateEx](#createex) en lugar de `Create`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]

##  <a name="createex"></a>  CStatusBarCtrl::CreateEx

Crea un control (una ventana secundaria) y lo asocia a la `CStatusBarCtrl` objeto.

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
Especifica el estilo extendido del control que se está creando. Para obtener una lista de los estilos extendidos de Windows, consulte el *dwExStyle* parámetro [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) en el SDK de Windows.

*dwStyle*<br/>
Especifica el estilo del control de barra de estado. Aplicar cualquier combinación de los estilos de control que aparece en la barra de estado [estilos de Control comunes](/windows/desktop/Controls/common-control-styles) en el SDK de Windows. Este parámetro debe incluir el estilo WS_CHILD. También debe incluir el estilo WS_VISIBLE.

*Rect*<br/>
Una referencia a un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que describe el tamaño y posición de la ventana que se creará, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Un puntero a la ventana que es primario del control.

*nID*<br/>
Identificador de ventana secundaria. del control

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Use `CreateEx` en lugar de [crear](#create) para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.

##  <a name="cstatusbarctrl"></a>  CStatusBarCtrl::CStatusBarCtrl

Construye un objeto `CStatusBarCtrl`.

```
CStatusBarCtrl();
```

##  <a name="drawitem"></a>  CStatusBarCtrl::DrawItem

Lo llama el marco cuando un aspecto visual de un cambios de control dibujado por el propietario de la barra de estado.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Un puntero largo a un [DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) estructura que contiene información sobre el tipo de dibujo necesaria.

### <a name="remarks"></a>Comentarios

El `itemAction` miembro de la `DRAWITEMSTRUCT` estructura define la acción de dibujo que se realiza.

De forma predeterminada, esta función miembro no hace nada. Reemplace esta función miembro para implementar un dibujado por el propietario del dibujo `CStatusBarCtrl` objeto.

La aplicación debe restaurar todos los objetos de interfaz (GDI) de dispositivo de gráficos seleccionados para proporciona el contexto de presentación en *lpDrawItemStruct* antes de este miembro de la función termina.

##  <a name="getborders"></a>  CStatusBarCtrl::GetBorders

Recupera el ancho actual del control de barra de estado de los bordes horizontales y verticales y del espacio entre los rectángulos.

```
BOOL GetBorders(int* pBorders) const;

BOOL GetBorders(
    int& nHorz,
    int& nVert,
    int& nSpacing) const;
```

### <a name="parameters"></a>Parámetros

*pBorders*<br/>
Dirección de una matriz de enteros con tres elementos. El primer elemento recibe el ancho del borde horizontal, el segundo recibe el ancho del borde vertical y el tercero recibe el ancho del borde entre rectángulos.

*nHorz*<br/>
Referencia a un entero que recibe el ancho del borde horizontal.

*nvertir*<br/>
Referencia a un entero que recibe el ancho del borde vertical.

*nSpacing*<br/>
Referencia a un entero que recibe el ancho del borde entre rectángulos.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Estos límites determinan el espaciado entre el borde exterior del control y los rectángulos dentro del control que contienen texto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]

##  <a name="geticon"></a>  CStatusBarCtrl::GetIcon

Recupera el icono de un elemento (también conocido como un panel) en el control de barra de estado actual.

```
HICON GetIcon(int iPart) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*iPart*|[in] Índice de base cero del elemento que contiene el icono que se va a recuperar. Si este parámetro es -1, la barra de estado se supone que una barra de estado de un modo sencillo.|

### <a name="return-value"></a>Valor devuelto

El identificador del icono si el método es correcto; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

Este método envía el [SB_GETICON](/windows/desktop/Controls/sb-geticon) mensaje, que se describe en el SDK de Windows.

Consta de un control de barra de estado de una fila de paneles de salida de texto, que también se denomina son partes. Para obtener más información acerca de la barra de estado, vea [implementación de la barra de estado en MFC](../../mfc/status-bar-implementation-in-mfc.md) y [establecer el modo de un objeto CStatusBarCtrl](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente define una variable, `m_statusBar`, que se usa para acceder al control de barra de estado actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se copia un icono en dos paneles de control de barra de estado actual. En una sección del ejemplo de código anterior se crea un control de barra de estado con tres paneles y, a continuación, agrega un icono para el primer panel. Este ejemplo recupera el icono de la primera sección y, a continuación, agrega al panel de segundo y tercero.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]

##  <a name="getparts"></a>  CStatusBarCtrl::GetParts

Recupera un recuento de las partes de un control de barra de estado.

```
int GetParts(
    int nParts,
    int* pParts) const;
```

### <a name="parameters"></a>Parámetros

*nParts*<br/>
Número de elementos que se va a recuperar las coordenadas. Si este parámetro es mayor que el número de partes del control, el mensaje recupera las coordenadas para que solo los elementos existentes.

*pParts*<br/>
Dirección de una matriz de enteros con el mismo número de elementos como el número de elementos especificados por *nParts*. Cada elemento de la matriz recibe las coordenadas de cliente del borde derecho de la parte correspondiente. Si un elemento se establece en - 1, la posición del borde derecho de esa parte amplía hasta el borde derecho de la barra de estado.

### <a name="return-value"></a>Valor devuelto

El número de elementos en el control si se realiza correctamente, o cero en caso contrario.

### <a name="remarks"></a>Comentarios

Esta función miembro también recupera la coordenada del borde derecho del número especificado de elementos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]

##  <a name="getrect"></a>  CStatusBarCtrl::GetRect

Recupera el rectángulo delimitador de un elemento en un control de barra de estado.

```
BOOL GetRect(
    int nPane,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*nPane*<br/>
Índice de base cero del elemento cuyo rectángulo delimitador es va a recuperar.

*lpRect*<br/>
Dirección de un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que recibe el rectángulo delimitador.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]

##  <a name="gettext"></a>  CStatusBarCtrl:: GetText

Recupera el texto de un elemento determinado de un control de barra de estado.

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
Índice de base cero del elemento en el que se va a recuperar el texto.

*PEscriba*<br/>
Puntero a un entero que recibe la información de tipo. El tipo puede ser uno de estos valores:

- **0** el texto se dibuja con un borde a parecer inferior del plano de la barra de estado.

- SBT_NOBORDERS el texto se dibuja sin bordes.

- SBT_POPOUT el texto se dibuja con un borde que aparezcan mayor que el plano de la barra de estado.

- SBT_OWNERDRAW si el texto tiene el tipo, de dibujo de SBT_OWNERDRAW *PEscriba* recibe este mensaje y devuelve el valor de 32 bits asociado con el texto en lugar del tipo de longitud y la operación.

### <a name="return-value"></a>Valor devuelto

La longitud en caracteres, del texto o un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene el texto actual.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]

##  <a name="gettextlength"></a>  CStatusBarCtrl:: Gettextlength

Recupera la longitud en caracteres, del texto de un elemento determinado de un control de barra de estado.

```
int GetTextLength(
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>Parámetros

*nPane*<br/>
Índice de base cero del elemento en el que se va a recuperar el texto.

*PEscriba*<br/>
Puntero a un entero que recibe la información de tipo. El tipo puede ser uno de estos valores:

- **0** el texto se dibuja con un borde a parecer inferior del plano de la barra de estado.

- SBT_NOBORDERS el texto se dibuja sin bordes.

- SBT_OWNERDRAW se dibuja el texto por la ventana primaria.

- SBT_POPOUT el texto se dibuja con un borde que aparezcan mayor que el plano de la barra de estado.

### <a name="return-value"></a>Valor devuelto

La longitud, en caracteres, del texto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]

##  <a name="gettiptext"></a>  CStatusBarCtrl:: GetTipText

Recupera el texto de información sobre herramientas para un panel en una barra de estado.

```
CString GetTipText(int nPane) const;
```

### <a name="parameters"></a>Parámetros

*nPane*<br/>
Índice de base cero del panel de barra de estado para recibir el texto de información sobre herramientas.

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el texto que se usará en la información sobre herramientas.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [SB_GETTIPTEXT](/windows/desktop/Controls/sb-gettiptext), tal y como se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]

##  <a name="issimple"></a>  CStatusBarCtrl::IsSimple

Comprueba un control de ventana de estado para determinar si se trata en el modo simple.

```
BOOL IsSimple() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el control de ventana de estado se encuentra en el modo simple; en caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [SB_ISSIMPLE](/windows/desktop/Controls/sb-issimple), tal y como se describe en el SDK de Windows.

##  <a name="setbkcolor"></a>  CStatusBarCtrl::SetBkColor

Establece el color de fondo de una barra de estado.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parámetros

*CR*<br/>
Valor COLORREF que especifica el nuevo color de fondo. Especifique el valor CLR_DEFAULT para hacer que la barra de estado utilizar su color de fondo predeterminado.

### <a name="return-value"></a>Valor devuelto

Un [COLORREF](/windows/desktop/gdi/colorref) valor que representa el color de fondo predeterminado anterior.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [SB_SETBKCOLOR](/windows/desktop/Controls/sb-setbkcolor), tal y como se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]

##  <a name="seticon"></a>  CStatusBarCtrl::SetIcon

Establece el icono para un panel en una barra de estado.

```
BOOL SetIcon(
    int nPane,
    HICON hIcon);
```

### <a name="parameters"></a>Parámetros

*nPane*<br/>
Índice de base cero del panel que recibirá el icono. Si este parámetro es -1, la barra de estado se supone que una barra de estado simple.

*hIcon*<br/>
Identificador del icono debe establecerse. Si este valor es NULL, se quita el icono de la parte.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [SB_SETICON](/windows/desktop/Controls/sb-seticon), tal y como se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CStatusBarCtrl::SetBkColor](#setbkcolor).

##  <a name="setminheight"></a>  CStatusBarCtrl::SetMinHeight

Establece el alto mínimo de estado de un área de dibujo del control de barra.

```
void SetMinHeight(int nMin);
```

### <a name="parameters"></a>Parámetros

*nmín.*<br/>
Alto mínimo, en píxeles, del control.

### <a name="remarks"></a>Comentarios

El alto mínimo es la suma de *nmín* y dos veces el ancho, en píxeles, del borde vertical del control de barra de estado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]

##  <a name="setparts"></a>  CStatusBarCtrl::SetParts

Establece el número de elementos en un control y la coordenada del borde derecho de cada parte de la barra de estado.

```
BOOL SetParts(
    int nParts,
    int* pWidths);
```

### <a name="parameters"></a>Parámetros

*nParts*<br/>
Número de elementos para establecer. El número de partes no puede ser mayor que 255.

*pWidths*<br/>
Dirección de una matriz de enteros con el mismo número de elementos como elementos especificados por *nParts*. Cada elemento de la matriz especifica la posición, en coordenadas de cliente, del borde derecho de la parte correspondiente. Si un elemento es - 1, la posición del borde derecho de esa parte se amplía hasta el borde derecho del control.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]

##  <a name="setsimple"></a>  CStatusBarCtrl::SetSimple

Especifica si un control de barra de estado muestra el texto simple o todos los elementos del control establecidos por una llamada anterior a [SetParts](#setparts).

```
BOOL SetSimple(BOOL bSimple = TRUE);
```

### <a name="parameters"></a>Parámetros

*bSimple*<br/>
[in] Indicador de tipo de visualización. Si este parámetro es TRUE, el control muestra texto simple; Si es FALSE, muestra varias partes.

### <a name="return-value"></a>Valor devuelto

Siempre devuelve 0.

### <a name="remarks"></a>Comentarios

Si la aplicación cambia el control de barra de estado de no simple en simple, o viceversa, el sistema vuelve a dibujar inmediatamente el control.

##  <a name="settext"></a>  CStatusBarCtrl::SetText

Establece el texto en un elemento determinado de un control de barra de estado.

```
BOOL SetText(
    LPCTSTR lpszText,
    int nPane,
    int nType);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
Dirección de una cadena terminada en null que especifica el texto que se debe establecer. Si *nLas* es SBT_OWNERDRAW, *lpszText* representa 32 bits de datos.

*nPane*<br/>
El índice de base cero del elemento que se debe establecer. Si este valor es 255, se asume que el control de barra de estado es un control simple que solo contiene un elemento.

*nLas*<br/>
Tipo de operación de dibujo. Consulte [mensaje SB_SETTEXT](/windows/desktop/Controls/sb-settext) para obtener una lista de valores posibles.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El mensaje invalida la parte del control que ha cambiado, lo que hace que muestra el texto nuevo cuando el control siguiente recibe el mensaje WM_PAINT.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]

##  <a name="settiptext"></a>  CStatusBarCtrl:: SetTipText

Establece el texto de información sobre herramientas para un panel en una barra de estado.

```
void SetTipText(
    int nPane,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Parámetros

*nPane*<br/>
Índice de base cero del panel de barra de estado para recibir el texto de información sobre herramientas.

*pszTipText*<br/>
Un puntero a una cadena que contiene el texto de información sobre herramientas.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [SB_SETTIPTEXT](/windows/desktop/Controls/sb-settiptext), tal y como se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl (clase)](../../mfc/reference/ctoolbarctrl-class.md)
