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
ms.openlocfilehash: 445b857400d8c82109ca7220b84bac692a2abf89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376178"
---
# <a name="cmfcspinbuttonctrl-class"></a>CMFCSpinButtonCtrl (clase)

La `CMFCSpinButtonCtrl` clase admite un administrador visual que dibuja un control de botón de giro.

## <a name="syntax"></a>Sintaxis

```
class CMFCSpinButtonCtrl : public CSpinButtonCtrl
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|Constructor predeterminado.|
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCSpinButtonCtrl::OnDraw](#ondraw)|Repinta el control de botón de giro actual.|

## <a name="remarks"></a>Observaciones

Para usar un administrador visual para dibujar un control de botón `CSpinButtonCtrl` de `CMFCSpinButtonCtrl` giro en la aplicación, reemplace todas las instancias de la clase por la clase.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCSpinButtonCtrl` cómo crear `Create` un objeto de la clase y utilizar su método.

[!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)

[CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxspinbuttonctrl.h

## <a name="cmfcspinbuttonctrlondraw"></a><a name="ondraw"></a>CMFCSpinButtonCtrl::OnDraw

Repinta el control de botón de giro actual.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

### <a name="remarks"></a>Observaciones

El marco `CMFCSpinButtonCtrl::OnPaint` de trabajo llama al método para controlar el [CWnd::OnPaint](../../mfc/reference/cwnd-class.md#onpaint) mensaje y ese método a su vez llama a este `CMFCSpinButtonCtrl::OnDraw` método. Invalide este método para personalizar la forma en que el marco de trabajo dibuja el control de botón de giro.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager (Clase)](../../mfc/reference/cmfcvisualmanager-class.md)
