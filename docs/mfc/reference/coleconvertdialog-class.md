---
title: Clase COleConvertDialog
ms.date: 11/04/2016
f1_keywords:
- COleConvertDialog
- AFXODLGS/COleConvertDialog
- AFXODLGS/COleConvertDialog::COleConvertDialog
- AFXODLGS/COleConvertDialog::DoConvert
- AFXODLGS/COleConvertDialog::DoModal
- AFXODLGS/COleConvertDialog::GetClassID
- AFXODLGS/COleConvertDialog::GetDrawAspect
- AFXODLGS/COleConvertDialog::GetIconicMetafile
- AFXODLGS/COleConvertDialog::GetSelectionType
- AFXODLGS/COleConvertDialog::m_cv
helpviewer_keywords:
- COleConvertDialog [MFC], COleConvertDialog
- COleConvertDialog [MFC], DoConvert
- COleConvertDialog [MFC], DoModal
- COleConvertDialog [MFC], GetClassID
- COleConvertDialog [MFC], GetDrawAspect
- COleConvertDialog [MFC], GetIconicMetafile
- COleConvertDialog [MFC], GetSelectionType
- COleConvertDialog [MFC], m_cv
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
ms.openlocfilehash: ba57e756457fcffca806eeba7454ddf7bcf99d34
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504293"
---
# <a name="coleconvertdialog-class"></a>Clase COleConvertDialog

Para obtener más información, vea la estructura [OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) en el Windows SDK.

## <a name="syntax"></a>Sintaxis

```
class COleConvertDialog : public COleDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleConvertDialog::COleConvertDialog](#coleconvertdialog)|Construye un objeto `COleConvertDialog`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleConvertDialog::DoConvert](#doconvert)|Realiza la conversión especificada en el cuadro de diálogo.|
|[COleConvertDialog::DoModal](#domodal)|Muestra el cuadro de diálogo cambiar elemento OLE.|
|[COleConvertDialog::GetClassID](#getclassid)|Obtiene el CLSID asociado al elemento elegido.|
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|Especifica si se debe dibujar el elemento como un icono.|
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|Obtiene un identificador para el metarchivo asociado al formulario de iconos de este elemento.|
|[COleConvertDialog::GetSelectionType](#getselectiontype)|Obtiene el tipo de selección elegido.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleConvertDialog::m_cv](#m_cv)|Estructura que controla el comportamiento del cuadro de diálogo.|

## <a name="remarks"></a>Comentarios

> [!NOTE]
>  El código de contenedor generado por el Asistente para aplicaciones utiliza esta clase.

Para obtener más información acerca de los cuadros de diálogo específicos de OLE, vea los [cuadros de diálogo de artículo en OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleConvertDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxodlgs. h

##  <a name="coleconvertdialog"></a>  COleConvertDialog::COleConvertDialog

Construye solo un `COleConvertDialog` objeto.

```
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Apunta al elemento que se va a convertir o activar.

*dwFlags*<br/>
Marca de creación, que contiene cualquier número de los siguientes valores combinados mediante el operador OR bit a bit:

- CF_SELECTCONVERTTO especifica que el botón de radio convertir en se seleccionará inicialmente cuando se llame al cuadro de diálogo. Este es el valor predeterminado.

- CF_SELECTACTIVATEAS especifica que el botón de radio activar como se seleccionará inicialmente cuando se llame al cuadro de diálogo.

- CF_SETCONVERTDEFAULT especifica que la clase cuyo CLSID se especifica mediante el `clsidConvertDefault` miembro de la `m_cv` estructura se usará como la selección predeterminada en el cuadro de lista clase cuando se selecciona el botón de radio convertir en.

- CF_SETACTIVATEDEFAULT especifica que la clase cuyo CLSID se especifica mediante el `clsidActivateDefault` miembro de la `m_cv` estructura se usará como la selección predeterminada en el cuadro de lista clase cuando se selecciona el botón de radio activar como.

- CF_SHOWHELPBUTTON especifica que el botón ayuda se mostrará cuando se llame al cuadro de diálogo.

*pClassID*<br/>
Apunta al CLSID del elemento que se va a convertir o activar. Si es NULL, se utilizará el CLSID asociado a *pItem* .

