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
ms.openlocfilehash: dc0e80e80d61104a4d8cb5f1cfd4e26a64c42249
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752746"
---
# <a name="cchecklistbox-class"></a>Clase CCheckListBox

Proporciona la funcionalidad de un cuadro de lista de comprobación de Windows.

## <a name="syntax"></a>Sintaxis

```
class CCheckListBox : public CListBox
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCheckListBox::CCheckListBox](#cchecklistbox)|Construye un objeto `CCheckListBox`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCheckListBox::Crear](#create)|Crea la casilla de verificación `CCheckListBox` de Windows y la adjunta al objeto.|
|[CCheckListBox::DrawItem](#drawitem)|Llamado por el marco de trabajo cuando cambia un aspecto visual de un cuadro de lista de dibujo del propietario.|
|[CCheckListBox::Habilitar](#enable)|Habilita o deshabilita un elemento de casilla de verificación.|
|[CCheckListBox::GetCheck](#getcheck)|Obtiene el estado de la casilla de verificación de un elemento.|
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|Obtiene el estilo de las casillas de verificación del control.|
|[CCheckListBox::IsEnabled](#isenabled)|Determina si un elemento está habilitado.|
|[CCheckListBox::MeasureItem](#measureitem)|Llamado por el marco de trabajo cuando se crea un cuadro de lista con un estilo de dibujo por el propietario.|
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|Llamado por el marco de trabajo para obtener la posición de la casilla de verificación de un elemento.|
|[CCheckListBox::SetCheck](#setcheck)|Establece el estado de la casilla de verificación de un elemento.|
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|Establece el estilo de las casillas de verificación del control.|

## <a name="remarks"></a>Observaciones

Una "caja de verificación" muestra una lista de elementos, como nombres de archivo. Cada elemento de la lista tiene una casilla de verificación junto a ella que el usuario puede marcar o borrar.

`CCheckListBox`es sólo para los controles dibujados por el propietario porque la lista contiene más que cadenas de texto. En su forma más simple, una casilla de verificación contiene cadenas de texto y casillas de verificación, pero no es necesario tener texto en absoluto. Por ejemplo, podría tener una lista de mapas de bits pequeños con una casilla de verificación junto a cada elemento.

Para crear su propia casilla de verificación, debe derivar su propia clase de `CCheckListBox`. Para derivar su propia clase, escriba un constructor `Create`para la clase derivada y, a continuación, llame a .

Si desea controlar los mensajes de notificación de Windows enviados por un cuadro de lista a su elemento primario (normalmente una clase derivada de [CDialog](../../mfc/reference/cdialog-class.md)), agregue una entrada de mapa de mensajes y la función miembro de controlador de mensajes a la clase primaria para cada mensaje.

Cada entrada de mapa de mensajes adopta la siguiente forma:

**ON\_**_Notificación_ **(** _id_, _memberFxn_ **)**

donde `id` especifica el identificador de ventana secundaria `memberFxn` del control que envía la notificación y es el nombre de la función miembro principal que ha escrito para controlar la notificación.

El prototipo de función del padre es el siguiente:

`afx_msg void memberFxn();`

Sólo hay una entrada de mapa de `CCheckListBox` mensajes que pertenezca específicamente a (pero vea también las entradas del mapa de mensajes para [CListBox):](../../mfc/reference/clistbox-class.md)

- ON_CLBN_CHKCHANGE El usuario ha cambiado el estado de la casilla de verificación de un elemento.

Si la casilla de verificación es una casilla de verificación predeterminada (una lista de cadenas con las casillas de verificación de tamaño predeterminado a la izquierda de cada una), puede usar el valor predeterminado [CCheckListBox::DrawItem](#drawitem) para dibujar la casilla de verificación. De lo contrario, debe invalidar la función [CListBox::CompareItem](../../mfc/reference/clistbox-class.md#compareitem) y las funciones [CCheckListBox::DrawItem](#drawitem) y [CCheckListBox::MeasureItem.](#measureitem)

Puede crear una casilla de verificación desde una plantilla de cuadro de diálogo o directamente en el código.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CCheckListBox`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cchecklistboxcchecklistbox"></a><a name="cchecklistbox"></a>CCheckListBox::CCheckListBox

Construye un objeto `CCheckListBox`.

```
CCheckListBox();
```

### <a name="remarks"></a>Observaciones

Construir un `CCheckListBox` objeto en dos pasos. En primer lugar, `CCheckListBox`defina una `Create`clase derivada de , a continuación, `CCheckListBox` llame a , que inicializa la casilla de verificación de Windows y la adjunta al objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]

## <a name="cchecklistboxcreate"></a><a name="create"></a>CCheckListBox::Crear

