---
title: Nociones de OLE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- OLE, about OLE
ms.assetid: 5f654eb5-66b1-40c9-9215-bb85356a67f8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e40fb7d2e58fa672196853e1edb9d5577c2cb14a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ole-background"></a>Nociones de OLE
OLE es un mecanismo que permite a los usuarios crear y editar documentos que contengan elementos u "objetos" creado en distintas aplicaciones.  
  
> [!NOTE]
>  OLE era originalmente un acrónimo de objeto de vinculación e incrustación de objetos. Sin embargo, se está ahora sucesivo OLE. Partes de OLE no relacionadas con la vinculación e incrustación de objetos ahora forman parte de la tecnología activa.  
  
 OLE (documentos), que históricamente se denominaba documentos compuestos, integran fácilmente varios tipos de datos o componentes. Clips de sonido, hojas de cálculo y los mapas de bits son ejemplos típicos de componentes que se encuentran en OLE (documentos). En la aplicación es compatible con OLE permite a los usuarios usar OLE (documentos) sin preocuparse de cambiar entre las distintas aplicaciones; OLE hace el cambio automáticamente.  
  
 Usar una aplicación de contenedor para crear documentos compuestos y una aplicación de servidor o componente para crear los elementos dentro del documento contenedor. Cualquier aplicación que escriba puede ser un contenedor, un servidor o ambos.  
  
 OLE incorpora muchos conceptos diferentes que todo el trabajo hacia el objetivo de la interacción uniforme entre aplicaciones. Estas áreas son los siguientes:  
  
 Vincular e incrustar  
 Vincular e incrustar son los dos métodos para almacenar los elementos creados dentro de un documento OLE que se crearon en otra aplicación. Para obtener información general sobre las diferencias entre los dos, vea el artículo [fondo OLE: vincular e incrustar](../mfc/ole-background-linking-and-embedding.md). Para obtener más información, consulte los artículos [contenedores](../mfc/containers.md) y [servidores](../mfc/servers.md).  
  
 Activación en contexto (edición Visual)  
 Activación de un elemento incrustado en el contexto del documento contenedor se denomina activación en contexto o edición visual. Interfaz de la aplicación contenedora cambia para incorporar las características de la aplicación componente que creó el elemento incrustado. Los elementos vinculados nunca se activan en su lugar, porque los datos reales para el elemento se encuentran en un archivo independiente, fuera del contexto de la aplicación que contiene el vínculo. Para obtener más información acerca de la activación en contexto, vea el artículo [activación](../mfc/activation-cpp.md).  
  
> [!NOTE]
>  Vincular e incrustar y activación en contexto proporcionan las principales características de edición visual OLE.  
  
 automatización  
 La automatización permite a una aplicación controlar otra aplicación. La aplicación controladora se conoce como un cliente de automatización y la aplicación controlada se conoce como un servidor de automatización o componente de automatización. Para obtener más información acerca de la automatización, vea los artículos [los clientes de automatización](../mfc/automation-clients.md) y [servidores de automatización](../mfc/automation-servers.md).  
  
> [!NOTE]
>  Funcionamiento de la automatización en contextos de tecnología OLE y activo. Puede automatizar cualquier objeto basado en COM.  
  
 Archivos compuestos  
 Archivos compuestos proporcionan un formato de archivo estándar que simplifica el almacenamiento estructurado de documentos compuestos para aplicaciones OLE. Dentro de un archivo compuesto, almacenamientos tienen muchas características de directorios y las secuencias tienen muchas características de archivos. Esta tecnología también se denomina almacenamiento estructurado. Para obtener más información sobre los archivos compuestos, vea el artículo [contenedores: archivos compuestos](../mfc/containers-compound-files.md).  
  
 Transferencia de datos uniforme  
 Transferencia de datos uniforme (UDT) es un conjunto de interfaces que permitir que los datos enviados y recibidos de un modo estándar, independientemente del método real elegido para transferir los datos. Formularios UDT mediante que transfiere de la base de datos arrastrar y colocar. Ahora sirve como base para la transferencia de datos existente de Windows, como el Portapapeles y el intercambio dinámico de datos (DDE). Para obtener más información sobre UDT, vea el artículo [objetos de datos y orígenes de datos (OLE)](../mfc/data-objects-and-data-sources-ole.md).  
  
 Arrastrar y colocar  
 Arrastrar y colocar es una técnica de manipulación directa, fácil de utilizar para transferir datos entre aplicaciones, entre ventanas dentro de una aplicación, o incluso dentro de una sola ventana en una aplicación. La transferencia de datos a están seleccionados y arrastrar al destino deseado. Arrastrar y colocar se basa en la transferencia de datos uniforme. Para obtener más información acerca de arrastrar y colocar, vea el artículo [arrastrar y colocar](../mfc/drag-and-drop-ole.md).  
  
 Modelo de objetos componentes  
 El modelo de objetos componentes (COM) proporciona la infraestructura que se utiliza cuando los objetos OLE se comunican entre sí. Las clases OLE de MFC simplifican COM para el programador. COM forma parte de la tecnología Active, porque los objetos COM subyacen de la tecnología OLE y activo. Para obtener más información sobre COM, vea el [Active Template Library (ATL)](../atl/active-template-library-atl-concepts.md) temas.  
  
 En los siguientes artículos se tratan algunos de los temas más importantes de OLE:  
  
-   [Nociones de OLE: Vincular e incrustar](../mfc/ole-background-linking-and-embedding.md)  
  
-   [Nociones de OLE: Contenedores y servidores](../mfc/ole-background-containers-and-servers.md)  
  
-   [Nociones de OLE: Estrategias de implementación](../mfc/ole-background-implementation-strategies.md)  
  
-   [Nociones de OLE: Implementación de MFC](../mfc/ole-background-mfc-implementation.md)  
  
 Para ver información general sobre OLE que no se encuentra en los artículos anteriores, busque OLE en MSDN.  
  
## <a name="see-also"></a>Vea también  
 [OLE](../mfc/ole-in-mfc.md)

