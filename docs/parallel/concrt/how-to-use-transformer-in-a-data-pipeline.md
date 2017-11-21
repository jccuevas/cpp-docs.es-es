---
title: "Cómo: usar la clase transformer en una canalización de datos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- transformer class, example
- data pipelines, using transformer [Concurrency Runtime]
- using transformer in data pipelines [Concurrency Runtime]
ms.assetid: ca49cb3f-4dab-4b09-a9c9-d3a109ae4c29
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 97591a66f7499e136072d47e2a7c5b87870a4702
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-use-transformer-in-a-data-pipeline"></a>Cómo: Usar la clase transformer en una canalización de datos
Este tema contiene un ejemplo básico que muestra cómo utilizar el [Concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) clase en una canalización de datos. Para obtener un ejemplo más completo que usa una canalización de datos para realizar el procesamiento de imágenes, vea [Tutorial: crear una red de procesamiento de imágenes](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).  
  
 *Canalización de datos* es un patrón común en la programación simultánea. Una canalización de datos se compone de una serie de fases donde en cada fase se realiza un trabajo y, a continuación, se pasa el resultado de ese trabajo a la siguiente fase. La clase `transformer` es un componente clave de la canalización de datos porque recibe un valor de entrada, realiza un trabajo en dicho valor y, a continuación, genera un resultado que otro componente va a usar.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se usa la canalización de datos siguiente para realizar una serie de transformaciones a partir de un valor de entrada inicial especificado:  
  
1.  En la primera fase se calcula el valor absoluto de la entrada.  
  
2.  En la segunda fase se calcula la raíz cuadrada de la entrada.  
  
3.  En la tercera fase se calcula el cuadrado de la entrada.  
  
4.  En la cuarta fase se calcula el valor negativo de la entrada.  
  
5.  En la quinta fase se escribe el resultado final en un búfer de mensajes.  
  
 Finalmente, el ejemplo imprime el resultado de la canalización en la consola.  
  
 [!code-cpp[concrt-data-pipeline#1](../../parallel/concrt/codesnippet/cpp/how-to-use-transformer-in-a-data-pipeline_1.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
```Output  
The result is -42.  
```  
  
 Es frecuente que una fase de una canalización de datos dé como resultado un valor cuyo tipo difiere del valor de entrada. En este ejemplo, en la segunda fase se toma un valor de tipo `int` como entrada y se genera la raíz cuadrada de ese valor (un valor de tipo `double`) como resultado.  
  
> [!NOTE]
>  La canalización de datos de este ejemplo corresponde a la ilustración. Dado que cada operación de transformación realiza poco trabajo, la sobrecarga necesaria para realizar el paso de mensajes puede sobrepasar las ventajas de usar una canalización de datos.  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `data-pipeline.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe/EHsc data-pipeline.cpp**  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)   
 [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Tutorial: Crear una red de procesamiento de imagen](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)