Crea la casilla de verificación `CCheckListBox` de Windows y la adjunta al objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo de la casilla de verificación. El estilo debe ser LBS_HASSTRINGS y LBS_OWNERDRAWFIXED (todos los elementos de la lista tienen la misma altura) o LBS_OWNERDRAWVARIABLE (los elementos de la lista son de diferentes alturas). Este estilo se puede combinar con otros [estilos de cuadro de lista](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) excepto LBS_USETABSTOPS.

*Rect*<br/>
Especifica el tamaño y la posición de la casilla de verificación. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](/windows/win32/api/windef/ns-windef-rect) estructura.

*pParentWnd*<br/>
Especifica la ventana primaria de la `CDialog` casilla de verificación (normalmente un objeto). No debe ser NULL.

*nID*<br/>
Especifica el identificador de control de la casilla de verificación.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Construir un `CCheckListBox` objeto en dos pasos. En primer lugar, defina `CcheckListBox` una `Create`clase derivada de y, a continuación, `CCheckListBox`llame a , que inicializa la casilla de verificación de Windows y la adjunta al archivo . Vea [CCheckListBox::CCheckListBox](#cchecklistbox) para obtener un ejemplo.

Cuando `Create` se ejecuta, Windows envía los mensajes [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)y [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) al control de casilla de comprobación.

Estos mensajes se controlan de forma predeterminada mediante las funciones miembro [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)y [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) de la `CWnd` clase base. Para extender el control de mensajes predeterminado, agregue un mapa de mensajes a la clase derivada e invalide las funciones miembro del controlador de mensajes anteriores. Invalidar `OnCreate`, por ejemplo, para realizar la inicialización necesaria para una nueva clase.

Aplique los siguientes [estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles) de ventana a un control de casilla de verificación:

- WS_CHILD Siempre

- WS_VISIBLE Por lo general

- WS_DISABLED Rara vez

- WS_VSCROLL Para añadir una barra de desplazamiento vertical

- WS_HSCROLL Para añadir una barra de desplazamiento horizontal

- WS_GROUP Para agrupar controles

- WS_TABSTOP Para permitir la tabulación de este control

## <a name="cchecklistboxdrawitem"></a><a name="drawitem"></a>CCheckListBox::DrawItem

Llamado por el marco de trabajo cuando cambia un aspecto visual de una casilla de verificación dibujada por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Puntero largo a una estructura [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) que contiene información sobre el tipo de dibujo necesario.

### <a name="remarks"></a>Observaciones

Los `itemAction` `itemState` miembros `DRAWITEMSTRUCT` y de la estructura definen la acción de dibujo que se va a realizar.

De forma predeterminada, esta función dibuja una lista de casillas de verificación predeterminada, que consta de una lista de cadenas cada una con una casilla de verificación de tamaño predeterminado a la izquierda. El tamaño de la lista de casillas de verificación es el especificado en [Crear](#create).

Invalide esta función miembro para implementar el dibujo de las casillas de verificación dibujadas por el propietario que no son la predeterminada, como las casillas de verificación con listas que no son cadenas, con elementos de altura variable o con casillas de verificación que no están a la izquierda. La aplicación debe restaurar todos los objetos de interfaz de dispositivo gráfico (GDI) seleccionados para el contexto de visualización proporcionado en *lpDrawItemStruct* antes de la terminación de esta función miembro.

Si los elementos de la casilla de verificación no `Create`tienen la misma altura, el estilo de casilla de verificación (especificado en ) debe **LBS_OWNERVARIABLE**y debe invalidar la función [MeasureItem](#measureitem) .

## <a name="cchecklistboxenable"></a><a name="enable"></a>CCheckListBox::Habilitar

Llame a esta función para habilitar o deshabilitar un elemento de casilla de verificación.

```cpp
void Enable(
    int nIndex,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice del elemento de la casilla de verificación que se va a habilitar.

*bHabilitado*<br/>
Especifica si el elemento está habilitado o deshabilitado.

## <a name="cchecklistboxgetcheck"></a><a name="getcheck"></a>CCheckListBox::GetCheck

Recupera el estado de la casilla de verificación especificada.

```
int GetCheck(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice de base cero de una casilla de verificación que se encuentra en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

El estado de la casilla de verificación especificada. En la tabla siguiente se enumeran los valores posibles.

|Value|Descripción|
|-----------|-----------------|
|BST_CHECKED|La casilla está activada.|
|BST_UNCHECKED|La casilla de verificación no está marcada.|
|BST_INDETERMINATE|El estado de la casilla de verificación es indeterminado.|

## <a name="cchecklistboxgetcheckstyle"></a><a name="getcheckstyle"></a>CCheckListBox::GetCheckStyle

Llame a esta función para obtener el estilo de la casilla de verificación.

```
UINT GetCheckStyle();
```

### <a name="return-value"></a>Valor devuelto

El estilo de las casillas de verificación del control.

### <a name="remarks"></a>Observaciones

Para obtener información sobre los posibles estilos, vea [SetCheckStyle](#setcheckstyle).

## <a name="cchecklistboxisenabled"></a><a name="isenabled"></a>CCheckListBox::IsEnabled

Llame a esta función para determinar si un elemento está habilitado.

```
BOOL IsEnabled(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Indice del elemento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento está habilitado; de lo contrario 0.

## <a name="cchecklistboxmeasureitem"></a><a name="measureitem"></a>CCheckListBox::MeasureItem

Llamado por el marco de trabajo cuando se crea una casilla de verificación con un estilo no predeterminado.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpMeasureItemStruct*<br/>
Un puntero largo a una estructura [MEASUREITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-measureitemstruct)

### <a name="remarks"></a>Observaciones

De forma predeterminada, esta función miembro no hace nada. Invalide esta función `MEASUREITEMSTRUCT` miembro y rellene la estructura para informar a Windows de las dimensiones de los elementos de la casilla de verificación. Si la casilla de verificación se crea con el [estilo LBS_OWNERDRAWVARIABLE,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) el marco de trabajo llama a esta función miembro para cada elemento en el cuadro de lista. De lo contrario, se llama a este miembro solo una vez.

## <a name="cchecklistboxongetcheckposition"></a><a name="ongetcheckposition"></a>CCheckListBox::OnGetCheckPosition

El marco de trabajo llama a esta función para obtener la posición y el tamaño de la casilla de verificación en un elemento.

```
virtual CRect OnGetCheckPosition(
    CRect rectItem,
    CRect rectCheckBox);
```

### <a name="parameters"></a>Parámetros

*rectItem*<br/>
La posición y el tamaño del elemento de lista.

*rectCheckBox*<br/>
La posición y el tamaño predeterminados de la casilla de verificación de un elemento.

### <a name="return-value"></a>Valor devuelto

La posición y el tamaño de la casilla de verificación de un elemento.

### <a name="remarks"></a>Observaciones

La implementación predeterminada solo devuelve la posición`rectCheckBox`y el tamaño predeterminados de la casilla de verificación ( ). De forma predeterminada, una casilla de verificación se alinea en la esquina superior izquierda de un elemento y es el tamaño de casilla de verificación estándar. Puede haber casos en los que desee las casillas de verificación de la derecha o desee una casilla de verificación más grande o más pequeña. En estos casos, reemplace `OnGetCheckPosition` para cambiar la posición y el tamaño de la casilla de verificación dentro del elemento.

## <a name="cchecklistboxsetcheck"></a><a name="setcheck"></a>CCheckListBox::SetCheck

Establece el estado de la casilla de verificación especificada.

```cpp
void SetCheck(
    int nIndex,
    int nCheck);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice de base cero de una casilla de verificación que se encuentra en el cuadro de lista.

*nCheck*<br/>
El estado del botón de la casilla de verificación especificada. Consulte la sección Comentarios para ver los valores posibles.

### <a name="remarks"></a>Observaciones

En la tabla siguiente se enumeran los valores posibles para el parámetro *nCheck.*

|Value|Descripción|
|-----------|-----------------|
|BST_CHECKED|Active la casilla de verificación especificada.|
|BST_UNCHECKED|Desactive la casilla de verificación especificada.|
|BST_INDETERMINATE|Establezca el estado de casilla de verificación especificado en indeterminado.<br /><br /> Este estado solo está disponible si el estilo de la casilla de verificación está BS_AUTO3STATE o BS_3STATE. Para obtener más información, consulte Estilos de [botón](../../mfc/reference/styles-used-by-mfc.md#button-styles).|

## <a name="cchecklistboxsetcheckstyle"></a><a name="setcheckstyle"></a>CCheckListBox::SetCheckStyle

Llame a esta función para establecer el estilo de las casillas de verificación en la casilla de verificación.

```cpp
void SetCheckStyle(UINT nStyle);
```

### <a name="parameters"></a>Parámetros

*nStyle*<br/>
Determina el estilo de las casillas de verificación de la casilla de verificación.

### <a name="remarks"></a>Observaciones

Los estilos válidos son:

- BS_CHECKBOX

- BS_AUTOCHECKBOX

- BS_AUTO3STATE

- BS_3STATE

Para obtener información sobre estos estilos, consulte Estilos de [botón](../../mfc/reference/styles-used-by-mfc.md#button-styles).

## <a name="see-also"></a>Vea también

[Ejemplo de MFC TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox (clase)](../../mfc/reference/clistbox-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CListBox (clase)](../../mfc/reference/clistbox-class.md)
