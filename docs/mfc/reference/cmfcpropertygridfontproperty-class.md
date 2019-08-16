---
title: Clase CMFCPropertyGridFontProperty
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
ms.openlocfilehash: a3c5b806482a97d64a9ffab92877781cb8778b6b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505121"
---
# <a name="cmfcpropertygridfontproperty-class"></a>Clase CMFCPropertyGridFontProperty

La `CMFCPropertyGridFileProperty` clase admite un elemento de control de la lista de propiedades que abre un cuadro de diálogo de selección de fuente.

## <a name="syntax"></a>Sintaxis

```
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|Construye un objeto `CMFCPropertyGridFontProperty`.|
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|`CMFCPropertyGridFontProperty::FormatProperty`|Da formato a la representación de texto de un valor de propiedad. (Invalida [CMFCPropertyGridProperty:: FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty)).|
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|Recupera el color de fuente que el usuario selecciona en el cuadro de diálogo fuente.|
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|Recupera la fuente que el usuario selecciona en el cuadro de diálogo fuente.|
|`CMFCPropertyGridFontProperty::GetThisClass`|Lo usa el marco de trabajo para obtener un puntero al objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|
|`CMFCPropertyGridFontProperty::OnClickButton`|Lo llama el marco cuando el usuario hace clic en un botón que se encuentra en una propiedad. (Invalida [CMFCPropertyGridProperty:: OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton)).|

## <a name="remarks"></a>Comentarios

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxpropertygridctrl. h

##  <a name="cmfcpropertygridfontproperty"></a>  CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty

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
de Nombre de la propiedad.

*lf*<br/>
de Una estructura de fuente lógica que especifica los atributos de la fuente.

*dwFontDialogFlags*<br/>
de Estilos que se aplican al cuadro de diálogo fuente que se muestra al hacer clic en el botón desplegable valor de propiedad. El valor predeterminado es la combinación bit a bit (o) de CF_EFFECTS y CF_SCREENFONTS. Para obtener más información, vea el parámetro flags de la [estructura CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw).

*lpszDescr*<br/>
de Descripción de la propiedad Font. El valor predeterminado es NULL.

*dwData*<br/>
de Datos específicos de la aplicación, como un entero o un puntero a otros datos asociados a la propiedad. El valor predeterminado es 0.

*color*<br/>
de Color de la fuente. El valor predeterminado es el color predeterminado.

### <a name="remarks"></a>Comentarios

Un `CMFCPropertyGridFontProperty` objeto representa una propiedad de fuente en un control de fuente de la cuadrícula de propiedades.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto `CMFCPropertyGridFontProperty` de la clase. Este ejemplo forma parte del [ejemplo de nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]

##  <a name="getcolor"></a>  CMFCPropertyGridFontProperty::GetColor

Recupera el color de fuente que el usuario selecciona en el cuadro de diálogo fuente.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de color RGB que representa el color de fuente seleccionado.

### <a name="remarks"></a>Comentarios

##  <a name="getlogfont"></a>  CMFCPropertyGridFontProperty::GetLogFont

Recupera la fuente que el usuario selecciona en el cuadro de diálogo fuente.

```
LPLOGFONT GetLogFont();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una estructura [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) que describe la fuente seleccionada.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl (clase)](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty (clase)](../../mfc/reference/cmfcpropertygridproperty-class.md)
