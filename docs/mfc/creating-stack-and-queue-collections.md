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
ms.openlocfilehash: 5b3427f7bb2e46435ddf2768bcbb816f9d7e5c1a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371602"
---
# <a name="creating-stack-and-queue-collections"></a>Crear colecciones de pila y de cola

En este artículo se explica cómo crear otras estructuras de datos, como [pilas](#_core_stacks) y colas, a partir de [clases](#_core_queues)de lista MFC. Los ejemplos utilizan clases derivadas `CList`de `CList` , pero puede usar directamente a menos que necesite agregar funcionalidad.

## <a name="stacks"></a><a name="_core_stacks"></a>Pilas

Dado que la colección de lista estándar tiene un cabezal y una cola, es fácil crear una colección de lista derivada que imita el comportamiento de una pila de último en entrar y salir. Una pila es como una pila de bandejas en una cafetería. A medida que las bandejas se agregan a la pila, van en la parte superior de la pila. La última bandeja añadida es la primera que se va a quitar. Las funciones `AddHead` miembro `RemoveHead` de la colección de lista y se pueden utilizar para agregar y quitar elementos específicamente del jefe de la lista; por lo tanto, el elemento añadido más recientemente es el primero en ser eliminado.

#### <a name="to-create-a-stack-collection"></a>Para crear una colección de pilas

1. Derive una nueva clase de lista de una de las clases de lista MFC existentes y agregue más funciones miembro para admitir la funcionalidad de las operaciones de pila.

   En el ejemplo siguiente se muestra cómo agregar funciones miembro para insertar elementos en la pila, echar un vistazo al elemento superior de la pila y extraer el elemento superior de la pila:

   [!code-cpp[NVC_MFCCollections#20](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_1.h)]

Tenga en cuenta que este `CObList` enfoque expone la clase subyacente. El usuario puede `CObList` llamar a cualquier función miembro, tenga sentido para una pila o no.

## <a name="queues"></a>Colas de <a name="_core_queues"></a>

Dado que la colección de lista estándar tiene un cabezal y una cola, también es fácil crear una colección de lista derivada que imita el comportamiento de una cola de primero en entrar y salir. Una cola es como una fila de personas en una cafetería. La primera persona en la fila es la primera en ser servida. A medida que más gente viene, van al final de la fila para esperar su turno. Las funciones `AddTail` miembro `RemoveHead` de la colección de listas y se pueden utilizar para agregar y quitar elementos específicamente de la cabeza o la cola de la lista; por lo tanto, el elemento añadido más recientemente es siempre el último en ser eliminado.

#### <a name="to-create-a-queue-collection"></a>Para crear una colección de colas

1. Derive una nueva clase de lista de una de las clases de lista predefinidas proporcionadas con la biblioteca Microsoft Foundation Class y agregue más funciones miembro para admitir la semántica de las operaciones de cola.

   En el ejemplo siguiente se muestra cómo se pueden anexar funciones miembro para agregar un elemento al final de la cola y obtener el elemento del frente de la cola.

   [!code-cpp[NVC_MFCCollections#21](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_2.h)]

## <a name="see-also"></a>Consulte también

[Colecciones](../mfc/collections.md)
