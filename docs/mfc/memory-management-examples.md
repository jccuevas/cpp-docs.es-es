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
ms.openlocfilehash: ca5056303f77f112e18ef09d606789a5b1c92acd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626312"
---
# <a name="memory-management-examples"></a>Administración de memoria: Ejemplos

En este artículo se describe cómo MFC realiza asignaciones de Marcos y asignaciones de montón para cada uno de los tres tipos de asignaciones de memoria típicas:

- [Matriz de bytes.](#_core_allocation_of_an_array_of_bytes)

- [Una estructura de datos](#_core_allocation_of_a_data_structure)

- [Un objeto](#_core_allocation_of_an_object)

## <a name="allocation-of-an-array-of-bytes"></a><a name="_core_allocation_of_an_array_of_bytes"></a>Asignación de una matriz de bytes

#### <a name="to-allocate-an-array-of-bytes-on-the-frame"></a>Para asignar una matriz de bytes en el marco

1. Defina la matriz como se muestra en el código siguiente. La matriz se elimina automáticamente y se reclama su memoria cuando la variable de matriz sale de su ámbito.

   [!code-cpp[NVC_MFC_Utilities#1](codesnippet/cpp/memory-management-examples_1.cpp)]

#### <a name="to-allocate-an-array-of-bytes-or-any-primitive-data-type-on-the-heap"></a>Para asignar una matriz de bytes (o cualquier tipo de datos primitivo) en el montón

1. Use el operador **New** con la sintaxis de la matriz que se muestra en este ejemplo:

   [!code-cpp[NVC_MFC_Utilities#2](codesnippet/cpp/memory-management-examples_2.cpp)]

#### <a name="to-deallocate-the-arrays-from-the-heap"></a>Para desasignar las matrices del montón

1. Use el operador **Delete** de la siguiente manera:

   [!code-cpp[NVC_MFC_Utilities#3](codesnippet/cpp/memory-management-examples_3.cpp)]

## <a name="allocation-of-a-data-structure"></a><a name="_core_allocation_of_a_data_structure"></a>Asignación de una estructura de datos

#### <a name="to-allocate-a-data-structure-on-the-frame"></a>Para asignar una estructura de datos en el marco

1. Defina la variable de estructura como se indica a continuación:

   [!code-cpp[NVC_MFC_Utilities#4](codesnippet/cpp/memory-management-examples_4.cpp)]

   La memoria ocupada por la estructura se recupera cuando sale de su ámbito.

#### <a name="to-allocate-data-structures-on-the-heap"></a>Para asignar estructuras de datos en el montón

1. Use **New** para asignar estructuras de datos en el montón y **Delete** para desasignarlas, como se muestra en los ejemplos siguientes:

   [!code-cpp[NVC_MFC_Utilities#5](codesnippet/cpp/memory-management-examples_5.cpp)]

## <a name="allocation-of-an-object"></a><a name="_core_allocation_of_an_object"></a>Asignación de un objeto

#### <a name="to-allocate-an-object-on-the-frame"></a>Para asignar un objeto en el marco

1. Declare el objeto de la siguiente manera:

   [!code-cpp[NVC_MFC_Utilities#6](codesnippet/cpp/memory-management-examples_6.cpp)]

   El destructor del objeto se invoca automáticamente cuando el objeto sale de su ámbito.

#### <a name="to-allocate-an-object-on-the-heap"></a>Para asignar un objeto en el montón

1. Use el operador **New** , que devuelve un puntero al objeto, para asignar objetos en el montón. Use el operador **Delete** para eliminarlos.

   En los siguientes ejemplos de montón y marco se supone que el `CPerson` constructor no toma ningún argumento.

   [!code-cpp[NVC_MFC_Utilities#7](codesnippet/cpp/memory-management-examples_7.cpp)]

   Si el argumento para el `CPerson` constructor es un puntero a **Char**, la instrucción para la asignación de Marcos es:

   [!code-cpp[NVC_MFC_Utilities#8](codesnippet/cpp/memory-management-examples_8.cpp)]

   La instrucción para la asignación del montón es:

   [!code-cpp[NVC_MFC_Utilities#9](codesnippet/cpp/memory-management-examples_9.cpp)]

## <a name="see-also"></a>Consulte también

[Administración de memoria: Asignación del montón](memory-management-heap-allocation.md)
