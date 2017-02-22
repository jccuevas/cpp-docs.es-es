---
title: "Macros y variables globales de MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "convención de nomenclatura Afx"
  - "funciones globales"
  - "funciones globales, MFC"
  - "variables globales, MFC"
  - "macros"
  - "macros, MFC"
  - "MFC, funciones y variables globales"
  - "MFC, macros"
ms.assetid: add4e33f-0e62-4d27-be14-896cb8675d22
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# Macros y variables globales de MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La biblioteca MFC \(Microsoft Foundation Class\) se puede dividir en dos secciones principales: \(1\) clases MFC y \(2\) macros y funciones globales.  Si una función o una variable no es miembro de una clase, es una función o una variable global.  
  
 La biblioteca MFC y Active Template Library \(ATL\) comparten macros de conversión de cadenas.  Para obtener más información, vea [String Conversion Macros](../../atl/reference/string-conversion-macros.md) en la documentación del ATL.  
  
 Las macros y funciones globales de MFC proporcionan funcionalidad en las categorías siguientes.  
  
## MFC general  
  
-   [Tipos de datos](../../mfc/reference/data-types-mfc.md)  
  
-   [Conversión de tipos de objetos de clase MFC](../../mfc/reference/type-casting-of-mfc-class-objects.md)  
  
-   [Servicios del modelo de objetos en tiempo de ejecución](../../mfc/reference/run-time-object-model-services.md)  
  
-   [Servicios de diagnóstico](../../mfc/reference/diagnostic-services.md)  
  
-   [Procesamiento de excepciones](../../mfc/reference/exception-processing.md)  
  
-   [Formato CString y presentación de cuadros de mensaje](../../mfc/reference/cstring-formatting-and-message-box-display.md)  
  
-   [Mapas de mensajes](../../mfc/reference/message-map-macros-mfc.md)  
  
-   [Información de aplicación y administración](../../mfc/reference/application-information-and-management.md)  
  
-   [Identificadores estándar de comando y de ventana](../../mfc/reference/standard-command-and-window-ids.md)  
  
-   [Aplicaciones auxiliares de clase de colección](../../mfc/reference/collection-class-helpers.md)  
  
-   [Funciones de mapa de bits interpoladas y en gris](../../mfc/reference/gray-and-dithered-bitmap-functions.md)  
  
-   [Rutinas de intercambio de datos de cuadro de diálogo estándar \(DDX\)](../../mfc/reference/standard-dialog-data-exchange-routines.md)  
  
-   [Rutinas de validación de datos de cuadro de diálogo estándar \(DDV\)](../../mfc/reference/standard-dialog-data-validation-routines.md)  
  
-   [Mensajes AFX](../../mfc/reference/afx-messages.md)  
  
-   [Estilos de control ToolBar](../../mfc/reference/toolbar-control-styles.md)  
  
-   [CMFCImagePaintArea::IMAGE\_EDIT\_MODE \(Enumeración\)](../../mfc/reference/cmfcimagepaintarea-image-edit-mode-enumeration.md)  
  
## Base de datos  
  
-   [Funciones de intercambio de campos de registro \(RFX\)](../../mfc/reference/record-field-exchange-functions.md) y [Funciones de intercambio masivo de campos de registro \(RFX masivo\)](../../mfc/reference/record-field-exchange-functions.md) para las clases ODBC de MFC  
  
-   [Funciones de intercambio de campos de registro de DAO \(DFX\)](../../mfc/reference/record-field-exchange-functions.md) para las clases DAO de MFC  
  
-   [Funciones de intercambio de datos de cuadro de diálogo \(DDX\) para CRecordView y CDaoRecordView](../../mfc/reference/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md) \(clases ODBC y DAO de MFC\)  
  
-   [Funciones de intercambio de datos de cuadro de diálogo \(DDX\) para los controles OLE](../../mfc/reference/dialog-data-exchange-functions-for-ole-controls.md)  
  
-   [Macros y funciones globales para ayudar a llamar directamente a las funciones de la API de ODBC](../../mfc/reference/database-macros-and-globals.md)  
  
-   [Inicialización y finalización del motor de base de datos de DAO](../../mfc/reference/dao-database-engine-initialization-and-termination.md)  
  
## Internet  
  
-   [Funciones globales de análisis de direcciones URL de Internet](../../mfc/reference/internet-url-parsing-globals.md)  
  
## Mapas de eventos DHTML y DHTML  
  
-   [Macros de la aplicación auxiliar de intercambio de datos de cuadro de diálogo DHTML \(DDX\)](../../mfc/reference/ddx-dhtml-helper-macros.md)  
  
-   [Mapas de eventos DHTML](../../mfc/reference/dhtml-event-maps.md)  
  
## OLE  
  
-   [Inicialización de OLE](../../mfc/reference/ole-initialization.md)  
  
-   [Control de la aplicación](../../mfc/reference/application-control.md)  
  
-   [Mapas de envío](../../mfc/reference/dispatch-maps.md)  
  
 Además, MFC proporciona una función denominada [AfxEnableControlContainer](../Topic/AfxEnableControlContainer.md) que habilita cualquier contenedor OLE desarrollado con MFC 4.0 para proporcionar compatibilidad completa con los controles OLE incrustados.  
  
## Controles OLE  
  
-   [Constantes de tipo de parámetro de variante](../../mfc/reference/variant-parameter-type-constants.md)  
  
-   [Acceso de la biblioteca de tipos](../../mfc/reference/type-library-access.md)  
  
-   [Páginas de propiedades](../../mfc/reference/property-pages-mfc.md)  
  
-   [Mapas de eventos](../../mfc/reference/event-maps.md)  
  
-   [Mapas de receptor de eventos](../../mfc/reference/event-sink-maps.md)  
  
-   [Mapas de conexiones](../../mfc/reference/connection-maps.md)  
  
-   [Registrar controles OLE](../../mfc/reference/registering-ole-controls.md)  
  
-   [Generadores de clases y licencias](../../mfc/reference/class-factories-and-licensing.md)  
  
-   [Persistencia de los controles OLE](../../mfc/reference/persistence-of-ole-controls.md)  
  
 En la primera parte de esta sección se explica brevemente cada una de las categorías anteriores y se enumera las funciones globales y macros de la categoría, junto con una descripción breve de la funcionalidad.  A continuación se encuentran las descripciones de las funciones globales, las variables globales y las macros en la biblioteca MFC.  
  
> [!NOTE]
>  Muchas funciones globales comienzan con el prefijo “Afx”, pero algunas, por ejemplo, las funciones de intercambio de datos de cuadro de diálogo \(DDX\) y muchas de las funciones de base de datos, no siguen esta convención.  Todas las variables globales comienzan con el prefijo "afx".  Las macros no comienzan con ningún prefijo concreto, sino que se escriben en letras mayúsculas.  
  
## Vea también  
 [Información general de clases](../../mfc/class-library-overview.md)