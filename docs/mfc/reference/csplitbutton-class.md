---
title: Clase CSplitButton
ms.date: 11/19/2018
f1_keywords:
- CSplitButton
- AFXCMN/CSplitButton
- AFXCMN/CSplitButton::CSplitButton
- AFXCMN/CSplitButton::Create
- AFXCMN/CSplitButton::SetDropDownMenu
- AFXCMN/CSplitButton::OnDropDown
helpviewer_keywords:
- CSplitButton [MFC], CSplitButton
- CSplitButton [MFC], Create
- CSplitButton [MFC], SetDropDownMenu
- CSplitButton [MFC], OnDropDown
ms.assetid: 6844d0a9-6408-4e44-9b5f-57628ed8bad6
ms.openlocfilehash: d493a2d4d1c531250abc1cd60d1d3d5b79dea1b7
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916769"
---
# <a name="csplitbutton-class"></a>Clase CSplitButton

La `CSplitButton` clase representa un control de botón de expansión. El control de botón de expansión realiza un comportamiento predeterminado cuando un usuario hace clic en la parte principal del botón y muestra un menú desplegable cuando un usuario hace clic en la flecha de lista desplegable del botón.

## <a name="syntax"></a>Sintaxis

```
class CSplitButton : public CButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSplitButton::CSplitButton](#csplitbutton)|Construye un objeto `CSplitButton`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSplitButton::Create](#create)|Crea un control de botón de expansión con los estilos especificados y lo adjunta `CSplitButton` al objeto actual.|
|[CSplitButton::SetDropDownMenu](#setdropdownmenu)|Establece el menú desplegable que se muestra cuando un usuario hace clic en la flecha de lista desplegable del control de botón de expansión actual.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSplitButton::OnDropDown](#ondropdown)|Controla la notificación BCN_DROPDOWN que el sistema envía cuando un usuario hace clic en la flecha desplegable del control de botón de expansión actual.|

## <a name="remarks"></a>Comentarios

La `CSplitButton` clase se deriva de la clase [CButton](../../mfc/reference/cbutton-class.md) . El control de botón de expansión es un control de botón cuyo estilo es BS_SPLITBUTTON. Muestra un menú personalizado cuando un usuario hace clic en la flecha de lista desplegable. Para obtener más información, consulte los estilos BS_SPLITBUTTON y BS_DEFSPLITBUTTON en los [estilos de botón](/windows/desktop/Controls/button-styles).

En la ilustración siguiente se muestra un cuadro de diálogo que contiene un control de paginación y un control de botón de expansión (1). Ya se ha hecho clic en la flecha desplegable (2) y se muestra el submenú (3).

![Cuadro de diálogo con un control de paginación y splitButton.](../../mfc/reference/media/splitbutton_pager.png "Cuadro de diálogo con un control de paginación y splitButton.")

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CSplitButton`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

Esta clase es compatible con Windows Vista y versiones posteriores.

Los requisitos adicionales para esta clase se describen en [requisitos de compilación para los controles comunes de Windows Vista](../../mfc/build-requirements-for-windows-vista-common-controls.md).

##  <a name="create"></a>  CSplitButton::Create

