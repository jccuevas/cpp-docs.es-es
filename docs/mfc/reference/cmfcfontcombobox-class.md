---
title: Clase CMFCFontComboBox
ms.date: 11/04/2016
f1_keywords:
- CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::GetSelFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::SelectFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::Setup
- AFXFONTCOMBOBOX/CMFCFontComboBox::m_bDrawUsingFont
helpviewer_keywords:
- CMFCFontComboBox [MFC], CMFCFontComboBox
- CMFCFontComboBox [MFC], GetSelFont
- CMFCFontComboBox [MFC], SelectFont
- CMFCFontComboBox [MFC], Setup
- CMFCFontComboBox [MFC], m_bDrawUsingFont
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
ms.openlocfilehash: 69e8f81e7e01d0610f3cbf88ac1725a21d59838f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505297"
---
# <a name="cmfcfontcombobox-class"></a>Clase CMFCFontComboBox

La `CMFCFontComboBox` clase crea un control de cuadro combinado que contiene una lista de fuentes.

## <a name="syntax"></a>Sintaxis

```
class CMFCFontComboBox : public CComboBox
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCFontComboBox::CMFCFontComboBox](#cmfcfontcombobox)|Construye un objeto `CMFCFontComboBox`.|
|`CMFCFontComboBox::~CMFCFontComboBox`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|`CMFCFontComboBox::CompareItem`|Lo llama el marco de trabajo para determinar la posición relativa de un nuevo elemento en el cuadro de lista ordenado del control de cuadro combinado de fuente actual. (Invalida [CComboBox:: CompareItem](../../mfc/reference/ccombobox-class.md#compareitem)).|
|`CMFCFontComboBox::DrawItem`|Lo llama el marco de trabajo para dibujar un elemento especificado en el control de cuadro combinado de fuente actual. (Invalida [CComboBox::D rawitem](../../mfc/reference/ccombobox-class.md#drawitem)).|
|[CMFCFontComboBox::GetSelFont](#getselfont)|Recupera información sobre la fuente seleccionada actualmente.|
|`CMFCFontComboBox::MeasureItem`|Lo llama el marco de trabajo para informar a las ventanas de las dimensiones del cuadro de lista en el control de cuadro combinado de fuente actual. (Invalida [CComboBox:: MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem)).|
|`CMFCFontComboBox::PreTranslateMessage`|Traduce los mensajes de ventana antes de que se envíen a las funciones de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . (Invalida [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)).|
|[CMFCFontComboBox::SelectFont](#selectfont)|Selecciona la fuente que coincide con los criterios especificados del cuadro combinado de fuente.|
|[CMFCFontComboBox::Setup](#setup)|Inicializa la lista de elementos del cuadro combinado de fuente.|

### <a name="data-members"></a>Miembros de datos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|Indica al marco de trabajo qué fuente se va a utilizar para dibujar las etiquetas de elemento en el cuadro combinado de fuente actual.|

## <a name="remarks"></a>Comentarios

Para usar un `CMFCFontComboBox` objeto en un cuadro de diálogo, agregue `CMFCFontComboBox` una variable a la clase de cuadro de diálogo. Después, en `OnInitDialog` el método de la clase de cuadro de diálogo, llame al método [CMFCFontComboBox:: Setup](#setup) para inicializar la lista de elementos del control de cuadro combinado.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

[CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxfontcombobox. h

##  <a name="cmfcfontcombobox"></a>  CMFCFontComboBox::CMFCFontComboBox

Construye un objeto `CMFCFontComboBox`.

```
CMFCFontComboBox();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getselfont"></a>  CMFCFontComboBox::GetSelFont

Recupera información sobre la fuente seleccionada actualmente.

```
CMFCFontInfo* GetSelFont() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto de la [clase CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md) que describe una fuente. Puede ser NULL si no hay ninguna fuente seleccionada en el cuadro combinado.

### <a name="remarks"></a>Comentarios

##  <a name="m_bdrawusingfont"></a>  CMFCFontComboBox::m_bDrawUsingFont

Indica al marco de trabajo qué fuente se va a utilizar para dibujar las etiquetas de elemento en el cuadro combinado de fuente actual.

```
static BOOL m_bDrawUsingFont;
```

### <a name="remarks"></a>Comentarios

Establezca este miembro en TRUE para indicar al marco de trabajo que use la misma fuente para dibujar cada etiqueta de elemento. Establezca este miembro en FALSE para indicar al marco de trabajo que dibuje cada etiqueta de elemento con la fuente cuyo nombre es el mismo que el de la etiqueta. El valor predeterminado de este miembro es FALSE.

##  <a name="selectfont"></a>  CMFCFontComboBox::SelectFont

Selecciona la fuente que coincide con los criterios especificados del cuadro combinado de fuente.

```
BOOL SelectFont(CMFCFontInfo* pDesc);

BOOL SelectFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET);
```

### <a name="parameters"></a>Parámetros

*pDesc*<br/>
de Apunta a un objeto de descripción de fuente.

*lpszName*<br/>
de Especifica un nombre de fuente.

*nCharSet*<br/>
de Especifica un juego de caracteres. El valor predeterminado es DEFAULT_CHARSET. Para obtener más información, vea `lfCharSet` el miembro de la estructura [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

### <a name="return-value"></a>Valor devuelto

TRUE si un elemento del cuadro combinado de fuente coincide con el nombre de fuente o el objeto de descripción de fuente especificado, y con el juego de caracteres. en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Utilice este método para seleccionar y desplazarse hasta el elemento del cuadro combinado de fuente que corresponde a la fuente especificada.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar `SelectFont` el método en `CMFCFontComboBox` la clase. Este ejemplo forma parte del [ejemplo de nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]

##  <a name="setup"></a>  CMFCFontComboBox::Setup

Inicializa la lista de elementos del cuadro combinado de fuente.

```
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,
    BYTE nCharSet=DEFAULT_CHARSET,
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```

### <a name="parameters"></a>Parámetros

*nFontType*<br/>
de Especifica el tipo de fuente. El valor predeterminado es la combinación bit a bit (o) de DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE.

*nCharSet*<br/>
de Especifica el juego de caracteres de la fuente. El valor predeterminado es DEFAULT_CHARSET.

*nPitchAndFamily*<br/>
de Especifica el extremo y la familia de la fuente. El valor predeterminado es DEFAULT_PITCH.

### <a name="return-value"></a>Valor devuelto

TRUE si el cuadro combinado de fuente se inicializó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método inicializa el cuadro combinado de fuente enumerando las fuentes actualmente instaladas que coinciden con los parámetros especificados e insertando esos nombres de fuente en el cuadro combinado de fuente.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar `Setup` el método en `CMFCFontComboBox` la clase. Este ejemplo forma parte del [ejemplo de nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox (clase)](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCFontInfo (clase)](../../mfc/reference/cmfcfontinfo-class.md)
