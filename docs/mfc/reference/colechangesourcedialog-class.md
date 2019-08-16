---
title: Clase COleChangeSourceDialog
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
ms.openlocfilehash: 239d7eed89796f414a7665b203ca50fafec51277
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504384"
---
# <a name="colechangesourcedialog-class"></a>Clase COleChangeSourceDialog

Se utiliza en el cuadro de diálogo Cambiar origen de OLE.

## <a name="syntax"></a>Sintaxis

```
class COleChangeSourceDialog : public COleDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleChangeSourceDialog::COleChangeSourceDialog](#colechangesourcedialog)|Construye un objeto `COleChangeSourceDialog`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleChangeSourceDialog::DoModal](#domodal)|Muestra el cuadro de diálogo cambiar origen de OLE.|
|[COleChangeSourceDialog::GetDisplayName](#getdisplayname)|Obtiene el nombre para mostrar del código fuente completo.|
|[COleChangeSourceDialog::GetFileName](#getfilename)|Obtiene el nombre de archivo del nombre de origen.|
|[COleChangeSourceDialog::GetFromPrefix](#getfromprefix)|Obtiene el prefijo del origen anterior.|
|[COleChangeSourceDialog::GetItemName](#getitemname)|Obtiene el nombre del elemento del nombre de origen.|
|[COleChangeSourceDialog::GetToPrefix](#gettoprefix)|Obtiene el prefijo del nuevo origen.|
|[COleChangeSourceDialog::IsValidSource](#isvalidsource)|Indica si el origen es válido.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleChangeSourceDialog::m_cs](#m_cs)|Estructura que controla el comportamiento del cuadro de diálogo.|

## <a name="remarks"></a>Comentarios

Cree un objeto de clase `COleChangeSourceDialog` cuando desee llamar a este cuadro de diálogo. Una vez `COleChangeSourceDialog` construido un objeto, puede usar la estructura [m_cs](#m_cs) para inicializar los valores o los Estados de los controles en el cuadro de diálogo. La `m_cs` estructura es de tipo [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew). Para obtener más información sobre el uso de esta clase de cuadro de diálogo, vea la función miembro [DoModal](#domodal) .

Para obtener más información, vea la estructura [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) en Windows SDK.

Para obtener más información acerca de los cuadros de diálogo específicos de OLE, vea los [cuadros de diálogo de artículo en OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeSourceDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxodlgs. h

##  <a name="colechangesourcedialog"></a>  COleChangeSourceDialog::COleChangeSourceDialog

Esta función crea un `COleChangeSourceDialog` objeto.

```
explicit COleChangeSourceDialog(
    COleClientItem* pItem,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Puntero al [COleClientItem](../../mfc/reference/coleclientitem-class.md) vinculado cuyo origen se va a actualizar.

*pParentWnd*<br/>
Apunta al objeto de ventana primario o propietario (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del cuadro de diálogo se establecerá en la ventana principal de la aplicación.

### <a name="remarks"></a>Comentarios

Para mostrar el cuadro de diálogo, llame a la función [DoModal](#domodal) .

Para obtener más información, vea la estructura [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) y la función [OLEUICHANGESOURCE](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew) en Windows SDK.

##  <a name="domodal"></a>  COleChangeSourceDialog::DoModal

Llame a esta función para mostrar el cuadro de diálogo cambiar origen de OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Estado de finalización del cuadro de diálogo. Uno de los siguientes valores:

- IDOK si el cuadro de diálogo se mostró correctamente.

- IDCANCEL si el usuario canceló el cuadro de diálogo.

- IDABORT si se produjo un error. Si se devuelve IDABORT, llame a la función miembro [COleDialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) para obtener más información sobre el tipo de error que se ha producido. Para obtener una lista de posibles errores, vea la función [OleUIChangeSource](/windows/win32/api/oledlg/nf-oledlg-oleuichangesourcew) en Windows SDK.

### <a name="remarks"></a>Comentarios

Si desea inicializar los distintos controles de cuadro de diálogo estableciendo los miembros de la estructura [m_cs](#m_cs) , debe hacerlo antes de llamar `DoModal`a, pero después de que se construya el objeto de cuadro de diálogo.

Si `DoModal` devuelve IDOK, puede llamar a funciones miembro para recuperar la información o los valores especificados por el usuario del cuadro de diálogo. En la lista siguiente se muestran las funciones de consulta típicas:

- [GetFileName](#getfilename)

- [GetDisplayName](#getdisplayname)

- [GetItemName](#getitemname)

##  <a name="getdisplayname"></a>  COleChangeSourceDialog::GetDisplayName

Llame a esta función para recuperar el nombre para mostrar completo del elemento de cliente vinculado.

```
CString GetDisplayName();
```

### <a name="return-value"></a>Valor devuelto

Nombre para mostrar de origen completo (moniker) para el [COleClientItem](../../mfc/reference/coleclientitem-class.md) especificado en el constructor.

##  <a name="getfilename"></a>  COleChangeSourceDialog::GetFileName

Llame a esta función para recuperar la parte del moniker de archivo del nombre para mostrar del elemento de cliente vinculado.

```
CString GetFileName();
```

### <a name="return-value"></a>Valor devuelto

Parte del moniker de archivo del nombre para mostrar de origen para el [COleClientItem](../../mfc/reference/coleclientitem-class.md) especificado en el constructor.

### <a name="remarks"></a>Comentarios

El moniker de archivo junto con el moniker de elemento proporciona el nombre para mostrar completo.

##  <a name="getfromprefix"></a>  COleChangeSourceDialog::GetFromPrefix

Llame a esta función para obtener la cadena de prefijo anterior para el origen.

```
CString GetFromPrefix();
```

### <a name="return-value"></a>Valor devuelto

Cadena de prefijo anterior del origen.

### <a name="remarks"></a>Comentarios

Llame a esta función solo después de que [DoModal](#domodal) devuelva IDOK.

Este valor procede directamente del `lpszFrom` miembro de la estructura [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) .

Para obtener más información, vea la estructura [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) en Windows SDK.

##  <a name="getitemname"></a>  COleChangeSourceDialog::GetItemName

Llame a esta función para recuperar la parte del moniker del elemento del nombre para mostrar del elemento de cliente vinculado.

```
CString GetItemName();
```

### <a name="return-value"></a>Valor devuelto

Parte del moniker del elemento del nombre para mostrar de origen para el [COleClientItem](../../mfc/reference/coleclientitem-class.md) especificado en el constructor.

### <a name="remarks"></a>Comentarios

El moniker de archivo junto con el moniker de elemento proporciona el nombre para mostrar completo.

##  <a name="gettoprefix"></a>  COleChangeSourceDialog::GetToPrefix

Llame a esta función para obtener la nueva cadena de prefijo para el origen.

```
CString GetToPrefix();
```

### <a name="return-value"></a>Valor devuelto

La nueva cadena de prefijo del origen.

### <a name="remarks"></a>Comentarios

Llame a esta función solo después de que [DoModal](#domodal) devuelva IDOK.

Este valor procede directamente del `lpszTo` miembro de la estructura [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) .

Para obtener más información, vea la estructura [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) en Windows SDK.

##  <a name="m_cs"></a>  COleChangeSourceDialog::m_cs

Este miembro de datos es una estructura de tipo [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew).

```
OLEUICHANGESOURCE m_cs;
```

### <a name="remarks"></a>Comentarios

`OLEUICHANGESOURCE`se utiliza para controlar el comportamiento del cuadro de diálogo cambiar origen de OLE. Los miembros de esta estructura se pueden modificar directamente.

Para obtener más información, vea la estructura [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) en Windows SDK.

##  <a name="isvalidsource"></a>  COleChangeSourceDialog::IsValidSource

Llame a esta función para determinar si el nuevo origen es válido.

```
BOOL IsValidSource();
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si el nuevo origen es válido; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Llame a esta función solo después de que [DoModal](#domodal) devuelva IDOK.

Para obtener más información, vea la estructura [OLEUICHANGESOURCE](/windows/win32/api/oledlg/ns-oledlg-oleuichangesourcew) en Windows SDK.

## <a name="see-also"></a>Vea también

[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)
