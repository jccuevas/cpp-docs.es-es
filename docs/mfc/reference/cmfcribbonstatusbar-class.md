---
title: CMFCRibbonStatusBar (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddDynamicElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddSeparator
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::Create
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::CreateEx
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindByID
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExtendedArea
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetSpace
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsBottomFrame
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsInformationMode
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RecalcLayout
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveAll
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::SetInformation
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::OnDrawInformation
helpviewer_keywords:
- CMFCRibbonStatusBar [MFC], AddDynamicElement
- CMFCRibbonStatusBar [MFC], AddElement
- CMFCRibbonStatusBar [MFC], AddExtendedElement
- CMFCRibbonStatusBar [MFC], AddSeparator
- CMFCRibbonStatusBar [MFC], Create
- CMFCRibbonStatusBar [MFC], CreateEx
- CMFCRibbonStatusBar [MFC], FindByID
- CMFCRibbonStatusBar [MFC], FindElement
- CMFCRibbonStatusBar [MFC], GetCount
- CMFCRibbonStatusBar [MFC], GetElement
- CMFCRibbonStatusBar [MFC], GetExCount
- CMFCRibbonStatusBar [MFC], GetExElement
- CMFCRibbonStatusBar [MFC], GetExtendedArea
- CMFCRibbonStatusBar [MFC], GetSpace
- CMFCRibbonStatusBar [MFC], IsBottomFrame
- CMFCRibbonStatusBar [MFC], IsExtendedElement
- CMFCRibbonStatusBar [MFC], IsInformationMode
- CMFCRibbonStatusBar [MFC], RecalcLayout
- CMFCRibbonStatusBar [MFC], RemoveAll
- CMFCRibbonStatusBar [MFC], RemoveElement
- CMFCRibbonStatusBar [MFC], SetInformation
- CMFCRibbonStatusBar [MFC], OnDrawInformation
ms.assetid: 921eb57f-3b40-49fa-a38c-3f2fb6dc2893
ms.openlocfilehash: 8d90e01db022c33edd654e83af05e9986799f2b9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754060"
---
# <a name="cmfcribbonstatusbar-class"></a>CMFCRibbonStatusBar (clase)

La `CMFCRibbonStatusBar` clase implementa un control de barra de estado que puede mostrar elementos de la cinta de opciones.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonStatusBar : public CMFCRibbonBar
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonStatusBar::AddDynamicElement](#adddynamicelement)|Agrega un elemento dinámico a la barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBar::AddElement](#addelement)|Agrega un nuevo elemento de la cinta de opciones a la barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBar::AddExtendedElement](#addextendedelement)|Agrega un elemento de la cinta de opciones al área extendida de la barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBar::AddSeparator](#addseparator)|Agrega un separador a la barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBar::Crear](#create)|Crea una barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBar::CreateEx](#createex)|Crea una barra de estado de la cinta de opciones con un estilo extendido.|
|[CMFCRibbonStatusBar::FindByID](#findbyid)||
|[CMFCRibbonStatusBar::FindElement](#findelement)|Devuelve un puntero al elemento que tiene el identificador de comando especificado.|
|[CMFCRibbonStatusBar::GetCount](#getcount)|Devuelve el número de elementos que se encuentran en el área principal de la barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBar::GetElement](#getelement)|Devuelve un puntero al elemento que se encuentra en un índice especificado.|
|[CMFCRibbonStatusBar::GetExCount](#getexcount)|Devuelve el número de elementos que se encuentran en el área extendida de la barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBar::GetExElement](#getexelement)|Devuelve un puntero al elemento ubicado en el índice especificado en el área extendida de la barra de estado de la cinta.|
|[CMFCRibbonStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCRibbonStatusBar::GetSpace](#getspace)||
|[CMFCRibbonStatusBar::IsBottomFrame](#isbottomframe)||
|[CMFCRibbonStatusBar::IsExtendedElement](#isextendedelement)||
|[CMFCRibbonStatusBar::IsInformationMode](#isinformationmode)|Determina si el modo de información está habilitado para la barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBar::RecalcLayout](#recalclayout)|(Reemplaza [CMFCRibbonBar::RecalcLayout](../../mfc/reference/cmfcribbonbar-class.md#recalclayout).)|
|[CMFCRibbonStatusBar::RemoveAll](#removeall)|Quita todos los elementos de la barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBar::RemoveElement](#removeelement)|Quita el elemento que tiene un identificador de comando especificado de la barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBar::SetInformation](#setinformation)|Habilita o deshabilita el modo de información para la barra de estado de la cinta de opciones.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonStatusBar::OnDrawInformation](#ondrawinformation)|Muestra la cadena de información que aparece en la barra de estado de la cinta de opciones cuando el modo de información está habilitado.|

## <a name="remarks"></a>Observaciones

Los usuarios pueden cambiar la visibilidad de los elementos de la cinta de opciones en una barra de estado de la cinta de opciones mediante el menú contextual integrado para la barra de estado de la cinta de opciones. Puede agregar o quitar elementos dinámicamente.

Una barra de estado de la cinta de opciones tiene dos áreas: un área principal y un área extendida. El área extendida se muestra en el lado derecho de la barra de estado de la cinta de opciones y aparece en un color diferente al del área principal.

Normalmente, el área principal de la barra de estado muestra notificaciones de estado y el área extendida muestra controles de vista. El área extendida permanece visible el mayor tiempo posible cuando el usuario cambia el tamaño de la barra de estado de la cinta de opciones.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCRibbonStatusBar` . En el ejemplo se muestra cómo agregar un nuevo elemento de la cinta de opciones a la barra de estado de la cinta de opciones, agregar un elemento de la cinta de opciones al área extendida de la barra de estado de la cinta de opciones, agregar un separador y habilitar el modo normal para la barra de estado de la cinta de opciones.

[!code-cpp[NVC_MFC_RibbonApp#15](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_1.cpp)]
[!code-cpp[NVC_MFC_RibbonApp#16](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)

[CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxribbonstatusbar.h

## <a name="cmfcribbonstatusbaradddynamicelement"></a><a name="adddynamicelement"></a>CMFCRibbonStatusBar::AddDynamicElement

Agrega un elemento dinámico a la barra de estado de la cinta de opciones.

```cpp
void AddDynamicElement(CMFCRibbonBaseElement* pElement);
```

### <a name="parameters"></a>Parámetros

*pElement*<br/>
[en] Un puntero a un elemento dinámico.

### <a name="remarks"></a>Observaciones

A diferencia de los elementos normales, los elementos dinámicos no son personalizables y el menú de personalización de la barra de estado no los muestra.

## <a name="cmfcribbonstatusbaraddelement"></a><a name="addelement"></a>CMFCRibbonStatusBar::AddElement

Agrega un nuevo elemento de la cinta de opciones a la barra de estado de la cinta de opciones.

```cpp
void AddElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parámetros

*pElement*<br/>
[en] Un puntero al elemento agregado.

*lpszLabel*<br/>
[en] Una etiqueta de texto del elemento.

*bIsVisible*<br/>
[en] TRUESi desea agregar el elemento como visible, FALSE si desea agregar el elemento como oculto.

## <a name="cmfcribbonstatusbaraddextendedelement"></a><a name="addextendedelement"></a>CMFCRibbonStatusBar::AddExtendedElement

Agrega un elemento de la cinta de opciones al área extendida de la barra de estado de la cinta de opciones.

```cpp
void AddExtendedElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parámetros

*pElement*<br/>
[en] Un puntero al elemento agregado.

*lpszLabel*<br/>
[en] La etiqueta de texto del elemento.

*bIsVisible*<br/>
[en] TRUESi desea agregar el elemento como visible, FALSE si desea agregar el elemento como oculto.

### <a name="remarks"></a>Observaciones

El área extendida está a la derecha del control de barra de estado.

## <a name="cmfcribbonstatusbaraddseparator"></a><a name="addseparator"></a>CMFCRibbonStatusBar::AddSeparator

Agrega un separador a la barra de estado de la cinta de opciones.

```cpp
void AddSeparator();
```

### <a name="remarks"></a>Observaciones

El marco de trabajo agrega un separador después del método [CMFCRibbonStatusBar::AddElement](#addelement). inserta el último elemento.

## <a name="cmfcribbonstatusbarcreate"></a><a name="create"></a>CMFCRibbonStatusBar::Crear

Crea una barra de estado de la cinta de opciones.

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
[en] Un puntero a la ventana primaria.

*dwStyle*<br/>
[en] Una combinación OR lógica de estilos de control.

*nID*<br/>
[en] El identificador de control de la barra de estado.

### <a name="return-value"></a>Valor devuelto

TRUESi la barra de estado se crea correctamente, FALSE en caso contrario.

## <a name="cmfcribbonstatusbarcreateex"></a><a name="createex"></a>CMFCRibbonStatusBar::CreateEx

Crea una barra de estado de la cinta de opciones que tiene un estilo extendido.

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle=0,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Puntero en la ventana primaria.

*dwCtrlStyle*<br/>
Una combinación OR lógica de estilos adicionales para crear el objeto de barra de estado.

*dwStyle*<br/>
El estilo de control de la barra de estado.

*nID*<br/>
El identificador de control de la barra de estado.

### <a name="return-value"></a>Valor devuelto

TRUESi la barra de estado se crea correctamente, FALSE en caso contrario.

## <a name="cmfcribbonstatusbarfindbyid"></a><a name="findbyid"></a>CMFCRibbonStatusBar::FindByID

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
CMFCRibbonBaseElement* FindByID(UINT uiCmdID, BOOL = TRUE);
```

### <a name="parameters"></a>Parámetros

[en] *uiCmdID*<br/>
[en] *BOOL*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonstatusbarfindelement"></a><a name="findelement"></a>CMFCRibbonStatusBar::FindElement

Devuelve un puntero al elemento que tiene el identificador de comando especificado.

```
CMFCRibbonBaseElement* FindElement(UINT uiID);
```

### <a name="parameters"></a>Parámetros

*uiID*<br/>
[en] El identificador del elemento.

### <a name="return-value"></a>Valor devuelto

Puntero al elemento que tiene el identificador de comando especificado. NULL si no existe tal elemento.

## <a name="cmfcribbonstatusbargetcount"></a><a name="getcount"></a>CMFCRibbonStatusBar::GetCount

Devuelve el número de elementos que se encuentran en el área principal de la barra de estado de la cinta de opciones.

```
int GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos que se encuentran en el área principal de la barra de estado de la cinta de opciones.

## <a name="cmfcribbonstatusbargetelement"></a><a name="getelement"></a>CMFCRibbonStatusBar::GetElement

Devuelve un puntero al elemento que se encuentra en un índice especificado.

```
CMFCRibbonBaseElement* GetElement(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[en] Especifica un índice de base cero de un elemento que se encuentra en el área principal del control de barra de estado.

### <a name="return-value"></a>Valor devuelto

Puntero al elemento que se encuentra en el índice especificado. NULL si el índice es negativo o supera el número de elementos de la barra de estado.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonstatusbargetexcount"></a><a name="getexcount"></a>CMFCRibbonStatusBar::GetExCount

Devuelve el número de elementos que se encuentran en el área extendida de la barra de estado de la cinta de opciones.

```
int GetExCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos que se encuentran en el área extendida de la barra de estado de la cinta de opciones.

## <a name="cmfcribbonstatusbargetexelement"></a><a name="getexelement"></a>CMFCRibbonStatusBar::GetExElement

Devuelve un puntero al elemento ubicado en el índice especificado en el área extendida de la barra de estado de la cinta. El área extendida está a la derecha del control de barra de estado.

```
CMFCRibbonBaseElement* GetExElement(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[en] Especifica el índice de base cero de un elemento que se encuentra en el área extendida del control de barra de estado.

### <a name="return-value"></a>Valor devuelto

Puntero al elemento ubicado en el índice especificado en el área extendida de la barra de estado de la cinta. NULL si *nIndex* es negativo o supera el número de elementos en el área extendida de la barra de estado de la cinta de opciones.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonstatusbargetextendedarea"></a><a name="getextendedarea"></a>CMFCRibbonStatusBar::GetExtendedArea

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Parámetros

[en] *rect*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonstatusbargetspace"></a><a name="getspace"></a>CMFCRibbonStatusBar::GetSpace

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
int GetSpace() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonstatusbarisbottomframe"></a><a name="isbottomframe"></a>CMFCRibbonStatusBar::IsBottomFrame

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
BOOL IsBottomFrame() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonstatusbarisextendedelement"></a><a name="isextendedelement"></a>CMFCRibbonStatusBar::IsExtendedElement

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
BOOL IsExtendedElement(CMFCRibbonBaseElement* pElement) const;
```

### <a name="parameters"></a>Parámetros

[en] *pElement*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonstatusbarisinformationmode"></a><a name="isinformationmode"></a>CMFCRibbonStatusBar::IsInformationMode

Determina si el modo de información está habilitado para la barra de estado de la cinta de opciones.

```
BOOL IsInformationMode() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi la barra de estado puede funcionar en modo de información; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

En el modo de información, la barra de estado oculta todos los paneles normales y muestra una cadena de mensaje.

## <a name="cmfcribbonstatusbarondrawinformation"></a><a name="ondrawinformation"></a>CMFCRibbonStatusBar::OnDrawInformation

Muestra la cadena que aparece en la barra de estado de la cinta de opciones cuando el modo de información está habilitado.

```
virtual void OnDrawInformation(
    CDC* pDC,
    CString& strInfo,
    CRect rectInfo);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

*strInfo*<br/>
[en] La cadena de información.

*rectInfo*<br/>
[en] El rectángulo delimitador.

### <a name="remarks"></a>Observaciones

Invalide este método en una clase derivada si desea personalizar la apariencia de la cadena de información en la barra de estado. Utilice el [método CMFCRibbonStatusBar::SetInformation](#setinformation) para colocar la barra de estado en modo de información. En este modo, la barra de estado oculta todos los paneles y muestra la cadena de información especificada por *strInfo*.

## <a name="cmfcribbonstatusbarrecalclayout"></a><a name="recalclayout"></a>CMFCRibbonStatusBar::RecalcLayout

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonstatusbarremoveall"></a><a name="removeall"></a>CMFCRibbonStatusBar::RemoveAll

Quita todos los elementos de la barra de estado de la cinta de opciones.

```cpp
void RemoveAll();
```

## <a name="cmfcribbonstatusbarremoveelement"></a><a name="removeelement"></a>CMFCRibbonStatusBar::RemoveElement

Quita el elemento que tiene un identificador de comando especificado de la barra de estado de la cinta de opciones.

```
BOOL RemoveElement(UINT uiID);
```

### <a name="parameters"></a>Parámetros

*uiID*<br/>
[en] El identificador del elemento que se va a quitar de la barra de estado.

### <a name="return-value"></a>Valor devuelto

TRUESi se quita un elemento con el *uiID* especificado. FALSE en caso contrario.

## <a name="cmfcribbonstatusbarsetinformation"></a><a name="setinformation"></a>CMFCRibbonStatusBar::SetInformation

Habilita o deshabilita el modo de información para la barra de estado de la cinta de opciones.

```cpp
void SetInformation(LPCTSTR lpszInfo);
```

### <a name="parameters"></a>Parámetros

*lpszInfo*<br/>
[en] La cadena de información.

### <a name="remarks"></a>Observaciones

Utilice este método para colocar la barra de estado en el modo de información. En este modo, la barra de estado oculta todos los paneles y muestra la cadena de información especificada por *lpszInfo*.

Cuando lpszInfo es NULL, la barra de estado vuelve al modo normal.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md)<br/>
[CMFCRibbonBaseElement Clase](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md)
