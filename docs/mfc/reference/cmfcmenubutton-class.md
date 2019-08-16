---
title: CMFCMenuButton (clase)
ms.date: 07/15/2019
f1_keywords:
- CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::PreTranslateMessage
- AFXMENUBUTTON/CMFCMenuButton::SizeToContent
- AFXMENUBUTTON/CMFCMenuButton::m_bOSMenu
- AFXMENUBUTTON/CMFCMenuButton::m_bRightArrow
- AFXMENUBUTTON/CMFCMenuButton::m_bStayPressed
- AFXMENUBUTTON/CMFCMenuButton::m_hMenu
- AFXMENUBUTTON/CMFCMenuButton::m_nMenuResult
- AFXMENUBUTTON/CMFCMenuButton::m_bDefaultClick
helpviewer_keywords:
- CMFCMenuButton [MFC], CMFCMenuButton
- CMFCMenuButton [MFC], PreTranslateMessage
- CMFCMenuButton [MFC], SizeToContent
- CMFCMenuButton [MFC], m_bOSMenu
- CMFCMenuButton [MFC], m_bRightArrow
- CMFCMenuButton [MFC], m_bStayPressed
- CMFCMenuButton [MFC], m_hMenu
- CMFCMenuButton [MFC], m_nMenuResult
- CMFCMenuButton [MFC], m_bDefaultClick
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
ms.openlocfilehash: d7c23cbda0a5af4dc3fa6b2d9f59497acc9bf5ff
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505212"
---
# <a name="cmfcmenubutton-class"></a>CMFCMenuButton (clase)

Un botón que muestra un menú emergente e informes en las selecciones de menú del usuario.

## <a name="syntax"></a>Sintaxis

