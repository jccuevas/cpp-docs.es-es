---
title: Clase COleLinksDialog
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
ms.openlocfilehash: 911108f9a231b752790abfdf86d1b4042d30b149
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504119"
---
# <a name="colelinksdialog-class"></a>Clase COleLinksDialog

Se utiliza en el cuadro de diálogo Editar vínculos de OLE.

## <a name="syntax"></a>Sintaxis

```
class COleLinksDialog : public COleDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleLinksDialog::COleLinksDialog](#colelinksdialog)|Construye un objeto `COleLinksDialog`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleLinksDialog::DoModal](#domodal)|Muestra el cuadro de diálogo Editar vínculos de OLE.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleLinksDialog::m_el](#m_el)|Estructura de tipo OLEUIEDITLINKS que controla el comportamiento del cuadro de diálogo.|

## <a name="remarks"></a>Comentarios

Cree un objeto de clase `COleLinksDialog` cuando desee llamar a este cuadro de diálogo. Una vez `COleLinksDialog` construido un objeto, puede usar la estructura [m_el](#m_el) para inicializar los valores o los Estados de los controles en el cuadro de diálogo. La `m_el` estructura es de tipo OLEUIEDITLINKS. Para obtener más información sobre el uso de esta clase de cuadro de diálogo, vea la función miembro [DoModal](#domodal) .

> [!NOTE]
>  El código de contenedor generado por el Asistente para aplicaciones utiliza esta clase.

Para obtener más información, vea la estructura [OLEUIEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw) en el Windows SDK.

Para obtener más información sobre los cuadros de diálogo específicos de OLE, vea los [cuadros de diálogo de artículo en OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleLinksDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxodlgs. h

##  <a name="domodal"></a>COleLinksDialog::D oModal

Muestra el cuadro de diálogo Editar vínculos de OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Estado de finalización del cuadro de diálogo. Uno de los siguientes valores:

- IDOK si el cuadro de diálogo se mostró correctamente.

- IDCANCEL si el usuario canceló el cuadro de diálogo.

- IDABORT si se produjo un error. Si se devuelve IDABORT, llame a `COleDialog::GetLastError` la función miembro para obtener más información sobre el tipo de error que se ha producido. Para obtener una lista de posibles errores, vea la función [OleUIEditLinks](/windows/win32/api/oledlg/nf-oledlg-oleuieditlinksw) en el Windows SDK.

### <a name="remarks"></a>Comentarios

Si desea inicializar los distintos controles de cuadro de diálogo estableciendo los miembros de la estructura [m_el](#m_el) , debe hacerlo antes de llamar `DoModal`a, pero después de que se construya el objeto de cuadro de diálogo.

##  <a name="colelinksdialog"></a>COleLinksDialog::COleLinksDialog

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
Apunta a la vista actual en *pDoc*.

*dwFlags*<br/>
Marca de creación, que contiene 0 o ELF_SHOWHELP para especificar si se mostrará el botón ayuda cuando se muestre el cuadro de diálogo.

*pParentWnd*<br/>
Apunta al objeto de ventana primario o propietario (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del cuadro de diálogo se establece en la ventana principal de la aplicación.

### <a name="remarks"></a>Comentarios

Esta función solo crea un `COleLinksDialog` objeto. Para mostrar el cuadro de diálogo, llame a la función [DoModal](#domodal) .

##  <a name="m_el"></a>COleLinksDialog::m_el

Estructura de tipo OLEUIEDITLINKS que se usa para controlar el comportamiento del cuadro de diálogo Editar vínculos.

```
OLEUIEDITLINKS m_el;
```

### <a name="remarks"></a>Comentarios

Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.

Para obtener más información, vea la estructura [OLEUIEDITLINKS](/windows/win32/api/oledlg/ns-oledlg-oleuieditlinksw) en el Windows SDK.

## <a name="see-also"></a>Vea también

[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)
