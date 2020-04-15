---
title: CMFCRibbonFontComboBox (Clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::BuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetCharSet
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontDesc
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontType
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetPitchAndFamily
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::RebuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::SetFont
helpviewer_keywords:
- CMFCRibbonFontComboBox [MFC], CMFCRibbonFontComboBox
- CMFCRibbonFontComboBox [MFC], BuildFonts
- CMFCRibbonFontComboBox [MFC], GetCharSet
- CMFCRibbonFontComboBox [MFC], GetFontDesc
- CMFCRibbonFontComboBox [MFC], GetFontType
- CMFCRibbonFontComboBox [MFC], GetPitchAndFamily
- CMFCRibbonFontComboBox [MFC], RebuildFonts
- CMFCRibbonFontComboBox [MFC], SetFont
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
ms.openlocfilehash: 822f4f6fe76bb5b82b455daec54ed96568ea6ba7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375166"
---
# <a name="cmfcribbonfontcombobox-class"></a>CMFCRibbonFontComboBox (Clase)

Implementa un cuadro combinado que contiene una lista de fuentes. El cuadro combinado se coloca en un panel de la cinta.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|Destructor.|

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|Construye e inicializa un objeto `CMFCRibbonFontComboBox`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|Rellena el cuadro combinado de fuente de la cinta con fuentes del tipo de fuente, el juego de caracteres y el paso y la familia especificados.|
|`CMFCRibbonFontComboBox::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|Devuelve el juego de caracteres especificado.|
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|Devuelve los tipos de fuente que se van a mostrar en el cuadro combinado. Las opciones válidas son DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE o cualquier combinación bit a bit de estas.|
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|Devuelve el paso y la familia de las fuentes que se muestran en el cuadro combinado.|
|`CMFCRibbonFontComboBox::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|Rellena el cuadro combinado de fuente de la cinta con fuentes del tipo de fuente, el juego de caracteres y el paso y la familia previamente especificados.|
|[CMFCRibbonFontComboBox::SetFont](#setfont)|Selecciona la fuente especificada en el cuadro combinado.|

## <a name="remarks"></a>Observaciones

Después de `CMFCRibbonFontComboBox` crear un objeto, agréguelo a un panel de la cinta de opciones llamando a [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxRibbonComboBox.h

## <a name="cmfcribbonfontcomboboxbuildfonts"></a><a name="buildfonts"></a>CMFCRibbonFontComboBox::BuildFonts

Rellena el cuadro combinado de la cinta de opciones con fuentes.

```
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```

### <a name="parameters"></a>Parámetros

*nFontType*<br/>
[en] Especifica el tipo de fuente de las fuentes que se va a agregar.

*nCharSet*<br/>
[en] Especifica el juego de caracteres de las fuentes que se va a agregar.

*nPitchAndFamily*<br/>
[en] Especifica el tono y la familia de las fuentes que se va a agregar.

## <a name="cmfcribbonfontcomboboxcmfcribbonfontcombobox"></a><a name="cmfcribbonfontcombobox"></a>CMFCRibbonFontComboBox::CMFCRibbonFontComboBox

Construye e inicializa un [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md) objeto.

```
CMFCRibbonFontComboBox(
    UINT nID,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH,
    int nWidth = -1);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
[en] El identificador de comando del comando que se ejecuta cuando el usuario selecciona un elemento del cuadro combinado.

*nFontType*<br/>
[en] Especifica qué tipos de fuente se mostrarán en el cuadro combinado. Las opciones válidas son DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE o cualquier combinación bit a bit de estas.

*nCharSet*<br/>
[en] Filtra las fuentes del cuadro combinado a las que pertenecen al juego de caracteres especificado.

*nPitchAndFamily*<br/>
[en] Especifica el tono y la familia de las fuentes que se muestran en el cuadro combinado.

*nAncho*<br/>
[en] Especifica el ancho, en píxeles, del cuadro combinado.

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de los posibles valores de parámetro *nFontType,* vea [EnumFontFamProc](/previous-versions/dd162621\(v=vs.85\)) en la documentación de Windows SDK.

Para obtener más información acerca de los conjuntos de caracteres válidos que se pueden asignar a *nCharSet*y los valores válidos que se pueden asignar a *nPitchAndFamily*, consulte [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) en la documentación de Windows SDK.

## <a name="cmfcribbonfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a>CMFCRibbonFontComboBox::GetFontDesc

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;
```

### <a name="parameters"></a>Parámetros

[en] *iIndex*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonfontcomboboxrebuildfonts"></a><a name="rebuildfonts"></a>CMFCRibbonFontComboBox::RebuildFonts

Rellena el cuadro combinado de la cinta de opciones con fuentes de un tipo de fuente, un juego de caracteres y un tono y una familia especificados anteriormente.

```
void RebuildFonts();
```

### <a name="remarks"></a>Observaciones

Puede especificar el tipo de fuente, el juego de caracteres y el tono y la familia de las fuentes que se incluirán en el cuadro combinado de fuentes de la cinta de opciones en el [constructor](#cmfcribbonfontcombobox) de esta clase o llamando a [CMFCRibbonFontComboBox::BuildFonts](#buildfonts).

## <a name="cmfcribbonfontcomboboxsetfont"></a><a name="setfont"></a>CMFCRibbonFontComboBox::SetFont

Selecciona la fuente especificada en el cuadro combinado.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet = DEFAULT_CHARSET,
    BOOL bExact = FALSE);
```

### <a name="parameters"></a>Parámetros

'lpszName* Especifica el nombre de la fuente que se va a seleccionar.

*nCharSet*<br/>
Especifica el juego de caracteres de la fuente seleccionada.

*bExact*<br/>
TRUE para especificar que el juego de caracteres debe coincidir al seleccionar una fuente; FALSE para especificar que el juego de caracteres se puede omitir al seleccionar una fuente.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encontró y seleccionó la fuente especificada; de lo contrario, cero.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonfontcomboboxgetcharset"></a><a name="getcharset"></a>CMFCRibbonFontComboBox::GetCharSet

Devuelve el juego de caracteres especificado.

```
BYTE GetCharSet() const;
```

### <a name="return-value"></a>Valor devuelto

Conjunto de caracteres (consulte LOGFONT en la documentación de Windows SDK).

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonfontcomboboxgetfonttype"></a><a name="getfonttype"></a>CMFCRibbonFontComboBox::GetFontType

Devuelve los tipos de fuente que se van a mostrar en el cuadro combinado. Las opciones válidas son DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE o cualquier combinación bit a bit de estas.

```
int GetFontType() const;
```

### <a name="return-value"></a>Valor devuelto

Tipos de fuente (consulte EnumFontFamProc en la documentación de Windows SDK).

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonfontcomboboxgetpitchandfamily"></a><a name="getpitchandfamily"></a>CMFCRibbonFontComboBox::GetPitchAndFamily

Devuelve el paso y la familia de las fuentes que se muestran en el cuadro combinado.

```
BYTE GetPitchAndFamily() const;
```

### <a name="return-value"></a>Valor devuelto

Pitch y la familia (consulte LOGFONT en la documentación de Windows SDK).

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonComboBox (clase)](../../mfc/reference/cmfcribboncombobox-class.md)
