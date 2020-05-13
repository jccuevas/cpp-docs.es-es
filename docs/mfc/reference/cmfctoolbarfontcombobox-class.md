---
title: CMFCToolBarFontComboBox (Clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::GetFontDesc
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::SetFont
helpviewer_keywords:
- CMFCToolBarFontComboBox [MFC], CMFCToolBarFontComboBox
- CMFCToolBarFontComboBox [MFC], GetFontDesc
- CMFCToolBarFontComboBox [MFC], SetFont
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
ms.openlocfilehash: 7b31f4b725a6983171162d9805d08224ad787808
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360460"
---
# <a name="cmfctoolbarfontcombobox-class"></a>CMFCToolBarFontComboBox (Clase)

Botón de barra de herramientas que contiene un control de cuadro combinado que permite al usuario seleccionar una fuente de una lista de fuentes del sistema.

## <a name="syntax"></a>Sintaxis

```
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|Construye un objeto `CMFCToolBarFontComboBox`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|Devuelve un puntero `CMFCFontInfo` al objeto para un índice especificado en el cuadro combinado.|
|[CMFCToolBarFontComboBox::SetFont](#setfont)|Selecciona una fuente en el cuadro combinado de fuentes según el nombre de la fuente o el prefijo y el juego de caracteres de la fuente.|

### <a name="data-members"></a>Miembros de datos

[CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)<br/>
La altura de los caracteres del cuadro combinado de fuentes.

## <a name="remarks"></a>Observaciones

Para agregar un botón de cuadro combinado de fuente a una barra de herramientas, siga estos pasos:

1. Reserve un id. de recurso ficticio para el botón en el recurso primario de la barra de herramientas.

1. Construir `CMFCToolBarFontComboBox` un objeto.

1. En el controlador de mensajes que procesa el mensaje de AFX_WM_RESETTOOLBAR, reemplace el botón original por el nuevo botón de cuadro combinado mediante [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

1. Sincronizar la fuente seleccionada en el cuadro combinado con la fuente en el documento mediante el [CMFCToolBarFontComboBox::SetFont](#setfont) método.

Para sincronizar la fuente del documento con la fuente seleccionada en el cuadro combinado, utilice el [CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc) método para recuperar los atributos de la fuente seleccionada y utilizar esos atributos para crear un [CFont Clase](../../mfc/reference/cfont-class.md) objeto.

El botón del cuadro combinado de fuentes llama a la función [Win32 EnumFontFamiliesEx](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesexw) para determinar las fuentes de pantalla e impresora disponibles para el sistema.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtoolbarfontcombobox.h

## <a name="cmfctoolbarfontcomboboxcmfctoolbarfontcombobox"></a><a name="cmfctoolbarfontcombobox"></a>CMFCToolBarFontComboBox::CMFCToolBarFontComboBox

Construye un [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) objeto.

```
public:
CMFCToolBarFontComboBox(
    UINT uiID,
    int iImage,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    DWORD dwStyle = CBS_DROPDOWN,
    int iWidth = 0,
    BYTE nPitchAndFamily = DEFAULT_PITCH);

protected:
CMFCToolBarFontComboBox(
    CObList* pLstFontsExternal,
    int nFontType,
    BYTE nCharSet,
    BYTE nPitchAndFamily);

CMFCToolBarFontComboBox();
```

### <a name="parameters"></a>Parámetros

*uiID*<br/>
[en] El identificador de comando del cuadro combinado.

*iImage*<br/>
[en] El índice de base cero de una imagen de barra de herramientas. La imagen se encuentra en el [CMFCToolBarImages clase](../../mfc/reference/cmfctoolbarimages-class.md) objeto que [CMFCToolBar clase](../../mfc/reference/cmfctoolbar-class.md) mantiene.

*nFontType*<br/>
[en] Los tipos de fuentes que contiene el cuadro combinado. Este parámetro puede ser una combinación (booleano OR) de los siguientes valores:

DEVICE_FONTTYPE

RASTER_FONTTYPE

TRUETYPE_FONTTYPE

*nCharSet*<br/>
[en] Si se establece en DEFAULT_CHARSET, el cuadro combinado contiene todas las fuentes con nombre único en todos los conjuntos de caracteres. (Si hay dos fuentes con el mismo nombre, el cuadro combinado contiene una de ellas.) Si se establece en un valor de conjunto de caracteres válido, el cuadro combinado contiene solo las fuentes del juego de caracteres especificado. Consulte [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) para obtener una lista de posibles conjuntos de caracteres.

*dwStyle*<br/>
[en] El estilo del cuadro combinado. (consulte [Estilos de cuadro combinado](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))

*iWidth*<br/>
[en] El ancho en píxeles del control de edición.

*nPitchAndFamily*<br/>
[en] Si se establece en DEFAULT_PITCH, el cuadro combinado contiene fuentes independientemente del tono. Si se establece en FIXED_PITCH o VARIABLE_PITCH, el cuadro combinado solo contiene fuentes con ese tipo de tono. Actualmente no se admite el filtrado basado en la familia de fuentes.

*pLstFontsExternal*<br/>
[fuera] Puntero a un [CObList Clase](../../mfc/reference/coblist-class.md) objeto que almacena las fuentes disponibles.

### <a name="remarks"></a>Observaciones

Normalmente, `CMFCToolBarFontComboBox` los objetos almacenan la `CObList` lista de fuentes disponibles en un único objeto compartido. Si utiliza la segunda sobrecarga del constructor y proporciona un puntero válido `CMFCToolBarFontComboBox` a *pLstFontsExternal*, ese objeto rellenará en su lugar el `CObList` que *pLstFontsExternal* apunta con las fuentes disponibles.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `CMFCToolBarFontComboBox` muestra cómo construir un objeto. Este fragmento de código forma parte del [ejemplo de WordPad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]

## <a name="cmfctoolbarfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a>CMFCToolBarFontComboBox::GetFontDesc

Devuelve un puntero `CMFCFontInfo` al objeto para un índice especificado en el cuadro combinado.

```
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
[en] Especifica el índice de base cero de un elemento de cuadro combinado.

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto `CMFCFontInfo` . Si *iIndex* no especifica un índice de elemento válido, el valor devuelto es NULL.

## <a name="cmfctoolbarfontcomboboxm_nfontheight"></a><a name="m_nfontheight"></a>CMFCToolBarFontComboBox::m_nFontHeight

Especifica la altura, en píxeles, de los caracteres del cuadro combinado de fuentes si el cuadro combinado tiene estilo de dibujo propietario.

```
static int m_nFontHeight
```

### <a name="remarks"></a>Observaciones

Si `m_nFontHeight` la variable es 0, la altura se calcula automáticamente según la fuente predeterminada del cuadro combinado. La altura incluye tanto el ascenso de caracteres por encima de la línea base como el descenso de caracteres debajo de la línea base.

## <a name="cmfctoolbarfontcomboboxsetfont"></a><a name="setfont"></a>CMFCToolBarFontComboBox::SetFont

Selecciona la fuente en el cuadro combinado de fuentes según el nombre de fuente y el juego de caracteres que se especifican en los parámetros.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET,
    BOOL bExact=FALSE);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
[en] Especifica el nombre o prefijo de fuente.

*nCharSet*<br/>
[en] Especifica el juego de caracteres.

*bExact*<br/>
[en] Especifica si *lpszName* contiene el nombre de fuente o el prefijo de fuente.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la fuente se seleccionó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si *bExact* es TRUE, este método selecciona una fuente que coincide exactamente con el nombre especificado como *lpszName*. Si *bExact* es FALSE, este método selecciona una fuente que comienza con el texto especificado como *lpszName* y que utiliza el juego de caracteres que especificó como *nCharSet*. Si *nCharSet* se establece en DEFAULT_CHARSET, se omitirá el juego de caracteres y solo *lpszName* se usará para seleccionar una fuente.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar (Clase)](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton (clase)](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton (Clase)](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo (Clase)](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)
