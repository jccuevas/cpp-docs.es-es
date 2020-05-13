---
title: CMFCPropertyGridColorProperty Clase
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableAutomaticButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableOtherButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColumnsNumber
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetOriginalValue
helpviewer_keywords:
- CMFCPropertyGridColorProperty [MFC], CMFCPropertyGridColorProperty
- CMFCPropertyGridColorProperty [MFC], EnableAutomaticButton
- CMFCPropertyGridColorProperty [MFC], EnableOtherButton
- CMFCPropertyGridColorProperty [MFC], GetColor
- CMFCPropertyGridColorProperty [MFC], SetColor
- CMFCPropertyGridColorProperty [MFC], SetColumnsNumber
- CMFCPropertyGridColorProperty [MFC], SetOriginalValue
ms.assetid: af37be93-a91e-40a2-9a65-0f3412c6f0f8
ms.openlocfilehash: 393a871a881aa4bddd786b1d4333e02d5e0dbef1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751833"
---
# <a name="cmfcpropertygridcolorproperty-class"></a>CMFCPropertyGridColorProperty Clase

La clase `CMFCPropertyGridColorProperty` admite un elemento de control de la lista de propiedades que abre un cuadro de diálogo de selección de color.

## <a name="syntax"></a>Sintaxis

