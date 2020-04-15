---
title: COleUpdateDialog (clase)
ms.date: 11/04/2016
f1_keywords:
- COleUpdateDialog
- AFXODLGS/COleUpdateDialog
- AFXODLGS/COleUpdateDialog::COleUpdateDialog
- AFXODLGS/COleUpdateDialog::DoModal
helpviewer_keywords:
- COleUpdateDialog [MFC], COleUpdateDialog
- COleUpdateDialog [MFC], DoModal
ms.assetid: 699ca980-52b1-4cf8-9ab1-ac6767ad5b0e
ms.openlocfilehash: 9e2c7a8d79ebf5e6483a06354b280e474d7b8e61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374834"
---
# <a name="coleupdatedialog-class"></a>COleUpdateDialog (clase)

Se utiliza para un caso especial del cuadro de diálogo Editar vínculos de OLE, que se debe utilizar cuando se necesita actualizar solo los objetos existentes vinculados o incrustados en un documento.

## <a name="syntax"></a>Sintaxis

```
class COleUpdateDialog : public COleLinksDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleUpdateDialog::COleUpdateDialog](#coleupdatedialog)|Construye un objeto `COleUpdateDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleUpdateDialog::DoModal](#domodal)|Muestra el cuadro de diálogo **Editar vínculos** en modo de actualización.|

## <a name="remarks"></a>Observaciones

Para obtener más información acerca de los cuadros de diálogo específicos de OLE, vea el artículo [Cuadros](../../mfc/dialog-boxes-in-ole.md)de diálogo en OLE .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

[COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

`COleUpdateDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxodlgs.h

## <a name="coleupdatedialogcoleupdatedialog"></a><a name="coleupdatedialog"></a>COleUpdateDialog::COleUpdateDialog

Construye un objeto `COleUpdateDialog`.

```
explicit COleUpdateDialog(
    COleDocument* pDoc,
    BOOL bUpdateLinks = TRUE,
    BOOL bUpdateEmbeddings = FALSE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*pDoc*<br/>
Señala el documento que contiene los vínculos que pueden necesitar actualización.

*bUpdateLinks*<br/>
Marcador que determina si se van a actualizar los objetos vinculados.

*bUpdateEmbeddings*<br/>
Marcador que determina si se van a actualizar los objetos incrustados.

*pParentWnd*<br/>
Apunta al objeto de ventana principal `CWnd`o propietario (de tipo ) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del cuadro de diálogo se establecerá en la ventana principal de la aplicación.

### <a name="remarks"></a>Observaciones

Esta función construye `COleUpdateDialog` solo un objeto. Para mostrar el cuadro de diálogo, llame a [DoModal](../../mfc/reference/colelinksdialog-class.md#domodal). Esta clase se debe `COleLinksDialog` usar en lugar de cuando desea actualizar solo los elementos vinculados o incrustados existentes.

## <a name="coleupdatedialogdomodal"></a><a name="domodal"></a>COleUpdateDialog::DoModal

Muestra el cuadro de diálogo Editar vínculos en modo de actualización.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Estado de finalización del cuadro de diálogo. Uno de los valores siguientes:

- IDOK si el cuadro de diálogo se devolvió correctamente.

- IDCANCEL si ninguno de los elementos vinculados o incrustados en el documento actual necesita actualizarse.

- IDABORT si se ha producido un error. Si se devuelve IDABORT, llame a la [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea la función [OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw) en el Windows SDK.

### <a name="remarks"></a>Observaciones

Todos los vínculos y/o incrustaciones se actualizan a menos que el usuario seleccione el botón Cancelar.

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleLinksDialog (clase)](../../mfc/reference/colelinksdialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleLinksDialog (clase)](../../mfc/reference/colelinksdialog-class.md)
