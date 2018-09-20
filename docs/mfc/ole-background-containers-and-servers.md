---
title: 'Nociones de OLE: Contenedores y servidores | Microsoft Docs'
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
ms.openlocfilehash: 23aa5e4c13e8049a2240462dab1c5b68bfb514f7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436941"
---
# <a name="ole-background-containers-and-servers"></a>Nociones de OLE: Contenedores y servidores

Una aplicación de contenedor es una aplicación que puede incorporar elementos incrustados o vinculados a sus propios documentos. Los documentos administrados por una aplicación de contenedor deben ser capaz de almacenar y mostrar los componentes de documentos OLE, así como los datos creados por la propia aplicación. Una aplicación contenedora también debe permitir a los usuarios insertar nuevos elementos o editar elementos existentes mediante la activación de aplicaciones de servidor cuando sea necesario. Se enumeran los requisitos de la interfaz de usuario de una aplicación contenedora en el artículo [contenedores: problemas de la interfaz de usuario](../mfc/containers-user-interface-issues.md).

Una aplicación de servidor o el componente de aplicación es una aplicación que puede crear componentes de documentos OLE para su uso por aplicaciones de contenedor. Las aplicaciones de servidor suelen permitir arrastrar y colocar o copiar sus datos en el Portapapeles para que una aplicación contenedora puede insertar los datos como un elemento incrustado o vinculado. Una aplicación puede ser un contenedor y un servidor.

Mayoría de los servidores es aplicaciones independientes o servidores completos; se pueden ejecutar como aplicaciones independientes o se puede iniciar una aplicación contenedora. Un miniservidor es un tipo especial de aplicación de servidor que puede iniciar un contenedor. No se puede ejecutar como una aplicación independiente. Servidores Microsoft Draw y Microsoft Graph son ejemplos de miniservidores.

Contenedores y servidores no se comunican directamente. En su lugar, se comunican a través de las bibliotecas de vínculos dinámicos del sistema OLE (DLL). Estos archivos DLL proporcionan funciones que llaman contenedores y servidores y los contenedores y servidores proporcionan funciones de devolución de llamada que llaman los archivos DLL.

Un contenedor con este medio de comunicación, no es necesario conocer los detalles de implementación de la aplicación de servidor. Permite a un contenedor Aceptar los elementos creados por cualquier servidor sin tener que definir los tipos de servidores con el que puede funcionar. Como resultado, el usuario de una aplicación contenedora puede aprovechar las ventajas de las aplicaciones futuras y formatos de datos. Si estas nuevas aplicaciones son componentes OLE, un documento compuesto podrá incorporar elementos creados por esas aplicaciones.

## <a name="see-also"></a>Vea también

[Nociones de OLE](../mfc/ole-background.md)<br/>
[Nociones de OLE: Implementación de MFC](../mfc/ole-background-mfc-implementation.md)<br/>
[Contenedores](../mfc/containers.md)<br/>
[Servidores](../mfc/servers.md)<br/>
[Contenedores: Elementos de cliente](../mfc/containers-client-items.md)<br/>
[Servidores: Elementos de servidor](../mfc/servers-server-items.md)

