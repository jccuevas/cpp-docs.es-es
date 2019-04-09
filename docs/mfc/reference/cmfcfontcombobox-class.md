---
title: CMFCFontComboBox (clase)
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
ms.openlocfilehash: ccc4e545b2274d6dbb9989cfb9c047de819b8d32
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781307"
---
# <a name="cmfcfontcombobox-class"></a>CMFCFontComboBox (clase)

La `CMFCFontComboBox` clase crea un control de cuadro combinado que contiene una lista de fuentes.

## <a name="syntax"></a>Sintaxis

```
class CMFCFontComboBox : public CComboBox
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCFontComboBox::CMFCFontComboBox](#cmfcfontcombobox)|Construye un objeto `CMFCFontComboBox`.|
|`CMFCFontComboBox::~CMFCFontComboBox`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|`CMFCFontComboBox::CompareItem`|Lo llama el marco de trabajo para determinar la posición relativa de un nuevo elemento en el cuadro de lista ordenada del control de cuadro de cuadro combinado de fuente actual. (Invalida [CComboBox::CompareItem](../../mfc/reference/ccombobox-class.md#compareitem).)|
|`CMFCFontComboBox::DrawItem`|Lo llama el marco de trabajo para dibujar un elemento especificado en el control de cuadro de cuadro combinado de fuente actual. (Invalida [CComboBox::DrawItem](../../mfc/reference/ccombobox-class.md#drawitem).)|
|[CMFCFontComboBox::GetSelFont](#getselfont)|Recupera información acerca de la fuente seleccionada actualmente.|
|`CMFCFontComboBox::MeasureItem`|Lo llama el marco de trabajo para informar a Windows de las dimensiones del cuadro de lista en el control de cuadro de cuadro combinado de fuente actual. (Invalida [CComboBox::MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem).)|
|`CMFCFontComboBox::PreTranslateMessage`|Traduce los mensajes de ventana antes de enviarlos a la [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funciones de Windows. (Invalida [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)).|
|[CMFCFontComboBox::SelectFont](#selectfont)|Selecciona la fuente que coincide con los criterios especificados en el cuadro combinado de fuente.|
|[CMFCFontComboBox::Setup](#setup)|Inicializa la lista de elementos en el cuadro combinado de fuente.|

### <a name="data-members"></a>Miembros de datos

|Name|Descripción|
|----------|-----------------|
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|Indica qué fuente se utiliza para dibujar las etiquetas de elemento en el cuadro combinado de fuente actual para el marco de trabajo.|

## <a name="remarks"></a>Comentarios

Para usar un `CMFCFontComboBox` objetos en un cuadro de diálogo, agregar un `CMFCFontComboBox` variable a la clase de cuadro de diálogo. A continuación, en el `OnInitDialog` método de la clase de cuadro de diálogo, llamada la [CMFCFontComboBox::Setup](#setup) método para inicializar la lista de elementos en el control de cuadro combinado.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

[CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxfontcombobox.h

##  <a name="cmfcfontcombobox"></a>  CMFCFontComboBox::CMFCFontComboBox

Construye un objeto `CMFCFontComboBox`.

```
CMFCFontComboBox();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getselfont"></a>  CMFCFontComboBox::GetSelFont

Recupera información acerca de la fuente seleccionada actualmente.

```
CMFCFontInfo* GetSelFont() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a [CMFCFontInfo (clase)](../../mfc/reference/cmfcfontinfo-class.md) objeto que describe una fuente. Puede ser NULL si no se selecciona ninguna fuente en el cuadro combinado.

### <a name="remarks"></a>Comentarios

##  <a name="m_bdrawusingfont"></a>  CMFCFontComboBox::m_bDrawUsingFont

Indica qué fuente se utiliza para dibujar las etiquetas de elemento en el cuadro combinado de fuente actual para el marco de trabajo.

```
static BOOL m_bDrawUsingFont;
```

### <a name="remarks"></a>Comentarios

Este miembro se establece en TRUE para indicar al marco que use la misma fuente para dibujar cada etiqueta de elemento. Este miembro se establece en FALSE para dirigir el marco de trabajo para dibujar cada etiqueta de elemento con la fuente cuyo nombre es el mismo que la etiqueta. El valor predeterminado de este miembro es FALSE.

##  <a name="selectfont"></a>  CMFCFontComboBox::SelectFont

Selecciona la fuente que coincide con los criterios especificados en el cuadro combinado de fuente.

```
BOOL SelectFont(CMFCFontInfo* pDesc);

BOOL SelectFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET);
```

### <a name="parameters"></a>Parámetros

*pDesc*<br/>
[in] Apunta a un objeto de descripción de la fuente.

*lpszName*<br/>
[in] Especifica un nombre de fuente.

*nCharSet*<br/>
[in] Especifica un juego de caracteres. El valor predeterminado es DEFAULT_CHARSET. Para obtener más información, consulte el `lfCharSet` miembro de la [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) estructura.

### <a name="return-value"></a>Valor devuelto

TRUE si un elemento en el cuadro combinado de fuente que coincide con el objeto de descripción de la fuente especificada o el nombre de la fuente y el juego de caracteres; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Utilice este método para seleccionar y desplácese hasta el elemento en el cuadro combinado de fuente que corresponde a la fuente especificada.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar el `SelectFont` método en el `CMFCFontComboBox` clase. Este ejemplo forma parte de la [ejemplo de controles nuevos](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]

##  <a name="setup"></a>  CMFCFontComboBox::Setup

Inicializa la lista de elementos en el cuadro combinado de fuente.

```
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,
    BYTE nCharSet=DEFAULT_CHARSET,
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```

### <a name="parameters"></a>Parámetros

*nFontType*<br/>
[in] Especifica el tipo de fuente. El valor predeterminado es la combinación bit a bit (OR) de DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE.

*nCharSet*<br/>
[in] Especifica el juego de caracteres de la fuente. El valor predeterminado es DEFAULT_CHARSET.

*nPitchAndFamily*<br/>
[in] Especifica el paso de la fuente y la familia. El valor predeterminado es DEFAULT_PITCH.

### <a name="return-value"></a>Valor devuelto

TRUE si el cuadro combinado de fuente se inicializó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método inicializa el cuadro combinado de fuente al enumerar las fuentes instaladas actualmente que coinciden con los parámetros especificados y la inserción de los nombres de fuente en el cuadro combinado de fuente.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar el `Setup` método en el `CMFCFontComboBox` clase. Este ejemplo forma parte de la [ejemplo de controles nuevos](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox (clase)](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCFontInfo (clase)](../../mfc/reference/cmfcfontinfo-class.md)
