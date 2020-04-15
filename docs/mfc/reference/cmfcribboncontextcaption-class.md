---
title: CMFCRibbonContextCaption Clase
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetColor
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetRightTabX
helpviewer_keywords:
- CMFCRibbonContextCaption [MFC], GetColor
- CMFCRibbonContextCaption [MFC], GetRightTabX
ms.assetid: cce2c0a2-8370-4266-997e-f8d0eeb3d616
ms.openlocfilehash: 7aacbe23684914c91129d9962ae847d442cc411b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375215"
---
# <a name="cmfcribboncontextcaption-class"></a>CMFCRibbonContextCaption Clase

Implementa una leyenda coloreada que aparece en la parte superior de una categoría de la cinta o de una categoría de contexto.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonContextCaption : public CMFCRibbonButton
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|`CMFCRibbonContextCaption::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|[CMFCRibbonContextCaption::GetColor](#getcolor)|Devuelve el color del título.|
|[CMFCRibbonContextCaption::GetRightTabX](#getrighttabx)||
|`CMFCRibbonContextCaption::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|

## <a name="remarks"></a>Observaciones

No se puede crear una instancia de esta clase directamente. La [clase CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md) utiliza esta clase internamente para agregar color a las categorías de la cinta de opciones.

Para establecer el color de las categorías de la cinta de opciones, llame a [CMFCRibbonCategory::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor). Para establecer el color de las categorías de contexto, llame a [CMFCRibbonBar::AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonContextCaption](../../mfc/reference/cmfcribboncontextcaption-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxRibbonBar.h

## <a name="cmfcribboncontextcaptiongetcolor"></a><a name="getcolor"></a>CMFCRibbonContextCaption::GetColor

Devuelve el color de fondo del título.

```
AFX_RibbonCategoryColor GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

El valor devuelto puede ser uno de los siguientes valores enumerados:

- `AFX_CategoryColor_None`

- `AFX_CategoryColor_Red`

- `AFX_CategoryColor_Orange`

- `AFX_CategoryColor_Yellow`

- `AFX_CategoryColor_Green`

- `AFX_CategoryColor_Blue`

- `AFX_CategoryColor_Indigo`

- `AFX_CategoryColor_Violet`

### <a name="remarks"></a>Observaciones

El color del título se puede establecer llamando a [CMFCRibbonCategory::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor) o [CMFCRibbonBar::AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory).

## <a name="cmfcribboncontextcaptiongetrighttabx"></a><a name="getrighttabx"></a>CMFCRibbonContextCaption::GetRightTabX

Recupera la posición del borde derecho de la ficha de la cinta de opciones de la categoría.

```
int GetRightTabX() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor X de la derecha del `CMFCRibbonCategory` rectángulo envolvente de la ficha de la cinta de opciones del objeto, o un valor de -1 si la ficha se trunca.

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton (clase)](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonCategory (Clase)](../../mfc/reference/cmfcribboncategory-class.md)<br/>
[CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md)
