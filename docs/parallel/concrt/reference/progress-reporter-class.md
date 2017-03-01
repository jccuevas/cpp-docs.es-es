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
- ppltasks/concurrency::progress_reporter
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
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: c6b4dfee5b5f9df98a36fcdac116182ced4cbe30
ms.lasthandoff: 02/24/2017

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
|[progress_reporter (Constructor)](#ctor)||  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[informe (método)](#report)|Envía un informe de progreso a la operación o acción asincrónica a la que está enlazado este informador de progreso.|  
  
## <a name="remarks"></a>Comentarios  
 Este tipo solo está disponible para las aplicaciones de la Tienda Windows.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `progress_reporter`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ppltasks.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-namectora-progressreporter"></a><a name="ctor"></a>progress_reporter 

```
progress_reporter();
```  
  
##  <a name="a-namereporta-report"></a><a name="report"></a>informe 

 Envía un informe de progreso a la operación o acción asincrónica a la que está enlazado este informador de progreso.  
  
```
void report(const _ProgressType& val) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `val`  
 La carga de informes a través de una notificación de progreso.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)

