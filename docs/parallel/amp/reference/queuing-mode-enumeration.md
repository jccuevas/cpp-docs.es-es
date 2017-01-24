---
title: "queuing_mode (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amprt/Concurrency::queuing_mode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "queuing_mode (enumeración)"
ms.assetid: 8c641054-906d-40b3-bbb4-f62af9356a14
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# queuing_mode (Enumeraci&#243;n)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Especifica los modos de la puesta en cola que se admiten en el acelerador.  
  
## Sintaxis  
  
```  
enum queuing_mode;  
```  
  
## Miembros  
  
### Valores  
  
|Name|Descripción|  
|----------|-----------------|  
|`queuing_mode_immediate`|Un modo de puesta en cola que especifica que cualquier comando, por ejemplo, [parallel\_for\_each \(Función\) \(C\+\+ AMP\)](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md), se envía al dispositivo acelerador correspondiente en cuanto el comando devuelva el control al que hizo la llamada.|  
|`queuing_mode_automatic`|Un modo de puesta en cola que especifica que los comandos se encolan en una cola de comando que corresponde al objeto [accelerator\_view](../../../parallel/amp/reference/accelerator-view-class.md).  Los comandos se envían al dispositivo cuando se llama a [accelerator\_view::flush](../Topic/accelerator_view::flush%20Method.md).|  
  
## Requisitos  
 **Encabezado:** amprt.h  
  
 **Espacio de nombres:** Simultaneidad  
  
## Vea también  
 [Espacio de nombres de simultaneidad \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)