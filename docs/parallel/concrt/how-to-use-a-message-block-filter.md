---
title: 'Cómo: Utilizar un filtro de bloque de mensaje'
ms.date: 11/04/2016
helpviewer_keywords:
- message-block filters, using [Concurrency Runtime]
- using message-block filters [Concurrency Runtime]
ms.assetid: db6b99fb-288d-4477-96dc-b9751772ebb2
ms.openlocfilehash: 074d3989ce48b0b6d69206e3f83c374a2ec65c93
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142817"
---
# <a name="how-to-use-a-message-block-filter"></a>Cómo: Utilizar un filtro de bloque de mensaje

En este documento se muestra cómo usar una función de filtro para permitir que un bloque de mensajes asincrónicos acepte o rechace un mensaje basándose en la carga de ese mensaje.

Cuando se crea un objeto de bloque de mensajes, como [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md), [Concurrency:: Call](../../parallel/concrt/reference/call-class.md)o [Concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md), se puede proporcionar una *función de filtro* que determina si el bloque de mensajes acepta o rechaza un mensaje. Una función de filtro resulta útil para garantizar que un bloque de mensajes recibe solo ciertos valores.

Las funciones de filtro son importantes porque permiten conectar bloques de mensajes para formar *redes de flujo de entrada*. En una red de flujo de datos, los bloques de mensajes controlan el flujo de datos y procesan solo los mensajes que cumplen determinados criterios. Compare esto con el modelo de flujo de control, donde el flujo de datos se regula con las estructuras de control, como instrucciones condicionales, bucles, etc.

En este documento se proporciona un ejemplo básico de cómo usar un filtro de mensajes. Para obtener ejemplos adicionales que usan filtros de mensajes y el modelo de flujo de entrada para conectar bloques de mensajes, vea [Tutorial: crear un agente de flujo de entrada](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md) y [Tutorial: crear una red de procesamiento de imágenes](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

## <a name="example"></a>Ejemplo

Considere la siguiente función, `count_primes`, que muestra el uso básico de un bloque de mensajes que no filtra los mensajes entrantes. El bloque de mensajes anexa los números primos a un objeto [STD:: Vector](../../standard-library/vector-class.md) . La función `count_primes` envía varios números al bloque de mensajes, recibe los valores de salida del bloque de mensajes e imprime aquellos números que son primos en la consola.

[!code-cpp[concrt-primes-filter#1](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_1.cpp)]

El objeto `transformer` procesa todos los valores de entrada; sin embargo, solo requiere los valores que son primos. Aunque la aplicación podría escribirse de forma que el remitente del mensaje envíe solo números primos, los requisitos del receptor del mensaje no se pueden conocer siempre.

## <a name="example"></a>Ejemplo

La siguiente función, `count_primes_filter`, realiza la misma tarea que la función `count_primes`. Sin embargo, el objeto `transformer` de esta versión usa una función de filtro para aceptar únicamente los valores que son primos. La función que realiza la acción recibe solo números primos; por consiguiente, no tiene que llamar a la función `is_prime`.

Dado que el objeto `transformer` recibe solo números primos, el propio objeto `transformer` puede contener números primos. Es decir, el objeto `transformer` de este ejemplo no es necesario para agregar los números primos al objeto `vector`.

[!code-cpp[concrt-primes-filter#2](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_2.cpp)]

El objeto `transformer` procesa ahora solo los valores que son primos. En el ejemplo anterior, el objeto `transformer` procesa todos los mensajes. Por consiguiente, en el ejemplo anterior debe recibir el mismo número de mensajes que envía. En este ejemplo se usa el resultado de la función [Concurrency:: Send](reference/concurrency-namespace-functions.md#send) para determinar el número de mensajes que se van a recibir del objeto `transformer`. La función `send` devuelve **true** cuando el búfer de mensajes acepta el mensaje y **false** cuando el búfer de mensajes rechaza el mensaje. Por tanto, el número de veces que el búfer de mensajes acepta el mensaje coincide con el contador de números primos.

## <a name="example"></a>Ejemplo

En el código siguiente se muestra el ejemplo completo. En el ejemplo se llama a las funciones `count_primes` y `count_primes_filter`.

[!code-cpp[concrt-primes-filter#3](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_3.cpp)]

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `primes-filter.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

> **cl. exe/EHsc primes-Filter. cpp**

## <a name="robust-programming"></a>Programación sólida

Una función de filtro puede ser una función lambda, un puntero a función o un objeto de función. Cada función de filtro toma una de las siguientes formas:

```Output
bool (T)
bool (T const &)
```

Para eliminar la copia innecesaria de datos, use el segundo formulario cuando tenga un tipo agregado que se transmite por valor.

## <a name="see-also"></a>Consulte también

[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Tutorial: Crear un agente de flujo de datos](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[Tutorial: Crear una red de procesamiento de imagen](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[transformer (clase)](../../parallel/concrt/reference/transformer-class.md)
