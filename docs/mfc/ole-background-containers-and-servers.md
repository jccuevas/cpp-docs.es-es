---
title: 'Nociones de OLE: Contenedores y servidores | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE full-server applications [MFC]
- server applications [MFC], communication with containers
- full-server [MFC]
- server applications [MFC], requirements
- server applications [MFC], defined
- OLE server applications [MFC], about server applications
- server applications [MFC], full-server vs. mini-server
- OLE server applications [MFC], mini-server applications
- OLE containers [MFC], container applications
- containers [MFC], OLE container applications
- server applications [MFC]
ms.assetid: dafbb31d-096c-4654-b774-12900d832919
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9f15ef532ba61a089f8adec9ed20f737c07eae2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="ole-background-containers-and-servers"></a>Nociones de OLE: Contenedores y servidores
Una aplicación de contenedor es una aplicación que puede incorporar elementos incrustados o vinculados en sus propios documentos. Los documentos administrados por una aplicación de contenedor deben ser capaz de almacenar y mostrar los componentes de documentos OLE, así como los datos creados por la propia aplicación. Una aplicación de contenedor también debe permitir a los usuarios insertar nuevos elementos o editar elementos existentes mediante la activación de aplicaciones de servidor cuando sea necesario. Los requisitos de la interfaz de usuario de una aplicación de contenedor se enumeran en el artículo [contenedores: problemas de la interfaz de usuario](../mfc/containers-user-interface-issues.md).  
  
 Una aplicación de servidor o componente es una aplicación que puede crear componentes de documentos OLE para su uso por aplicaciones de contenedor. Las aplicaciones de servidor suelen permitir arrastrar y colocar o copiar sus datos en el Portapapeles para que una aplicación de contenedor puede insertar los datos como un elemento incrustado o vinculado. Una aplicación puede ser un contenedor y un servidor.  
  
 Mayoría de los servidores es aplicaciones independientes o servidores completos; se pueden ejecutar como aplicaciones independientes o se pueden iniciar una aplicación de contenedor. Un miniservidor es un tipo especial de aplicación de servidor que puede iniciar un contenedor. Ésta no se ejecutará como una aplicación independiente. Servidores Microsoft Draw y Microsoft Graph son ejemplos de miniservidores.  
  
 Contenedores y servidores no se comunican directamente. En su lugar, se comunican a través de las bibliotecas de vínculos dinámicos (DLL) del sistema OLE. Estas DLL proporcionan funciones que llaman contenedores y servidores, y los contenedores y servidores proporcionan funciones de devolución de llamada que llaman los archivos DLL.  
  
 Un contenedor con este medio de comunicación, no necesita conocer los detalles de implementación de la aplicación de servidor. Permite a un contenedor aceptar elementos creados por cualquier servidor sin tener que definir los tipos de servidores con los que puede trabajar. Como resultado, el usuario de una aplicación de contenedor puede sacar partido de las aplicaciones futuras y formatos de datos. Si estas nuevas aplicaciones son componentes OLE, un documento compuesto podrá incorporar elementos creados por dichas aplicaciones.  
  
## <a name="see-also"></a>Vea también  
 [Nociones de OLE](../mfc/ole-background.md)   
 [Nociones OLE: Implementación de MFC](../mfc/ole-background-mfc-implementation.md)   
 [Contenedores](../mfc/containers.md)   
 [Servidores](../mfc/servers.md)   
 [Contenedores: Elementos de cliente](../mfc/containers-client-items.md)   
 [Servidores: Elementos de servidor](../mfc/servers-server-items.md)

