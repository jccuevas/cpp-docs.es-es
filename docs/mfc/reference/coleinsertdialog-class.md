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
ms.openlocfilehash: 750243ddf6494ecc4a6a28c0cb47b05ca7089c33
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260691"
---
# <a name="coleinsertdialog-class"></a>COleInsertDialog (clase)

Se utiliza para el cuadro de diálogo Insertar objeto OLE.

## <a name="syntax"></a>Sintaxis

```
class COleInsertDialog : public COleDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|Construye un objeto `COleInsertDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COleInsertDialog::CreateItem](#createitem)|Crea el elemento seleccionado en el cuadro de diálogo.|
|[COleInsertDialog::DoModal](#domodal)|Muestra el cuadro de diálogo Insertar objeto OLE.|
|[COleInsertDialog::GetClassID](#getclassid)|Obtiene el CLSID asociado al elemento seleccionado.|
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|Indica si se debe dibujar el elemento como un icono.|
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|Obtiene un identificador del metarchivo asociado al formulario icónico de este elemento.|
|[COleInsertDialog::GetPathName](#getpathname)|Obtiene la ruta de acceso completa al archivo seleccionado en el cuadro de diálogo.|
|[COleInsertDialog::GetSelectionType](#getselectiontype)|Obtiene el tipo de objeto seleccionado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[COleInsertDialog::m_io](#m_io)|Una estructura de tipo OLEUIINSERTOBJECT que controla el comportamiento del cuadro de diálogo.|

## <a name="remarks"></a>Comentarios

Crear un objeto de clase `COleInsertDialog` cuando desee llamar a este cuadro de diálogo. Después de un `COleInsertDialog` se ha construido el objeto, puede usar el [m_io](#m_io) estructura para inicializar los valores o los Estados de los controles en el cuadro de diálogo. El `m_io` estructura es de tipo OLEUIINSERTOBJECT. Para obtener más información sobre el uso de esta clase de cuadro de diálogo, vea el [DoModal](#domodal) función miembro.

> [!NOTE]
>  Código de contenedor generados por el Asistente para la aplicación usa esta clase.

Para obtener más información, consulte el [OLEUIINSERTOBJECT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiinsertobjecta) estructura en el SDK de Windows.

Para obtener más información sobre los cuadros de diálogo OLE específicos, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).

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

##  <a name="coleinsertdialog"></a>  COleInsertDialog::COleInsertDialog

Esta función solo construye un `COleInsertDialog` objeto.

```
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Indicador de creación que contiene cualquier número de los siguientes valores que va a combinarse con el operador OR bit a bit:

- IOF_SHOWHELP especifica que el botón de ayuda se mostrará cuando se llama el cuadro de diálogo.

- IOF_SELECTCREATENEW especifica que el botón de radio crear nuevo estará había seleccionado inicialmente cuando se llama el cuadro de diálogo. Este es el valor predeterminado y no se puede usar con IOF_SELECTCREATEFROMFILE.

- IOF_SELECTCREATEFROMFILE especifica que el botón de radio crear desde archivo estará había seleccionado inicialmente cuando se llama el cuadro de diálogo. No se puede usar con IOF_SELECTCREATENEW.

- IOF_CHECKLINK especifica que la casilla de verificación vínculo estará había activada inicialmente cuando se llama el cuadro de diálogo.

- IOF_DISABLELINK especifica que el vínculo de la casilla de verificación se deshabilitarán cuando se llama el cuadro de diálogo.

- IOF_CHECKDISPLAYASICON especifica que se comprobará la casilla de verificación Mostrar como icono inicialmente, se mostrará el icono actual y se habilitará el botón Cambiar icono cuando se llama el cuadro de diálogo.

- IOF_VERIFYSERVERSEXIST especifica que el cuadro de diálogo debería validar las clases que agrega al cuadro de lista al garantizar que los servidores especificados en la base de datos de registro existen antes de que aparezca el cuadro de diálogo. Establecer este indicador puede afectar significativamente al rendimiento.

*pParentWnd*<br/>
Señala al objeto de ventana principal o propietaria (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.

### <a name="remarks"></a>Comentarios

Para mostrar el cuadro de diálogo, llame a la [DoModal](#domodal) función.

##  <a name="createitem"></a>  COleInsertDialog::CreateItem

Llame a esta función para crear un objeto de tipo [COleClientItem](../../mfc/reference/coleclientitem-class.md) solo si [DoModal](#domodal) devuelve IDOK.

```
BOOL CreateItem(COleClientItem* pItem);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Apunta al elemento que se va a crearse.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se creó el elemento; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Debe asignar el `COleClientItem` objeto antes de que se puede llamar a esta función.

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

`COleInsertDialog::DocObjectsOnly` Inserta solo DocObjects.

`COleInsertDialog::ControlsOnly` inserta sólo los controles ActiveX.

Cero inserta DocObject ni un control ActiveX. Este valor da como resultado la misma implementación que el primer prototipo mencionados anteriormente.

### <a name="return-value"></a>Valor devuelto

Estado de finalización para el cuadro de diálogo. Uno de los siguientes valores:

- IDOK si el cuadro de diálogo se mostró correctamente.

- IDCANCEL si el usuario canceló el cuadro de diálogo.

- IDABORT si se produjo un error. Si se devuelve IDABORT, llame a la [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea el [OleUIInsertObject](/windows/desktop/api/oledlg/nf-oledlg-oleuiinsertobjecta) función en el SDK de Windows.

### <a name="remarks"></a>Comentarios

Si desea inicializar los distintos controles de cuadro de diálogo mediante el establecimiento de los miembros de la [m_io](#m_io) estructura, debe hacerlo antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.

Si `DoModal` devuelve IDOK, puede llamar a otra funciones miembro para recuperar la configuración o la entrada de información en el cuadro de diálogo por el usuario.

##  <a name="getclassid"></a>  COleInsertDialog::GetClassID

Llame a esta función para obtener el CLSID asociado con el elemento únicamente si seleccionada [DoModal](#domodal) devuelve IDOK y el tipo de selección es `COleInsertDialog::createNewItem`.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el CLSID asociado con el elemento seleccionado.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [clave CLSID](/windows/desktop/com/clsid-key-hklm) en el SDK de Windows.

##  <a name="getdrawaspect"></a>  COleInsertDialog::GetDrawAspect

Llame a esta función para determinar si el usuario optó por mostrar el elemento seleccionado como un icono.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Valor devuelto

El método necesario para representar el objeto.

- DVASPECT_CONTENT devuelto si no se ha activado la casilla de verificación Mostrar como icono.

- DVASPECT_ICON devuelto si se ha activado la casilla de verificación Mostrar como icono.

### <a name="remarks"></a>Comentarios

Llamar a este únicamente si función [DoModal](#domodal) devuelve IDOK.

Para obtener más información sobre los aspectos de dibujo, consulte [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) estructura de datos en el SDK de Windows.

##  <a name="geticonicmetafile"></a>  COleInsertDialog::GetIconicMetafile

Llame a esta función para obtener un identificador del metarchivo que contiene el aspecto del icono del elemento seleccionado.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Valor devuelto

El identificador del metarchivo que contiene el aspecto del icono del elemento seleccionado, si la casilla de verificación Mostrar como icono comprobar cuándo se descarta el cuadro de diálogo eligiendo **Aceptar**; de lo contrario, NULL.

##  <a name="getpathname"></a>  COleInsertDialog::GetPathName

Llame a esta función para obtener la ruta de acceso completa del archivo seleccionado solo si [DoModal](#domodal) devuelve IDOK y el tipo de selección no es `COleInsertDialog::createNewItem`.

```
CString GetPathName() const;
```

### <a name="return-value"></a>Valor devuelto

La ruta de acceso completa al archivo seleccionado en el cuadro de diálogo. Si el tipo de selección es `createNewItem`, esta función devuelve un sentido `CString` en modo de lanzamiento o produce una aserción en modo de depuración.

##  <a name="getselectiontype"></a>  COleInsertDialog::GetSelectionType

Llame a esta función para obtener el tipo de selección que elige cuándo se descarta el cuadro de diálogo Insertar objeto eligiendo **Aceptar**.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Valor devuelto

Tipo de selección realizada.

### <a name="remarks"></a>Comentarios

Se especifican los valores de tipo de valor devuelto por la `Selection` tipo de enumeración declarado en el `COleInsertDialog` clase.

```
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };
```

Siguen breves descripciones de los valores siguientes:

- `COleInsertDialog::createNewItem` Se ha seleccionado el botón de opción Crear nuevo.

- `COleInsertDialog::insertFromFile` Se ha seleccionado el botón de opción de crear desde archivo y no se comprobó la casilla de verificación de vínculo.

- `COleInsertDialog::linkToFile` Se ha seleccionado el botón de opción de crear desde archivo y se ha activado la casilla de verificación de vínculo.

##  <a name="m_io"></a>  COleInsertDialog::m_io

Estructura del tipo OLEUIINSERTOBJECT usado para controlar el comportamiento del cuadro de diálogo Insertar objeto.

```
OLEUIINSERTOBJECT m_io;
```

### <a name="remarks"></a>Comentarios

Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.

Para obtener más información, consulte el [OLEUIINSERTOBJECT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiinsertobjecta) estructura en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Ejemplo MFC OCLIENT](../../visual-cpp-samples.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)
