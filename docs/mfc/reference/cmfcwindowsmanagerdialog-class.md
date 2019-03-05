---
title: CMFCWindowsManagerDialog (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog
helpviewer_keywords:
- CMFCWindowsManagerDialog [MFC], CMFCWindowsManagerDialog
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
ms.openlocfilehash: 566eae1f1b2ca4e91ed2c4b41c36073c205a272e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302798"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>CMFCWindowsManagerDialog (clase)

La `CMFCWindowsManagerDialog` objeto permite que un usuario administrar ventanas secundarias MDI en una aplicación MDI.

## <a name="syntax"></a>Sintaxis

```
class CMFCWindowsManagerDialog : public CDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCWindowsManagerDialog::CMFCWindowsManagerDialog](#cmfcwindowsmanagerdialog)|Construye un objeto `CMFCWindowsManagerDialog`.|

## <a name="remarks"></a>Comentarios

El `CMFCWindowsManagerDialog` contiene una lista de ventanas MDI secundarias abiertas en la aplicación. El usuario puede controlar manualmente el estado de las ventanas secundarias MDI mediante este cuadro de diálogo.

`CMFCWindowsManagerDialog` se incrusta dentro de la [CMDIFrameWndEx (clase)](../../mfc/reference/cmdiframewndex-class.md). El `CMFCWindowsManagerDialog` no es una clase que debe crear manualmente. En su lugar, llame a la función [CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog), y creará y mostrar un `CMFCWindowsManagerDialog` objeto.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un `CMFCWindowsManagerDialog` objeto mediante una llamada a `CMDIFrameWndEx::ShowWindowsDialog`. Este fragmento de código forma parte de la [ejemplo de demostración de Visual Studio](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxWindowsManagerDialog.h

##  <a name="cmfcwindowsmanagerdialog"></a>  CMFCWindowsManagerDialog::CMFCWindowsManagerDialog

Construye un [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) objeto.

```
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,
    BOOL bHelpButton = FALSE);
```

### <a name="parameters"></a>Parámetros

*pMDIFrame*<br/>
[in] Un puntero a la ventana principal o propietaria.

*bHelpButton*<br/>
[in] Un parámetro booleano que especifica si el marco de trabajo muestra un **ayuda** botón.

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de los administradores visuales, consulte [Administrador de visualización](../../mfc/visualization-manager.md).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMDIFrameWndEx (clase)](../../mfc/reference/cmdiframewndex-class.md)
