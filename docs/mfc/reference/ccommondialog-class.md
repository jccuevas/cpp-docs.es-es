---
title: Clase CCommonDialog
ms.date: 11/04/2016
f1_keywords:
- CCommonDialog
- AFXDLGS/CCommonDialog
- AFXDLGS/CCommonDialog::CCommonDialog
helpviewer_keywords:
- CCommonDialog [MFC], CCommonDialog
ms.assetid: 1f68d65f-a0fd-4778-be22-ebbe51a95f95
ms.openlocfilehash: 853a4756df3b70f4f33deb7159b4d1aee610092c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369442"
---
# <a name="ccommondialog-class"></a>Clase CCommonDialog

La clase base para las clases que encapsulan la funcionalidad de los cuadros de diálogo comunes de Windows.

## <a name="syntax"></a>Sintaxis

```
class CCommonDialog : public CDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCommonDialog::CCommonDialog](#ccommondialog)|Construye un objeto `CCommonDialog`.|

## <a name="remarks"></a>Observaciones

Las clases siguientes encapsulan la funcionalidad de los cuadros de diálogo comunes de Windows:

- [CFileDialog](../../mfc/reference/cfiledialog-class.md)

- [CFontDialog](../../mfc/reference/cfontdialog-class.md)

- [CColorDialog](../../mfc/reference/ccolordialog-class.md)

- [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)

- [CPrintDialog](../../mfc/reference/cprintdialog-class.md)

- [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)

- [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)

- [COleDialog](../../mfc/reference/coledialog-class.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CCommonDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs.h

## <a name="ccommondialogccommondialog"></a><a name="ccommondialog"></a>CCommonDialog::CCommonDialog

Construye un objeto `CCommonDialog`.

```
explicit CCommonDialog(CWnd* pParentWnd);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Apunta al objeto de ventana primario o propietario (de tipo [CWnd](../../mfc/reference/cwnd-class.md)) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.

### <a name="remarks"></a>Observaciones

Vea [CDialog::CDialog](../../mfc/reference/cdialog-class.md#cdialog) para obtener información completa.

## <a name="see-also"></a>Consulte también

[Clase CDialog](../../mfc/reference/cdialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFileDialog (clase)](../../mfc/reference/cfiledialog-class.md)<br/>
[Clase CFontDialog](../../mfc/reference/cfontdialog-class.md)<br/>
[CColorDialog (clase)](../../mfc/reference/ccolordialog-class.md)<br/>
[Clase CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)<br/>
[Clase CPrintDialog](../../mfc/reference/cprintdialog-class.md)<br/>
[Clase CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)
