---
title: "C&#243;mo: Usar la clase transformer en una canalizaci&#243;n de datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "transformer (clase), ejemplo"
  - "canalizaciones de datos, usar la clase transformer [Runtime de simultaneidad]"
  - "usar la clase transformer en las canalizaciones de datos [Runtime de simultaneidad]"
ms.assetid: ca49cb3f-4dab-4b09-a9c9-d3a109ae4c29
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Usar la clase transformer en una canalizaci&#243;n de datos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema contiene un ejemplo básico que muestra cómo usar la clase [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) en una canalización de datos.  Para obtener un ejemplo más completo en el que usa una canalización de datos para realizar el procesamiento de imágenes, vea [Tutorial: Crear una red de procesamiento de imagen](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).  
  
 La *canalización de datos* es un modelo frecuente en la programación simultánea.  Una canalización de datos se compone de una serie de fases donde en cada fase se realiza un trabajo y, a continuación, se pasa el resultado de ese trabajo a la siguiente fase.  La clase `transformer` es un componente clave de la canalización de datos porque recibe un valor de entrada, realiza un trabajo en dicho valor y, a continuación, genera un resultado que otro componente va a usar.  
  
## Ejemplo  
 En este ejemplo se usa la canalización de datos siguiente para realizar una serie de transformaciones a partir de un valor de entrada inicial especificado:  
  
1.  En la primera fase se calcula el valor absoluto de la entrada.  
  
2.  En la segunda fase se calcula la raíz cuadrada de la entrada.  
  
3.  En la tercera fase se calcula el cuadrado de la entrada.  
  
4.  En la cuarta fase se calcula el valor negativo de la entrada.  
  
5.  En la quinta fase se escribe el resultado final en un búfer de mensajes.  
  
 Finalmente, el ejemplo imprime el resultado de la canalización en la consola.  
  
 [!code-cpp[concrt-data-pipeline#1](../../parallel/concrt/codesnippet/CPP/how-to-use-transformer-in-a-data-pipeline_1.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **The result is \-42.** Es frecuente que una fase de una canalización de datos dé como resultado un valor cuyo tipo difiere del valor de entrada.  En este ejemplo, en la segunda fase se toma un valor de tipo `int` como entrada y se genera la raíz cuadrada de ese valor \(un valor de tipo `double`\) como resultado.  
  
> [!NOTE]
>  La canalización de datos de este ejemplo corresponde a la ilustración.  Dado que cada operación de transformación realiza poco trabajo, la sobrecarga necesaria para realizar el paso de mensajes puede sobrepasar las ventajas de usar una canalización de datos.  
  
## Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o en un archivo denominado `data-pipeline.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc data\-pipeline.cpp**  
  
## Vea también  
 [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)   
 [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Tutorial: Crear una red de procesamiento de imagen](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)