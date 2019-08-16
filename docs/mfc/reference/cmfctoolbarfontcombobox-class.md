---
title: Clase CMFCToolBarFontComboBox
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
ms.openlocfilehash: 7e19fc9257c1fe986ff09a8bbc86bf2fb55af7ee
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504743"
---
# <a name="cmfctoolbarfontcombobox-class"></a>Clase CMFCToolBarFontComboBox

Un botón de la barra de herramientas que contiene un control de cuadro combinado que permite al usuario seleccionar una fuente de una lista de fuentes del sistema.

## <a name="syntax"></a>Sintaxis

```
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|Construye un objeto `CMFCToolBarFontComboBox`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|Devuelve un puntero al `CMFCFontInfo` objeto para un índice especificado en el cuadro combinado.|
|[CMFCToolBarFontComboBox::SetFont](#setfont)|Selecciona una fuente en el cuadro combinado de fuente según el nombre de la fuente, o el prefijo y el juego de caracteres de la fuente.|

### <a name="data-members"></a>Miembros de datos

[CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)<br/>
Alto de los caracteres del cuadro combinado de fuente.

## <a name="remarks"></a>Comentarios

Para agregar un botón de cuadro combinado de fuente a una barra de herramientas, siga estos pasos:

1. Reserve un id. de recurso ficticio para el botón en el recurso primario de la barra de herramientas.

1. Construya un `CMFCToolBarFontComboBox` objeto.

1. En el controlador de mensajes que procesa el mensaje AFX_WM_RESETTOOLBAR, reemplace el botón original por el nuevo botón de cuadro combinado con [CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

1. Sincronizar la fuente seleccionada en el cuadro combinado con la fuente del documento utilizando el método [CMFCToolBarFontComboBox:: SetFont](#setfont) .

Para sincronizar la fuente del documento con la fuente seleccionada en el cuadro combinado, use el método [CMFCToolBarFontComboBox:: GetFontDesc](#getfontdesc) para recuperar los atributos de la fuente seleccionada y use esos atributos para crear un objeto de la [clase Cfont (](../../mfc/reference/cfont-class.md) .

El botón de cuadro combinado fuente llama a la función [EnumFontFamiliesEx](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesexw) de Win32 para determinar las fuentes de pantalla y de impresora disponibles para el sistema.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtoolbarfontcombobox. h

##  <a name="cmfctoolbarfontcombobox"></a>  CMFCToolBarFontComboBox::CMFCToolBarFontComboBox

Construye un objeto [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) .

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
de IDENTIFICADOR del comando del cuadro combinado.

*iImage*<br/>
de Índice de base cero de una imagen de la barra de herramientas. La imagen se encuentra en el objeto de la [clase CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md) que mantiene la clase [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) .

*nFontType*<br/>
de Tipos de fuentes que contiene el cuadro combinado. Este parámetro puede ser una combinación (booleano o) de los siguientes valores:

DEVICE_FONTTYPE

RASTER_FONTTYPE

TRUETYPE_FONTTYPE

*nCharSet*<br/>
de Si se establece en DEFAULT_CHARSET, el cuadro combinado contiene todas las fuentes con nombre único en todos los juegos de caracteres. (Si hay dos fuentes con el mismo nombre, el cuadro combinado contiene una de ellas). Si se establece en un valor de juego de caracteres válido, el cuadro combinado solo contiene fuentes del juego de caracteres especificado. Consulte [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) para obtener una lista de los posibles conjuntos de caracteres.

*dwStyle*<br/>
de Estilo del cuadro combinado. (consulte [estilos de cuadro combinado](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))

*iWidth*<br/>
de Ancho en píxeles del control de edición.

*nPitchAndFamily*<br/>
de Si se establece en DEFAULT_PITCH, el cuadro combinado contiene fuentes sin tener en consideración el paso. Si se establece en FIXED_PITCH o VARIABLE_PITCH, el cuadro combinado solo contiene fuentes con ese tipo de tono. Actualmente no se admite el filtrado basado en la familia de fuentes.

*pLstFontsExternal*<br/>
enuncia Puntero a un objeto de la [clase CObList](../../mfc/reference/coblist-class.md) que almacena las fuentes disponibles.

### <a name="remarks"></a>Comentarios

Normalmente, `CMFCToolBarFontComboBox` los objetos almacenan la lista de fuentes disponibles en un `CObList` solo objeto compartido. Si usa la segunda sobrecarga del constructor y proporciona un puntero válido a *pLstFontsExternal*, ese `CMFCToolBarFontComboBox` objeto rellenará en su lugar la `CObList` *pLstFontsExternal* a la que apunta con las fuentes disponibles.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir `CMFCToolBarFontComboBox` un objeto. Este fragmento de código forma parte del [ejemplo de WordPad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]

##  <a name="getfontdesc"></a>  CMFCToolBarFontComboBox::GetFontDesc

Devuelve un puntero al `CMFCFontInfo` objeto para un índice especificado en el cuadro combinado.

```
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
de Especifica el índice de base cero de un elemento de cuadro combinado.

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto `CMFCFontInfo` . Si *iIndex* no especifica un índice de elemento válido, el valor devuelto es NULL.

##  <a name="m_nfontheight"></a>  CMFCToolBarFontComboBox::m_nFontHeight

Especifica el alto, en píxeles, de los caracteres del cuadro combinado de fuente si el cuadro combinado tiene estilo de dibujo de propietario.

```
static int m_nFontHeight
```

### <a name="remarks"></a>Comentarios

Si la `m_nFontHeight` variable es 0, el alto se calcula automáticamente de acuerdo con la fuente predeterminada del cuadro combinado. El alto incluye el ascenso de caracteres por encima de la línea de base y el descenso de los caracteres situados debajo de la línea base.

##  <a name="setfont"></a>  CMFCToolBarFontComboBox::SetFont

Selecciona la fuente en el cuadro combinado de fuente según el nombre de fuente y el juego de caracteres que se especifican en los parámetros.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET,
    BOOL bExact=FALSE);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
de Especifica el nombre de la fuente o el prefijo.

*nCharSet*<br/>
de Especifica el juego de caracteres.

*bExact*<br/>
de Especifica si *lpszName* contiene el nombre de fuente o el prefijo de fuente.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la fuente se seleccionó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Si *bExact* es true, este método selecciona una fuente que coincide exactamente con el nombre especificado como *lpszName*. Si *bExact* es false, este método selecciona una fuente que empieza con el texto especificado como *lpszName* y que usa el juego de caracteres que especificó como *nCharSet*. Si *nCharSet* se establece en DEFAULT_CHARSET, se omitirá el juego de caracteres y solo se usará *lpszName* para seleccionar una fuente.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton (clase)](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton (clase)](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo (clase)](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)
