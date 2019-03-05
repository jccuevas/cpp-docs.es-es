---
title: Servidores
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC]
- OLE server applications [MFC], activation
- full-server
- servers
- mini-server
- OLE server applications [MFC], server types
- server applications [MFC]
ms.assetid: e45172e8-eae3-400a-8139-0fa009a42fdc
ms.openlocfilehash: 7b1eb0df439bcfde3aa295f23a90291e865df3a9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290811"
---
# <a name="servers"></a>Servidores

Una aplicación de servidor (o el componente de aplicación) crea elementos OLE (o componentes) para su uso por aplicaciones de contenedor. Una aplicación de servidor de edición visual también admite la edición visual o la activación en contexto. Otra forma de servidor OLE es un [servidor de automatización](../mfc/automation-servers.md). Algunas aplicaciones de servidor sólo admiten la creación de elementos incrustados; otras admiten la creación de elementos vinculados e incrustados. Algunas sólo admiten la vinculación, aunque es poco frecuente. Todas las aplicaciones de servidor deben admitir la activación por las aplicaciones de contenedor cuando el usuario desea editar un elemento. Una aplicación puede ser un contenedor y un servidor. En otras palabras, puede incorporar datos en sus documentos tanto crear datos que puedan incorporarse como elementos en documentos de otras aplicaciones.

Un miniservidor es un tipo especial de aplicación de servidor que sólo se puede iniciar por un contenedor. Microsoft Draw y Microsoft Graph son ejemplos de miniservidores. Un miniservidor no almacenar documentos como archivos en disco. En su lugar, lee sus documentos y los escribe en elementos de documentos que pertenecen a los contenedores. Como resultado, un miniservidor admite sólo incrustación, no la vinculación.

Un servidor completo se puede ejecutar como una aplicación independiente o iniciar una aplicación contenedora. Un servidor completo puede almacenar documentos como archivos en disco. Sólo incrustación, ambos incrustación y vinculación, o bien vincular solo puede admitir. El usuario de una aplicación contenedora puede crear un elemento incrustado eligiendo el comando Cortar o copiar en el servidor y el comando Pegar en el contenedor. Se crea un elemento vinculado eligiendo el comando de copia en el servidor y el comando Pegar vínculo en el contenedor. Como alternativa, el usuario puede crear un elemento incrustado o vinculado mediante el cuadro de diálogo Insertar objeto.

En la tabla siguiente se resume las características de diferentes tipos de servidores:

### <a name="server-characteristics"></a>Características del servidor

|Tipo de servidor|Admite varias instancias|Elementos por documento|Documentos por instancia|
|--------------------|---------------------------------|------------------------|----------------------------|
|Miniservidor|Sí|1|1|
|Servidor completo SDI|Sí|1 (si se admite la vinculación, 1 o más)|1|
|Servidor completo MDI|No (no es necesario)|1 (si se admite la vinculación, 1 o más)|0 o más|

Una aplicación de servidor debe admitir varios contenedores al mismo tiempo, en caso de que se usará más de un contenedor para editar un elemento incrustado o vinculado. Si el servidor es una aplicación SDI (o un miniservidor con una interfaz de cuadro de diálogo), varias instancias del servidor deben ser capaz de ejecutar al mismo tiempo. Esto permite que una instancia independiente de la aplicación para controlar cada solicitud de contenedor.

Si el servidor es una aplicación MDI, puede crear una nueva ventana secundaria MDI cada vez que necesita un contenedor para editar un elemento. De esta manera, una sola instancia de la aplicación puede admitir varios contenedores.

La aplicación de servidor debe indicar la DLL del sistema OLE qué hacer si ya se está ejecutando una instancia del servidor cuando otro contenedor solicita sus servicios: si se debe iniciar una nueva instancia del servidor o dirigir las solicitudes de todos los contenedores a una instancia de la servidor.

Para obtener más información sobre los servidores, consulte:

- [servidores: Implementación de un servidor](../mfc/servers-implementing-a-server.md)

- [servidores: Implementar documentos de servidor](../mfc/servers-implementing-server-documents.md)

- [servidores: Implementación de Windows de marco en contexto](../mfc/servers-implementing-in-place-frame-windows.md)

- [servidores: Elementos del servidor](../mfc/servers-server-items.md)

- [servidores: Problemas de la interfaz de usuario](../mfc/servers-user-interface-issues.md)

## <a name="see-also"></a>Vea también

[OLE](../mfc/ole-in-mfc.md)<br/>
[Contenedores](../mfc/containers.md)<br/>
[Contenedores: Características avanzadas](../mfc/containers-advanced-features.md)<br/>
[Menús y recursos (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Registro](../mfc/registration.md)<br/>
[Servidores de automatización](../mfc/automation-servers.md)
