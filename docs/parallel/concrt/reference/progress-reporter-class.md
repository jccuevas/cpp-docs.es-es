---
title: progress_reporter (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- progress_reporter
- PPLTASKS/concurrency::progress_reporter
- PPLTASKS/concurrency::progress_reporter::progress_reporter
- PPLTASKS/concurrency::progress_reporter::report
dev_langs:
- C++
helpviewer_keywords:
- progress_reporter class
ms.assetid: b836efab-2d05-4649-b6fa-d15236f1f813
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aaac198ab17c33330cbc63d951bfbee97c1d4e94
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="progressreporter-class"></a>progress_reporter (Clase)
La clase del informador de progreso que permite informar de notificaciones de progreso de un tipo específico. Cada objeto progress_reporter se vincula a una acción u operación asincrónica determinada.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<typename _ProgressType>
class progress_reporter;
```  
  
#### <a name="parameters"></a>Parámetros  
 `_ProgressType`  
 El tipo de carga de cada notificación de progreso que se notifican a través del informador de progreso.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[progress_reporter](#ctor)||  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[report](#report)|Envía un informe de progreso a la operación o acción asincrónica a la que está enlazado este informador de progreso.|  
  
## <a name="remarks"></a>Comentarios  
 Este tipo solo está disponible para las aplicaciones de Windows en tiempo de ejecución.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `progress_reporter`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ppltasks.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="ctor"></a> progress_reporter 

```
progress_reporter();
```  
  
##  <a name="report"></a> Informe 

 Envía un informe de progreso a la operación o acción asincrónica a la que está enlazado este informador de progreso.  
  
```
void report(const _ProgressType& val) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `val`  
 La carga de informes a través de una notificación de progreso.  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)
