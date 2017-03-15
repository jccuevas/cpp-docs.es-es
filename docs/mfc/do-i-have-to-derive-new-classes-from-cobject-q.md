---
title: "&#191;Tengo que derivar las clases nuevas de CObject? | Microsoft Docs"
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
  - "CObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CObject (clase), cuándo se deben utilizar"
  - "clases derivadas, desde CObject"
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &#191;Tengo que derivar las clases nuevas de CObject?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

No, no lo hace.  
  
 Derive una clase de [CObject](../mfc/reference/cobject-class.md) cuando necesita las funciones que proporciona, por ejemplo la serialización o el creatability dinámico.  Muchas clases de datos necesitan serializar los archivos, por lo que a menudo conveniente derivar de `CObject`.  Para obtener un ejemplo de una clase derivada de `CObject`, vea [Ejemplo scribble](../top/visual-cpp-samples.md).  
  
## Vea también  
 [CObject \(Clase\): Preguntas más frecuentes](../mfc/cobject-class-frequently-asked-questions.md)