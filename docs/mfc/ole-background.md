---
title: Nociones de OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, about OLE
ms.assetid: 5f654eb5-66b1-40c9-9215-bb85356a67f8
ms.openlocfilehash: f7d65f48c1af678f6626ba7d315ceb735d3e960a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364518"
---
# <a name="ole-background"></a>Nociones de OLE

OLE es un mecanismo que permite a los usuarios crear y editar documentos que contienen elementos u "objetos" creados por varias aplicaciones.

> [!NOTE]
> OLE fue originalmente un acrónimo de Object Linking and Embedding. Sin embargo, ahora se conoce como OLE. Las partes de OLE no relacionadas con la vinculación y la incrustación ahora forman parte de la tecnología Activa.

Los documentos OLE, llamados históricamente documentos compuestos, integran sin problemas varios tipos de datos o componentes. Los clips de sonido, hojas de cálculo y mapas de bits son ejemplos típicos de componentes que se encuentran en documentos OLE. La compatibilidad con OLE en la aplicación permite a los usuarios usar documentos OLE sin preocuparse por cambiar entre las diferentes aplicaciones; OLE realiza el cambio por usted.

Utilice una aplicación contenedora para crear documentos compuestos y una aplicación de servidor o una aplicación de componente para crear los elementos dentro del documento contenedor. Cualquier aplicación que escriba puede ser un contenedor, un servidor o ambos.

OLE incorpora muchos conceptos diferentes que funcionan hacia el objetivo de una interacción perfecta entre las aplicaciones. Estas áreas incluyen lo siguiente:

- Vinculación e incrustación de objetos

   La vinculación y la incrustación son los dos métodos para almacenar elementos creados dentro de un documento OLE que se crearon en otra aplicación. Para obtener información general sobre las diferencias entre los dos, vea el artículo [Fondo OLE: Vincular e incrustar](../mfc/ole-background-linking-and-embedding.md). Para obtener información más detallada, consulte los artículos [Contenedores](../mfc/containers.md) y [servidores](../mfc/servers.md).

- Activación in situ (edición visual)

   La activación de un elemento incrustado en el contexto del documento contenedor se denomina activación in situ o edición visual. La interfaz de la aplicación contenedora cambia para incorporar las características de la aplicación de componente que creó el elemento incrustado. Los elementos vinculados nunca se activan en su lugar porque los datos reales del elemento están contenidos en un archivo independiente, fuera del contexto de la aplicación que contiene el vínculo. Para obtener más información sobre la activación in situ, consulte el artículo [Activación](../mfc/activation-cpp.md).

   > [!NOTE]
   > La vinculación e incrustación y la activación in situ proporcionan las principales características de la edición visual OLE.

- Automation Automation Automation permite que una aplicación conduzca otra aplicación. La aplicación de conducción se conoce como cliente de automatización y la aplicación que se está controlando se conoce como un servidor de automatización o componente de automatización. Para obtener más información sobre la automatización, consulte los [artículos Clientes](../mfc/automation-clients.md) de automatización y Servidores de [automatización](../mfc/automation-servers.md).

   > [!NOTE]
   > La automatización funciona en contextos de tecnología OLE y Active. Puede automatizar cualquier objeto basado en COM.

- archivos compuestos

   Los archivos compuestos proporcionan un formato de archivo estándar que simplifica el almacenamiento estructurado de documentos compuestos para aplicaciones OLE. Dentro de un archivo compuesto, los almacenamientos tienen muchas características de directorios y las secuencias tienen muchas características de archivos. Esta tecnología también se denomina almacenamiento estructurado. Para obtener más información sobre los archivos compuestos, consulte el artículo [Contenedores: Archivos compuestos](../mfc/containers-compound-files.md).

- Transferencia uniforme de datos

   La transferencia uniforme de datos (UDT) es un conjunto de interfaces que permiten enviar y recibir datos de forma estándar, independientemente del método real elegido para transferir los datos. UDT constituye la base para las transferencias de datos mediante arrastrar y soltar. UDT ahora sirve como base para la transferencia de datos de Windows existente, como el Portapapeles y el intercambio dinámico de datos (DDE). Para obtener más información sobre UDT, vea el artículo Objetos de datos y orígenes de [datos (OLE)](../mfc/data-objects-and-data-sources-ole.md).

- Arrastrar y colocar

   Arrastrar y soltar es una técnica de manipulación directa fácil de usar para transferir datos entre aplicaciones, entre ventanas dentro de una aplicación o incluso dentro de una sola ventana de una aplicación. Los datos que se van a transferir se seleccionan y se arrastran al destino deseado. Arrastrar y colocar se basa en la transferencia de datos uniforme. Para obtener más información sobre arrastrar y colocar, consulte el artículo [Arrastrar y colocar](../mfc/drag-and-drop-ole.md).

- Modelo de objetos componentes

   El modelo de objetos componentes (COM) proporciona la infraestructura utilizada cuando los objetos OLE se comunican entre sí. Las clases OLE de MFC simplifican COM para el programador. COM forma parte de la tecnología Active, ya que los objetos COM subyacen a la tecnología OLE y Active. Para obtener más información acerca de COM, consulte los temas de la biblioteca de plantillas activas [(ATL).](../atl/active-template-library-atl-concepts.md)

Algunos de los temas OLE más importantes se tratan en los siguientes artículos:

- [Nociones de OLE: Vincular e incrustar](../mfc/ole-background-linking-and-embedding.md)

- [Nociones de OLE: Contenedores y servidores](../mfc/ole-background-containers-and-servers.md)

- [Nociones de OLE: Estrategias de implementación](../mfc/ole-background-implementation-strategies.md)

- [Nociones de OLE: Implementación de MFC](../mfc/ole-background-mfc-implementation.md)

Para obtener información OLE general que no se encuentra en los artículos anteriores, busque OLE en MSDN.

## <a name="see-also"></a>Consulte también

[OLE](../mfc/ole-in-mfc.md)
