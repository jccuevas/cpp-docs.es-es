---
title: COleChangeIconDialog (clase)
ms.date: 11/04/2016
f1_keywords:
- COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::DoChangeIcon
- AFXODLGS/COleChangeIconDialog::DoModal
- AFXODLGS/COleChangeIconDialog::GetIconicMetafile
- AFXODLGS/COleChangeIconDialog::m_ci
helpviewer_keywords:
- COleChangeIconDialog [MFC], COleChangeIconDialog
- COleChangeIconDialog [MFC], DoChangeIcon
- COleChangeIconDialog [MFC], DoModal
- COleChangeIconDialog [MFC], GetIconicMetafile
- COleChangeIconDialog [MFC], m_ci
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
ms.openlocfilehash: 6cdc0ed6bfa4765817de8b7628f339db5e7e5bf5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369633"
---
# <a name="colechangeicondialog-class"></a>COleChangeIconDialog (clase)

Se utiliza en el cuadro de diálogo Cambiar icono de OLE.

## <a name="syntax"></a>Sintaxis

```
class COleChangeIconDialog : public COleDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleChangeIconDialog::COleChangeIconDialog](#colechangeicondialog)|Construye un objeto `COleChangeIconDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleChangeIconDialog::DoChangeIcon](#dochangeicon)|Realiza el cambio especificado en el cuadro de diálogo.|
|[COleChangeIconDialog::DoModal](#domodal)|Muestra el cuadro de diálogo Icono de cambio ole 2.|
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|Obtiene un identificador del metarchivo asociado con la forma icónica de este elemento.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleChangeIconDialog::m_ci](#m_ci)|Estructura que controla el comportamiento del cuadro de diálogo.|

## <a name="remarks"></a>Observaciones

Cree un objeto `COleChangeIconDialog` de clase cuando desee llamar a este cuadro de diálogo. Una `COleChangeIconDialog` vez construido un objeto, puede utilizar la [estructura m_ci](#m_ci) para inicializar los valores o estados de los controles en el cuadro de diálogo. La `m_ci` estructura es de tipo OLEUICHANGEICON. Para obtener más información sobre el uso de esta clase de cuadro de diálogo, vea el [DoModal](#domodal) función miembro.

Para obtener más información, vea la estructura [OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) en el Windows SDK.

Para obtener más información acerca de los cuadros de diálogo específicos de OLE, vea el artículo [Cuadros](../../mfc/dialog-boxes-in-ole.md)de diálogo en OLE .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxodlgs.h

## <a name="colechangeicondialogcolechangeicondialog"></a><a name="colechangeicondialog"></a>COleChangeIconDialog::COleChangeIconDialog

Esta función construye `COleChangeIconDialog` solo un objeto.

```
explicit COleChangeIconDialog(
    COleClientItem* pItem,
    DWORD dwFlags = CIF_SELECTCURRENT,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Apunta al elemento que se va a convertir.

*dwFlags*<br/>
Marca de creación, que contiene cualquier número de los siguientes valores combinados mediante el operador bit a bit:

- CIF_SELECTCURRENT Especifica que el botón de opción Actual se seleccionará inicialmente cuando se llame al cuadro de diálogo. Este es el valor predeterminado.

- CIF_SELECTDEFAULT Especifica que el botón de opción Predeterminado se seleccionará inicialmente cuando se llame al cuadro de diálogo.

- CIF_SELECTFROMFILE Especifica que el botón de opción Desde archivo se seleccionará inicialmente cuando se llame al cuadro de diálogo.

- CIF_SHOWHELP Especifica que el botón Ayuda se mostrará cuando se llame al cuadro de diálogo.

- CIF_USEICONEXE Especifica que el icono se debe extraer del `szIconExe` ejecutable especificado en el campo de [m_ci](#m_ci) en lugar de recuperarse del tipo. Esto es útil para incrustar o vincular a archivos que no son OLE.

*pParentWnd*<br/>
Apunta al objeto de ventana principal `CWnd`o propietario (de tipo ) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del cuadro de diálogo se establecerá en la ventana principal de la aplicación.

### <a name="remarks"></a>Observaciones

Para mostrar el cuadro de diálogo, llame a la [Función DoModal.](#domodal)

Para obtener más información, vea la estructura [OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) en el Windows SDK.

## <a name="colechangeicondialogdochangeicon"></a><a name="dochangeicon"></a>COleChangeIconDialog::DoChangeIcon

Llame a esta función para cambiar el icono que representa el elemento al seleccionado en el cuadro de diálogo después de [DoModal](#domodal) devuelve IDOK.

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Señala al elemento cuyo icono está cambiando.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el cambio se realiza correctamente; de lo contrario 0.

## <a name="colechangeicondialogdomodal"></a><a name="domodal"></a>COleChangeIconDialog::DoModal

Llame a esta función para mostrar el icono de cambio OLE cuadro de diálogo.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Estado de finalización del cuadro de diálogo. Uno de los valores siguientes:

- IDOK si el cuadro de diálogo se ha mostrado correctamente.

- IDCANCEL si el usuario canceló el cuadro de diálogo.

- IDABORT si se ha producido un error. Si se devuelve IDABORT, llame a la `COleDialog::GetLastError` función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea la función [OleUIChangeIcon](/windows/win32/api/oledlg/nf-oledlg-oleuichangeiconw) en el Windows SDK.

### <a name="remarks"></a>Observaciones

Si desea inicializar los distintos controles de cuadro de diálogo estableciendo `DoModal`miembros de la [estructura m_ci,](#m_ci) debe hacerlo antes de llamar a , pero después de que se construye el objeto de cuadro de diálogo.

Si `DoModal` devuelve IDOK, puede llamar a otras funciones miembro para recuperar la configuración o información que el usuario ha introducido en el cuadro de diálogo.

## <a name="colechangeicondialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleChangeIconDialog::GetIconicMetafile

Llame a esta función para obtener un identificador del metarchivo que contiene el aspecto icónico del elemento seleccionado.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Valor devuelto

El identificador del metarchivo que contiene el aspecto icónico del nuevo icono, si el cuadro de diálogo se descartó seleccionando **Aceptar**; de lo contrario, el icono tal como era antes de que se mostrara el cuadro de diálogo.

## <a name="colechangeicondialogm_ci"></a><a name="m_ci"></a>COleChangeIconDialog::m_ci

Estructura de tipo OLEUICHANGEICON utilizada para controlar el comportamiento del cuadro de diálogo Cambiar icono.

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>Observaciones

Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.

Para obtener más información, vea la estructura [OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)
