---
title: Contenedores de documentos activos
ms.date: 11/19/2018
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
ms.openlocfilehash: e2005ffed592fa1de278e0f6339d94687a20fd06
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377387"
---
# <a name="active-document-containers"></a>Contenedores de documentos activos

Un contenedor de documentos activo, como Microsoft Office Binder o Internet Explorer, le permite trabajar con varios documentos de diferentes tipos de aplicación dentro de un único marco (en lugar de obligarle a crear y usar varios marcos de aplicación para cada tipo de documento).

MFC proporciona compatibilidad completa con `COleDocObjectItem` los contenedores de documentos activos en la clase. Puede usar el Asistente para aplicaciones MFC para crear un contenedor de documentos activo seleccionando la casilla contenedor de **documentos activos** en la página **Compatibilidad con documentos compuestos** del Asistente para aplicaciones MFC. Para obtener más información, consulte Creación de una aplicación contenedora de [documentos activos](../mfc/creating-an-active-document-container-application.md).

Para obtener más información acerca de los contenedores de documentos activos, consulte:

- [Requisitos del contenedor](#container_requirements)

- [Objetos de sitio de documentos](#document_site_objects)

- [Ver objetos del sitio](#view_site_objects)

- [Objeto marco](#frame_object)

- [Combinación del menú Ayuda](../mfc/help-menu-merging.md)

- [Impresión programática](../mfc/programmatic-printing.md)

- [Destinos de comando](../mfc/message-handling-and-command-targets.md)

## <a name="container-requirements"></a><a name="container_requirements"></a>Requisitos del contenedor

La compatibilidad con documentos activos en un contenedor de documentos activo implica algo más que implementaciones de interfaz: también requiere conocimiento sin usar las interfaces de un objeto contenido. Lo mismo se aplica a las extensiones de documentoactivas, donde el contenedor también debe saber cómo utilizar esas interfaces de extensión en los propios documentos activos.

Un contenedor de documentos activo que integre documentos activos debe:

- Ser capaz de controlar `IPersistStorage` el almacenamiento de objetos `IStorage` a través de la interfaz, es decir, debe proporcionar una instancia a cada documento activo.

- Admite las características básicas de incrustación de documentos OLE, lo que requiere `IOleClientSite` `IAdviseSink`objetos de "sitio" (uno por documento o incrustación) que implementan y .

- Admite la activación in situ de objetos incrustados o documentos activos. Los objetos de sitio `IOleInPlaceSite` del contenedor deben implementarse `IOleInPlaceFrame`y el objeto frame del contenedor debe proporcionar .

- Apoyar las extensiones de `IOleDocumentSite` los documentos activos mediante la implementación para proporcionar el mecanismo para que el contenedor hable con el documento. Opcionalmente, el contenedor puede implementar `IOleCommandTarget` las `IContinueCallback` interfaces de documentoactivas y recoger comandos simples como imprimir o guardar.

El objeto frame, los objetos de vista `IOleCommandTarget` y el objeto contenedor pueden implementarse opcionalmente para admitir la distribución de determinados comandos, como se describe en Destinos de [comando](../mfc/message-handling-and-command-targets.md). Los objetos de vista `IPrint` y `IContinueCallback`contenedor también se pueden implementar opcionalmente y , para admitir la impresión mediante programación, como se describe en [Impresión mediante programación](../mfc/programmatic-printing.md).

La figura siguiente muestra las relaciones conceptuales entre un contenedor y sus componentes (a la izquierda) y el documento activo y sus vistas (a la derecha). El documento activo administra el almacenamiento y los datos, y la vista muestra u imprime opcionalmente esos datos. Las interfaces en negrita son las necesarias para la participación activa de documentos; los negritas y cursivas son opcionales. Todas las demás interfaces son necesarias.

![Interfaces de contenedor de documentos activo](../mfc/media/vc37gj1.gif "Interfaces de contenedor de documentos activo")

Un documento que admite una sola vista puede implementar los componentes de vista y documento (es decir, sus interfaces correspondientes) en una sola clase concreta. Además, un sitio contenedor que solo admite una vista a la vez puede combinar el sitio de documento y el sitio de vista en una sola clase de sitio concreta. El objeto frame del contenedor, sin embargo, debe seguir siendo distinto, y el componente de documento del contenedor se incluye simplemente aquí para dar una imagen completa de la arquitectura; no se ve afectada por la arquitectura de contención de documentos activa.

## <a name="document-site-objects"></a><a name="document_site_objects"></a>Objetos de sitio de documentos

En la arquitectura de contención de documentos activa, un sitio de documento `IOleDocument` es el mismo que un objeto de sitio de cliente en documentos OLE con la adición de la interfaz:

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```

El sitio del documento es conceptualmente el contenedor de uno o varios objetos de "sitio de vista". Cada objeto de sitio de vista está asociado a objetos de vista individuales del documento administrado por el sitio del documento. Si el contenedor solo admite una sola vista por sitio de documento, puede implementar el sitio del documento y el sitio de vista con una sola clase concreta.

## <a name="view-site-objects"></a><a name="view_site_objects"></a>Ver objetos del sitio

El objeto de sitio de vista de un contenedor administra el espacio de visualización de una vista determinada de un documento. Además de admitir `IOleInPlaceSite` la interfaz estándar, un `IContinueCallback` sitio de vista también generalmente implementa para el control de impresión mediante programación. (Tenga en cuenta que el `IContinueCallback` objeto de vista nunca consulta para que realmente se pueda implementar en cualquier objeto que el contenedor desee.)

Un contenedor que admita varias vistas debe poder crear varios objetos de sitio de vista dentro del sitio del documento. Esto proporciona a cada vista servicios de `IOleInPlaceSite`activación y desactivación independientes según lo proporcionado a través de .

## <a name="frame-object"></a><a name="frame_object"></a>Objeto Frame

El objeto de marco del contenedor es, en su mayor parte, el mismo marco que se utiliza para la activación en contexto en documentos OLE, es decir, el que controla la negociación de menú y barra de herramientas. Un objeto de vista tiene `IOleInPlaceSite::GetWindowContext`acceso a este objeto de marco a través de , que también proporciona acceso al objeto contenedor que representa el documento contenedor (que puede controlar la negociación de la barra de herramientas de nivel de panel y la enumeración de objetos contenidos).

Un contenedor de documentos activo `IOleCommandTarget`puede aumentar el marco agregando . Esto le permite recibir comandos que se originan en la interfaz de usuario del documento activo de la misma manera que esta interfaz puede permitir que un contenedor envíe los mismos comandos (como **File New**, **Open**, **Save As**, **Print**; **Editar copiar**, **Pegar**, **Deshacer**y otros) en un documento activo. Para obtener más información, consulte [Destinos de comando](../mfc/message-handling-and-command-targets.md).

## <a name="see-also"></a>Consulte también

[Contención de documentos activos](../mfc/active-document-containment.md)
