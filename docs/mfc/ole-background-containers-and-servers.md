---
title: "Nociones de OLE: Contenedores y servidores | Microsoft Docs"
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
  - "contenedores, aplicaciones de contenedor OLE"
  - "servidor completo"
  - "contenedores OLE, aplicaciones de contenedor"
  - "aplicaciones de servidor completo OLE"
  - "aplicaciones de servidor OLE, acerca de aplicaciones de servidor"
  - "aplicaciones de servidor OLE, aplicaciones de miniservidor"
  - "aplicaciones de servidor"
  - "aplicaciones de servidor, comunicación con contenedores"
  - "aplicaciones de servidor, definición"
  - "aplicaciones de servidor, servidor completo frente a miniservidor"
  - "aplicaciones de servidor, requisitos"
ms.assetid: dafbb31d-096c-4654-b774-12900d832919
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Nociones de OLE: Contenedores y servidores
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una aplicación contenedora es una aplicación que puede escribir incrustado o elementos vinculados en solitario documentan.  Los documentos administrados por una aplicación contenedora deben poder almacenar y mostrar los componentes de OLE de documento así como datos creados por la propia aplicación.  Una aplicación contenedora también debe permitir que los usuarios inserten nuevos elementos o elementos existentes de edición por aplicaciones de servidor que provocan cuando sea necesario.  Los requisitos de la interfaz de usuario de una aplicación contenedora se enumeran en el caso [Contenedores: Problemas de la interfaz de usuario](../mfc/containers-user-interface-issues.md).  
  
 Una aplicación de servidor o una aplicación de componente es una aplicación que puede crear componentes de OLE del documento para uso de aplicaciones contenedoras.  Las aplicaciones de servidor admiten normalmente arrastrar y colocar o copiar los datos en el portapapeles de manera que una aplicación contenedora puede insertar los datos como elemento incrustado o vinculado.  Una aplicación puede ser un contenedor y servidor.  
  
 La mayoría de los servidores son aplicaciones independientes o servidores completos; pueden ejecutarse como aplicaciones independientes o pueden ser que por una aplicación contenedora.  Un miniserver es un tipo especial de aplicación de servidor que puede ser iniciará únicamente por un contenedor.  No se puede ejecutar como una aplicación independiente.  Servidores Microsoft Draw y Microsoft gráficos son ejemplos de miniservers.  
  
 Los contenedores y los servidores no se comunican directamente.  En su lugar, se comunican a través de las bibliotecas de vínculos dinámicos VIEJAS \(DLL\) del sistema.  Estos archivos DLL proporcionan las funciones contenedores y la llamada de servidores, y los contenedores y los servidores proporcionan funciones de devolución de llamada que los archivos DLL llaman.  
  
 Mediante este significa de comunicación, un contenedor no necesita conocer los detalles de implementación de la aplicación de servidor.  Permite que un contenedor acepte los elementos creados por cualquier servidor sin tener que definir los tipos de servidores con los que pueda trabajar.  Como resultado, el usuario de una aplicación contenedora puede aprovechar las aplicaciones y los formatos de datos futuros.  Si estas nuevas aplicaciones son componentes de OLE, un documento compuesto podrá escribir los elementos creados por dichas aplicaciones.  
  
## Vea también  
 [Nociones de OLE](../mfc/ole-background.md)   
 [Nociones de OLE: Implementación de MFC](../mfc/ole-background-mfc-implementation.md)   
 [Contenedores](../mfc/containers.md)   
 [Servidores](../mfc/servers.md)   
 [Contenedores: Elementos de cliente](../mfc/containers-client-items.md)   
 [Servidores: Elementos de servidor](../mfc/servers-server-items.md)