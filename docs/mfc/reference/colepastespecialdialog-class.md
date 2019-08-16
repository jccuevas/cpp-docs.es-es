---
title: Clase COlePasteSpecialDialog
ms.date: 11/04/2016
f1_keywords:
- COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::AddFormat
- AFXODLGS/COlePasteSpecialDialog::AddLinkEntry
- AFXODLGS/COlePasteSpecialDialog::AddStandardFormats
- AFXODLGS/COlePasteSpecialDialog::CreateItem
- AFXODLGS/COlePasteSpecialDialog::DoModal
- AFXODLGS/COlePasteSpecialDialog::GetDrawAspect
- AFXODLGS/COlePasteSpecialDialog::GetIconicMetafile
- AFXODLGS/COlePasteSpecialDialog::GetPasteIndex
- AFXODLGS/COlePasteSpecialDialog::GetSelectionType
- AFXODLGS/COlePasteSpecialDialog::m_ps
helpviewer_keywords:
- COlePasteSpecialDialog [MFC], COlePasteSpecialDialog
- COlePasteSpecialDialog [MFC], AddFormat
- COlePasteSpecialDialog [MFC], AddLinkEntry
- COlePasteSpecialDialog [MFC], AddStandardFormats
- COlePasteSpecialDialog [MFC], CreateItem
- COlePasteSpecialDialog [MFC], DoModal
- COlePasteSpecialDialog [MFC], GetDrawAspect
- COlePasteSpecialDialog [MFC], GetIconicMetafile
- COlePasteSpecialDialog [MFC], GetPasteIndex
- COlePasteSpecialDialog [MFC], GetSelectionType
- COlePasteSpecialDialog [MFC], m_ps
ms.assetid: 0e82ef9a-9bbe-457e-8240-42c86a0534f7
ms.openlocfilehash: f4174369620f14f2d1ac410aa5d756c75097ad0f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503762"
---
# <a name="colepastespecialdialog-class"></a>Clase COlePasteSpecialDialog

Se utiliza en el cuadro de diálogo Pegado especial de OLE.

## <a name="syntax"></a>Sintaxis

```
class COlePasteSpecialDialog : public COleDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COlePasteSpecialDialog::COlePasteSpecialDialog](#colepastespecialdialog)|Construye un objeto `COlePasteSpecialDialog`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COlePasteSpecialDialog::AddFormat](#addformat)|Agrega formatos personalizados a la lista de formatos que puede pegar la aplicación.|
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|Agrega una nueva entrada a la lista de formatos de Portapapeles admitidos.|
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|Agrega CF_BITMAP, CF_DIB, CF_METAFILEPICT y, opcionalmente, CF_LINKSOURCE a la lista de formatos que puede pegar la aplicación.|
|[COlePasteSpecialDialog::CreateItem](#createitem)|Crea el elemento en el documento contenedor usando el formato especificado.|
|[COlePasteSpecialDialog::DoModal](#domodal)|Muestra el cuadro de diálogo Pegado especial de OLE.|
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|Indica si se debe dibujar el elemento como un icono o no.|
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|Obtiene un identificador para el metarchivo asociado al formulario de iconos de este elemento.|
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|Obtiene el índice de las opciones de pegado disponibles elegidas por el usuario.|
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|Obtiene el tipo de selección elegido.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COlePasteSpecialDialog::m_ps](#m_ps)|Estructura de tipo OLEUIPASTESPECIAL que controla la función del cuadro de diálogo.|

## <a name="remarks"></a>Comentarios

Cree un objeto de clase `COlePasteSpecialDialog` cuando desee llamar a este cuadro de diálogo. Una vez `COlePasteSpecialDialog` construido un objeto, puede usar las funciones miembro [AddFormat](#addformat) y [AddStandardFormats](#addstandardformats) para agregar formatos del Portapapeles al cuadro de diálogo. También puede usar la estructura [m_ps](#m_ps) para inicializar los valores o los Estados de los controles en el cuadro de diálogo. La `m_ps` estructura es de tipo OLEUIPASTESPECIAL.

Para obtener más información, vea la estructura [OLEUIPASTESPECIAL](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) en el Windows SDK.

Para obtener más información sobre los cuadros de diálogo específicos de OLE, vea los [cuadros de diálogo de artículo en OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePasteSpecialDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxodlgs. h

##  <a name="addformat"></a>  COlePasteSpecialDialog::AddFormat

Llame a esta función para agregar nuevos formatos a la lista de formatos que la aplicación puede admitir en una operación de pegado especial.

```
void AddFormat(
    const FORMATETC& formatEtc,
    LPTSTR lpszFormat,
    LPTSTR lpszResult,
    DWORD flags);

