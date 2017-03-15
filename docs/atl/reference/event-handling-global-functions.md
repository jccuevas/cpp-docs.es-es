---
title: Funciones globales de control de eventos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 4bf2a8b0211361f5d5d2bf0f996e978638631116
ms.lasthandoff: 02/24/2017

---
# <a name="event-handling-global-functions"></a>Funciones globales de control de eventos
Esta función proporciona un controlador de eventos.  
  
> [!IMPORTANT]
>  La función que se muestran en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
|||  
|-|-|  
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|Espera un objeto que se va a señalar, mientras envía mensajes de ventana según sea necesario.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  

##  <a name="a-nameatlwaitwithmessageloopa--atlwaitwithmessageloop"></a><a name="atlwaitwithmessageloop"></a>AtlWaitWithMessageLoop  
 Espera el objeto que se va a señalizar mientras envía mensajes de ventana según sea necesario.  
  
> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```  
  
### <a name="parameters"></a>Parámetros  
 `hEvent`  
 [in] Identificador del objeto que se va a esperar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** si el objeto se ha señalado.  
  
### <a name="remarks"></a>Comentarios  
 Esto es útil si desea esperar a los eventos de un objeto a suceder y recibir una notificación de se produzcan, pero permitir que los mensajes de ventana se distribuyan mientras espera.  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../atl/reference/atl-functions.md)

