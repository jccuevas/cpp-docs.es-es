---
title: 'Tutorial: Crear una red de procesamiento de imagen'
ms.date: 11/04/2016
helpviewer_keywords:
- image-processing networks, creating [Concurrency Runtime]
- creating image-processing networks [Concurrency Runtime]
ms.assetid: 78ccadc9-5ce2-46cc-bd62-ce0f99d356b8
ms.openlocfilehash: 4eb1d6f9e5bc0055a1a4b4be5e18497b20c3a73a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643643"
---
# <a name="walkthrough-creating-an-image-processing-network"></a>Tutorial: Crear una red de procesamiento de imagen

Este documento muestra cómo crear una red de bloques de mensajes asincrónicos que realizan procesamiento de imágenes.

La red determina qué operaciones se realizan en una imagen basándose en sus características. Este ejemplo se usa el *dataflow* modelos para distribuir las imágenes a través de la red. En el modelo de flujo de datos, los componentes independientes de un programa se comunican entre sí mediante mensajes. Cuando un componente recibe un mensaje, puede realizar alguna acción y, a continuación, pase el resultado de esa acción a otro componente. Compare esto con el *flujo de control* modelo, en el que una aplicación utiliza estructuras de control, por ejemplo, instrucciones condicionales, bucles etc., para controlar el orden de las operaciones en un programa.

Crea una red que se basa en el flujo de datos un *canalización* de tareas. Cada fase de la canalización lleva a cabo al mismo tiempo parte de la tarea global. Se podría establecer una analogía de esto con una cadena de montaje en la fabricación de automóviles. Mientras cada vehículo pasa a través de la línea de ensamblado, una estación monta el bastidor, otro instala el motor y así sucesivamente. Al habilitar varios vehículos que se montarán simultáneamente, la línea de ensamblado proporciona mejor rendimiento que montar uno los vehículos completos a la vez.

## <a name="prerequisites"></a>Requisitos previos

Lea los documentos siguientes antes de iniciar este tutorial:

- [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)

- [Procedimiento para usar un filtro de bloque de mensaje](../../parallel/concrt/how-to-use-a-message-block-filter.md)

- [Tutorial: Crear un agente de flujo de datos](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)

También se recomienda comprender los conceptos básicos de GDI + antes de empezar este tutorial.

##  <a name="top"></a> Secciones

Este tutorial contiene las siguientes secciones:

