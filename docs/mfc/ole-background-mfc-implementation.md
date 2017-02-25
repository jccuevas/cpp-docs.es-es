---
title: "Nociones de OLE: Implementaci&#243;n de MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IMarshall"
  - "IMoniker"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IMarshall (clase)"
  - "IMoniker (interfaz), MFC"
  - "MFC (bibliotecas), implementar"
  - "OLE IMarshal (interfaz)"
  - "OLE IMoniker (interfaz)"
  - "IUnknown en OLE"
  - "implementación de biblioteca MFC OLE"
  - "OLE, archivos compuestos"
ms.assetid: 2b67016a-d78e-4d60-925f-c28ec8fb6180
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Nociones de OLE: Implementaci&#243;n de MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Debido al tamaño y la complejidad de API OLE sin formato, llamar directamente para escribir aplicaciones OLE puede ser largo.  El objetivo de la implementación de la biblioteca Microsoft Foundation Class OLE es reducir la cantidad de trabajo que tiene que hacer para escribir aplicaciones totalmente instrumentadas, OLE\- capaces.  
  
 En este artículo se explica las partes OLE API que no han sido MFC interior implementado.  La explicación también explica cómo lo asigna implementados a la sección OLE de [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
##  <a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a> Partes de OLE No implementadas por la biblioteca de clases  
 Algunas interfaces y características de OLE no proporciona directamente por MFC.  Si desea usar estas características, puede llamar a OLE API directamente.  
  
 Interfaz de IMoniker  
 La interfaz de `IMoniker` es implementada por la biblioteca de clases \(por ejemplo, la clase de `COleServerItem` \) pero no se ha expuesto anteriormente el programador.  Para obtener más información sobre esta interfaz, vea las implementaciones VIEJAS el moniker en la sección OLE de [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  Sin embargo, vea también la clase [CMonikerFile](../mfc/reference/cmonikerfile-class.md) y [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md).  
  
 IUnknown e interfaces de IMarshal  
 La interfaz de **IUnknown** es implementada por la biblioteca de clases pero no expuesta al programador.  La interfaz de **IMarshal** no es implementada por la biblioteca de clases pero se utiliza internamente.  Los servidores de automatización compilados mediante la biblioteca de clases ya tienen capacidades de cálculo de referencias integradas.  
  
 Docfiles \(archivos compuestos\)  
 Archivos compuestos se admiten parcialmente por la biblioteca de clases.  No se admite ninguna de las funciones que manipulan directamente los archivos compuestos más allá de creación.  MFC usa la clase **COleFileStream** para admitir la manipulación de secuencias con funciones de archivo estándar.  Para obtener más información, vea el artículo [Contenedores: Archivos compuestos](../mfc/containers-compound-files.md).  
  
 Servidores en proceso y controladores de objetos  
 Los servidores en proceso y controladores de objetos permiten la implementación de los datos de edición visual u objetos completos de \(COM\) del modelo de objetos componentes en una biblioteca de vínculos dinámicos \(DLL\).  Para ello, puede implementar un archivo DLL llamando a la API OLE directamente.  Sin embargo, si está escribiendo en un servidor de automatización y el servidor no tiene interfaz de usuario, puede utilizar AppWizard para crear el servidor en un servidor en proceso y para colocarlo dentro de un archivo DLL.  Para obtener más información sobre estos temas, vea [Servidores de automatización](../mfc/automation-servers.md).  
  
> [!TIP]
>  La manera más fácil de implementar en un servidor de automatización es colocarlo en una DLL.  MFC admite este enfoque.  
  
 Para obtener más información sobre cómo las clases VIEJAS de windows presentation foundation Microsoft implementan interfaces VIEJAS, vea las notas técnicas [38](../mfc/tn038-mfc-ole-iunknown-implementation.md), [39](../mfc/tn039-mfc-ole-automation-implementation.md), y [40](../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md)MFC.  
  
## Vea también  
 [Nociones de OLE](../mfc/ole-background.md)   
 [Nociones de OLE: Estrategias de implementación](../mfc/ole-background-implementation-strategies.md)