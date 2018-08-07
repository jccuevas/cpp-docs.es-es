---
title: InvokeAll (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::InvokeAll
dev_langs:
- C++
helpviewer_keywords:
- InvokeAll method
ms.assetid: 1506618f-0421-4428-a4d0-4ea2b10a3bf6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 04a31c7d080ff4fbfae094e07ab02d912966f4b1
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570662"
---
# <a name="eventsourceinvokeall-method"></a>EventSource::InvokeAll (Método)
Llama a cada controlador de eventos asociado con el actual [EventSource](../windows/eventsource-class.md) objeto utilizando los argumentos y tipos de argumento especificados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void InvokeAll();  
template <  
   typename T0  
>  
void InvokeAll(  
   T0arg0  
);  
template <  
   typename T0,  
   typename T1  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4,  
   typename T5  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4,  
   T5arg5  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4,  
   typename T5,  
   typename T6  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4,  
   T5arg5,  
   T6arg6  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4,  
   typename T5,  
   typename T6,  
   typename T7  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4,  
   T5arg5,  
   T6arg6,  
   T7arg7  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4,  
   typename T5,  
   typename T6,  
   typename T7,  
   typename T8  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4,  
   T5arg5,  
   T6arg6,  
   T7arg7,  
   T8arg8  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4,  
   typename T5,  
   typename T6,  
   typename T7,  
   typename T8,  
   typename T9  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4,  
   T5arg5,  
   T6arg6,  
   T7arg7,  
   T8arg8,  
   T9arg9  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *T0*  
 El tipo del argumento del controlador de evento inicial.  
  
 *T1*  
 El tipo del primer argumento de controlador de eventos.  
  
 *T2*  
 El tipo del segundo argumento de controlador de eventos.  
  
 *T3*  
 El tipo del tercer argumento de controlador de eventos.  
  
 *T4*  
 El tipo del cuarto argumento de controlador de eventos.  
  
 *T5*  
 El tipo del quinto argumento de controlador de eventos.  
  
 *T6*  
 El tipo del sexto argumento de controlador de eventos.  
  
 *T7*  
 El tipo del séptimo argumento de controlador de eventos.  
  
 *T8*  
 El tipo del argumento del controlador de evento de identificador de octava.  
  
 *T9*  
 El tipo del noveno argumento de controlador de eventos.  
  
 *arg0*  
 El argumento de controlador de evento inicial.  
  
 *Arg1*  
 El primer argumento de controlador de eventos.  
  
 *Arg2*  
 El segundo argumento de controlador de eventos.  
  
 *Arg3*  
 El tercer argumento de controlador de eventos.  
  
 *Arg4*  
 El cuarto argumento de controlador de eventos.  
  
 *Arg5*  
 El quinto argumento de controlador de eventos.  
  
 *Arg6*  
 El sexto argumento de controlador de eventos.  
  
 *Arg7*  
 El séptimo argumento de controlador de eventos.  
  
 *Arg8*  
 El argumento de controlador de evento de identificador de octava.  
  
 *Arg9*  
 El noveno argumento de controlador de eventos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [EventSource (clase)](../windows/eventsource-class.md)