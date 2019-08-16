---
title: Clase CMFCPropertyPage
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
helpviewer_keywords:
- CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
ms.openlocfilehash: 4be584135ef789d7fbe3b1743ac0ad6ce66ac5b1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505036"
---
# <a name="cmfcpropertypage-class"></a>Clase CMFCPropertyPage

La `CMFCPropertyPage` clase admite la presentación de menús emergentes en una página de propiedades.

## <a name="syntax"></a>Sintaxis

```
class CMFCPropertyPage : public CPropertyPage
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|Construye un objeto `CMFCPropertyPage`.|
|`CMFCPropertyPage::~CMFCPropertyPage`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|`CMFCPropertyPage::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|`CMFCPropertyPage::GetThisClass`|Lo usa el marco de trabajo para obtener un puntero al objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|
|`CMFCPropertyPage::OnSetActive`|El marco de trabajo llama a esta función miembro cuando el usuario elige la página y se convierte en la página activa. (Invalida [CPropertyPage:: OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive)).|
|`CMFCPropertyPage::PreTranslateMessage`|Traduce los mensajes de ventana antes de que se envíen a las funciones de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . Para obtener más información y la sintaxis de método, vea [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Invalida `CPropertyPage::PreTranslateMessage`).|

## <a name="remarks"></a>Comentarios

La `CMFCPropertyPage` clase representa las páginas individuales de una hoja de propiedades, también conocida como cuadro de diálogo de pestaña.

Use la `CMFCPropertyPage` clase junto con la clase [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) . Para usar menús en una página de propiedades, reemplace todas las apariciones de `CPropertyPage` la clase por `CMFCPropertyPage` la clase.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxpropertypage. h

##  <a name="cmfcpropertypage"></a>  CMFCPropertyPage::CMFCPropertyPage

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
IDENTIFICADOR de recurso de la plantilla para esta página.

*nIDCaption*<br/>
IDENTIFICADOR de recurso de la etiqueta que se va a colocar en la pestaña de esta página. Si es 0, el nombre se obtiene de la plantilla de cuadro de diálogo de esta página. El valor predeterminado es 0.

*lpszTemplateName*<br/>
Apunta al nombre de la plantilla para esta página. No puede ser nulo.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

Para obtener más información sobre los parámetros de constructor, vea [CPropertyPage:: CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertySheet (clase)](../../mfc/reference/cmfcpropertysheet-class.md)
