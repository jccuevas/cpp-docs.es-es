---
title: 'Contenedores: Características avanzadas'
ms.date: 11/04/2016
helpviewer_keywords:
- links [MFC], to embedded OLE objects
- containers [MFC], links to embedded OLE objects
- containers [MFC], advanced features
- container/server applications [MFC]
- embedded objects [MFC]
- OLE controls [MFC], containers
- OLE containers [MFC], advanced features
- server/container applications [MFC]
- containers [MFC], container applications
ms.assetid: 221fd99c-b138-40fa-ad6a-974e3b3ad1f8
ms.openlocfilehash: cf130bf8dead5c59548821658b979785c4d54726
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376495"
---
# <a name="containers-advanced-features"></a>Contenedores: Características avanzadas

En este artículo se describen los pasos necesarios para incorporar características avanzadas opcionales en las aplicaciones de contenedor existentes. Estas características son:

- [Una aplicación que es a la vez un contenedor y un servidor](#_core_creating_a_container_server_application)

- [Un vínculo OLE a un objeto incrustado](#_core_links_to_embedded_objects)

## <a name="creating-a-containerserver-application"></a><a name="_core_creating_a_container_server_application"></a>Creación de una aplicación de contenedor/servidor

Una aplicación contenedora/servidor es una aplicación que actúa como contenedor y como servidor. Microsoft Word para Windows es un ejemplo de esto. Puede incrustar documentos de Word para Windows en otras aplicaciones y también puede incrustar elementos en documentos de Word para Windows. El proceso para modificar la aplicación contenedora para que sea un contenedor y un servidor completo (no se puede crear una aplicación de contenedor/miniservidor de combinación) es similar al proceso para crear un servidor completo.

En el artículo [Servidores: implementar un servidor](../mfc/servers-implementing-a-server.md) se enumeran una serie de tareas necesarias para implementar una aplicación de servidor. Si convierte una aplicación contenedora en una aplicación contenedora o de servidor, debe realizar algunas de esas mismas tareas, agregando código al contenedor. A continuación se enumeran las cosas importantes a tener en cuenta:

- El código contenedor creado por el asistente para aplicaciones ya inicializa el subsistema OLE. No tendrá que cambiar ni agregar nada para ese soporte.

- Dondequiera que esté `COleDocument`la clase base de `COleServerDoc`una clase de documento, cambie la clase base a .

- Reemplazar `COleClientItem::CanActivate` para evitar la edición de elementos en su lugar mientras el propio servidor se utiliza para editar en su lugar.

   Por ejemplo, el ejemplo OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md) ha incrustado un elemento creado por la aplicación contenedor/servidor. Abra la aplicación OCLIENT y edite in situ el elemento creado por la aplicación contenedor/servidor. Al editar el elemento de la aplicación, decide que desea incrustar un elemento creado por el ejemplo OLE de MFC [HIERSVR](../overview/visual-cpp-samples.md). Para ello, no puede utilizar la activación in situ. Debe abrir completamente HIERSVR para activar este elemento. Dado que la biblioteca Microsoft Foundation Class no `COleClientItem::CanActivate` admite esta característica OLE, la invalidación le permite comprobar esta situación y evitar un posible error en tiempo de ejecución en la aplicación.

Si va a crear una nueva aplicación y desea que funcione como una aplicación contenedora/servidor, elija esa opción en el cuadro de diálogo Opciones OLE del asistente para aplicaciones y esta compatibilidad se creará automáticamente. Para obtener más información, consulte el artículo [Información general: Creación de un contenedor](../mfc/reference/creating-an-mfc-activex-control-container.md)de controles ActiveX . Para obtener información acerca de los ejemplos de MFC, vea [Ejemplos de MFC](../overview/visual-cpp-samples.md#mfc-samples).

Tenga en cuenta que no puede insertar una aplicación MDI en sí misma. Una aplicación que es un contenedor/servidor no se puede insertar en sí misma a menos que sea una aplicación SDI.

## <a name="links-to-embedded-objects"></a><a name="_core_links_to_embedded_objects"></a>Vínculos a objetos incrustados

La característica Vínculos a objetos incrustados permite a un usuario crear un documento con un vínculo OLE a un objeto incrustado dentro de la aplicación contenedora. Por ejemplo, cree un documento en un procesador de textos que contenga una hoja de cálculo incrustada. Si la aplicación admite vínculos a objetos incrustados, podría pegar un vínculo a la hoja de cálculo contenida en el documento del procesador de texto. Esta característica permite a la aplicación utilizar la información contenida en la hoja de cálculo sin saber dónde la obtuvo originalmente el procesador de textos.

#### <a name="to-link-to-embedded-objects-in-your-application"></a>Para vincular a objetos incrustados en la aplicación

1. Derive la clase `COleLinkingDoc` de `COleDocument`documento en lugar de .

1. Cree un identificador de clase OLE (**CLSID**) para la aplicación mediante el generador de identificador de clase incluido con las herramientas de desarrollo OLE.

1. Registre la aplicación con OLE.

1. Cree `COleTemplateServer` un objeto como miembro de la clase de aplicación.

1. En la función `InitInstance` miembro de la clase de aplicación, haga lo siguiente:

   - Conecte `COleTemplateServer` el objeto a las plantillas de `ConnectTemplate` documento llamando a la función miembro del objeto.

   - Llame `COleTemplateServer::RegisterAll` a la función miembro para registrar todos los objetos de clase con el sistema OLE.

   - Llame a `COleTemplateServer::UpdateRegistry`. El único `UpdateRegistry` parámetro que debe *ser OAT_CONTAINER* si la aplicación no se inicia con el modificador "/Embedded". Esto registra la aplicación como un contenedor que puede admitir vínculos a objetos incrustados.

      Si la aplicación se inicia con el modificador "/Embedded", no debe mostrar su ventana principal, similar a una aplicación de servidor.

El ejemplo OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md) implementa esta característica. Para obtener un ejemplo de cómo `InitInstance` se hace esto, vea la función en el *OCLIENT. CPP* de esta aplicación de ejemplo.

## <a name="see-also"></a>Consulte también

[Contenedores](../mfc/containers.md)<br/>
[Servidores](../mfc/servers.md)
