---
title: CCheckListBox (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 57844b3304ccea0156d80c50aa250ef054f715cf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448459"
---
# <a name="cchecklistbox-class"></a>CCheckListBox (clase)

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
|[CCheckListBox::Create](#create)|Crea el cuadro de lista de comprobación de Windows y lo adjunta a la `CCheckListBox` objeto.|
|[CCheckListBox::DrawItem](#drawitem)|Lo llama el marco cuando un aspecto visual de un cuadro de lista dibujado por el propietario cambie.|
|[CCheckListBox::Enable](#enable)|Habilita o deshabilita un elemento de cuadro de lista de comprobación.|
|[CCheckListBox::GetCheck](#getcheck)|Obtiene el estado de la casilla de verificación de un elemento.|
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|Obtiene el estilo del control casillas de verificación.|
|[CCheckListBox::IsEnabled](#isenabled)|Determina si un elemento está habilitado.|
|[CCheckListBox::MeasureItem](#measureitem)|Lo llama el marco de trabajo cuando se crea un cuadro de lista con un estilo de dibujo del propietario.|
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|Lo llama el marco de trabajo para obtener la posición de la casilla de verificación de un elemento.|
|[CCheckListBox::SetCheck](#setcheck)|Establece el estado de la casilla de verificación de un elemento.|
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|Establece el estilo del control casillas de verificación.|

## <a name="remarks"></a>Comentarios

"Cuadro de lista de comprobación" muestra una lista de elementos, como los nombres de archivo. Cada elemento de la lista tiene una casilla de verificación junto a él que el usuario puede activar o desactivar.

`CCheckListBox` es solo para los controles dibujados por el propietario porque la lista contiene más de las cadenas de texto. En su forma más simple, un cuadro de lista de comprobación contiene cadenas de texto y casillas de verificación, pero no es necesario para que el texto en absoluto. Por ejemplo, podría tener una lista de mapas de bits pequeño con una casilla de verificación junto a cada elemento.

Para crear su propio cuadro de lista de comprobación, debe derivar su propia clase de `CCheckListBox`. Al derivar su propia clase, escribir un constructor de la clase derivada, a continuación, llame a `Create`.

Si desea controlar los mensajes de notificación de Windows enviados por un cuadro de lista a su elemento primario (normalmente una clase derivada de [CDialog](../../mfc/reference/cdialog-class.md)), agregue una función de miembro de entrada y el controlador de mensajes del mapa de mensajes a la clase primaria para cada mensaje.

Cada entrada de mapa de mensajes tiene el formato siguiente:

**ON_** notificación **(**`id`, `memberFxn` **)**

donde `id` especifica el identificador de ventana secundaria del control que envía la notificación y `memberFxn` es el nombre de la función de miembro primario que ha escrito para controlar la notificación.

Prototipo de función del elemento primario es el siguiente:

**afx_msg** `void` `memberFxn` **();**

Hay solo una entrada de mapa de mensajes que pertenecen específicamente a `CCheckListBox` (pero Vea también las entradas de mapa de mensajes para [CListBox](../../mfc/reference/clistbox-class.md)):

- ON_CLBN_CHKCHANGE el usuario ha cambiado el estado de la casilla de verificación de un elemento.

Si el cuadro de lista de comprobación es un cuadro de lista de comprobación predeterminado (una lista de cadenas con las casillas de verificación de tamaño predeterminado a la izquierda de cada uno), puede usar el valor predeterminado [CCheckListBox::DrawItem](#drawitem) para dibujar el cuadro de lista de comprobación. En caso contrario, es necesario reemplazar el [CListBox::CompareItem](../../mfc/reference/clistbox-class.md#compareitem) función y el [CCheckListBox::DrawItem](#drawitem) y [CCheckListBox::MeasureItem](#measureitem) funciones.

Puede crear un cuadro de lista de comprobación de una plantilla de cuadro de diálogo o directamente en el código.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CCheckListBox`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="cchecklistbox"></a>  CCheckListBox::CCheckListBox

Construye un objeto `CCheckListBox`.

```
CCheckListBox();
```

### <a name="remarks"></a>Comentarios

Construir un `CCheckListBox` objeto en dos pasos. Definir primero una clase derivada de `CCheckListBox`, a continuación, llame a `Create`, que inicializa el cuadro de lista de comprobación de Windows y lo asocia a la `CCheckListBox` objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]

##  <a name="create"></a>  CCheckListBox::Create

Crea el cuadro de lista de comprobación de Windows y lo adjunta a la `CCheckListBox` objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del cuadro de lista de comprobación. El estilo debe ser LBS_HASSTRINGS y LBS_OWNERDRAWFIXED (todos los elementos de la lista tienen la misma altura) o LBS_OWNERDRAWVARIABLE (elementos de la lista son de diferentes alturas). Este estilo se puede combinar con otras [estilos de cuadro de lista](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) excepto LBS_USETABSTOPS.

*Rect*<br/>
Especifica la posición y tamaño del cuadro de lista de comprobación. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](../../mfc/reference/rect-structure1.md) estructura.

*pParentWnd*<br/>
Especifica la ventana del elemento primario del cuadro de lista de comprobación (normalmente un `CDialog` objeto). No debe ser NULL.

*nID*<br/>
Especifica el identificador del control. del cuadro de lista de comprobación

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Construir un `CCheckListBox` objeto en dos pasos. En primer lugar, defina una clase derivada de `CcheckListBox` y, a continuación, llame a `Create`, que inicializa el cuadro de lista de comprobación de Windows y lo asocia a la `CCheckListBox`. Consulte [CCheckListBox::CCheckListBox](#cchecklistbox) para obtener un ejemplo.

Cuando `Create` envíos de Windows que se ejecuta el [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), y [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) mensajes para el control de cuadro de lista de comprobación.

Estos mensajes se controlan de manera predeterminada el [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), y [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) funciones miembro en el `CWnd` clase base. Para extender el control de mensajes de forma predeterminada, agregue un mapa de mensajes para el su clase derivada y las funciones de miembro de reemplazo el anterior controlador de mensajes. Invalidar `OnCreate`, por ejemplo, para realizar la inicialización necesaria para una nueva clase.

Aplique el siguiente [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) a un control de cuadro de lista de comprobación:

- WS_CHILD siempre

- WS_VISIBLE normalmente

- WS_DISABLED rara vez

- WS_VSCROLL para agregar una barra de desplazamiento vertical

- WS_HSCROLL para agregar una barra de desplazamiento horizontal

- WS_GROUP a controles de grupo

- WS_TABSTOP para permitir a este control de tabulación

##  <a name="drawitem"></a>  CCheckListBox::DrawItem

Lo llama el marco cuando un aspecto visual de los cambios del cuadro de lista de comprobación dibujado por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Un puntero largo a un [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) estructura que contiene información sobre el tipo de dibujo necesaria.

### <a name="remarks"></a>Comentarios

El `itemAction` y `itemState` los miembros de la `DRAWITEMSTRUCT` estructura define la acción de dibujo que se realiza.

De forma predeterminada, esta función dibuja una lista de casilla de verificación de forma predeterminada, que consta de una lista de cadenas con una casilla tamaño predeterminado a la izquierda. El tamaño de la lista de casilla de verificación es el especificado en [crear](#create).

Reemplace esta función miembro para implementar el dibujo de cuadros de lista de comprobación dibujado por el propietario que no son los predeterminados, como cuadros de lista de comprobación con las listas que no son cadenas, con elementos de alto variable o con las casillas de verificación que no son de la izquierda. La aplicación debe restaurar todos los objetos de interfaz (GDI) de dispositivo de gráficos seleccionados para proporciona el contexto de presentación en *lpDrawItemStruct* antes de la finalización de esta función miembro.

Si los elementos del cuadro de lista de comprobación no son la misma altura, la lista de comprobación cuadro Estilo (especificado en `Create`) debe ser ** LBS_OWNERVARIABLE así que debe invalidar el [MeasureItem](#measureitem) función.

##  <a name="enable"></a>  CCheckListBox::Enable

Llame a esta función para habilitar o deshabilitar un elemento de cuadro de lista de comprobación.

```
void Enable(
    int nIndex,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del elemento de cuadro de lista de comprobación para habilitarse.

*bHabilitado*<br/>
Especifica si el elemento está habilitado o deshabilitado.

##  <a name="getcheck"></a>  CCheckListBox::GetCheck

Recupera el estado de la casilla de verificación especificado.

```
int GetCheck(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de base cero de la casilla de verificación que se encuentra en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

El estado de la casilla de verificación especificado. En la tabla siguiente se enumera los valores posibles.

|Valor|Descripción|
|-----------|-----------------|
|BST_CHECKED|La casilla está activada.|
|BST_UNCHECKED|No se comprueba la casilla de verificación.|
|BST_INDETERMINATE|El estado de la casilla es indeterminado.|

##  <a name="getcheckstyle"></a>  CCheckListBox::GetCheckStyle

Llame a esta función para obtener el estilo del cuadro de lista de comprobación.

```
UINT GetCheckStyle();
```

### <a name="return-value"></a>Valor devuelto

El estilo del control casillas de verificación.

### <a name="remarks"></a>Comentarios

Para obtener información sobre los posibles estilos, consulte [SetCheckStyle](#setcheckstyle).

##  <a name="isenabled"></a>  CCheckListBox::IsEnabled

Llame a esta función para determinar si un elemento está habilitado.

```
BOOL IsEnabled(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del elemento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento está habilitado; en caso contrario, es 0.

##  <a name="measureitem"></a>  CCheckListBox::MeasureItem

Lo llama el marco de trabajo cuando se crea un cuadro de lista de comprobación con un estilo no predeterminado.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpMeasureItemStruct*<br/>
Un puntero largo a un [MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md) estructura.

### <a name="remarks"></a>Comentarios

De forma predeterminada, esta función miembro no hace nada. Reemplace esta función miembro y rellene el `MEASUREITEMSTRUCT` estructura para informar a Windows de las dimensiones de elementos del cuadro de lista de comprobación. Si el cuadro de lista de comprobación se crea con el [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) estilo, el marco llama a esta función miembro para cada elemento en el cuadro de lista. En caso contrario, este miembro se llama solo una vez.

##  <a name="ongetcheckposition"></a>  CCheckListBox::OnGetCheckPosition

El marco de trabajo llama a esta función para obtener la posición y tamaño de la casilla de verificación en un elemento.

```
virtual CRect OnGetCheckPosition(
    CRect rectItem,
    CRect rectCheckBox);
```

### <a name="parameters"></a>Parámetros

*rectItem*<br/>
La posición y el tamaño del elemento de lista.

*rectCheckBox*<br/>
La posición predeterminada y el tamaño de un elemento de casilla de verificación.

### <a name="return-value"></a>Valor devuelto

La posición y tamaño de un elemento de casilla de verificación.

### <a name="remarks"></a>Comentarios

La implementación predeterminada devuelve solo la posición predeterminada y el tamaño de la casilla de verificación (`rectCheckBox`). De forma predeterminada, una casilla de verificación está alineada en la esquina superior izquierda de un elemento y es el tamaño de la casilla de verificación estándar. Puede haber casos en que desea que las casillas de verificación de la derecha, o desea una casilla de verificación mayor o menor. En estos casos, reemplazar `OnGetCheckPosition` para cambiar la posición de la casilla de verificación y tamaño dentro del elemento.

##  <a name="setcheck"></a>  CCheckListBox::SetCheck

Establece el estado de la casilla de verificación especificado.

```
void SetCheck(
    int nIndex,
    int nCheck);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de base cero de la casilla de verificación que se encuentra en el cuadro de lista.

*nCompruebe*<br/>
El estado del botón de la casilla de verificación especificada. Consulte la sección Comentarios para los valores posibles.

### <a name="remarks"></a>Comentarios

En la tabla siguiente se enumera los valores posibles para el *nCompruebe* parámetro.

|Valor|Descripción|
|-----------|-----------------|
|BST_CHECKED|Seleccione la casilla de verificación especificada.|
|BST_UNCHECKED|Desactive la casilla de verificación especificada.|
|BST_INDETERMINATE|Establecer el estado de la casilla de verificación especificada en indeterminado.<br /><br /> Este estado solo está disponible si el estilo de la casilla de verificación es BS_AUTO3STATE o BS_3STATE. Para obtener más información, consulte [estilos de botón](../../mfc/reference/styles-used-by-mfc.md#button-styles).|

##  <a name="setcheckstyle"></a>  CCheckListBox::SetCheckStyle

Llame a esta función para establecer el estilo de las casillas de verificación en el cuadro de lista de comprobación.

```
void SetCheckStyle(UINT nStyle);
```

### <a name="parameters"></a>Parámetros

*nStyle*<br/>
Determina el estilo de las casillas de verificación en el cuadro de lista de comprobación.

### <a name="remarks"></a>Comentarios

Los estilos válidos son:

- BS_CHECKBOX

- BS_AUTOCHECKBOX

- BS_AUTO3STATE

- BS_3STATE

Para obtener información acerca de estos estilos, consulte [estilos de botón](../../mfc/reference/styles-used-by-mfc.md#button-styles).

## <a name="see-also"></a>Vea también

[Ejemplo de MFC TSTCON](../../visual-cpp-samples.md)<br/>
[CListBox (clase)](../../mfc/reference/clistbox-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CListBox (clase)](../../mfc/reference/clistbox-class.md)
