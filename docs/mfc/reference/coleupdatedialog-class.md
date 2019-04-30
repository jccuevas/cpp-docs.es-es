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
ms.openlocfilehash: b8e580130b025f07b8f85a624b7f5a224a00e49e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62373601"
---
# <a name="coleupdatedialog-class"></a>COleUpdateDialog (clase)

Se utiliza para un caso especial del cuadro de diálogo Editar vínculos de OLE, que se debe utilizar cuando se necesita actualizar solo los objetos existentes vinculados o incrustados en un documento.

## <a name="syntax"></a>Sintaxis

```
class COleUpdateDialog : public COleLinksDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[COleUpdateDialog::COleUpdateDialog](#coleupdatedialog)|Construye un objeto `COleUpdateDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COleUpdateDialog::DoModal](#domodal)|Muestra el **editar vínculos** cuadro de diálogo en el modo de actualización.|

## <a name="remarks"></a>Comentarios

Para obtener más información sobre los cuadros de diálogo OLE específicos, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).

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

##  <a name="coleupdatedialog"></a>  COleUpdateDialog::COleUpdateDialog

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
Señala el documento que contiene los vínculos que necesiten actualizarse.

*bUpdateLinks*<br/>
Marca que determina si los objetos vinculados deben actualizarse.

*bUpdateEmbeddings*<br/>
Marca que determina si los objetos incrustados se van a actualizarse.

*pParentWnd*<br/>
Señala al objeto de ventana principal o propietaria (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del cuadro de diálogo se establecerá en la ventana principal de la aplicación.

### <a name="remarks"></a>Comentarios

Esta función solo construye un `COleUpdateDialog` objeto. Para mostrar el cuadro de diálogo, llame a [DoModal](../../mfc/reference/colelinksdialog-class.md#domodal). Esta clase se debe usar en lugar de `COleLinksDialog` cuando desea actualizar solo existentes elementos vinculados o incrustados.

##  <a name="domodal"></a>  COleUpdateDialog::DoModal

Muestra el cuadro de diálogo Editar vínculos cuadro en modo de actualización.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Estado de finalización para el cuadro de diálogo. Uno de los siguientes valores:

- IDOK si se devolvió correctamente el cuadro de diálogo.

- IDCANCEL si ninguno de los elementos vinculados o incrustados en el documento actual deben actualizar.

- IDABORT si se produjo un error. Si se devuelve IDABORT, llame a la [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea el [OleUIEditLinks](/windows/desktop/api/oledlg/nf-oledlg-oleuieditlinksa) función en el SDK de Windows.

### <a name="remarks"></a>Comentarios

Todos los vínculos o incrustaciones se actualizan a menos que el usuario selecciona el botón Cancelar.

## <a name="see-also"></a>Vea también

[Ejemplo MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleLinksDialog (clase)](../../mfc/reference/colelinksdialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleLinksDialog (clase)](../../mfc/reference/colelinksdialog-class.md)