*pParentWnd*<br/>
Apunta al objeto de ventana primario o propietario (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del cuadro de diálogo se establece en la ventana principal de la aplicación.

### <a name="remarks"></a>Comentarios

Para mostrar el cuadro de diálogo, llame a la función [DoModal](#domodal) .

Para obtener más información, consulte la [clave CLSID](/windows/win32/com/clsid-key-hklm) y la estructura [OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) .

##  <a name="doconvert"></a>  COleConvertDialog::DoConvert

Llame a esta función después de que se devuelva correctamente desde [DoModal](#domodal), bien para convertir o para activar un objeto de tipo [COleClientItem](../../mfc/reference/coleclientitem-class.md).

```
BOOL DoConvert(COleClientItem* pItem);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Apunta al elemento que se va a convertir o activar. No puede ser nulo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El elemento se convierte o se activa según la información seleccionada por el usuario en el cuadro de diálogo convertir.

##  <a name="domodal"></a>  COleConvertDialog::DoModal

Llame a esta función para mostrar el cuadro de diálogo convertir OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Estado de finalización del cuadro de diálogo. Uno de los siguientes valores:

- IDOK si el cuadro de diálogo se mostró correctamente.

- IDCANCEL si el usuario canceló el cuadro de diálogo.

- IDABORT si se produjo un error. Si se devuelve IDABORT, llame a la función miembro [COleDialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) para obtener más información sobre el tipo de error que se ha producido. Para obtener una lista de posibles errores, vea la función [OleUIConvert](/windows/win32/api/oledlg/nf-oledlg-oleuiconvertw) en el Windows SDK.

### <a name="remarks"></a>Comentarios

Si desea inicializar los distintos controles de cuadro de diálogo estableciendo los miembros de la estructura [m_cv](#m_cv) , debe hacerlo antes de llamar `DoModal`a, pero después de que se construya el objeto de cuadro de diálogo.

Si `DoModal` devuelve IDOK, puede llamar a otras funciones miembro para recuperar la configuración o la información que el usuario ha introducido en el cuadro de diálogo.

##  <a name="getclassid"></a>  COleConvertDialog::GetClassID

Llame a esta función para obtener el CLSID asociado al elemento seleccionado por el usuario en el cuadro de diálogo convertir.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Valor devuelto

CLSID asociado al elemento que se seleccionó en el cuadro de diálogo convertir.

### <a name="remarks"></a>Comentarios

Llame a esta función solo después de que [DoModal](#domodal) devuelva IDOK.

Para obtener más información, consulte la [clave CLSID](/windows/win32/com/clsid-key-hklm) en el Windows SDK.

##  <a name="getdrawaspect"></a>  COleConvertDialog::GetDrawAspect

Llame a esta función para determinar si el usuario ha elegido mostrar el elemento seleccionado como un icono.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Valor devuelto

Método necesario para representar el objeto.

- DVASPECT_CONTENT se devuelve si la casilla Mostrar como icono no estaba activada.

- DVASPECT_ICON se devuelve si la casilla Mostrar como icono estaba activada.

### <a name="remarks"></a>Comentarios

Llame a esta función solo después de que [DoModal](#domodal) devuelva IDOK.

Para obtener más información sobre cómo dibujar el aspecto, consulte la estructura de datos de [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

##  <a name="geticonicmetafile"></a>  COleConvertDialog::GetIconicMetafile

Llame a esta función para obtener un identificador para el metarchivo que contiene el aspecto de los iconos del elemento seleccionado.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del metarchivo que contiene el aspecto de los iconos del elemento seleccionado, si la casilla Mostrar como icono estaba activada cuando el cuadro de diálogo se descartó; para ello, elija Aceptar; de lo contrario, NULL.

##  <a name="getselectiontype"></a>  COleConvertDialog::GetSelectionType

Llame a esta función para determinar el tipo de conversión seleccionado en el cuadro de diálogo convertir.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Valor devuelto

Tipo de selección realizada.

### <a name="remarks"></a>Comentarios

Los valores de tipo devuelto se especifican mediante el `Selection` tipo de enumeración declarado en la `COleConvertDialog` clase.

```
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };
```

A continuación se muestran descripciones breves de estos valores:

- `COleConvertDialog::noConversion`Se devuelve si se cancela el cuadro de diálogo o el usuario no seleccionó ninguna conversión. Si `COleConvertDialog::DoModal` se devuelve IDOK, es posible que el usuario seleccionara un icono diferente del que se seleccionó anteriormente.

- `COleConvertDialog::convertItem`Se devuelve si el botón de radio convertir en está activado, el usuario seleccionó un elemento diferente al que `DoModal` convertir y devolvió IDOK.

- `COleConvertDialog::activateAs`Se devuelve si el botón de radio activar como estaba activado, el usuario seleccionó un elemento diferente para `DoModal` activar y devolvió IDOK.

##  <a name="m_cv"></a>  COleConvertDialog::m_cv

Estructura de tipo OLEUICONVERT que se usa para controlar el comportamiento del cuadro de diálogo convertir.

```
OLEUICONVERT m_cv;
```

### <a name="remarks"></a>Comentarios

Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.

Para obtener más información, vea la estructura [OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) en el Windows SDK.

## <a name="see-also"></a>Vea también

[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)
