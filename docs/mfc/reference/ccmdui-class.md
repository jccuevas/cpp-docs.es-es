---
title: CCmdUI (clase)
ms.date: 09/06/2019
f1_keywords:
- CCmdUI
- AFXWIN/CCmdUI
- AFXWIN/CCmdUI::ContinueRouting
- AFXWIN/CCmdUI::Enable
- AFXWIN/CCmdUI::SetCheck
- AFXWIN/CCmdUI::SetRadio
- AFXWIN/CCmdUI::SetText
- AFXWIN/CCmdUI::m_nID
- AFXWIN/CCmdUI::m_nIndex
- AFXWIN/CCmdUI::m_pMenu
- AFXWIN/CCmdUI::m_pOther
- AFXWIN/CCmdUI::m_pSubMenu
helpviewer_keywords:
- CCmdUI [MFC], ContinueRouting
- CCmdUI [MFC], Enable
- CCmdUI [MFC], SetCheck
- CCmdUI [MFC], SetRadio
- CCmdUI [MFC], SetText
- CCmdUI [MFC], m_nID
- CCmdUI [MFC], m_nIndex
- CCmdUI [MFC], m_pMenu
- CCmdUI [MFC], m_pOther
- CCmdUI [MFC], m_pSubMenu
ms.assetid: 04eaaaf5-f510-48ab-b425-94665ba24766
ms.openlocfilehash: 3e167d9e305481e05808f5e553222c10abbc88de
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752729"
---
# <a name="ccmdui-class"></a>CCmdUI (clase)

Solo se usa `ON_UPDATE_COMMAND_UI` dentro `CCmdTarget`de un controlador en una clase derivada.

## <a name="syntax"></a>Sintaxis

```
class CCmdUI
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCmdUI::ContinueRouting](#continuerouting)|Indica al mecanismo de enrutamiento de comandos que continúe enrutando el mensaje actual en la cadena de controladores.|
|[CCmdUI::Habilitar](#enable)|Habilita o deshabilita el elemento de interfaz de usuario para este comando.|
|[CCmdUI::SetCheck](#setcheck)|Establece el estado de comprobación del elemento de interfaz de usuario para este comando.|
|[CCmdUI::SetRadio](#setradio)|Al `SetCheck` igual que la función miembro, pero funciona en grupos de radio.|
|[CCmdUI::SetText](#settext)|Establece el texto del elemento de interfaz de usuario para este comando.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCmdUI::m_nID](#m_nid)|El identificador del objeto de interfaz de usuario.|
|[CCmdUI::m_nIndex](#m_nindex)|El índice del objeto de interfaz de usuario.|
|[CCmdUI::m_pMenu](#m_pmenu)|Apunta al menú representado `CCmdUI` por el objeto.|
|[CCmdUI::m_pOther](#m_pother)|Apunta al objeto de ventana que envió la notificación.|
|[CCmdUI::m_pSubMenu](#m_psubmenu)|Apunta al submenú contenido representado por `CCmdUI` el objeto.|

## <a name="remarks"></a>Observaciones

`CCmdUI`no tiene una clase base.

Cuando un usuario de la aplicación extrae un menú, cada elemento de menú debe saber si debe mostrarse como habilitado o deshabilitado. El destino de un comando de menú proporciona esta información mediante la implementación de un controlador de ON_UPDATE_COMMAND_UI. Para cada uno de los objetos de interfaz de usuario de comando de la aplicación, utilice la ventana [Asistente para](mfc-class-wizard.md) clases o **Propiedades** (en **la vista**de clases ) para crear una entrada de mapa de mensajes y un prototipo de función para cada controlador.

Cuando se extrae el menú, el marco de trabajo busca `CCmdUI` y llama `Enable` `Check`a cada ON_UPDATE_COMMAND_UI controlador, cada controlador llama a funciones miembro como y , y el marco de trabajo, a continuación, muestra correctamente cada elemento de menú.

Un elemento de menú se puede reemplazar con un botón de barra de `ON_UPDATE_COMMAND_UI` control u otro objeto de interfaz de usuario de comando sin cambiar el código dentro del controlador.

En la tabla siguiente `CCmdUI`se resume el efecto que tienen las funciones miembro en varios elementos de interfaz de usuario de comando.

|Elemento de interfaz de usuario|Habilitar|SetCheck|SetRadio|SetText|
|--------------------------|------------|--------------|--------------|-------------|
|Elemento de menú|Habilita o deshabilita|Cheques o desmarcaciones|Comprobaciones usando un punto|Establece el texto del elemento|
|Botón de la barra de herramientas|Habilita o deshabilita|Selecciona, anula la selección o no se determina|Igual que `SetCheck`.|(No aplicable)|
|Panel de la barra de estado|Hace que el texto sea visible o invisible|Establece el borde emergente o normal|Igual que `SetCheck`.|Establece el texto del panel|
|Botón normal en`CDialogBar`|Habilita o deshabilita|Marca o desmarca la casilla de verificación|Igual que `SetCheck`.|Establece el texto del botón|
|Control normal en`CDialogBar`|Habilita o deshabilita|(No aplicable)|(No aplicable)|Establece el texto de la ventana|

Para obtener más información sobre el uso de esta clase, vea [Cómo actualizar objetos de interfaz de usuario](../../mfc/how-to-update-user-interface-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CCmdUI`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="ccmduicontinuerouting"></a><a name="continuerouting"></a>CCmdUI::ContinueRouting

