---
title: COleBusyDialog (clase)
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
ms.openlocfilehash: 5be42463c08cacd83de84900fb4d98771774e897
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364241"
---
# <a name="colebusydialog-class"></a>COleBusyDialog (clase)

Se utiliza en los cuadros de diálogo que indican que el servidor OLE no responde o el servidor está ocupado.

## <a name="syntax"></a>Sintaxis

```
class COleBusyDialog : public COleDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleBusyDialog::COleBusyDialog](#colebusydialog)|Construye un objeto `COleBusyDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleBusyDialog::DoModal](#domodal)|Muestra el cuadro de diálogo OCASO Server ocupado.|
|[COleBusyDialog::GetSelectionType](#getselectiontype)|Determina la elección realizada en el cuadro de diálogo.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleBusyDialog::m_bz](#m_bz)|Estructura de tipo OLEUIBUSY que controla el comportamiento del cuadro de diálogo.|

## <a name="remarks"></a>Observaciones

Cree un objeto `COleBusyDialog` de clase cuando desee llamar a estos cuadros de diálogo. Una `COleBusyDialog` vez construido un objeto, puede utilizar la estructura [m_bz](#m_bz) para inicializar los valores o estados de los controles en el cuadro de diálogo. La `m_bz` estructura es de tipo OLEUIBUSY. Para obtener más información sobre el uso de esta clase de cuadro de diálogo, vea el [DoModal](#domodal) función miembro.

> [!NOTE]
> El código de contenedor generado por el Asistente para aplicaciones utiliza esta clase.

Para obtener más información, vea la estructura [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) en el Windows SDK.

Para obtener más información sobre los cuadros de diálogo específicos de OLE, vea el artículo [Cuadros](../../mfc/dialog-boxes-in-ole.md)de diálogo en OLE .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleBusyDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxodlgs.h

## <a name="colebusydialogcolebusydialog"></a><a name="colebusydialog"></a>COleBusyDialog::COleBusyDialog

Esta función solo `COleBusyDialog` construye un objeto.

```
explicit COleBusyDialog(
    HTASK htaskBusy,
    BOOL bNotResponding = FALSE,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*htaskBusy*<br/>
Controle la tarea del servidor que está ocupada.

*bNotResponding*<br/>
Si es TRUE, llame al cuadro de diálogo No responde en lugar del cuadro de diálogo Servidor ocupado. El texto del cuadro de diálogo No responde es ligeramente diferente del texto del cuadro de diálogo Ocupada del servidor y el botón Cancelar está deshabilitado.

*dwFlags*<br/>
Bandera de creación. Puede contener cero o más de los siguientes valores combinados con el operador OR bit a bit:

- BZ_DISABLECANCELBUTTON Deshabilitar el botón Cancelar al llamar al cuadro de diálogo.

- BZ_DISABLESWITCHTOBUTTON Deshabilitar el botón Cambiar a al llamar al cuadro de diálogo.

- BZ_DISABLERETRYBUTTON Deshabilitar el botón Reintentar al llamar al cuadro de diálogo.

*pParentWnd*<br/>
Apunta al objeto de ventana principal `CWnd`o propietario (de tipo ) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.

### <a name="remarks"></a>Observaciones

Para mostrar el cuadro de diálogo, llame a [DoModal](#domodal).

Para obtener más información, vea la estructura [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) en el Windows SDK.

## <a name="colebusydialogdomodal"></a><a name="domodal"></a>COleBusyDialog::DoModal

Llame a esta función para mostrar el cuadro de diálogo Servidor OLE ocupado o Servidor que no responde.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Estado de finalización del cuadro de diálogo. Uno de los valores siguientes:

- IDOK si el cuadro de diálogo se ha mostrado correctamente.

- IDCANCEL si el usuario canceló el cuadro de diálogo.

- IDABORT si se ha producido un error. Si se devuelve IDABORT, llame a la `COleDialog::GetLastError` función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea la función [OleUIBusy](/windows/win32/api/oledlg/nf-oledlg-oleuibusyw) en el Windows SDK.

### <a name="remarks"></a>Observaciones

Si desea inicializar los distintos controles de cuadro de diálogo estableciendo `DoModal`miembros de la [estructura m_bz,](#m_bz) debe hacerlo antes de llamar a , pero después de que se construye el objeto de cuadro de diálogo.

Si `DoModal` devuelve IDOK, puede llamar a otras funciones miembro para recuperar la configuración o información que el usuario ha introducido en el cuadro de diálogo.

## <a name="colebusydialoggetselectiontype"></a><a name="getselectiontype"></a>COleBusyDialog::GetSelectionType

Llame a esta función para obtener el tipo de selección elegido por el usuario en el cuadro de diálogo Ocupada del servidor.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Valor devuelto

Tipo de selección realizada.

### <a name="remarks"></a>Observaciones

Los valores de tipo devuelto `Selection` se especifican `COleBusyDialog` mediante el tipo de enumeración declarado en la clase.

```
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```

A continuación se describen breves de estos valores:

- `COleBusyDialog::switchTo`Se ha pulsado el botón Cambiar a.

- `COleBusyDialog::retry`Se ha pulsado el botón Reintentar.

- `COleBusyDialog::callUnblocked`La llamada para activar el servidor ahora está desbloqueada.

## <a name="colebusydialogm_bz"></a><a name="m_bz"></a>COleBusyDialog::m_bz

Estructura de tipo OLEUIBUSY utilizada para controlar el comportamiento del cuadro de diálogo Servidor ocupado.

```
OLEUIBUSY m_bz;
```

### <a name="remarks"></a>Observaciones

Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.

Para obtener más información, vea la estructura [OLEUIBUSY](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)
