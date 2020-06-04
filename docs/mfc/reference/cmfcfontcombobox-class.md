---
title: CMFCFontComboBox (Clase)
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
ms.openlocfilehash: 60b4b7cdfdace2332de35dd93c43eacf592e99e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367500"
---
# <a name="cmfcfontcombobox-class"></a>CMFCFontComboBox (Clase)

La `CMFCFontComboBox` clase crea un control de cuadro combinado que contiene una lista de fuentes.

## <a name="syntax"></a>Sintaxis

```
class CMFCFontComboBox : public CComboBox
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCFontComboBox::CMFCFontComboBox](#cmfcfontcombobox)|Construye un objeto `CMFCFontComboBox`.|
|`CMFCFontComboBox::~CMFCFontComboBox`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|`CMFCFontComboBox::CompareItem`|Llamado por el marco de trabajo para determinar la posición relativa de un nuevo elemento en el cuadro de lista ordenado del control de cuadro combinado de fuente actual. (Reemplaza [CComboBox::CompareItem](../../mfc/reference/ccombobox-class.md#compareitem).)|
|`CMFCFontComboBox::DrawItem`|Llamado por el marco de trabajo para dibujar un elemento especificado en el control de cuadro combinado de fuente actual. (Reemplaza [CComboBox::DrawItem](../../mfc/reference/ccombobox-class.md#drawitem).)|
|[CMFCFontComboBox::GetSelFont](#getselfont)|Recupera información sobre la fuente seleccionada actualmente.|
|`CMFCFontComboBox::MeasureItem`|Llamado por el marco de trabajo para informar a Windows de las dimensiones del cuadro de lista en el control de cuadro combinado de fuente actual. (Reemplaza [CComboBox::MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem).)|
|`CMFCFontComboBox::PreTranslateMessage`|Traduce los mensajes de ventana antes de que se distribuyan a las funciones de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage.](/windows/win32/api/winuser/nf-winuser-dispatchmessage) (Invalida [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)).|
|[CMFCFontComboBox::SelectFont](#selectfont)|Selecciona la fuente que coincide con los criterios especificados en el cuadro combinado de fuentes.|
|[CMFCFontComboBox::Setup](#setup)|Inicializa la lista de elementos en el cuadro combinado de fuentes.|

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|Indica al marco de trabajo qué fuente utilizar para dibujar las etiquetas de elemento en el cuadro combinado de fuente actual.|

## <a name="remarks"></a>Observaciones

Para utilizar `CMFCFontComboBox` un objeto en un `CMFCFontComboBox` cuadro de diálogo, agregue una variable a la clase de cuadro de diálogo. A continuación, en el `OnInitDialog` método de la clase de cuadro de diálogo, llame a la [CMFCFontComboBox::Setup](#setup) método para inicializar la lista de elementos en el control de cuadro combinado.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

[CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxfontcombobox.h

## <a name="cmfcfontcomboboxcmfcfontcombobox"></a><a name="cmfcfontcombobox"></a>CMFCFontComboBox::CMFCFontComboBox

Construye un objeto `CMFCFontComboBox`.

```
CMFCFontComboBox();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcfontcomboboxgetselfont"></a><a name="getselfont"></a>CMFCFontComboBox::GetSelFont

Recupera información sobre la fuente seleccionada actualmente.

```
CMFCFontInfo* GetSelFont() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a [CMFCFontInfo clase](../../mfc/reference/cmfcfontinfo-class.md) objeto que describe una fuente. Puede ser NULL si no se selecciona ninguna fuente en el cuadro combinado.

### <a name="remarks"></a>Observaciones

## <a name="cmfcfontcomboboxm_bdrawusingfont"></a><a name="m_bdrawusingfont"></a>CMFCFontComboBox::m_bDrawUsingFont

Indica al marco de trabajo qué fuente utilizar para dibujar las etiquetas de elemento en el cuadro combinado de fuente actual.

```
static BOOL m_bDrawUsingFont;
```

### <a name="remarks"></a>Observaciones

Establezca este miembro en TRUE para dirigir el marco de trabajo para usar la misma fuente para dibujar cada etiqueta de elemento. Establezca este miembro en FALSE para dirigir el marco de trabajo para dibujar cada etiqueta de elemento con la fuente cuyo nombre es el mismo que la etiqueta. El valor predeterminado de este miembro es FALSE.

## <a name="cmfcfontcomboboxselectfont"></a><a name="selectfont"></a>CMFCFontComboBox::SelectFont

Selecciona la fuente que coincide con los criterios especificados en el cuadro combinado de fuentes.

```
BOOL SelectFont(CMFCFontInfo* pDesc);

BOOL SelectFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET);
```

### <a name="parameters"></a>Parámetros

*pDesc*<br/>
[en] Apunta a un objeto de descripción de fuente.

*lpszName*<br/>
[en] Especifica un nombre de fuente.

*nCharSet*<br/>
[en] Especifica un juego de caracteres. El valor predeterminado es DEFAULT_CHARSET. Para obtener más `lfCharSet` información, consulte el miembro de la [estructura LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

### <a name="return-value"></a>Valor devuelto

TRUESi un elemento del cuadro combinado de fuentes coincide con el objeto de descripción de fuente especificado o el nombre de fuente y el conjunto de caracteres; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Utilice este método para seleccionar y desplazarse hasta el elemento del cuadro combinado de fuentes que corresponde a la fuente especificada.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `SelectFont` muestra `CMFCFontComboBox` cómo utilizar el método en la clase. Este ejemplo forma parte del [ejemplo Nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]

## <a name="cmfcfontcomboboxsetup"></a><a name="setup"></a>CMFCFontComboBox::Setup

Inicializa la lista de elementos en el cuadro combinado de fuentes.

```
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,
    BYTE nCharSet=DEFAULT_CHARSET,
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```

### <a name="parameters"></a>Parámetros

*nFontType*<br/>
[en] Especifica el tipo de fuente. El valor predeterminado es la combinación bit a bit (OR) de DEVICE_FONTTYPE, RASTER_FONTTYPE y TRUETYPE_FONTTYPE.

*nCharSet*<br/>
[en] Especifica el juego de caracteres de fuente. El valor predeterminado es DEFAULT_CHARSET.

*nPitchAndFamily*<br/>
[en] Especifica el tono de fuente y la familia. El valor predeterminado es DEFAULT_PITCH.

### <a name="return-value"></a>Valor devuelto

TRUESi el cuadro combinado de fuente se inicializó correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método inicializa el cuadro combinado de fuentes enumerando las fuentes instaladas actualmente que coinciden con los parámetros especificados e insertando esos nombres de fuente en el cuadro combinado de fuentes.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `Setup` muestra `CMFCFontComboBox` cómo utilizar el método en la clase. Este ejemplo forma parte del [ejemplo Nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox (Clase)](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCFontInfo (Clase)](../../mfc/reference/cmfcfontinfo-class.md)
