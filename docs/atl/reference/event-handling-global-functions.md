---
title: Funciones globales de control de eventos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
dev_langs:
- C++
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb2c7834e7d5475810973a42ef179ea4f5f0079f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="event-handling-global-functions"></a>Funciones globales de control de eventos
Esta función proporciona un controlador de eventos.  
  
> [!IMPORTANT]
>  La función que se muestran en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
|||  
|-|-|  
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|Espera un objeto que se va a señalar, mientras envía mensajes de ventana según sea necesario.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  

##  <a name="atlwaitwithmessageloop"></a>  AtlWaitWithMessageLoop  
 Espera el objeto que se va a señalizar mientras envía mensajes de ventana según sea necesario.  
  
> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```  
  
### <a name="parameters"></a>Parámetros  
 `hEvent`  
 [in] El identificador de objeto que se va a esperar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** si el objeto se ha señalado.  
  
### <a name="remarks"></a>Comentarios  
 Esto es útil si desea esperar al evento de un objeto a ocurrir y recibir una notificación del mismo sucede, pero permitir que los mensajes de ventana pueden enviar mientras se esperaba.  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../atl/reference/atl-functions.md)
