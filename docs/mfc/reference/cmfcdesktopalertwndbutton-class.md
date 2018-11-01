---
title: CMFCDesktopAlertWndButton (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCaptionButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCloseButton
helpviewer_keywords:
- CMFCDesktopAlertWndButton [MFC], IsCaptionButton
- CMFCDesktopAlertWndButton [MFC], IsCloseButton
ms.assetid: df39a0c8-0c39-4ab0-8c64-78c5b2c4ecaf
ms.openlocfilehash: daa2f978b306bbe45f91514ada0f264a848521c0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450614"
---
# <a name="cmfcdesktopalertwndbutton-class"></a>CMFCDesktopAlertWndButton (clase)

Permite que los botones que se agregarán a un cuadro de diálogo de alerta de escritorio.

## <a name="syntax"></a>Sintaxis

```
class CMFCDesktopAlertWndButton : public CMFCButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Name|Descripción|
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|Constructor predeterminado.|
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Name|Descripción|
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|Determina si el botón se muestra en el área de título del cuadro de diálogo de alerta.|
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|Determina si el botón cierra el cuadro de diálogo de alerta.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|nombre|Descripción|
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|Un valor booleano que especifica si el botón se muestra en el área de título del cuadro de diálogo de alerta.|
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|Un valor booleano que especifica si el botón cierra el cuadro de diálogo de alerta.|

### <a name="remarks"></a>Comentarios

De forma predeterminada, el constructor establece la `m_bIsCaptionButton` y `m_bIsCloseButton` los miembros de datos en FALSE. El elemento primario `CMFCDesktopAlertDialog` conjuntos de objetos `m_bIsCaptionButton` en TRUE si el botón está situado en el área de título del cuadro de diálogo de alerta. El `CMFCDesktopAlertDialog` clase crea un `CMFCDesktopAlertWndButton` objeto que actúa como el botón que cierra el cuadro de diálogo de alerta cuadro y establece `m_bIsCloseButton` en TRUE.

Agregar `CMFCDesktopAlertWndButton` objetos a un `CMFCDesktopAlertDialog` como lo haría cualquier botón de objeto. Para obtener más información acerca de `CMFCDesktopAlertDialog`, consulte [CMFCDesktopAlertDialog (clase)](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar el `SetImage` método en el `CMFCDesktopAlertWndButton` clase. Este fragmento de código forma parte de la [ejemplo de demostración de alerta de escritorio](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdesktopalertwnd.h

##  <a name="iscaptionbutton"></a>  CMFCDesktopAlertWndButton::IsCaptionButton

Determina si el botón se muestra en el área de título del cuadro de diálogo de alerta.

```
BOOL IsCaptionButton() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el botón se muestra en el área de título del cuadro de diálogo de alerta; en caso contrario, es 0.

##  <a name="isclosebutton"></a>  CMFCDesktopAlertWndButton::IsCloseButton

Determina si el botón cierra el cuadro de diálogo de alerta.

```
BOOL IsCloseButton() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el botón cierra el cuadro de diálogo de alerta; en caso contrario, es 0.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertDialog (clase)](../../mfc/reference/cmfcdesktopalertdialog-class.md)
