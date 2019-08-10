---
title: Clase CMFCRibbonLinkCtrl
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CopyFrom
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetCompactSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetRegularSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetToolTipText
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::IsDrawTooltipImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDraw
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDrawMenuImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnMouseMove
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnSetIcon
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OpenLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::SetLink
helpviewer_keywords:
- CMFCRibbonLinkCtrl [MFC], CMFCRibbonLinkCtrl
- CMFCRibbonLinkCtrl [MFC], CopyFrom
- CMFCRibbonLinkCtrl [MFC], GetCompactSize
- CMFCRibbonLinkCtrl [MFC], GetLink
- CMFCRibbonLinkCtrl [MFC], GetRegularSize
- CMFCRibbonLinkCtrl [MFC], GetToolTipText
- CMFCRibbonLinkCtrl [MFC], IsDrawTooltipImage
- CMFCRibbonLinkCtrl [MFC], OnDraw
- CMFCRibbonLinkCtrl [MFC], OnDrawMenuImage
- CMFCRibbonLinkCtrl [MFC], OnMouseMove
- CMFCRibbonLinkCtrl [MFC], OnSetIcon
- CMFCRibbonLinkCtrl [MFC], OpenLink
- CMFCRibbonLinkCtrl [MFC], SetLink
ms.assetid: 77ae1941-e0ab-4a9d-911e-1752d34c079b
ms.openlocfilehash: 12a83e45176f7fc6020da1f0d0ee5923ef0f466c
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866165"
---
# <a name="cmfcribbonlinkctrl-class"></a>Clase CMFCRibbonLinkCtrl

Implementa un hipervínculo que se coloca en una cinta. El hipervínculo abre una página web cuando se hace clic en él.
Para obtener más información, consulte el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\MFC** de la instalación de Visual Studio.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonLinkCtrl : public CMFCRibbonButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl](#cmfcribbonlinkctrl)|Construye e inicializa un objeto `CMFCRibbonLinkCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CopyFrom](#copyfrom)|(Invalida `CMFCRibbonButton::CopyFrom`).|
|[CMFCRibbonLinkCtrl::GetCompactSize](#getcompactsize)|(Invalida [CMFCRibbonButton:: GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)).|
|[CMFCRibbonLinkCtrl::GetLink](#getlink)|Devuelve el valor del hipervínculo.|
|[CMFCRibbonLinkCtrl::GetRegularSize](#getregularsize)|(Invalida [CMFCRibbonButton:: GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)).|
|[CMFCRibbonLinkCtrl::GetToolTipText](#gettooltiptext)|(Invalida [CMFCRibbonButton:: getToolTipText](../../mfc/reference/cmfcribbonbutton-class.md#gettooltiptext)).|
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](#isdrawtooltipimage)|(Invalida `CMFCRibbonButton::IsDrawTooltipImage`).|
|[CMFCRibbonLinkCtrl::OnDraw](#ondraw)|(Invalida [CMFCRibbonButton:: OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)).|
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](#ondrawmenuimage)|(Invalida [CMFCRibbonBaseElement:: OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)).|
|[CMFCRibbonLinkCtrl::OnMouseMove](#onmousemove)|(Invalida `CMFCRibbonButton::OnMouseMove`).|
|[CMFCRibbonLinkCtrl::OnSetIcon](#onseticon)||
|[CMFCRibbonLinkCtrl::OpenLink](#openlink)|Se abre la página web especificada en el hipervínculo.|
|[CMFCRibbonLinkCtrl::SetLink](#setlink)|Establece el valor del hipervínculo.|

## <a name="remarks"></a>Comentarios

Después de crear un hipervínculo, agréguelo a un panel mediante una llamada a [CMFCRibbonPanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp;[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxRibbonLinkCtrl. h

##  <a name="cmfcribbonlinkctrl"></a>  CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl

Construye e inicializa un objeto [CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md) .

```
CMFCRibbonLinkCtrl(
    UINT nID,
    LPCTSTR lpszText,
    LPCTSTR lpszLink);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
de Especifica el identificador de comando del comando que se ejecuta cuando se hace clic en el control de vínculo.

*lpszText*<br/>
de Especifica la etiqueta que se va a mostrar en el control de vínculo.

*lpszLink*<br/>
de Especifica el hipervínculo asociado al control de vínculo.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar el constructor de `CMFCRibbonLinkCtrl` la clase. Este fragmento de código forma parte del [ejemplo gadgets](../../overview/visual-cpp-samples.md)de la cinta de opciones.

[!code-cpp[NVC_MFC_RibbonGadgets#1](../../mfc/reference/codesnippet/cpp/cmfcribbonlinkctrl-class_1.cpp)]

##  <a name="copyfrom"></a>CMFCRibbonLinkCtrl:: CopyFrom

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parámetros

de *src*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="getcompactsize"></a>  CMFCRibbonLinkCtrl::GetCompactSize

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

de *pDC* de<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getlink"></a>  CMFCRibbonLinkCtrl::GetLink

Devuelve el valor del hipervínculo.

```
LPCTSTR GetLink() const;
```

### <a name="return-value"></a>Valor devuelto

Valor actual del hipervínculo.

### <a name="remarks"></a>Comentarios

##  <a name="getregularsize"></a>  CMFCRibbonLinkCtrl::GetRegularSize

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

de *pDC* de<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="gettooltiptext"></a>  CMFCRibbonLinkCtrl::GetToolTipText

```
virtual CString GetToolTipText() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="ondrawmenuimage"></a>  CMFCRibbonLinkCtrl::OnDrawMenuImage

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>Parámetros

de *CDC&#42;*<br/>
de *CRect*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="isdrawtooltipimage"></a>  CMFCRibbonLinkCtrl::IsDrawTooltipImage

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="ondraw"></a>  CMFCRibbonLinkCtrl::OnDraw

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

de *pDC* de<br/>

### <a name="remarks"></a>Comentarios

##  <a name="onmousemove"></a>  CMFCRibbonLinkCtrl::OnMouseMove

```
virtual void OnMouseMove(CPoint point);
```

### <a name="parameters"></a>Parámetros

de *punto* de<br/>

### <a name="remarks"></a>Comentarios

##  <a name="onseticon"></a>  CMFCRibbonLinkCtrl::OnSetIcon

```
virtual void OnSetIcon();
```

### <a name="remarks"></a>Comentarios

##  <a name="openlink"></a>  CMFCRibbonLinkCtrl::OpenLink

Se abre la página web especificada en el hipervínculo.

```
BOOL OpenLink();
```

### <a name="return-value"></a>Valor devuelto

TRUE si la página web asociada se abrió correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Abre una página web con el hipervínculo asociado `CMFCRibbonLinkCtrl` al objeto.

##  <a name="setlink"></a>  CMFCRibbonLinkCtrl::SetLink

Establece el valor del hipervínculo.

```
void SetLink(LPCTSTR lpszLink);
```

### <a name="parameters"></a>Parámetros

*lpszLink*<br/>
de Especifica el texto del hipervínculo.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton (clase)](../../mfc/reference/cmfcribbonbutton-class.md)
