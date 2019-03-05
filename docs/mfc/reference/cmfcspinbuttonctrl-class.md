---
title: CMFCSpinButtonCtrl (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl::OnDraw
helpviewer_keywords:
- CMFCSpinButtonCtrl [MFC], OnDraw
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
ms.openlocfilehash: 60808359c11604368493031e1b6f4573b3b2026f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292151"
---
# <a name="cmfcspinbuttonctrl-class"></a>CMFCSpinButtonCtrl (clase)

La `CMFCSpinButtonCtrl` clase es compatible con un administrador visual que dibuja un control de botón de número.

## <a name="syntax"></a>Sintaxis

```
class CMFCSpinButtonCtrl : public CSpinButtonCtrl
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|Constructor predeterminado.|
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCSpinButtonCtrl::OnDraw](#ondraw)|Vuelve a dibujar el control de botón de número actual.|

## <a name="remarks"></a>Comentarios

Para usar un administrador visual para dibujar un control de botón de número en la aplicación, reemplace todas las instancias de la `CSpinButtonCtrl` clase con la `CMFCSpinButtonCtrl` clase.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo crear un objeto de la `CMFCSpinButtonCtrl` clase y usar su `Create` método.

[!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)

[CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxspinbuttonctrl.h

##  <a name="ondraw"></a>  CMFCSpinButtonCtrl::OnDraw

Vuelve a dibujar el control de botón de número actual.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] Un puntero a un contexto de dispositivo.

### <a name="remarks"></a>Comentarios

Llama el marco del `CMFCSpinButtonCtrl::OnPaint` método para controlar el [CWnd::OnPaint](../../mfc/reference/cwnd-class.md#onpaint) mensaje y que a su vez llama método esto `CMFCSpinButtonCtrl::OnDraw` método. Invalide este método para personalizar la forma en que el marco dibuja el control de botón de número.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager (clase)](../../mfc/reference/cmfcvisualmanager-class.md)
