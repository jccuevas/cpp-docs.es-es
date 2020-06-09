---
title: Puntos de entrada de la interfaz COM
ms.date: 03/27/2019
helpviewer_keywords:
- entry points, COM interfaces
- state management, OLE/COM interfaces
- MFC COM, COM interface entry points
- OLE, interface entry points
- MFC, managing state data
- COM interfaces, entry points
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
ms.openlocfilehash: 132dd7394119081dcaeb098c2088782ff5d40ae4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619334"
---
# <a name="com-interface-entry-points"></a>Puntos de entrada de la interfaz COM

En el caso de las funciones miembro de una interfaz COM, utilice la `METHOD_PROLOGUE` macro para mantener el estado global adecuado al llamar a los métodos de una interfaz exportada.

Normalmente, las funciones miembro de interfaces implementadas por `CCmdTarget` objetos derivados de ya usan esta macro para proporcionar la inicialización automática del `pThis` puntero. Por ejemplo:

[!code-cpp[NVC_MFCConnectionPoints#5](codesnippet/cpp/com-interface-entry-points_1.cpp)]

Para obtener más información, vea la [Nota técnica 38](tn038-mfc-ole-iunknown-implementation.md) sobre la implementación de MFC/OLE `IUnknown` .

La `METHOD_PROLOGUE` macro se define como:

```cpp
#define METHOD_PROLOGUE(theClass, localClass) \
    theClass* pThis = \
    ((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \
    AFX_MANAGE_STATE(pThis->m_pModuleState) \
```

La parte de la macro que se refiere a la administración del estado global es:

`AFX_MANAGE_STATE( pThis->m_pModuleState )`

En esta expresión, se supone que *m_pModuleState* es una variable miembro del objeto contenedor. Lo implementa la `CCmdTarget` clase base y se inicializa en el valor adecuado de `COleObjectFactory` , cuando se crea una instancia del objeto.

## <a name="see-also"></a>Consulte también

[Administrar los datos de estado de los módulos MFC](managing-the-state-data-of-mfc-modules.md)
