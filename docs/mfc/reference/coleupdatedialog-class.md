---
title: Clase COleUpdateDialog
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
ms.openlocfilehash: 150e78b7880a61343db21c3c787ffdd1f0b734a5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503166"
---
# <a name="coleupdatedialog-class"></a>Clase COleUpdateDialog

Se utiliza para un caso especial del cuadro de diálogo Editar vínculos de OLE, que se debe utilizar cuando se necesita actualizar solo los objetos existentes vinculados o incrustados en un documento.

## <a name="syntax"></a>Sintaxis

```
class COleUpdateDialog : public COleLinksDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleUpdateDialog::COleUpdateDialog](#coleupdatedialog)|Construye un objeto `COleUpdateDialog`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleUpdateDialog::DoModal](#domodal)|Muestra el cuadro de diálogo **Editar vínculos** en un modo de actualización.|

## <a name="remarks"></a>Comentarios

Para obtener más información sobre los cuadros de diálogo específicos de OLE, vea los [cuadros de diálogo de artículo en OLE](../../mfc/dialog-boxes-in-ole.md).

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

**Encabezado:** afxodlgs. h

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
Apunta al documento que contiene los vínculos que pueden necesitar actualizarse.

*bUpdateLinks*<br/>
Marca que determina si los objetos vinculados se van a actualizar.

*bUpdateEmbeddings*<br/>
Marca que determina si los objetos incrustados se van a actualizar.

*pParentWnd*<br/>
Apunta al objeto de ventana primario o propietario (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del cuadro de diálogo se establecerá en la ventana principal de la aplicación.

### <a name="remarks"></a>Comentarios

Esta función solo crea un `COleUpdateDialog` objeto. Para mostrar el cuadro de diálogo, llame a [DoModal](../../mfc/reference/colelinksdialog-class.md#domodal). Se debe usar esta clase en lugar de `COleLinksDialog` cuando se desea actualizar solo los elementos vinculados o incrustados existentes.

##  <a name="domodal"></a>  COleUpdateDialog::DoModal

Muestra el cuadro de diálogo Editar vínculos en modo de actualización.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Estado de finalización del cuadro de diálogo. Uno de los siguientes valores:

- IDOK si el cuadro de diálogo se devuelve correctamente.

- IDCANCEL si no es necesario actualizar ninguno de los elementos vinculados o incrustados en el documento actual.

- IDABORT si se produjo un error. Si se devuelve IDABORT, llame a la función miembro [COleDialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) para obtener más información sobre el tipo de error que se ha producido. Para obtener una lista de posibles errores, vea la función [OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw) en el Windows SDK.

### <a name="remarks"></a>Comentarios

Todos los vínculos o las inserciones se actualizan a menos que el usuario seleccione el botón Cancelar.

## <a name="see-also"></a>Vea también

[Ejemplo OCLIENT de MFC](../../overview/visual-cpp-samples.md)<br/>
[COleLinksDialog (clase)](../../mfc/reference/colelinksdialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleLinksDialog (clase)](../../mfc/reference/colelinksdialog-class.md)
