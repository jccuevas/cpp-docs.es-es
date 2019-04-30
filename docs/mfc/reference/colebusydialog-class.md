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
ms.openlocfilehash: 08e482e6900e96f1d02c34efddc7635bb8e0120e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400713"
---
# <a name="colebusydialog-class"></a>COleBusyDialog (clase)

Se utiliza en los cuadros de diálogo que indican que el servidor OLE no responde o el servidor está ocupado.

## <a name="syntax"></a>Sintaxis

```
class COleBusyDialog : public COleDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[COleBusyDialog::COleBusyDialog](#colebusydialog)|Construye un objeto `COleBusyDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COleBusyDialog::DoModal](#domodal)|Muestra el cuadro de diálogo OLE servidor ocupado.|
|[COleBusyDialog::GetSelectionType](#getselectiontype)|Determina la elección realizada en el cuadro de diálogo.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[COleBusyDialog::m_bz](#m_bz)|Estructura de tipo OLEUIBUSY que controla el comportamiento del cuadro de diálogo.|

## <a name="remarks"></a>Comentarios

Crear un objeto de clase `COleBusyDialog` cuando desee llamar a estos cuadros de diálogo. Después de un `COleBusyDialog` se ha construido el objeto, puede usar el [m_bz](#m_bz) estructura para inicializar los valores o los Estados de los controles en el cuadro de diálogo. El `m_bz` estructura es de tipo OLEUIBUSY. Para obtener más información sobre el uso de esta clase de cuadro de diálogo, vea el [DoModal](#domodal) función miembro.

> [!NOTE]
>  Código de contenedor generados por el Asistente para la aplicación usa esta clase.

Para obtener más información, consulte el [OLEUIBUSY](/windows/desktop/api/oledlg/ns-oledlg-tagoleuibusya) estructura en el SDK de Windows.

Para obtener más información sobre los cuadros de diálogo OLE específicos, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).

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

##  <a name="colebusydialog"></a>  COleBusyDialog::COleBusyDialog

Esta función solo construye un `COleBusyDialog` objeto.

```
explicit COleBusyDialog(
    HTASK htaskBusy,
    BOOL bNotResponding = FALSE,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*htaskBusy*<br/>
Identificador de la tarea de servidor está ocupada.

*bNotResponding*<br/>
Si es TRUE, llame el cuadro de diálogo no responde en lugar del cuadro de diálogo servidor ocupado. En el cuadro de diálogo no responde con la redacción es ligeramente diferente en el cuadro de diálogo servidor ocupado con la redacción y se deshabilita el botón Cancelar.

*dwFlags*<br/>
Indicador de creación. Puede contener cero o más de los siguientes valores que se combinan con el operador OR bit a bit:

- BZ_DISABLECANCELBUTTON deshabilitar el botón de cancelación al llamar el cuadro de diálogo.

- BZ_DISABLESWITCHTOBUTTON deshabilitar el botón Cambiar a cuando se llama el cuadro de diálogo.

- BZ_DISABLERETRYBUTTON deshabilita el botón de reintento cuando se llama el cuadro de diálogo.

*pParentWnd*<br/>
Señala al objeto de ventana principal o propietaria (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.

### <a name="remarks"></a>Comentarios

Para mostrar el cuadro de diálogo, llame a [DoModal](#domodal).

Para obtener más información, consulte el [OLEUIBUSY](/windows/desktop/api/oledlg/ns-oledlg-tagoleuibusya) estructura en el SDK de Windows.

##  <a name="domodal"></a>  COleBusyDialog::DoModal

Llame a esta función para mostrar el cuadro de diálogo OLE servidor ocupado o no responde el servidor.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Estado de finalización para el cuadro de diálogo. Uno de los siguientes valores:

- IDOK si el cuadro de diálogo se mostró correctamente.

- IDCANCEL si el usuario canceló el cuadro de diálogo.

- IDABORT si se produjo un error. Si se devuelve IDABORT, llame a la `COleDialog::GetLastError` la función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea el [OleUIBusy](/windows/desktop/api/oledlg/nf-oledlg-oleuibusya) función en el SDK de Windows.

### <a name="remarks"></a>Comentarios

Si desea inicializar los distintos controles de cuadro de diálogo mediante el establecimiento de los miembros de la [m_bz](#m_bz) estructura, debe hacerlo antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.

Si `DoModal` devuelve IDOK, se puede llamar a otro miembro de funciones para recuperar la configuración o la información que se ha especificado por el usuario en el cuadro de diálogo.

##  <a name="getselectiontype"></a>  COleBusyDialog::GetSelectionType

Llame a esta función para obtener el tipo de selección elegido por el usuario en el cuadro de diálogo servidor ocupado.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Valor devuelto

Tipo de selección realizada.

### <a name="remarks"></a>Comentarios

Se especifican los valores de tipo de valor devuelto por la `Selection` tipo de enumeración declarado en el `COleBusyDialog` clase.

```
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```

Siguen breves descripciones de los valores siguientes:

- `COleBusyDialog::switchTo` Se presionó el botón Cambiar a.

- `COleBusyDialog::retry` Se presionó el botón de reintento.

- `COleBusyDialog::callUnblocked` Llamada a activar el servidor ya está desbloqueado.

##  <a name="m_bz"></a>  COleBusyDialog::m_bz

Estructura del tipo OLEUIBUSY usado para controlar el comportamiento del cuadro de diálogo servidor ocupado.

```
OLEUIBUSY m_bz;
```

### <a name="remarks"></a>Comentarios

Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.

Para obtener más información, consulte el [OLEUIBUSY](/windows/desktop/api/oledlg/ns-oledlg-tagoleuibusya) estructura en el SDK de Windows.

## <a name="see-also"></a>Vea también

[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)
