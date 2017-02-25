---
title: "EventTargetArray::EventTargetArray (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EventTargetArray, constructor"
ms.assetid: 6c6d3737-3cd3-4515-a8f6-d27901bb8ed2
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# EventTargetArray::EventTargetArray (Constructor)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
EventTargetArray(  
   _Out_ HRESULT* hr,  
   size_t items  
);  
```  
  
#### Parámetros  
 `hr`  
 Después de operaciones de este constructor, el parámetro `hr` indica si la asignación de la matriz se realizó correctamente o no.  La tabla siguiente se enumeran los posibles valores para `hr`.  
  
 S\_OK  
 La operación correcta.  
  
 E\_OUTOFMEMORY  
 Memoria no se pudo asignar para la matriz.  
  
 S\_FALSE  
 El parámetro `items` es menor o igual que cero.  
  
 `items`  
 El número de elementos de matriz para asignar.  
  
## Comentarios  
 Inicializa una nueva instancia de la clase de EventTargetArray.  
  
 EventTargetArray se utiliza para mantener una matriz de controladores de eventos en un objeto de EventSource.  
  
## Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [EventTargetArray \(Clase\)](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)