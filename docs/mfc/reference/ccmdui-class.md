---
title: "CCmdUI Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CCmdUI"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "botones [C++], actualizar cuando el contexto cambia"
  - "CCmdUI class"
  - "command user interface"
  - "comandos [C++], updating UI"
  - "menus [C++], actualizar cuando el contexto cambia"
  - "estados, updating user interface object"
  - "barras de herramientas [C++], actualizar"
  - "updating user interfaces for commands"
  - "interfaces de usuario, actualizar"
ms.assetid: 04eaaaf5-f510-48ab-b425-94665ba24766
caps.latest.revision: 21
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCmdUI Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Solo se utiliza dentro de un controlador en `CCmdTarget`\- clase derivada de `ON_UPDATE_COMMAND_UI` .  
  
## Sintaxis  
  
```  
class CCmdUI  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCmdUI::ContinueRouting](../Topic/CCmdUI::ContinueRouting.md)|Indica al mecanismo de comando\- enrutamiento que continúe distribuyendo el mensaje actual bajar la cadena de controladores.|  
|[CCmdUI::Enable](../Topic/CCmdUI::Enable.md)|Permisos o neutralizaciones el elemento de interfaz de usuario para este comando.|  
|[CCmdUI::SetCheck](../Topic/CCmdUI::SetCheck.md)|Establece el estado de activación de elementos de interfaz de usuario para este comando.|  
|[CCmdUI::SetRadio](../Topic/CCmdUI::SetRadio.md)|Como la función miembro de `SetCheck` , pero se utiliza con grupos de radio.|  
|[CCmdUI::SetText](../Topic/CCmdUI::SetText.md)|Establece el texto para el elemento de interfaz de usuario para este comando.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCmdUI::m\_nID](../Topic/CCmdUI::m_nID.md)|El id. de objeto de la interfaz de usuario.|  
|[CCmdUI::m\_nIndex](../Topic/CCmdUI::m_nIndex.md)|El índice del objeto de la interfaz de usuario.|  
|[CCmdUI::m\_pMenu](../Topic/CCmdUI::m_pMenu.md)|Los puntos al menú representado por `CCmdUI` se oponen.|  
|[CCmdUI::m\_pOther](../Topic/CCmdUI::m_pOther.md)|Señala la ventana se oponen que envía la notificación.|  
|[CCmdUI::m\_pSubMenu](../Topic/CCmdUI::m_pSubMenu.md)|Los puntos al submenú contenido representado por `CCmdUI` se oponen.|  
  
## Comentarios  
 `CCmdUI` no tiene una clase base.  
  
 Cuando un usuario de la aplicación spline bajarán un menú, cada elemento de menú necesita saber si se mostrará como habilitado o deshabilitado.  El destino de un comando de menú proporciona esta información implementar un controlador de `ON_UPDATE_COMMAND_UI` .  Para cada uno de los objetos de la interfaz de usuario del comando en la aplicación, use la ventana Propiedades para crear un prototipo de entrada y la función de mensaje\- mapa para cada controlador.  
  
 Cuando se spline abajo el menú, el marco de las llamadas cada controlador de `ON_UPDATE_COMMAND_UI` , las funciones de cada controlador de las llamadas miembro de `CCmdUI` como **Habilitar** y **Activar**, y el marco después se muestran correctamente cada elemento de menú.  
  
 Un elemento de menú se puede reemplazar con el botón de la barra de control u otro objeto de la interfaz de usuario del comando sin cambiar el código del controlador de `ON_UPDATE_COMMAND_UI` .  
  
 La tabla siguiente se resume el miembro de entity\_CODECCmdUI en el efecto que las funciones tienen en diferentes elementos de la interfaz de usuario del comando.  
  
|Elemento de la interfaz de usuario|Habilitar|SetCheck|SetRadio|SetText|  
|----------------------------------------|---------------|--------------|--------------|-------------|  
|Elemento de menú|Permisos o neutralizaciones|Las comprobaciones \(x\) o desactivan|Comprobaciones utilizando el punto \(•\)|Establece el texto del elemento|  
|Botón de la barra de herramientas|Permisos o neutralizaciones|Selecciona, los anula, o indeterminado|Igual que `SetCheck`|\(No aplicable\)|  
|Panel de barra de estado|Haga el texto visible o invisible|Establece pop \- out o el borde normal|Igual que `SetCheck`|Establece el texto del panel|  
|Botón normal en `CDialogBar`|Permisos o neutralizaciones|Las comprobaciones o desactiva la casilla|Igual que `SetCheck`|Establece el texto del botón|  
|Control normal en `CDialogBar`|Permisos o neutralizaciones|\(No aplicable\)|\(No aplicable\)|Establece el texto de la ventana|  
  
 Para obtener más información sobre el uso de esta clase, vea [cómo actualizar objetos de la Usuario\-Interfaz](../../mfc/how-to-update-user-interface-objects.md).  
  
## Jerarquía de herencia  
 `CCmdUI`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo MDI de MFC](../../top/visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)