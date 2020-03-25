---
title: C++ AMP (C++ Accelerated Massive Parallelism)
ms.date: 11/04/2016
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
ms.openlocfilehash: c9ef7ab816ec0d17b9dc0b569a6f3a43af83cc68
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167698"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)

C++AMP (C++ paralelismo masivo acelerado) acelera la ejecución del C++ código aprovechando el hardware en paralelo de datos que normalmente está presente como una unidad de procesamiento de gráficos (GPU) en una tarjeta gráfica discreta. El C++ modelo de programación de amp incluye compatibilidad con matrices multidimensionales, indexación, transferencia de memoria y mosaico. También incluye una biblioteca de funciones matemáticas. Puede usar C++ las extensiones de lenguaje amp para controlar cómo se mueven los datos de la CPU a la GPU y viceversa.

## <a name="related-topics"></a>Temas relacionados

|Título|Descripción|
|-----------|-----------------|
|[Información general sobre C++ AMP](../../parallel/amp/cpp-amp-overview.md)|Describe las características clave de C++ amp y la biblioteca matemática.|
|[Uso de expresiones lambda, objetos de función y funciones restringidas](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|Describe cómo usar expresiones lambda, objetos de función y funciones restringidas en llamadas al método [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) .|
|[Uso de mosaicos](../../parallel/amp/using-tiles.md)|Describe cómo usar los mosaicos para acelerar el C++ código del amp.|
|[Uso de objetos accelerator y accelerator_view](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|Describe cómo usar aceleradores para personalizar la ejecución del código en la GPU.|
|[Uso de C++ AMP en aplicaciones de UWP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|Describe cómo usar C++ las aplicaciones de AMP en plataforma universal de Windows (UWP) que usan tipos de Windows Runtime.|
|[Gráficos (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|Describe cómo usar la biblioteca C++ de gráficos del amp.|
|[Tutorial: Multiplicación de matrices](../../parallel/amp/walkthrough-matrix-multiplication.md)|Muestra la multiplicación de C++ matrices mediante el código y el mosaico de amp.|
|[Tutorial: Depurar una aplicación de C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|Explica cómo crear y depurar una aplicación que utiliza la reducción paralela para sumar una matriz grande de enteros.|

## <a name="reference"></a>Referencia

[Referencia (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[tile_static (Palabra clave)](../../cpp/tile-static-keyword.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)

## <a name="other-resources"></a>Otros recursos

[Blog de programación en paralelo en código nativo](https://go.microsoft.com/fwlink/p/?linkid=238472)<br/>
[C++Proyectos de ejemplo de AMP para descargar](https://go.microsoft.com/fwlink/p/?linkid=248508)<br/>
[Analizar C++ código de amp con el visualizador de simultaneidad](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)
