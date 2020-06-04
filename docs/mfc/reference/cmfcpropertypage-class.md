---
title: CMFCPropertyPage (Clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
helpviewer_keywords:
- CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
ms.openlocfilehash: e493f016b6384a768935186c31e3fc71ade6382f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361767"
---
# <a name="cmfcpropertypage-class"></a>CMFCPropertyPage (Clase)

La `CMFCPropertyPage` clase admite la visualización de menús emergentes en una página de propiedades.

## <a name="syntax"></a>Sintaxis

```
class CMFCPropertyPage : public CPropertyPage
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|Construye un objeto `CMFCPropertyPage`.|
|`CMFCPropertyPage::~CMFCPropertyPage`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|`CMFCPropertyPage::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|`CMFCPropertyPage::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|`CMFCPropertyPage::OnSetActive`|El marco de trabajo llama a esta función miembro cuando el usuario elige la página y se convierte en la página activa. (Reemplaza [CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).)|
|`CMFCPropertyPage::PreTranslateMessage`|Traduce los mensajes de ventana antes de que se distribuyan a las funciones de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage.](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Para obtener más información y sintaxis de método, vea [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Invalida `CPropertyPage::PreTranslateMessage`).|

## <a name="remarks"></a>Observaciones

La `CMFCPropertyPage` clase representa páginas individuales de una hoja de propiedades, también conocida como un cuadro de diálogo de ficha.

Utilice `CMFCPropertyPage` la clase junto con la [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) clase. Para usar menús en una página de `CPropertyPage` propiedades, `CMFCPropertyPage` reemplace todas las apariciones de la clase por la clase.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxpropertypage.h

## <a name="cmfcpropertypagecmfcpropertypage"></a><a name="cmfcpropertypage"></a>CMFCPropertyPage::CMFCPropertyPage

Construye un objeto `CMFCPropertyPage`.

```
CMFCPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption=0);

CMFCPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption=0);
```

### <a name="parameters"></a>Parámetros

*nIDTemplate*<br/>
Identificador de recurso de la plantilla para esta página.

*nIDCaption*<br/>
Identificador de recurso de la etiqueta que se colocará en la pestaña de esta página. Si es 0, el nombre se obtiene de la plantilla de cuadro de diálogo para esta página. El valor predeterminado es 0.

*lpszTemplateName*<br/>
Señala el nombre de la plantilla para esta página. No puede ser NULL.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de los parámetros del constructor, vea [CPropertyPage::CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage).

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertySheet (clase)](../../mfc/reference/cmfcpropertysheet-class.md)
