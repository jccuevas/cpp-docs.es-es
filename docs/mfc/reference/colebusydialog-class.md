---
title: Clase COleBusyDialog
ms.date: 11/04/2016
f1_keywords:
- COleBusyDialog
- AFXODLGS/COleBusyDialog
- AFXODLGS/COleBusyDialog::COleBusyDialog
- AFXODLGS/COleBusyDialog::DoModal
- AFXODLGS/COleBusyDialog::GetSelectionType
- AFXODLGS/COleBusyDialog::m_bz
helpviewer_keywords:
- COleBusyDialog [MFC], COleBusyDialog
- COleBusyDialog [MFC], DoModal
- COleBusyDialog [MFC], GetSelectionType
- COleBusyDialog [MFC], m_bz
ms.assetid: c881a532-9672-4c41-b51b-5ce4a7246a6b
ms.openlocfilehash: aa3f0d85bcbf34d325125187b22b38c4da01fb43
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504406"
---
# <a name="colebusydialog-class"></a>Clase COleBusyDialog

Se utiliza en los cuadros de diálogo que indican que el servidor OLE no responde o el servidor está ocupado.

## <a name="syntax"></a>Sintaxis

```
class COleBusyDialog : public COleDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleBusyDialog::COleBusyDialog](#colebusydialog)|Construye un objeto `COleBusyDialog`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleBusyDialog::DoModal](#domodal)|Muestra el cuadro de diálogo servidor ocupado de OLE.|
|[COleBusyDialog::GetSelectionType](#getselectiontype)|Determina la elección realizada en el cuadro de diálogo.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleBusyDialog::m_bz](#m_bz)|Estructura de tipo OLEUIBUSY que controla el comportamiento del cuadro de diálogo.|

## <a name="remarks"></a>Comentarios

Cree un objeto de clase `COleBusyDialog` cuando desee llamar a estos cuadros de diálogo. Una vez `COleBusyDialog` construido un objeto, puede usar la estructura [m_bz](#m_bz) para inicializar los valores o los Estados de los controles en el cuadro de diálogo. La `m_bz` estructura es de tipo OLEUIBUSY. Para obtener más información sobre el uso de esta clase de cuadro de diálogo, vea la función miembro [DoModal](#domodal) .

> [!NOTE]
>  El código de contenedor generado por el Asistente para aplicaciones utiliza esta clase.

Para obtener más información, vea la estructura [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) en el Windows SDK.

Para obtener más información sobre los cuadros de diálogo específicos de OLE, vea los [cuadros de diálogo de los artículos en OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleBusyDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxodlgs. h

##  <a name="colebusydialog"></a>  COleBusyDialog::COleBusyDialog

Esta función solo crea un `COleBusyDialog` objeto.

```
explicit COleBusyDialog(
    HTASK htaskBusy,
    BOOL bNotResponding = FALSE,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*htaskBusy*<br/>
Identificador de la tarea de servidor que está ocupada.

*bNotResponding*<br/>
Si es TRUE, llame al cuadro de diálogo no responde en lugar de al cuadro de diálogo servidor ocupado. El texto del cuadro de diálogo no responde es ligeramente diferente del que aparece en el cuadro de diálogo servidor ocupado y el botón Cancelar está deshabilitado.

*dwFlags*<br/>
Marca de creación. Puede contener cero o más de los siguientes valores combinados con el operador OR bit a bit:

- BZ_DISABLECANCELBUTTON deshabilite el botón Cancelar al llamar al cuadro de diálogo.

- BZ_DISABLESWITCHTOBUTTON deshabilite el botón cambiar a al llamar al cuadro de diálogo.

- BZ_DISABLERETRYBUTTON deshabilite el botón Reintentar al llamar al cuadro de diálogo.

*pParentWnd*<br/>
Apunta al objeto de ventana primario o propietario (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.

### <a name="remarks"></a>Comentarios

Para mostrar el cuadro de diálogo, llame a [DoModal](#domodal).

Para obtener más información, vea la estructura [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) en el Windows SDK.

##  <a name="domodal"></a>  COleBusyDialog::DoModal

Llame a esta función para mostrar el cuadro de diálogo servidor ocupado de OLE o servidor que no responde.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Estado de finalización del cuadro de diálogo. Uno de los siguientes valores:

- IDOK si el cuadro de diálogo se mostró correctamente.

- IDCANCEL si el usuario canceló el cuadro de diálogo.

- IDABORT si se produjo un error. Si se devuelve IDABORT, llame a `COleDialog::GetLastError` la función miembro para obtener más información sobre el tipo de error que se ha producido. Para obtener una lista de posibles errores, vea la función [OleUIBusy](/windows/win32/api/oledlg/nf-oledlg-oleuibusyw) en el Windows SDK.

### <a name="remarks"></a>Comentarios

Si desea inicializar los distintos controles de cuadro de diálogo estableciendo los miembros de la estructura [m_bz](#m_bz) , debe hacerlo antes de llamar `DoModal`a, pero después de que se construya el objeto de cuadro de diálogo.

Si `DoModal` devuelve IDOK, puede llamar a otras funciones miembro para recuperar la configuración o la información que el usuario ha introducido en el cuadro de diálogo.

##  <a name="getselectiontype"></a>  COleBusyDialog::GetSelectionType

Llame a esta función para obtener el tipo de selección elegido por el usuario en el cuadro de diálogo servidor ocupado.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Valor devuelto

Tipo de selección realizada.

### <a name="remarks"></a>Comentarios

Los valores de tipo devuelto se especifican mediante el `Selection` tipo de enumeración declarado en la `COleBusyDialog` clase.

```
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```

A continuación se muestran descripciones breves de estos valores:

- `COleBusyDialog::switchTo`Se presionó el botón cambiar a.

- `COleBusyDialog::retry`Se presionó el botón Reintentar.

- `COleBusyDialog::callUnblocked`La llamada para activar el servidor está ahora desbloqueada.

##  <a name="m_bz"></a>  COleBusyDialog::m_bz

Estructura de tipo OLEUIBUSY que se usa para controlar el comportamiento del cuadro de diálogo servidor ocupado.

```
OLEUIBUSY m_bz;
```

### <a name="remarks"></a>Comentarios

Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.

Para obtener más información, vea la estructura [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) en el Windows SDK.

## <a name="see-also"></a>Vea también

[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)
