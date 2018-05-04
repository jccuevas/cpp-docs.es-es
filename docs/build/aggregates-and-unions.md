---
title: Agregados y uniones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- aggregates [C++], and unions
ms.assetid: 859fc211-b111-4f12-af98-de78e48f9b92
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b1afd3be89e1d18da9889d88dbbbef3fb104e02
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="aggregates-and-unions"></a>Agregados y uniones
Otros tipos, como matrices, estructuras y uniones, tienen requisitos de alineación más estrictos que garantizan coherente agregada y union almacenamiento y recuperación de datos. Estas son las definiciones de matriz, estructura y unión:  
  
 Matriz  
 Contiene un grupo ordenado de objetos de datos adyacentes. Cada objeto se denomina un elemento. Todos los elementos dentro de una matriz tienen el mismo tamaño y tipo de datos.  
  
 Estructura  
 Contiene un grupo ordenado de objetos de datos. A diferencia de los elementos de una matriz, los objetos de datos dentro de una estructura pueden tener tamaños y tipos de datos diferentes. Cada objeto de datos en una estructura se denomina a miembro.  
  
 Unión  
 Objeto que contiene cualquier miembro de un conjunto de miembros con nombre. Los miembros del conjunto con nombre pueden ser de cualquier tipo. El almacenamiento asignado para una unión es igual que el almacenamiento necesario para el miembro mayor de unión, más algo de relleno necesario para la alineación.  
  
 En la tabla siguiente se muestra la alineación sugerida encarecidamente para los miembros escalares de uniones y estructuras.  
  
||||  
|-|-|-|  
|Tipo escalar|Tipo de datos C|Alineación requerida|  
|**INT8**|`char`|Byte|  
|**UINT8**|`unsigned char`|Byte|  
|**INT16**|**short**|Palabra|  
|**UINT16**|**unsigned short**|Palabra|  
|**INT32**|**int, long**|Palabra doble|  
|**UINT32**|**int sin signo, largo sin signo**|Palabra doble|  
|**INT64**|`__int64`|Quadword|  
|**UINT64**|**unsigned __int64**|Quadword|  
|**FP32 (precisión simple)**|**float**|Palabra doble|  
|**FP64 (precisión doble)**|**double**|Quadword|  
|**PUNTERO**|**\***|Quadword|  
|`__m64`|**__m64 (struct)**|Quadword|  
|`__m128`|**__m128 (struct)**|Octaword|  
  
 Se aplican las siguientes reglas de alineación de agregados:  
  
-   La alineación de una matriz es igual que la alineación de uno de los elementos de la matriz.  
  
-   La alineación del principio de una estructura o unión es la alineación máxima de cualquier miembro individual. Cada miembro dentro de la estructura o unión debe colocarse en su alineación apropiada, como se define en la tabla anterior, lo que puede requerir relleno interno implícito, dependiendo del miembro anterior.  
  
-   Tamaño de la estructura debe ser un múltiplo entero de su alineación, lo que puede requerir relleno después del último miembro. Puesto que las estructuras y uniones se pueden agrupar en matrices, cada elemento de la matriz de una estructura o unión debe empezar y finalizar en la alineación apropiada, determinada previamente.  
  
-   Es posible alinear datos de tal manera que sean mayores que los requisitos de alineación siempre que se mantienen las reglas anteriores.  
  
-   Un compilador individual puede ajustar el empaquetado de una estructura por razones de tamaño. Por ejemplo [/Zp (alineación de miembros de Struct)](../build/reference/zp-struct-member-alignment.md) permite ajustar el empaquetado de estructuras.  
  
## <a name="see-also"></a>Vea también  
 [Tipos y almacenamiento](../build/types-and-storage.md)
