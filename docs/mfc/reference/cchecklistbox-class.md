---
title: Clase CCheckListBox
ms.date: 11/04/2016
f1_keywords:
- CCheckListBox
- AFXWIN/CCheckListBox
- AFXWIN/CCheckListBox::CCheckListBox
- AFXWIN/CCheckListBox::Create
- AFXWIN/CCheckListBox::DrawItem
- AFXWIN/CCheckListBox::Enable
- AFXWIN/CCheckListBox::GetCheck
- AFXWIN/CCheckListBox::GetCheckStyle
- AFXWIN/CCheckListBox::IsEnabled
- AFXWIN/CCheckListBox::MeasureItem
- AFXWIN/CCheckListBox::OnGetCheckPosition
- AFXWIN/CCheckListBox::SetCheck
- AFXWIN/CCheckListBox::SetCheckStyle
helpviewer_keywords:
- CCheckListBox [MFC], CCheckListBox
- CCheckListBox [MFC], Create
- CCheckListBox [MFC], DrawItem
- CCheckListBox [MFC], Enable
- CCheckListBox [MFC], GetCheck
- CCheckListBox [MFC], GetCheckStyle
- CCheckListBox [MFC], IsEnabled
- CCheckListBox [MFC], MeasureItem
- CCheckListBox [MFC], OnGetCheckPosition
- CCheckListBox [MFC], SetCheck
- CCheckListBox [MFC], SetCheckStyle
ms.assetid: 1dd78438-00e8-441c-b36f-9c4f9ac0d019
ms.openlocfilehash: cd50711813a3cfc1305cd5558c95e909ddbfc3f2
ms.sourcegitcommit: ab8d7b47b63b62892a1256a09b1324a9a136eccf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2020
ms.locfileid: "78215523"
---
# <a name="cchecklistbox-class"></a>Clase CCheckListBox

Proporciona la funcionalidad de un cuadro de lista de comprobación de Windows.

## <a name="syntax"></a>Sintaxis

```
class CCheckListBox : public CListBox
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CCheckListBox::CCheckListBox](#cchecklistbox)|Construye un objeto `CCheckListBox`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CCheckListBox:: Create](#create)|Crea el cuadro de lista de comprobación de Windows y lo adjunta al objeto `CCheckListBox`.|
|[CCheckListBox::D rawItem](#drawitem)|Lo llama el marco de trabajo cuando cambia el aspecto visual de un cuadro de lista dibujado por el propietario.|
|[CCheckListBox:: enable](#enable)|Habilita o deshabilita un elemento de cuadro de lista de comprobación.|
|[CCheckListBox::GetCheck](#getcheck)|Obtiene el estado de la casilla de un elemento.|
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|Obtiene el estilo de las casillas del control.|
|[CCheckListBox:: IsEnabled](#isenabled)|Determina si un elemento está habilitado.|
|[CCheckListBox::MeasureItem](#measureitem)|Lo llama el marco de trabajo cuando se crea un cuadro de lista con un estilo dibujado por el propietario.|
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|Lo llama el marco de trabajo para obtener la posición de la casilla de un elemento.|
|[CCheckListBox::SetCheck](#setcheck)|Establece el estado de la casilla de un elemento.|
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|Establece el estilo de las casillas del control.|

## <a name="remarks"></a>Comentarios

Un "cuadro de lista de comprobación" muestra una lista de elementos, como los nombres de archivo. Cada elemento de la lista tiene una casilla junto a él que el usuario puede activar o desactivar.

`CCheckListBox` es solo para los controles dibujados por el propietario, ya que la lista contiene más cadenas de texto. En su forma más simple, un cuadro de lista de comprobación contiene cadenas de texto y casillas, pero no es necesario tener texto. Por ejemplo, podría tener una lista de mapas de bits pequeños con una casilla junto a cada elemento.

Para crear su propio cuadro de lista de comprobación, debe derivar su propia clase de `CCheckListBox`. Para derivar su propia clase, escriba un constructor para la clase derivada y, a continuación, llame a `Create`.

Si desea controlar los mensajes de notificación de Windows enviados por un cuadro de lista a su elemento primario (normalmente una clase derivada de [CDialog](../../mfc/reference/cdialog-class.md)), agregue una entrada de mapa de mensajes y una función miembro de controlador de mensajes a la clase primaria para cada mensaje.

Cada entrada de mapa de mensajes tiene el siguiente formato:

**En\_** _notificación_ **(** _ID._ , _memberFxn_ **)**

donde `id` especifica el identificador de la ventana secundaria del control que envía la notificación y `memberFxn` es el nombre de la función miembro primaria que ha escrito para controlar la notificación.

El prototipo de función del elemento primario es el siguiente:

`afx_msg void memberFxn();`

Solo hay una entrada de mapa de mensajes que pertenece específicamente a `CCheckListBox` (pero vea también las entradas de mapa de mensajes para [CListBox](../../mfc/reference/clistbox-class.md)):

- ON_CLBN_CHKCHANGE el usuario ha cambiado el estado de la casilla de un elemento.

Si el cuadro de lista de comprobación es un cuadro de lista de comprobación predeterminado (una lista de cadenas con las casillas de tamaño predeterminado a la izquierda de cada), puede usar el valor predeterminado [CCheckListBox::D rawitem](#drawitem) para dibujar el cuadro de lista de comprobación. De lo contrario, debe invalidar la función [CListBox:: CompareItem](../../mfc/reference/clistbox-class.md#compareitem) y las funciones [CCheckListBox::D rawitem](#drawitem) y [CCheckListBox:: MeasureItem](#measureitem) .

Puede crear un cuadro de lista de comprobación desde una plantilla de cuadro de diálogo o directamente en el código.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CCheckListBox`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="cchecklistbox"></a>CCheckListBox::CCheckListBox