void AddFormat(
    UINT cf,
    DWORD tymed,
    UINT nFormatID,
    BOOL bEnableIcon,
    BOOL bLink);
```

### <a name="parameters"></a>Parámetros

*fmt*<br/>
Referencia al tipo de datos que se va a agregar.

*lpszFormat*<br/>
Cadena que describe el formato del usuario.

*lpszResult*<br/>
Cadena que describe el resultado si se elige este formato en el cuadro de diálogo.

*flags*<br/>
Las distintas opciones de vinculación e incrustación disponibles para este formato. Esta marca es una combinación bit a bit de uno o varios valores diferentes en el tipo enumerado OLEUIPASTEFLAG.

*cf*<br/>
Formato del portapapeles que se va a agregar.

*tymed*<br/>
Tipos de medios disponibles en este formato. Se trata de una combinación bit a bit de uno o varios de los valores del tipo enumerado TYMED.

*nFormatID*<br/>
IDENTIFICADOR de la cadena que identifica este formato. El formato de esta cadena es dos cadenas independientes separadas por un carácter "\n". La primera cadena es la misma que se pasaría en el parámetro *lpstrFormat* y la segunda es igual que el parámetro *lpstrResult* .

*bEnableIcon*<br/>
Marca que determina si la casilla Mostrar como icono está habilitada cuando se elige este formato en el cuadro de lista.

*Intermitente*<br/>
Marca que determina si el botón de radio pegar vínculo está habilitado cuando se elige este formato en el cuadro de lista.

### <a name="remarks"></a>Comentarios

Se puede llamar a esta función para agregar formatos estándar, como CF_TEXT o CF_TIFF, o los formatos personalizados que la aplicación ha registrado con el sistema. Para obtener más información sobre cómo pegar objetos de datos en la aplicación, vea [el artículo objetos de datos y orígenes de datos: Manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Para obtener más información, vea el tipo de enumeración [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) y la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, vea el tipo enumerado [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) en el Windows SDK.

##  <a name="addlinkentry"></a>  COlePasteSpecialDialog::AddLinkEntry

Agrega una nueva entrada a la lista de formatos de Portapapeles admitidos.

```
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```

### <a name="parameters"></a>Parámetros

*cf*<br/>
Formato del portapapeles que se va a agregar.

### <a name="return-value"></a>Valor devuelto

Estructura [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) que contiene la información de la nueva entrada de vínculo.

##  <a name="addstandardformats"></a>  COlePasteSpecialDialog::AddStandardFormats

Llame a esta función para agregar los siguientes formatos de portapapeles a la lista de formatos que la aplicación puede admitir en una operación de pegado especial:

```
void AddStandardFormats(BOOL bEnableLink = TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnableLink*<br/>
Marca que determina si se debe agregar CF_LINKSOURCE a la lista de formatos que puede pegar la aplicación.

### <a name="remarks"></a>Comentarios

- CF_BITMAP

- CF_DIB

- CF_METAFILEPICT

- **"Objeto incrustado"**

- Opcionalmente **"Origen del vínculo"**

Estos formatos se utilizan para admitir la incrustación y vinculación.

##  <a name="colepastespecialdialog"></a>  COlePasteSpecialDialog::COlePasteSpecialDialog

Construye un objeto `COlePasteSpecialDialog`.

```
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,
    COleDataObject* pDataObject = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Marca de creación, contiene cualquier número de las siguientes marcas combinadas mediante el operador bit a bit or:

- PSF_SELECTPASTE especifica que el botón de radio pegar se activará inicialmente cuando se llame al cuadro de diálogo. No se puede usar en combinación con PSF_SELECTPASTELINK. Este es el valor predeterminado.

- PSF_SELECTPASTELINK especifica que el botón de radio pegar vínculo se activará inicialmente cuando se llame al cuadro de diálogo. No se puede usar en combinación con PSF_SELECTPASTE.

- PSF_CHECKDISPLAYASICON especifica que la casilla Mostrar como icono se activará inicialmente cuando se llame al cuadro de diálogo.

- PSF_SHOWHELP especifica que el botón ayuda se mostrará cuando se llame al cuadro de diálogo.

*pDataObject*<br/>
Apunta a [COleDataObject](../../mfc/reference/coledataobject-class.md) para pegarlo. Si este valor es null, obtiene el `COleDataObject` del portapapeles.

*pParentWnd*<br/>
Apunta al objeto de ventana primario o propietario (de tipo `CWnd`) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del cuadro de diálogo se establece en la ventana principal de la aplicación.

### <a name="remarks"></a>Comentarios

Esta función solo crea un `COlePasteSpecialDialog` objeto. Para mostrar el cuadro de diálogo, llame a la función [DoModal](#domodal) .

Para obtener más información, vea el tipo enumerado [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) en el Windows SDK.

##  <a name="createitem"></a>  COlePasteSpecialDialog::CreateItem

Crea el nuevo elemento que se eligió en el cuadro de diálogo Pegar especial.

```
BOOL CreateItem(COleClientItem* pNewItem);
```

### <a name="parameters"></a>Parámetros

*pNewItem*<br/>
Apunta a una `COleClientItem` instancia de. No puede ser nulo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento se creó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Solo se debe llamar a esta función después de que [DoModal](#domodal) devuelva IDOK.

##  <a name="domodal"></a>  COlePasteSpecialDialog::DoModal

Muestra el cuadro de diálogo Pegado especial de OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Estado de finalización del cuadro de diálogo. Uno de los siguientes valores:

- IDOK si el cuadro de diálogo se mostró correctamente.

- IDCANCEL si el usuario canceló el cuadro de diálogo.

- IDABORT si se produjo un error. Si se devuelve IDABORT, llame a `COleDialog::GetLastError` la función miembro para obtener más información sobre el tipo de error que se ha producido. Para obtener una lista de posibles errores, vea la función [OleUIPasteSpecial](/windows/win32/api/oledlg/nf-oledlg-oleuipastespecialw) en el Windows SDK.

### <a name="remarks"></a>Comentarios

Si desea inicializar los distintos controles de cuadro de diálogo estableciendo los miembros de la estructura [m_ps](#m_ps) , debe hacerlo antes de llamar `DoModal`a, pero después de que se construya el objeto de cuadro de diálogo.

Si `DoModal` devuelve IDOK, puede llamar a otras funciones miembro para recuperar la información de configuración o la entrada del usuario en el cuadro de diálogo.

##  <a name="getdrawaspect"></a>  COlePasteSpecialDialog::GetDrawAspect

Determina si el usuario ha elegido mostrar el elemento seleccionado como un icono.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Valor devuelto

Método necesario para representar el objeto.

- DVASPECT_CONTENT se devuelve si no se ha activado la casilla Mostrar como icono cuando se descartó el cuadro de diálogo.

- DVASPECT_ICON se devuelve si se ha activado la casilla Mostrar como icono cuando se descartó el cuadro de diálogo.

### <a name="remarks"></a>Comentarios

Llame a esta función solo después de que [DoModal](#domodal) devuelva IDOK.

Para obtener más información sobre cómo dibujar el aspecto, consulte la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

##  <a name="geticonicmetafile"></a>  COlePasteSpecialDialog::GetIconicMetafile

Obtiene el metarchivo asociado al elemento seleccionado por el usuario.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del metarchivo que contiene el aspecto de los iconos del elemento seleccionado, si la casilla Mostrar como icono estaba activada cuando el cuadro de diálogo se descartó; para ello, elija **Aceptar**; de lo contrario, NULL.

##  <a name="getpasteindex"></a>  COlePasteSpecialDialog::GetPasteIndex

Obtiene el valor de índice asociado a la entrada seleccionada por el usuario.

```
int GetPasteIndex() const;
```

### <a name="return-value"></a>Valor devuelto

Índice de la matriz de `OLEUIPASTEENTRY` estructuras seleccionada por el usuario. El formato que corresponde al índice seleccionado debe usarse al realizar la operación de pegado.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea la estructura [OLEUIPASTEENTRY](/windows/win32/api/oledlg/ns-oledlg-oleuipasteentryw) en el Windows SDK.

##  <a name="getselectiontype"></a>  COlePasteSpecialDialog::GetSelectionType

Determina el tipo de selección que realizó el usuario.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el tipo de selección realizada.

### <a name="remarks"></a>Comentarios

Los valores de tipo devuelto se especifican mediante el `Selection` tipo de enumeración declarado en la `COlePasteSpecialDialog` clase.

```
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };
```

Breve desccriptions de estos valores:

- `COlePasteSpecialDialog::pasteLink`Se activó el botón de radio pegar vínculo y el formato elegido era un formato OLE estándar.

- `COlePasteSpecialDialog::pasteNormal`Se activó el botón de radio pegar y el formato elegido era un formato OLE estándar.

- `COlePasteSpecialDialog::pasteOther`El formato seleccionado no es un formato OLE estándar.

- `COlePasteSpecialDialog::pasteStatic`El formato elegido era un metarchivo.

##  <a name="m_ps"></a>  COlePasteSpecialDialog::m_ps

Estructura de tipo OLEUIPASTESPECIAL que se usa para controlar el comportamiento del cuadro de diálogo Pegado especial.

```
OLEUIPASTESPECIAL m_ps;
```

### <a name="remarks"></a>Comentarios

Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.

Para obtener más información, vea la estructura [OLEUIPASTESPECIAL](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Ejemplo OCLIENT de MFC](../../overview/visual-cpp-samples.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)
