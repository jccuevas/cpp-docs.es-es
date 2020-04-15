---
title: CSplitButton (clase)
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
ms.openlocfilehash: 0b54324c3c5503182add15a3dd0a9ecd07c24b18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318113"
---
# <a name="csplitbutton-class"></a>CSplitButton (clase)

La `CSplitButton` clase representa un control de botón de división. El control de botón de expansión realiza un comportamiento predeterminado cuando un usuario hace clic en la parte principal del botón y muestra un menú desplegable cuando un usuario hace clic en la flecha de lista desplegable del botón.

## <a name="syntax"></a>Sintaxis

```
class CSplitButton : public CButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSplitButton::CSplitButton](#csplitbutton)|Construye un objeto `CSplitButton`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSplitButton::Create](#create)|Crea un control de botón de división `CSplitButton` con estilos especificados y lo asocia al objeto actual.|
|[CSplitButton::SetDropDownMenu](#setdropdownmenu)|Establece el menú desplegable que se muestra cuando un usuario hace clic en la flecha desplegable del control de botón de división actual.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CSplitButton::OnDropDown](#ondropdown)|Controla la notificación BCN_DROPDOWN que el sistema envía cuando un usuario hace clic en la flecha desplegable del control de botón de división actual.|

## <a name="remarks"></a>Observaciones

La `CSplitButton` clase se deriva de la [clase CButton.](../../mfc/reference/cbutton-class.md) El control de botón de división es un control de botón cuyo estilo es BS_SPLITBUTTON. Muestra un menú personalizado cuando un usuario hace clic en la flecha desplegable. Para obtener más información, consulte los estilos BS_SPLITBUTTON y BS_DEFSPLITBUTTON en Estilos de [botón](/windows/win32/Controls/button-styles).

En la ilustración siguiente se muestra un cuadro de diálogo que contiene un control de paginación y un (1) control de botón dividido. La (2) flecha desplegable ya se ha hecho clic y se muestra el submenú (3).

![Cuadro de diálogo con botón de división y control de paginación.](../../mfc/reference/media/splitbutton_pager.png "Cuadro de diálogo con botón de división y control de paginación.")

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CSplitButton`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

Esta clase se admite en Windows Vista y versiones posteriores.

Los requisitos adicionales para esta clase se describen en [Requisitos de compilación para controles comunes](../../mfc/build-requirements-for-windows-vista-common-controls.md)de Windows Vista .

## <a name="csplitbuttoncreate"></a><a name="create"></a>CSplitButton::Create

