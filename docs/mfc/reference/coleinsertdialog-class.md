---
title: COleInsertDialog (clase)
ms.date: 11/04/2016
f1_keywords:
- COleInsertDialog
- AFXODLGS/COleInsertDialog
- AFXODLGS/COleInsertDialog::COleInsertDialog
- AFXODLGS/COleInsertDialog::CreateItem
- AFXODLGS/COleInsertDialog::DoModal
- AFXODLGS/COleInsertDialog::GetClassID
- AFXODLGS/COleInsertDialog::GetDrawAspect
- AFXODLGS/COleInsertDialog::GetIconicMetafile
- AFXODLGS/COleInsertDialog::GetPathName
- AFXODLGS/COleInsertDialog::GetSelectionType
- AFXODLGS/COleInsertDialog::m_io
helpviewer_keywords:
- COleInsertDialog [MFC], COleInsertDialog
- COleInsertDialog [MFC], CreateItem
- COleInsertDialog [MFC], DoModal
- COleInsertDialog [MFC], GetClassID
- COleInsertDialog [MFC], GetDrawAspect
- COleInsertDialog [MFC], GetIconicMetafile
- COleInsertDialog [MFC], GetPathName
- COleInsertDialog [MFC], GetSelectionType
- COleInsertDialog [MFC], m_io
ms.assetid: a9ec610b-abde-431e-bd01-c40159a66dbb
ms.openlocfilehash: b5de4ff5daa80e1d8727444a4cfd275597e18c08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374968"
---
# <a name="coleinsertdialog-class"></a>COleInsertDialog (clase)

Se utiliza para el cuadro de diálogo Insertar objeto OLE.

## <a name="syntax"></a>Sintaxis

