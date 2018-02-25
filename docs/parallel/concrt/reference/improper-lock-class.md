---
title: improper_lock (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- improper_lock
- CONCRT/concurrency::improper_lock
- CONCRT/concurrency::improper_lock::improper_lock
dev_langs:
- C++
helpviewer_keywords:
- improper_lock class
ms.assetid: 8f494942-7748-4a2a-8de2-23414bfe6346
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 37cf615460cda6d0f33f0431e258cac843f456c4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="improperlock-class"></a>improper_lock (Clase)
Esta clase describe una excepción que se produce cuando se realiza un bloqueo de forma incorrecta.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class improper_lock : public std::exception;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[improper_lock](#ctor)|Sobrecargado. Construye un objeto `improper_lock exception`.|  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, esta excepción se produce cuando se realiza un intento de adquirir un bloqueo no reentrante de forma recursiva en el mismo contexto.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 `improper_lock`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="ctor"></a> improper_lock) 

 Construye un objeto `improper_lock exception`.  
  
```
explicit _CRTIMP improper_lock(_In_z_ const char* _Message) throw();

improper_lock() throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `_Message`  
 Mensaje descriptivo del error.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [critical_section (clase)](critical-section-class.md)   
 [reader_writer_lock (clase)](reader-writer-lock-class.md)
