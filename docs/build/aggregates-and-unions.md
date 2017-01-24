---
title: "Agregados y uniones | Microsoft Docs"
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
  - "agregados [C++], y uniones"
ms.assetid: 859fc211-b111-4f12-af98-de78e48f9b92
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Agregados y uniones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Otros tipos como matrices, structs y uniones tienen requisitos de alineación más estrictos que garantizan la coherencia en el almacenamiento de agregados y uniones y la recuperación de datos.  Estas son las definiciones de matriz, struct y unión:  
  
 Matriz  
 Contiene un grupo ordenado de objetos de datos adyacentes.  Cada objeto se denomina elemento.  Todos los elementos de una matriz tienen el mismo tamaño y tipo de datos.  
  
 Estructura  
 Contiene un grupo ordenado de objetos de datos.  A diferencia de los elementos de una matriz, los objetos de datos de un struct pueden tener tipos de datos y tamaños diferentes.  Cada objeto de datos en un struct se denomina miembro.  
  
 Unión  
 Un objeto que contiene cualquier miembro de un conjunto de miembros con nombre.  Los miembros del conjunto con nombre pueden ser de cualquier tipo.  El espacio de almacenamiento asignado a una unión es igual al espacio requerido por el miembro de mayor tamaño de la unión, más algo de relleno necesario para alineaciones.  
  
 La tabla siguiente muestra la alineación sugerida encarecidamente para los miembros escalares de uniones y structs.  
  
||||  
|-|-|-|  
|Tipo escalar|Tipo de datos en C|Alineación necesaria|  
|**Int8**|`char`|Byte|  
|**UInt8**|`unsigned char`|Byte|  
|**Int16**|**short**|Word|  
|**UInt16**|**unsigned short**|Word|  
|**Int32**|**int, long**|Doubleword|  
|**UInt32**|**int sin signo, long sin signo**|Doubleword|  
|**Int64**|`__int64`|Quadword|  
|**UInt64**|**unsigned \_\_int64**|Quadword|  
|**FP32 \(precisión sencilla\)**|**float**|Doubleword|  
|**FP64 \(precisión doble\)**|**double**|Quadword|  
|**POINTER**|**\***|Quadword|  
|`__m64`|**struct \_\_m64**|Quadword|  
|`__m128`|**struct \_\_m128**|Octaword|  
  
 Se aplican las siguientes reglas de alineación de agregados:  
  
-   La alineación de una matriz es igual que la alineación de uno de los elementos de la matriz.  
  
-   La alineación del principio de un struct o una unión es la alineación máxima de cualquier miembro individual.  Cada miembro de la estructura o la unión se debe colocar en su alineación apropiada, según se define en la tabla anterior, lo que puede requerir relleno interno implícito, dependiendo del miembro anterior.  
  
-   El tamaño de la estructura debe ser un múltiplo entero de su alineación, que puede requerir relleno después del último miembro.  Puesto que estructuras y uniones se pueden agrupar en matrices, cada elemento de matriz de un struct o una unión debe empezar y finalizar en la alineación apropiada, determinada previamente.  
  
-   Es posible alinear datos de tal modo que sean mayores que los requisitos de alineación, siempre que se respeten las reglas mencionadas.  
  
-   Un compilador individual puede ajustar el empaquetado de un struct por razones de tamaño.  Por ejemplo, [\/Zp \(Alineación de miembros de estructura\)](../build/reference/zp-struct-member-alignment.md) permite ajustar el empaquetado de estructuras.  
  
## Vea también  
 [Tipos y almacenamiento](../build/types-and-storage.md)