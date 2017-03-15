---
title: "Crear colecciones de pila y de cola | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases de colección, crear"
  - "colecciones, poner en cola"
  - "colecciones, pila"
  - "clases de la colección MFC, colecciones de cola"
  - "clases de la colección MFC, colecciones de pila"
  - "colecciones de cola"
  - "pila"
  - "colecciones de pila"
ms.assetid: 3c7bc198-35f0-4fc3-aaed-6005a0f22638
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Crear colecciones de pila y de cola
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica cómo crear otras estructuras de datos, como [montones](#_core_stacks) y [colas](#_core_queues), clases de la lista de MFC.  Los ejemplos utilizan las clases derivadas de `CList`, pero puede utilizar `CList` directamente a menos que necesite agregar funcionalidad.  
  
##  <a name="_core_stacks"></a> Montones  
 Puesto que la colección de listas estándar tiene un encabezado y una cola, es fácil crear una colección de listas derivada que imita el comportamiento de una pila LIFO \(último en entrar, primero en salir\).  Un montón es como una pila de bandejas en una cafetería.  Mientras que las bandejas se agregan a la pila, van encima de la pila.  La bandeja última agregada es la primera que se quitará.  Las funciones `AddHead` y `RemoveHead` miembro de la colección de listas se pueden utilizar para agregar y quitar elementos específicamente de encabezado de la lista; así, el elemento recientemente agregado es el primero que se quitará.  
  
#### Para crear una colección de pila  
  
1.  Derive una nueva clase de lista a partir de una de las clases existentes de la lista de MFC y agregue más funciones miembro para admitir la funcionalidad de las operaciones del montón.  
  
     El ejemplo siguiente se muestra cómo agregar funciones miembro a los elementos de la inserción en la pila, recurrir a escondidas en el elemento superior de la pila, y extraer el elemento superior de la pila:  
  
     [!code-cpp[NVC_MFCCollections#20](../mfc/codesnippet/CPP/creating-stack-and-queue-collections_1.h)]  
  
 Observe que este enfoque expone la clase subyacente de `CObList` .  El usuario puede llamar a la función miembro de `CObList` , si tiene sentido para una pila o no.  
  
##  <a name="_core_queues"></a> Colas  
 Puesto que la colección de listas estándar tiene un encabezado y una cola, también es fácil crear una colección de listas derivada que imita el comportamiento de una cola primero en entrar, primero en salir.  Una cola es como una línea de personas en una cafetería.  La primera person de la línea es la primera que se procesará.  Mientras proceden más personas, ir al final de la línea para esperar el giro.  Las funciones `AddTail` y `RemoveHead` miembro de la colección de listas se pueden utilizar para agregar y quitar elementos específicamente el encabezado o de la cola de la lista; así, el elemento recientemente agregado siempre es el último que se quitará.  
  
#### Para crear una colección de cola  
  
1.  Derive una nueva clase de lista a partir de una de las clases predefinidas de lista proporcionadas en la biblioteca Microsoft Foundation Class\) y agregue más funciones miembro para admitir la semántica de las operaciones de la cola.  
  
     El ejemplo siguiente muestra cómo puede anexar funciones miembro para agregar un elemento al final de la cola y obtener el elemento de delante de la cola.  
  
     [!code-cpp[NVC_MFCCollections#21](../mfc/codesnippet/CPP/creating-stack-and-queue-collections_2.h)]  
  
## Vea también  
 [Colecciones](../mfc/collections.md)