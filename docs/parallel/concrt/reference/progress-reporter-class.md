---
title: progress_reporter (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 98856e26c82d01433e6f8eb0d76110aff1535936
ms.lasthandoff: 03/17/2017

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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[progress_reporter](#ctor)||  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[informe](#report)|Envía un informe de progreso a la operación o acción asincrónica a la que está enlazado este informador de progreso.|  
  
## <a name="remarks"></a>Comentarios  
 Este tipo solo está disponible para las aplicaciones de la Tienda Windows.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `progress_reporter`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ppltasks.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="ctor"></a>progress_reporter 

```
progress_reporter();
```  
  
##  <a name="report"></a>informe 

 Envía un informe de progreso a la operación o acción asincrónica a la que está enlazado este informador de progreso.  
  
```
void report(const _ProgressType& val) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `val`  
 La carga de informes a través de una notificación de progreso.  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)

