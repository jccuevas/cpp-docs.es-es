---
title: Referencia (C++ AMP) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::Reference (C++ AMP)
dev_langs:
- C++
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, reference
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 22ba62ab8b3b4f9d14953dbab3edd8228ea85193
ms.openlocfilehash: cc654cedd8639377ab7011c91454f1508c730247
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="reference-c-amp"></a>Referencia (C++ AMP)
Esta sección contiene información de referencia para el runtime C++ Accelerated Massive Parallelism (C++ AMP).  
  
> [!NOTE]
>  El estándar del lenguaje C++ reserva el uso de los identificadores que comienzan con un carácter de subrayado (`_`) para implementaciones como bibliotecas. No utilice nombres que comiencen por un carácter de subrayado en el código. El comportamiento de los elementos de código cuyos nombres siguen esta convención no está garantizado y está sujeto a cambios en el futuro. Por estos motivos, dichos elementos de código se omiten de esta documentación.  
  
## <a name="in-this-section"></a>En esta sección  
 [Namespace de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)  
 Proporciona clases y funciones que permiten la aceleración de código de C++ en hardware paralelo de datos.  
  
 [Namespace Concurrency::Direct3D](concurrency-direct3d-namespace.md)  
 Proporciona funciones que admiten interoperabilidad de D3D. Habilita el uso sin problemas de los recursos D3D para el cálculo en el código AMP y el uso de los recursos creados con AMP en código D3D, sin crear copias intermedias redundantes. Puede usar C++ AMP para acelerar incrementalmente las secciones de cálculo intensivo de las aplicaciones DirectX y usar la API D3D en los datos producidos por los cálculos de AMP.  
  
 [Namespace fast_math](concurrency-fast-math-namespace.md)  
 Las funciones del espacio de nombres `fast_math` no cumplen el estándar C99. Solo se proporcionan versiones de precisión sencilla de cada función. Estas funciones usan las funciones intrínsecas de DirectX, que son más rápidas que las funciones correspondientes del espacio de nombres `precise_math` y no requieren la compatibilidad de doble precisión extendida en el acelerador, pero son menos precisas. Hay dos versiones de cada función para la compatibilidad de nivel de origen con el código C99; ambas toman y devuelven valores de precisión sencilla.  
  
 [Graphics Namespace](concurrency-graphics-namespace.md)  
 Proporciona tipos y funciones que están diseñados para la programación de gráficos.  
  
 [Namespace precise_math](concurrency-precise-math-namespace.md)  
 Las funciones del espacio de nombres `precise_math` cumplen el estándar C99. Se incluyen las versiones de simple precisión y de doble precisión de cada función. Estas funciones, incluidas las funciones de precisión simple, requieren la compatibilidad de doble precisión extendida en el acelerador.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)  
 C++ AMP acelera la ejecución del código C++, al aprovechar el hardware paralelo de datos que se encuentra comúnmente como una unidad de procesamiento de gráficos (GPU) en una tarjeta gráfica independiente.






