---
title: 'Contenedores: Elementos de cliente'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client items
- client items and OLE containers
ms.assetid: 231528b5-0744-4f83-8897-083bf55ed087
ms.openlocfilehash: ad347c78fb6aa7af94b306a3edb538b9f740c305
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619018"
---
# <a name="containers-client-items"></a>Contenedores: Elementos de cliente

En este artículo se explica qué son los elementos de cliente y de qué clases debe derivar sus elementos de cliente.

Los elementos de cliente son elementos de datos que pertenecen a otra aplicación que están contenidas en un documento de una aplicación contenedora OLE o a los que este hace referencia. Los elementos de cliente cuyos datos se incluyen en el documento se incrustan; aquellos cuyos datos se almacenan en otra ubicación a la que hace referencia el documento contenedor están vinculados.

La clase de documento en una aplicación OLE se deriva de la clase [COleDocument](reference/coledocument-class.md) en lugar de `CDocument` . La `COleDocument` clase hereda de `CDocument` toda la funcionalidad necesaria para utilizar la arquitectura documento/vista en la que se basan las aplicaciones MFC. `COleDocument`también define una interfaz que trata un documento como una colección de `CDocItem` objetos. `COleDocument`Se proporcionan varias funciones miembro para agregar, recuperar y eliminar elementos de esa colección.

Cada aplicación contenedora debe derivar al menos una clase de `COleClientItem` . Los objetos de esta clase representan elementos, incrustados o vinculados, en el documento OLE. Estos objetos existen mientras dure el documento que los contiene, a menos que se eliminen del documento.

`CDocItem`es la clase base para `COleClientItem` y `COleServerItem` . Los objetos de clases derivadas de estos dos actúan como intermediarios entre el elemento OLE y las aplicaciones cliente y servidor, respectivamente. Cada vez que se agrega un nuevo elemento OLE al documento, el marco de trabajo de MFC agrega un nuevo objeto de la clase derivada de la aplicación cliente `COleClientItem` a la colección de objetos del documento `CDocItem` .

## <a name="see-also"></a>Consulte también

[Contenedores](containers.md)<br/>
[Contenedores: Archivos compuestos](containers-compound-files.md)<br/>
[Contenedores: Problemas de la interfaz de usuario](containers-user-interface-issues.md)<br/>
[Contenedores: Características avanzadas](containers-advanced-features.md)<br/>
[COleClientItem (clase)](reference/coleclientitem-class.md)<br/>
[COleServerItem (clase)](reference/coleserveritem-class.md)
