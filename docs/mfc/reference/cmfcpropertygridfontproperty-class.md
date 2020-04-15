---
title: CMFCPropertyGridFontProperty (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetLogFont
helpviewer_keywords:
- CMFCPropertyGridFontProperty [MFC], CMFCPropertyGridFontProperty
- CMFCPropertyGridFontProperty [MFC], GetColor
- CMFCPropertyGridFontProperty [MFC], GetLogFont
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
ms.openlocfilehash: a1c9905d8d7f32a049496c4e164c9eaac13455d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361837"
---
# <a name="cmfcpropertygridfontproperty-class"></a>CMFCPropertyGridFontProperty (clase)

La `CMFCPropertyGridFileProperty` clase admite un elemento de control de lista de propiedades que abre un cuadro de diálogo de selección de fuentes.

## <a name="syntax"></a>Sintaxis

```
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|Construye un objeto `CMFCPropertyGridFontProperty`.|
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|`CMFCPropertyGridFontProperty::FormatProperty`|Da formato a la representación de texto de un valor de propiedad. (Reemplaza [CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|Recupera el color de fuente que el usuario selecciona en el cuadro de diálogo de fuente.|
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|Recupera la fuente que el usuario selecciona en el cuadro de diálogo de fuente.|
|`CMFCPropertyGridFontProperty::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|`CMFCPropertyGridFontProperty::OnClickButton`|Lo llama el marco cuando el usuario hace clic en un botón que se encuentra en una propiedad. (Reemplaza [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

## <a name="remarks"></a>Observaciones

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxpropertygridctrl.h

## <a name="cmfcpropertygridfontpropertycmfcpropertygridfontproperty"></a><a name="cmfcpropertygridfontproperty"></a>CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty

Construye un objeto `CMFCPropertyGridFontProperty`.

```
CMFCPropertyGridFontProperty(
    const CString& strName,
    LOGFONT& lf,
    DWORD dwFontDialogFlags = CF_EFFECTS | CF_SCREENFONTS,
    LPCTSTR lpszDescr = NULL,
    DWORD_PTR dwData = 0,
    COLORREF color = (COLORREF)-1);
```

### <a name="parameters"></a>Parámetros

*strName*<br/>
[in] Nombre de la propiedad.

*Si*<br/>
[en] Estructura de fuente lógica que especifica los atributos de la fuente.

*dwFontDialogFlags*<br/>
[en] Estilos que se aplican al cuadro de diálogo de fuente que se muestra al hacer clic en el botón desplegable valor de propiedad. El valor predeterminado es la combinación bit a bit (OR) de CF_EFFECTS y CF_SCREENFONTS. Para obtener más información, consulte el parámetro *Flags* de la [estructura CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw).

*lpszDescr*<br/>
[en] Descripción de la propiedad font. El valor predeterminado es NULL.

*dwData*<br/>
[en] Datos específicos de la aplicación, como un entero o un puntero a otros datos asociados a la propiedad. El valor predeterminado es 0.

*color*<br/>
[en] El color de la fuente. El valor predeterminado es el color predeterminado.

### <a name="remarks"></a>Observaciones

Un `CMFCPropertyGridFontProperty` objeto representa una propiedad de fuente en un control de fuente de cuadrícula de propiedades.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCPropertyGridFontProperty` cómo construir un objeto de la clase. Este ejemplo forma parte del [ejemplo Nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]

## <a name="cmfcpropertygridfontpropertygetcolor"></a><a name="getcolor"></a>CMFCPropertyGridFontProperty::GetColor

Recupera el color de fuente que el usuario selecciona en el cuadro de diálogo de fuente.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de color RGB que representa el color de fuente seleccionado.

### <a name="remarks"></a>Observaciones

## <a name="cmfcpropertygridfontpropertygetlogfont"></a><a name="getlogfont"></a>CMFCPropertyGridFontProperty::GetLogFont

Recupera la fuente que el usuario selecciona en el cuadro de diálogo de fuente.

```
LPLOGFONT GetLogFont();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una estructura [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) que describe la fuente seleccionada.

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl (clase)](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty (Clase)](../../mfc/reference/cmfcpropertygridproperty-class.md)
