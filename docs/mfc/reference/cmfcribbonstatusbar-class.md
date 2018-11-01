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
ms.openlocfilehash: 068cff9ea3827e780bec886bc5d4b0e263c02e62
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635349"
---
# <a name="cmfcribbonstatusbar-class"></a>CMFCRibbonStatusBar (clase)

La `CMFCRibbonStatusBar` clase implementa un control de barra de estado que se puede mostrar los elementos de la cinta de opciones.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonStatusBar : public CMFCRibbonBar
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCRibbonStatusBar::AddDynamicElement](#adddynamicelement)|Agrega un elemento dinámico a la barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBar::AddElement](#addelement)|Agrega un nuevo elemento de la cinta de opciones en la barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBar::AddExtendedElement](#addextendedelement)|Agrega un elemento de la cinta de opciones para el área extendida de la barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBar::AddSeparator](#addseparator)|Agrega un separador en la barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBar::Create](#create)|Crea una barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBar::CreateEx](#createex)|Crea una barra de estado de la cinta de opciones con un estilo extendido.|
|[CMFCRibbonStatusBar::FindByID](#findbyid)||
|[CMFCRibbonStatusBar::FindElement](#findelement)|Devuelve un puntero al elemento que tiene el identificador de comando especificado.|
|[CMFCRibbonStatusBar::GetCount](#getcount)|Devuelve el número de elementos que se encuentran en el área principal de la barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBar::GetElement](#getelement)|Devuelve un puntero al elemento que se encuentra en el índice especificado.|
|[CMFCRibbonStatusBar::GetExCount](#getexcount)|Devuelve el número de elementos que se encuentran en el área extendida de la barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBar::GetExElement](#getexelement)|Devuelve un puntero al elemento ubicado en el índice especificado en el área extendida de la barra de estado de la cinta.|
|[CMFCRibbonStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCRibbonStatusBar::GetSpace](#getspace)||
|[CMFCRibbonStatusBar::IsBottomFrame](#isbottomframe)||
|[CMFCRibbonStatusBar::IsExtendedElement](#isextendedelement)||
|[CMFCRibbonStatusBar::IsInformationMode](#isinformationmode)|Determina si está habilitado el modo de información para la barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBar::RecalcLayout](#recalclayout)|(Invalida [CMFCRibbonBar::RecalcLayout](../../mfc/reference/cmfcribbonbar-class.md#recalclayout).)|
|[CMFCRibbonStatusBar::RemoveAll](#removeall)|Quita todos los elementos de la barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBar::RemoveElement](#removeelement)|Quita el elemento que tiene un identificador de comando especificado en la barra de estado de la cinta de opciones.|
|[CMFCRibbonStatusBar::SetInformation](#setinformation)|Habilita o deshabilita el modo de información de la barra de estado de la cinta de opciones.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CMFCRibbonStatusBar::OnDrawInformation](#ondrawinformation)|Muestra la cadena de información que aparece en la barra cuando está habilitado el modo de información de estado de cinta de opciones.|

## <a name="remarks"></a>Comentarios

Los usuarios pueden cambiar la visibilidad de los elementos de la cinta de opciones en una barra de estado de la cinta de opciones mediante el menú de contexto integradas para la barra de estado de la cinta de opciones. Puede agregar o quitar elementos de forma dinámica.

Una barra de estado de la cinta de opciones tiene dos áreas: un área principal y un área extendida. El área extendida se muestra en el lado derecho de la barra de estado de la cinta de opciones y aparece en un color diferente que el área principal no.

Normalmente, el área principal de la barra de estado muestra las notificaciones de estado y el área extendida muestra los controles de vista. El área extendida permanece visible mientras sea posible cuando el usuario cambia el tamaño de la barra de estado de la cinta de opciones.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCRibbonStatusBar` . El ejemplo muestra cómo agregar un nuevo elemento de la cinta de opciones a la barra de estado de la cinta de opciones, agregue un elemento de la cinta de opciones para el área extendida de la barra de estado de la cinta de opciones, agregue un separador y habilitar el modo normal de la barra de estado de la cinta de opciones.

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

##  <a name="adddynamicelement"></a>  CMFCRibbonStatusBar::AddDynamicElement

Agrega un elemento dinámico a la barra de estado de la cinta de opciones.

```
void AddDynamicElement(CMFCRibbonBaseElement* pElement);
```

### <a name="parameters"></a>Parámetros

*pElement*<br/>
[in] Un puntero a un elemento dinámico.

### <a name="remarks"></a>Comentarios

A diferencia de los elementos regulares, elementos dinámicos no son personalizables y el menú de personalizar la barra de estado no los muestra.

##  <a name="addelement"></a>  CMFCRibbonStatusBar::AddElement

Agrega un nuevo elemento de la cinta de opciones en la barra de estado de la cinta de opciones.

```
void AddElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parámetros

*pElement*<br/>
[in] Un puntero para el elemento agregado.

*lpszLabel*<br/>
[in] Una etiqueta de texto del elemento.

*bIsVisible*<br/>
[in] TRUE si desea agregar el elemento como visible, FALSE si desea agregar el elemento como oculto.

##  <a name="addextendedelement"></a>  CMFCRibbonStatusBar::AddExtendedElement

Agrega un elemento de la cinta de opciones para el área extendida de la barra de estado de la cinta de opciones.

```
void AddExtendedElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parámetros

*pElement*<br/>
[in] Un puntero para el elemento agregado.

*lpszLabel*<br/>
[in] La etiqueta de texto del elemento.

*bIsVisible*<br/>
[in] TRUE si desea agregar el elemento como visible, FALSE si desea agregar el elemento como oculto.

### <a name="remarks"></a>Comentarios

El área extendida está a la derecha del control de barra de estado.

##  <a name="addseparator"></a>  CMFCRibbonStatusBar::AddSeparator

Agrega un separador en la barra de estado de la cinta de opciones.

```
void AddSeparator();
```

### <a name="remarks"></a>Comentarios

El marco de trabajo, agrega un separador después del método [CMFCRibbonStatusBar::AddElement](#addelement). Inserta el último elemento.

##  <a name="create"></a>  CMFCRibbonStatusBar::Create

Crea una barra de estado de la cinta de opciones.

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
[in] Un puntero a la ventana primaria.

*dwStyle*<br/>
[in] Una combinación de OR lógica de los estilos de control.

*nID*<br/>
[in] El identificador de control de la barra de estado.

### <a name="return-value"></a>Valor devuelto

TRUE si la barra de estado se ha creado correctamente, FALSE en caso contrario.

##  <a name="createex"></a>  CMFCRibbonStatusBar::CreateEx

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
Un puntero a la ventana primaria.

*dwCtrlStyle*<br/>
Una combinación de OR lógica de estilos adicionales para crear el objeto de barra de estado.

*dwStyle*<br/>
El estilo de control de la barra de estado.

*nID*<br/>
El identificador de control de la barra de estado.

### <a name="return-value"></a>Valor devuelto

TRUE si la barra de estado se ha creado correctamente, FALSE en caso contrario.

##  <a name="findbyid"></a>  CMFCRibbonStatusBar::FindByID

Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.

```
CMFCRibbonBaseElement* FindByID(UINT uiCmdID, BOOL = TRUE);
```

### <a name="parameters"></a>Parámetros

[in] *uiCmdID*<br/>
[in] *BOOL*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="findelement"></a>  CMFCRibbonStatusBar::FindElement

Devuelve un puntero al elemento que tiene el identificador de comando especificado.

```
CMFCRibbonBaseElement* FindElement(UINT uiID);
```

### <a name="parameters"></a>Parámetros

*uiID*<br/>
[in] El identificador del elemento.

### <a name="return-value"></a>Valor devuelto

Un puntero al elemento que tiene el identificador de comando especificado. Es NULL si no hay ningún elemento.

##  <a name="getcount"></a>  CMFCRibbonStatusBar::GetCount

Devuelve el número de elementos que se encuentran en el área principal de la barra de estado de la cinta de opciones.

```
int GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos que se encuentran en el área principal de la barra de estado de la cinta de opciones.

##  <a name="getelement"></a>  CMFCRibbonStatusBar::GetElement

Devuelve un puntero al elemento que se encuentra en el índice especificado.

```
CMFCRibbonBaseElement* GetElement(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[in] Especifica un índice de base cero de un elemento que se encuentra en el área principal del control de barra de estado.

### <a name="return-value"></a>Valor devuelto

Un puntero al elemento que se encuentra en el índice especificado. Es NULL si el índice es negativo o supera el número de elementos en la barra de estado.

### <a name="remarks"></a>Comentarios

##  <a name="getexcount"></a>  CMFCRibbonStatusBar::GetExCount

Devuelve el número de elementos que se encuentran en el área extendida de la barra de estado de la cinta de opciones.

```
int GetExCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos que se encuentran en el área extendida de la barra de estado de la cinta de opciones.

##  <a name="getexelement"></a>  CMFCRibbonStatusBar::GetExElement

Devuelve un puntero al elemento ubicado en el índice especificado en el área extendida de la barra de estado de la cinta. El área extendida está a la derecha del control de barra de estado.

```
CMFCRibbonBaseElement* GetExElement(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[in] Especifica el índice de base cero de un elemento que se encuentra en el área extendida del control de barra de estado.

### <a name="return-value"></a>Valor devuelto

Puntero al elemento ubicado en el índice especificado en el área extendida de la barra de estado de la cinta. NULL si *nIndex* es negativo o supera el número de elementos en el área extendida de la barra de estado de la cinta de opciones.

### <a name="remarks"></a>Comentarios

##  <a name="getextendedarea"></a>  CMFCRibbonStatusBar::GetExtendedArea

Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Parámetros

[in] *rect*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getspace"></a>  CMFCRibbonStatusBar::GetSpace

Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.

```
int GetSpace() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="isbottomframe"></a>  CMFCRibbonStatusBar::IsBottomFrame

Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.

```
BOOL IsBottomFrame() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="isextendedelement"></a>  CMFCRibbonStatusBar::IsExtendedElement

Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.

```
BOOL IsExtendedElement(CMFCRibbonBaseElement* pElement) const;
```

### <a name="parameters"></a>Parámetros

[in] *pElement*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="isinformationmode"></a>  CMFCRibbonStatusBar::IsInformationMode

Determina si está habilitado el modo de información para la barra de estado de la cinta de opciones.

```
BOOL IsInformationMode() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si la barra de estado, puede trabajar en modo de información; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

En el modo de información, la barra de estado oculta todos los paneles regulares y muestra una cadena de mensaje.

##  <a name="ondrawinformation"></a>  CMFCRibbonStatusBar::OnDrawInformation

Muestra la cadena que aparece en la barra cuando está habilitado el modo de información de estado de cinta de opciones.

```
virtual void OnDrawInformation(
    CDC* pDC,
    CString& strInfo,
    CRect rectInfo);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] Un puntero a un contexto de dispositivo.

*strInfo*<br/>
[in] La cadena de información.

*rectInfo*<br/>
[in] El rectángulo delimitador.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada si desea personalizar la apariencia de la cadena de información en la barra de estado. Use la [CMFCRibbonStatusBar::SetInformation](#setinformation) método para poner la barra de estado en modo de información. En este modo, la barra de estado oculta todos los paneles y muestra la cadena de información especificada por *strInfo*.

##  <a name="recalclayout"></a>  CMFCRibbonStatusBar::RecalcLayout

Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Comentarios

##  <a name="removeall"></a>  CMFCRibbonStatusBar::RemoveAll

Quita todos los elementos de la barra de estado de la cinta de opciones.

```
void RemoveAll();
```

##  <a name="removeelement"></a>  CMFCRibbonStatusBar::RemoveElement

Quita el elemento que tiene un identificador de comando especificado en la barra de estado de la cinta de opciones.

```
BOOL RemoveElement(UINT uiID);
```

### <a name="parameters"></a>Parámetros

*uiID*<br/>
[in] El identificador del elemento para quitar de la barra de estado.

### <a name="return-value"></a>Valor devuelto

TRUE si un elemento con los valores especificados *uiID* se quita. FALSE en caso contrario.

##  <a name="setinformation"></a>  CMFCRibbonStatusBar::SetInformation

Habilita o deshabilita el modo de información de la barra de estado de la cinta de opciones.

```
void SetInformation(LPCTSTR lpszInfo);
```

### <a name="parameters"></a>Parámetros

*lpszInfo*<br/>
[in] La cadena de información.

### <a name="remarks"></a>Comentarios

Utilice este método para colocar la barra de estado en el modo de información. En este modo, la barra de estado oculta todos los paneles y muestra la cadena de información especificada por *lpszInfo*.

Cuando lpszInfo es NULL, la barra de estado se vuelve al modo normal.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md)<br/>
[CMFCRibbonBaseElement (clase)](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md)
