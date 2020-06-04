---
title: 'Administración de memoria: Ejemplos'
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], memory allocation
- data structures [MFC]
- arrays [MFC], allocating resources
- objects [MFC], allocating memory
- data structures [MFC], allocating memory
- examples [MFC], memory allocation
- heap allocation [MFC], examples
- memory allocation [MFC], arrays
- MFC, memory management
- struct memory allocation [MFC]
- types [MFC], memory allocation
- memory allocation [MFC], objects
- memory allocation [MFC], examples
- arrays [MFC], memory management
- frame allocation [MFC]
- memory allocation [MFC], data structures
ms.assetid: f10240f8-b698-4c83-9288-97a54318930b
ms.openlocfilehash: 3a1e647175b7b5294e672efbf234e3ae2853e411
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367844"
---
# <a name="memory-management-examples"></a>Administración de memoria: Ejemplos

En este artículo se describe cómo MFC realiza asignaciones de marcos y asignaciones de montón para cada uno de los tres tipos típicos de asignaciones de memoria:

- [Una matriz de bytes](#_core_allocation_of_an_array_of_bytes)

- [Una estructura de datos](#_core_allocation_of_a_data_structure)

- [Un objeto](#_core_allocation_of_an_object)

## <a name="allocation-of-an-array-of-bytes"></a><a name="_core_allocation_of_an_array_of_bytes"></a>Asignación de una matriz de bytes

#### <a name="to-allocate-an-array-of-bytes-on-the-frame"></a>Para asignar una matriz de bytes en la trama

1. Defina la matriz como se muestra en el código siguiente. La matriz se elimina automáticamente y su memoria se recupera cuando la variable de matriz sale de su ámbito.

   [!code-cpp[NVC_MFC_Utilities#1](../mfc/codesnippet/cpp/memory-management-examples_1.cpp)]

#### <a name="to-allocate-an-array-of-bytes-or-any-primitive-data-type-on-the-heap"></a>Para asignar una matriz de bytes (o cualquier tipo de datos primitivo) en el montón

1. Utilice el **operador new** con la sintaxis de la matriz mostrada en este ejemplo:

   [!code-cpp[NVC_MFC_Utilities#2](../mfc/codesnippet/cpp/memory-management-examples_2.cpp)]

#### <a name="to-deallocate-the-arrays-from-the-heap"></a>Para desasignar las matrices del montón

1. Utilice el operador **delete** de la siguiente manera:

   [!code-cpp[NVC_MFC_Utilities#3](../mfc/codesnippet/cpp/memory-management-examples_3.cpp)]

## <a name="allocation-of-a-data-structure"></a><a name="_core_allocation_of_a_data_structure"></a>Asignación de una estructura de datos

#### <a name="to-allocate-a-data-structure-on-the-frame"></a>Para asignar una estructura de datos en el marco

1. Defina la variable de estructura de la siguiente manera:

   [!code-cpp[NVC_MFC_Utilities#4](../mfc/codesnippet/cpp/memory-management-examples_4.cpp)]

   La memoria ocupada por la estructura se recupera cuando sale de su ámbito.

#### <a name="to-allocate-data-structures-on-the-heap"></a>Para asignar estructuras de datos en el montón

1. Utilice **new** para asignar estructuras de datos en el montón y **eliminarlas** para desasignarlas, como se muestra en los ejemplos siguientes:

   [!code-cpp[NVC_MFC_Utilities#5](../mfc/codesnippet/cpp/memory-management-examples_5.cpp)]

## <a name="allocation-of-an-object"></a><a name="_core_allocation_of_an_object"></a>Asignación de un objeto

#### <a name="to-allocate-an-object-on-the-frame"></a>Para asignar un objeto en el marco

1. Declare el objeto de la siguiente manera:

   [!code-cpp[NVC_MFC_Utilities#6](../mfc/codesnippet/cpp/memory-management-examples_6.cpp)]

   El destructor del objeto se invoca automáticamente cuando el objeto sale de su ámbito.

#### <a name="to-allocate-an-object-on-the-heap"></a>Para asignar un objeto en el montón

1. Utilice el operador **new,** que devuelve un puntero al objeto, para asignar objetos en el montón. Utilice el operador **delete** para eliminarlos.

   En los siguientes ejemplos de `CPerson` montón y marco se supone que el constructor no toma ningún argumento.

   [!code-cpp[NVC_MFC_Utilities#7](../mfc/codesnippet/cpp/memory-management-examples_7.cpp)]

   Si el argumento `CPerson` para el constructor es un puntero a **char**, la instrucción para la asignación de marcos es:

   [!code-cpp[NVC_MFC_Utilities#8](../mfc/codesnippet/cpp/memory-management-examples_8.cpp)]

   La instrucción para la asignación de montones es:

   [!code-cpp[NVC_MFC_Utilities#9](../mfc/codesnippet/cpp/memory-management-examples_9.cpp)]

## <a name="see-also"></a>Consulte también

[Administración de memoria: Asignación del montón](../mfc/memory-management-heap-allocation.md)
