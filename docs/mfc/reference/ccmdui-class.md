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
ms.openlocfilehash: 42aec2937cd81ebbb50482321b8deae001723d3a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424570"
---
# <a name="ccmdui-class"></a>CCmdUI (clase)

Solo se usa dentro de un controlador de `ON_UPDATE_COMMAND_UI` en una clase derivada de `CCmdTarget`.

## <a name="syntax"></a>Sintaxis

```
class CCmdUI
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCmdUI:: ContinueRouting](#continuerouting)|Indica al mecanismo de enrutamiento de comandos que continúe enrutando el mensaje actual hacia la cadena de controladores.|
|[CCmdUI:: enable](#enable)|Habilita o deshabilita el elemento de la interfaz de usuario para este comando.|
|[CCmdUI:: SetCheck](#setcheck)|Establece el estado de activación del elemento de la interfaz de usuario para este comando.|
|[CCmdUI:: SetRadio](#setradio)|Como la función miembro `SetCheck`, pero funciona en grupos de radio.|
|[CCmdUI:: SetText](#settext)|Establece el texto del elemento de la interfaz de usuario para este comando.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCmdUI:: m_nID](#m_nid)|IDENTIFICADOR del objeto de la interfaz de usuario.|
|[CCmdUI:: m_nIndex](#m_nindex)|Índice del objeto de la interfaz de usuario.|
|[CCmdUI:: m_pMenu](#m_pmenu)|Apunta al menú representado por el objeto `CCmdUI`.|
|[CCmdUI:: m_pOther](#m_pother)|Apunta al objeto de ventana que envió la notificación.|
|[CCmdUI:: m_pSubMenu](#m_psubmenu)|Apunta al submenú contenido representado por el objeto `CCmdUI`.|

## <a name="remarks"></a>Observaciones

`CCmdUI` no tiene una clase base.

Cuando un usuario de la aplicación extrae un menú, cada elemento de menú debe saber si debe mostrarse como habilitado o deshabilitado. El destino de un comando de menú proporciona esta información implementando un controlador de ON_UPDATE_COMMAND_UI. Para cada uno de los objetos de interfaz de usuario de comandos de la aplicación, use el [Asistente para clases](mfc-class-wizard.md) o la ventana **propiedades** (en **vista de clases**) para crear una entrada de mapa de mensajes y un prototipo de función para cada controlador.

Cuando se extrae el menú, el marco de trabajo busca y llama a cada controlador de ON_UPDATE_COMMAND_UI, cada controlador llama a `CCmdUI` funciones miembro como `Enable` y `Check`, y el marco de trabajo muestra, en consecuencia, cada elemento de menú.

Un elemento de menú se puede reemplazar por un botón de barra de control u otro objeto de interfaz de usuario de comandos sin cambiar el código del controlador de `ON_UPDATE_COMMAND_UI`.

En la tabla siguiente se resumen las funciones miembro de `CCmdUI`efecto de los distintos elementos de la interfaz de usuario de comandos.

|Elemento de la interfaz de usuario|Habilitar|SetCheck|SetRadio|SetText|
|--------------------------|------------|--------------|--------------|-------------|
|Elemento de menú|Habilita o deshabilita|Comprueba o desactiva|Comprobaciones con un punto|Establece el texto del elemento|
|Botón de la barra de herramientas|Habilita o deshabilita|Selecciona, anula la selección o indeterminado.|Igual que `SetCheck`.|(No aplicable)|
|Panel de barra de estado|Hace que el texto sea visible o invisible|Establece el borde emergente o normal|Igual que `SetCheck`.|Establece el texto del panel|
|Botón normal en `CDialogBar`|Habilita o deshabilita|Casilla comprobaciones o desactivaciones|Igual que `SetCheck`.|Establece el texto del botón|
|Control normal en `CDialogBar`|Habilita o deshabilita|(No aplicable)|(No aplicable)|Establece el texto de la ventana|

Para obtener más información sobre el uso de esta clase, vea [Cómo actualizar objetos de la interfaz de usuario](../../mfc/how-to-update-user-interface-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CCmdUI`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="continuerouting"></a>CCmdUI:: ContinueRouting

