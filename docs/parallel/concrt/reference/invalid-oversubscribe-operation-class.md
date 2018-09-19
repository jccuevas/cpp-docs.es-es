---
title: invalid_oversubscribe_operation (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation::invalid_oversubscribe_operation
dev_langs:
- C++
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b4e1eaf4bfca27ef22af103a5696ca2a34265d6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069190"
---
# <a name="invalidoversubscribeoperation-class"></a>invalid_oversubscribe_operation (Clase)
Esta clase describe una excepción cuando se llama al método `Context::Oversubscribe` con el parámetro `_BeginOversubscription` establecido en `false` sin realizar antes una llamada al método `Context::Oversubscribe` con el parámetro `_BeginOversubscription` establecido en `true`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class invalid_oversubscribe_operation : public std::exception;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[invalid_oversubscribe_operation](#ctor)|Sobrecargado. Construye un objeto `invalid_oversubscribe_operation`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 `invalid_oversubscribe_operation`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="ctor"></a> invalid_oversubscribe_operation) 

 Construye un objeto `invalid_oversubscribe_operation`.  
  
```  
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

 
invalid_oversubscribe_operation() throw();
```  
  
### <a name="parameters"></a>Parámetros  
*_Cuerpo*<br/>
Mensaje descriptivo del error.  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)
