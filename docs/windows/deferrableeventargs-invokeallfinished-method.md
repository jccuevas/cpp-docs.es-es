---
title: 'Método deferrableeventargs:: Invokeallfinished | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 86b45205-3edb-4134-9cd0-ed7a7b4c3b1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 23d521b8373969abdd739b6e4f48eb334284664d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605178"
---
# <a name="deferrableeventargsinvokeallfinished-method"></a>Método DeferrableEventArgs::InvokeAllFinished
Se llama para indicar que se ha completado todo el procesamiento para controlar un evento diferido.
  
## <a name="syntax"></a>Sintaxis
  
```cpp
void InvokeAllFinished()  
```
  
## <a name="remarks"></a>Comentarios
 Debe llamar a este método después de las llamadas de origen del evento [InvokeAll](../windows/eventsource-invokeall-method.md). Llamar a este método evita que se realicen futuros aplazamientos y obliga al controlador de finalización a ejecutarse si no se realizaron aplazamientos.
  
 Para obtener un ejemplo de código, vea [DeferrableEventArgs (clase)](../windows/deferrableeventargs-class.md).
  
## <a name="requirements"></a>Requisitos
 **Encabezado:** event.h
  
 **Espacio de nombres:** Microsoft::WRL
  
## <a name="see-also"></a>Vea también
 [DeferrableEventArgs (clase)](../windows/deferrableeventargs-class.md)  
 [EventSource::InvokeAll (método)](../windows/eventsource-invokeall-method.md)