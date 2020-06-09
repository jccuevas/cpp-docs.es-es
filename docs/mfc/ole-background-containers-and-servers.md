---
title: 'Nociones de OLE: Contenedores y servidores'
ms.date: 11/04/2016
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
ms.openlocfilehash: 7c3130ab9d8dff6551ef0ecbec43e5422dbdc4c4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617907"
---
# <a name="ole-background-containers-and-servers"></a>Nociones de OLE: Contenedores y servidores

Una aplicación contenedora es una aplicación que puede incorporar elementos incrustados o vinculados en sus propios documentos. Los documentos administrados por una aplicación contenedora deben ser capaces de almacenar y Mostrar componentes de documentos OLE, así como de los datos creados por la propia aplicación. Una aplicación contenedora también debe permitir que los usuarios inserten nuevos elementos o editen los elementos existentes activando las aplicaciones del servidor cuando sea necesario. Los requisitos de la interfaz de usuario de una aplicación de contenedor se muestran en el artículo [contenedores: problemas de la interfaz de usuario](containers-user-interface-issues.md).

Una aplicación de servidor o aplicación de componentes es una aplicación que puede crear componentes de documentos OLE para su uso por parte de aplicaciones de contenedor. Las aplicaciones de servidor suelen admitir la función de arrastrar y colocar o copiar sus datos en el portapapeles para que una aplicación contenedora pueda insertar los datos como un elemento incrustado o vinculado. Una aplicación puede ser tanto un contenedor como un servidor.

La mayoría de los servidores son aplicaciones independientes o servidores completos; pueden ejecutarse como aplicaciones independientes o pueden ser iniciadas por una aplicación contenedora. Un miniservidor es un tipo especial de aplicación de servidor que solo puede iniciar un contenedor. No se puede ejecutar como una aplicación independiente. Los servidores Microsoft Draw y Microsoft Graph son ejemplos de miniservers.

Los contenedores y los servidores no se comunican directamente. En su lugar, se comunican a través de las bibliotecas de vínculos dinámicos (DLL) del sistema OLE. Estos archivos dll proporcionan funciones a las que los contenedores y servidores llaman, y los contenedores y servidores proporcionan funciones de devolución de llamada a las que llaman los archivos dll.

Mediante el uso de este medio de comunicación, un contenedor no necesita conocer los detalles de implementación de la aplicación de servidor. Permite que un contenedor acepte elementos creados por cualquier servidor sin tener que definir los tipos de servidores con los que puede trabajar. Como resultado, el usuario de una aplicación contenedora puede aprovechar las ventajas de las aplicaciones y los formatos de datos futuros. Si estas nuevas aplicaciones son componentes OLE, un documento compuesto podrá incorporar elementos creados por esas aplicaciones.

## <a name="see-also"></a>Consulte también

[Nociones de OLE](ole-background.md)<br/>
[Nociones de OLE: Implementación de MFC](ole-background-mfc-implementation.md)<br/>
[Contenedores](containers.md)<br/>
[Servidores](servers.md)<br/>
[Contenedores: Elementos de cliente](containers-client-items.md)<br/>
[Servidores: Elementos de servidor](servers-server-items.md)
