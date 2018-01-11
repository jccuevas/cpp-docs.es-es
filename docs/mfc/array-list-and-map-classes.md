---
title: Matriz, lista y mapa clases | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.mfc
dev_langs: C++
helpviewer_keywords:
- arrays [MFC], classes
- list classes [MFC]
- collection classes [MFC], maps
- map classes [MFC]
- collection classes [MFC], lists
ms.assetid: 81a13a7f-0c2c-4efd-b6bb-b4e624a0743d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7de6f3c72b31ea9094af032bc81e9f2506606cce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="array-list-and-map-classes"></a>Clases de matriz, lista y mapa
Para gestionar los agregados de datos, la biblioteca de clases proporciona un grupo de clases de colección: matrices, listas y mapas, que puede contener una variedad de objetos y tipos predefinidos. Las colecciones se dimensiona dinámicamente. Estas clases se pueden usar en cualquier programa, si escritos para Windows o no. Sin embargo, son más útiles para implementar las estructuras de datos que definen las clases de documento en el marco de aplicación. Puede derivar clases de colección especializadas con facilidad desde estas, o puede crear a partir de las clases de plantilla. Para obtener más información acerca de estos métodos, vea el artículo [colecciones](../mfc/collections.md). Para obtener una lista de las clases de colección de plantilla, vea el artículo [clases de plantillas para matrices, listas y mapas](../mfc/template-classes-for-arrays-lists-and-maps.md).  
  
 Las matrices son estructuras de datos unidimensional que se almacenan de forma contigua en la memoria. Que admiten el acceso aleatorio muy rápido porque la dirección de memoria de cualquier elemento puede calcularse multiplicando el índice del elemento por el tamaño de un elemento y agrega el resultado a la dirección base de la matriz. Pero las matrices son muy costosas si tiene que insertar elementos en la matriz, porque toda la matriz pasada el elemento insertado se tiene que mover para dejar espacio para el elemento que se va a insertar. Las matrices pueden aumentar y reducir según sea necesarias.  
  
 Las listas son similares a las matrices, pero se almacenan de forma muy diferente. Cada elemento de una lista también incluye un puntero a los elementos anteriores y siguientes, que hace una lista doblemente vinculada. Es muy rápido para agregar o eliminar elementos porque solo si lo hace, implica cambiar algunos punteros. Sin embargo, la búsqueda en una lista puede ser costosa porque todas las búsquedas deben iniciar en uno de los extremos de la lista.  
  
 Mapas están relacionadas con un valor de clave en un valor de datos. Por ejemplo, la clave de una asignación podría ser una cadena y los datos de un puntero a una lista. Usted podría solicitar la asignación para proporcionarle el puntero asociado a una cadena determinada. Búsquedas de mapa son rápidas, porque los mapas usan tablas hash para búsquedas de claves. Agregar y eliminar elementos también son rápido. Asignaciones se utilizan a menudo con otras estructuras de datos como índices auxiliares. MFC utiliza una clase especial de mapa llamado un [mapa de mensajes](../mfc/mapping-messages.md) para asignar mensajes de Windows a un puntero a la función de controlador para ese mensaje.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

