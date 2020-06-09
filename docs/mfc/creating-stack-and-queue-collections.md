---
title: Crear colecciones de pila y de cola
ms.date: 11/04/2016
helpviewer_keywords:
- MFC collection classes [MFC], stack collections
- collections, stack
- stack
- collection classes [MFC], creating
- queue collections
- MFC collection classes [MFC], queue collections
- stack collections
- collections, queue
ms.assetid: 3c7bc198-35f0-4fc3-aaed-6005a0f22638
ms.openlocfilehash: 5db90422f78fc6ca3bc2a182f9569c33db56cad1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623217"
---
# <a name="creating-stack-and-queue-collections"></a>Crear colecciones de pila y de cola

En este artículo se explica cómo crear otras estructuras de datos, como [pilas](#_core_stacks) y [colas](#_core_queues), desde clases de lista de MFC. En los ejemplos se usan clases derivadas de `CList` , pero puede usar `CList` directamente a menos que necesite agregar funcionalidad.

## <a name="stacks"></a><a name="_core_stacks"></a>Pilas

Dado que la colección de listas estándar tiene un encabezado y una cola, es fácil crear una colección de listas derivadas que imite el comportamiento de una pila de tipo "el último en salir es el primero en salir". Una pila es como una pila de bandejas en una cafetería. A medida que las bandejas se agregan a la pila, se encuentran en la parte superior de la pila. La última bandeja agregada es la primera que se va a quitar. Las funciones miembro de colección de lista `AddHead` y `RemoveHead` se pueden usar para agregar y quitar elementos específicamente del encabezado de la lista; por lo tanto, el elemento agregado más recientemente es el primero que se va a quitar.

#### <a name="to-create-a-stack-collection"></a>Para crear una colección de pilas

1. Derive una nueva clase de lista de una de las clases de lista de MFC existentes y agregue más funciones miembro para admitir la funcionalidad de las operaciones de pila.

   En el ejemplo siguiente se muestra cómo agregar funciones miembro para enviar elementos a la pila, inspeccionar el elemento superior de la pila y extraer el elemento superior de la pila:

   [!code-cpp[NVC_MFCCollections#20](codesnippet/cpp/creating-stack-and-queue-collections_1.h)]

Tenga en cuenta que este enfoque expone la `CObList` clase subyacente. El usuario puede llamar a cualquier `CObList` función miembro, tanto si tiene sentido para una pila como si no.

## <a name="queues"></a>Colas de <a name="_core_queues"></a>

Dado que la colección de listas estándar tiene un encabezado y una cola, también es fácil crear una colección de listas derivadas que imite el comportamiento de una cola primero en salir. Una cola es como una línea de personas en una cafetería. La primera persona de la línea es la primera que se atiende. A medida que vayan llegando más personas, Irán al final de la línea para esperar su turno. Las funciones miembro de colección `AddTail` de lista y `RemoveHead` se pueden usar para agregar y quitar elementos específicamente del encabezado o la cola de la lista; por lo tanto, el elemento agregado más recientemente siempre es el último que se va a quitar.

#### <a name="to-create-a-queue-collection"></a>Para crear una colección de colas

1. Derive una nueva clase List de una de las clases de lista predefinidas proporcionadas con la biblioteca MFC y agregue más funciones miembro para admitir la semántica de las operaciones de cola.

   En el ejemplo siguiente se muestra cómo puede anexar funciones miembro para agregar un elemento al final de la cola y obtener el elemento de la parte delantera de la cola.

   [!code-cpp[NVC_MFCCollections#21](codesnippet/cpp/creating-stack-and-queue-collections_2.h)]

## <a name="see-also"></a>Consulte también

[Colecciones](collections.md)
