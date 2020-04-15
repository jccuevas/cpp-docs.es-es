---
title: COleConvertDialog Clase
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
ms.openlocfilehash: 6d6690b8d06df29ce9fcd323eb8724009ee3cca9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366166"
---
# <a name="coleconvertdialog-class"></a>COleConvertDialog Clase

Para obtener más información, vea la estructura [OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) en el Windows SDK.

## <a name="syntax"></a>Sintaxis

```
class COleConvertDialog : public COleDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleConvertDialog::COleConvertDialog](#coleconvertdialog)|Construye un objeto `COleConvertDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleConvertDialog::DoConvert](#doconvert)|Realiza la conversión especificada en el cuadro de diálogo.|
|[COleConvertDialog::DoModal](#domodal)|Muestra el cuadro de diálogo Elemento de cambio OLE.|
|[COleConvertDialog::GetClassID](#getclassid)|Obtiene el CLSID asociado al elemento elegido.|
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|Especifica si se va a dibujar el elemento como un icono.|
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|Obtiene un identificador del metarchivo asociado con la forma icónica de este elemento.|
|[COleConvertDialog::GetSelectionType](#getselectiontype)|Obtiene el tipo de selección elegido.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleConvertDialog::m_cv](#m_cv)|Estructura que controla el comportamiento del cuadro de diálogo.|

## <a name="remarks"></a>Observaciones

> [!NOTE]
> El código de contenedor generado por el Asistente para aplicaciones utiliza esta clase.

Para obtener más información acerca de los cuadros de diálogo específicos de OLE, vea el artículo [Cuadros](../../mfc/dialog-boxes-in-ole.md)de diálogo en OLE .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleConvertDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxodlgs.h

## <a name="coleconvertdialogcoleconvertdialog"></a><a name="coleconvertdialog"></a>COleConvertDialog::COleConvertDialog

Construye solo `COleConvertDialog` un objeto.

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
Marca de creación, que contiene cualquier número de los siguientes valores combinados mediante el operador bit a bit:

- CF_SELECTCONVERTTO Especifica que el botón de opción Convertir en se seleccionará inicialmente cuando se llame al cuadro de diálogo. Este es el valor predeterminado.

- CF_SELECTACTIVATEAS Especifica que el botón de opción Activar como se seleccionará inicialmente cuando se llame al cuadro de diálogo.

- CF_SETCONVERTDEFAULT Especifica que la clase cuyo CLSID `clsidConvertDefault` se `m_cv` especifica mediante el miembro de la estructura se utilizará como selección predeterminada en el cuadro de lista de clases cuando se selecciona el botón de opción Convertir a.

- CF_SETACTIVATEDEFAULT Especifica que la clase cuyo CLSID `clsidActivateDefault` se `m_cv` especifica mediante el miembro de la estructura se utilizará como selección predeterminada en el cuadro de lista de clases cuando se selecciona el botón de opción Activar como.

- CF_SHOWHELPBUTTON Especifica que el botón Ayuda se mostrará cuando se llame al cuadro de diálogo.

*pClassID*<br/>
Señala al CLSID del elemento que se va a convertir o activar. Si NULL, se usará el CLSID asociado a *pItem.*

*pParentWnd*<br/>
Apunta al objeto de ventana principal `CWnd`o propietario (de tipo ) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del cuadro de diálogo se establece en la ventana principal de la aplicación.

### <a name="remarks"></a>Observaciones

Para mostrar el cuadro de diálogo, llame a la [Función DoModal.](#domodal)

Para obtener más información, vea [clave CLSID](/windows/win32/com/clsid-key-hklm) y la estructura [OLEUICONVERT.](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw)

## <a name="coleconvertdialogdoconvert"></a><a name="doconvert"></a>COleConvertDialog::DoConvert

Llame a esta función, después de devolver correctamente desde [DoModal](#domodal), para convertir o activar un objeto de tipo [COleClientItem](../../mfc/reference/coleclientitem-class.md).

```
BOOL DoConvert(COleClientItem* pItem);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Apunta al elemento que se va a convertir o activar. No puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El elemento se convierte o activa según la información seleccionada por el usuario en el cuadro de diálogo Convertir.

## <a name="coleconvertdialogdomodal"></a><a name="domodal"></a>COleConvertDialog::DoModal

Llame a esta función para mostrar el cuadro de diálogo Convertir OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Estado de finalización del cuadro de diálogo. Uno de los valores siguientes:

- IDOK si el cuadro de diálogo se ha mostrado correctamente.

- IDCANCEL si el usuario canceló el cuadro de diálogo.

- IDABORT si se ha producido un error. Si se devuelve IDABORT, llame a la [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea la función [OleUIConvert](/windows/win32/api/oledlg/nf-oledlg-oleuiconvertw) en el Windows SDK.

### <a name="remarks"></a>Observaciones

Si desea inicializar los distintos controles de cuadro de diálogo estableciendo `DoModal`miembros de la [estructura m_cv,](#m_cv) debe hacerlo antes de llamar a , pero después de que se construye el objeto de cuadro de diálogo.

Si `DoModal` devuelve IDOK, puede llamar a otras funciones miembro para recuperar la configuración o información que el usuario ha introducido en el cuadro de diálogo.

## <a name="coleconvertdialoggetclassid"></a><a name="getclassid"></a>COleConvertDialog::GetClassID

Llame a esta función para obtener el CLSID asociado con el elemento seleccionado por el usuario en el cuadro de diálogo Convertir.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Valor devuelto

El CLSID asociado al elemento seleccionado en el cuadro de diálogo Convertir.

### <a name="remarks"></a>Observaciones

Llame a esta función solo después de [DoModal](#domodal) devuelve IDOK.

Para obtener más información, consulte [Clave CLSID](/windows/win32/com/clsid-key-hklm) en el Windows SDK.

## <a name="coleconvertdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COleConvertDialog::GetDrawAspect

Llame a esta función para determinar si el usuario eligió mostrar el elemento seleccionado como un icono.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Valor devuelto

El método necesario para representar el objeto.

- DVASPECT_CONTENT Se devuelve si la casilla mostrar como icono no está activada.

- DVASPECT_ICON Se devuelve si la casilla mostrar como icono está activada.

### <a name="remarks"></a>Observaciones

Llame a esta función solo después de [DoModal](#domodal) devuelve IDOK.

Para obtener más información sobre el aspecto del dibujo, consulte la estructura de datos [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

## <a name="coleconvertdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleConvertDialog::GetIconicMetafile

Llame a esta función para obtener un identificador del metarchivo que contiene el aspecto icónico del elemento seleccionado.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Valor devuelto

El identificador del metarchivo que contiene el aspecto icónico del elemento seleccionado, si la casilla de verificación Mostrar como icono estaba activada cuando se descartó el cuadro de diálogo seleccionando Aceptar; NULL.

## <a name="coleconvertdialoggetselectiontype"></a><a name="getselectiontype"></a>COleConvertDialog::GetSelectionType

Llame a esta función para determinar el tipo de conversión seleccionado en el cuadro de diálogo Convertir.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Valor devuelto

Tipo de selección realizada.

### <a name="remarks"></a>Observaciones

Los valores de tipo devuelto `Selection` se especifican `COleConvertDialog` mediante el tipo de enumeración declarado en la clase.

```
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };
```

A continuación se describen breves de estos valores:

- `COleConvertDialog::noConversion`Se ha devuelto si se canceló el cuadro de diálogo o si el usuario no seleccionó ninguna conversión. Si `COleConvertDialog::DoModal` se devuelve IDOK, es posible que el usuario haya seleccionado un icono diferente al seleccionado anteriormente.

- `COleConvertDialog::convertItem`Se ha devuelto si se ha activado el botón de `DoModal` opción Convertir a, el usuario seleccionó un elemento diferente al que convertir y devolvió IDOK.

- `COleConvertDialog::activateAs`Se ha devuelto si se ha activado el botón de `DoModal` opción Activar como, el usuario ha seleccionado un elemento diferente para activar y se ha devuelto IDOK.

## <a name="coleconvertdialogm_cv"></a><a name="m_cv"></a>COleConvertDialog::m_cv

Estructura de tipo OLEUICONVERT utilizada para controlar el comportamiento del cuadro de diálogo Convertir.

```
OLEUICONVERT m_cv;
```

### <a name="remarks"></a>Observaciones

Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.

Para obtener más información, vea la estructura [OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)
