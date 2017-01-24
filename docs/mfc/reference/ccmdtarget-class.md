---
title: "CCmdTarget Class | Microsoft Docs"
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
  - "CCmdTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCmdTarget class"
  - "enrutamiento de comandos, command targets"
  - "command targets"
  - "message maps, CCmdTarget base class"
  - "destinos, comando"
ms.assetid: 8883b132-2057-4ce0-a5f2-88979f8f2b13
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCmdTarget Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase base para la arquitectura de mapa de mensajes MFC \(Microsoft Foundation Class\).  
  
## Sintaxis  
  
```  
class CCmdTarget : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCmdTarget::CCmdTarget](../Topic/CCmdTarget::CCmdTarget.md)|Crea un objeto `CCmdTarget`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCmdTarget::BeginWaitCursor](../Topic/CCmdTarget::BeginWaitCursor.md)|Muestra el cursor como un cursor de reloj de arena.|  
|[CCmdTarget::DoOleVerb](../Topic/CCmdTarget::DoOleVerb.md)|Produce una acción especificado por un verbo OLE que se va a realizar.|  
|[CCmdTarget::EnableAutomation](../Topic/CCmdTarget::EnableAutomation.md)|permite la automatización OLE para el objeto de `CCmdTarget` .|  
|[CCmdTarget::EnableConnections](../Topic/CCmdTarget::EnableConnections.md)|Habilita el evento que se desencadena sobre los puntos de conexión.|  
|[CCmdTarget::EnableTypeLib](../Topic/CCmdTarget::EnableTypeLib.md)|habilita la biblioteca de tipos de un objeto.|  
|[CCmdTarget::EndWaitCursor](../Topic/CCmdTarget::EndWaitCursor.md)|Vuelve al cursor anterior.|  
|[CCmdTarget::EnumOleVerbs](../Topic/CCmdTarget::EnumOleVerbs.md)|Muestra los verbos de OLE de un objeto.|  
|[CCmdTarget::FromIDispatch](../Topic/CCmdTarget::FromIDispatch.md)|Devuelve un puntero al objeto de `CCmdTarget` asociado con el puntero de `IDispatch` .|  
|[CCmdTarget::GetDispatchIID](../Topic/CCmdTarget::GetDispatchIID.md)|Obtiene la identificación primaria de la interfaz de envío|  
|[CCmdTarget::GetIDispatch](../Topic/CCmdTarget::GetIDispatch.md)|Devuelve un puntero al objeto de `IDispatch` asociado con el objeto de `CCmdTarget` .|  
|[CCmdTarget::GetTypeInfoCount](../Topic/CCmdTarget::GetTypeInfoCount.md)|Recupera el número de interfaces de la información de tipo que un objeto proporciona.|  
|[CCmdTarget::GetTypeInfoOfGuid](../Topic/CCmdTarget::GetTypeInfoOfGuid.md)|Recupera la descripción de tipo que se corresponde con el GUID especificado.|  
|[CCmdTarget::GetTypeLib](../Topic/CCmdTarget::GetTypeLib.md)|Es un puntero a una biblioteca de tipos.|  
|[CCmdTarget::GetTypeLibCache](../Topic/CCmdTarget::GetTypeLibCache.md)|Obtiene la memoria caché de la biblioteca de tipos.|  
|[CCmdTarget::IsInvokeAllowed](../Topic/CCmdTarget::IsInvokeAllowed.md)|Habilita la invocación de método de automatización.|  
|[CCmdTarget::IsResultExpected](../Topic/CCmdTarget::IsResultExpected.md)|Devuelve cero si una función de automatización devuelve un valor.|  
|[CCmdTarget::OnCmdMsg](../Topic/CCmdTarget::OnCmdMsg.md)|Rutas y mensajes de comando de los envíos.|  
|[CCmdTarget::OnFinalRelease](../Topic/CCmdTarget::OnFinalRelease.md)|Limpia después de que se libere la referencia\) del último.|  
|[CCmdTarget::RestoreWaitCursor](../Topic/CCmdTarget::RestoreWaitCursor.md)|restablece el cursor de reloj de arena.|  
  
## Comentarios  
 Un mapa de mensajes enruta comandos o mensajes a las funciones miembro que se escribe para controlarlos.  \(El comando consiste en un mensaje de un elemento de menú, un botón de comando, o una tecla de aceleración.\)  
  
 Las principales clases de marco derivadas de `CCmdTarget` incluyen [CView](../../mfc/reference/cview-class.md), [CWinApp](../../mfc/reference/cwinapp-class.md), [CDocument](../../mfc/reference/cdocument-class.md), [CWnd](../../mfc/reference/cwnd-class.md), y [CFrameWnd](../../mfc/reference/cframewnd-class.md).  Si piensa para una nueva clase controlar mensajes, derive la clase de una de este `CCmdTarget`\- clases derivadas.  Se derivará en una clase de `CCmdTarget` directamente.  
  
 Para obtener información general sobre los destinos y de `OnCmdMsg` de comando de enrutamiento, vea [Destinos de comando](../../mfc/command-targets.md), [Enrutamiento de comandos](../../mfc/command-routing.md), y [Mensajes de asignación](../../mfc/mapping-messages.md).  
  
 `CCmdTarget` incluye las funciones miembro que controlan la presentación de un cursor de reloj de arena.  Muestre el cursor de reloj de arena cuando se espera un comando de tomar un intervalo de tiempo considerable para ejecutarse.  
  
 Envíe los mapas, similares a los mapas de mensajes, se utilizan para exponer la funcionalidad de `IDispatch` de automatización OLE.  Expone esta interfaz, otras aplicaciones \(como Visual Basic\) pueden llamar a la aplicación.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCmdTarget`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo ACDUAL de MFC](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CCmdUI Class](../../mfc/reference/ccmdui-class.md)   
 [CDocument Class](../../mfc/reference/cdocument-class.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [CWinApp Class](../../mfc/reference/cwinapp-class.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [COleDispatchDriver Class](../../mfc/reference/coledispatchdriver-class.md)