---
title: "Servidores | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "servidor completo"
  - "miniservidor"
  - "aplicaciones de servidor OLE"
  - "aplicaciones de servidor OLE, activación"
  - "aplicaciones de servidor OLE, tipos de servidor"
  - "aplicaciones de servidor"
  - "servidores"
ms.assetid: e45172e8-eae3-400a-8139-0fa009a42fdc
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Servidores
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una aplicación de servidor \(o la aplicación componente\) crea elementos de OLE \(o componentes\) para uso de aplicaciones contenedoras.  Una aplicación de servidor de edición visual también admite la edición o activación in situ visual.  Otra forma de servidor OLE es [servidor de automatización](../mfc/automation-servers.md).  Algunas aplicaciones de servidor sólo admiten la creación de elementos incrustados; otros admiten la creación de elementos insertados y vinculados.  Algunos admiten vincular sólo, aunque este es poco frecuente.  Todas las aplicaciones de servidor deben admitir la activación por aplicaciones contenedoras cuando el usuario desea editar un elemento.  Una aplicación puede ser un contenedor y servidor.  Es decir puede escribir datos en documentos, y crea los datos que se pueden especificar como elementos en los documentos de otras aplicaciones.  
  
 Un miniserver es un tipo especial de aplicación de servidor que puede ser iniciará únicamente por un contenedor.  Microsoft Draw y Microsoft gráficos son ejemplos de miniservers.  Un miniserver no almacena documentos como archivos en el disco.  En su lugar, lee los documentos de y los escribe en los elementos de los documentos que pertenecen a los contenedores.  Como resultado, un miniserver admite insertar sólo, no vinculando.  
  
 Un servidor completo se puede ejecutar como una aplicación independiente o se iniciará mediante una aplicación contenedora.  Un servidor completo puede almacenar documentos como archivos en el disco.  Puede admitir integrar sólo, integrando y vincular, o vincular únicamente.  El usuario de una aplicación contenedora puede crear un elemento incrustado eligiendo el comando cortar o de copia en el servidor y el comando pegar en el contenedor.  Un elemento vinculado se crea al elegir el comando de copia en el servidor y el comando de pegar vínculos en el contenedor.  Alternativamente, puede crear un elemento incrustado o vinculado mediante el cuadro de diálogo de objeto INSERT.  
  
 La tabla siguiente se resumen las características de diferentes tipos de servidores:  
  
### Características de Servidor  
  
|Tipo de servidor|Admite varias instancias|Elementos por el documento|Documentos por la instancia|  
|----------------------|------------------------------|--------------------------------|---------------------------------|  
|Miniserver|Sí|1|1|  
|Servidor completo SDI|Sí|1 \(si se admite la vinculación, 1 o más\)|1|  
|Servidor completo de MDI|No \(no necesario\)|1 \(si se admite la vinculación, 1 o más\)|0 o más|  
  
 Una aplicación de servidor debe admitir los contenedores simultáneamente, en caso que más de un contenedor se usará para editar un elemento incrustado o vinculado.  Si el servidor es una aplicación SDI \(o un miniserver con una interfaz del cuadro de diálogo\), varias instancias del servidor deben poder ejecutarse simultáneamente.  Esto permite una instancia independiente de la aplicación para tratar cada solicitud de contenedor.  
  
 Si el servidor es una aplicación MDI, puede crear una ventana MDI secundaria cada vez que un contenedor necesita modificar un elemento.  De esta manera, una única instancia de la aplicación puede admitir los contenedores.  
  
 La aplicación de servidor debe indicar a archivos DLL del sistema OLE qué hacer si una instancia del servidor está ejecutando cuando otro contenedor ordena sus servicios: si debe iniciar una nueva instancia del servidor o dirigir las solicitudes de todos los contenedores a una instancia del servidor.  
  
 Para obtener más detalles sobre los servidores, vea:  
  
-   [Servidores: implementar un servidor](../mfc/servers-implementing-a-server.md)  
  
-   [Servidores: Implementar documentos de Servidor](../mfc/servers-implementing-server-documents.md)  
  
-   [Servidores: Implementar el cuadro en contexto Windows](../mfc/servers-implementing-in-place-frame-windows.md)  
  
-   [Servidores: Elementos de Servidor](../mfc/servers-server-items.md)  
  
-   [Servidores: Problemas de la interfaz de usuario](../mfc/servers-user-interface-issues.md)  
  
## Vea también  
 [OLE](../mfc/ole-in-mfc.md)   
 [Contenedores](../mfc/containers.md)   
 [Contenedores: Características avanzadas](../mfc/containers-advanced-features.md)   
 [Menús y recursos \(OLE\)](../mfc/menus-and-resources-ole.md)   
 [Registro](../mfc/registration.md)   
 [Servidores de automatización](../mfc/automation-servers.md)