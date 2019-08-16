---
title: C++ AMP (C++ Accelerated Massive Parallelism)
ms.date: 11/04/2016
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
ms.openlocfilehash: 3dbd7d646b455ac57833d28b18602b533c8388e6
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450351"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)

C++ AMP (C++ Accelerated Massive Parallelism) acelera la ejecución del código de C++ al aprovechar el hardware paralelo de datos que normalmente aparece como una unidad de procesamiento de gráficos (GPU) en una tarjeta gráfica discreta. El modelo de programación de C++ AMP incluye compatibilidad con las matrices multidimensionales, indexación, transferencia de memoria y disposición en mosaico. También incluye una biblioteca de funciones matemáticas. Puede usar las extensiones del lenguaje C++ AMP para controlar cómo se mueven los datos de la CPU a la GPU y en espera.

## <a name="related-topics"></a>Temas relacionados

|Título|Descripción|
|-----------|-----------------|
|[Información general sobre C++ AMP](../../parallel/amp/cpp-amp-overview.md)|Describe las características clave de C++ AMP y la biblioteca matemática.|
|[Uso de expresiones lambda, objetos de función y funciones restringidas](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|Describe cómo usar expresiones lambda, objetos de función y funciones restringidas en llamadas a la [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) método.|
|[Uso de mosaicos](../../parallel/amp/using-tiles.md)|Describe cómo utilizar los mosaicos y para acelerar su código C++ AMP.|
|[Uso de objetos accelerator y accelerator_view](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|Describe cómo utilizar los aceleradores para personalizar la ejecución del código en la GPU.|
|[Uso de C++ AMP en aplicaciones de UWP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|Describe cómo utilizar C++ AMP en aplicaciones de plataforma Universal de Windows (UWP) que usan tipos en tiempo de ejecución de Windows.|
|[Gráficos (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|Describe cómo usar la biblioteca de gráficos del AMP de C++.|
|[Tutorial: Multiplicación de matrices](../../parallel/amp/walkthrough-matrix-multiplication.md)|Muestra la multiplicación de matrices mediante código C++ AMP y disposición en mosaico.|
|[Tutorial: Depurar una aplicación de C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|Explica cómo crear y depurar una aplicación que utilice la reducción paralela para resumir una matriz grande de enteros.|

## <a name="reference"></a>Referencia

[Referencia (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[tile_static (Palabra clave)](../../cpp/tile-static-keyword.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)

## <a name="other-resources"></a>Otros recursos

[Programación en paralelo en código nativo](https://go.microsoft.com/fwlink/p/?linkid=238472)<br/>
[Proyectos de ejemplo de C++ AMP para su descarga](https://go.microsoft.com/fwlink/p/?linkid=248508)<br/>
[Análisis de código de AMP de C++ con el visualizador de simultaneidad](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)