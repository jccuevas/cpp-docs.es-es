---
title: "Referencia (C++ AMP) | Microsoft Docs"
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
  - "amp/Concurrency::Reference (C++ AMP)"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ Accelerated Massive Parallelism, referencia"
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Referencia (C++ AMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta sección contiene información de referencia para el runtime de C\+\+ Accelerated Massive Parallelism \(AMP de C\+\+\).  
  
> [!NOTE]
>  El estándar del lenguaje C\+\+ reserva el uso de identificadores que comienzan con un carácter de subrayado \(`_`\) para las implementaciones de, por ejemplo, bibliotecas.  No utilice nombres que empiecen con un subrayado en el código.  No se garantiza el comportamiento de los elementos de código cuyos nombres siguen esta convención y está sujeto a cambios en futuras versiones.  Por estas razones, estos elementos de código se omiten en esta documentación.  
  
## En esta sección  
 [Espacio de nombres de simultaneidad \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)  
 Proporciona clases y funciones que permiten la aceleración de código C\+\+ en el hardware en paralelo de datos.  
  
 [Concurrency::direct3d \(Espacio de nombres\)](../../../parallel/amp/reference/concurrency-direct3d-namespace.md)  
 Proporciona funciones que admiten interoperabilidad de D3D.  Habilita el uso sin problemas de los recursos D3D para el cálculo en el código AMP y el uso de los recursos creados con AMP en código D3D, sin crear copias intermedias redundantes.  Puede usar C\+\+ AMP para acelerar incrementalmente las secciones de cálculo intensivo de las aplicaciones DirectX y usar la API D3D en los datos producidos por los cálculos de AMP.  
  
 [Concurrency::fast\_math \(Espacio de nombres\)](../../../parallel/amp/reference/concurrency-fast-math-namespace.md)  
 Las funciones del espacio de nombres `fast_math` no cumplen el estándar C99.  Solo se proporcionan versiones de precisión sencilla de cada función.  Estas funciones usan las funciones intrínsecas de DirectX, que son más rápidas que las funciones correspondientes del espacio de nombres `precise_math` y no requieren la compatibilidad de doble precisión extendida en el acelerador, pero son menos precisas.  Hay dos versiones de cada función para la compatibilidad de nivel de origen con el código C99; ambas toman y devuelven valores de precisión sencilla.  
  
 [Concurrency::graphics \(Espacio de nombres\)](../../../parallel/amp/reference/concurrency-graphics-namespace.md)  
 Proporciona tipos y funciones que están diseñados para la programación de gráficos.  
  
 [Concurrency::precise\_math \(Espacio de nombres\)](../../../parallel/amp/reference/concurrency-precise-math-namespace.md)  
 Las funciones del espacio de nombres `precise_math` cumplen el estándar C99.  Se incluyen las versiones de simple precisión y de doble precisión de cada función.  Estas funciones, incluidas las funciones de precisión simple, requieren la compatibilidad de doble precisión extendida en el acelerador.  
  
## Secciones relacionadas  
 [C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)  
 C\+\+ AMP acelera la ejecución del código de C\+\+ aprovechando el hardware en paralelo de datos que normalmente aparece como una unidad de procesamiento gráfico \(GPU\) en una tarjeta de gráficos discretos.