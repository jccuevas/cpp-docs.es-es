---
title: "Contenedores: Características avanzadas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4e79b1c88996e835a907129fa5810d4c4dca0770
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="containers-advanced-features"></a>Contenedores: Características avanzadas
Este artículo describen los pasos necesarios para incorporar características avanzadas adicionales a aplicaciones contenedoras existentes. Estas características son:  
  
-   [Una aplicación que es un contenedor y un servidor](#_core_creating_a_container_server_application)  
  
-   [Un vínculo OLE a un objeto incrustado](#_core_links_to_embedded_objects)  
  
##  <a name="_core_creating_a_container_server_application"></a>Crear una aplicación de contenedor y servidor  
 Una aplicación contenedor/servidor es una aplicación que actúa como un contenedor y un servidor. Microsoft Word para Windows es un ejemplo de esto. Puede incrustar documentos de Word para Windows en otras aplicaciones, y también puede incrustar elementos en documentos de Word para Windows. El proceso para modificar la aplicación de contenedor para ser un contenedor y un servidor completo (no se puede crear una aplicación de combinación contenedor/miniservidor) es similar al proceso para crear un servidor completo.  
  
 El artículo [servidores: implementar un servidor](../mfc/servers-implementing-a-server.md) enumera una serie de tareas necesarias para implementar una aplicación de servidor. Si convierte una aplicación de contenedor para una aplicación de contenedor/servidor, deberá realizar algunas de estas mismas tareas, agregando código al contenedor. A continuación enumeran los aspectos importantes a tener en cuenta:  
  
-   El código de contenedor creado por el Asistente para aplicaciones ya inicializa el subsistema OLE. No debe cambiar ni agregar nada para ofrecer la compatibilidad.  
  
-   Siempre que sea la clase base de una clase de documento `COleDocument`, cambie la clase base para `COleServerDoc`.  
  
-   Invalidar `COleClientItem::CanActivate` para evitar que editar elementos en su lugar mientras está utilizando el propio servidor para editar en su lugar.  
  
     Por ejemplo, la aplicación OLE de ejemplo [OCLIENT](../visual-cpp-samples.md) tiene incrustado un elemento creado por la aplicación contenedor/servidor. Abra la aplicación OCLIENT y vigentes editar el elemento creado por la aplicación contenedor/servidor. Mientras edita el elemento de la aplicación, decide que desea incrustar un elemento creado por el ejemplo de MFC OLE [HIERSVR](../visual-cpp-samples.md). Para ello, no puede utilizar la activación en contexto. Debe abrir completamente HIERSVR para activar este elemento. Dado que la biblioteca Microsoft Foundation Class no admite esta característica OLE, reemplazar `COleClientItem::CanActivate` le permite comprobar esta situación y evitar un posible error de tiempo de ejecución en la aplicación.  
  
 Si está creando una nueva aplicación y desea que funcione como una aplicación de contenedor/servidor, elija la opción en el cuadro de diálogo Opciones OLE en el Asistente para aplicaciones y esta compatibilidad se creará automáticamente. Para obtener más información, vea el artículo [información general: crear un contenedor de controles ActiveX](../mfc/reference/creating-an-mfc-activex-control-container.md). Para obtener información acerca de los ejemplos MFC, vea ejemplos de MFC.  
  
 Tenga en cuenta que no se puede insertar una aplicación MDI en sí mismo. Una aplicación que es un contenedor/servidor no se pueden insertar en sí mismo a menos que sea una aplicación SDI.  
  
##  <a name="_core_links_to_embedded_objects"></a>Vínculos a objetos incrustados  
 Los vínculos en función de los objetos incrustados permite a un usuario crear un documento con un vínculo OLE a un objeto incrustado dentro de la aplicación contenedora. Por ejemplo, puede crear un documento en un procesador de textos que contiene una hoja de cálculo incrustada. Si la aplicación admite vínculos a objetos incrustados, podrá pegar un vínculo a la hoja de cálculo contenida en el documento del procesador de textos. Esta característica permite a la aplicación utilizar la información contenida en la hoja de cálculo sin necesidad de saber que el procesador de textos obtuvo.  
  
#### <a name="to-link-to-embedded-objects-in-your-application"></a>Para vincular a los objetos incrustados en la aplicación  
  
1.  Derive la clase de documento de `COleLinkingDoc` en lugar de `COleDocument`.  
  
2.  Crear un identificador de clase OLE (**CLSID**) para la aplicación mediante el generador de Id. de clase incluidos con las herramientas de desarrollo OLE.  
  
3.  Registrar la aplicación con OLE.  
  
4.  Crear un `COleTemplateServer` objeto como un miembro de la clase de aplicación.  
  
5.  En la clase de aplicación `InitInstance` miembro de función, haga lo siguiente:  
  
    -   Conectar su `COleTemplateServer` objeto a las plantillas de documento mediante una llamada del objeto `ConnectTemplate` función miembro.  
  
    -   Llame a la **COleTemplateServer:: RegisterAll** función de miembro para registrar todos los objetos de clase con el sistema OLE.  
  
    -   Llame a `COleTemplateServer::UpdateRegistry`. El único parámetro para `UpdateRegistry` debe ser `OAT_CONTAINER` si no se inicia la aplicación con el modificador "/ incrustado". Esto registra la aplicación como un contenedor que puede admitir vínculos a objetos incrustados.  
  
         Si la aplicación se inicia con el modificador "/ incrustado", no debe mostrar su ventana principal, similar a una aplicación de servidor.  
  
 El ejemplo de MFC OLE [OCLIENT](../visual-cpp-samples.md) implementa esta característica. Para obtener un ejemplo de cómo hacerlo, consulte el `InitInstance` función en el OCLIENT. Archivo CPP de esta aplicación de ejemplo.  
  
## <a name="see-also"></a>Vea también  
 [Contenedores](../mfc/containers.md)   
 [Servidores](../mfc/servers.md)

