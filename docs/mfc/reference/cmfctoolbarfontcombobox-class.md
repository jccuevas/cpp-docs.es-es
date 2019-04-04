---
title: CMFCToolBarFontComboBox (clase)
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
ms.openlocfilehash: 89767a3ed6880703c3c754700ea5669c0cc183e5
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58779201"
---
# <a name="cmfctoolbarfontcombobox-class"></a>CMFCToolBarFontComboBox (clase)

Un botón de barra de herramientas que contiene un control de cuadro combinado que permite al usuario seleccionar una fuente de una lista de fuentes del sistema.

## <a name="syntax"></a>Sintaxis

```
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Name|Descripción|
|----------|-----------------|
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|Construye un objeto `CMFCToolBarFontComboBox`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|Devuelve un puntero a la `CMFCFontInfo` objeto para un índice especificado en el cuadro combinado.|
|[CMFCToolBarFontComboBox::SetFont](#setfont)|Selecciona una fuente en el cuadro combinado de fuente según ya sea el nombre de la fuente o el conjunto de prefijo y el carácter de la fuente.|

### <a name="data-members"></a>Miembros de datos

[CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)<br/>
El alto de los caracteres en el cuadro combinado de fuente.

## <a name="remarks"></a>Comentarios

Para agregar un botón de cuadro combinado de fuente a una barra de herramientas, siga estos pasos:

1. Reserve un id. de recurso ficticio para el botón en el recurso primario de la barra de herramientas.

1. Construir un `CMFCToolBarFontComboBox` objeto.

1. En el controlador de mensajes que procesa el mensaje AFX_WM_RESETTOOLBAR, reemplazar el botón original con el nuevo botón de cuadro combinado mediante [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

1. Sincronizar la fuente que está seleccionada en el cuadro combinado con la fuente en el documento mediante el uso de la [CMFCToolBarFontComboBox::SetFont](#setfont) método.

Para sincronizar la fuente del documento con la fuente seleccionada en el cuadro combinado, utilice el [CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc) método para recuperar los atributos de la fuente seleccionada y usar esos atributos para crear un [ CFont (clase)](../../mfc/reference/cfont-class.md) objeto.

El botón de cuadro combinado de fuente llama a la función de Win32 [EnumFontFamiliesEx](/windows/desktop/api/wingdi/nf-wingdi-enumfontfamiliesexa) para determinar las fuentes de pantalla y la impresora disponibles en el sistema.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtoolbarfontcombobox.h

##  <a name="cmfctoolbarfontcombobox"></a>  CMFCToolBarFontComboBox::CMFCToolBarFontComboBox

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
[in] El identificador de comando del cuadro combinado.

*iImage*<br/>
[in] Índice de base cero de una imagen de la barra de herramientas. La imagen se encuentra en la [CMFCToolBarImages (clase)](../../mfc/reference/cmfctoolbarimages-class.md) objeto que [CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md) clase mantiene.

*nFontType*<br/>
[in] Los tipos de fuentes que contiene el cuadro combinado. Este parámetro puede ser una combinación (booleano OR) de los siguientes valores:

DEVICE_FONTTYPE

RASTER_FONTTYPE

TRUETYPE_FONTTYPE

*nCharSet*<br/>
[in] Si el conjunto a DEFAULT_CHARSET, el cuadro combinado contiene todos los nombra fuentes en todos los juegos de caracteres. (Si hay dos fuentes con el mismo nombre, el cuadro combinado contiene uno de ellos). Si se establece en un valor de conjunto de caracteres válido, el cuadro combinado contenga solo fuentes en el juego de caracteres especificado. Consulte [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) establece una lista de caracteres posible.

*dwStyle*<br/>
[in] El estilo del cuadro combinado. (consulte [estilos de cuadro combinado](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))

*iWidth*<br/>
[in] El ancho en píxeles del control de edición.

*nPitchAndFamily*<br/>
[in] Si establece en DEFAULT_PITCH, el cuadro combinado contiene fuentes independientemente de tono. Si se establece en FIXED_PITCH o VARIABLE_PITCH, el cuadro combinado contiene sólo las fuentes con ese tipo de paso. Actualmente no se admite el filtrado basado en la familia de fuentes.

*pLstFontsExternal*<br/>
[out] Puntero a un [CObList (clase)](../../mfc/reference/coblist-class.md) objeto que almacena las fuentes disponibles.

### <a name="remarks"></a>Comentarios

Por lo general, `CMFCToolBarFontComboBox` objetos almacenan la lista de fuentes disponibles en una única compartida `CObList` objeto. Si usa la segunda sobrecarga del constructor y proporcionar un puntero válido a *pLstFontsExternal*, que `CMFCToolBarFontComboBox` objeto en su lugar, se rellenará el `CObList` que *pLstFontsExternal* señala con fuentes disponibles.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un `CMFCToolBarFontComboBox` objeto. Este fragmento de código forma parte del [ejemplo de WordPad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]

##  <a name="getfontdesc"></a>  CMFCToolBarFontComboBox::GetFontDesc

Devuelve un puntero a la `CMFCFontInfo` objeto para un índice especificado en el cuadro combinado.

```
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
[in] Especifica el índice de base cero de un elemento de cuadro combinado.

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto `CMFCFontInfo` . Si *iÍndice* no especifica un índice de elemento válido, el valor devuelto es NULL.

##  <a name="m_nfontheight"></a>  CMFCToolBarFontComboBox::m_nFontHeight

Especifica el alto, en píxeles, de caracteres en el cuadro combinado de fuente si el cuadro combinado tiene propietario del estilo de dibujo.

```
static int m_nFontHeight
```

### <a name="remarks"></a>Comentarios

Si el `m_nFontHeight` variable es 0, el alto se calcula automáticamente según la fuente predeterminada del cuadro combinado. El alto incluye el ascenso de caracteres por encima de la línea base y el descenso de caracteres debajo de la línea de base.

##  <a name="setfont"></a>  CMFCToolBarFontComboBox::SetFont

Selecciona que la fuente en el cuadro combinado de fuente según el nombre de la fuente y el carácter había establecido que se especifica en los parámetros.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET,
    BOOL bExact=FALSE);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
[in] Especifica el nombre de la fuente o el prefijo.

*nCharSet*<br/>
[in] Especifica el juego de caracteres.

*bExact*<br/>
[in] Especifica si *lpszName* contiene el nombre de fuente o el prefijo de la fuente.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la fuente se ha seleccionado correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Si *bExact* es TRUE, este método selecciona una fuente que coincide exactamente con el nombre que especificó como *lpszName*. Si *bExact* es FALSE, este selecciona método una fuente que se inicia con el texto especificada como *lpszName* y que usa el juego de caracteres que especificó como *nCharSet*. Si *nCharSet* se establece a DEFAULT_CHARSET, será el juego de caracteres omitidos y solo *lpszName* se usará para seleccionar una fuente.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton (clase)](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton (clase)](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo (clase)](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Tutorial: Insertar controles en barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)
