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
ms.openlocfilehash: 5b18a15f8bfd98396acae0558d121b32bc4127c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367623"
---
# <a name="cmfcdesktopalertwndbutton-class"></a>CMFCDesktopAlertWndButton (clase)

Permite agregar botones a un cuadro de diálogo de alerta de escritorio.

## <a name="syntax"></a>Sintaxis

```
class CMFCDesktopAlertWndButton : public CMFCButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Nombre|Descripción|
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|Constructor predeterminado.|
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Nombre|Descripción|
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|Determina si el botón se muestra en el área de título del cuadro de diálogo de alerta.|
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|Determina si el botón cierra el cuadro de diálogo de alerta.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|Nombre|Descripción|
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|Valor booleano que especifica si el botón se muestra en el área de título del cuadro de diálogo de alerta.|
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|Valor booleano que especifica si el botón cierra el cuadro de diálogo de alerta.|

### <a name="remarks"></a>Observaciones

De forma predeterminada, `m_bIsCaptionButton` el `m_bIsCloseButton` constructor establece los miembros de datos y FALSE. El `CMFCDesktopAlertDialog` objeto `m_bIsCaptionButton` primario se establece en TRUE si el botón se coloca en el área de título del cuadro de diálogo de alerta. La `CMFCDesktopAlertDialog` clase `CMFCDesktopAlertWndButton` crea un objeto que actúa como el botón que cierra el cuadro de diálogo de alerta y se establece en `m_bIsCloseButton` TRUE.

Agregue `CMFCDesktopAlertWndButton` objetos `CMFCDesktopAlertDialog` a un objeto como agregaría cualquier botón. Para obtener `CMFCDesktopAlertDialog`más información acerca de , vea [CMFCDesktopAlertDialog (Clase)](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se `SetImage` muestra `CMFCDesktopAlertWndButton` cómo utilizar el método en la clase. Este fragmento de código forma parte del [ejemplo Demostración de alertas](../../overview/visual-cpp-samples.md)de escritorio.

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

## <a name="cmfcdesktopalertwndbuttoniscaptionbutton"></a><a name="iscaptionbutton"></a>CMFCDesktopAlertWndButton::IsCaptionButton

Determina si el botón se muestra en el área de título del cuadro de diálogo de alerta.

```
BOOL IsCaptionButton() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el botón se muestra en el área de título del cuadro de diálogo de alerta; de lo contrario, 0.

## <a name="cmfcdesktopalertwndbuttonisclosebutton"></a><a name="isclosebutton"></a>CMFCDesktopAlertWndButton::IsCloseButton

Determina si el botón cierra el cuadro de diálogo de alerta.

```
BOOL IsCloseButton() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el botón cierra el cuadro de diálogo de alerta; de lo contrario, 0.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertDialog (clase)](../../mfc/reference/cmfcdesktopalertdialog-class.md)
