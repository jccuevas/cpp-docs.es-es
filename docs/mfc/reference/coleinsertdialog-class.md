---
title: Clase COleInsertDialog
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
ms.openlocfilehash: a884f946b60be0567f39477f434db8efe041e393
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503930"
---
# <a name="coleinsertdialog-class"></a>Clase COleInsertDialog

Se utiliza para el cuadro de diálogo Insertar objeto OLE.

## <a name="syntax"></a>Sintaxis

```
class COleInsertDialog : public COleDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|Construye un objeto `COleInsertDialog`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleInsertDialog::CreateItem](#createitem)|Crea el elemento seleccionado en el cuadro de diálogo.|
|[COleInsertDialog::DoModal](#domodal)|Muestra el cuadro de diálogo Insertar objeto OLE.|
|[COleInsertDialog::GetClassID](#getclassid)|Obtiene el CLSID asociado al elemento elegido.|
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|Indica si se debe dibujar el elemento como un icono.|
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|Obtiene un identificador para el metarchivo asociado al formulario de iconos de este elemento.|
|[COleInsertDialog::GetPathName](#getpathname)|Obtiene la ruta de acceso completa al archivo seleccionado en el cuadro de diálogo.|
|[COleInsertDialog::GetSelectionType](#getselectiontype)|Obtiene el tipo de objeto seleccionado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleInsertDialog::m_io](#m_io)|Estructura de tipo OLEUIINSERTOBJECT que controla el comportamiento del cuadro de diálogo.|

## <a name="remarks"></a>Comentarios

Cree un objeto de clase `COleInsertDialog` cuando desee llamar a este cuadro de diálogo. Una vez `COleInsertDialog` construido un objeto, puede usar la estructura [m_io](#m_io) para inicializar los valores o los Estados de los controles en el cuadro de diálogo. La `m_io` estructura es de tipo OLEUIINSERTOBJECT. Para obtener más información sobre el uso de esta clase de cuadro de diálogo, vea la función miembro [DoModal](#domodal) .

> [!NOTE]
>  El código de contenedor generado por el Asistente para aplicaciones utiliza esta clase.

Para obtener más información, vea la estructura [OLEUIINSERTOBJECT](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw) en el Windows SDK.

Para obtener más información sobre los cuadros de diálogo específicos de OLE, vea los [cuadros de diálogo de artículo en OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleInsertDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxodlgs. h

##  <a name="coleinsertdialog"></a>  COleInsertDialog::COleInsertDialog

Esta función solo crea un `COleInsertDialog` objeto.

```
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Marca de creación que contiene cualquier número de los siguientes valores que se van a combinar mediante el operador OR bit a bit:

- IOF_SHOWHELP especifica que el botón ayuda se mostrará cuando se llame al cuadro de diálogo.

- IOF_SELECTCREATENEW especifica que el botón de radio crear nuevo se seleccionará inicialmente cuando se llame al cuadro de diálogo. Este es el valor predeterminado y no se puede usar con IOF_SELECTCREATEFROMFILE.

- IOF_SELECTCREATEFROMFILE especifica que el botón de radio crear desde archivo se seleccionará inicialmente cuando se llame al cuadro de diálogo. No se puede usar con IOF_SELECTCREATENEW.

- IOF_CHECKLINK especifica que la casilla de vínculo se activará inicialmente cuando se llame al cuadro de diálogo.

- IOF_DISABLELINK especifica que la casilla de vínculo se deshabilitará cuando se llame al cuadro de diálogo.

- IOF_CHECKDISPLAYASICON especifica que la casilla Mostrar como icono se activará inicialmente, se mostrará el icono actual y el botón Cambiar icono se habilitará cuando se llame al cuadro de diálogo.

- IOF_VERIFYSERVERSEXIST especifica que el cuadro de diálogo debe validar las clases que se agregan al cuadro de lista asegurándose de que los servidores especificados en la base de datos de registro existen antes de que se muestre el cuadro de diálogo. La configuración de esta marca puede afectar significativamente al rendimiento.

