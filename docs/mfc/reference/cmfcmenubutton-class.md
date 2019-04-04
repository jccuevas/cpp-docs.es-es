---
title: CMFCMenuButton (clase)
ms.date: 11/04/2016
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
helpviewer_keywords:
- CMFCMenuButton [MFC], CMFCMenuButton
- CMFCMenuButton [MFC], PreTranslateMessage
- CMFCMenuButton [MFC], SizeToContent
- CMFCMenuButton [MFC], m_bOSMenu
- CMFCMenuButton [MFC], m_bRightArrow
- CMFCMenuButton [MFC], m_bStayPressed
- CMFCMenuButton [MFC], m_hMenu
- CMFCMenuButton [MFC], m_nMenuResult
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
ms.openlocfilehash: cbdf4005ee1a0249e7ed2b5f1d50621fb951f64f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58777368"
---
# <a name="cmfcmenubutton-class"></a>CMFCMenuButton (clase)

Un botón que muestra un menú emergente e informes en las selecciones de menú del usuario.

## <a name="syntax"></a>Sintaxis

```
class CMFCMenuButton : public CMFCButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCMenuButton::CMFCMenuButton](#cmfcmenubutton)|Construye un objeto `CMFCMenuButton`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|Lo llama el marco para traducir los mensajes de ventana antes de enviarlos. (Invalida `CMFCButton::PreTranslateMessage`).|
|[CMFCMenuButton::SizeToContent](#sizetocontent)|Cambia el tamaño del botón según su tamaño de texto e imagen.|

### <a name="data-members"></a>Miembros de datos

|Name|Descripción|
|----------|-----------------|
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|Especifica si desea mostrar el menú emergente del sistema predeterminada o usar [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).|
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|Especifica si el menú emergente aparecerán debajo o a la derecha del botón.|
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|Especifica si el botón de menú cambia su estado después de que el usuario suelta el botón.|
|[CMFCMenuButton::m_hMenu](#m_hmenu)|Identificador del menú de Windows asociada.|
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|Un identificador que indica qué elemento del usuario seleccionado en el menú emergente.|

## <a name="remarks"></a>Comentarios

El `CMFCMenuButton` clase se deriva el [CMFCButton (clase)](../../mfc/reference/cmfcbutton-class.md) que, a su vez, deriva el [CButton (clase)](../../mfc/reference/cbutton-class.md). Por lo tanto, puede usar `CMFCMenuButton` en el código de la misma manera que utilizaría `CButton`.

Cuando creas un `CMFCMenuButton`, debe pasar un identificador para el menú emergente asociado. A continuación, llame a la función `CMFCMenuButton::SizeToContent`. `CMFCMenuButton::SizeToContent` comprueba que el tamaño del botón es suficiente para incluir una flecha que apunta a la ubicación donde la ventana emergente aparecerá: es decir, debajo o a la derecha del botón.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo establecer el identificador del menú asociado al botón, cambiar el tamaño del botón según su tamaño de texto e imagen y el menú emergente que se muestra el marco de trabajo. Este fragmento de código forma parte de la [ejemplo de controles nuevos](../../overview/visual-cpp-samples.md).

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

**Encabezado:** afxmenubutton.h

##  <a name="cmfcmenubutton"></a>  CMFCMenuButton::CMFCMenuButton

Construye un nuevo [CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md) objeto.

```
CMFCMenuButton();
```

##  <a name="m_bosmenu"></a>  CMFCMenuButton::m_bOSMenu

Una variable de miembro booleano que indica qué menú emergente que muestra el marco de trabajo.

```
BOOL m_bOSMenu;
```

### <a name="remarks"></a>Comentarios

Si `m_bOSMenu` es TRUE, el marco llama a heredadas `TrackPopupMenu` método para este objeto. En caso contrario, el marco llama a [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).

##  <a name="m_brightarrow"></a>  CMFCMenuButton::m_bRightArrow

Una variable de miembro booleano que indica la ubicación del menú emergente.

```
BOOL m_bRightArrow;
```

### <a name="remarks"></a>Comentarios

Cuando el usuario presiona el botón de menú, la aplicación muestra un menú emergente. El marco de trabajo mostrará en el menú emergente en el botón o a la derecha del botón. El botón también tiene una pequeña flecha que indica dónde aparecerá el menú emergente. Si `m_bRightArrow` es TRUE, el marco de trabajo muestra el menú emergente a la derecha del botón. En caso contrario, muestra el menú emergente en el botón.

##  <a name="m_bstaypressed"></a>  CMFCMenuButton::m_bStayPressed

Una variable de miembro de tipo Boolean que indica si aparece el botón de menú presionado mientras el usuario realiza una selección en el menú emergente.

```
BOOL m_bStayPressed;
```

### <a name="remarks"></a>Comentarios

Si el `m_bStayPressed` miembro es FALSE, el botón de menú no se convierten en presionado cuando el usuario hace clic en el botón. En este caso, el marco de trabajo muestra sólo el menú emergente.

Si el `m_bStayPressed` miembro es TRUE, se convierte en presiona el botón de menú cuando el usuario hace clic en el botón. Se mantiene presionado hasta después de que el usuario cierra el menú emergente, ya sea realizar una selección o Cancelar.

##  <a name="m_hmenu"></a>  CMFCMenuButton::m_hMenu

El identificador del menú adjunto.

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

El valor de esta variable de miembro es cero si el usuario cancela el menú sin realizar una selección o si se produce un error.

##  <a name="pretranslatemessage"></a>  CMFCMenuButton::PreTranslateMessage

Lo llama el marco para traducir los mensajes de ventana antes de enviarlos.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parámetros

*pMsg*<br/>
[in] Apunta a un [MSG](/windows/desktop/api/winuser/ns-winuser-tagmsg) estructura que contiene el mensaje que se va a procesar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el mensaje ha sido traducido y no se debería enviar; 0 si el mensaje no se ha traducido y debería enviarse.

### <a name="remarks"></a>Comentarios

##  <a name="sizetocontent"></a>  CMFCMenuButton::SizeToContent

Cambia el tamaño del botón según su tamaño de texto y el tamaño de la imagen.

```
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```

### <a name="parameters"></a>Parámetros

*bCalcOnly*<br/>
[in] Un parámetro booleano que indica si este método cambia el tamaño del botón.

### <a name="return-value"></a>Valor devuelto

Un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que especifica el nuevo tamaño del botón.

### <a name="remarks"></a>Comentarios

Si se llama a esta función y *bCalcOnly* es TRUE, `SizeToContent` calculará solo el nuevo tamaño del botón.

Se calcula el nuevo tamaño del botón para ajustar el texto del botón, la imagen y la flecha. También agrega el marco de trabajo de márgenes predefinidos de 10 píxeles del borde horizontal y 5 píxeles del borde vertical.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton (clase)](../../mfc/reference/cmfcbutton-class.md)
