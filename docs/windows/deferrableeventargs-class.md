---
title: Clase DeferrableEventArgs | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9ce2c554ac6d959df868b80c1959a286fb0ef307
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="deferrableeventargs-class"></a>Clase DeferrableEventArgs
Una clase de plantilla utilizada para los tipos de argumento de evento de los aplazamientos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template <  
typename TEventArgsInterface,  
typename TEventArgsClass  
>  
class DeferrableEventArgs : public TEventArgsInterface  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `TEventArgsInterface`  
 El tipo de interfaz que declara los argumentos de un evento diferido.  
  
 `TEventArgsClass`  
 La clase que implementa `TEventArgsInterface`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[DeferrableEventArgs::GetDeferral (método)](../windows/deferrableeventargs-getdeferral-method.md)|Obtiene una referencia a la [aplazamiento](http://go.microsoft.com/fwlink/p/?linkid=526520) el objeto que representa un evento diferido.|  
|[DeferrableEventArgs::InvokeAllFinished (método)](../windows/deferrableeventargs-invokeallfinished-method.md)|Se llama para indicar que se ha completado todo el procesamiento para controlar un evento diferido.|  
  
## <a name="remarks"></a>Comentarios  
 Las instancias de esta clase se pasan a los controladores de eventos para eventos diferidos. Los parámetros de plantilla representan una interfaz que define los detalles de los argumentos de evento de un tipo específico de evento diferido y una clase que implementa esa interfaz.  
  
 La clase aparece como el primer argumento de un controlador de eventos para un evento diferido. Puede llamar a la [GetDeferral](../windows/deferrableeventargs-getdeferral-method.md) método para obtener el [aplazamiento](http://go.microsoft.com/fwlink/p/?linkid=526520) objeto desde el que puede obtener toda la información relativa al evento diferido. Tras completar el control de eventos, debe llamar a Complete en el objeto Aplazamiento. A continuación, debe llamar a [InvokeAllFinished](../windows/deferrableeventargs-invokeallfinished-method.md) al final del método de controlador de eventos, lo que garantiza que la finalización de todos los eventos diferidos se comunique correctamente.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)