*pParentWnd*<br/>
Apunta al objeto de ventana primario o propietario (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.

### <a name="remarks"></a>Comentarios

Para mostrar el cuadro de diálogo, llame a la función [DoModal](#domodal) .

##  <a name="createitem"></a>  COleInsertDialog::CreateItem

Llame a esta función para crear un objeto de tipo [COleClientItem](../../mfc/reference/coleclientitem-class.md) solo si [DoModal](#domodal) devuelve IDOK.

```
BOOL CreateItem(COleClientItem* pItem);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Apunta al elemento que se va a crear.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha creado el elemento; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Debe asignar el objeto `COleClientItem` antes de poder llamar a esta función.

##  <a name="domodal"></a>  COleInsertDialog::DoModal

Llame a esta función para mostrar el cuadro de diálogo Insertar objeto OLE.

```
virtual INT_PTR
    DoModal();

INT_PTR
    DoModal(DWORD  dwFlags);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Uno de los siguientes valores:

`COleInsertDialog::DocObjectsOnly`inserta solo DocObjects.

`COleInsertDialog::ControlsOnly`inserta solo controles ActiveX.

Cero no inserta ni un DocObject ni un control ActiveX. Este valor da como resultado la misma implementación que el primer prototipo indicado anteriormente.

### <a name="return-value"></a>Valor devuelto

Estado de finalización del cuadro de diálogo. Uno de los siguientes valores:

- IDOK si el cuadro de diálogo se mostró correctamente.

- IDCANCEL si el usuario canceló el cuadro de diálogo.

- IDABORT si se produjo un error. Si se devuelve IDABORT, llame a la función miembro [COleDialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) para obtener más información sobre el tipo de error que se ha producido. Para obtener una lista de posibles errores, vea la función [OleUIInsertObject](/windows/win32/api/oledlg/nf-oledlg-oleuiinsertobjectw) en el Windows SDK.

### <a name="remarks"></a>Comentarios

Si desea inicializar los distintos controles de cuadro de diálogo estableciendo los miembros de la estructura [m_io](#m_io) , debe hacerlo antes de llamar `DoModal`a, pero después de que se construya el objeto de cuadro de diálogo.

Si `DoModal` devuelve IDOK, puede llamar a otras funciones miembro para recuperar la entrada de información o la configuración en el cuadro de diálogo del usuario.

##  <a name="getclassid"></a>  COleInsertDialog::GetClassID

Llame a esta función para obtener el CLSID asociado al elemento seleccionado solo si [DoModal](#domodal) devuelve IDOK y el tipo de selección es `COleInsertDialog::createNewItem`.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el CLSID asociado al elemento seleccionado.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte la [clave CLSID](/windows/win32/com/clsid-key-hklm) en el Windows SDK.

##  <a name="getdrawaspect"></a>  COleInsertDialog::GetDrawAspect

Llame a esta función para determinar si el usuario ha elegido mostrar el elemento seleccionado como un icono.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Valor devuelto

Método necesario para representar el objeto.

- DVASPECT_CONTENT se devuelve si la casilla Mostrar como icono no estaba activada.

- DVASPECT_ICON se devuelve si la casilla Mostrar como icono estaba activada.

### <a name="remarks"></a>Comentarios

Llame a esta función solo si [DoModal](#domodal) devuelve IDOK.

Para obtener más información sobre el dibujo de aspectos, consulte la estructura de datos de [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

##  <a name="geticonicmetafile"></a>  COleInsertDialog::GetIconicMetafile

Llame a esta función para obtener un identificador para el metarchivo que contiene el aspecto de los iconos del elemento seleccionado.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del metarchivo que contiene el aspecto de los iconos del elemento seleccionado, si la casilla Mostrar como icono estaba activada cuando el cuadro de diálogo se descartó; para ello, elija **Aceptar**; de lo contrario, NULL.

##  <a name="getpathname"></a>  COleInsertDialog::GetPathName

Llame a esta función para obtener la ruta de acceso completa del archivo seleccionado solo si [DoModal](#domodal) devuelve IDOK y el tipo de selección `COleInsertDialog::createNewItem`no.

```
CString GetPathName() const;
```

### <a name="return-value"></a>Valor devuelto

Ruta de acceso completa al archivo seleccionado en el cuadro de diálogo. Si el tipo de selección `createNewItem`es, esta función devuelve un `CString` sentido en modo de versión o produce una aserción en modo de depuración.

##  <a name="getselectiontype"></a>  COleInsertDialog::GetSelectionType

Llame a esta función para obtener el tipo de selección elegido cuando se descartó el cuadro de diálogo Insertar objeto; para ello, elija **Aceptar**.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Valor devuelto

Tipo de selección realizada.

### <a name="remarks"></a>Comentarios

Los valores de tipo devuelto se especifican mediante el `Selection` tipo de enumeración declarado en la `COleInsertDialog` clase.

```
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };
```

A continuación se muestran descripciones breves de estos valores:

- `COleInsertDialog::createNewItem`Se ha seleccionado el botón de radio crear nuevo.

- `COleInsertDialog::insertFromFile`Se ha seleccionado el botón de radio crear desde archivo y la casilla de verificación vínculo no está activada.

- `COleInsertDialog::linkToFile`Se seleccionó el botón de radio crear desde archivo y se activó la casilla vínculo.

##  <a name="m_io"></a>  COleInsertDialog::m_io

Estructura de tipo OLEUIINSERTOBJECT que se usa para controlar el comportamiento del cuadro de diálogo Insertar objeto.

```
OLEUIINSERTOBJECT m_io;
```

### <a name="remarks"></a>Comentarios

Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.

Para obtener más información, vea la estructura [OLEUIINSERTOBJECT](/windows/win32/api/oledlg/ns-oledlg-oleuiinsertobjectw) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Ejemplo OCLIENT de MFC](../../overview/visual-cpp-samples.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)
