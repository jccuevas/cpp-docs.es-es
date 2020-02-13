---
title: 'Tutorial: Crear una red de procesamiento de imagen'
ms.date: 04/25/2019
helpviewer_keywords:
- image-processing networks, creating [Concurrency Runtime]
- creating image-processing networks [Concurrency Runtime]
ms.assetid: 78ccadc9-5ce2-46cc-bd62-ce0f99d356b8
ms.openlocfilehash: 03d95be8fae3565a51811357ed9553c3a2649674
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140759"
---
# <a name="walkthrough-creating-an-image-processing-network"></a>Tutorial: Crear una red de procesamiento de imagen

En este documento se muestra cómo crear una red de bloques de mensajes asincrónicos que realizan el procesamiento de imágenes.

La red determina qué operaciones se realizan en una imagen en función de sus características. En este ejemplo se usa el modelo de *flujo de entrada* para enrutar imágenes a través de la red. En el modelo de flujo de datos, los componentes independientes de un programa se comunican entre sí mediante mensajes. Cuando un componente recibe un mensaje, puede realizar alguna acción y, a continuación, pasar el resultado de esa acción a otro componente. Compare esto con el modelo de *flujo de control* , en el que una aplicación utiliza estructuras de control, por ejemplo, instrucciones condicionales, bucles, etc., para controlar el orden de las operaciones en un programa.

Una red basada en el flujo de entrada crea una *canalización* de tareas. Cada fase de la canalización realiza de forma simultánea parte de la tarea global. Se podría establecer una analogía de esto con una cadena de montaje en la fabricación de automóviles. A medida que cada vehículo pasa a través de la línea de montaje, una estación ensambla el fotograma, otro instala el motor, etc. Al permitir que varios vehículos se ensamblen simultáneamente, la línea de montaje proporciona un mejor rendimiento que el montaje de vehículos completos de uno en uno.

## <a name="prerequisites"></a>Prerequisites

Lea los documentos siguientes antes de iniciar este tutorial:

- [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)

- [Procedimiento para usar un filtro de bloque de mensaje](../../parallel/concrt/how-to-use-a-message-block-filter.md)

- [Tutorial: Crear un agente de flujo de datos](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)

También se recomienda que comprenda los conceptos básicos de GDI+ antes de comenzar este tutorial.

## <a name="top"></a> Secciones

Este tutorial contiene las siguientes secciones:

