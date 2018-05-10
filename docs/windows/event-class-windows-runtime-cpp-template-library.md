---
title: Clase de eventos (biblioteca de plantillas C++ de Windows en tiempo de ejecución) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event
dev_langs:
- C++
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 12c9e5bfe01de0a9864ff1e94364e0c42178ad11
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="event-class-windows-runtime-c-template-library"></a>Event (Clase) (Biblioteca de plantillas C++ de Windows en tiempo de ejecución)
Representa un evento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class Event : public HandleT<HandleTraits::EventTraits>;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Event::Event (constructor) (Biblioteca de plantillas C++ de Windows en tiempo de ejecución)](../windows/event-event-constructor-windows-runtime-cpp-template-library.md)|Inicializa una nueva instancia de la clase Event.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Event::operator= (operador)](../windows/event-operator-assign-operator.md)|Asigna la referencia de evento especificada a la instancia de evento actual.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `HandleT`  
  
 `Event`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers (espacio de nombres)](../windows/microsoft-wrl-wrappers-namespace.md)