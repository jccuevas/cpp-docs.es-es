---
title: Clases de matriz, lista y mapa
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [MFC], classes
- list classes [MFC]
- collection classes [MFC], maps
- map classes [MFC]
- collection classes [MFC], lists
ms.assetid: 81a13a7f-0c2c-4efd-b6bb-b4e624a0743d
ms.openlocfilehash: f5fe4acb35074e924555029d715ccbc23b55f49a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446514"
---
# <a name="array-list-and-map-classes"></a>Clases de matriz, lista y mapa

Para controlar los agregados de los datos, la biblioteca de clases proporciona un grupo de clases de colección (matrices, listas y asignaciones) que pueden contener diversos tipos de objetos y predefinidos. Las colecciones tienen un tamaño dinámico. Estas clases se pueden usar en cualquier programa, tanto si están escritas para Windows como si no. Sin embargo, son más útiles para implementar las estructuras de datos que definen las clases de documento en el marco de trabajo de la aplicación. Puede derivar fácilmente clases de colección especializadas de estas o puede crearlas en función de las clases de plantilla. Para obtener más información sobre estos métodos, vea las [colecciones](../mfc/collections.md)de artículos. Para obtener una lista de las clases de colección de plantillas, vea el artículo [plantillas clases para matrices, listas y asignaciones](../mfc/template-classes-for-arrays-lists-and-maps.md).

Las matrices son estructuras de datos unidimensionales que se almacenan de forma contigua en la memoria. Admiten un acceso aleatorio muy rápido, ya que la dirección de memoria de cualquier elemento determinado se puede calcular multiplicando el índice del elemento por el tamaño de un elemento y agregando el resultado a la dirección base de la matriz. Sin embargo, las matrices son muy caras si tiene que insertar elementos en la matriz, ya que toda la matriz más allá del elemento insertado debe moverse para dejar espacio para el elemento que se va a insertar. Las matrices pueden aumentar y reducir según sea necesario.

Las listas son similares a las matrices, pero se almacenan de forma muy diferente. Cada elemento de una lista también incluye un puntero a los elementos anterior y siguiente, convirtiéndolo en una lista de doble vínculo. Es muy rápido agregar o eliminar elementos, ya que hacerlo solo implica cambiar algunos punteros. Sin embargo, la búsqueda de una lista puede ser costosa, ya que todas las búsquedas deben iniciarse en uno de los extremos de la lista.

Maps relaciona un valor de clave con un valor de datos. Por ejemplo, la clave de un mapa podría ser una cadena y los datos de un puntero a una lista. Se le pedirá al mapa que le proporcione el puntero asociado a una cadena determinada. Las búsquedas de mapas son rápidas porque las asignaciones usan tablas hash para búsquedas de claves. La adición y eliminación de elementos también es rápida. Las asignaciones se utilizan a menudo con otras estructuras de datos como índices auxiliares. MFC utiliza un tipo especial de mapa denominado [mapa de mensajes](../mfc/mapping-messages.md) para asignar mensajes de Windows a un puntero a la función de controlador de ese mensaje.

## <a name="see-also"></a>Consulte también

[Información general sobre clases](../mfc/class-library-overview.md)
