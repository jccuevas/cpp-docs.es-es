---
title: 'Contenedores: Elementos de cliente'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client items
- client items and OLE containers
ms.assetid: 231528b5-0744-4f83-8897-083bf55ed087
ms.openlocfilehash: e0d56d4a8f25828de954a78e9bafd8df150c7ff9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437016"
---
# <a name="containers-client-items"></a>Contenedores: Elementos de cliente

En este artículo se explica qué son los elementos de cliente y de qué clases debe derivar sus elementos de cliente a una aplicación.

Elementos de cliente son elementos de datos que pertenecen a otra aplicación que están contenidos en o documento de una aplicación de contenedor OLE al que hace referencia. Se insertan los elementos de cliente cuyos datos se encuentran en el documento; aquellos cuyos datos se almacenan en otra ubicación, al que hace referencia el documento contenedor están vinculadas.

La clase de documento en una aplicación OLE se deriva de la clase [COleDocument](../mfc/reference/coledocument-class.md) en lugar de desde `CDocument`. El `COleDocument` clase hereda de `CDocument` toda la funcionalidad necesaria para utilizar la arquitectura documento/vista en que MFC se basan las aplicaciones. `COleDocument` También define una interfaz que se trata de un documento como una colección de `CDocItem` objetos. Varios `COleDocument` se proporcionan funciones de miembro para agregar, recuperar y eliminar elementos de esa colección.

Cada aplicación de contenedor debe derivar al menos una clase de `COleClientItem`. Los objetos de esta clase representan elementos incrustados o vinculados en el documento OLE. Estos objetos existen durante la vida del documento que los contiene, a menos que se eliminan del documento.

`CDocItem` es la clase base para `COleClientItem` y `COleServerItem`. Objetos de las clases derivadas de estas dos actúan como intermediarios entre el elemento OLE y las aplicaciones cliente y servidor, respectivamente. Cada vez que se agrega un nuevo elemento OLE en el documento, el marco de trabajo MFC agrega un nuevo objeto de la aplicación cliente `COleClientItem`-clase derivada a la colección del documento de `CDocItem` objetos.

## <a name="see-also"></a>Vea también

[Contenedores](../mfc/containers.md)<br/>
[Contenedores: Archivos compuestos](../mfc/containers-compound-files.md)<br/>
[Contenedores: Problemas de la interfaz de usuario](../mfc/containers-user-interface-issues.md)<br/>
[Contenedores: Características avanzadas](../mfc/containers-advanced-features.md)<br/>
[COleClientItem (clase)](../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem (clase)](../mfc/reference/coleserveritem-class.md)
