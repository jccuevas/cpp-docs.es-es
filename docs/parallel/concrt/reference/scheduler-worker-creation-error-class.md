---
title: scheduler_worker_creation_error (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error::scheduler_worker_creation_error
dev_langs: C++
helpviewer_keywords: scheduler_worker_creation_error class
ms.assetid: 4aec1c3e-c32a-41b2-899d-2d898f23b3c7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0a628d0ce3d85a2bdcae9c7d25550cbd36386e67
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="schedulerworkercreationerror-class"></a>scheduler_worker_creation_error (Clase)
Esta clase describe una excepción producida debido a un error al crear un contexto de ejecución del trabajo en el runtime de simultaneidad.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class scheduler_worker_creation_error : public scheduler_resource_allocation_error;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[scheduler_worker_creation_error)](#ctor)|Sobrecargado. Construye un objeto `scheduler_worker_creation_error`.|  
  
## <a name="remarks"></a>Comentarios  
 Esta excepción normalmente se produce cuando se produce un error en una llamada al sistema operativo para crear contextos de ejecución desde dentro del Runtime de simultaneidad. Contextos de ejecución son subprocesos en los que se ejecutan las tareas en el Runtime de simultaneidad. El código de error que normalmente se devolvería desde una llamada al método Win32 `GetLastError` se convierte en un valor de tipo `HRESULT` y se pueden recuperar mediante el método de clase base `get_error_code`.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 [scheduler_resource_allocation_error)](scheduler-resource-allocation-error-class.md)  
  
 `scheduler_worker_creation_error`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="ctor"></a>scheduler_worker_creation_error) 

 Construye un objeto `scheduler_worker_creation_error`.  
  
```
scheduler_worker_creation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_worker_creation_error(
    HRESULT _Hresult) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `_Message`  
 Mensaje descriptivo del error.  
  
 `_Hresult`  
 El `HRESULT` valor del error que provocó la excepción.  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)
