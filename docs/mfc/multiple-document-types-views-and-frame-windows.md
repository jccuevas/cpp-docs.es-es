---
title: Varios tipos de documentos, vistas y ventanas de marco | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- static splitter windows [MFC]
- multiple views [MFC]
- multiple document types [MFC]
- multiple views [MFC], frame windows
- document classes [MFC], multiple
- documents [MFC], multiple types of
- splitter windows [MFC], dynamic
- dynamic splitter windows [MFC]
- windows [MFC], dynamic splitter
- windows [MFC], static splitter
- multiple frame windows [MFC]
- splitter windows [MFC], static
ms.assetid: c6b9e4e0-7c9c-45f1-a804-aeac39c9a128
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2ab8bff6484f81c482ddd8629ff33772fab1aeba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="multiple-document-types-views-and-frame-windows"></a>Varios tipos de documentos, vistas y ventanas de marco
La relación estándar entre un documento, su vista y su ventana de marco se describe en [Document/View Creation](../mfc/document-view-creation.md)(Creación de documentos/vistas). Muchas aplicaciones admiten un único tipo de documento (aunque probablemente permitan que haya muchos documentos abiertos de ese tipo) con una sola vista en el documento y una sola ventana de marco por documento. Pero puede que algunas aplicaciones necesiten modificar uno o varios de estos valores predeterminados.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Multiple document types](#_core_multiple_document_types)  
  
-   [Multiple views](#_core_multiple_views)  
  
-   [Multiple frame windows](#_core_multiple_frame_windows)  
  
-   [Ventanas divisoras](#_core_splitter_windows)  
  
##  <a name="_core_multiple_document_types"></a> Multiple Document Types  
 El Asistente para aplicaciones MFC crea una clase de documento único automáticamente. Sin embargo, en algunos casos puede que necesite admitir más de un tipo de documento, por ejemplo, si la aplicación necesita hojas de cálculo y gráficos. Cada tipo de documento viene representado por su propia clase de documento y, probablemente, también por su propia clase de vista. Cuando el usuario elige el comando Archivo Nuevo, se abre un cuadro de diálogo en el marco de trabajo donde se enumeran los tipos de documento admitidos. Después, se crea un documento del tipo que el usuario haya elegido. Cada tipo de documento se administra mediante su propio objeto de plantilla de documento.  
  
 Para crear más clases de documento, vea [Adding a Class](../ide/adding-a-class-visual-cpp.md)(Agregar una clase). Elija [CDocument](../mfc/reference/cdocument-class.md) como el tipo de clase del que se va a derivar y proporcione la información del documento solicitada. Luego, implemente los datos de la nueva clase.  
  
 Para que el marco de trabajo sepa de la existencia de la clase de documento adicional, debe agregar una segunda llamada a [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) en la invalidación [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) de la clase de aplicación. Para obtener más información, vea [Document Templates](../mfc/document-templates-and-the-document-view-creation-process.md)(Plantillas de documento).  
  
##  <a name="_core_multiple_views"></a> Multiple Views  
 Varios documentos necesitan una sola vista, pero se puede admitir más de una vista de un documento. Para ayudarle a implementar varias vistas, un objeto de documento conserva una lista de sus vistas, proporciona funciones miembro para agregar o quitar vistas y, asimismo, proporciona la función miembro [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) para permitir que varias vistas sepan cuándo han cambiado los datos del documento.  
  
 MFC admite tres interfaces de usuario comunes que requieren varias vistas en el mismo documento. Estos modelos son:  
  
-   Objetos de vista de la misma clase, cada uno en una ventana de marco de documento MDI propia.  
  
     Es conveniente que exista la posibilidad de crear una segunda ventana de marco en un documento. Así, los usuarios podrían elegir un comando Nueva ventana para abrir un segundo marco con una vista del mismo documento y, después, usar ambos marcos para ver distintas partes del documento al mismo tiempo. Para dar cabida al comando Nueva ventana del menú Ventana en las aplicaciones MDI, lo que el marco de trabajo hace es duplicar la vista y la ventana de marco iniciales conectadas al documento.  
  
-   Objetos de vista de la misma clase en la misma ventana de marco de documento.  
  
     Las ventanas divisoras dividen el espacio de una vista de documento único en varias vistas distintas de ese documento. El marco de trabajo crea varios objetos de vista a partir de la misma clase de vista. Para obtener más información, vea [Ventanas divisoras](#_core_splitter_windows).  
  
-   Objetos de vista de diferente clase en una sola ventana de marco.  
  
     En este modelo, que es una variación de la ventana divisora, varias vistas comparten una sola ventana de marco. Las vistas se construyen a partir de clases diferentes, y cada una de esas vistas proporciona una forma distinta de ver el mismo documento. Por ejemplo, una vista podría mostrar un documento de procesamiento de texto en modo normal, mientras que otra lo muestra en modo de esquema. Un control divisor permite al usuario ajustar los tamaños relativos de las vistas.  
  
 En la siguiente imagen, dividida en las partes a, b y c, se muestran los tres modelos de interfaz de usuario en el orden descrito anteriormente.  
  
 ![Varios &#45; interfaces de usuario de vista](../mfc/media/vc37a71.gif "vc37a71")  
Interfaces de usuarios de varias vistas  
  
 Para proporcionar estos modelos, el marco de trabajo implementa el comando Nueva ventana y proporciona la clase [CSplitterWnd](../mfc/reference/csplitterwnd-class.md), como se describe en [Ventanas divisoras](#_core_splitter_windows). Se pueden implementar otros modelos teniendo estos como punto de partida. Para ver programas de ejemplo que ilustran distintas configuraciones de vistas, ventanas de marco y divisores, vea [MFC Samples](../visual-cpp-samples.md)(Ejemplos de MFC).  
  
 Para obtener más información sobre `UpdateAllViews`, vea la clase [CView](../mfc/reference/cview-class.md) en *MFC Reference* (Referencia de MFC), así como [Scribble sample](../visual-cpp-samples.md)(Ejemplo de Scribble).  
  
##  <a name="_core_multiple_frame_windows"></a> Multiple Frame Windows  
 Puede usar el comando Nueva ventana del menú Ventana de las aplicaciones MDI para crear una segunda ventana de marco en el mismo documento. Para obtener más información, vea el primer modelo en la ilustración Interfaces de usuario de varias vistas.  
  
##  <a name="_core_splitter_windows"></a> Splitter Windows  
 En una ventana divisora, la ventana se divide (o puede dividirse) en dos o más paneles desplazables. Un control divisor (o "cuadro de división") del marco de ventana, situado junto a las barras de desplazamiento, permite ajustar los tamaños relativos de los paneles. Cada panel es una vista en el mismo documento. En los divisores "dinámicos", las vistas son de la misma clase, como se muestra en la parte b de la ilustración Interfaces de usuario de varias vistas. En los divisores "estáticos", las vistas pueden pertenecer a clases diferentes. Las ventanas divisoras de ambos tipos son compatibles con la clase [CSplitterWnd](../mfc/reference/csplitterwnd-class.md).  
  
 Las ventanas divisoras dinámicas, con vistas de la misma clase, permiten dividir una ventana en múltiples paneles a placer y, después, desplazarse por esos paneles para ver diferentes partes del documento. También se pueden eliminar las divisiones de ventana para quitar las vistas adicionales. Las ventanas divisoras agregadas a [Scribble sample](../visual-cpp-samples.md) (Ejemplo de Scribble) son un ejemplo. En dicho tema se detalla la técnica para crear ventanas divisoras dinámicas. Se muestra una ventana divisora dinámica en la parte b de la ilustración Interfaces de usuario de varias vistas.  
  
 Las ventanas divisoras estáticas, con vistas de clases distintas, comienzan con la división de la ventana en varios paneles, cada uno con un propósito diferente. Por ejemplo, en el editor de mapa de bits de Visual C++, la ventana de imagen muestra dos paneles en paralelo. El panel de la izquierda muestra una imagen en tamaño real del mapa de bits, mientras que el de la derecha muestra una imagen ampliada o agrandada del mismo mapa de bits. Los paneles están separados por una "barra divisora" que se puede arrastrar para cambiar el tamaño relativo de los paneles. Se muestra una ventana divisora estática en la parte c de la ilustración Interfaces de usuario de varias vistas.  
  
 Para obtener más información, vea la clase [CSplitterWnd](../mfc/reference/csplitterwnd-class.md) en *MFC Reference* (Referencia de MFC), así como [MFC Samples](../visual-cpp-samples.md)(Ejemplos de MFC).  
  
## <a name="see-also"></a>Vea también  
 [Arquitectura documento/vista](../mfc/document-view-architecture.md)

