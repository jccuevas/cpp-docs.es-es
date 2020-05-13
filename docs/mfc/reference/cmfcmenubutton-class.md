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
ms.openlocfilehash: 929fc1c8166f249fe3babc724b2c0bcd9cb99676
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369709"
---
# <a name="cmfcmenubutton-class"></a>CMFCMenuButton (clase)

Un botón que muestra un menú emergente e informes en las selecciones de menú del usuario.

## <a name="syntax"></a>Sintaxis

```
class CMFCMenuButton : public CMFCButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCMenuButton::CMFCMenuButton](#cmfcmenubutton)|Construye un objeto `CMFCMenuButton`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|Llamado por el marco de trabajo para traducir los mensajes de ventana antes de que se distribuyen. (Invalida `CMFCButton::PreTranslateMessage`).|
|[CMFCMenuButton::SizeToContent](#sizetocontent)|Cambia el tamaño del botón según su texto y el tamaño de la imagen.|

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|Especifica si se debe mostrar el menú emergente predeterminado del sistema o utilizar [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).|
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|Especifica si el menú emergente aparecerá debajo o a la derecha del botón.|
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|Especifica si el botón de menú cambia su estado después de que el usuario suelte el botón.|
|[CMFCMenuButton::m_hMenu](#m_hmenu)|Identificador del menú de Windows adjunto.|
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|Identificador que indica qué elemento seleccionó el usuario en el menú emergente.|
|[CMFCMenuButton::m_bDefaultClick](#m_bdefaultclick)| Permitir el procesamiento predeterminado (en el texto/imagen del botón).|

## <a name="remarks"></a>Observaciones

La `CMFCMenuButton` clase se deriva de la [CMFCButton (Clase)](../../mfc/reference/cmfcbutton-class.md) que, a su vez, se deriva de la [clase CButton](../../mfc/reference/cbutton-class.md). Por lo tanto, puede usar `CMFCMenuButton` en el `CButton`código de la misma manera que usaría .

Al crear `CMFCMenuButton`un , debe pasar un identificador al menú emergente asociado. A continuación, `CMFCMenuButton::SizeToContent`llame a la función . `CMFCMenuButton::SizeToContent`comprueba que el tamaño del botón es suficiente para incluir una flecha que apunte a la ubicación donde aparecerá la ventana emergente, a saber, debajo o a la derecha del botón.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo establecer el identificador del menú adjunto al botón, cambiar el tamaño del botón según su texto y tamaño de imagen y establecer el menú emergente que muestra el marco de trabajo. Este fragmento de código forma parte del [ejemplo New Controls](../../overview/visual-cpp-samples.md).

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

## <a name="cmfcmenubuttoncmfcmenubutton"></a><a name="cmfcmenubutton"></a>CMFCMenuButton::CMFCMenuButton

Construye un nuevo [CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md) objeto.

```
CMFCMenuButton();
```

## <a name="cmfcmenubuttonm_bosmenu"></a><a name="m_bosmenu"></a>CMFCMenuButton::m_bOSMenu

Una variable miembro booleana que indica qué menú emergente muestra el marco de trabajo.

```
BOOL m_bOSMenu;
```

### <a name="remarks"></a>Observaciones

Si `m_bOSMenu` es TRUE, el `TrackPopupMenu` marco de trabajo llama al método heredado para este objeto. De lo contrario, el marco de trabajo llama [a CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).

## <a name="cmfcmenubuttonm_brightarrow"></a><a name="m_brightarrow"></a>CMFCMenuButton::m_bRightArrow

Variable miembro booleana que indica la ubicación del menú emergente.

```
BOOL m_bRightArrow;
```

### <a name="remarks"></a>Observaciones

Cuando el usuario presiona el botón de menú, la aplicación muestra un menú emergente. El marco de trabajo mostrará el menú emergente debajo del botón o a la derecha del botón. El botón también tiene una pequeña flecha que indica dónde aparecerá el menú emergente. Si `m_bRightArrow` es TRUE, el marco de trabajo muestra el menú emergente a la derecha del botón. De lo contrario, muestra el menú emergente debajo del botón.

## <a name="cmfcmenubuttonm_bstaypressed"></a><a name="m_bstaypressed"></a>CMFCMenuButton::m_bStayPressed

Una variable miembro booleana que indica si el botón de menú aparece presionado mientras el usuario realiza una selección en el menú emergente.

```
BOOL m_bStayPressed;
```

### <a name="remarks"></a>Observaciones

Si `m_bStayPressed` el miembro es FALSE, el botón de menú no se presiona cuando los usos hacen clic en el botón. En este caso, el marco de trabajo solo muestra el menú emergente.

Si `m_bStayPressed` el miembro es TRUE, el botón de menú se presiona cuando el usuario hace clic en el botón. Permanece presionado hasta que el usuario cierra el menú emergente, ya sea haciendo una selección o cancelando.

## <a name="cmfcmenubuttonm_hmenu"></a><a name="m_hmenu"></a>CMFCMenuButton::m_hMenu

El asa del menú adjunto.

```
HMENU m_hMenu;
```

### <a name="remarks"></a>Observaciones

El marco de trabajo muestra el menú indicado por esta variable miembro cuando el usuario hace clic en el botón de menú.

## <a name="cmfcmenubuttonm_nmenuresult"></a><a name="m_nmenuresult"></a>CMFCMenuButton::m_nMenuResult

Entero que indica qué elemento selecciona el usuario en el menú emergente.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Observaciones

El valor de esta variable miembro es cero si el usuario cancela el menú sin realizar una selección o si se produce un error.

## <a name="cmfcmenubuttonm_bdefaultclick"></a><a name="m_bdefaultclick"></a>CMFCMenuButton::m_bDefaultClick

Permite el procesamiento predeterminado de texto o imágenes en el botón.

```
BOOL  m_bDefaultClick;
```

### <a name="remarks"></a>Observaciones

Si se establece m_bDefaultClick en false, el botón mostrará el menú al hacer clic en cualquier parte del botón.

## <a name="cmfcmenubuttonm_nmenuresult"></a><a name="m_nmenuresult"></a>CMFCMenuButton::m_nMenuResult

Entero que indica qué elemento selecciona el usuario en el menú emergente.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Observaciones

## <a name="cmfcmenubuttonpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCMenuButton::PreTranslateMessage

Llamado por el marco de trabajo para traducir los mensajes de ventana antes de que se distribuyen.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parámetros

*Pmsg*<br/>
[en] Apunta a una estructura [MSG](/windows/win32/api/winuser/ns-winuser-msg) que contiene el mensaje que se debe procesar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el mensaje se tradujo y no se debe distribuir; 0 si el mensaje no se ha traducido y debe enviarse.

### <a name="remarks"></a>Observaciones

## <a name="cmfcmenubuttonsizetocontent"></a><a name="sizetocontent"></a>CMFCMenuButton::SizeToContent

Cambia el tamaño del botón según su tamaño de texto y tamaño de imagen.

```
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```

### <a name="parameters"></a>Parámetros

*bCalcOnly*<br/>
[en] Un parámetro booleano que indica si este método cambia el tamaño del botón .

### <a name="return-value"></a>Valor devuelto

Un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que especifica el nuevo tamaño para el botón.

### <a name="remarks"></a>Observaciones

Si llama a esta función y `SizeToContent` *bCalcOnly* es TRUE, calculará solo el nuevo tamaño del botón.

El nuevo tamaño del botón se calcula para ajustarse al texto, la imagen y la flecha del botón. El marco de trabajo también agrega márgenes predefinidos de 10 píxeles para el borde horizontal y 5 píxeles para el borde vertical.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton (Clase)](../../mfc/reference/cmfcbutton-class.md)
