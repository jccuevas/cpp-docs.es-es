---
title: Puntos de entrada de la interfaz COM | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- entry points, COM interfaces
- state management, OLE/COM interfaces
- MFC COM, COM interface entry points
- OLE, interface entry points
- MFC, managing state data
- COM interfaces, entry points
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 010df3546a6ac2b6276281c39efdd76abd5ec222
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="com-interface-entry-points"></a>Puntos de entrada de la interfaz COM
Para las funciones miembro de una interfaz COM, utilice la [METHOD_PROLOGUE](com-interface-entry-points.md#method_prologue) macro para mantener el estado global adecuado al llamar a métodos de una interfaz exportada.  
  
 Normalmente, las funciones miembro de las interfaces se implementan mediante `CCmdTarget`-objetos derivados ya utilizan esta macro para proporcionar automáticamente la inicialización de la `pThis` puntero. Por ejemplo:  
  
 [!code-cpp[NVC_MFCConnectionPoints#5](../mfc/codesnippet/cpp/com-interface-entry-points_1.cpp)]  
  
 Para obtener más información, consulte [Nota técnica 38](../mfc/tn038-mfc-ole-iunknown-implementation.md) en MFC/OLE **IUnknown** implementación.  
  
 El `METHOD_PROLOGUE` macro se define como:  
  
 `#define METHOD_PROLOGUE(theClass, localClass) \`  
  
 `theClass* pThis = \`  
  
 `((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \`  
  
 `AFX_MANAGE_STATE(pThis->m_pModuleState) \`  
  
 La parte de la macro relacionada con la administración del estado global es:  
  
 `AFX_MANAGE_STATE( pThis->m_pModuleState )`  
  
 En esta expresión, *m_pModuleState* se supone que es una variable de miembro del objeto contenedor. Se implementa mediante el `CCmdTarget` clase base y se inicializa en el valor adecuado por `COleObjectFactory`, cuando se crea una instancia del objeto.  
  
## <a name="see-also"></a>Vea también  
 [Administración de los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

