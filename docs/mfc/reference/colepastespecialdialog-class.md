---
title: COlePasteSpecialDialog (Clase)
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
ms.openlocfilehash: 47fb421ef9dedcae7f92d33f55988dbbc2ea452d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753816"
---
# <a name="colepastespecialdialog-class"></a>COlePasteSpecialDialog (Clase)

Se utiliza en el cuadro de diálogo Pegado especial de OLE.

## <a name="syntax"></a>Sintaxis

```
class COlePasteSpecialDialog : public COleDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COlePasteSpecialDialog::COlePasteSpecialDialog](#colepastespecialdialog)|Construye un objeto `COlePasteSpecialDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COlePasteSpecialDialog::AddFormat](#addformat)|Agrega formatos personalizados a la lista de formatos que la aplicación puede pegar.|
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|Agrega una nueva entrada a la lista de formatos de Portapapeles compatibles.|
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|Agrega CF_BITMAP, CF_DIB, CF_METAFILEPICT y, opcionalmente, CF_LINKSOURCE a la lista de formatos que la aplicación puede pegar.|
|[COlePasteSpecialDialog::CreateItem](#createitem)|Crea el elemento en el documento contenedor con el formato especificado.|
|[COlePasteSpecialDialog::DoModal](#domodal)|Muestra el cuadro de diálogo Especial de pegado OLE.|
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|Indica si se debe dibujar el elemento como un icono o no.|
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|Obtiene un identificador del metarchivo asociado con la forma icónica de este elemento.|
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|Obtiene el índice de opciones de pegado disponibles elegido según el usuario.|
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|Obtiene el tipo de selección elegido.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COlePasteSpecialDialog::m_ps](#m_ps)|Estructura de tipo OLEUIPASTESPECIAL que controla la función del cuadro de diálogo.|

## <a name="remarks"></a>Observaciones

Cree un objeto `COlePasteSpecialDialog` de clase cuando desee llamar a este cuadro de diálogo. Una `COlePasteSpecialDialog` vez construido un objeto, puede usar las funciones miembro [AddFormat](#addformat) y [AddStandardFormats](#addstandardformats) para agregar formatos de Portapapeles al cuadro de diálogo. También puede utilizar la [estructura m_ps](#m_ps) para inicializar los valores o estados de los controles en el cuadro de diálogo. La `m_ps` estructura es de tipo OLEUIPASTESPECIAL.

Para obtener más información, vea la estructura [OLEUIPASTESPECIAL](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) en el Windows SDK.

Para obtener más información acerca de los cuadros de diálogo específicos de OLE, vea el artículo [Cuadros](../../mfc/dialog-boxes-in-ole.md)de diálogo en OLE .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePasteSpecialDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxodlgs.h

## <a name="colepastespecialdialogaddformat"></a><a name="addformat"></a>COlePasteSpecialDialog::AddFormat

Llame a esta función para agregar nuevos formatos a la lista de formatos que la aplicación puede admitir en una operación Pegar especial.

```cpp
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

*Fmt*<br/>
Referencia al tipo de datos que se va a agregar.

*lpszFormat*<br/>
Cadena que describe el formato para el usuario.

*lpszResult*<br/>
Cadena que describe el resultado si se elige este formato en el cuadro de diálogo.

*flags*<br/>
Las diferentes opciones de vinculación e incrustación disponibles para este formato. Este indicador es una combinación bit a bit de uno o varios de los valores diferentes en el tipo enumerado OLEUIPASTEFLAG.

*Cf*<br/>
El formato del portapapeles que se va a agregar.

*tymed*<br/>
Los tipos de medios disponibles en este formato. Se trata de una combinación bit a bit de uno o varios de los valores del tipo enumerado TYMED.

*nFormatID*<br/>
El identificador de la cadena que identifica este formato. El formato de esta cadena es de dos cadenas separadas separadas por un carácter 'n'. La primera cadena es la misma que se pasaría en el parámetro *lpstrFormat* y la segunda es la misma que el parámetro *lpstrResult.*

*bEnableIcon*<br/>
Marcador que determina si la casilla Mostrar como icono está habilitada cuando se elige este formato en el cuadro de lista.

*Parpadear*<br/>
Marcador que determina si el botón de opción Pegar vínculo está habilitado cuando se elige este formato en el cuadro de lista.

### <a name="remarks"></a>Observaciones

Se puede llamar a esta función para agregar formatos estándar como CF_TEXT o CF_TIFF o formatos personalizados que la aplicación ha registrado en el sistema. Para obtener más información sobre cómo pegar objetos de datos en la aplicación, consulte el artículo Objetos de datos y orígenes de [datos: Manipulación](../../mfc/data-objects-and-data-sources-manipulation.md).

Para obtener más información, vea el tipo de enumeración [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) y la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

Para obtener más información, vea el tipo enumerado [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) en el Windows SDK.

## <a name="colepastespecialdialogaddlinkentry"></a><a name="addlinkentry"></a>COlePasteSpecialDialog::AddLinkEntry

Agrega una nueva entrada a la lista de formatos de Portapapeles compatibles.

```
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```

### <a name="parameters"></a>Parámetros

*Cf*<br/>
El formato del portapapeles que se va a agregar.

### <a name="return-value"></a>Valor devuelto

Estructura [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) que contiene la información de la nueva entrada de vínculo.

## <a name="colepastespecialdialogaddstandardformats"></a><a name="addstandardformats"></a>COlePasteSpecialDialog::AddStandardFormats

Llame a esta función para agregar los siguientes formatos de Portapapeles a la lista de formatos que la aplicación puede admitir en una operación Pegar especial:

```cpp
void AddStandardFormats(BOOL bEnableLink = TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnableLink*<br/>
Marcador que determina si se debe agregar CF_LINKSOURCE a la lista de formatos que la aplicación puede pegar.

### <a name="remarks"></a>Observaciones

- CF_BITMAP

- CF_DIB

- CF_METAFILEPICT

- **"Objeto incrustado"**

- (opcionalmente) **"Fuente de enlace"**

Estos formatos se utilizan para admitir la incrustación y vinculación.

## <a name="colepastespecialdialogcolepastespecialdialog"></a><a name="colepastespecialdialog"></a>COlePasteSpecialDialog::COlePasteSpecialDialog

Construye un objeto `COlePasteSpecialDialog`.

```
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,
    COleDataObject* pDataObject = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Marca de creación, contiene cualquier número de los siguientes indicadores combinados mediante el operador OR bit a bit:

- PSF_SELECTPASTE Especifica que el botón de opción Pegar se comprobará inicialmente cuando se llame al cuadro de diálogo. No se puede utilizar en combinación con PSF_SELECTPASTELINK. Este es el valor predeterminado.

- PSF_SELECTPASTELINK Especifica que el botón de opción Pegar vínculo se comprobará inicialmente cuando se llame al cuadro de diálogo. No se puede utilizar en combinación con PSF_SELECTPASTE.

- PSF_CHECKDISPLAYASICON Especifica que la casilla mostrar como icono se desactivará inicialmente cuando se llame al cuadro de diálogo.

- PSF_SHOWHELP Especifica que el botón Ayuda se mostrará cuando se llame al cuadro de diálogo.

*pDataObject*<br/>
Apunta a la [COleDataObject](../../mfc/reference/coledataobject-class.md) para pegar. Si este valor es NULL, `COleDataObject` obtiene el del Portapapeles.

*pParentWnd*<br/>
Apunta al objeto de ventana principal `CWnd`o propietario (de tipo ) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del cuadro de diálogo se establece en la ventana principal de la aplicación.

### <a name="remarks"></a>Observaciones

Esta función solo `COlePasteSpecialDialog` construye un objeto. Para mostrar el cuadro de diálogo, llame a la [Función DoModal.](#domodal)

Para obtener más información, vea el tipo enumerado [OLEUIPASTEFLAG](/windows/win32/api/oledlg/ne-oledlg-oleuipasteflag) en el Windows SDK.

## <a name="colepastespecialdialogcreateitem"></a><a name="createitem"></a>COlePasteSpecialDialog::CreateItem

Crea el nuevo elemento que se ha elegido en el cuadro de diálogo Pegar especial.

```
BOOL CreateItem(COleClientItem* pNewItem);
```

### <a name="parameters"></a>Parámetros

*pNewItem*<br/>
Apunta a `COleClientItem` una instancia. No puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento se creó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función solo se debe llamar después de [DoModal](#domodal) devuelve IDOK.

## <a name="colepastespecialdialogdomodal"></a><a name="domodal"></a>COlePasteSpecialDialog::DoModal

Muestra el cuadro de diálogo Especial de pegado OLE.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Estado de finalización del cuadro de diálogo. Uno de los valores siguientes:

- IDOK si el cuadro de diálogo se ha mostrado correctamente.

- IDCANCEL si el usuario canceló el cuadro de diálogo.

- IDABORT si se ha producido un error. Si se devuelve IDABORT, llame a la `COleDialog::GetLastError` función miembro para obtener más información sobre el tipo de error que se produjo. Para obtener una lista de posibles errores, vea la función [OleUIPasteSpecial](/windows/win32/api/oledlg/nf-oledlg-oleuipastespecialw) en el Windows SDK.

### <a name="remarks"></a>Observaciones

Si desea inicializar los distintos controles de cuadro de diálogo estableciendo `DoModal`miembros de la [estructura m_ps,](#m_ps) debe hacerlo antes de llamar a , pero después de que se construye el objeto de cuadro de diálogo.

Si `DoModal` devuelve IDOK, puede llamar a otras funciones miembro para recuperar la configuración o la información introducida por el usuario en el cuadro de diálogo.

## <a name="colepastespecialdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COlePasteSpecialDialog::GetDrawAspect

Determina si el usuario eligió mostrar el elemento seleccionado como un icono.

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>Valor devuelto

El método necesario para representar el objeto.

- DVASPECT_CONTENT Se devuelve si la casilla de verificación Mostrar como icono no estaba activada cuando se descartó el cuadro de diálogo.

- DVASPECT_ICON Se devuelve si la casilla mostrar como icono estaba activada cuando se descartó el cuadro de diálogo.

### <a name="remarks"></a>Observaciones

Solo llame a esta función después de [DoModal](#domodal) devuelve IDOK.

Para obtener más información sobre el aspecto del dibujo, consulte la estructura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) en el Windows SDK.

## <a name="colepastespecialdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COlePasteSpecialDialog::GetIconicMetafile

Obtiene el metarchivo asociado al elemento seleccionado por el usuario.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Valor devuelto

El identificador del metarchivo que contiene el aspecto icónico del elemento seleccionado, si la casilla de verificación Mostrar como icono se ha seleccionado cuando se descartó el cuadro de diálogo seleccionando **Aceptar**; NULL.

## <a name="colepastespecialdialoggetpasteindex"></a><a name="getpasteindex"></a>COlePasteSpecialDialog::GetPasteIndex

Obtiene el valor de índice asociado a la entrada seleccionada por el usuario.

```
int GetPasteIndex() const;
```

### <a name="return-value"></a>Valor devuelto

El índice en `OLEUIPASTEENTRY` la matriz de estructuras seleccionada por el usuario. El formato que corresponde al índice seleccionado debe utilizarse al realizar la operación de pegar.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea la estructura [OLEUIPASTEENTRY](/windows/win32/api/oledlg/ns-oledlg-oleuipasteentryw) en el Windows SDK.

## <a name="colepastespecialdialoggetselectiontype"></a><a name="getselectiontype"></a>COlePasteSpecialDialog::GetSelectionType

Determina el tipo de selección que realizó el usuario.

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el tipo de selección realizada.

### <a name="remarks"></a>Observaciones

Los valores de tipo devuelto `Selection` se especifican `COlePasteSpecialDialog` mediante el tipo de enumeración declarado en la clase.

```
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };
```

A continuación se presentan breves descripciones de estos valores:

- `COlePasteSpecialDialog::pasteLink`Se ha activado el botón de opción Pegar vínculo y el formato elegido era un formato OLE estándar.

- `COlePasteSpecialDialog::pasteNormal`Se ha activado el botón de opción Pegar y el formato elegido era un formato OLE estándar.

- `COlePasteSpecialDialog::pasteOther`El formato seleccionado no es un formato OLE estándar.

- `COlePasteSpecialDialog::pasteStatic`El formato elegido era un metarchivo.

## <a name="colepastespecialdialogm_ps"></a><a name="m_ps"></a>COlePasteSpecialDialog::m_ps

Estructura de tipo OLEUIPASTESPECIAL utilizada para controlar el comportamiento del cuadro de diálogo Pegado especial.

```
OLEUIPASTESPECIAL m_ps;
```

### <a name="remarks"></a>Observaciones

Los miembros de esta estructura se pueden modificar directamente o a través de funciones miembro.

Para obtener más información, vea la estructura [OLEUIPASTESPECIAL](/windows/win32/api/oledlg/ns-oledlg-oleuipastespecialw) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Ejemplo de MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDialog (clase)](../../mfc/reference/coledialog-class.md)