Crea un control de botón de división `CSplitButton` con estilos especificados y lo asocia al objeto actual.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*dwStyle*|[en] Una combinación bit a bit (OR) de estilos que se aplicarán al control. Para obtener más información, consulte Estilos de [botón](../../mfc/reference/styles-used-by-mfc.md#button-styles).|
|*Rect*|[en] Una referencia a una estructura [RECT](/previous-versions/dd162897\(v=vs.85\)) que contiene la posición y el tamaño del control.|
|*pParentWnd*|[en] Un puntero no nulo a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que es la ventana primaria del control.|
|*nID*|[en] El identificador del control.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

## <a name="csplitbuttoncsplitbutton"></a><a name="csplitbutton"></a>CSplitButton::CSplitButton

Construye un objeto `CSplitButton`. Los parámetros del constructor especifican un submenú que se muestra cuando un usuario hace clic en la flecha desplegable del control de botón de división.

```
CSplitButton();

CSplitButton(
    UINT nMenuId,
    UINT nSubMenuId)
CSplitButton(CMenu* pMenu)
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*nMenuId*|[en] El identificador de recurso de la barra de menús.|
|*nSubMenuId*|[en] El identificador de recurso de un submenú.|
|*pMenu*|[en] Puntero a un [CMenu](../../mfc/reference/cmenu-class.md) objeto que especifica un submenú. El `CSplitButton` objeto elimina `CMenu` el objeto y su `CSplitButton` HMENU asociado cuando el objeto sale del ámbito.|

### <a name="remarks"></a>Observaciones

Utilice el método [CSplitButton::Create](#create) para crear un control `CSplitButton` de botón de división y adjuntarlo al objeto.

## <a name="csplitbuttonondropdown"></a><a name="ondropdown"></a>CSplitButton::OnDropDown

Controla la notificación BCN_DROPDOWN que el sistema envía cuando un usuario hace clic en la flecha desplegable del control de botón de división actual.

```
afx_msg void OnDropDown(
    NMHDR* pNMHDR,
    LRESULT* pResult);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pNMHDR*|[en] Puntero a una estructura [NMHDR](/windows/win32/api/richedit/ns-richedit-nmhdr) que contiene información sobre la [notificación BCN_DROPDOWN.](/windows/win32/Controls/bcn-dropdown)|
|*pResult*|[fuera] (No se utiliza; no se devuelve ningún valor.) Devuelve el valor de la notificación [BCN_DROPDOWN.](/windows/win32/Controls/bcn-dropdown)|

### <a name="remarks"></a>Observaciones

Cuando el usuario hace clic en la flecha desplegable de un control de `OnDropDown` botón dividido, el sistema envía un mensaje de notificación BCN_DROPDOWN, que el método controla. Sin `CSplitButton` embargo, el objeto no reenvía la notificación BCN_DROPDOWN al control que contiene el control de botón de división. Por consiguiente, el control contenedor no puede admitir una acción personalizada en respuesta a la notificación.

Para implementar una acción personalizada que admite el control contenedor, utilice un `CSplitButton` [CButton](../../mfc/reference/cbutton-class.md) objeto con un estilo de BS_SPLITBUTTON en lugar de un objeto. A continuación, implemente un controlador `CButton` para la notificación BCN_DROPDOWN en el objeto. Para obtener más información, consulte Estilos de [botón](../../mfc/reference/styles-used-by-mfc.md#button-styles).

Para implementar una acción personalizada que admita el propio control de botón de división, utilice la reflexión de [mensajes](../../mfc/tn062-message-reflection-for-windows-controls.md). Derive su propia `CSplitButton` clase de la clase y asímócela, por ejemplo, CMySplitButton. A continuación, agregue el siguiente mapa de mensajes a la aplicación para controlar la notificación BCN_DROPDOWN:

```
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)
END_MESSAGE_MAP()
```

## <a name="csplitbuttonsetdropdownmenu"></a><a name="setdropdownmenu"></a>CSplitButton::SetDropDownMenu

Establece el menú desplegable que se muestra cuando un usuario hace clic en la flecha desplegable del control de botón de división actual.

```
void SetDropDownMenu(
    UINT nMenuId,
    UINT nSubMenuId);

void SetDropDownMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*nMenuId*|[en] El identificador de recurso de la barra de menús.|
|*nSubMenuId*|[en] El identificador de recurso de un submenú.|
|*pMenu*|[en] Puntero a un [CMenu](../../mfc/reference/cmenu-class.md) objeto que especifica un submenú. El `CSplitButton` objeto elimina `CMenu` el objeto y su `CSplitButton` HMENU asociado cuando el objeto sale del ámbito.|

### <a name="remarks"></a>Observaciones

El *nMenuId* parámetro identifica una barra de menús, que es una lista horizontal de elementos de la barra de menús. El *nSubMenuId* parámetro es un número de índice de base cero que identifica un submenú, que es la lista desplegable de elementos de menú asociados a cada elemento de la barra de menús. Por ejemplo, una aplicación típica tiene un menú que contiene los elementos de la barra de menús, "Archivo", "Editar" y "Ayuda." El elemento de la barra de menús "Archivo" tiene un submenú que contiene los elementos de menú, "Abrir", "Cerrar" y "Salir." Cuando se hace clic en la flecha desplegable del control de botón dividido, el control muestra el submenú especificado, no la barra de menús.

En la ilustración siguiente se muestra un cuadro de diálogo que contiene un control de paginación y un (1) control de botón dividido. La (2) flecha desplegable ya se ha hecho clic y se muestra el submenú (3).

![Cuadro de diálogo con botón de división y control de paginación.](../../mfc/reference/media/splitbutton_pager.png "Cuadro de diálogo con botón de división y control de paginación.")

### <a name="example"></a>Ejemplo

La primera instrucción del ejemplo de código siguiente muestra el [CSplitButton::SetDropDownMenu](#setdropdownmenu) método. Hemos creado el menú con el editor de recursos de Visual Studio, que automáticamente denomina el identificador de la barra de menús IDR_MENU1. El *nSubMenuId* parámetro, que es cero, hace referencia al único submenú de la barra de menús.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]

## <a name="see-also"></a>Consulte también

[CSplitButton (clase)](../../mfc/reference/csplitbutton-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CButton (clase)](../../mfc/reference/cbutton-class.md)
