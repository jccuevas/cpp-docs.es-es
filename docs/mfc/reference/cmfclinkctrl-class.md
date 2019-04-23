---
title: CMFCLinkCtrl (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl::SetURL
- AFXLINKCTRL/CMFCLinkCtrl::SetURLPrefix
- AFXLINKCTRL/CMFCLinkCtrl::SizeToContent
- AFXLINKCTRL/CMFCLinkCtrl::OnDrawFocusRect
helpviewer_keywords:
- CMFCLinkCtrl [MFC], SetURL
- CMFCLinkCtrl [MFC], SetURLPrefix
- CMFCLinkCtrl [MFC], SizeToContent
- CMFCLinkCtrl [MFC], OnDrawFocusRect
ms.assetid: 80f3874d-7cc8-410e-9ff1-62a225f5034b
ms.openlocfilehash: 839448694cee17f5bc1a1e47f7c113026a1a4006
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58776432"
---
# <a name="cmfclinkctrl-class"></a>CMFCLinkCtrl (clase)

La `CMFCLinkCtrl` clase muestra un botón como hipervínculo e invoca el destino del vínculo cuando se hace clic en el botón.

## <a name="syntax"></a>Sintaxis

```
class CMFCLinkCtrl : public CMFCButton
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCLinkCtrl::SetURL](#seturl)|Muestra una dirección URL especificada como el texto del botón.|
|[CMFCLinkCtrl::SetURLPrefix](#seturlprefix)|Establece el protocolo implícito (por ejemplo, "http:") de la dirección URL.|
|[CMFCLinkCtrl::SizeToContent](#sizetocontent)|Cambia el tamaño del botón para que contenga el texto del botón o un mapa de bits.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|Lo llama el marco de trabajo antes de que se dibuja el rectángulo de foco del botón.|

## <a name="remarks"></a>Comentarios

Al hacer clic en un botón que se deriva el `CMFCLinkCtrl` (clase), el marco de trabajo pasa la dirección URL del botón como un parámetro a la `ShellExecute` método. El `ShellExecute` método abre el destino de la dirección URL.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo establecer el tamaño de un `CMFCLinkCtrl` objeto y cómo establecer una dirección url y una información sobre herramientas en un `CMFCLinkCtrl` objeto. Este ejemplo forma parte de la [ejemplo de controles nuevos](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#9](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#10](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxlinkctrl.h

##  <a name="ondrawfocusrect"></a>  CMFCLinkCtrl::OnDrawFocusRect

Lo llama el marco de trabajo antes de que se dibuja el rectángulo de foco del botón.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] Un puntero a un contexto de dispositivo.

*rectClient*<br/>
[in] Un rectángulo que delimita el control de vínculo.

### <a name="remarks"></a>Comentarios

Invalide este método cuando desee utilizar su propio código para dibujar el rectángulo de foco del botón.

##  <a name="seturl"></a>  CMFCLinkCtrl::SetURL

Muestra una dirección URL especificada como el texto del botón.

```
void SetURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>Parámetros

*lpszURL*<br/>
[in] Para mostrar el texto del botón.

### <a name="remarks"></a>Comentarios

##  <a name="seturlprefix"></a>  CMFCLinkCtrl::SetURLPrefix

Establece el protocolo implícito (por ejemplo, "http:") de la dirección URL.

```
void SetURLPrefix(LPCTSTR lpszPrefix);
```

### <a name="parameters"></a>Parámetros

*lpszPrefix*<br/>
[in] El prefijo del protocolo de dirección URL.

### <a name="remarks"></a>Comentarios

Utilice este método para establecer el prefijo de dirección URL. El prefijo no se muestra en la cara del botón, pero se puede usar para ayudar a buscar de destino de la dirección URL.

##  <a name="sizetocontent"></a>  CMFCLinkCtrl::SizeToContent

Cambia el tamaño del botón para que contenga el texto del botón o un mapa de bits.

```
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,
    BOOL bHCenter=FALSE);
```

### <a name="parameters"></a>Parámetros

*bVCenter*<br/>
[in] TRUE para centrar el texto del botón y un mapa de bits verticalmente entre la parte superior e inferior del control de vínculo; en caso contrario, FALSE. El valor predeterminado es FALSE.

*bHCenter*<br/>
[in] TRUE para centrar el texto del botón y un mapa de bits horizontalmente entre los lados izquierdo y derecho del control link; en caso contrario, FALSE. El valor predeterminado es FALSE.

### <a name="return-value"></a>Valor devuelto

Un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que contiene el nuevo tamaño del control link.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CLinkCtrl (clase)](../../mfc/reference/clinkctrl-class.md)<br/>
[CMFCButton (clase)](../../mfc/reference/cmfcbutton-class.md)
