---
title: "Documentos activos en Internet | Microsoft Docs"
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
  - "documentos activos [C++], crear"
  - "documentos activos [C++], pasos de programación"
  - "documentos activos [C++], utilizar asistentes para aplicaciones"
  - "asistentes para aplicaciones [C++]"
  - "asistentes para aplicaciones [C++], documentos activos"
ms.assetid: a46bd8a0-e27a-4116-b1bf-dacdb7ae78d1
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Documentos activos en Internet
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los documentos activos proporcionan una extensión de los objetos incrustados tradicionales.  Los documentos activos pueden ser de varias páginas y se muestran en el área cliente completa.  Haga la negociación tradicional de menú, y pueden ser en contexto editado así como en una ventana abierta en la aplicación de servidor.  En lugar de mostrar como un rectángulo pequeño rodeado por un borde tramado, documentos activos es cuadro completo y activa siempre en contexto.  
  
 Los documentos activos se pueden ver en un contenedor como Microsoft Office binder, que proporciona una manera de crear un documento compuesto compuesta de distintos tipos de documento como Excel, word, y el tipo de documento personalizado, que puede ser cuadro completo editado.  Los documentos activos también se pueden mostrar en un explorador como Microsoft Internet Explorer, que es un contenedor de documentos activos.  
  
 **Entre las ventajas del documento activo:**  
  
-   Los documentos pueden ser cuadro completo vean, en la ventana completa del cliente.  
  
-   Los documentos se pueden abrir en una ventana de la aplicación independiente.  
  
     Para que el documento abierto, la aplicación auxiliar debe existir en el cliente, o se descargue por separado antes de que la aplicación pueda ejecutarse.  Un visor se puede escribir para proporcionar funcionalidad limitada \(la palabra, PowerPoint, y Excel proporcionan visores para los documentos\).  La versión completa de la aplicación puede proporcionar compatibilidad completa con la edición.  
  
-   Los documentos son siempre activa en contexto.  
  
-   Comandos de menú invocados del contenedor se pueden distribuir al documento.  
  
-   Los documentos se pueden ver en un explorador web.  Esto proporciona la integración sin problemas entre documentos y otras páginas Web.  
  
     Un usuario puede examinar una página Web HTML, después una hoja de cálculo de Excel, y a continuación a un documento que ha escrito utilizando la compatibilidad de MFC con los documentos activos.  El usuario puede navegar mediante la interfaz web familiarizado, como el explorador sin problemas entre los menús y las vistas de una página HTML, Excel, y el documento de la aplicación.  
  
-   Todas las aplicaciones se muestra en un cuadro común.  
  
## Requisitos para los documentos activos  
 Las interfaces que se enumeran en la tabla bajo las interfaces de inclusión necesarias ya para servidores incrustados y de varias nuevas interfaces específicas de los documentos activos.  MFC proporciona implementaciones predeterminadas de la mayoría de estas interfaces en la clase de [COleServerDoc](../mfc/reference/coleserverdoc-class.md) .  
  
|Un documento que…|Implementa estas interfaces|  
|-----------------------|---------------------------------|  
|Utiliza archivos compuestos como el mecanismo de almacenamiento.|`IPersistStorage`.|  
|Admite las características básicas de incrustación de documentos activos, incluidos crean desde un archivo.|`IPersistFile`, `IOleObject` y `IDataObject`.|  
|Admite la activación en contexto.|`IOleInPlaceObject` y `IOleInPlaceActiveObject` \(mediante `IOleInPlaceSite` de contenedor y las interfaces de **IOleInPlaceFrame** \).|  
|Admite las extensiones del documento activo que comprenden estas nuevas interfaces.  Algunas interfaces son opcionales.|`IOleDocument`, `IOleDocumentView`, `IOleCommandTarget` y `IPrint`.|  
  
 MFC proporciona compatibilidad para compatibilidad incrustado existente del servidor que extiende a los documentos activos.  
  
## Agregar compatibilidad del documento activo a una nueva aplicación  
 Para crear una aplicación con el documento activo: En el Asistente para aplicaciones MFC, en la página de **Compatib. doc. compuestos** , bajo “compatibilidad seleccione de documento compuesto” recomendaciones **Full\-server** o **Container\/Full\-server**y, bajo “opciones adicionales seleccionar” active la casilla para **Active document server**.  
  
##  <a name="_core_convert_an_existing_mfc_in.2d.process_server_to_an_activex_document_server"></a> Convierta en un servidor en proceso existente MFC a un Servidor de documentos activos  
 Si la aplicación se creó con una versión de Visual C\+\+ antes de la versión 4.2 y ya es un servidor en proceso, puede agregar compatibilidad de documentos activos realizar cambios a las clases siguientes:  
  
|Tipo de clase|Derivado antes de|Cambio a derivar de|  
|-------------------|-----------------------|-------------------------|  
|Cuadro en contexto|`COleIPFrameWnd`|**COleDocIPFrameWnd**|  
|Elemento|`COleServerItem`|`CDocObjectServerItem`|  
  
 También cambiará cómo se escribe en el registro, y realizará varios otros cambios.  Si la aplicación no tiene actualmente ningún componente COM compatibilidad, puede agregar compatibilidad de servidor ejecutando el Asistente para aplicaciones e integración del código componente\- concreto COM con la aplicación existente.  
  
## Vea también  
 [Tareas de programación para Internet de MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)