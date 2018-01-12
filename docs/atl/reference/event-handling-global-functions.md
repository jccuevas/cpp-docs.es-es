---
title: Funciones globales de control de eventos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: atlbase/ATL::AtlWaitWithMessageLoop
dev_langs: C++
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6670ef283d24f57b407ad70693421feae427855f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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

##  <a name="atlwaitwithmessageloop"></a>AtlWaitWithMessageLoop  
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
