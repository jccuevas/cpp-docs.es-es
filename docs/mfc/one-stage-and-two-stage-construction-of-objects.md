---
title: "Construcci&#243;n de objetos en una fase y en dos fases | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "creación de objetos, objetos gráficos"
  - "objetos [C++], crear objetos gráficos"
  - "objetos [C++], objetos gráficos"
  - "construcción de objetos en una fase y en dos fases"
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Construcci&#243;n de objetos en una fase y en dos fases
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede elegir entre dos técnicas para crear objetos gráficos, como lápices y pinceles:  
  
-   *construcción de la Uno\- fase*: Cree e inicialice el objeto en una fase, todas con el constructor.  
  
-   *Construcción de dos pasos*: Cree e inicialice el objeto en dos fases independientes.  El constructor crea el objeto y una función de inicialización inicializarlo.  
  
 La construcción de dos pasos siempre es más segura.  En la construcción de la uno\- fase, el constructor podría producir una excepción si proporciona argumentos incorrectos o se produce un error en la asignación de memoria.  Ese problema es evitó la construcción de dos fases, aunque tenga que comprobar error.  En cualquier caso, la destrucción de objetos es el mismo proceso.  
  
> [!NOTE]
>  Estas técnicas se aplican a crear cualquier objeto, no sólo objetos gráficos.  
  
## Ejemplo de las técnicas de Both Construction  
 El ejemplo abreviado siguiente muestra ambos métodos de construir un objeto pen:  
  
 [!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/CPP/one-stage-and-two-stage-construction-of-objects_1.cpp)]  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Objetos gráficos](../mfc/graphic-objects.md)  
  
-   [Seleccionar un objeto gráfico en un contexto de dispositivo](../mfc/selecting-a-graphic-object-into-a-device-context.md)  
  
-   [Contextos de dispositivo](../mfc/device-contexts.md)  
  
-   [Dibujar en una vista](../mfc/drawing-in-a-view.md)  
  
## Vea también  
 [Objetos gráficos](../mfc/graphic-objects.md)