```
class CMFCMenuButton : public CMFCButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCMenuButton::CMFCMenuButton](#cmfcmenubutton)|Construye un objeto `CMFCMenuButton`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|Lo llama el marco de trabajo para traducir los mensajes de ventana antes de enviarlos. (Invalida `CMFCButton::PreTranslateMessage`).|
|[CMFCMenuButton::SizeToContent](#sizetocontent)|Cambia el tamaño del botón en función de su tamaño de imagen y texto.|

### <a name="data-members"></a>Miembros de datos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|Especifica si se va a mostrar el menú emergente del sistema predeterminado o si se va a usar [CContextMenuManager:: TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).|
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|Especifica si el menú emergente aparecerá debajo o a la derecha del botón.|
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|Especifica si el botón de menú cambia su estado una vez que el usuario suelta el botón.|
|[CMFCMenuButton::m_hMenu](#m_hmenu)|Identificador del menú de Windows asociado.|
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|Identificador que indica qué elemento ha seleccionado el usuario en el menú emergente.|
|[CMFCMenuButton::m_bDefaultClick](#m_bdefaultclick)| Permitir el procesamiento predeterminado (en el texto o la imagen del botón).|

## <a name="remarks"></a>Comentarios

La `CMFCMenuButton` clase se deriva de la [clase CMFCButton](../../mfc/reference/cmfcbutton-class.md) , que, a su vez, se deriva de la [clase CButton](../../mfc/reference/cbutton-class.md). Por lo tanto, puede `CMFCMenuButton` usar en el código de la misma manera que `CButton`usaría.

Al crear un `CMFCMenuButton`, se debe pasar un identificador al menú emergente asociado. A continuación, llame a `CMFCMenuButton::SizeToContent`la función. `CMFCMenuButton::SizeToContent`comprueba que el tamaño del botón es suficiente para incluir una flecha que apunta a la ubicación en la que aparecerá la ventana emergente: es decir, debajo o a la derecha del botón.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo establecer el identificador del menú asociado al botón, cambiar el tamaño del botón según su tamaño de imagen y texto, y establecer el menú emergente que muestra el marco de trabajo. Este fragmento de código forma parte del [ejemplo de nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmenubutton. h

##  <a name="cmfcmenubutton"></a>Cmfcmenubutton (:: Cmfcmenubutton (

Construye un nuevo objeto [cmfcmenubutton (](../../mfc/reference/cmfcmenubutton-class.md) .

```
CMFCMenuButton();
```

##  <a name="m_bosmenu"></a>  CMFCMenuButton::m_bOSMenu

Una variable de miembro booleano que indica qué menú emergente muestra el marco de trabajo.

```
BOOL m_bOSMenu;
```

### <a name="remarks"></a>Comentarios

Si `m_bOSMenu` es true, el marco de trabajo llama `TrackPopupMenu` al método heredado para este objeto. De lo contrario, el marco de trabajo llama a [CContextMenuManager:: TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).

##  <a name="m_brightarrow"></a>  CMFCMenuButton::m_bRightArrow

Variable de miembro booleana que indica la ubicación del menú emergente.

```
BOOL m_bRightArrow;
```

### <a name="remarks"></a>Comentarios

Cuando el usuario presiona el botón de menú, la aplicación muestra un menú emergente. El marco de trabajo mostrará el menú emergente debajo del botón o a la derecha del botón. El botón también tiene una flecha pequeña que indica dónde aparecerá el menú emergente. Si `m_bRightArrow` es true, el marco de trabajo muestra el menú emergente a la derecha del botón. De lo contrario, muestra el menú emergente en el botón.

##  <a name="m_bstaypressed"></a>  CMFCMenuButton::m_bStayPressed

Una variable de miembro booleano que indica si el botón de menú aparece presionado mientras el usuario realiza una selección en el menú emergente.

```
BOOL m_bStayPressed;
```

### <a name="remarks"></a>Comentarios

Si el `m_bStayPressed` miembro es false, el botón de menú no se presiona cuando el usa hace clic en el botón. En este caso, el marco de trabajo muestra solo el menú emergente.

Si el `m_bStayPressed` miembro es true, el botón de menú se presiona cuando el usuario hace clic en el botón. Permanece presionado hasta que el usuario cierra el menú emergente, ya sea mediante una selección o una cancelación.

##  <a name="m_hmenu"></a>  CMFCMenuButton::m_hMenu

Identificador del menú asociado.

```
HMENU m_hMenu;
```

### <a name="remarks"></a>Comentarios

El marco de trabajo muestra el menú indicado por esta variable miembro cuando el usuario hace clic en el botón de menú.

##  <a name="m_nmenuresult"></a>  CMFCMenuButton::m_nMenuResult

Un entero que indica el elemento que el usuario selecciona en el menú emergente.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Comentarios

El valor de esta variable miembro es cero si el usuario cancela el menú sin efectuar una selección o si se produce un error.

##  <a name="m_bdefaultclick"></a>  CMFCMenuButton::m_bDefaultClick

Permite el procesamiento predeterminado de texto o imágenes en el botón.

```
BOOL  m_bDefaultClick;
```

### <a name="remarks"></a>Comentarios

Establecer m_bDefaultClick en false hace que el botón muestre el menú al hacer clic en cualquier lugar del botón.

##  <a name="m_nmenuresult"></a>  CMFCMenuButton::m_nMenuResult

Un entero que indica el elemento que el usuario selecciona en el menú emergente.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Comentarios

##  <a name="pretranslatemessage"></a>  CMFCMenuButton::PreTranslateMessage

Lo llama el marco de trabajo para traducir los mensajes de ventana antes de enviarlos.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parámetros

*pMsg*<br/>
de Apunta a una estructura [MSG](/windows/win32/api/winuser/ns-winuser-msg) que contiene el mensaje que se va a procesar.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si el mensaje se ha traducido y no se debe enviar; 0 si el mensaje no se ha traducido y debe enviarse.

### <a name="remarks"></a>Comentarios

##  <a name="sizetocontent"></a>  CMFCMenuButton::SizeToContent

Cambia el tamaño del botón según su tamaño de texto y tamaño de imagen.

```
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```

### <a name="parameters"></a>Parámetros

*bCalcOnly*<br/>
de Un parámetro booleano que indica si este método cambia el tamaño del botón.

### <a name="return-value"></a>Valor devuelto

Objeto [CSize](../../atl-mfc-shared/reference/csize-class.md) que especifica el nuevo tamaño del botón.

### <a name="remarks"></a>Comentarios

Si llama a esta función y *bCalcOnly* es true, `SizeToContent` calculará solo el nuevo tamaño del botón.

El nuevo tamaño del botón se calcula para ajustarse al texto del botón, la imagen y la flecha. El marco de trabajo también agrega márgenes predefinidos de 10 píxeles para el borde horizontal y 5 píxeles para el borde vertical.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton (clase)](../../mfc/reference/cmfcbutton-class.md)
