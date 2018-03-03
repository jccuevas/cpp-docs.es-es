---
title: CCmdUI (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 32413fe7939b5e5d5d3d41bf32a923dd308f0395
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ccmdui-class"></a>CCmdUI (clase)
Solo se utiliza dentro un `ON_UPDATE_COMMAND_UI` controlador en un `CCmdTarget`-clase derivada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CCmdUI  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCmdUI::ContinueRouting](#continuerouting)|Indica al mecanismo de enrutamiento de comandos para continuar enrutar el mensaje actual hacia abajo de la cadena de controladores.|  
|[A CCmdUI:: Enable](#enable)|Habilita o deshabilita el elemento de interfaz de usuario para este comando.|  
|[CCmdUI::SetCheck](#setcheck)|Establece el estado de activación del elemento de interfaz de usuario para este comando.|  
|[CCmdUI::SetRadio](#setradio)|Al igual que el `SetCheck` función miembro, pero funciona en los grupos de radio.|  
|[CCmdUI::SetText](#settext)|Establece el texto para el elemento de interfaz de usuario para este comando.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCmdUI::m_nID](#m_nid)|El identificador del objeto de interfaz de usuario.|  
|[CCmdUI::m_nIndex](#m_nindex)|El índice del objeto de interfaz de usuario.|  
|[CCmdUI::m_pMenu](#m_pmenu)|Apunta al menú representado por la `CCmdUI` objeto.|  
|[CCmdUI::m_pOther](#m_pother)|Señala al objeto de ventana que envió la notificación.|  
|[CCmdUI::m_pSubMenu](#m_psubmenu)|Señala el submenú independiente representado por la `CCmdUI` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CCmdUI`no tiene una clase base.  
  
 Cuando un usuario de la aplicación extrae hacia abajo de un menú, cada necesidades de elemento de menú para saber si debe mostrarse como habilitado o deshabilitado. El destino de un comando de menú proporciona esta información mediante la implementación de un `ON_UPDATE_COMMAND_UI` controlador. Para cada uno de los objetos de interfaz de usuario de comandos de la aplicación, utilice la ventana Propiedades para crear un prototipo de entrada y la función de asignación de mensajes para cada controlador.  
  
 Cuando se extrae el menú, el marco de trabajo busca y llama a cada uno `ON_UPDATE_COMMAND_UI` controlador, llama a cada controlador `CCmdUI` funciones miembro como **habilitar** y **comprobar**y, a continuación, el marco de trabajo adecuadamente muestra cada elemento de menú.  
  
 Un elemento de menú puede reemplazarse con un botón de barra de control u otro objeto de interfaz de usuario de comando sin cambiar el código dentro de la `ON_UPDATE_COMMAND_UI` controlador.  
  
 En la tabla siguiente se resume el efecto `CCmdUI`de funciones miembro tienen en distintos elementos de interfaz de usuario de comandos.  
  
|Elemento de la interfaz de usuario|Habilitar|SetCheck|SetRadio|SetText|  
|--------------------------|------------|--------------|--------------|-------------|  
|Elemento de menú|Habilita o deshabilita|Activa o desactiva|Comprobaciones mediante un punto|Conjuntos de elementos de texto|  
|Botón de barra de herramientas|Habilita o deshabilita|Se selecciona, se anula la selección, o indeterminado|Igual a `SetCheck`|(No aplicable)|  
|Panel de barra de estado|Convierte el texto visible o invisible|Borde de emergente o normal de conjuntos|Igual a `SetCheck`|Establece el texto del panel|  
|Botón normal en`CDialogBar`|Habilita o deshabilita|Activa o desactiva la casilla de verificación|Igual a `SetCheck`|Establece el texto del botón|  
|Control normal en`CDialogBar`|Habilita o deshabilita|(No aplicable)|(No aplicable)|Establece el texto de la ventana|  
  
 Para obtener más información sobre el uso de esta clase, vea [cómo actualizar objetos de interfaz de usuario](../../mfc/how-to-update-user-interface-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CCmdUI`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="continuerouting"></a>CCmdUI::ContinueRouting  
 Llame a esta función miembro para indicar el mecanismo de enrutamiento de comandos para continuar enrutar el mensaje actual hacia abajo de la cadena de controladores.  
  
```  
void ContinueRouting();
```  
  
### <a name="remarks"></a>Comentarios  
 Se trata de una función miembro avanzado que debe usarse junto con un `ON_COMMAND_EX` controlador que devuelve **FALSE**. Para obtener más información, consulte [6 de nota técnica](../../mfc/tn006-message-maps.md).  
  
##  <a name="enable"></a>A CCmdUI:: Enable  
 Llame a esta función miembro para habilitar o deshabilitar el elemento de interfaz de usuario para este comando.  
  
```  
virtual void Enable(BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bOn`  
 **TRUE** para habilitar el elemento **FALSE** para deshabilitarlo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]  
  
##  <a name="m_nid"></a>CCmdUI::m_nID  
 El identificador del elemento de menú, botón de barra de herramientas u otro objeto de interfaz de usuario representado por la `CCmdUI` objeto.  
  
```  
UINT m_nID;  
```  
  
##  <a name="m_nindex"></a>CCmdUI::m_nIndex  
 El índice del elemento de menú, botón de barra de herramientas u otro objeto de interfaz de usuario representado por la `CCmdUI` objeto.  
  
```  
UINT m_nIndex;  
```  
  
##  <a name="m_pmenu"></a>CCmdUI::m_pMenu  
 Puntero (de `CMenu` tipo) en el menú representado por la `CCmdUI` objeto.  
  
```  
CMenu* m_pMenu;  
```  
  
### <a name="remarks"></a>Comentarios  
 **NULL** si el elemento no es un menú.  
  
##  <a name="m_psubmenu"></a>CCmdUI::m_pSubMenu  
 Puntero (de `CMenu` tipo) en el submenú independiente representado por la `CCmdUI` objeto.  
  
```  
CMenu* m_pSubMenu;  
```  
  
### <a name="remarks"></a>Comentarios  
 **NULL** si el elemento no es un menú. Si el submenú es una ventana emergente, `m_nID` contiene el identificador del primer elemento del menú emergente. Para obtener más información, consulte [21 de nota técnica](../../mfc/tn021-command-and-message-routing.md).  
  
##  <a name="m_pother"></a>CCmdUI::m_pOther  
 Puntero (de tipo `CWnd`) para el objeto de ventana, como una barra de estado o la herramienta, que envía la notificación.  
  
```  
CWnd* m_pOther;  
```  
  
### <a name="remarks"></a>Comentarios  
 **NULL** si el elemento es un menú o no `CWnd` objeto.  
  
##  <a name="setcheck"></a>CCmdUI::SetCheck  
 Llame a esta función miembro para establecer el elemento de interfaz de usuario para este comando en el estado de activación adecuada.  
  
```  
virtual void SetCheck(int nCheck = 1);
```  
  
### <a name="parameters"></a>Parámetros  
 `nCheck`  
 Especifica el estado de verificación para establecer. Si se desactiva el 0, Si las comprobaciones de 1, y si es 2, Establece indeterminado.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro funciona para los elementos de menú y botones de barra de herramientas. El estado indeterminado se aplica solo a los botones de barra de herramientas.  
  
##  <a name="setradio"></a>CCmdUI::SetRadio  
 Llame a esta función miembro para establecer el elemento de interfaz de usuario para este comando en el estado de activación adecuada.  
  
```  
virtual void SetRadio(BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bOn`  
 **TRUE** para habilitar el elemento; en caso contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro funciona igual que `SetCheck`, excepto en que funciona en elementos de interfaz de usuario que actúa como parte de un grupo de radio. Desactive los demás elementos en el grupo no es automática, a menos que los propios elementos mantendrán el comportamiento del grupo de radio.  
  
##  <a name="settext"></a>CCmdUI::SetText  
 Llame a esta función miembro para establecer el texto del elemento de interfaz de usuario para este comando.  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszText`  
 Un puntero a una cadena de texto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MDI de MFC](../../visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)