- [Definir la funcionalidad de procesamiento de imágenes](#functionality)

- [Creación de la red de procesamiento de imágenes](#network)

- [Ejemplo completo](#complete)

##  <a name="functionality"></a> Definir la funcionalidad de procesamiento de imágenes

Esta sección muestra las funciones de soporte técnico que utiliza la red de procesamiento de imágenes para trabajar con imágenes que se leen del disco.

Las siguientes funciones, `GetRGB` y `MakeColor`, extraiga y combine los componentes individuales del color determinado, respectivamente.

[!code-cpp[concrt-image-processing-filter#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_1.cpp)]

La siguiente función, `ProcessImage`, llama a la determinada [std:: Function](../../standard-library/function-class.md) objeto para transformar el valor de color de cada píxel de GDI + [mapa de bits](/windows/desktop/api/gdiplusheaders/nl-gdiplusheaders-bitmap) objeto. El `ProcessImage` función usa el [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmo para procesar cada fila del mapa de bits en paralelo.

[!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_2.cpp)]

Las siguientes funciones, `Grayscale`, `Sepiatone`, `ColorMask`, y `Darken`, llame a la `ProcessImage` función para transformar el valor de color de cada píxel de un `Bitmap` objeto. Cada una de estas funciones utiliza una expresión lambda para definir la transformación de color de un píxel.

[!code-cpp[concrt-image-processing-filter#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_3.cpp)]

La siguiente función, `GetColorDominance`, también se llama a la `ProcessImage` función. Sin embargo, en lugar de cambiar el valor de cada color, esta función usa [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) objetos para calcular si el componente de color rojo, verde o azul domina la imagen.

[!code-cpp[concrt-image-processing-filter#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_4.cpp)]

La siguiente función, `GetEncoderClsid`, recupera el identificador de clase para el tipo MIME especificado de un codificador. La aplicación usa esta función para recuperar el codificador para un mapa de bits.

[!code-cpp[concrt-image-processing-filter#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_5.cpp)]

[[Arriba](#top)]

##  <a name="network"></a> Creación de la red de procesamiento de imágenes

En esta sección se describe cómo crear una red de bloques de mensajes asincrónicos que realizan procesamiento de imágenes en cada imagen JPEG (.jpg) en un directorio determinado. La red realiza las siguientes operaciones de procesamiento de imágenes:

1. Para cualquier imagen que fue creado por Tom, convertir a escala de grises.

1. Para cualquier imagen que tiene rojo como color dominante, quite los componentes verdes y azules y, a continuación, oscurecerlo.

1. Para cualquier otra imagen, se aplica un tono sepia.

La red aplica sólo la operación de procesamiento de imágenes primera que coincide con una de estas condiciones. Por ejemplo, si una imagen es creada por Tom y tiene rojo como el color predominante, la imagen sólo se convierte a escala de grises.

Después de la red realiza cada operación de procesamiento de imágenes, guarda la imagen en el disco como un archivo de mapa de bits (.bmp).

Los pasos siguientes muestran cómo crear una función que implementa esta red de procesamiento de imágenes y se aplica a esa red para cada imagen JPEG en un directorio determinado.

#### <a name="to-create-the-image-processing-network"></a>Para crear la red de procesamiento de imágenes

1. Creación de una función, `ProcessImages`, que toma el nombre de un directorio en el disco.

   [!code-cpp[concrt-image-processing-filter#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_6.cpp)]

1. En el `ProcessImages` función, cree un `countdown_event` variable. La `countdown_event` clase se muestra más adelante en este tutorial.

   [!code-cpp[concrt-image-processing-filter#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_7.cpp)]

1. Crear un [std:: Map](../../standard-library/map-class.md) objeto que se asocia un `Bitmap` objeto con el nombre de archivo original.

   [!code-cpp[concrt-image-processing-filter#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_8.cpp)]

1. Agregue el código siguiente para definir a los miembros de la red de procesamiento de imágenes.

   [!code-cpp[concrt-image-processing-filter#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_9.cpp)]

1. Agregue el código siguiente para conectarse a la red.

   [!code-cpp[concrt-image-processing-filter#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_10.cpp)]

1. Agregue el código siguiente para enviar la ruta de acceso completa de cada archivo JPEG en el encabezado de la red en el directorio.

   [!code-cpp[concrt-image-processing-filter#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_11.cpp)]

1. Espere a que el `countdown_event` variable para llegar a cero.

   [!code-cpp[concrt-image-processing-filter#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_12.cpp)]

En la tabla siguiente se describen los miembros de la red.

|Miembro|Descripción|
|------------|-----------------|
|`load_bitmap`|Un [Concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) objeto que carga un `Bitmap` objeto desde el disco y agrega una entrada para el `map` objeto para asociar la imagen con el nombre de archivo original.|
|`loaded_bitmaps`|Un [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) objeto que envía las imágenes de cargadas a los filtros de procesamiento de imágenes.|
|`grayscale`|Un `transformer` objeto que convierte las imágenes que se crean por Tom a escala de grises. Los metadatos de la imagen usa para determinar a su autor.|
|`colormask`|Un `transformer` objeto que quita los componentes de color verde y azul de las imágenes que tienen rojo como color dominante.|
|`darken`|Un `transformer` objeto que se oscurece imágenes con rojo como color dominante.|
|`sepiatone`|Un `transformer` objeto que se aplica un tono sepia a las imágenes que no se crean por Tom y no son fundamentalmente rojo.|
|`save_bitmap`|Un `transformer` objeto que guarda el procesado `image` en el disco como un mapa de bits. `save_bitmap` Recupera el nombre de archivo original desde el `map` de objetos y cambia su extensión de nombre de archivo a. bmp.|
|`delete_bitmap`|Un `transformer` objeto que libera la memoria para las imágenes.|
|`decrement`|Un [Concurrency:: call](../../parallel/concrt/reference/call-class.md) objeto que actúa como nodo terminal de la red. Se reduce la `countdown_event` objeto para señalar a la aplicación principal que se ha procesado una imagen.|

El `loaded_bitmaps` búfer de mensajes es importante porque, como un `unbounded_buffer` objeto, ofrece `Bitmap` objetos a varios receptores. Cuando un bloque de destino acepta un `Bitmap` objeto, el `unbounded_buffer` objeto no ofrece `Bitmap` objeto a cualquier otro destino. Por consiguiente, el orden en que se vinculan los objetos a un `unbounded_buffer` objeto es importante. El `grayscale`, `colormask`, y `sepiatone` bloques cada usan un filtro para aceptar el mensaje solo ciertos `Bitmap` objetos. El `decrement` búfer de mensajes es un objetivo importante de la `loaded_bitmaps` búfer de mensajes porque aceptan todos `Bitmap` objetos que son rechazados por los otros búferes de mensajes. Un `unbounded_buffer` objeto se requiere para propagar los mensajes en orden. Por lo tanto, un `unbounded_buffer` objeto bloquea hasta que un nuevo bloque de destino está vinculado a él y acepta el mensaje si ningún bloque de destino actual acepta ese mensaje.

Si la aplicación requiere que varios de mensaje bloquea procesar el mensaje, en lugar de simplemente el bloque de un mensaje que primero se acepta el mensaje, puede usar otro tipo de bloque de mensaje, como `overwrite_buffer`. La `overwrite_buffer` clase contiene un mensaje a la vez, pero propaga ese mensaje a cada uno de sus destinos.

La siguiente ilustración muestra la red de procesamiento de imágenes:

![Red de procesamiento de imágenes](../../parallel/concrt/media/concrt_imageproc.png "concrt_imageproc")

La `countdown_event` objeto en este ejemplo habilita la red de procesamiento de imágenes informar a la aplicación principal cuando se han procesado todas las imágenes. El `countdown_event` clase utiliza un [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) objeto que se va a señalar cuando un valor de contador llega a cero. La aplicación principal incrementa el contador cada vez que TI envía un nombre de archivo a la red. El nodo terminal de la red disminuye el contador después de procesar cada imagen. Una vez que la aplicación principal atraviesa el directorio especificado, espera el `countdown_event` objeto para indicar que el contador llegue a cero.

El ejemplo siguiente se muestra la `countdown_event` clase:

[!code-cpp[concrt-image-processing-filter#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_13.cpp)]

[[Arriba](#top)]

##  <a name="complete"></a> El ejemplo completo

En el código siguiente se muestra el ejemplo completo. El `wmain` función administra la biblioteca de GDI + y llama a la `ProcessImages` archivos de la función para procesar la imagen JPEG en la `Sample Pictures` directory.

[!code-cpp[concrt-image-processing-filter#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_14.cpp)]

La siguiente ilustración muestra la salida de ejemplo. Cada imagen de origen está por encima de su correspondiente imagen modificada.

![Ejemplo de salida para el ejemplo](../../parallel/concrt/media/concrt_imageout.png "concrt_imageout")

`Lighthouse` creado por Tom Alphin y, por tanto, se convierte a escala de grises. `Chrysanthemum`, `Desert`, `Koala`, y `Tulips` tiene rojo como color dominante y, por tanto, tienen los componentes de color azul y verde que se quita y se oscurecerá. `Hydrangeas`, `Jellyfish`, y `Penguins` coinciden con los criterios predeterminados y, por tanto, son sepia tonos.

[[Arriba](#top)]

### <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `image-processing-network.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl.exe /DUNICODE/EHsc /link procesamiento-image-network.cpp gdiplus.lib**

## <a name="see-also"></a>Vea también

[Tutoriales del Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime-walkthroughs.md)
