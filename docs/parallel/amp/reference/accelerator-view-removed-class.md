---
title: accelerator_view_removed (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- accelerator_view_removed
- AMPRT/accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed:accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed:get_view_removed_reason
dev_langs:
- C++
helpviewer_keywords:
- AMPRT/Concurrency::accelerator_view_removed:accelerator_view_removed Class
ms.assetid: 262446de-311c-454e-a5ed-e2aaced0d88a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0426dd44cfcb8f655f3981802dfe23adcd436a0d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="acceleratorviewremoved-class"></a>accelerator_view_removed (Clase)
La excepción que se produce cuando se produce un error en una llamada de DirectX subyacente porque el mecanismo de detección y recuperación de tiempo de espera de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class accelerator_view_removed : public runtime_exception;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[accelerator_view_removed (Constructor)](#ctor)|Inicializa una nueva instancia de la clase `accelerator_view_removed`.|  

### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[get_view_removed_reason](#get_view_removed_reason)|Devuelve un código de error HRESULT que indica la causa de la `accelerator_view` eliminación del objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 `runtime_exception`  
  
 `out_of_memory`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amprt.h  
  
 **Espacio de nombres:** Concurrency  

## <a name="ctor"></a> accelerator_view_removed) 

Inicializa una nueva instancia de la [accelerator_view_removed ()](accelerator-view-removed-class.md) clase.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
explicit accelerator_view_removed(  
    const char * _Message,  
    HRESULT _View_removed_reason ) throw();  
  
explicit accelerator_view_removed(  
    HRESULT _View_removed_reason ) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Message`  
 Descripción del error.  
  
 `_View_removed_reason`  
 Un código de error HRESULT que indica la causa de la eliminación de la `accelerator_view` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Una nueva instancia de la clase accelerator_view_removed ().  
  
## <a name="get_view_removed_reason_method"></a> get_view_removed_reason 

Devuelve un código de error HRESULT que indica la causa de la `accelerator_view` eliminación del objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
HRESULT get_view_removed_reason() const throw();  
```  
  
 
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
