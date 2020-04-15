---
title: Clase CMFCRibbonLabel
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::SetACCData
helpviewer_keywords:
- CMFCRibbonLabel [MFC], CMFCRibbonLabel
- CMFCRibbonLabel [MFC], SetACCData
ms.assetid: 0346c891-83bf-4f20-b8a1-c84cf2aadced
ms.openlocfilehash: cd30e374441661368d3ea7abf5177424f8dffb3c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375120"
---
# <a name="cmfcribbonlabel-class"></a>Clase CMFCRibbonLabel

Implementa una etiqueta de texto no seleccionable en una cinta.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonLabel : public CMFCRibbonButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonLabel::CMFCRibbonLabel](#cmfcribbonlabel)|Construye e inicializa `CMFCRibbonLabel` un objeto con la cadena de texto especificada.|
|`CMFCRibbonLabel::~CMFCRibbonLabel`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|`CMFCRibbonLabel::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|`CMFCRibbonLabel::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|[CMFCRibbonLabel::SetACCData](#setaccdata)|Determina los datos de accesibilidad para el elemento de etiqueta de la cinta de opciones actual. (Reemplaza [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

### <a name="remarks"></a>Observaciones

Después de crear una etiqueta de la cinta de opciones, agréguela a un panel llamando a [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

No puede agregar una etiqueta de cinta de opciones a la barra de herramientas de acceso rápido.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxRibbonLabel.h

## <a name="cmfcribbonlabelcmfcribbonlabel"></a><a name="cmfcribbonlabel"></a>CMFCRibbonLabel::CMFCRibbonLabel

Construye e inicializa un [CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md) objeto que muestra la cadena de texto especificada.

```
CMFCRibbonLabel(
    LPCTSTR lpszText,
    BOOL bIsMultiLine = FALSE);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
[en] El texto que aparecerá en la etiqueta.

*bIsMultiLine*<br/>
[en] TRUE para especificar que la etiqueta es una etiqueta de varias líneas; de lo contrario, FALSE.

## <a name="cmfcribbonlabelsetaccdata"></a><a name="setaccdata"></a>CMFCRibbonLabel::SetACCData

Determina los datos de accesibilidad para el elemento de etiqueta de la cinta de opciones actual.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parámetros

*pParent*<br/>
[en] Representa la ventana primaria de la etiqueta de la cinta de opciones actual.

*datos*<br/>
[fuera] Objeto de `CAccessibilityData` tipo que se rellena con los datos de accesibilidad de la etiqueta de la cinta de opciones actual.

### <a name="return-value"></a>Valor devuelto

TRUESi el parámetro *de datos* se ha rellenado correctamente con los datos de accesibilidad de la etiqueta de la cinta de opciones actual; de lo contrario, FALSE.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton (clase)](../../mfc/reference/cmfcribbonbutton-class.md)
