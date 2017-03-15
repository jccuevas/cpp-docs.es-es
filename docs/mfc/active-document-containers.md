---
title: "Contenedores de documentos activos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contenedores de documentos activos [C++]"
  - "documentos activos [C++], contenedores"
  - "contenedores [C++], documento activo"
  - "MFC COM [C++], contención de documentos activos"
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Contenedores de documentos activos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un contenedor de documentos activos, como enlazador de Microsoft Office o Internet Explorer, permite ejecutar varios documentos de diferentes tipos de aplicación dentro de un mismo cuadro \(en lugar de forzarle para crear y utilizar los cuadros de aplicación múltiple para cada tipo de documento\).  
  
 MFC proporciona compatibilidad completa para los contenedores de documento activo en la clase de `COleDocObjectItem` .  Puede utilizar el Asistente para aplicaciones MFC para crear un contenedor de documento activo activando la casilla de **Active document container** en la página de **Compatib. doc. compuestos** del Asistente para aplicaciones MFC.  Para obtener más información, vea [Crear una aplicación contenedora de documentos activos](../mfc/creating-an-active-document-container-application.md).  
  
 Para obtener más información sobre los contenedores del documento activo, vea:  
  
-   [Requisitos de contenedor](#container_requirements)  
  
-   [Objetos de sitio de documento](#document_site_objects)  
  
-   [Objetos de sitio de vista](#view_site_objects)  
  
-   [Objeto de marco](#frame_object)  
  
-   [Combinación del menú ayuda](../mfc/help-menu-merging.md)  
  
-   [Impresión mediante programación](../mfc/programmatic-printing.md)  
  
-   [Destinos de comando](../mfc/message-handling-and-command-targets.md)  
  
##  <a name="container_requirements"></a> Requisitos de contenedor  
 Compatibilidad del documento activo en un contenedor de documento activo implica algo más que implementaciones de interfaz: también requiere conocimientos de utilizar las interfaces de un objeto contenido.  Lo mismo se aplica a las extensiones del documento activo, donde el contenedor también debe saber utilizar esas interfaces en los documentos activos propios de extensión.  
  
 Un contenedor de documento activo que integra documentos activos debe:  
  
-   Es capaz de administrar el almacenamiento del objeto a través de la interfaz de **IPersistStorage** , es decir, debe proporcionar una instancia de `IStorage` a cada documento activo.  
  
-   Admite las características principales de incrustación de documentos OLE, necesitando los objetos de “sitio” \(uno por el documento o insertar\) que implementan **IOleClientSite** y **IAdviseSink**.  
  
-   Admite la activación de contexto de objetos incrustados o de documentos activos.  Los objetos del sitio del contenedor deben implementar `IOleInPlaceSite` y el objeto de marco de contenedor debe proporcionar **IOleInPlaceFrame**.  
  
-   Admite las extensiones de los documentos activos implementando `IOleDocumentSite` para proporcionar un mecanismo para que el contenedor hable con el documento.  Opcionalmente, el contenedor puede implementar las interfaces `IOleCommandTarget` y `IContinueCallback` de documento activo para detectar comandos simples como imprimir o guardar.  
  
 El objeto de marco, los objetos de vista, y el objeto contenedor pueden implementar opcionalmente **IOleCommandTarget** para admitir el envío de determinados comandos, como se describe en [Destinos de comando](../mfc/message-handling-and-command-targets.md).  La vista y objetos contenedor también pueden implementar opcionalmente `IPrint` y `IContinueCallback`, para admitir la impresión mediante programación, como se describe en [Impresión mediante programación](../mfc/programmatic-printing.md).  
  
 La ilustración siguiente muestra las relaciones conceptuales entre un contenedor y sus componentes \(a la izquierda\), y el documento activo y sus vistas \(a la derecha\).  El documento activo administra el almacenamiento y datos, y la muestra o imprime opcionalmente esos datos.  Las interfaces en negrita son las necesarias para la participación del documento activo; que negrita y cursiva son opcionales.  Se requieren el resto de interfaces.  
  
 ![Interfaces de contenedor de documentos activo](../mfc/media/vc37gj1.png "vc37gj1")  
  
 Un documento que sólo admite una vista única puede implementar los componentes de la vista y el documento \(es decir, sus interfaces correspondientes\) en una única clase concreta.  Además, un sitio de contenedor que sólo admite una vista al mismo tiempo puede combinar el sitio del documento y el sitio de una clase concreta única del sitio.  El objeto de marco de contenedor, sin embargo, debe seguir siendo distinto, e incluyen el componente de contenedor simplemente aquí para dar una imagen completa de arquitectura; no se ve afectado por la arquitectura de contención del documento activo.  
  
##  <a name="document_site_objects"></a> Objetos de sitio de documento  
 En la arquitectura de contención de documento activo, un sitio de documento es igual que un objeto de sitio de cliente en documentos de OLE con la adición de la interfaz de `IOleDocument` :  
  
 `interface IOleDocumentSite : IUnknown`  
  
 `{`  
  
 `HRESULT ActivateMe(IOleDocumentView *pViewToActivate);`  
  
 `}`  
  
 El sitio de documento es conceptual el contenedor para uno o más “objetos de sitio de vista”.  Cada objeto de sitio de vista se asocia ver los objetos individuales de documento administrado por el sitio del documento.  Si el contenedor sólo admite una vista única por sitio de documento, puede implementar el sitio del documento y el sitio de la vista con una sola clase concreta.  
  
##  <a name="view_site_objects"></a> Objetos de sitio de vista  
 El objeto del sitio de la vista de un contenedor administra el espacio de pantalla para una vista determinada de un documento.  Además de admitir la interfaz estándar de `IOleInPlaceSite` , un sitio de la vista también suele implementar `IContinueCallback` para el control de impresión mediante programación. \(Observe que de vista del objeto consultas nunca para `IContinueCallback` para que se pueden implementar realmente en cualquier objeto el contenedor desea.\)  
  
 Un contenedor que admite varias vistas debe poder crear varios objetos de sitio de vista dentro del sitio del documento.  Esto proporciona cada vista con servicios independientes de activación y la desactivación suministrados con `IOleInPlaceSite`.  
  
##  <a name="frame_object"></a> Objeto de marco  
 El objeto de marco del contenedor es, en general, el mismo marco que se utiliza para la activación en contexto en documentos de OLE, es decir, la que controla la negociación del menú y la barra de herramientas.  Un objeto de vista tiene acceso a este objeto de cuadro con **IOleInPlaceSite::GetWindowContext**, que también proporciona acceso al objeto contenedor que representa el documento contenedor \(que puede controlar la negociación de la barra de herramientas de panel\- nivel y la enumeración contenida de objeto\).  
  
 Un contenedor de documentos activos pueden aumentar el cuadro agregando `IOleCommandTarget`.  Esto permite recibir los comandos que se originan en la interfaz de usuario del documento activo de la misma manera que esta interfaz puede permitir que un contenedor envíe los mismos comandos \(como **File New**, **Abierta**, **Guardar como**, **Impresión**; **Edit Copy**, **Pegar**, **Deshacer**, etc.\) a un documento activo.  Para obtener más información, vea [Destinos de comando](../mfc/message-handling-and-command-targets.md).  
  
## Vea también  
 [Contención de documentos activos](../mfc/active-document-containment.md)