---
title: Clase CFolderPickerDialog
ms.date: 03/27/2019
f1_keywords:
- CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog::CFolderPickerDialog
helpviewer_keywords:
- CFolderPickerDialog [MFC], CFolderPickerDialog
ms.assetid: 8db01684-dd1d-4e9c-989e-07a2318a8156
ms.openlocfilehash: ed3dc151060519bce216cf4a2f3d6559d6b8937e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373871"
---
# <a name="cfolderpickerdialog-class"></a>Clase CFolderPickerDialog

CFolderPickerDialog clase implementa CFileDialog en el modo de selector de carpetas.

## <a name="syntax"></a>Sintaxis

```
class CFolderPickerDialog : public CFileDialog;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFolderPickerDialog::-CFolderPickerDialog](#_dtorcfolderpickerdialog)|Destructor.|
|[CFolderPickerDialog::CFolderPickerDialog](#cfolderpickerdialog)|Constructor.|

## <a name="remarks"></a>Observaciones

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[CFileDialog](../../mfc/reference/cfiledialog-class.md)

`CFolderPickerDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs.h

## <a name="cfolderpickerdialogcfolderpickerdialog"></a><a name="cfolderpickerdialog"></a>CFolderPickerDialog::CFolderPickerDialog

Constructor.

```
explicit CFolderPickerDialog(
    LPCTSTR lpszFolder = NULL,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL,
    DWORD dwSize = 0);
```

### <a name="parameters"></a>Parámetros

*lpszFolder*<br/>
Carpeta inicial.

*dwFlags*<br/>
Una combinación de uno o más indicadores que le permiten personalizar el cuadro de diálogo.

*pParentWnd*<br/>
Puntero a la ventana principal o propietaria del objeto de cuadro de diálogo.

*dwSize*<br/>
El tamaño de la estructura OPENFILENAME.

### <a name="remarks"></a>Observaciones

## <a name="cfolderpickerdialogcfolderpickerdialog"></a><a name="_dtorcfolderpickerdialog"></a>CFolderPickerDialog::-CFolderPickerDialog

Destructor.

```
virtual ~CFolderPickerDialog();
```

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
