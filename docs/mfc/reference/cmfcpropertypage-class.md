---
title: CMFCPropertyPage (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
helpviewer_keywords:
- CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
ms.openlocfilehash: 62e33da998f1e5332436d887c38d3fd65526561b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288524"
---
# <a name="cmfcpropertypage-class"></a>CMFCPropertyPage (clase)

La `CMFCPropertyPage` clase admite la visualización de los menús emergentes en una página de propiedades.

## <a name="syntax"></a>Sintaxis

```
class CMFCPropertyPage : public CPropertyPage
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|Construye un objeto `CMFCPropertyPage`.|
|`CMFCPropertyPage::~CMFCPropertyPage`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|`CMFCPropertyPage::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|`CMFCPropertyPage::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|
|`CMFCPropertyPage::OnSetActive`|Esta función miembro se llama el marco de trabajo cuando la página elegida por el usuario y se convierte en la página activa. (Invalida [notificaciones CPropertyPage:: OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).)|
|`CMFCPropertyPage::PreTranslateMessage`|Traduce los mensajes de ventana antes de enviarlos a la [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funciones de Windows. Para obtener más información y la sintaxis de método, consulte [CWnd:: PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Invalida `CPropertyPage::PreTranslateMessage`).|

## <a name="remarks"></a>Comentarios

La `CMFCPropertyPage` clase representa páginas individuales de una hoja de propiedades, también conocido como un cuadro de diálogo de pestaña.

Use la `CMFCPropertyPage` clase junto con el [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) clase. Para usar los menús en una página de propiedades, reemplace todas las apariciones de la `CPropertyPage` clase con la `CMFCPropertyPage` clase.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxpropertypage.h

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
Identificador de recurso de la plantilla para esta página.

*nIDCaption*<br/>
Identificador de recurso de la etiqueta a colocar en la ficha para esta página. Si es 0, se obtiene el nombre de la plantilla de cuadro de diálogo para esta página. El valor predeterminado es 0.

*lpszTemplateName*<br/>
Señala al nombre de la plantilla para esta página. No puede ser nulo.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de los parámetros del constructor, vea [CPropertyPage::CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertySheet (clase)](../../mfc/reference/cmfcpropertysheet-class.md)
