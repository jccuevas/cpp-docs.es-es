---
title: "progress_reporter (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ppltasks/concurrency::progress_reporter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "progress_reporter (clase)"
ms.assetid: b836efab-2d05-4649-b6fa-d15236f1f813
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# progress_reporter (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase del informador de progreso que permite informar de notificaciones de progreso de un tipo específico.  Cada objeto progress\_reporter se vincula a una acción u operación asincrónica determinada.  
  
## Sintaxis  
  
```  
template<  
   typename _ProgressType  
>  
class progress_reporter;  
```  
  
#### Parámetros  
 `_ProgressType`  
 El tipo de carga de cada notificación de progreso notificada a través del informador de progreso.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[progress\_reporter::progress\_reporter \(Constructor\)](../Topic/progress_reporter::progress_reporter%20Constructor.md)||  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[progress\_reporter::report \(Método\)](../Topic/progress_reporter::report%20Method.md)|Envía un informe de progreso a la acción u operación asincrónica a la que está enlazado este informador de progreso.|  
  
## Comentarios  
 Este tipo solo está disponible para las aplicaciones de la Tienda Windows.  
  
## Jerarquía de herencia  
 `progress_reporter`  
  
## Requisitos  
 **Encabezado:** ppltasks.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [create\_async \(Función\)](../Topic/create_async%20Function.md)