```
class COleInsertDialog : public COleDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|Construye un objeto `COleInsertDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleInsertDialog::CreateItem](#createitem)|Crea el elemento seleccionado en el cuadro de diálogo.|
|[COleInsertDialog::DoModal](#domodal)|Muestra el cuadro de diálogo Insertar objeto OLE.|
|[COleInsertDialog::GetClassID](#getclassid)|Obtiene el CLSID asociado al elemento elegido.|
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|Indica si se debe dibujar el elemento como un icono.|
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|Obtiene un identificador del metarchivo asociado con la forma icónica de este elemento.|
|[COleInsertDialog::GetPathName](#getpathname)|Obtiene la ruta de acceso completa al archivo elegido en el cuadro de diálogo.|
|[COleInsertDialog::GetSelectionType](#getselectiontype)|Obtiene el tipo de objeto seleccionado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleInsertDialog::m_io](#m_io)|Estructura de tipo OLEUIINSERTOBJECT que controla el comportamiento del cuadro de diálogo.|

## <a name="remarks"></a>Observaciones

Cree un objeto `COleInsertDialog` de clase cuando desee llamar a este cuadro de diálogo. Una `COleInsertDialog` vez construido un objeto, puede utilizar la [estructura m_io](#m_io) para inicializar los valores o estados de los controles en el cuadro de diálogo. La `m_io` estructura es de tipo OLEUIINSERTOBJECT. Para obtener más información sobre el uso de esta clase de cuadro de diálogo, vea el [DoModal](#domodal) función miembro.

> [!NOTE]
> El código de contenedor generado por el Asistente para aplicaciones utiliza esta clase.

Para obtener más información, vea la estructura [OLEUIINSERTOBJECT](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw) en el Windows SDK.

Para obtener más información acerca de los cuadros de diálogo específicos de OLE, vea el artículo [Cuadros](../../mfc/dialog-boxes-in-ole.md)de diálogo en OLE .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleInsertDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxodlgs.h

## <a name="coleinsertdialogcoleinsertdialog"></a><a name="coleinsertdialog"></a>COleInsertDialog::COleInsertDialog

Esta función construye `COleInsertDialog` solo un objeto.

```
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Marca de creación que contiene cualquier número de los siguientes valores que se combinarán mediante el operador OR bit a bit:

- IOF_SHOWHELP Especifica que el botón Ayuda se mostrará cuando se llame al cuadro de diálogo.

- IOF_SELECTCREATENEW Especifica que el botón de opción Crear nuevo se seleccionará inicialmente cuando se llame al cuadro de diálogo. Este es el valor predeterminado y no se puede utilizar con IOF_SELECTCREATEFROMFILE.

- IOF_SELECTCREATEFROMFILE Especifica que el botón de opción Crear a partir de archivo se seleccionará inicialmente cuando se llame al cuadro de diálogo. No se puede utilizar con IOF_SELECTCREATENEW.

- IOF_CHECKLINK Especifica que la casilla de verificación Vínculo se comprobará inicialmente cuando se llame al cuadro de diálogo.

- IOF_DISABLELINK Especifica que la casilla vínculo se deshabilitará cuando se llame al cuadro de diálogo.

- IOF_CHECKDISPLAYASICON Especifica que la casilla de verificación Mostrar como icono se activará inicialmente, se mostrará el icono actual y se habilitará el botón Cambiar icono cuando se llame al cuadro de diálogo.

- IOF_VERIFYSERVERSEXIST Especifica que el cuadro de diálogo debe validar las clases que agrega al cuadro de lista asegurándose de que los servidores especificados en la base de datos de registro existen antes de que se muestre el cuadro de diálogo. Establecer esta marca puede perjudicar significativamente el rendimiento.

*pParentWnd*<br/>
Apunta al objeto de ventana principal `CWnd`o propietario (de tipo ) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.

### <a name="remarks"></a>Observaciones

Para mostrar el cuadro de diálogo, llame a la [Función DoModal.](#domodal)

## <a name="coleinsertdialogcreateitem"></a><a name="createitem"></a>COleInsertDialog::CreateItem

Llame a esta función para crear un objeto de tipo [COleClientItem](../../mfc/reference/coleclientitem-class.md) solo si [DoModal](#domodal) devuelve IDOK.

```
BOOL CreateItem(COleClientItem* pItem);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Apunta al elemento que se va a crear.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se creó el elemento; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Debe asignar `COleClientItem` el objeto antes de poder llamar a esta función.

## <a name="coleinsertdialogdomodal"></a><a name="domodal"></a>COleInsertDialog::DoModal

Llame a esta función para mostrar el cuadro de diálogo Insertar objeto OLE.

```
virtual INT_PTR
    DoModal();

INT_PTR
    DoModal(DWORD  dwFlags);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Uno de los valores siguientes:

`COleInsertDialog::DocObjectsOnly`inserta sólo DocObjects.

`COleInsertDialog::ControlsOnly`inserta solo controles ActiveX.

Zero no inserta ni un DocObject ni un control ActiveX. Este valor da como resultado la misma implementación que el primer prototipo mencionado anteriormente.

### <a name="return-value"></a>Valor devuelto

Estado de finalización del cuadro de diálogo. Uno de los valores siguientes:

- IDOK si el cuadro de diálogo se ha mostrado correctamente.

- IDCANCEL si el usuario canceló el cuadro de diálogo.

- IDABORT si se ha producido un error. Si se devuelve IDABORT, llame a la [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea la función [OleUIInsertObject](/windows/win32/api/oledlg/nf-oledlg-oleuiinsertobjectw) en el Windows SDK.

### <a name="remarks"></a>Observaciones

Si desea inicializar los distintos controles de cuadro de diálogo estableciendo `DoModal`miembros de la [estructura m_io,](#m_io) debe hacerlo antes de llamar a , pero después de que se construye el objeto de cuadro de diálogo.

Si `DoModal` devuelve IDOK, puede llamar a otras funciones miembro para recuperar la configuración o la información introducida en el cuadro de diálogo por el usuario.

## <a name="coleinsertdialoggetclassid"></a><a name="getclassid"></a>COleInsertDialog::GetClassID

Llame a esta función para obtener el CLSID asociado al elemento seleccionado `COleInsertDialog::createNewItem`solo si [DoModal](#domodal) devuelve IDOK y el tipo de selección es .

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el CLSID asociado al elemento seleccionado.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [Clave CLSID](/windows/win32/com/clsid-key-hklm) en el Windows SDK.

## <a name="coleinsertdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COleInsertDialog::GetDrawAspect

Llame a esta función para determinar si el usuario eligió mostrar el elemento seleccionado como un icono.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Valor devuelto

El método necesario para representar el objeto.

- DVASPECT_CONTENT Se devuelve si la casilla mostrar como icono no está activada.

- DVASPECT_ICON Se devuelve si la casilla mostrar como icono está activada.

### <a name="remarks"></a>Observaciones

Llame a esta función solo si [DoModal](#domodal) devuelve IDOK.

Para obtener más información sobre el aspecto del dibujo, consulte Estructura de datos [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

## <a name="coleinsertdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleInsertDialog::GetIconicMetafile

Llame a esta función para obtener un identificador del metarchivo que contiene el aspecto icónico del elemento seleccionado.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Valor devuelto

El identificador del metarchivo que contiene el aspecto icónico del elemento seleccionado, si la casilla de verificación Mostrar como icono estaba activada cuando se descartó el cuadro de diálogo seleccionando **Aceptar**; NULL.

## <a name="coleinsertdialoggetpathname"></a><a name="getpathname"></a>COleInsertDialog::GetPathName

Llame a esta función para obtener la ruta de acceso completa del `COleInsertDialog::createNewItem`archivo seleccionado solo si [DoModal](#domodal) devuelve IDOK y el tipo de selección no es .

```
CString GetPathName() const;
```

### <a name="return-value"></a>Valor devuelto

La ruta de acceso completa al archivo seleccionado en el cuadro de diálogo. Si el tipo `createNewItem`de selección es `CString` , esta función devuelve un modo de liberación sin sentido o provoca una aserción en modo de depuración.

## <a name="coleinsertdialoggetselectiontype"></a><a name="getselectiontype"></a>COleInsertDialog::GetSelectionType

Llame a esta función para obtener el tipo de selección elegido cuando se descartó el cuadro de diálogo Insertar objeto seleccionando **Aceptar**.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Valor devuelto

Tipo de selección realizada.

### <a name="remarks"></a>Observaciones

Los valores de tipo devuelto `Selection` se especifican `COleInsertDialog` mediante el tipo de enumeración declarado en la clase.

```
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };
```

A continuación se describen breves de estos valores:

- `COleInsertDialog::createNewItem`Se ha seleccionado el botón de opción Crear nuevo.

- `COleInsertDialog::insertFromFile`Se ha seleccionado el botón de opción Crear desde archivo y la casilla De verificación Vínculo no está activada.

- `COleInsertDialog::linkToFile`Se ha seleccionado el botón de opción Crear desde archivo y se ha activado la casilla de verificación Vínculo.

## <a name="coleinsertdialogm_io"></a><a name="m_io"></a>COleInsertDialog::m_io

Estructura de tipo OLEUIINSERTOBJECT utilizada para controlar el comportamiento del cuadro de diálogo Insertar objeto.

```
OLEUIINSERTOBJECT m_io;
```

### <a name="remarks"></a>Observaciones

Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.

Para obtener más información, vea la estructura [OLEUIINSERTOBJECT](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)
