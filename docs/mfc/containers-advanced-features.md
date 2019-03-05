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
ms.openlocfilehash: 9d83ba601766f4b6fb84576571239a250169abb1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278709"
---
# <a name="containers-advanced-features"></a>Contenedores: Características avanzadas

En este artículo se describe los pasos necesarios para incorporar características avanzadas adicionales a las aplicaciones existentes de contenedor. Estas características son:

- [Una aplicación que es un contenedor y un servidor](#_core_creating_a_container_server_application)

- [Un vínculo OLE a un objeto incrustado](#_core_links_to_embedded_objects)

##  <a name="_core_creating_a_container_server_application"></a> Creación de una aplicación de contenedor y servidor

Una aplicación de contenedor y servidor es una aplicación que actúa como un contenedor y un servidor. Microsoft Word para Windows es un ejemplo de esto. Puede insertar documentos de Word para Windows en otras aplicaciones, y también puede insertar elementos en documentos de Word para Windows. El proceso para modificar la aplicación de contenedor para ser un contenedor y un servidor completo (no se puede crear una aplicación de contenedor/miniservidor combinación) es similar al proceso de creación de un servidor completo.

El artículo [servidores: Implementación de un servidor](../mfc/servers-implementing-a-server.md) se enumeran una serie de tareas necesarias para implementar una aplicación de servidor. Si convierte una aplicación de contenedor a una aplicación de contenedor y servidor, a continuación, deberá realizar algunas de estas mismas tareas, agregar código al contenedor. A continuación enumeran los aspectos importantes a tener en cuenta:

- El código de contenedor creado por el Asistente para aplicaciones ya inicializa el subsistema OLE. No necesitará cambiar ni agregar nada para que admiten.

- Siempre que sea la clase base de una clase de documento `COleDocument`, cambie la clase base para `COleServerDoc`.

- Invalidar `COleClientItem::CanActivate` para evitar la edición de elementos en su lugar mientras el propio servidor se utiliza para editar en su lugar.

   Por ejemplo, el ejemplo OLE [OCLIENT](../visual-cpp-samples.md) tiene incrustado un elemento creado por la aplicación de contenedor y servidor. Abra la aplicación OCLIENT y in situ editar el elemento creado por la aplicación de contenedor y servidor. Mientras edita el elemento de la aplicación, decide que desea insertar un elemento creado por el ejemplo OLE de MFC [HIERSVR](../visual-cpp-samples.md). Para ello, no puede utilizar la activación en contexto. Debe abrir completamente HIERSVR para activar este elemento. Dado que la biblioteca Microsoft Foundation Class no admite esta característica OLE, reemplazar `COleClientItem::CanActivate` le permite comprobar esta situación y evitar un posible error de tiempo de ejecución en la aplicación.

Si está creando una nueva aplicación y desea que funcione como una aplicación de contenedor y servidor, elija la opción en el cuadro de diálogo Opciones OLE en el Asistente para la aplicación y esta compatibilidad se crearán automáticamente. Para obtener más información, vea el artículo [información general: Creación de un contenedor de controles ActiveX](../mfc/reference/creating-an-mfc-activex-control-container.md). Para obtener información acerca de los ejemplos MFC, vea los ejemplos de MFC.

Tenga en cuenta que no se puede insertar una aplicación MDI en sí mismo. Una aplicación que es un contenedor y el servidor no puede insertarse en sí mismo a menos que sea una aplicación SDI.

##  <a name="_core_links_to_embedded_objects"></a> Vínculos a objetos incrustados

Los vínculos a la función de los objetos incrustados permite al usuario crear un documento con un vínculo OLE a un objeto incrustado dentro de la aplicación contenedora. Por ejemplo, puede crear un documento en un procesador de textos que contiene una hoja de cálculo incrustada. Si la aplicación admite vínculos a objetos incrustados, puede pegar un vínculo a la hoja de cálculo incluido en el documento del procesador de textos. Esta característica permite la aplicación para usar la información contenida en la hoja de cálculo sin necesidad de saber que el procesador de textos la obtuvo.

#### <a name="to-link-to-embedded-objects-in-your-application"></a>Para vincular a objetos incrustados en la aplicación

1. Derive la clase de documento de `COleLinkingDoc` en lugar de `COleDocument`.

1. Crear un identificador de clase OLE (**CLSID**) para la aplicación mediante el generador de Id. de clase incluidos con las herramientas de desarrollo OLE.

1. Registrar la aplicación con OLE.

1. Crear un `COleTemplateServer` objeto como un miembro de la clase de aplicación.

1. En la clase de aplicación `InitInstance` miembro de función, haga lo siguiente:

   - Conectar su `COleTemplateServer` objeto a las plantillas de documento mediante una llamada del objeto `ConnectTemplate` función miembro.

   - Llame a la `COleTemplateServer::RegisterAll` la función miembro para registrar todos los objetos de clase con el sistema OLE.

   - Llame a `COleTemplateServer::UpdateRegistry`. El único parámetro a `UpdateRegistry` debe ser *OAT_CONTAINER* si no se inicia la aplicación con el modificador "/ incrustado". Esto registra la aplicación como un contenedor que puede admitir vínculos a objetos incrustados.

         If the application is launched with the "/Embedded" switch, it should not show its main window, similar to a server application.

El ejemplo OLE de MFC [OCLIENT](../visual-cpp-samples.md) implementa esta característica. Para obtener un ejemplo de cómo hacerlo, consulte el `InitInstance` funcionando en el *OCLIENT. CPP* archivos de esta aplicación de ejemplo.

## <a name="see-also"></a>Vea también

[Contenedores](../mfc/containers.md)<br/>
[Servidores](../mfc/servers.md)
