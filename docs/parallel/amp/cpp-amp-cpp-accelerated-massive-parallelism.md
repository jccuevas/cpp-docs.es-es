---
title: C++ AMP (C++ Accelerated Massive Parallelism) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6bda8be9d3cc939e95ccfe68397eef259dd3a2f4
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)
C++ AMP (C++ Accelerated Massive Parallelism) acelera la ejecución del código C++ aprovechando las ventajas del hardware de datos en paralelo que se encuentra habitualmente como una unidad de procesamiento de gráficos (GPU) en una tarjeta gráfica discreta. El modelo de programación de C++ AMP incluye compatibilidad con matrices multidimensionales, indización, transferencia de memoria y disponer en mosaico. También incluye una biblioteca de funciones matemáticas. Puede usar las extensiones del lenguaje C++ AMP para controlar cómo se mueven los datos de la CPU a la GPU y en espera.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Información general sobre C++ AMP](../../parallel/amp/cpp-amp-overview.md)|Describe las características claves de AMP de C++ y la biblioteca matemática.|  
|[Uso de expresiones lambda, objetos de función y funciones restringidas](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|Describe cómo usar expresiones lambda, objetos de función y funciones restringidas en las llamadas a la [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) método.|  
|[Uso de mosaicos](../../parallel/amp/using-tiles.md)|Describe cómo usar iconos para acelerar el código de C++ AMP.|  
|[Uso de objetos accelerator y accelerator_view](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|Describe cómo usar aceleradores para personalizar la ejecución del código en la GPU.|  
|[Uso de C++ AMP en aplicaciones de la Tienda Windows](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|Describe cómo usar C++ AMP en [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplicaciones que usan los tipos en tiempo de ejecución de Windows.|  
|[Gráficos (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|Describe cómo usar la biblioteca de gráficos de C++ AMP.|  
|[Tutorial: Multiplicación de matrices](../../parallel/amp/walkthrough-matrix-multiplication.md)|Muestra la multiplicación de matrices mediante código de C++ AMP y disponer en mosaico.|  
|[Tutorial: Depurar una aplicación de C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|Explica cómo crear y depurar una aplicación que utiliza reducción paralela para sumar una matriz grande de enteros.|  
  
## <a name="reference"></a>Referencia  
 [Referencia (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)  
  
 [tile_static (Palabra clave)](../../cpp/tile-static-keyword.md)  
  
 [restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)  
  
## <a name="other-resources"></a>Otros recursos  
 [Programación paralela en código nativo](http://go.microsoft.com/fwlink/p/?linkid=238472)  
  
 [Proyectos de ejemplo de C++ AMP para su descarga](http://go.microsoft.com/fwlink/p/?linkid=248508)  
  
 [Análisis de código de AMP de C++ con el visualizador de simultaneidad](http://go.microsoft.com/fwlink/p/?linkid=253987&clcid=0x409)