- [Definir la funcionalidad de procesamiento de imágenes](#functionality)

- [Creación de la red de procesamiento de imágenes](#network)

- [Ejemplo completo](#complete)

## <a name="functionality"></a>Definir la funcionalidad de procesamiento de imágenes

En esta sección se muestran las funciones de soporte que la red de procesamiento de imágenes utiliza para trabajar con imágenes que se leen desde el disco.

Las siguientes funciones, `GetRGB` y `MakeColor`, extraen y combinan los componentes individuales del color determinado, respectivamente.

[!code-cpp[concrt-image-processing-filter#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_1.cpp)]

La siguiente función, `ProcessImage`, llama al objeto [STD:: function](../../standard-library/function-class.md) determinado para transformar el valor de color de cada píxel de un objeto de [mapa de bits](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap) GDI+. La función `ProcessImage` usa el algoritmo [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) para procesar cada fila del mapa de bits en paralelo.

[!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_2.cpp)]

Las siguientes funciones, `Grayscale`, `Sepiatone`, `ColorMask`y `Darken`, llaman a la función `ProcessImage` para transformar el valor de color de cada píxel de un objeto `Bitmap`. Cada una de estas funciones usa una expresión lambda para definir la transformación de color de un píxel.

[!code-cpp[concrt-image-processing-filter#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_3.cpp)]

La siguiente función, `GetColorDominance`, también llama a la función `ProcessImage`. Sin embargo, en lugar de cambiar el valor de cada color, esta función usa objetos [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) para calcular si el componente de color rojo, verde o azul domina la imagen.

[!code-cpp[concrt-image-processing-filter#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_4.cpp)]

La siguiente función, `GetEncoderClsid`, recupera el identificador de clase para el tipo MIME especificado de un codificador. La aplicación usa esta función para recuperar el codificador para un mapa de bits.

[!code-cpp[concrt-image-processing-filter#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_5.cpp)]

[[Arriba](#top)]

## <a name="network"></a>Creación de la red de procesamiento de imágenes

En esta sección se describe cómo crear una red de bloques de mensajes asincrónicos que realizan el procesamiento de imágenes en cada imagen JPEG (. jpg) en un directorio determinado. La red realiza las siguientes operaciones de procesamiento de imágenes:

1. Para cualquier imagen creada por Tom, convierta a escala de grises.

1. En el caso de las imágenes que tengan rojo como color dominante, quite los componentes verde y azul y, a continuación, oscurecerlos.

1. Para cualquier otra imagen, aplique tonos sepia.

La red solo aplica la primera operación de procesamiento de imágenes que coincida con una de estas condiciones. Por ejemplo, si una imagen es creada por Tom y tiene rojo como color dominante, la imagen solo se convierte en escala de grises.

Una vez que la red realiza cada operación de procesamiento de imágenes, guarda la imagen en el disco como un archivo de mapa de bits (. bmp).

En los pasos siguientes se muestra cómo crear una función que implementa esta red de procesamiento de imágenes y la aplica a cada imagen JPEG en un directorio determinado.

#### <a name="to-create-the-image-processing-network"></a>Para crear la red de procesamiento de imágenes

1. Cree una función, `ProcessImages`, que tome el nombre de un directorio en el disco.

   [!code-cpp[concrt-image-processing-filter#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_6.cpp)]

1. En la función `ProcessImages`, cree una variable de `countdown_event`. La clase `countdown_event` se muestra más adelante en este tutorial.

   [!code-cpp[concrt-image-processing-filter#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_7.cpp)]

1. Cree un objeto [STD:: Map](../../standard-library/map-class.md) que asocie un objeto `Bitmap` con su nombre de archivo original.

   [!code-cpp[concrt-image-processing-filter#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_8.cpp)]

1. Agregue el código siguiente para definir los miembros de la red de procesamiento de imágenes.

   [!code-cpp[concrt-image-processing-filter#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_9.cpp)]

1. Agregue el siguiente código para conectar la red.

   [!code-cpp[concrt-image-processing-filter#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_10.cpp)]

1. Agregue el código siguiente para enviar al encabezado de la red la ruta de acceso completa de cada archivo JPEG en el directorio.

   [!code-cpp[concrt-image-processing-filter#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_11.cpp)]

1. Espere a que la variable `countdown_event` llegue a cero.

   [!code-cpp[concrt-image-processing-filter#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_12.cpp)]

En la tabla siguiente se describen los miembros de la red.

|Member|Descripción|
|------------|-----------------|
|`load_bitmap`|Un objeto [Concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) que carga un objeto de `Bitmap` desde el disco y agrega una entrada al objeto `map` para asociar la imagen con su nombre de archivo original.|
|`loaded_bitmaps`|Un objeto [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) que envía las imágenes cargadas a los filtros de procesamiento de imágenes.|
|`grayscale`|Objeto `transformer` que convierte las imágenes creadas por Tom en una escala de grises. Usa los metadatos de la imagen para determinar su autor.|
|`colormask`|Objeto `transformer` que quita los componentes de color verde y azul de las imágenes que tienen rojo como color dominante.|
|`darken`|Objeto `transformer` que oscurece las imágenes que tienen el rojo como color dominante.|
|`sepiatone`|Objeto `transformer` que aplica tonos sepia a imágenes no creadas por Tom y que no están principalmente en rojo.|
|`save_bitmap`|Objeto `transformer` que guarda la `image` procesada en el disco como un mapa de bits. `save_bitmap` recupera el nombre de archivo original del objeto `map` y cambia su extensión de nombre de archivo a. bmp.|
|`delete_bitmap`|Objeto `transformer` que libera la memoria de las imágenes.|
|`decrement`|Un objeto [Concurrency:: Call](../../parallel/concrt/reference/call-class.md) que actúa como el nodo terminal de la red. Disminuye el objeto de `countdown_event` para indicar a la aplicación principal que se ha procesado una imagen.|

El búfer de mensajes `loaded_bitmaps` es importante porque, como un objeto `unbounded_buffer`, ofrece objetos `Bitmap` a varios receptores. Cuando un bloque de destino acepta un objeto `Bitmap`, el objeto `unbounded_buffer` no ofrece ese objeto `Bitmap` a ningún otro destino. Por lo tanto, es importante el orden en el que se vinculan los objetos a un objeto `unbounded_buffer`. Los bloques de mensajes `grayscale`, `colormask`y `sepiatone` usan un filtro para aceptar solo ciertos objetos `Bitmap`. El búfer de mensajes `decrement` es un objetivo importante del búfer de mensajes de `loaded_bitmaps` porque acepta todos los `Bitmap` objetos que los demás búferes de mensajes rechazan. Un objeto `unbounded_buffer` es necesario para propagar los mensajes en orden. Por lo tanto, un objeto de `unbounded_buffer` se bloquea hasta que se vincula un nuevo bloque de destino y acepta el mensaje si ningún bloque de destino actual acepta ese mensaje.

Si su aplicación requiere que varios bloques de mensajes procesen el mensaje, en lugar de simplemente el bloque de mensajes que primero acepta el mensaje, puede utilizar otro tipo de bloque de mensajes, como `overwrite_buffer`. La clase `overwrite_buffer` contiene un mensaje cada vez, pero propaga ese mensaje a cada uno de sus destinos.

En la ilustración siguiente se muestra la red de procesamiento de imágenes:

![Red de procesamiento de imágenes](../../parallel/concrt/media/concrt_imageproc.png "Red de procesamiento de imágenes")

El objeto `countdown_event` de este ejemplo habilita la red de procesamiento de imágenes para informar a la aplicación principal cuando se han procesado todas las imágenes. La clase `countdown_event` usa un objeto [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) para indicar cuando un valor de contador llega a cero. La aplicación principal incrementa el contador cada vez que envía un nombre de archivo a la red. El nodo terminal de la red disminuye el contador después de procesar cada imagen. Una vez que la aplicación principal atraviesa el directorio especificado, espera a que el objeto `countdown_event` señale que el contador ha alcanzado cero.

En el ejemplo siguiente se muestra la clase `countdown_event`:

[!code-cpp[concrt-image-processing-filter#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_13.cpp)]

[[Arriba](#top)]

## <a name="complete"></a>El ejemplo completo

En el código siguiente se muestra el ejemplo completo. La función `wmain` administra la biblioteca GDI+ y llama a la función `ProcessImages` para procesar los archivos JPEG en el directorio `Sample Pictures`.

[!code-cpp[concrt-image-processing-filter#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_14.cpp)]

En la ilustración siguiente se muestra el resultado del ejemplo. Cada imagen de origen está por encima de su imagen modificada correspondiente.

![Salida de ejemplo para el ejemplo](../../parallel/concrt/media/concrt_imageout.png "Resultado del ejemplo")

`Lighthouse` es creado por Tom ALPHIN y, por tanto, se convierte a escala de grises. `Chrysanthemum`, `Desert`, `Koala`y `Tulips` tienen rojo como color dominante y, por lo tanto, se quitan los componentes de color azul y verde y se oscurecen. `Hydrangeas`, `Jellyfish`y `Penguins` coinciden con los criterios predeterminados y, por tanto, son sepia toned.

[[Arriba](#top)]

### <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `image-processing-network.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl. exe/DUNICODE/EHsc Image-Processing-Network. cpp/Link gdiplus. lib**

## <a name="see-also"></a>Consulte también

[Tutoriales del Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime-walkthroughs.md)
