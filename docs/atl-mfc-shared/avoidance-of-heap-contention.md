---
title: "Avoidance of Heap Contention | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "heap contention"
ms.assetid: 797129d7-5f8c-4b0e-8974-bb93217e9ab5
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Avoidance of Heap Contention
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los administradores predeterminados de cadena proporcionados por MFC y ATL son contenedores simples hacia arriba una pila global.  Esta pila global es segura para subprocesos, lo que significa que varios subprocesos pueden asignar y liberar memoria de ella simultáneamente sin dañar la pila.  Para ayudar a proporcionar seguridad para subprocesos, la pila es necesario serializar el acceso a sí mismo.  Esto se realiza normalmente con una sección crítica o un mecanismo de bloqueo similar.  Siempre que el intento de dos subprocesos para tener acceso a la pila simultáneamente, un subproceso está bloqueado hasta que finalice la solicitud de otro subproceso.  Para muchas aplicaciones, esta situación raramente y el impacto en el rendimiento del mecanismo de bloqueo de la pila es insignificante.  Sin embargo, para las aplicaciones que con frecuencia tienen acceso la pila de contención de varios subprocesos para el bloqueo de la pila puede hacer que la aplicación se ejecute más lento que si se tratara de un único subproceso \(incluso en equipos con Varias CPU\).  
  
 Las aplicaciones que utilizan [CStringT](../atl-mfc-shared/reference/cstringt-class.md) son especialmente susceptibles a la contención de la pila porque las operaciones en los objetos de `CStringT` a menudo requieren la reasignación de búfer de cadena.  
  
 Una manera de aliviar la contención de la pila entre subprocesos es hacer que cada subproceso asigna cadenas de un private, pila local de subproceso.  Cuando las cadenas asignadas al asignador de un subproceso determinado se utilizan solo en ese subproceso, el asignador no necesita ser seguros para subprocesos.  
  
## Ejemplo  
 El ejemplo siguiente se muestra un procedimiento de subproceso que asigna su propia pila no privada para cadenas en ese subproceso:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#182](../atl-mfc-shared/codesnippet/CPP/avoidance-of-heap-contention_1.cpp)]  
  
## Comentarios  
 Varios subprocesos pueden ejecutarse utilizando este mismo procedimiento de subproceso pero puesto que cada subproceso dispone de su propia pila no hay contención entre los subprocesos.  Además, el hecho de que cada pila no es segura para subprocesos proporciona una mejora apreciable en rendimiento aunque sólo una copia del subproceso se está ejecutando.  Éste es el resultado de pila no utilizando las operaciones entrelazadas costosas a proteger contra el acceso simultáneo.  
  
 Para un procedimiento más complicado de subprocesos, puede ser conveniente almacenar un puntero al administrador de la cadena de subproceso en una ranura \(TLS\) de almacenamiento local de subprocesos.  Esto permite que otras funciones llamadas por el procedimiento de subproceso para tener acceso al administrador de la cadena de subproceso.  
  
## Vea también  
 [Memory Management with CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)