Construye un objeto `CCheckListBox`.

```
CCheckListBox();
```

### <a name="remarks"></a>Comentarios

Cree un objeto de `CCheckListBox` en dos pasos. En primer lugar, defina una clase derivada de `CCheckListBox`y, a continuación, llame a `Create`, que inicializa el cuadro de lista de comprobación de Windows y lo adjunta al objeto `CCheckListBox`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]

##  <a name="create"></a>CCheckListBox:: Create

Crea el cuadro de lista de comprobación de Windows y lo adjunta al objeto `CCheckListBox`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del cuadro de lista de comprobación. El estilo debe ser LBS_HASSTRINGS y LBS_OWNERDRAWFIXED (todos los elementos de la lista tienen el mismo alto) o LBS_OWNERDRAWVARIABLE (los elementos de la lista tienen un alto diferente). Este estilo se puede combinar con otros [estilos de cuadro de lista](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) excepto LBS_USETABSTOPS.

*Rect*<br/>
Especifica el tamaño y la posición del cuadro de lista de comprobación. Puede ser un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) o una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) .

*pParentWnd*<br/>
Especifica la ventana primaria del cuadro de lista de comprobación (normalmente un objeto `CDialog`). No debe ser NULL.

*nID*<br/>
Especifica el identificador de control del cuadro de lista de comprobación.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Cree un objeto de `CCheckListBox` en dos pasos. En primer lugar, defina una clase derivada de `CcheckListBox` y, a continuación, llame a `Create`, que inicializa el cuadro de lista de comprobación de Windows y lo adjunta al `CCheckListBox`. Vea [CCheckListBox:: CCheckListBox](#cchecklistbox) para obtener un ejemplo.

Cuando se ejecuta `Create`, Windows envía los mensajes [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)y [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) al control de cuadro de lista de comprobación.

Estos mensajes se controlan de forma predeterminada mediante las funciones miembro [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [alcrear](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)y [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) en la clase base `CWnd`. Para extender el control de mensajes predeterminado, agregue un mapa de mensajes a la clase derivada e invalide las funciones miembro de controlador de mensaje anteriores. Invalide `OnCreate`, por ejemplo, para realizar la inicialización necesaria para una nueva clase.

Aplique los siguientes [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) a un control de cuadro de lista de comprobación:

- WS_CHILD siempre

- WS_VISIBLE normalmente

- WS_DISABLED raramente

- WS_VSCROLL para agregar una barra de desplazamiento vertical

- WS_HSCROLL para agregar una barra de desplazamiento horizontal

- WS_GROUP a controles de grupo

- WS_TABSTOP para permitir la tabulación a este control

##  <a name="drawitem"></a>CCheckListBox::D rawItem

Lo llama el marco de trabajo cuando cambia el aspecto visual de un cuadro de lista de comprobación dibujado por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Puntero largo a una estructura [drawitemstruct (](/windows/win32/api/winuser/ns-winuser-drawitemstruct) que contiene información sobre el tipo de dibujo necesario.

### <a name="remarks"></a>Comentarios

Los miembros `itemAction` y `itemState` de la estructura `DRAWITEMSTRUCT` definen la acción de dibujo que se va a realizar.

De forma predeterminada, esta función dibuja una lista de casillas predeterminada, que consta de una lista de cadenas cada una con una casilla de tamaño predeterminado a la izquierda. El tamaño de la lista de casillas es el especificado en [crear](#create).

Invalide esta función miembro para implementar el dibujo de cuadros de lista de comprobación dibujados por el propietario que no son los predeterminados, como los cuadros de lista de comprobación con listas que no son cadenas, con elementos de alto variable o con casillas que no están a la izquierda. La aplicación debe restaurar todos los objetos de la interfaz de dispositivo gráfico (GDI) seleccionados para el contexto de presentación proporcionado en *lpDrawItemStruct* antes de la finalización de esta función miembro.

Si los elementos del cuadro de lista de comprobación no tienen el mismo alto, el estilo del cuadro de lista de comprobación (especificado en `Create`) debe ser **LBS_OWNERVARIABLE**y debe invalidar la función [MeasureItem](#measureitem) .

##  <a name="enable"></a>CCheckListBox:: enable

Llame a esta función para habilitar o deshabilitar un elemento de cuadro de lista de comprobación.

```
void Enable(
    int nIndex,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del elemento del cuadro de lista de comprobación que se va a habilitar.

*bEnabled*<br/>
Especifica si el elemento está habilitado o deshabilitado.

##  <a name="getcheck"></a>CCheckListBox::GetCheck

Recupera el estado de la casilla especificada.

```
int GetCheck(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de base cero de una casilla incluida en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Estado de la casilla especificada. En la tabla siguiente se enumeran los valores posibles.

|Valor|Descripción|
|-----------|-----------------|
|BST_CHECKED|La casilla está activada.|
|BST_UNCHECKED|La casilla no está activada.|
|BST_INDETERMINATE|El estado de la casilla es indeterminado.|

##  <a name="getcheckstyle"></a>CCheckListBox::GetCheckStyle

Llame a esta función para obtener el estilo del cuadro de lista de comprobación.

```
UINT GetCheckStyle();
```

### <a name="return-value"></a>Valor devuelto

Estilo de las casillas del control.

### <a name="remarks"></a>Comentarios

Para obtener información sobre los posibles estilos, vea [SetCheckStyle](#setcheckstyle).

##  <a name="isenabled"></a>CCheckListBox:: IsEnabled

Llame a esta función para determinar si un elemento está habilitado.

```
BOOL IsEnabled(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del elemento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento está habilitado; de lo contrario, es 0.

##  <a name="measureitem"></a>CCheckListBox::MeasureItem

Lo llama el marco de trabajo cuando se crea un cuadro de lista de comprobación con un estilo no predeterminado.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpMeasureItemStruct*<br/>
Puntero largo a una estructura [measureitemstruct (](/windows/win32/api/winuser/ns-winuser-measureitemstruct) .

### <a name="remarks"></a>Comentarios

De forma predeterminada, esta función miembro no hace nada. Invalide esta función miembro y rellene la estructura `MEASUREITEMSTRUCT` para informar a las ventanas de las dimensiones de los elementos de la lista de comprobación. Si se crea el cuadro de lista de comprobación con el estilo [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , el marco de trabajo llama a esta función miembro para cada elemento del cuadro de lista. De lo contrario, se llama a este miembro solo una vez.

##  <a name="ongetcheckposition"></a>CCheckListBox::OnGetCheckPosition

El marco de trabajo llama a esta función para obtener la posición y el tamaño de la casilla de un elemento.

```
virtual CRect OnGetCheckPosition(
    CRect rectItem,
    CRect rectCheckBox);
```

### <a name="parameters"></a>Parámetros

*rectItem*<br/>
La posición y el tamaño del elemento de lista.

*rectCheckBox*<br/>
Posición y tamaño predeterminados de la casilla de un elemento.

### <a name="return-value"></a>Valor devuelto

La posición y el tamaño de la casilla de un elemento.

### <a name="remarks"></a>Comentarios

La implementación predeterminada solo devuelve la posición y el tamaño predeterminados de la casilla (`rectCheckBox`). De forma predeterminada, una casilla está alineada en la esquina superior izquierda de un elemento y es el tamaño de la casilla estándar. Puede haber casos en los que desee las casillas de verificación a la derecha o que desee una casilla mayor o menor. En estos casos, invalide `OnGetCheckPosition` para cambiar la posición y el tamaño de la casilla dentro del elemento.

##  <a name="setcheck"></a>CCheckListBox::SetCheck

Establece el estado de la casilla especificada.

```
void SetCheck(
    int nIndex,
    int nCheck);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de base cero de una casilla incluida en el cuadro de lista.

*nCompruebe*<br/>
Estado del botón de la casilla especificada. Vea la sección Comentarios para ver los posibles valores.

### <a name="remarks"></a>Comentarios

En la tabla siguiente se enumeran los posibles valores para el parámetro *nCompruebe* .

|Valor|Descripción|
|-----------|-----------------|
|BST_CHECKED|Active la casilla especificada.|
|BST_UNCHECKED|Desactive la casilla especificada.|
|BST_INDETERMINATE|Establezca el estado de casilla especificado en indeterminado.<br /><br /> Este estado solo está disponible si el estilo de casilla está BS_AUTO3STATE o BS_3STATE. Para obtener más información, consulte [estilos de botón](../../mfc/reference/styles-used-by-mfc.md#button-styles).|

##  <a name="setcheckstyle"></a>CCheckListBox::SetCheckStyle

Llame a esta función para establecer el estilo de las casillas en el cuadro de lista de comprobación.

```
void SetCheckStyle(UINT nStyle);
```

### <a name="parameters"></a>Parámetros

*nStyle*<br/>
Determina el estilo de las casillas en el cuadro de lista de comprobación.

### <a name="remarks"></a>Comentarios

Los estilos válidos son:

- BS_CHECKBOX

- BS_AUTOCHECKBOX

- BS_AUTO3STATE

- BS_3STATE

Para obtener información sobre estos estilos, consulte [estilos de botón](../../mfc/reference/styles-used-by-mfc.md#button-styles).

## <a name="see-also"></a>Vea también

[Ejemplo TSTCON de MFC](../../overview/visual-cpp-samples.md)<br/>
[CListBox (clase)](../../mfc/reference/clistbox-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CListBox (clase)](../../mfc/reference/clistbox-class.md)