Llame a esta función miembro para indicar al mecanismo de enrutamiento de comandos que continúe enrutando el mensaje actual hacia la cadena de controladores.

```
void ContinueRouting();
```

### <a name="remarks"></a>Observaciones

Se trata de una función miembro avanzada que se debe usar junto con un controlador de ON_COMMAND_EX que devuelve FALSE. Para obtener más información, vea la [Nota técnica 6](../../mfc/tn006-message-maps.md).

##  <a name="enable"></a>CCmdUI:: enable

Llame a esta función miembro para habilitar o deshabilitar el elemento de la interfaz de usuario para este comando.

```
virtual void Enable(BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parámetros

*Despedida*<br/>
TRUE para habilitar el elemento y FALSE para deshabilitarlo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]

##  <a name="m_nid"></a>CCmdUI:: m_nID

IDENTIFICADOR del elemento de menú, botón de la barra de herramientas u otro objeto de interfaz de usuario representado por el objeto `CCmdUI`.

```
UINT m_nID;
```

##  <a name="m_nindex"></a>CCmdUI:: m_nIndex

Índice del elemento de menú, botón de la barra de herramientas u otro objeto de interfaz de usuario representado por el objeto `CCmdUI`.

```
UINT m_nIndex;
```

##  <a name="m_pmenu"></a>CCmdUI:: m_pMenu

Puntero (de `CMenu` tipo) al menú representado por el objeto `CCmdUI`.

```
CMenu* m_pMenu;
```

### <a name="remarks"></a>Observaciones

Es NULL si el elemento no es un menú.

##  <a name="m_psubmenu"></a>CCmdUI:: m_pSubMenu

Puntero (de `CMenu` tipo) al submenú contenido representado por el objeto `CCmdUI`.

```
CMenu* m_pSubMenu;
```

### <a name="remarks"></a>Observaciones

Es NULL si el elemento no es un menú. Si el submenú es un elemento emergente, *m_nID* contiene el identificador del primer elemento del menú emergente. Para obtener más información, vea la [Nota técnica 21](../../mfc/tn021-command-and-message-routing.md).

##  <a name="m_pother"></a>CCmdUI:: m_pOther

Puntero (de tipo `CWnd`) al objeto de ventana, como una herramienta o una barra de estado, que envió la notificación.

```
CWnd* m_pOther;
```

### <a name="remarks"></a>Observaciones

Es NULL si el elemento es un menú o un objeto que no es de `CWnd`.

##  <a name="setcheck"></a>CCmdUI:: SetCheck

Llame a esta función miembro para establecer el elemento de la interfaz de usuario para este comando en el estado de comprobación adecuado.

```
virtual void SetCheck(int nCheck = 1);
```

### <a name="parameters"></a>Parámetros

*nCompruebe*<br/>
Especifica el estado de comprobación que se va a establecer. Si es 0, desactiva; Si es 1, comprueba; y si 2, establece indeterminados.

### <a name="remarks"></a>Observaciones

Esta función miembro funciona para los elementos de menú y los botones de barra de herramientas. El estado indeterminado solo se aplica a los botones de la barra de herramientas.

##  <a name="setradio"></a>CCmdUI:: SetRadio

Llame a esta función miembro para establecer el elemento de la interfaz de usuario para este comando en el estado de comprobación adecuado.

```
virtual void SetRadio(BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parámetros

*Despedida*<br/>
TRUE para habilitar el elemento; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Esta función miembro funciona como `SetCheck`, salvo que funciona en elementos de la interfaz de usuario que actúan como parte de un grupo de radio. La desactivación de los demás elementos del grupo no es automática a menos que los propios elementos mantengan el comportamiento del grupo de radio.

##  <a name="settext"></a>CCmdUI:: SetText

Llame a esta función miembro para establecer el texto del elemento de la interfaz de usuario para este comando.

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
Puntero a una cadena de texto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MDI de MFC](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)
