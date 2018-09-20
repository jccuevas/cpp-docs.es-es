---
title: CMFCPropertyGridColorProperty (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridColorProperty [MFC], CMFCPropertyGridColorProperty
- CMFCPropertyGridColorProperty [MFC], EnableAutomaticButton
- CMFCPropertyGridColorProperty [MFC], EnableOtherButton
- CMFCPropertyGridColorProperty [MFC], GetColor
- CMFCPropertyGridColorProperty [MFC], SetColor
- CMFCPropertyGridColorProperty [MFC], SetColumnsNumber
- CMFCPropertyGridColorProperty [MFC], SetOriginalValue
ms.assetid: af37be93-a91e-40a2-9a65-0f3412c6f0f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f238f74127c5f3241a8ce50cf75189358512cb6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400190"
---
# <a name="cmfcpropertygridcolorproperty-class"></a>CMFCPropertyGridColorProperty (clase)

La clase `CMFCPropertyGridColorProperty` admite un elemento de control de la lista de propiedades que abre un cuadro de diálogo de selección de color.

## <a name="syntax"></a>Sintaxis

```
class CMFCPropertyGridColorProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty](#cmfcpropertygridcolorproperty)|Construye un objeto `CMFCPropertyGridColorProperty`.|
|`CMFCPropertyGridColorProperty::~CMFCPropertyGridColorProperty`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](#enableautomaticbutton)|Habilita la *automática* botón en el cuadro de diálogo de selección de color. (El botón automático estándar tiene la etiqueta **automática**.)|
|[CMFCPropertyGridColorProperty::EnableOtherButton](#enableotherbutton)|Habilita la *otros* botón en el cuadro de diálogo de selección de color. (El estándar otro botón se etiqueta como **más colores**.)|
|`CMFCPropertyGridColorProperty::FormatProperty`|Da formato a la representación de texto de un valor de propiedad. (Invalida [cmfcpropertygridproperty:: Formatproperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFCPropertyGridColorProperty::GetColor](#getcolor)|Obtiene el color actual de la propiedad.|
|`CMFCPropertyGridColorProperty::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|
|`CMFCPropertyGridColorProperty::OnClickButton`|Lo llama el marco cuando el usuario hace clic en un botón que se encuentra en una propiedad. (Invalida [cmfcpropertygridproperty:: Onclickbutton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|
|`CMFCPropertyGridColorProperty::OnDrawValue`|Lo llama el marco para mostrar el valor de la propiedad. (Invalida [cmfcpropertygridproperty:: Ondrawvalue](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue).)|
|`CMFCPropertyGridColorProperty::OnEdit`|Lo llama el marco cuando el usuario está a punto de modificar un valor de propiedad. (Invalida [cmfcpropertygridproperty:: Onedit](../../mfc/reference/cmfcpropertygridproperty-class.md#onedit).)|
|`CMFCPropertyGridColorProperty::OnUpdateValue`|Lo llama el marco cuando el valor de una propiedad editable ha cambiado. (Invalida [cmfcpropertygridproperty:: Onupdatevalue](../../mfc/reference/cmfcpropertygridproperty-class.md#onupdatevalue).)|
|[CMFCPropertyGridColorProperty::SetColor](#setcolor)|Establece un nuevo color para la propiedad.|
|[CMFCPropertyGridColorProperty::SetColumnsNumber](#setcolumnsnumber)|Especifica el número de columnas de la cuadrícula de propiedades de color actual.|
|[CMFCPropertyGridColorProperty::SetOriginalValue](#setoriginalvalue)|Establece el valor original de una propiedad editable.|

## <a name="remarks"></a>Comentarios

La clase `CMFCPropertyGridColorProperty` admite una propiedad de color que puede agregarse a un control de lista de propiedades. Para obtener más información, consulte el [CMFCPropertyGridCtrl (clase)](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto de la clase `CMFCPropertyGridColorProperty` y configurarlo con varios métodos de la clase `CMFCPropertyGridColorProperty`. El código explica cómo habilitar los botones automáticos y otros botones, y cómo establecer el color y el número de columnas. Este ejemplo forma parte de la [ejemplo de controles nuevos](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#13](../../mfc/reference/codesnippet/cpp/cmfcpropertygridcolorproperty-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxpropertygridctrl.h

##  <a name="cmfcpropertygridcolorproperty"></a>  CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty

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
[in] El nombre de la propiedad.

*Color*<br/>
[in] El valor de color de la propiedad.

*pPalette*<br/>
[in] Puntero a una paleta de colores. El valor predeterminado es NULL.

*lpszDescr*<br/>
[in] Descripción de propiedad. El valor predeterminado es NULL.

*dwData*<br/>
[in] Datos específicos de la aplicación, como un entero o un puntero a otros datos que está asociados a la propiedad. El valor predeterminado es 0.

##  <a name="enableautomaticbutton"></a>  CMFCPropertyGridColorProperty::EnableAutomaticButton

Habilita la *automática* botón en el cuadro de diálogo de selección de color. (El botón automático estándar tiene la etiqueta **automática**.)

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
[in] El texto de la etiqueta del botón automático.

*automáticoColor*<br/>
[in] El valor de color RGB del color automático (predeterminado).

*bHabilitar el*<br/>
[in] TRUE para habilitar el botón automático; en caso contrario, FALSE. El valor predeterminado es TRUE.

### <a name="remarks"></a>Comentarios

##  <a name="enableotherbutton"></a>  CMFCPropertyGridColorProperty::EnableOtherButton

Habilita la *otros* botón en el cuadro de diálogo de selección de color. (El estándar otro botón se etiqueta como **más colores**.)

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg = TRUE,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
[in] El texto de la etiqueta del otro botón.

*bAltColorDlg*<br/>
[in] True para mostrar el `CMFCColorDialog` cuadro de diálogo; FALSE para mostrar el cuadro de diálogo de selección de color estándar. El valor predeterminado es TRUE.

*bHabilitar el*<br/>
[in] TRUE para mostrar el botón otro; en caso contrario, FALSE.  El valor predeterminado es TRUE.

### <a name="remarks"></a>Comentarios

##  <a name="getcolor"></a>  CMFCPropertyGridColorProperty::GetColor

Obtiene el color actual de la propiedad.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de color RGB.

### <a name="remarks"></a>Comentarios

##  <a name="setcolor"></a>  CMFCPropertyGridColorProperty::SetColor

Establece un nuevo color para la propiedad.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parámetros

*Color*<br/>
[in] Un valor de color RGB.

### <a name="remarks"></a>Comentarios

##  <a name="setcolumnsnumber"></a>  CMFCPropertyGridColorProperty::SetColumnsNumber

Especifica el número de columnas de la cuadrícula de propiedades de color actual.

```
void SetColumnsNumber(int nColumnsNumber);
```

### <a name="parameters"></a>Parámetros

*nColumnsNumber*<br/>
[in] El número preferido de las columnas de la cuadrícula de propiedades de color.

### <a name="remarks"></a>Comentarios

Este método establece el valor de la `m_nColumnsNumber` protegido el miembro de datos.

##  <a name="setoriginalvalue"></a>  CMFCPropertyGridColorProperty::SetOriginalValue

Establece el valor original de una propiedad editable.

```
virtual void SetOriginalValue(const COleVariant& varValue);
```

### <a name="parameters"></a>Parámetros

*varValue*<br/>
[in] Un valor.

### <a name="remarks"></a>Comentarios

Use la [cmfcpropertygridproperty:: Resetoriginalvalue](../../mfc/reference/cmfcpropertygridproperty-class.md#resetoriginalvalue) método para restablecer el valor original de una propiedad editada.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl (clase)](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty (clase)](../../mfc/reference/cmfcpropertygridproperty-class.md)
