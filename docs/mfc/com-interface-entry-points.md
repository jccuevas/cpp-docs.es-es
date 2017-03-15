---
title: "Puntos de entrada de la interfaz COM | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interfaces COM, puntos de entrada"
  - "puntos de entrada, interfaces COM"
  - "MFC COM, puntos de entrada de la interfaz COM"
  - "MFC, administrar datos de estado"
  - "OLE, puntos de entrada de la interfaz"
  - "administración de estados, interfaces OLE/COM"
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Puntos de entrada de la interfaz COM
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para las funciones miembro de interfaz COM, utilice la macro de [METHOD\_PROLOGUE](../Topic/METHOD_PROLOGUE.md) para mantener el estado global adecuada al llamar a métodos de una interfaz exportada.  
  
 Normalmente, las funciones miembro de las interfaces implementadas por `CCmdTarget`\- objetos derivados utilizan ya esta macro para proporcionar inicialización automática de puntero de `pThis` .  Por ejemplo:  
  
 [!code-cpp[NVC_MFCConnectionPoints#5](../mfc/codesnippet/CPP/com-interface-entry-points_1.cpp)]  
  
 Para obtener más información, vea [Nota técnica 38](../mfc/tn038-mfc-ole-iunknown-implementation.md) en la implementación de MFC\/OLE **IUnknown** .  
  
 La macro se define de `METHOD_PROLOGUE` como:  
  
 `#define METHOD_PROLOGUE(theClass, localClass) \`  
  
 `theClass* pThis = \`  
  
 `((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \`  
  
 `AFX_MANAGE_STATE(pThis->m_pModuleState) \`  
  
 La parte de la macro ocuparse de administrar el estado global es:  
  
 `AFX_MANAGE_STATE( pThis->m_pModuleState )`  
  
 En esta expresión, *el m\_pModuleState* se supone que una variable miembro del objeto contenedor.  Se implementa mediante la clase base de `CCmdTarget` y inicializado el valor adecuado para `COleObjectFactory`, cuando se crean instancias del objeto.  
  
## Vea también  
 [Administrar los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md)