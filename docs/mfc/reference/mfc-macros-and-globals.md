---
title: Macros MFC y variables globales | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- MFC, global functions and variables
- MFC, macros
- global functions, MFC
- macros, MFC
- global functions
- global variables, MFC
- Afx naming convention
- macros
ms.assetid: add4e33f-0e62-4d27-be14-896cb8675d22
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d26b374e233326ac5acc97486edc8d38e6bf5d81
ms.openlocfilehash: 75db28c7be1ab497ba9656136d22b114b488c4ae
ms.lasthandoff: 02/24/2017

---
# <a name="mfc-macros-and-globals"></a>Macros y variables globales de MFC
La biblioteca MFC (Microsoft Foundation Class) se puede dividir en dos secciones principales: (1) clases MFC y (2) macros y funciones globales. Si una función o una variable no es miembro de una clase, es una función o una variable global.  
  
 La biblioteca MFC y Active Template Library (ATL) comparten macros de conversión de cadenas. Para obtener más información, consulte [Macros de conversión de cadena](../../atl/reference/string-conversion-macros.md) en la documentación de ATL.  
  
 Las macros y funciones globales de MFC proporcionan funcionalidad en las categorías siguientes.  
  
## <a name="general-mfc"></a>MFC general  
  
-   [Tipos de datos](../../mfc/reference/data-types-mfc.md)  
  
-   [Conversión de tipos de objetos de clase MFC](../../mfc/reference/type-casting-of-mfc-class-objects.md)  
  
-   [Servicios de modelo de objetos en tiempo de ejecución](../../mfc/reference/run-time-object-model-services.md)  
  
-   [Servicios de diagnóstico](../../mfc/reference/diagnostic-services.md)  
  
-   [Procesamiento de excepciones](../../mfc/reference/exception-processing.md)  
  
-   [Formato CString y presentación del cuadro de mensaje](../../mfc/reference/cstring-formatting-and-message-box-display.md)  
  
-   [Mapas de mensajes](../../mfc/reference/message-map-macros-mfc.md)  
  
-   [Información de la aplicación y administración](../../mfc/reference/application-information-and-management.md)  
  
-   [Identificadores de comando y de ventana estándar](../../mfc/reference/standard-command-and-window-ids.md)  
  
-   [Aplicaciones auxiliares de clase de colección](../../mfc/reference/collection-class-helpers.md)  
  
-   [Funciones de mapa de bits grises o interpoladas](../../mfc/reference/gray-and-dithered-bitmap-functions.md)  
  
-   [Rutinas de intercambio (DDX) de datos de cuadro de diálogo estándar](../../mfc/reference/standard-dialog-data-exchange-routines.md)  
  
-   [Rutinas de validación (DDV) de datos de cuadro de diálogo estándar](../../mfc/reference/standard-dialog-data-validation-routines.md)  
  
-   [Mensajes AFX](../../mfc/reference/afx-messages.md)  
  
-   [Estilos de Control de barra de herramientas](../../mfc/reference/toolbar-control-styles.md)  
  
-   [Cmfcimagepaintarea (enumeración)](cmfcimagepaintarea-image-edit-mode-enumeration.md)  

  
## <a name="database"></a>Base de datos  
  
-   [Funciones de intercambio de campos (RFX) Registro](../../mfc/reference/record-field-exchange-functions.md) y [funciones de intercambio masivo de campos de registro (RFX masivo)](../../mfc/reference/record-field-exchange-functions.md) para las clases ODBC de MFC  
  
-   [Funciones de intercambio (DFX) de campos de registro](../../mfc/reference/record-field-exchange-functions.md) para las clases DAO de MFC  
  
-   [Funciones de intercambio de datos de cuadro de diálogo (DDX) para CRecordView y CDaoRecordView](../../mfc/reference/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md) (clases ODBC de MFC y DAO)  
  
-   [Funciones de intercambio (DDX) de datos de cuadro de diálogo para controles OLE](../../mfc/reference/dialog-data-exchange-functions-for-ole-controls.md)  
  
-   [Macros y funciones globales para ayudar a llamar directamente a funciones de API de Open Database Connectivity (ODBC)](../../mfc/reference/database-macros-and-globals.md)  
  
-   [Inicialización del motor de base de datos DAO y terminación](../../mfc/reference/dao-database-engine-initialization-and-termination.md)  
  
## <a name="internet"></a>Internet  
  
-   [Variables globales de análisis de direcciones URL de Internet](../../mfc/reference/internet-url-parsing-globals.md)  
  
## <a name="dhtml--dhtml-event-maps"></a>Mapas de eventos DHTML y DHTML  
  
-   [Macros de auxiliar (DDX) de intercambio de datos de cuadro de diálogo DHTML](../../mfc/reference/ddx-dhtml-helper-macros.md)  
  
-   [Mapas de eventos DHTML](../../mfc/reference/dhtml-event-maps.md)  
  
## <a name="ole"></a>OLE  
  
-   [Inicialización de OLE](../../mfc/reference/ole-initialization.md)  
  
-   [Control de la aplicación](../../mfc/reference/application-control.md)  
  
-   [Mapas de envío](../../mfc/reference/dispatch-maps.md)  
  
 Además, MFC proporciona una función denominada [AfxEnableControlContainer](http://msdn.microsoft.com/library/7aa0b9d2-5329-4bc3-9d41-856e30fe2c2b) que habilita cualquier contenedor OLE desarrollado con MFC 4.0 para son totalmente compatibles con los controles OLE incrustados.  
  
## <a name="ole-controls"></a>Controles OLE  
  
-   [Constantes de tipo de parámetro Variant](../../mfc/reference/variant-parameter-type-constants.md)  
  
-   [Acceso a la biblioteca de tipos](../../mfc/reference/type-library-access.md)  
  
-   [Páginas de propiedades](../../mfc/reference/property-pages-mfc.md)  
  
-   [Mapas de eventos](../../mfc/reference/event-maps.md)  
  
-   [Mapas de receptor de eventos](../../mfc/reference/event-sink-maps.md)  
  
-   [Mapas de conexiones](../../mfc/reference/connection-maps.md)  
  
-   [Registrar controles OLE](../../mfc/reference/registering-ole-controls.md)  
  
-   [Generadores de clases y licencias](../../mfc/reference/class-factories-and-licensing.md)  
  
-   [Persistencia de los controles OLE](../../mfc/reference/persistence-of-ole-controls.md)  
  
 En la primera parte de esta sección se explica brevemente cada una de las categorías anteriores y se enumera las funciones globales y macros de la categoría, junto con una descripción breve de la funcionalidad. A continuación se encuentran las descripciones de las funciones globales, las variables globales y las macros en la biblioteca MFC.  
  
> [!NOTE]
>  Muchas funciones globales comienzan con el prefijo “Afx”, pero algunas, por ejemplo, las funciones de intercambio de datos de cuadro de diálogo (DDX) y muchas de las funciones de base de datos, no siguen esta convención. Todas las variables globales comienzan con el prefijo "afx". Las macros no comienzan con ningún prefijo concreto, sino que se escriben en letras mayúsculas.  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../mfc/class-library-overview.md)




