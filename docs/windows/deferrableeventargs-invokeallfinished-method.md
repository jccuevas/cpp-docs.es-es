---
title: 'Método deferrableeventargs:: Invokeallfinished | Documentos de Microsoft'
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
ms.openlocfilehash: 1aaaf8c6849b30e26463810ff353234319960048
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="deferrableeventargsinvokeallfinished-method"></a>Método DeferrableEventArgs::InvokeAllFinished
Se llama para indicar que se ha completado todo el procesamiento para controlar un evento diferido.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
void InvokeAllFinished()  
```  
  
## <a name="remarks"></a>Comentarios  
 Debe llamar a este método después de las llamadas del origen de evento [InvokeAll](../windows/eventsource-invokeall-method.md). Llamar a este método evita que se realicen futuros aplazamientos y obliga al controlador de finalización a ejecutarse si no se realizaron aplazamientos.  
  
 Para obtener un ejemplo de código, vea [clase DeferrableEventArgs](../windows/deferrableeventargs-class.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Clase DeferrableEventArgs](../windows/deferrableeventargs-class.md)   
 [EventSource::InvokeAll (método)](../windows/eventsource-invokeall-method.md)