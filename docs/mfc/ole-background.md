---
title: "Nociones de OLE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE, acerca de OLE"
ms.assetid: 5f654eb5-66b1-40c9-9215-bb85356a67f8
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Nociones de OLE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

OLE es un mecanismo que permite a los usuarios crear y que editen los documentos que contienen los elementos o “objetos” creados por varias aplicaciones.  
  
> [!NOTE]
>  OLE era originalmente acrónimo del objeto al vincular y al incrustar.  Sin embargo, ahora se denomina OLE.  Las partes de OLE no relacionadas con vinculación y insertar ahora forman parte de tecnología activa.  
  
 Los documentos de OLE, históricamente denominados documentos compuestos, sin problemas integran distintos tipos de datos, o componentes.  Las secuencias de sonido, hojas de cálculo, y los mapas de bits son ejemplos comunes de los componentes incluidos en documentos de OLE.  Admitir OLE en la aplicación permite a los usuarios utilizar documentos de OLE sin preocuparse de conmutación entre las diferentes aplicaciones; OLE hace conmutación automáticamente.  
  
 Utiliza una aplicación contenedora para crear documentos compuestos y una aplicación de servidor o una aplicación de componente para crear elementos dentro del documento contenedor.  Cualquier aplicación que se escriba puede ser un contenedor, servidor, o ambos.  
  
 OLE incorpora varios conceptos que todo el trabajo hacia el objetivo de interacción sin problemas entre aplicaciones.  Estas áreas incluyen:  
  
 Vinculación y la inserción  
 Vinculación y la inserción son los dos métodos para almacenar los elementos creados en un documento OLE que se crearon en otra aplicación.  Para obtener información general sobre las diferencias entre los dos, vea el artículo [Información general de OLE: Vinculación y la inserción](../mfc/ole-background-linking-and-embedding.md).  Para obtener información detallada, vea los artículos [Contenedores](../mfc/containers.md) y [servidores](../mfc/servers.md).  
  
 Activación de contexto \(edición visual\)  
 Provocando un elemento incrustado en el contexto del documento contenedor se denomina activación en contexto o edición visual.  Los cambios en la interfaz de la aplicación contenedora para escribir las características de aplicación componente que creó el elemento incrustado.  Los elementos vinculados nunca se provocan en el lugar porque los datos real del elemento se incluye en un archivo independiente, fuera del contexto de la aplicación que contiene el vínculo.  Para obtener más información sobre la activación en contexto, vea el artículo [Activación](../mfc/activation-cpp.md).  
  
> [!NOTE]
>  Vinculación y la inserción y activación en contexto proporcionan las características principales de edición visual de activex.  
  
 Automatización  
 La automatización permite una aplicación para controlar otra aplicación.  La aplicación de control se conoce como cliente de automatización, y la aplicación que está controlada se conoce como un servidor de automatización o componente de automatización.  Para obtener más información sobre la automatización, vea los artículos [Clientes de automatización](../mfc/automation-clients.md) y [Servidores de automatización](../mfc/automation-servers.md).  
  
> [!NOTE]
>  Automatización funciona en contextos de OLE y activo de la tecnología.  Puede automatizar cualquier objeto basado en COM.  
  
 Archivos compuestos  
 Los archivos compuestos proporcionan un formato de archivo estándar que simplifica el almacenamiento estructurado de documentos compuestos para aplicaciones OLE.  Dentro de un archivo compuesto, los almacenes tienen muchas características de directorios y secuencias tienen muchas características de archivos.  Esta tecnología también se denomina almacenamiento estructurado.  Para obtener más información sobre los archivos compuestos, vea el artículo [Contenedores: Archivos compuestos](../mfc/containers-compound-files.md).  
  
 Transferencia de datos uniforme  
 La Transferencia de datos uniforme \(UDT\) es un conjunto de interfaces que permiten recibens los datos son enviados y en un modo estándar, independientemente del método real elegido para transferir los datos.  El UDT forma la base para las transferencias de datos mediante arrastrar y colocar.  El UDT ahora actúa como base para la transferencia de datos de Windows, como el portapapeles y \(DDE\) de intercambio de datos dinámicos.  Para obtener más información sobre UDT, vea el artículo [Objetos de datos y orígenes de datos \(OLE\)](../mfc/data-objects-and-data-sources-ole.md).  
  
 Arrastrar y colocar  
 La operación de arrastrar y colocar es una técnica descriptivo, de la directo\- manipulación de transferir datos entre aplicaciones, entre ventanas dentro de una aplicación, o incluso dentro de una sola ventana en una aplicación.  Los datos que se transferirá está activada y se arrastra el destino deseado.  La operación de arrastrar y colocar se basa en la transferencia de datos uniforme.  Para obtener más información sobre arrastrar y colocar, vea el artículo [Arrastrar y colocar](../mfc/drag-and-drop-ole.md).  
  
 Modelo de objetos componentes  
 El modelo de objetos componentes \(COM\) proporciona la infraestructura utilizada cuando los objetos OLE se comunican entre sí.  Las clases VIEJAS MFC simplifican COM para el programador.  COM es parte de tecnología activa, porque los objetos COM son la base de tecnología OLE y activo.  Para obtener más información sobre COM, vea los temas de [Active Template Library \(ATL\)](../atl/active-template-library-atl-concepts.md) .  
  
 Algunos de los temas de OLE más importantes se cubren en los casos siguientes:  
  
-   [Información general de OLE: Vinculación y la inserción](../mfc/ole-background-linking-and-embedding.md)  
  
-   [Información general de OLE: Contenedores y Servidores](../mfc/ole-background-containers-and-servers.md)  
  
-   [Información general de OLE: Estrategias de implementación](../mfc/ole-background-implementation-strategies.md)  
  
-   [Información general de OLE: Implementación de MFC](../mfc/ole-background-mfc-implementation.md)  
  
 Para obtener información OLE de general no encontrada en los casos anteriores, busque OLE en MSDN.  
  
## Vea también  
 [OLE](../mfc/ole-in-mfc.md)