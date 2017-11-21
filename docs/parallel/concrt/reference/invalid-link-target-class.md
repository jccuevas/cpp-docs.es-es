---
title: invalid_link_target (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- invalid_link_target
- CONCRT/concurrency::invalid_link_target
- CONCRT/concurrency::invalid_link_target::invalid_link_target
dev_langs: C++
helpviewer_keywords: invalid_link_target class
ms.assetid: 33b64885-34d8-4d4e-a893-02e9f19c958e
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6335c51ef9edc97d1b44a6ed6bade6b653a87101
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="invalidlinktarget-class"></a>invalid_link_target (Clase)
Esta clase describe una excepción que se produce cuando se llama al método `link_target` de un bloque de mensajería y el bloque de mensajería no se puede vincular al destino. Este puede ser el resultado de superar el número de vínculos que se permiten en el bloque de mensajería o de intentar vincular un destino específico al mismo origen dos veces.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class invalid_link_target : public std::exception;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[invalid_link_target)](#ctor)|Sobrecargado. Construye un objeto `invalid_link_target`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 `invalid_link_target`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="ctor"></a>invalid_link_target) 

 Construye un objeto `invalid_link_target`.  
  
```
explicit _CRTIMP invalid_link_target(_In_z_ const char* _Message) throw();

invalid_link_target() throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `_Message`  
 Mensaje descriptivo del error.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [Bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md)



