---
title: COleChangeSourceDialog (clase)
ms.date: 11/04/2016
f1_keywords:
- COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::DoModal
- AFXODLGS/COleChangeSourceDialog::GetDisplayName
- AFXODLGS/COleChangeSourceDialog::GetFileName
- AFXODLGS/COleChangeSourceDialog::GetFromPrefix
- AFXODLGS/COleChangeSourceDialog::GetItemName
- AFXODLGS/COleChangeSourceDialog::GetToPrefix
- AFXODLGS/COleChangeSourceDialog::IsValidSource
- AFXODLGS/COleChangeSourceDialog::m_cs
helpviewer_keywords:
- COleChangeSourceDialog [MFC], COleChangeSourceDialog
- COleChangeSourceDialog [MFC], DoModal
- COleChangeSourceDialog [MFC], GetDisplayName
- COleChangeSourceDialog [MFC], GetFileName
- COleChangeSourceDialog [MFC], GetFromPrefix
- COleChangeSourceDialog [MFC], GetItemName
- COleChangeSourceDialog [MFC], GetToPrefix
- COleChangeSourceDialog [MFC], IsValidSource
- COleChangeSourceDialog [MFC], m_cs
ms.assetid: d0e08be7-21ef-45e1-97af-fe27d99e3bac
ms.openlocfilehash: 78da0a495de6ea951deab984550756a2d6f3e2bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321869"
---
# <a name="colechangesourcedialog-class"></a>COleChangeSourceDialog (clase)

Se utiliza en el cuadro de diálogo Cambiar origen de OLE.

## <a name="syntax"></a>Sintaxis

