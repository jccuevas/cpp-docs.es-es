---
title: Contenedores de documentos activos
ms.date: 11/19/2018
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
ms.openlocfilehash: dc7017a205bedd716e5c87aa23ac96b257af2e16
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626032"
---
# <a name="active-document-containers"></a>Contenedores de documentos activos

Un contenedor de documentos activo, como Microsoft Office Binder o Internet Explorer, le permite trabajar con varios documentos de distintos tipos de aplicación dentro de un solo fotograma (en lugar de obligarle a crear y usar varios marcos de aplicación para cada tipo de documento).

MFC proporciona compatibilidad total con los contenedores de documentos activos en la `COleDocObjectItem` clase. Puede usar el Asistente para aplicaciones MFC para crear un contenedor de documentos activo activando la casilla **contenedor de documentos activos** en la página **compatibilidad con documentos compuestos** del Asistente para aplicaciones MFC. Para obtener más información, consulte [crear una aplicación de contenedor de documentos activos](creating-an-active-document-container-application.md).

Para obtener más información acerca de los contenedores de documentos activos, vea:

- [Requisitos de contenedor](#container_requirements)

- [Objetos de sitio de documento](#document_site_objects)

- [Ver objetos de sitio](#view_site_objects)

- [Objeto marco](#frame_object)

- [Combinación del menú Ayuda](help-menu-merging.md)

- [Impresión mediante programación](programmatic-printing.md)

- [Destinos de comando](message-handling-and-command-targets.md)

## <a name="container-requirements"></a><a name="container_requirements"></a>Requisitos de contenedor

La compatibilidad con documentos activos en un contenedor de documentos activo implica algo más que las implementaciones de interfaz: también requiere el conocimiento del uso de las interfaces de un objeto contenido. Lo mismo se aplica a las extensiones de documento activas, donde el contenedor también debe saber cómo usar esas interfaces de extensión en los propios documentos activos.

Un contenedor de documentos activo que integra documentos activos debe:

- Ser capaz de controlar el almacenamiento de objetos a través de la `IPersistStorage` interfaz, es decir, debe proporcionar una `IStorage` instancia a cada documento activo.

- Admite las características de inserción básicas de documentos OLE, que requieren objetos de "sitio" (uno por documento o incrustación) que implementan `IOleClientSite` y `IAdviseSink` .

- Admitir la activación en contexto de objetos incrustados o documentos activos. Los objetos de sitio del contenedor deben implementar `IOleInPlaceSite` y el objeto de marco del contenedor debe proporcionar `IOleInPlaceFrame` .

- Admitir las extensiones de los documentos activos implementando `IOleDocumentSite` para proporcionar el mecanismo para que el contenedor se comunique con el documento. Opcionalmente, el contenedor puede implementar las interfaces de documento activo `IOleCommandTarget` y `IContinueCallback` seleccionar comandos sencillos, como imprimir o guardar.

El objeto de marco, los objetos de vista y el objeto contenedor pueden implementar opcionalmente `IOleCommandTarget` para admitir el envío de determinados comandos, como se describe en [destinos de comando](message-handling-and-command-targets.md). Los objetos de vista y contenedor también pueden implementar opcionalmente `IPrint` y `IContinueCallback` , para admitir la impresión mediante programación, como se describe en [impresión mediante programación](programmatic-printing.md).

En la ilustración siguiente se muestran las relaciones conceptuales entre un contenedor y sus componentes (a la izquierda) y el documento activo y sus vistas (a la derecha). El documento activo administra el almacenamiento y los datos, y la vista muestra u opcionalmente los datos. Las interfaces en negrita son las necesarias para la participación de documentos activos. los de negrita y cursiva son opcionales. Todas las demás interfaces son necesarias.

![Interfaces de contenedor de documentos activo](../mfc/media/vc37gj1.gif "Interfaces de contenedor de documentos activo")

Un documento que admite una sola vista puede implementar los componentes de la vista y del documento (es decir, sus interfaces correspondientes) en una sola clase concreta. Además, un sitio de contenedor que solo admite una vista cada vez puede combinar el sitio de documento y el sitio de vista en una única clase de sitio concreta. Sin embargo, el objeto de marco del contenedor debe ser distinto y el componente de documento del contenedor se incluye simplemente aquí para proporcionar una imagen completa de la arquitectura. no se ve afectado por la arquitectura de contención de documentos activos.

## <a name="document-site-objects"></a><a name="document_site_objects"></a>Objetos de sitio de documento

En la arquitectura de contención de documentos activos, un sitio de documento es igual que un objeto de sitio de cliente en documentos OLE con la adición de la `IOleDocument` interfaz:

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```

El sitio del documento es conceptualmente el contenedor para uno o más objetos de "ver sitio". Cada objeto de sitio de vista está asociado a objetos de vista individuales del documento administrado por el sitio de documento. Si el contenedor solo admite una vista única por cada sitio de documento, puede implementar el sitio de documento y el sitio de vista con una sola clase concreta.

## <a name="view-site-objects"></a><a name="view_site_objects"></a>Ver objetos de sitio

El objeto de sitio de vista de un contenedor administra el espacio de presentación para una vista determinada de un documento. Además de admitir la interfaz estándar `IOleInPlaceSite` , un sitio de vista también implementa normalmente `IContinueCallback` para el control de impresión mediante programación. (Observe que el objeto de vista nunca consulta para `IContinueCallback` , por lo que realmente se puede implementar en cualquier objeto que desee el contenedor).

Un contenedor que admite varias vistas debe ser capaz de crear varios objetos de sitio de vista en el sitio de documento. Esto proporciona cada vista con servicios de activación y desactivación independientes, tal y como se proporciona a través de `IOleInPlaceSite` .

## <a name="frame-object"></a><a name="frame_object"></a>Objeto Frame

El objeto de marco del contenedor es, en su mayor parte, el mismo fotograma que se usa para la activación en contexto en documentos OLE, es decir, el que controla la negociación de menús y barras de herramientas. Un objeto de vista tiene acceso a este objeto de marco a través `IOleInPlaceSite::GetWindowContext` de, que también proporciona acceso al objeto contenedor que representa el documento contenedor (que puede controlar la negociación de la barra de herramientas de nivel de panel y la enumeración de objetos contenidos).

Un contenedor de documentos activo puede aumentar el marco agregando `IOleCommandTarget` . Esto le permite recibir comandos que se originan en la interfaz de usuario del documento activo de la misma manera que esta interfaz puede permitir que un contenedor envíe los mismos comandos (como **archivo nuevo**, **abrir**, **Guardar como**, **Imprimir**; **Editar Copiar**, **pegar**, **Deshacer**y otros) en un documento activo. Para obtener más información, consulte [destinos de comandos](message-handling-and-command-targets.md).

## <a name="see-also"></a>Consulte también

[Contención de documentos activos](active-document-containment.md)
