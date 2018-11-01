---
title: Nociones de OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, about OLE
ms.assetid: 5f654eb5-66b1-40c9-9215-bb85356a67f8
ms.openlocfilehash: 5006a648729e1fc561855fcb8cba1d658a9c82cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619055"
---
# <a name="ole-background"></a>Nociones de OLE

OLE es un mecanismo que permite a los usuarios crear y editar documentos que contengan elementos u "objetos" creado por varias aplicaciones.

> [!NOTE]
>  OLE era originalmente un acrónimo de Object Linking and Embedding. Sin embargo, se ahora se conoce a como OLE. Las partes de OLE no relacionadas con la vinculación e incrustación de objetos ahora forman parte de la tecnología activa.

Documentos OLE, históricamente se les denominados documentos compuestos, integran varios tipos de datos o los componentes. Clips de sonido, hojas de cálculo y los mapas de bits son ejemplos típicos de componentes que se encuentran en documentos OLE. En la aplicación es compatible con OLE permite que los usuarios usen documentos OLE sin preocuparse sobre cómo cambiar entre las diferentes aplicaciones. OLE hace que el cambio automáticamente.

Usar una aplicación de contenedor para crear documentos compuestos y una aplicación de servidor o el componente de aplicación para crear los elementos dentro del documento contenedor. Puede ser cualquier aplicación que escriba un contenedor, un servidor o ambos.

OLE incorpora muchos conceptos diferentes que funcionan hacia el objetivo de interacción perfecta entre aplicaciones. Estas áreas incluyen lo siguiente:

- Vinculación e incrustación de objetos

   Vinculación e incrustación de objetos son los dos métodos para almacenar los elementos creados dentro de un documento OLE que se crearon en otra aplicación. Para obtener información general sobre las diferencias entre los dos, consulte el artículo [fondo OLE: vincular e incrustar](../mfc/ole-background-linking-and-embedding.md). Para obtener más información, consulte los artículos [contenedores](../mfc/containers.md) y [servidores](../mfc/servers.md).

- Activación en contexto (edición Visual)

   Activación de un elemento incrustado en el contexto del documento contenedor se denomina activación en contexto o la edición visual. Interfaz de la aplicación contenedora cambia para incorporar las características de la aplicación de componente que creó el elemento incrustado. Los elementos vinculados nunca se activan en su lugar, porque los datos reales para el elemento está contenidos en un archivo independiente, fuera del contexto de la aplicación que contiene el vínculo. Para obtener más información sobre la activación en contexto, vea el artículo [activación](../mfc/activation-cpp.md).

   > [!NOTE]
   > Vinculación e incrustación y activación en contexto proporcionan las principales características de edición visual OLE.

- Automatización de la automatización permite a una aplicación controlar otra aplicación. La aplicación de conducción se conoce como un cliente de automatización y la aplicación controlada se conoce como un servidor de automatización o el componente de automatización. Para obtener más información sobre la automatización, consulte los artículos [los clientes de automatización](../mfc/automation-clients.md) y [servidores de automatización](../mfc/automation-servers.md).

   > [!NOTE]
   > Automation funciona en los contextos de tecnología OLE y activo. Puede automatizar cualquier objeto basado en COM.

- Archivos compuestos

   Archivos compuestos proporcionan un formato de archivo estándar que simplifica el almacenamiento estructurado de documentos compuestos para las aplicaciones OLE. Dentro de un archivo compuesto, almacenamientos tienen muchas características de directorios y las secuencias tienen muchas características de archivos. Esta tecnología también se denomina almacenamiento estructurado. Para obtener más información sobre los archivos compuestos, vea el artículo [contenedores: archivos compuestos](../mfc/containers-compound-files.md).

- Transferencia de datos uniforme

   Transferencia de datos uniforme (UDT) es un conjunto de interfaces que permiten a los datos enviados y recibidos en un modo estándar, independientemente del método real elegido para transferir los datos. Formularios UDT mediante que transfiere de la base de datos arrastrar y colocar. Ahora sirve como base para la transferencia de datos existente de Windows, como el Portapapeles y el intercambio dinámico de datos (DDE). Para obtener más información sobre UDT, vea el artículo [objetos de datos y orígenes de datos (OLE)](../mfc/data-objects-and-data-sources-ole.md).

- Arrastrar y colocar

   Arrastrar y colocar es una técnica fácil de usar, la manipulación directa de transferir datos entre aplicaciones, entre las ventanas dentro de una aplicación, o incluso en una sola ventana en una aplicación. Los datos que se transfieren está activados y arrastrados hasta el destino deseado. Arrastrar y colocar se basa en la transferencia de datos uniforme. Para obtener más información acerca de arrastrar y colocar, vea el artículo [arrastrar y colocar](../mfc/drag-and-drop-ole.md).

- Modelo de objetos componentes

   El modelo de objetos componentes (COM) proporciona la infraestructura usa al comunican entre sí los objetos OLE. Las clases OLE de MFC simplifican COM para el programador. COM es parte de la tecnología Active, porque los objetos COM subyacen de la tecnología OLE y activo. Para obtener más información acerca de COM, consulte el [Active Template Library (ATL)](../atl/active-template-library-atl-concepts.md) temas.

En los artículos siguientes se tratan algunos de los temas más importantes de OLE:

- [Nociones de OLE: Vincular e incrustar](../mfc/ole-background-linking-and-embedding.md)

- [Nociones de OLE: Contenedores y servidores](../mfc/ole-background-containers-and-servers.md)

- [Nociones de OLE: Estrategias de implementación](../mfc/ole-background-implementation-strategies.md)

- [Nociones de OLE: Implementación de MFC](../mfc/ole-background-mfc-implementation.md)

Para ver información general sobre OLE que no se encuentra en los artículos anteriores, busque OLE en MSDN.

## <a name="see-also"></a>Vea también

[OLE](../mfc/ole-in-mfc.md)

