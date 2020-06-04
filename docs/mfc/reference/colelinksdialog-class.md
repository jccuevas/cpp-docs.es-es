---
title: COleLinksDialog (clase)
ms.date: 11/04/2016
f1_keywords:
- COleLinksDialog
- AFXODLGS/COleLinksDialog
- AFXODLGS/COleLinksDialog::COleLinksDialog
- AFXODLGS/COleLinksDialog::DoModal
- AFXODLGS/COleLinksDialog::m_el
helpviewer_keywords:
- COleLinksDialog [MFC], COleLinksDialog
- COleLinksDialog [MFC], DoModal
- COleLinksDialog [MFC], m_el
ms.assetid: fb2eb638-2809-46db-ac74-392a732affc7
ms.openlocfilehash: f120678c822749c8f27c3c56c95fcdd54647aca3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374931"
---
# <a name="colelinksdialog-class"></a>COleLinksDialog (clase)

Se utiliza en el cuadro de diálogo Editar vínculos de OLE.

## <a name="syntax"></a>Sintaxis

```
class COleLinksDialog : public COleDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleLinksDialog::COleLinksDialog](#colelinksdialog)|Construye un objeto `COleLinksDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleLinksDialog::DoModal](#domodal)|Muestra el cuadro de diálogo Editar vínculos OLE.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleLinksDialog::m_el](#m_el)|Estructura de tipo OLEUIEDITLINKS que controla el comportamiento del cuadro de diálogo.|

## <a name="remarks"></a>Observaciones

Cree un objeto `COleLinksDialog` de clase cuando desee llamar a este cuadro de diálogo. Una `COleLinksDialog` vez construido un objeto, puede utilizar la [estructura m_el](#m_el) para inicializar los valores o estados de los controles en el cuadro de diálogo. La `m_el` estructura es de tipo OLEUIEDITLINKS. Para obtener más información sobre el uso de esta clase de cuadro de diálogo, vea el [DoModal](#domodal) función miembro.

> [!NOTE]
> El código de contenedor generado por el Asistente para aplicaciones utiliza esta clase.

Para obtener más información, vea la estructura [OLEUIEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw) en el Windows SDK.

Para obtener más información acerca de los cuadros de diálogo específicos de OLE, vea el artículo [Cuadros](../../mfc/dialog-boxes-in-ole.md)de diálogo en OLE .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleLinksDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxodlgs.h

## <a name="colelinksdialogdomodal"></a><a name="domodal"></a>COleLinksDialog::DoModal

Muestra el cuadro de diálogo Editar vínculos OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Estado de finalización del cuadro de diálogo. Uno de los valores siguientes:

- IDOK si el cuadro de diálogo se ha mostrado correctamente.

- IDCANCEL si el usuario canceló el cuadro de diálogo.

- IDABORT si se ha producido un error. Si se devuelve IDABORT, llame a la `COleDialog::GetLastError` función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea la función [OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw) en el Windows SDK.

### <a name="remarks"></a>Observaciones

Si desea inicializar los distintos controles de cuadro de diálogo estableciendo `DoModal`miembros de la [estructura m_el,](#m_el) debe hacerlo antes de llamar a , pero después de que se construye el objeto de cuadro de diálogo.

## <a name="colelinksdialogcolelinksdialog"></a><a name="colelinksdialog"></a>COleLinksDialog::COleLinksDialog

Construye un objeto `COleLinksDialog`.

```
COleLinksDialog (
    COleDocument* pDoc,
    CView* pView,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*pDoc*<br/>
Apunta al documento OLE que contiene los vínculos que se van a editar.

*pView*<br/>
Señala a la vista actual en *pDoc*.

*dwFlags*<br/>
Marca de creación, que contiene 0 o ELF_SHOWHELP para especificar si el botón Ayuda se mostrará cuando se muestre el cuadro de diálogo.

*pParentWnd*<br/>
Apunta al objeto de ventana principal `CWnd`o propietario (de tipo ) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del cuadro de diálogo se establece en la ventana principal de la aplicación.

### <a name="remarks"></a>Observaciones

Esta función construye `COleLinksDialog` solo un objeto. Para mostrar el cuadro de diálogo, llame a la [Función DoModal.](#domodal)

## <a name="colelinksdialogm_el"></a><a name="m_el"></a>COleLinksDialog::m_el

Estructura de tipo OLEUIEDITLINKS utilizada para controlar el comportamiento del cuadro de diálogo Editar vínculos.

```
OLEUIEDITLINKS m_el;
```

### <a name="remarks"></a>Observaciones

Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.

Para obtener más información, vea la estructura [OLEUIEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)
