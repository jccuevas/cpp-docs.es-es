---
title: Puntos de entrada de la interfaz COM
ms.date: 11/04/2016
helpviewer_keywords:
- entry points, COM interfaces
- state management, OLE/COM interfaces
- MFC COM, COM interface entry points
- OLE, interface entry points
- MFC, managing state data
- COM interfaces, entry points
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
ms.openlocfilehash: 0a8db9c6920b4223296f700d084e0b59b9b3ef15
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521224"
---
# <a name="com-interface-entry-points"></a>Puntos de entrada de la interfaz COM

Para las funciones miembro de una interfaz COM, utilice el [METHOD_PROLOGUE](com-interface-entry-points.md#method_prologue) macro para mantener el estado global adecuado al llamar a métodos de una interfaz exportada.

Normalmente, las funciones miembro de las interfaces se implementan por `CCmdTarget`-objetos derivados ya usan esta macro para proporcionar automáticamente la inicialización de la `pThis` puntero. Por ejemplo:

[!code-cpp[NVC_MFCConnectionPoints#5](../mfc/codesnippet/cpp/com-interface-entry-points_1.cpp)]

Para obtener más información, consulte [Nota técnica 38](../mfc/tn038-mfc-ole-iunknown-implementation.md) en MFC/OLE `IUnknown` implementación.

El `METHOD_PROLOGUE` macro se define como:

```cpp
#define METHOD_PROLOGUE(theClass, localClass) \
    theClass* pThis = \
    ((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \
    AFX_MANAGE_STATE(pThis->m_pModuleState) \
```

La parte de la macro relacionada con la administración del estado global es:

`AFX_MANAGE_STATE( pThis->m_pModuleState )`

En esta expresión, *m_pModuleState* se supone que es una variable de miembro del objeto contenedor. Se implementa mediante el `CCmdTarget` clase base y se inicializa en el valor adecuado por `COleObjectFactory`, cuando se crea una instancia del objeto.

## <a name="see-also"></a>Vea también

[Administración de los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

