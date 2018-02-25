---
title: bad_target Class | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- bad_target
- CONCRT/concurrency::bad_target
- CONCRT/concurrency::bad_target::bad_target
dev_langs:
- C++
helpviewer_keywords:
- bad_target class
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 178d8519516790be3cdb2d9178cc8ffdf144ea23
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="badtarget-class"></a>bad_target (Clase)
Esta clase describe una excepción que se produce cuando un bloque de mensajería recibe un puntero a un destino que no es válido para la operación que se realiza.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class bad_target : public std::exception;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[bad_target](#ctor)|Sobrecargado. Construye un objeto `bad_target`.|  
  
## <a name="remarks"></a>Comentarios  
 Esta excepción se produce normalmente por razones como un destino si se intenta consumir un mensaje que se reserva para un destino diferente o liberando una reserva que no contienen.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 `bad_target`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="ctor"></a> bad_target 

 Construye un objeto `bad_target`.  
  
```
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `_Message`  
 Mensaje descriptivo del error.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [Bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md)



