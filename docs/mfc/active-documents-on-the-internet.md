---
title: Documentos activos en Internet | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], creating
- application wizards [MFC], active documents
- active documents [MFC], programming steps
- application wizards [MFC]
- active documents [MFC], using application wizards
ms.assetid: a46bd8a0-e27a-4116-b1bf-dacdb7ae78d1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0980f048b9be411308b159dea0ceaa71f8eee563
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2018
---
# <a name="active-documents-on-the-internet"></a>Documentos activos en Internet
Documentos activos proporcionan una extensión para los objetos incrustados tradicionales. Los documentos activos pueden ser varias páginas y se muestran en el área de clientes en su totalidad. No tradicional negociación de menús y se pueden editar en contexto, así como en una ventana abierta en la aplicación de servidor. En lugar de mostrar como un pequeño rectángulo rodeado por un borde sombreado, documentos activos son un marco completo y siempre en el contexto activo.  
  
 Documentos activos se pueden ver en un contenedor como el cuaderno de Office de Microsoft, que proporciona una manera de crear un documento compuesto consta de varios tipos de documentos como Excel, Word, y su tipo de documento personalizadas, cada uno de los cuales puede ser editado un marco completo. Documentos activos también puede mostrarse en un explorador como Microsoft Internet Explorer, que es un contenedor de documento activo.  
  
 **Documento activo ventajas incluyen:**  
  
-   Se pueden ver los documentos de un marco completo, en la ventana completa del cliente.  
  
-   Se pueden abrir documentos en una ventana de aplicación diferente.  
  
     Para el documento para abrirlo, la aplicación auxiliar debe existir en el cliente, o descargarse por separado antes de ejecutar la aplicación. Puede escribirse un visor para proporcionar una funcionalidad limitada (Word, PowerPoint y Excel proporcionan visores para sus documentos). La versión completa de la aplicación puede proporcionar compatibilidad total con la edición.  
  
-   Los documentos son siempre activo en contexto.  
  
-   Comandos de menú invocados desde el contenedor se pueden enrutar a un documento.  
  
-   Documentos pueden verse en un explorador Web. Esto proporciona una perfecta integración entre los documentos y otras páginas Web.  
  
     Un usuario puede examinar una página HTML Web, a continuación, una hoja de cálculo Excel y, a continuación, a un documento que se haya creado mediante MFC compatibilidad con documentos activos. El usuario puede navegar mediante la conocida interfaz de Web, como el explorador cambia sin problemas entre los menús y vistas de una página HTML, Excel y documento de la aplicación.  
  
-   Todas las aplicaciones que se muestran en un marco común.  
  
## <a name="requirements-for-active-documents"></a>Requisitos de documentos activos  
 Las interfaces enumeradas en la tabla siguiente incluyen interfaces previamente requeridas para los servidores incrustados y varias nuevas interfaces específicas de documentos activos. MFC proporciona implementaciones predeterminadas para la mayoría de estas interfaces en el [COleServerDoc](../mfc/reference/coleserverdoc-class.md) clase.  
  
|Un documento que...|Implementa estas interfaces|  
|-------------------------|---------------------------------|  
|Utiliza archivos compuestos como mecanismo de almacenamiento.|`IPersistStorage`.|  
|Es compatible con las características básicas de incrustación de documentos activos, incluida la creación de archivo.|`IPersistFile`, `IOleObject` y `IDataObject`.|  
|Admite la activación en contexto.|`IOleInPlaceObject` y `IOleInPlaceActiveObject` (usando el contenedor `IOleInPlaceSite` y **IOleInPlaceFrame** interfaces).|  
|Es compatible con las extensiones de documentos activos que comprenden estas nuevas interfaces. Algunas interfaces son opcionales.|`IOleDocument`, `IOleDocumentView`, `IOleCommandTarget` y `IPrint`.|  
  
 MFC proporciona compatibilidad para ampliar la compatibilidad de servidor incrustado existentes para documentos activos.  
  
## <a name="add-active-document-support-to-a-new-application"></a>Agregar compatibilidad con documentos activos a una nueva aplicación  
 Para crear una nueva aplicación con compatibilidad con documentos activos: en el Asistente para aplicaciones MFC, en la **compatibilidad con documentos compuestos** página, en "compatibilidad con documentos compuestos seleccione" elija **servidor completo** o  **Contenedor o servidor completo**y en "Seleccionar opciones adicionales", active la casilla de verificación para **servidor de documentos activos**.  
  
##  <a name="_core_convert_an_existing_mfc_in.2d.process_server_to_an_activex_document_server"></a> Convertir a un servidor en proceso MFC existente en un servidor de documentos activos  
 Si la aplicación se creó con una versión de Visual C++ anteriores a la versión 4.2 y ya es un servidor en proceso, puede agregar compatibilidad con documentos activos realizando cambios en las siguientes clases:  
  
|Tipo de clase|Anteriormente se deriva de|Cambio de derivar de|  
|----------------|---------------------------|---------------------------|  
|Marco en contexto|`COleIPFrameWnd`|**COleDocIPFrameWnd**|  
|Elemento|`COleServerItem`|`CDocObjectServerItem`|  
  
 También se cambia la forma de especificar información en el registro y realizar otros cambios. Si la aplicación no tiene actualmente ninguna compatibilidad con componentes de COM, puede agregar compatibilidad con el servidor al ejecutar al Asistente para aplicaciones e integrar el código específico del componente COM con la aplicación existente.  
  
## <a name="see-also"></a>Vea también  
 [Tareas de programación de Internet MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)

