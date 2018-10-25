---
title: Creación de colecciones de pila y cola | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 96bcaf768ece46c22422fb3d98b85def7c57ed6b
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056599"
---
# <a name="creating-stack-and-queue-collections"></a>Crear colecciones de pila y de cola

En este artículo se explica cómo crear otras estructuras de datos, como [pilas](#_core_stacks) y [colas](#_core_queues), lista de clases de MFC. Los ejemplos usan las clases derivadas de `CList`, pero puede usar `CList` directamente a menos que necesite agregar funcionalidad.

##  <a name="_core_stacks"></a> Pilas

Dado que la colección de listas estándar tiene un encabezado y cola, es fácil crear una colección de lista derivada que imita el comportamiento de una pila de último en el primero en salir. Una pila es como una pila de bandejas de una cafetería. Cuando las bandejas se agregan a la pila, entran en la pila. La última bandeja agregada es la primera que se va a quitar. Las funciones miembro de colección de lista `AddHead` y `RemoveHead` se puede usar para agregar y quitar elementos específicamente desde el principio de la lista; por lo tanto, el último agregado elemento es el primero que se va a quitar.

#### <a name="to-create-a-stack-collection"></a>Para crear una recopilación de pila

1. Derivar una nueva clase de lista de una de las clases de lista MFC existentes y agregue más funciones miembro para admitir la funcionalidad de las operaciones de pila.

   En el ejemplo siguiente se muestra cómo agregar funciones miembro para insertar elementos en la pila, inspeccionar el elemento superior de la pila y extraer el elemento superior de la pila:

   [!code-cpp[NVC_MFCCollections#20](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_1.h)]

Tenga en cuenta que este enfoque expone subyacente `CObList` clase. El usuario puede llamar a cualquiera `CObList` función miembro, si tiene sentido para una pila o no.

##  <a name="_core_queues"></a> Colas

Dado que la colección de listas estándar tiene un encabezado y una cola, también es fácil crear una colección de lista derivada que imita el comportamiento de una cola primero en el primero en salir. Una cola es como una línea de personas en una cafetería. La primera persona en línea es el primero atendiendo. Igual que tienen más personas, van al final de la línea debe esperar su turno. Las funciones miembro de colección de lista `AddTail` y `RemoveHead` se puede usar para agregar y quitar elementos específicamente desde el encabezado o un final de la lista; por lo tanto, el último agregado elemento siempre es el último que se va a quitar.

#### <a name="to-create-a-queue-collection"></a>Para crear una colección de colas

1. Derivar una nueva clase de lista de una de las clases de lista predefinidas proporcionadas con la biblioteca Microsoft Foundation Class y agregue más funciones miembro para admitir la semántica de las operaciones de cola.

   El ejemplo siguiente muestra cómo se pueden anexar funciones miembro para agregar un elemento al final de la cola y obtener el elemento de la parte delantera de la cola.

   [!code-cpp[NVC_MFCCollections#21](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_2.h)]

## <a name="see-also"></a>Vea también

[Colecciones](../mfc/collections.md)

