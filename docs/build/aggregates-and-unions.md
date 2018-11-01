---
title: Agregados y uniones
ms.date: 11/04/2016
helpviewer_keywords:
- aggregates [C++], and unions
ms.assetid: 859fc211-b111-4f12-af98-de78e48f9b92
ms.openlocfilehash: a4206a5e07c765e9c789eab5c8963c9db4c2f234
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496266"
---
# <a name="aggregates-and-unions"></a>Agregados y uniones

Otros tipos, como matrices, estructuras y uniones, tienen requisitos de alineación más estrictos que garantizan la coherencia agregada y union almacenamiento y recuperación de datos. Estas son las definiciones de matriz, estructura y unión:

- Matriz

   Contiene un grupo ordenado de objetos de datos adyacentes. Cada objeto se denomina un elemento. Todos los elementos dentro de una matriz tienen el mismo tamaño y tipo de datos.

- Estructura

   Contiene un grupo ordenado de objetos de datos. A diferencia de los elementos de una matriz, los objetos de datos dentro de una estructura pueden tener diferentes tipos de datos y tamaños. Cada objeto de datos en una estructura se llama a un miembro.

- Unión

   Objeto que contiene cualquier miembro de un conjunto de miembros con nombre. Los miembros del conjunto con nombre pueden ser de cualquier tipo. El almacenamiento asignado para una unión es igual que el almacenamiento necesario para el miembro de unión, más cualquier relleno necesario para la alineación mayor.

En la tabla siguiente se muestra la alineación sugerida encarecidamente para los miembros de estructuras y uniones escalares.

||||
|-|-|-|
|Tipo escalar|Tipo de datos C|Alineación requerida|
|**INT8**|**char**|Byte|
|**UINT8**|**unsigned char**|Byte|
|**INT16**|**short**|Palabra|
|**UINT16**|**unsigned short**|Palabra|
|**INT32**|**int**, **largo**|Palabra doble|
|**UINT32**|**int sin signo, unsigned long**|Palabra doble|
|**INT64**|**__int64**|Quadword|
|**UINT64**|**unsigned __int64**|Quadword|
|**FP32 (precisión simple)**|**float**|Palabra doble|
|**FP64 (precisión doble)**|**double**|Quadword|
|**PUNTERO**|<strong>\*</strong>|Quadword|
|**__m64**|**__m64 (struct)**|Quadword|
|**__m128**|**__m128 struct**|Octaword|

Se aplican las siguientes reglas de alineación de agregados:

- La alineación de una matriz es igual que la alineación de uno de los elementos de la matriz.

- La alineación del principio de una estructura o unión es la alineación máxima de cualquier miembro individual. Cada miembro dentro de la estructura o unión debe colocarse en su alineación apropiada, tal como se define en la tabla anterior, lo que puede requerir relleno interno implícito, dependiendo del miembro anterior.

- Tamaño de la estructura debe ser un múltiplo integral de su alineación, que puede requerir relleno después del último miembro. Dado que las estructuras y uniones se pueden agrupar en matrices, cada elemento de matriz de una estructura o unión debe empiezan y terminan en la correcta alineación determinada previamente.

- Es posible alinear los datos de tal forma que sean mayores que los requisitos de alineación, siempre se mantienen las reglas anteriores.

- Un compilador individual puede ajustar el empaquetado de una estructura por motivos de tamaño. Por ejemplo [/Zp (alineación de miembros de Struct)](../build/reference/zp-struct-member-alignment.md) permite ajustar el empaquetado de estructuras.

## <a name="see-also"></a>Vea también

[Tipos y almacenamiento](../build/types-and-storage.md)
