---
title: Matriz, lista y asignar clases | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- arrays [MFC], classes
- list classes [MFC]
- collection classes [MFC], maps
- map classes [MFC]
- collection classes [MFC], lists
ms.assetid: 81a13a7f-0c2c-4efd-b6bb-b4e624a0743d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8d044f8844fdf46969342d1b4fc5cf2f007c041
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436343"
---
# <a name="array-list-and-map-classes"></a>Clases de matriz, lista y mapa

Para controlar agregados de datos, la biblioteca de clases proporciona un grupo de clases de colección: matrices, listas y mapas, que puede contener una variedad de objetos y tipos predefinidos. Las colecciones son de tamaño dinámicamente. Estas clases se pueden usar en cualquier programa, escritas para Windows o no. Sin embargo, son más útiles para la implementación de las estructuras de datos que definen las clases de documento en el marco de aplicación. Fácilmente puede derivar clases de colección especializadas de estos, o puede crear a partir de las clases de plantilla. Para obtener más información acerca de estos enfoques, vea el artículo [colecciones](../mfc/collections.md). Para obtener una lista de las clases de colección de la plantilla, consulte el artículo [clases de plantillas para matrices, listas y mapas](../mfc/template-classes-for-arrays-lists-and-maps.md).

Las matrices son estructuras de datos unidimensional que se almacenan de forma contigua en la memoria. Admiten el acceso aleatorio muy rápido ya que la dirección de memoria de cualquier elemento puede calcularse multiplicando el índice del elemento por el tamaño de un elemento y agregando el resultado a la dirección base de la matriz. Pero las matrices son muy costosas si tiene que insertar elementos en la matriz, desde toda la matriz pasada el elemento insertado se tiene que mover para dejar espacio para el elemento que se va a insertar. Las matrices pueden aumentar y reducir según sea necesarias.

Las listas son similares a las matrices, pero se almacenan de forma muy diferente. Cada elemento de una lista también incluye un puntero a los elementos anteriores y siguientes, lo que una lista vinculada por partida doble. Es muy rápido para agregar o eliminar elementos, porque si lo hace, sólo implica cambiar algunos punteros. Sin embargo, una lista de la búsqueda puede ser costosa ya que todas las búsquedas que necesita para empezar en uno de los extremos de la lista.

Mapas se relacionan con un valor de clave en un valor de datos. Por ejemplo, la clave de una asignación podría ser una cadena y los datos de un puntero en una lista. Podría solicitar la asignación para ofrecerle el puntero asociado a una cadena determinada. Las búsquedas de mapa son rápidas porque el uso de mapas de las tablas hash para búsquedas de claves. Agregar y eliminar elementos también son rápido. Asignaciones se utilizan a menudo con otras estructuras de datos como índices auxiliares. MFC utiliza un tipo especial de mapa llamado un [mapa de mensajes](../mfc/mapping-messages.md) para asignar mensajes de Windows a un puntero a la función de controlador para ese mensaje.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)

