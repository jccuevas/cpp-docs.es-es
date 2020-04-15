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
ms.openlocfilehash: 1ef4e390d88f81d738d2ee18be6ba02843633011
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374402"
---
# <a name="cmfclinkctrl-class"></a>CMFCLinkCtrl (clase)

La `CMFCLinkCtrl` clase muestra un botón como hipervínculo e invoca el destino del vínculo cuando se hace clic en el botón.

## <a name="syntax"></a>Sintaxis

```
class CMFCLinkCtrl : public CMFCButton
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCLinkCtrl::SetURL](#seturl)|Muestra una dirección URL especificada como texto del botón.|
|[CMFCLinkCtrl::SetURLPrefix](#seturlprefix)|Establece el protocolo implícito (por ejemplo, "http:") de la dirección URL.|
|[CMFCLinkCtrl::SizeToContent](#sizetocontent)|Cambia el tamaño del botón para que contenga el texto del botón o el mapa de bits.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|Llamado por el marco de trabajo antes de dibujar el rectángulo de foco del botón.|

## <a name="remarks"></a>Observaciones

Al hacer clic en un botón que se deriva de la `CMFCLinkCtrl` clase, el `ShellExecute` marco de trabajo pasa la dirección URL del botón como parámetro al método. A `ShellExecute` continuación, el método abre el destino de la dirección URL.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCLinkCtrl` cómo establecer el tamaño de un objeto `CMFCLinkCtrl` y cómo establecer una url y una información sobre herramientas en un objeto. Este ejemplo forma parte del [ejemplo Nuevos controles](../../overview/visual-cpp-samples.md).

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

## <a name="cmfclinkctrlondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFCLinkCtrl::OnDrawFocusRect

Llamado por el marco de trabajo antes de dibujar el rectángulo de foco del botón.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

*rectClient*<br/>
[en] Rectángulo que limita el control de vínculo.

### <a name="remarks"></a>Observaciones

Invalide este método cuando desee usar su propio código para dibujar el rectángulo de foco del botón.

## <a name="cmfclinkctrlseturl"></a><a name="seturl"></a>CMFCLinkCtrl::SetURL

Muestra una dirección URL especificada como texto del botón.

```
void SetURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>Parámetros

*lpszURL*<br/>
[en] El texto del botón que se va a mostrar.

### <a name="remarks"></a>Observaciones

## <a name="cmfclinkctrlseturlprefix"></a><a name="seturlprefix"></a>CMFCLinkCtrl::SetURLPrefix

Establece el protocolo implícito (por ejemplo, "http:") de la dirección URL.

```
void SetURLPrefix(LPCTSTR lpszPrefix);
```

### <a name="parameters"></a>Parámetros

*lpszPrefix*<br/>
[en] El prefijo del protocolo URL.

### <a name="remarks"></a>Observaciones

Utilice este método para establecer el prefijo de dirección URL. El prefijo no se muestra en la cara del botón, pero puede usarlo para ayudar a buscar el destino de la dirección URL.

## <a name="cmfclinkctrlsizetocontent"></a><a name="sizetocontent"></a>CMFCLinkCtrl::SizeToContent

Cambia el tamaño del botón para que contenga el texto del botón o el mapa de bits.

```
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,
    BOOL bHCenter=FALSE);
```

### <a name="parameters"></a>Parámetros

*bVCenter*<br/>
[en] TRUE para centrar el texto del botón y el mapa de bits verticalmente entre la parte superior e inferior del control de vínculo; de lo contrario, FALSE. El valor predeterminado es FALSE.

*bHCenter*<br/>
[en] TRUE para centrar el texto del botón y el mapa de bits horizontalmente entre los lados izquierdo y derecho del control de vínculo; de lo contrario, FALSE. El valor predeterminado es FALSE.

### <a name="return-value"></a>Valor devuelto

Un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que contiene el nuevo tamaño del control de vínculo.

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CLinkCtrl (clase)](../../mfc/reference/clinkctrl-class.md)<br/>
[CMFCButton (Clase)](../../mfc/reference/cmfcbutton-class.md)
