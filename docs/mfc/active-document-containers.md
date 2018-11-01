---
title: Contenedores de documentos activos
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
ms.openlocfilehash: ec2e4d11e00040cf0b94957db8466d127e0b5420
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50510843"
---
# <a name="active-document-containers"></a>Contenedores de documentos activos

Un contenedor de documentos activos, por ejemplo, el cuaderno de Microsoft Office o Internet Explorer, le permite trabajar con varios documentos de diferentes tipos de aplicaciones en un solo marco (en lugar de obligarle a crear y usar varios marcos de aplicación para cada uno tipo de documento).

MFC proporciona compatibilidad total con contenedores de documentos activos en el `COleDocObjectItem` clase. Puede usar el Asistente para aplicaciones MFC para crear un contenedor de documentos activos seleccionando el **contenedor de documentos activos** casilla de verificación en la **compatibilidad con documentos compuestos** página del Asistente para aplicaciones MFC. Para obtener más información, consulte [crear una aplicación de contenedor de documentos activos](../mfc/creating-an-active-document-container-application.md).

Para obtener más información sobre los contenedores de documentos activos, vea:

- [Requisitos de los contenedores](#container_requirements)

- [Objetos de sitio de documento](#document_site_objects)

- [Ver objetos de sitio](#view_site_objects)

- [Objeto marco](#frame_object)

- [Combinación del menú Ayuda](../mfc/help-menu-merging.md)

- [Impresión mediante programación](../mfc/programmatic-printing.md)

- [Destinos de comando](../mfc/message-handling-and-command-targets.md)

##  <a name="container_requirements"></a> Requisitos de los contenedores

Soporte técnico del documento activo en un contenedor de documentos activos implica algo más que las implementaciones de interfaz: también requiere un conocimiento del uso de las interfaces de un objeto contenido. Lo mismo se aplica a las extensiones de documento activo, donde el contenedor también debe saber cómo usar esas interfaces de extensión en los documentos activos.

Un contenedor de documentos activos que integre documentos activos debe:

- Ser capaz de controlar el almacenamiento de objetos a través de la `IPersistStorage` interfaz, es decir, debe proporcionar un `IStorage` instancia para cada documento activo.

- Admite las características básicas de incrustación de documentos OLE, se necesitan objetos de "sitio" (uno por cada documento o incrustación) que implementan `IOleClientSite` y `IAdviseSink`.

- Admite la activación en contexto de objetos incrustados o documentos activos. Deben implementar los objetos de sitio del contenedor `IOleInPlaceSite` y debe proporcionar el objeto de marco del contenedor `IOleInPlaceFrame`.

- Compatibilidad con las extensiones de los documentos activos mediante la implementación de `IOleDocumentSite` para proporcionar el mecanismo para el contenedor para comunicarse con el documento. Opcionalmente, el contenedor puede implementar las interfaces de documento activo `IOleCommandTarget` y `IContinueCallback` para recoger comandos sencillos como imprimir o guardar.

El objeto de marco, los objetos de vista y el objeto contenedor pueden implementar opcionalmente `IOleCommandTarget` para admitir el envío de determinados comandos, como se describe en [destinos de comando](../mfc/message-handling-and-command-targets.md). Opcionalmente, también pueden implementar objetos de vista y el contenedor `IPrint` y `IContinueCallback`, para admitir la impresión mediante programación, como se describe en [impresión mediante programación](../mfc/programmatic-printing.md).

En la siguiente ilustración muestra las relaciones conceptuales entre un contenedor y sus componentes (a la izquierda) y el documento activo y sus vistas (a la derecha). El documento activo administra el almacenamiento y datos, y la vista se muestra o imprime, opcionalmente, esos datos. Las interfaces en negrita son las necesarias para la participación del documento activo; esos negrita y cursiva son opcionales. Todas las demás interfaces son necesarios.

![Interfaces de contenedor de documentos activos](../mfc/media/vc37gj1.gif "vc37gj1")

Un documento que admite una sola vista puede implementar los componentes de la vista y el documento (es decir, sus interfaces correspondientes) en una clase concreta individual. Además, un sitio de contenedor que sólo admite una vista a la vez puede combinar el sitio de documento y la vista en una clase único sitio concreto. Objeto de marco del contenedor, sin embargo, debe ser distintos, y el componente del documento del contenedor sólo se incluye aquí para ofrecer una imagen completa de la arquitectura; no se ve afectado por la arquitectura de contención de documentos activos.

##  <a name="document_site_objects"></a> Objetos de sitio de documento

En la arquitectura de contención de documentos activos, un sitio de documento es el mismo que un objeto de sitio de cliente en los documentos OLE con la adición de la `IOleDocument` interfaz:

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```

El sitio de documento es conceptualmente el contenedor para uno o más objetos de "sitio de vista". Cada objeto de sitio de vista está asociado con los objetos de vista individuales del documento administrado por el sitio de documento. Si el contenedor solo admite una vista única por cada sitio de documento, puede implementar el sitio de documento y el sitio de vista con una clase concreta individual.

##  <a name="view_site_objects"></a> Ver objetos de sitio

Objeto de sitio de vista de un contenedor administra el espacio de visualización para una vista concreta de un documento. Además de admitir el estándar `IOleInPlaceSite` interfaz, generalmente también implementa un sitio de vista `IContinueCallback` para control de impresión mediante programación. (Tenga en cuenta que el objeto de vista nunca consulta `IContinueCallback` por lo que realmente se pueden implementar en cualquier objeto del contenedor de deseos.)

Un contenedor que admite varias vistas debe ser capaz de crear la vista de varios objetos del sitio en el sitio de documento. Esto proporciona a cada vista con los servicios de activación y desactivación independientes a través de `IOleInPlaceSite`.

##  <a name="frame_object"></a> Objeto de marco

En su mayor parte, objeto de marco del contenedor es el mismo marco que se usa para la activación en contexto en los documentos OLE, es decir, lo que controla la negociación de menú y barra de herramientas. Un objeto de vista tiene acceso a este objeto de marco a través de `IOleInPlaceSite::GetWindowContext`, que también proporciona acceso al objeto contenedor que representa el documento contenedor (que puede controlar la negociación de la barra de herramientas del panel de nivel y enumeración de objetos contenidos).

Un contenedor de documentos activos puede ampliar el marco agregando `IOleCommandTarget`. Esto le permite recibir comandos que se originan en la interfaz de usuario del documento activo de la misma manera que esta interfaz puede permitir que un contenedor enviar los mismos comandos (como **nuevo archivo**, **abierto**,  **Guardar como**, **impresión**; **Editar una copia**, **pegar**, **deshacer**etc.) a un documento activo. Para obtener más información, consulte [destinos de comando](../mfc/message-handling-and-command-targets.md).

## <a name="see-also"></a>Vea también

[Contención de documentos activos](../mfc/active-document-containment.md)

