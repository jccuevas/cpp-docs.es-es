---
title: "Método deferrableeventargs:: Invokeallfinished | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: 86b45205-3edb-4134-9cd0-ed7a7b4c3b1a
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: acae8467ceeaaafea6668d4fbf6b5e2f4884b373
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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