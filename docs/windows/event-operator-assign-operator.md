---
title: 'Event:: operator = (operador) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: d8fe9820-8856-4899-9553-56226bdc4945
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d3da41ff7fd145889ec799bb2f8ebe99aed36934
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="eventoperator-operator"></a>Event::operator= (Operador)
Asigna la referencia de evento especificada a la instancia de evento actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
WRL_NOTHROW Event& operator=(  
   _Inout_ Event&& h  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `h`  
 Una referencia a valor r a una instancia de evento.  
  
## <a name="return-value"></a>Valor devuelto  
 Un puntero a la instancia actual de eventos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Event (clase) (Biblioteca de plantillas C++ de Windows en tiempo de ejecución)](../windows/event-class-windows-runtime-cpp-template-library.md)