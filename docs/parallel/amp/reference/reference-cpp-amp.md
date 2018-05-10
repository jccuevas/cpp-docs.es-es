---
title: Referencia (C++ AMP) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- amp/Concurrency::Reference (C++ AMP)
dev_langs:
- C++
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, reference
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c39528bf3b1e6c9235e4b2daabcd8bbddd0d52f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="reference-c-amp"></a>Referencia (C++ AMP)
Esta sección contiene información de referencia para el tiempo de ejecución de C++ Accelerated Massive Parallelism (C++ AMP).  
  
> [!NOTE]
>  El estándar del lenguaje C++ reserva el uso de los identificadores que comienzan con un carácter de subrayado (`_`) para implementaciones como bibliotecas. No utilice nombres que comiencen por un carácter de subrayado en el código. El comportamiento de los elementos de código cuyos nombres siguen esta convención no está garantizado y está sujeto a cambios en el futuro. Por estos motivos, dichos elementos de código se omiten de esta documentación.  
  
## <a name="in-this-section"></a>En esta sección  
 [Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)  
 Proporciona clases y funciones que permiten la aceleración de código de C++ en hardware paralelo de datos.  
  
 [Concurrency::direct3d (espacio de nombres)](concurrency-direct3d-namespace.md)  
 Proporciona funciones que admiten interoperabilidad de D3D. Habilita el uso sin problemas de los recursos D3D para el cálculo en el código AMP y el uso de los recursos creados con AMP en código D3D, sin crear copias intermedias redundantes. Puede usar C++ AMP para acelerar incrementalmente las secciones de cálculo intensivo de las aplicaciones DirectX y usar la API D3D en los datos producidos por los cálculos de AMP.  
  
 [Concurrency::fast_math (espacio de nombres)](concurrency-fast-math-namespace.md)  
 Las funciones del espacio de nombres `fast_math` no cumplen el estándar C99. Solo se proporcionan versiones de precisión sencilla de cada función. Estas funciones usan las funciones intrínsecas de DirectX, que son más rápidas que las funciones correspondientes del espacio de nombres `precise_math` y no requieren la compatibilidad de doble precisión extendida en el acelerador, pero son menos precisas. Hay dos versiones de cada función para la compatibilidad de nivel de origen con el código C99; ambas toman y devuelven valores de precisión sencilla.  
  
 [Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)  
 Proporciona tipos y funciones que están diseñados para la programación de gráficos.  
  
 [Concurrency::precise_math (espacio de nombres)](concurrency-precise-math-namespace.md)  
 Las funciones del espacio de nombres `precise_math` cumplen el estándar C99. Se incluyen las versiones de simple precisión y de doble precisión de cada función. Estas funciones, incluidas las funciones de precisión simple, requieren la compatibilidad de doble precisión extendida en el acelerador.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)  
 C++ AMP acelera la ejecución del código C++ aprovechando las ventajas del hardware de datos en paralelo que se encuentra habitualmente como una unidad de procesamiento de gráficos (GPU) en una tarjeta gráfica discreta.