```
class COleChangeSourceDialog : public COleDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleChangeSourceDialog::COleChangeSourceDialog](#colechangesourcedialog)|Construye un objeto `COleChangeSourceDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleChangeSourceDialog::DoModal](#domodal)|Muestra el cuadro de diálogo Origen de cambio OLE.|
|[COleChangeSourceDialog::GetDisplayName](#getdisplayname)|Obtiene el nombre para mostrar de origen completo.|
|[COleChangeSourceDialog::GetFileName](#getfilename)|Obtiene el nombre de archivo del nombre de origen.|
|[COleChangeSourceDialog::GetFromPrefix](#getfromprefix)|Obtiene el prefijo del origen anterior.|
|[COleChangeSourceDialog::GetItemName](#getitemname)|Obtiene el nombre del elemento del nombre de origen.|
|[COleChangeSourceDialog::GetToPrefix](#gettoprefix)|Obtiene el prefijo de la nueva fuente|
|[COleChangeSourceDialog::IsValidSource](#isvalidsource)|Indica si el origen es válido.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleChangeSourceDialog::m_cs](#m_cs)|Estructura que controla el comportamiento del cuadro de diálogo.|

## <a name="remarks"></a>Observaciones

Cree un objeto `COleChangeSourceDialog` de clase cuando desee llamar a este cuadro de diálogo. Una `COleChangeSourceDialog` vez construido un objeto, puede utilizar la [estructura m_cs](#m_cs) para inicializar los valores o estados de los controles en el cuadro de diálogo. La `m_cs` estructura es de tipo [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew). Para obtener más información sobre el uso de esta clase de cuadro de diálogo, vea el [DoModal](#domodal) función miembro.

Para obtener más información, vea la estructura [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) en Windows SDK.

Para obtener más información acerca de los cuadros de diálogo específicos de OLE, vea el artículo [Cuadros](../../mfc/dialog-boxes-in-ole.md)de diálogo en OLE .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeSourceDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxodlgs.h

## <a name="colechangesourcedialogcolechangesourcedialog"></a><a name="colechangesourcedialog"></a>COleChangeSourceDialog::COleChangeSourceDialog

Esta función `COleChangeSourceDialog` construye un objeto.

```
explicit COleChangeSourceDialog(
    COleClientItem* pItem,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Puntero al [vinculado COleClientItem](../../mfc/reference/coleclientitem-class.md) cuyo origen se va a actualizar.

*pParentWnd*<br/>
Apunta al objeto de ventana principal `CWnd`o propietario (de tipo ) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del cuadro de diálogo se establecerá en la ventana principal de la aplicación.

### <a name="remarks"></a>Observaciones

Para mostrar el cuadro de diálogo, llame a la [Función DoModal.](#domodal)

Para obtener más información, vea la estructura [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) y la función [OleUIChangeSource](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew) en Windows SDK.

## <a name="colechangesourcedialogdomodal"></a><a name="domodal"></a>COleChangeSourceDialog::DoModal

Llame a esta función para mostrar el cuadro de diálogo Origen de cambio OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Estado de finalización del cuadro de diálogo. Uno de los valores siguientes:

- IDOK si el cuadro de diálogo se ha mostrado correctamente.

- IDCANCEL si el usuario canceló el cuadro de diálogo.

- IDABORT si se ha producido un error. Si se devuelve IDABORT, llame a la [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea la función [OleUIChangeSource](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew) en Windows SDK.

### <a name="remarks"></a>Observaciones

Si desea inicializar los distintos controles de cuadro de diálogo estableciendo `DoModal`miembros de la [estructura m_cs,](#m_cs) debe hacerlo antes de llamar a , pero después de que se construye el objeto de cuadro de diálogo.

Si `DoModal` devuelve IDOK, puede llamar a funciones miembro para recuperar la configuración introducida por el usuario o la información del cuadro de diálogo. La siguiente lista nombra funciones de consulta típicas:

- [GetFileName](#getfilename)

- [GetDisplayName](#getdisplayname)

- [GetItemName](#getitemname)

## <a name="colechangesourcedialoggetdisplayname"></a><a name="getdisplayname"></a>COleChangeSourceDialog::GetDisplayName

Llame a esta función para recuperar el nombre para mostrar completo para el elemento de cliente vinculado.

```
CString GetDisplayName();
```

### <a name="return-value"></a>Valor devuelto

El nombre para mostrar de origen completo (moniker) para el [COleClientItem](../../mfc/reference/coleclientitem-class.md) especificado en el constructor.

## <a name="colechangesourcedialoggetfilename"></a><a name="getfilename"></a>COleChangeSourceDialog::GetFileName

Llame a esta función para recuperar la parte del moniker de archivo del nombre para mostrar para el elemento de cliente vinculado.

```
CString GetFileName();
```

### <a name="return-value"></a>Valor devuelto

La parte del moniker de archivo del nombre para mostrar del origen para el [COleClientItem](../../mfc/reference/coleclientitem-class.md) especificado en el constructor.

### <a name="remarks"></a>Observaciones

El moniker de archivo junto con el moniker de elemento da el nombre para mostrar completo.

## <a name="colechangesourcedialoggetfromprefix"></a><a name="getfromprefix"></a>COleChangeSourceDialog::GetFromPrefix

Llame a esta función para obtener la cadena de prefijo anterior para el origen.

```
CString GetFromPrefix();
```

### <a name="return-value"></a>Valor devuelto

La cadena de prefijo anterior del origen.

### <a name="remarks"></a>Observaciones

Llame a esta función solo después de [DoModal](#domodal) devuelve IDOK.

Este valor procede `lpszFrom` directamente del miembro de la [estructura OLEUICHANGESOURCE.](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)

Para obtener más información, vea la estructura [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) en Windows SDK.

## <a name="colechangesourcedialoggetitemname"></a><a name="getitemname"></a>COleChangeSourceDialog::GetItemName

Llame a esta función para recuperar la parte del moniker del elemento del nombre para mostrar del elemento de cliente vinculado.

```
CString GetItemName();
```

### <a name="return-value"></a>Valor devuelto

La parte del moniker del elemento del nombre para mostrar del origen para el [COleClientItem](../../mfc/reference/coleclientitem-class.md) especificado en el constructor.

### <a name="remarks"></a>Observaciones

El moniker de archivo junto con el moniker de elemento da el nombre para mostrar completo.

## <a name="colechangesourcedialoggettoprefix"></a><a name="gettoprefix"></a>COleChangeSourceDialog::GetToPrefix

Llame a esta función para obtener la nueva cadena de prefijo para el origen.

```
CString GetToPrefix();
```

### <a name="return-value"></a>Valor devuelto

La nueva cadena de prefijo del origen.

### <a name="remarks"></a>Observaciones

Llame a esta función solo después de [DoModal](#domodal) devuelve IDOK.

Este valor procede `lpszTo` directamente del miembro de la [estructura OLEUICHANGESOURCE.](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew)

Para obtener más información, vea la estructura [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) en Windows SDK.

## <a name="colechangesourcedialogm_cs"></a><a name="m_cs"></a>COleChangeSourceDialog::m_cs

Este miembro de datos es una estructura de tipo [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew).

```
OLEUICHANGESOURCE m_cs;
```

### <a name="remarks"></a>Observaciones

`OLEUICHANGESOURCE`se utiliza para controlar el comportamiento del cuadro de diálogo Origen de cambio OLE. Los miembros de esta estructura se pueden modificar directamente.

Para obtener más información, vea la estructura [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) en Windows SDK.

## <a name="colechangesourcedialogisvalidsource"></a><a name="isvalidsource"></a>COleChangeSourceDialog::IsValidSource

Llame a esta función para determinar si el nuevo origen es válido.

```
BOOL IsValidSource();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el nuevo origen es válido, en caso contrario 0.

### <a name="remarks"></a>Observaciones

Llame a esta función solo después de [DoModal](#domodal) devuelve IDOK.

Para obtener más información, vea la estructura [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) en Windows SDK.

## <a name="see-also"></a>Consulte también

[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)