```
class CMFCPropertyGridColorProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty](#cmfcpropertygridcolorproperty)|Construye un objeto `CMFCPropertyGridColorProperty`.|
|`CMFCPropertyGridColorProperty::~CMFCPropertyGridColorProperty`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](#enableautomaticbutton)|Activa el botón *automático* en el cuadro de diálogo de selección de color. (El botón automático estándar está etiquetado como **Automático**.)|
|[CMFCPropertyGridColorProperty::EnableOtherButton](#enableotherbutton)|Habilita el *otro* botón en el cuadro de diálogo de selección de color. (El otro botón estándar está etiquetado como **Más colores**.)|
|`CMFCPropertyGridColorProperty::FormatProperty`|Da formato a la representación de texto de un valor de propiedad. (Reemplaza [CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFCPropertyGridColorProperty::GetColor](#getcolor)|Obtiene el color actual de la propiedad.|
|`CMFCPropertyGridColorProperty::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|`CMFCPropertyGridColorProperty::OnClickButton`|Lo llama el marco cuando el usuario hace clic en un botón que se encuentra en una propiedad. (Reemplaza [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|
|`CMFCPropertyGridColorProperty::OnDrawValue`|Lo llama el marco para mostrar el valor de la propiedad. (Reemplaza [CMFCPropertyGridProperty::OnDrawValue](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue).)|
|`CMFCPropertyGridColorProperty::OnEdit`|Lo llama el marco cuando el usuario está a punto de modificar un valor de propiedad. (Reemplaza [CMFCPropertyGridProperty::OnEdit](../../mfc/reference/cmfcpropertygridproperty-class.md#onedit).)|
|`CMFCPropertyGridColorProperty::OnUpdateValue`|Lo llama el marco cuando el valor de una propiedad editable ha cambiado. (Reemplaza [CMFCPropertyGridProperty::OnUpdateValue](../../mfc/reference/cmfcpropertygridproperty-class.md#onupdatevalue).)|
|[CMFCPropertyGridColorProperty::SetColor](#setcolor)|Establece un nuevo color para la propiedad.|
|[CMFCPropertyGridColorProperty::SetColumnsNumber](#setcolumnsnumber)|Especifica el número de columnas de la cuadrícula de propiedades de color actual.|
|[CMFCPropertyGridColorProperty::SetOriginalValue](#setoriginalvalue)|Establece el valor original de una propiedad editable.|

## <a name="remarks"></a>Observaciones

La clase `CMFCPropertyGridColorProperty` admite una propiedad de color que puede agregarse a un control de lista de propiedades. Para obtener más información, vea la [clase CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto de la clase `CMFCPropertyGridColorProperty` y configurarlo con varios métodos de la clase `CMFCPropertyGridColorProperty`. El código explica cómo habilitar los botones automáticos y otros botones, y cómo establecer el color y el número de columnas. Este ejemplo forma parte del [ejemplo Nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#13](../../mfc/reference/codesnippet/cpp/cmfcpropertygridcolorproperty-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxpropertygridctrl.h

## <a name="cmfcpropertygridcolorpropertycmfcpropertygridcolorproperty"></a><a name="cmfcpropertygridcolorproperty"></a>CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty

Construye un objeto `CMFCPropertyGridColorProperty`.

```
CMFCPropertyGridColorProperty(
    const CString& strName,
    const COLORREF& color,
    CPalette* pPalette = NULL,
    LPCTSTR lpszDescr = NULL,
    DWORD_PTR dwData = 0);
```

### <a name="parameters"></a>Parámetros

*strName*<br/>
[in] Nombre de la propiedad.

*Color*<br/>
[en] El valor de color de la propiedad.

*pPalette*<br/>
[en] Puntero a una paleta de colores. El valor predeterminado es NULL.

*lpszDescr*<br/>
[en] La descripción de la propiedad. El valor predeterminado es NULL.

*dwData*<br/>
[en] Datos específicos de la aplicación, como un entero o un puntero a otros datos asociados a la propiedad. El valor predeterminado es 0.

## <a name="cmfcpropertygridcolorpropertyenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCPropertyGridColorProperty::EnableAutomaticButton

Activa el botón *automático* en el cuadro de diálogo de selección de color. (El botón automático estándar está etiquetado como **Automático**.)

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
[en] El texto de la etiqueta del botón automático.

*colorAutomático*<br/>
[en] El valor de color RGB del color automático (predeterminado).

*bHabilitar*<br/>
[en] TRUE para habilitar el botón automático; de lo contrario, FALSE. El valor predeterminado es TRUE.

### <a name="remarks"></a>Observaciones

## <a name="cmfcpropertygridcolorpropertyenableotherbutton"></a><a name="enableotherbutton"></a>CMFCPropertyGridColorProperty::EnableOtherButton

Habilita el *otro* botón en el cuadro de diálogo de selección de color. (El otro botón estándar está etiquetado como **Más colores**.)

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg = TRUE,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
[en] El texto de la etiqueta del otro botón.

*bAltColorDlg*<br/>
[en] TRUE para `CMFCColorDialog` mostrar el cuadro de diálogo; FALSE para mostrar el cuadro de diálogo de selección de color estándar. El valor predeterminado es TRUE.

*bHabilitar*<br/>
[en] TRUE para mostrar el otro botón; de lo contrario, FALSE.  El valor predeterminado es TRUE.

### <a name="remarks"></a>Observaciones

## <a name="cmfcpropertygridcolorpropertygetcolor"></a><a name="getcolor"></a>CMFCPropertyGridColorProperty::GetColor

Obtiene el color actual de la propiedad.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de color RGB.

### <a name="remarks"></a>Observaciones

## <a name="cmfcpropertygridcolorpropertysetcolor"></a><a name="setcolor"></a>CMFCPropertyGridColorProperty::SetColor

Establece un nuevo color para la propiedad.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parámetros

*Color*<br/>
[en] Un valor de color RGB.

### <a name="remarks"></a>Observaciones

## <a name="cmfcpropertygridcolorpropertysetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFCPropertyGridColorProperty::SetColumnsNumber

Especifica el número de columnas de la cuadrícula de propiedades de color actual.

```cpp
void SetColumnsNumber(int nColumnsNumber);
```

### <a name="parameters"></a>Parámetros

*nColumnsNumber*<br/>
[en] El número preferido de columnas en la cuadrícula de propiedades de color.

### <a name="remarks"></a>Observaciones

Este método establece el `m_nColumnsNumber` valor del miembro de datos protegido.

## <a name="cmfcpropertygridcolorpropertysetoriginalvalue"></a><a name="setoriginalvalue"></a>CMFCPropertyGridColorProperty::SetOriginalValue

Establece el valor original de una propiedad editable.

```
virtual void SetOriginalValue(const COleVariant& varValue);
```

### <a name="parameters"></a>Parámetros

*varValue*<br/>
[en] Un valor.

### <a name="remarks"></a>Observaciones

Utilice el [CMFCPropertyGridProperty::ResetOriginalValue](../../mfc/reference/cmfcpropertygridproperty-class.md#resetoriginalvalue) método para restablecer el valor original de una propiedad editada.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl (clase)](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty (Clase)](../../mfc/reference/cmfcpropertygridproperty-class.md)
