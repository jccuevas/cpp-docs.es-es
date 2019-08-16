---
title: Clase CMFCRibbonFontComboBox
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
ms.openlocfilehash: 186c4bc3e1b26529ed0e000d2893e1b2d81c4304
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504966"
---
# <a name="cmfcribbonfontcombobox-class"></a>Clase CMFCRibbonFontComboBox

Implementa un cuadro combinado que contiene una lista de fuentes. El cuadro combinado se coloca en un panel de la cinta.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|Destructor.|

### <a name="protected-constructors"></a>Constructores protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|Construye e inicializa un objeto `CMFCRibbonFontComboBox`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|Rellena el cuadro combinado de fuente de la cinta con fuentes del tipo de fuente, el juego de caracteres y el paso y la familia especificados.|
|`CMFCRibbonFontComboBox::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|Devuelve el juego de caracteres especificado.|
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|Devuelve los tipos de fuente que se van a mostrar en el cuadro combinado. Las opciones válidas son DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE o cualquier combinación bit a bit de estas.|
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|Devuelve el paso y la familia de las fuentes que se muestran en el cuadro combinado.|
|`CMFCRibbonFontComboBox::GetThisClass`|Lo usa el marco de trabajo para obtener un puntero al objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|Rellena el cuadro combinado de fuente de la cinta con fuentes del tipo de fuente, el juego de caracteres y el paso y la familia previamente especificados.|
|[CMFCRibbonFontComboBox::SetFont](#setfont)|Selecciona la fuente especificada en el cuadro combinado.|

## <a name="remarks"></a>Comentarios

Después de crear un `CMFCRibbonFontComboBox` objeto, agréguelo a un panel de la cinta de [Opciones llamando a CMFCRibbonPanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxRibbonComboBox. h

##  <a name="buildfonts"></a>  CMFCRibbonFontComboBox::BuildFonts

Rellena el cuadro combinado de la cinta de opciones con fuentes.

```
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```

### <a name="parameters"></a>Parámetros

*nFontType*<br/>
de Especifica el tipo de fuente de las fuentes que se van a agregar.

*nCharSet*<br/>
de Especifica el juego de caracteres de las fuentes que se van a agregar.

*nPitchAndFamily*<br/>
de Especifica el paso y la familia de las fuentes que se van a agregar.

##  <a name="cmfcribbonfontcombobox"></a>  CMFCRibbonFontComboBox::CMFCRibbonFontComboBox

Construye e inicializa un objeto [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md) .

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
de IDENTIFICADOR de comando del comando que se ejecuta cuando el usuario selecciona un elemento en el cuadro combinado.

*nFontType*<br/>
de Especifica los tipos de fuente que se van a mostrar en el cuadro combinado. Las opciones válidas son DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE o cualquier combinación bit a bit de estas.

*nCharSet*<br/>
de Filtra las fuentes del cuadro combinado para aquellas que pertenecen al Juego de caracteres especificado.

*nPitchAndFamily*<br/>
de Especifica el paso y la familia de las fuentes que se muestran en el cuadro combinado.

*nWidth*<br/>
de Especifica el ancho, en píxeles, del cuadro combinado.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre los posibles valores de los parámetros de *nFontType* , vea [EnumFontFamProc](/previous-versions/dd162621\(v=vs.85\)) en la documentación de Windows SDK.

Para obtener más información sobre los juegos de caracteres válidos que se pueden asignar a *nCharSet*y los valores válidos que se pueden asignar a *NPitchAndFamily*, consulte [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) en la documentación de Windows SDK.

##  <a name="getfontdesc"></a>  CMFCRibbonFontComboBox::GetFontDesc

Para obtener más información, consulte el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\MFC** de la instalación de Visual Studio.

```
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;
```

### <a name="parameters"></a>Parámetros

de *iIndex*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="rebuildfonts"></a>  CMFCRibbonFontComboBox::RebuildFonts

Rellena el cuadro combinado de la cinta de opciones con fuentes de un tipo de fuente, un juego de caracteres y un paso y familia especificados previamente.

```
void RebuildFonts();
```

### <a name="remarks"></a>Comentarios

Puede especificar el tipo de fuente, el juego de caracteres y el paso y la familia de las fuentes que se van a incluir en el cuadro combinado de fuente de la cinta de opciones en el [constructor](#cmfcribbonfontcombobox) de esta clase o mediante una llamada a [CMFCRibbonFontComboBox:: BuildFonts](#buildfonts).

##  <a name="setfont"></a>  CMFCRibbonFontComboBox::SetFont

Selecciona la fuente especificada en el cuadro combinado.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet = DEFAULT_CHARSET,
    BOOL bExact = FALSE);
```

### <a name="parameters"></a>Parámetros

' lpszName * especifica el nombre de la fuente que se va a seleccionar.

*nCharSet*<br/>
Especifica el juego de caracteres de la fuente seleccionada.

*bExact*<br/>
TRUE para especificar que el juego de caracteres debe coincidir al seleccionar una fuente; FALSE para especificar que se puede omitir el juego de caracteres al seleccionar una fuente.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha encontrado y seleccionado la fuente especificada; de lo contrario, es cero.

### <a name="remarks"></a>Comentarios

##  <a name="getcharset"></a>  CMFCRibbonFontComboBox::GetCharSet

Devuelve el juego de caracteres especificado.

```
BYTE GetCharSet() const;
```

### <a name="return-value"></a>Valor devuelto

Juego de caracteres (consulte LOGFONT en la documentación de Windows SDK).

### <a name="remarks"></a>Comentarios

##  <a name="getfonttype"></a>  CMFCRibbonFontComboBox::GetFontType

Devuelve los tipos de fuente que se van a mostrar en el cuadro combinado. Las opciones válidas son DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE o cualquier combinación bit a bit de estas.

```
int GetFontType() const;
```

### <a name="return-value"></a>Valor devuelto

Tipos de fuentes (consulte EnumFontFamProc en la documentación de Windows SDK).

### <a name="remarks"></a>Comentarios

##  <a name="getpitchandfamily"></a>  CMFCRibbonFontComboBox::GetPitchAndFamily

Devuelve el paso y la familia de las fuentes que se muestran en el cuadro combinado.

```
BYTE GetPitchAndFamily() const;
```

### <a name="return-value"></a>Valor devuelto

El paso y la familia (consulte LOGFONT en la documentación de Windows SDK).

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonComboBox (clase)](../../mfc/reference/cmfcribboncombobox-class.md)
