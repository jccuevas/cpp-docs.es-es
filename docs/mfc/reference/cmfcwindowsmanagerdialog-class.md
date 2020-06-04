---
title: CMFCWindowsManagerDialog (Clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog
helpviewer_keywords:
- CMFCWindowsManagerDialog [MFC], CMFCWindowsManagerDialog
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
ms.openlocfilehash: e3928c0d3ae4f607dceb99c0762277e8ea9ddbde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319825"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>CMFCWindowsManagerDialog (Clase)

El `CMFCWindowsManagerDialog` objeto permite a un usuario administrar ventanas secundarias MDI en una aplicación MDI.

## <a name="syntax"></a>Sintaxis

```
class CMFCWindowsManagerDialog : public CDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCWindowsManagerDialog::CMFCWindowsManagerDialog](#cmfcwindowsmanagerdialog)|Construye un objeto `CMFCWindowsManagerDialog`.|

## <a name="remarks"></a>Observaciones

Contiene `CMFCWindowsManagerDialog` una lista de ventanas secundarias MDI que están abiertas actualmente en la aplicación. El usuario puede controlar manualmente el estado de las ventanas secundarias MDI mediante este cuadro de diálogo.

`CMFCWindowsManagerDialog`está incrustado dentro de la [CMDIFrameWndEx (clase).](../../mfc/reference/cmdiframewndex-class.md) No `CMFCWindowsManagerDialog` es una clase que debe crear manualmente. En su lugar, llame a la función [CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog)y creará y mostrará un `CMFCWindowsManagerDialog` objeto.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se `CMFCWindowsManagerDialog` muestra `CMDIFrameWndEx::ShowWindowsDialog`cómo construir un objeto llamando a . Este fragmento de código forma parte del [ejemplo de demostración](../../overview/visual-cpp-samples.md)de Visual Studio.

[!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxWindowsManagerDialog.h

## <a name="cmfcwindowsmanagerdialogcmfcwindowsmanagerdialog"></a><a name="cmfcwindowsmanagerdialog"></a>CMFCWindowsManagerDialog::CMFCWindowsManagerDialog

Construye un [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) objeto.

```
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,
    BOOL bHelpButton = FALSE);
```

### <a name="parameters"></a>Parámetros

*pMDIFrame*<br/>
[en] Un puntero a la ventana principal o propietario.

*bHelpButton*<br/>
[en] Un parámetro booleano que especifica si el marco de trabajo muestra un botón **Ayuda.**

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de los administradores visuales, consulte [Administrador de visualización](../../mfc/visualization-manager.md).

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMDIFrameWndEx Clase](../../mfc/reference/cmdiframewndex-class.md)
