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
ms.openlocfilehash: 1ef4ed9865d3a88a6ff85f777984b856d03cc48e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616358"
---
# <a name="containers-advanced-features"></a>Contenedores: Características avanzadas

En este artículo se describen los pasos necesarios para incorporar características avanzadas opcionales en aplicaciones de contenedor existentes. Estas características son:

- [Una aplicación que sea un contenedor y un servidor](#_core_creating_a_container_server_application)

- [Vínculo OLE a un objeto incrustado](#_core_links_to_embedded_objects)

## <a name="creating-a-containerserver-application"></a><a name="_core_creating_a_container_server_application"></a>Creación de una aplicación de contenedor/servidor

Una aplicación de contenedor/servidor es una aplicación que actúa como un contenedor y un servidor. Microsoft Word para Windows es un ejemplo de esto. Puede incrustar documentos de Word para Windows en otras aplicaciones y también puede incrustar elementos en documentos de Word para Windows. El proceso para modificar la aplicación contenedora para que sea un contenedor y un servidor completo (no se puede crear una aplicación de contenedor/miniservidor) es similar al proceso para crear un servidor completo.

En el artículo [servidores: implementar un servidor](servers-implementing-a-server.md) se enumeran varias tareas necesarias para implementar una aplicación de servidor. Si convierte una aplicación contenedora en una aplicación de contenedor/servidor, deberá realizar algunas de esas mismas tareas, agregando código al contenedor. A continuación se enumeran los aspectos importantes que se deben tener en cuenta:

- El código de contenedor creado por el Asistente para aplicaciones ya inicializa el subsistema OLE. No tendrá que cambiar ni agregar nada para ese soporte.

- Siempre que la clase base de una clase de documento sea `COleDocument` , cambie la clase base a `COleServerDoc` .

- Invalide `COleClientItem::CanActivate` para evitar la edición de elementos en su lugar mientras se usa el propio servidor para realizar la edición en contexto.

   Por ejemplo, el [OCLIENT](../overview/visual-cpp-samples.md) de ejemplo OLE de MFC ha incrustado un elemento creado por la aplicación de contenedor/servidor. Abra la aplicación OCLIENT y edite en contexto el elemento creado por la aplicación de contenedor/servidor. Mientras edita el elemento de la aplicación, decide que desea incrustar un elemento creado por el ejemplo de OLE de MFC [HIERSVR](../overview/visual-cpp-samples.md). Para ello, no puede usar la activación en contexto. Debe abrir por completo HIERSVR para activar este elemento. Dado que el biblioteca MFC no es compatible con esta característica OLE, el reemplazo `COleClientItem::CanActivate` le permite comprobar esta situación y evitar un posible error en tiempo de ejecución en la aplicación.

Si va a crear una nueva aplicación y desea que funcione como una aplicación contenedor/servidor, elija esa opción en el cuadro de diálogo Opciones OLE del Asistente para aplicaciones y esta compatibilidad se creará automáticamente. Para obtener más información, vea el artículo [información general: crear un contenedor de controles ActiveX](reference/creating-an-mfc-activex-control-container.md). Para obtener información acerca de los ejemplos de MFC, vea [ejemplos de MFC](../overview/visual-cpp-samples.md#mfc-samples).

Tenga en cuenta que no puede insertar una aplicación MDI en sí misma. Una aplicación que es un contenedor o servidor no se puede insertar en sí misma a menos que sea una aplicación SDI.

## <a name="links-to-embedded-objects"></a><a name="_core_links_to_embedded_objects"></a>Vínculos a objetos incrustados

La característica vínculos a objetos incrustados permite al usuario crear un documento con un vínculo OLE a un objeto incrustado dentro de la aplicación contenedora. Por ejemplo, cree un documento en un procesador de textos que contenga una hoja de cálculo incrustada. Si la aplicación admite vínculos a objetos incrustados, podría pegar un vínculo a la hoja de cálculo incluida en el documento del procesador de textos. Esta característica permite a la aplicación usar la información contenida en la hoja de cálculo sin saber dónde la obtuvo originalmente el procesador de textos.

#### <a name="to-link-to-embedded-objects-in-your-application"></a>Para vincular a los objetos incrustados en la aplicación

1. Derive la clase de documento de en `COleLinkingDoc` lugar de `COleDocument` .

1. Cree un identificador de clase OLE (**CLSID**) para la aplicación mediante el generador de ID. de clase incluido con las herramientas de desarrollo de OLE.

1. Registre la aplicación con OLE.

1. Cree un `COleTemplateServer` objeto como miembro de la clase de la aplicación.

1. En la función miembro de la clase de la aplicación `InitInstance` , haga lo siguiente:

   - Conecte el `COleTemplateServer` objeto a las plantillas de documento mediante una llamada a la `ConnectTemplate` función miembro del objeto.

   - Llame `COleTemplateServer::RegisterAll` a la función miembro para registrar todos los objetos de clase en el sistema OLE.

   - Llame a `COleTemplateServer::UpdateRegistry`. El único parámetro a `UpdateRegistry` debe ser *OAT_CONTAINER* si la aplicación no se inicia con el modificador "/embedded". Esto registra la aplicación como un contenedor que puede admitir vínculos a objetos incrustados.

      Si la aplicación se inicia con el modificador "/embedded", no debería mostrar su ventana principal, de forma similar a una aplicación de servidor.

El ejemplo de OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md) implementa esta característica. Para obtener un ejemplo de cómo hacerlo, vea la `InitInstance` función en el *OCLIENT. Archivo CPP* de esta aplicación de ejemplo.

## <a name="see-also"></a>Consulte también

[Contenedores](containers.md)<br/>
[Servidores](servers.md)
