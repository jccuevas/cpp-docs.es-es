---
title: CMFCRibbonCustomizeDialog (Clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog
helpviewer_keywords:
- CMFCRibbonCustomizeDialog [MFC], CMFCRibbonCustomizeDialog
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
ms.openlocfilehash: a66c0a19c04e0a900b91c0c28c45bb9c766d25c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375205"
---
# <a name="cmfcribboncustomizedialog-class"></a>CMFCRibbonCustomizeDialog (Clase)

Muestra la página **Personalizar** de la cinta de opciones.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog](#cmfcribboncustomizedialog)|Construye un objeto `CMFCRibbonCustomizeDialog`.|
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|`CMFCRibbonCustomizeDialog::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|

## <a name="remarks"></a>Observaciones

MFC crea una instancia de esta clase automáticamente si no procesa el mensaje de AFX_WM_ON_RIBBON_CUSTOMIZE o si devuelve 0 desde el controlador de mensajes.

Si desea utilizar esta clase en la **Customize** aplicación para mostrar el cuadro `DoModal` de diálogo Personalizar de la cinta de opciones, simplemente cree una instancia de ella y llame al método.

Dado que esta clase se deriva de [CMFCPropertySheet (clase),](../../mfc/reference/cmfcpropertysheet-class.md)puede agregar páginas personalizadas mediante la `CMFCPropertySheet` API.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

[CMFCRibbonCustomizeDialog](../../mfc/reference/cmfcribboncustomizedialog-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxribboncustomizedialog.h

## <a name="cmfcribboncustomizedialogcmfcribboncustomizedialog"></a><a name="cmfcribboncustomizedialog"></a>CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog

Construye un objeto `CMFCRibbonCustomizeDialog`.

```
CMFCRibbonCustomizeDialog(
    CWnd* pWndParent,
    CMFCRibbonBar* pRibbon);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[en] Un puntero a la ventana primaria (normalmente el marco principal).

*pRibbon*<br/>
[en] Un puntero `CMFCRibbonBar` a la que se va a personalizar.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `CMFCRibbonCustomizeDialog` muestra cómo construir un objeto.

[!code-cpp[NVC_MFC_RibbonApp#18](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]

### <a name="remarks"></a>Observaciones

El constructor crea una instancia de un [CMFCRibbonCustomizePropertyPage clase](../../mfc/reference/cmfcribboncustomizepropertypage-class.md) objeto y lo agrega a la colección de páginas de hoja de propiedades.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