Llame a esta función miembro para indicar al mecanismo de enrutamiento de comandos que continúe enrutando el mensaje actual en la cadena de controladores.

```cpp
void ContinueRouting();
```

### <a name="remarks"></a>Observaciones

Se trata de una función miembro avanzada que se debe usar junto con un controlador de ON_COMMAND_EX que devuelve FALSE. Para obtener más información, consulte [la Nota técnica 6](../../mfc/tn006-message-maps.md).

## <a name="ccmduienable"></a><a name="enable"></a>CCmdUI::Habilitar

Llame a esta función miembro para habilitar o deshabilitar el elemento de interfaz de usuario para este comando.

```
virtual void Enable(BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parámetros

*Bon*<br/>
TRUE para habilitar el elemento, FALSE para deshabilitarlo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]

## <a name="ccmduim_nid"></a><a name="m_nid"></a>CCmdUI::m_nID

El identificador del elemento de menú, el botón de `CCmdUI` barra de herramientas u otro objeto de interfaz de usuario representado por el objeto.

```
UINT m_nID;
```

## <a name="ccmduim_nindex"></a><a name="m_nindex"></a>CCmdUI::m_nIndex

El índice del elemento de menú, el botón de `CCmdUI` barra de herramientas u otro objeto de interfaz de usuario representado por el objeto.

```
UINT m_nIndex;
```

## <a name="ccmduim_pmenu"></a><a name="m_pmenu"></a>CCmdUI::m_pMenu

Puntero (de `CMenu` tipo) al menú `CCmdUI` representado por el objeto.

```
CMenu* m_pMenu;
```

### <a name="remarks"></a>Observaciones

NULL si el elemento no es un menú.

## <a name="ccmduim_psubmenu"></a><a name="m_psubmenu"></a>CCmdUI::m_pSubMenu

Puntero (de `CMenu` tipo) al submenú contenido representado `CCmdUI` por el objeto.

```
CMenu* m_pSubMenu;
```

### <a name="remarks"></a>Observaciones

NULL si el elemento no es un menú. Si el submenú es una ventana emergente, *m_nID* contiene el identificador del primer elemento del menú emergente. Para obtener más información, consulte [la Nota técnica 21](../../mfc/tn021-command-and-message-routing.md).

## <a name="ccmduim_pother"></a><a name="m_pother"></a>CCmdUI::m_pOther

Puntero (de `CWnd`tipo) al objeto de ventana, como una herramienta o barra de estado, que envió la notificación.

```
CWnd* m_pOther;
```

### <a name="remarks"></a>Observaciones

NULL si el elemento es un `CWnd` menú o un no objeto.

## <a name="ccmduisetcheck"></a><a name="setcheck"></a>CCmdUI::SetCheck

Llame a esta función miembro para establecer el elemento de interfaz de usuario para este comando en el estado de comprobación adecuado.

```
virtual void SetCheck(int nCheck = 1);
```

### <a name="parameters"></a>Parámetros

*nCheck*<br/>
Especifica el estado de comprobación que se va a establecer. Si 0, desmarca; si 1, cheques; y si 2, establece indeterminado.

### <a name="remarks"></a>Observaciones

Esta función miembro funciona para los elementos de menú y botones de barra de herramientas. El estado indeterminado solo se aplica a los botones de la barra de herramientas.

## <a name="ccmduisetradio"></a><a name="setradio"></a>CCmdUI::SetRadio

Llame a esta función miembro para establecer el elemento de interfaz de usuario para este comando en el estado de comprobación adecuado.

```
virtual void SetRadio(BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parámetros

*Bon*<br/>
TRUE para habilitar el elemento; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Esta función miembro `SetCheck`funciona como , excepto que funciona en elementos de interfaz de usuario que actúan como parte de un grupo de radio. Desmarcar los otros elementos del grupo no es automático a menos que los propios elementos mantengan el comportamiento del grupo de radio.

## <a name="ccmduisettext"></a><a name="settext"></a>CCmdUI::SetText

Llame a esta función miembro para establecer el texto del elemento de interfaz de usuario para este comando.

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
Un puntero a una cadena de texto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)
