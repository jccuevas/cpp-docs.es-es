---
title: Procedimiento Utilice un filtro de bloque de mensajes
ms.date: 11/04/2016
helpviewer_keywords:
- message-block filters, using [Concurrency Runtime]
- using message-block filters [Concurrency Runtime]
ms.assetid: db6b99fb-288d-4477-96dc-b9751772ebb2
ms.openlocfilehash: 1bfa11953d27dc7e013e715b3f58111f124caeaf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321947"
---
# <a name="how-to-use-a-message-block-filter"></a>Procedimiento Utilice un filtro de bloque de mensajes

En este documento se muestra cómo usar una función de filtro para permitir que un bloque de mensajes asincrónicos acepte o rechace un mensaje basándose en la carga de ese mensaje.

Cuando crea un objeto de bloque de mensaje como un [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md), un [Concurrency:: call](../../parallel/concrt/reference/call-class.md), o un [Concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md), puede proporcionar un *filter, función* que determina si el bloque de mensajes acepta o rechaza un mensaje. Una función de filtro resulta útil para garantizar que un bloque de mensajes recibe solo ciertos valores.

Las funciones de filtro son importantes porque permiten conectar los bloques de mensajes para formar *redes de flujo de datos*. En una red de flujo de datos, los bloques de mensajes controlan el flujo de datos y procesan solo los mensajes que cumplen determinados criterios. Compare esto con el modelo de flujo de control, donde el flujo de datos se regula con las estructuras de control, como instrucciones condicionales, bucles, etc.

En este documento se proporciona un ejemplo básico de cómo usar un filtro de mensajes. Para obtener ejemplos adicionales que usan filtros de mensajes y el modelo de flujo de datos para conectar los bloques de mensaje, consulte [Tutorial: Creación de un agente de flujo de datos](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md) y [Tutorial: Creación de una red de procesamiento de imágenes](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

## <a name="example"></a>Ejemplo

Considere la siguiente función, `count_primes`, que muestra el uso básico de un bloque de mensajes que no filtra los mensajes entrantes. El bloque de mensajes anexa los números primos en un [std:: vector](../../standard-library/vector-class.md) objeto. La función `count_primes` envía varios números al bloque de mensajes, recibe los valores de salida del bloque de mensajes e imprime aquellos números que son primos en la consola.

[!code-cpp[concrt-primes-filter#1](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_1.cpp)]

El objeto `transformer` procesa todos los valores de entrada; sin embargo, solo requiere los valores que son primos. Aunque la aplicación podría escribirse de forma que el remitente del mensaje envíe solo números primos, los requisitos del receptor del mensaje no se pueden conocer siempre.

## <a name="example"></a>Ejemplo

La siguiente función, `count_primes_filter`, realiza la misma tarea que la función `count_primes`. Sin embargo, el objeto `transformer` de esta versión usa una función de filtro para aceptar únicamente los valores que son primos. La función que realiza la acción recibe solo números primos; por consiguiente, no tiene que llamar a la función `is_prime`.

Dado que el objeto `transformer` recibe solo números primos, el propio objeto `transformer` puede contener números primos. Es decir, el objeto `transformer` de este ejemplo no es necesario para agregar los números primos al objeto `vector`.

[!code-cpp[concrt-primes-filter#2](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_2.cpp)]

El objeto `transformer` procesa ahora solo los valores que son primos. En el ejemplo anterior, el objeto `transformer` procesa todos los mensajes. Por consiguiente, en el ejemplo anterior debe recibir el mismo número de mensajes que envía. En este ejemplo usa el resultado de la [Concurrency:: Send](reference/concurrency-namespace-functions.md#send) función para determinar cuántos mensajes se reciben los `transformer` objeto. El `send` función devuelve **true** cuando el búfer de mensajes acepta el mensaje y **false** cuando el búfer de mensajes rechaza el mensaje. Por tanto, el número de veces que el búfer de mensajes acepta el mensaje coincide con el contador de números primos.

## <a name="example"></a>Ejemplo

En el código siguiente se muestra el ejemplo completo. En el ejemplo se llama a las funciones `count_primes` y `count_primes_filter`.

[!code-cpp[concrt-primes-filter#3](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_3.cpp)]

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `primes-filter.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl.exe/EHsc primes-filter.cpp**

## <a name="robust-programming"></a>Programación sólida

Una función de filtro puede ser una función lambda, un puntero a función o un objeto de función. Cada función de filtro toma una de las siguientes formas:

```Output
bool (T)
bool (T const &)
```

Para eliminar la copia innecesaria de datos, use el segundo formulario cuando tenga un tipo agregado que se transmite por valor.

## <a name="see-also"></a>Vea también

[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Tutorial: Creación de un agente de flujo de datos](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[Tutorial: Creación de una red de procesamiento de imagen](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[transformer (clase)](../../parallel/concrt/reference/transformer-class.md)
