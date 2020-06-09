---
title: Nociones de OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, about OLE
ms.assetid: 5f654eb5-66b1-40c9-9215-bb85356a67f8
ms.openlocfilehash: 96ece9a2a5be6ea29c95e17e81f6ce4adbfd4c0b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624161"
---
# <a name="ole-background"></a>Nociones de OLE

OLE es un mecanismo que permite a los usuarios crear y editar documentos que contienen elementos o "objetos" creados por varias aplicaciones.

> [!NOTE]
> OLE originalmente era un acrónimo de vinculación e incrustación de objetos. Sin embargo, ahora se conoce como OLE. Las partes de OLE que no están relacionadas con la vinculación e incrustación ahora forman parte de la tecnología activa.

Los documentos OLE, tradicionalmente denominados documentos compuestos, integran sin problemas distintos tipos de datos o componentes. Los clips de sonido, las hojas de cálculo y los mapas de bits son ejemplos típicos de componentes que se encuentran en documentos OLE. La compatibilidad de OLE en la aplicación permite a los usuarios utilizar documentos OLE sin preocuparse por cambiar entre las distintas aplicaciones. OLE realiza el cambio.

Use una aplicación contenedora para crear documentos compuestos y una aplicación de servidor o una aplicación de componentes para crear los elementos dentro del documento contenedor. Cualquier aplicación que escriba puede ser un contenedor, un servidor o ambos.

OLE incorpora muchos conceptos diferentes que funcionan con el objetivo de una interacción fluida entre las aplicaciones. Entre estas áreas se incluyen las siguientes:

- Vinculación e incrustación de objetos

   La vinculación e incrustación son los dos métodos para almacenar los elementos creados dentro de un documento OLE creado en otra aplicación. Para obtener información general sobre las diferencias entre los dos, vea el artículo [OLE Background: vinculación e incrustación](ole-background-linking-and-embedding.md). Para obtener información más detallada, vea los artículos [contenedores](containers.md) y [servidores](servers.md).

- Activación en contexto (edición visual)

   La activación de un elemento incrustado en el contexto del documento contenedor se denomina activación en contexto o edición visual. La interfaz de la aplicación contenedora cambia para incorporar las características de la aplicación de componentes que creó el elemento incrustado. Los elementos vinculados nunca se activan en su lugar porque los datos reales del elemento se encuentran en un archivo independiente, fuera del contexto de la aplicación que contiene el vínculo. Para obtener más información sobre la activación en contexto, consulte el artículo [activación](activation-cpp.md).

   > [!NOTE]
   > La vinculación e incrustación y la activación en contexto proporcionan las principales características de la edición visual de OLE.

- Automatización de automatización permite a una aplicación controlar otra aplicación. La aplicación de conducción se conoce como cliente de automatización y la aplicación que se controla se conoce como un servidor de automatización o un componente de automatización. Para obtener más información sobre la automatización, consulte los artículos [clientes de automatización](automation-clients.md) y [servidores de automatización](automation-servers.md).

   > [!NOTE]
   > La automatización funciona en los contextos de tecnología OLE y activo. Puede automatizar cualquier objeto basado en COM.

- archivos compuestos

   Los archivos compuestos proporcionan un formato de archivo estándar que simplifica el almacenamiento estructurado de documentos compuestos para aplicaciones OLE. Dentro de un archivo compuesto, los almacenamientos tienen muchas características de los directorios y las secuencias tienen muchas características de los archivos. Esta tecnología también se denomina almacenamiento estructurado. Para obtener más información sobre los archivos compuestos, vea el artículo [contenedores: archivos compuestos](containers-compound-files.md).

- Transferencia de datos uniformes

   El Transferencia de datos uniforme (UDT) es un conjunto de interfaces que permiten enviar y recibir datos de forma estándar, independientemente del método real elegido para transferir los datos. UDT constituye la base para las transferencias de datos arrastrando y colocando. UDT ahora sirve como base para la transferencia de datos de Windows existente, como el portapapeles y el intercambio dinámico de datos (DDE). Para obtener más información sobre UDT, vea el artículo [objetos de datos y orígenes de datos (OLE)](data-objects-and-data-sources-ole.md).

- Arrastrar y colocar

   Arrastrar y colocar es una técnica fácil de usar y de manipulación directa para transferir datos entre aplicaciones, entre ventanas dentro de una aplicación, o incluso dentro de una única ventana en una aplicación. Los datos que se van a transferir se seleccionan y se arrastran al destino deseado. Arrastrar y colocar se basa en la transferencia de datos uniforme. Para obtener más información sobre la función de arrastrar y colocar, vea el artículo [arrastrar y colocar](drag-and-drop-ole.md).

- Modelo de objetos componentes

   El modelo de objetos componentes (COM) proporciona la infraestructura que se utiliza cuando los objetos OLE se comunican entre sí. Las clases OLE de MFC simplifican COM para el programador. COM forma parte de la tecnología activa, ya que los objetos COM subyacen a la tecnología OLE y activa. Para obtener más información acerca de COM, vea los temas sobre [Active Template Library (ATL)](../atl/active-template-library-atl-concepts.md) .

En los artículos siguientes se tratan algunos de los temas de OLE más importantes:

- [Nociones de OLE: Vincular e incrustar](ole-background-linking-and-embedding.md)

- [Nociones de OLE: Contenedores y servidores](ole-background-containers-and-servers.md)

- [Nociones de OLE: Estrategias de implementación](ole-background-implementation-strategies.md)

- [Nociones de OLE: Implementación de MFC](ole-background-mfc-implementation.md)

Para obtener información general de OLE que no se encuentra en los artículos anteriores, busque OLE en MSDN.

## <a name="see-also"></a>Consulte también

[OLE](ole-in-mfc.md)