Crea un control de botón de expansión con los estilos especificados y lo adjunta `CSplitButton` al objeto actual.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*dwStyle*|de Combinación bit a bit (o) de estilos que se va a aplicar al control. Para obtener más información, consulte [estilos de botón](../../mfc/reference/styles-used-by-mfc.md#button-styles).|
|*rect*|de Referencia a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que contiene la posición y el tamaño del control.|
|*pParentWnd*|de Un puntero no nulo a un objeto [CWnd](../../mfc/reference/cwnd-class.md) que es la ventana primaria del control.|
|*nID*|de IDENTIFICADOR del control.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

##  <a name="csplitbutton"></a>  CSplitButton::CSplitButton

Construye un objeto `CSplitButton`. Los parámetros del constructor especifican un submenú que se muestra cuando un usuario hace clic en la flecha de lista desplegable del control de botón de expansión.

```
CSplitButton();

CSplitButton(
    UINT nMenuId,
    UINT nSubMenuId)
CSplitButton(CMenu* pMenu)
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*nMenuId*|de IDENTIFICADOR de recurso de la barra de menús.|
|*nSubMenuId*|de El identificador de recurso de un submenú.|
|*pMenu*|de Un puntero a un objeto [CMenu](../../mfc/reference/cmenu-class.md) que especifica un submenú. El `CSplitButton` objeto elimina el `CMenu` objeto y su HMENU asociado cuando el `CSplitButton` objeto sale del ámbito.|

### <a name="remarks"></a>Comentarios

Use el método [CSplitButton:: Create](#create) para crear un control de botón de expansión y adjuntarlo al `CSplitButton` objeto.

##  <a name="ondropdown"></a>  CSplitButton::OnDropDown

Controla la notificación BCN_DROPDOWN que el sistema envía cuando un usuario hace clic en la flecha desplegable del control de botón de expansión actual.

```
afx_msg void OnDropDown(
    NMHDR* pNMHDR,
    LRESULT* pResult);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*pNMHDR*|de Puntero a una estructura [NMHDR](/windows/desktop/api/richedit/ns-richedit-nmhdr) que contiene información sobre la notificación de [BCN_DROPDOWN](/windows/desktop/Controls/bcn-dropdown) .|
|*pResult*|enuncia (No se usa; no se devuelve ningún valor). Valor devuelto de la notificación [BCN_DROPDOWN](/windows/desktop/Controls/bcn-dropdown) .|

### <a name="remarks"></a>Comentarios

Cuando el usuario hace clic en la flecha desplegable de un control de botón de expansión, el sistema envía un mensaje de notificación `OnDropDown` BCN_DROPDOWN, que controla el método. Sin embargo, `CSplitButton` el objeto no reenvía la notificación BCN_DROPDOWN al control que contiene el control de botón de expansión. Por consiguiente, el control contenedor no puede admitir una acción personalizada en respuesta a la notificación.

Para implementar una acción personalizada compatible con el control contenedor, utilice un objeto [CButton](../../mfc/reference/cbutton-class.md) con un estilo de BS_SPLITBUTTON en lugar de un `CSplitButton` objeto. A continuación, implemente un controlador para la notificación `CButton` BCN_DROPDOWN en el objeto. Para obtener más información, consulte [estilos de botón](../../mfc/reference/styles-used-by-mfc.md#button-styles).

Para implementar una acción personalizada compatible con el control de botón de expansión, utilice la [reflexión de mensajes](../../mfc/tn062-message-reflection-for-windows-controls.md). Derive su propia clase de la `CSplitButton` clase y asígnele el nombre, por ejemplo, CMySplitButton. Después, agregue el siguiente mapa de mensajes a la aplicación para controlar la notificación BCN_DROPDOWN:

```
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)
END_MESSAGE_MAP()
```

##  <a name="setdropdownmenu"></a>  CSplitButton::SetDropDownMenu

Establece el menú desplegable que se muestra cuando un usuario hace clic en la flecha de lista desplegable del control de botón de expansión actual.

```
void SetDropDownMenu(
    UINT nMenuId,
    UINT nSubMenuId);

void SetDropDownMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*nMenuId*|de IDENTIFICADOR de recurso de la barra de menús.|
|*nSubMenuId*|de El identificador de recurso de un submenú.|
|*pMenu*|de Puntero a un objeto [CMenu](../../mfc/reference/cmenu-class.md) que especifica un submenú. El `CSplitButton` objeto elimina el `CMenu` objeto y su HMENU asociado cuando el `CSplitButton` objeto sale del ámbito.|

### <a name="remarks"></a>Comentarios

El parámetro *nMenuId* identifica una barra de menús, que es una lista horizontal de elementos de barra de menús. El parámetro *nSubMenuId* es un número de índice de base cero que identifica un submenú, que es la lista desplegable de elementos de menú asociados a cada elemento de la barra de menús. Por ejemplo, una aplicación típica tiene un menú que contiene los elementos de la barra de menús, "File", "Edit" y "Help". El elemento de barra de menú "archivo" tiene un submenú que contiene los elementos de menú, "abrir", "cerrar" y "salir". Cuando se hace clic en la flecha desplegable del control de botón de expansión, el control muestra el submenú especificado, no la barra de menús.

En la ilustración siguiente se muestra un cuadro de diálogo que contiene un control de paginación y un control de botón de expansión (1). Ya se ha hecho clic en la flecha desplegable (2) y se muestra el submenú (3).

![Cuadro de diálogo con un control de paginación y splitButton.](../../mfc/reference/media/splitbutton_pager.png "Cuadro de diálogo con un control de paginación y splitButton.")

### <a name="example"></a>Ejemplo

La primera instrucción del ejemplo de código siguiente muestra el método [CSplitButton:: SetDropDownMenu](#setdropdownmenu) . Hemos creado el menú con el editor de recursos de Visual Studio, que se denomina automáticamente el identificador de la barra de menús, IDR_MENU1. El parámetro *nSubMenuId* , que es cero, hace referencia al único submenú de la barra de menús.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]

## <a name="see-also"></a>Vea también

[CSplitButton (clase)](../../mfc/reference/csplitbutton-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CButton (clase)](../../mfc/reference/cbutton-class.md)
