---
title: "Administración de memoria: Ejemplos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8282847c9bbaf18b9f54180b08b5d98a109d75b4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="memory-management-examples"></a>Administración de memoria: Ejemplos
Este artículo describe cómo realiza MFC la asignación en el marco y las asignaciones del montón para cada uno de los tres tipos típicos de las asignaciones de memoria:  
  
-   [Una matriz de bytes](#_core_allocation_of_an_array_of_bytes)  
  
-   [Una estructura de datos](#_core_allocation_of_a_data_structure)  
  
-   [Un objeto](#_core_allocation_of_an_object)  
  
##  <a name="_core_allocation_of_an_array_of_bytes"></a>Asignación de una matriz de Bytes  
  
#### <a name="to-allocate-an-array-of-bytes-on-the-frame"></a>Para asignar una matriz de bytes en el marco  
  
1.  Defina la matriz tal como se muestra en el código siguiente. La matriz se elimina automáticamente y su memoria se recupera cuando la variable de matriz sale de su ámbito.  
  
     [!code-cpp[NVC_MFC_Utilities#1](../mfc/codesnippet/cpp/memory-management-examples_1.cpp)]  
  
#### <a name="to-allocate-an-array-of-bytes-or-any-primitive-data-type-on-the-heap"></a>Para asignar una matriz de bytes (o cualquier tipo de datos primitivo) en el montón  
  
1.  Use la **nueva** operador con la sintaxis de la matriz se muestra en este ejemplo:  
  
     [!code-cpp[NVC_MFC_Utilities#2](../mfc/codesnippet/cpp/memory-management-examples_2.cpp)]  
  
#### <a name="to-deallocate-the-arrays-from-the-heap"></a>Para desasignar las matrices del montón  
  
1.  Use la **eliminar** operador como sigue:  
  
     [!code-cpp[NVC_MFC_Utilities#3](../mfc/codesnippet/cpp/memory-management-examples_3.cpp)]  
  
##  <a name="_core_allocation_of_a_data_structure"></a>Asignación de una estructura de datos  
  
#### <a name="to-allocate-a-data-structure-on-the-frame"></a>Para asignar una estructura de datos en el marco  
  
1.  Defina la variable de estructura como sigue:  
  
     [!code-cpp[NVC_MFC_Utilities#4](../mfc/codesnippet/cpp/memory-management-examples_4.cpp)]  
  
     Cuando sale de su ámbito, se reclama la memoria ocupada por la estructura.  
  
#### <a name="to-allocate-data-structures-on-the-heap"></a>Para asignar estructuras de datos en el montón  
  
1.  Use **nueva** asignar estructuras de datos en el montón y **eliminar** para cancelar la asignación, tal como se muestra en los ejemplos siguientes:  
  
     [!code-cpp[NVC_MFC_Utilities#5](../mfc/codesnippet/cpp/memory-management-examples_5.cpp)]  
  
##  <a name="_core_allocation_of_an_object"></a>Asignación de un objeto  
  
#### <a name="to-allocate-an-object-on-the-frame"></a>Para asignar un objeto en el marco  
  
1.  Declare el objeto como sigue:  
  
     [!code-cpp[NVC_MFC_Utilities#6](../mfc/codesnippet/cpp/memory-management-examples_6.cpp)]  
  
     El destructor del objeto se invoca automáticamente cuando el objeto sale de su ámbito.  
  
#### <a name="to-allocate-an-object-on-the-heap"></a>Para asignar un objeto en el montón  
  
1.  Use la **nueva** operador, que devuelve un puntero al objeto, para asignar objetos en el montón. Use la **eliminar** operador para eliminarlos.  
  
     Los siguientes ejemplos de montón y marco asumen que el `CPerson` constructor no toma ningún argumento.  
  
     [!code-cpp[NVC_MFC_Utilities#7](../mfc/codesnippet/cpp/memory-management-examples_7.cpp)]  
  
     Si el argumento para la `CPerson` constructor es un puntero a `char`, la instrucción de asignación en el marco es:  
  
     [!code-cpp[NVC_MFC_Utilities#8](../mfc/codesnippet/cpp/memory-management-examples_8.cpp)]  
  
     La instrucción de asignación en el montón es:  
  
     [!code-cpp[NVC_MFC_Utilities#9](../mfc/codesnippet/cpp/memory-management-examples_9.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Administración de memoria: asignación del montón](../mfc/memory-management-heap-allocation.md)

