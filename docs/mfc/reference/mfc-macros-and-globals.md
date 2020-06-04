---
title: Macros y variables globales de MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, global functions and variables
- MFC, macros
- global functions, MFC
- macros, MFC
- global functions [MFC]
- global variables, MFC
- Afx naming convention
- macros
ms.assetid: add4e33f-0e62-4d27-be14-896cb8675d22
ms.openlocfilehash: ed45fc7014bda18887be6dc8fbcdff8ba9a9c5f1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373043"
---
# <a name="mfc-macros-and-globals"></a>Macros y variables globales de MFC

La biblioteca MFC (Microsoft Foundation Class) se puede dividir en dos secciones principales: (1) clases MFC y (2) macros y funciones globales. Si una función o una variable no es miembro de una clase, es una función o una variable global.

La biblioteca MFC y Active Template Library (ATL) comparten macros de conversión de cadenas. Para obtener más información, consulte Macros de [conversión](../../atl/reference/string-conversion-macros.md) de cadenas en la documentación de ATL.

Las macros y funciones globales de MFC proporcionan funcionalidad en las categorías siguientes.

## <a name="general-mfc"></a>MFC general

- [Tipos de datos](data-types-mfc.md)

- [Conversión de tipos de objetos de clase MFC](type-casting-of-mfc-class-objects.md)

- [Servicios de modelo de objetos en tiempo de ejecución](run-time-object-model-services.md)

- [Servicios de diagnóstico](diagnostic-services.md)

- [Procesamiento de excepciones](exception-processing.md)

- [Formato y presentación del cuadro de mensaje CString](cstring-formatting-and-message-box-display.md)

- [Mapas de mensajes](message-map-macros-mfc.md)

- [Mapas de delegados e interfaces](delegate-and-interface-maps.md)

- [Módulos y archivos DLL](extension-dll-macros.md)

- [Información y gestión de aplicaciones](application-information-and-management.md)

- [Cuentas estándar de comandos y ventanas](standard-command-and-window-ids.md)

- [Ayudantes de clase de colección](collection-class-helpers.md)

- [Funciones de mapa de bits grises y tramadas](gray-and-dithered-bitmap-functions.md)

- [Rutinas de intercambio de datos de cuadro de diálogo estándar (DDX)](standard-dialog-data-exchange-routines.md)

- [Rutinas de validación de datos de cuadro de diálogo estándar (DDV)](standard-dialog-data-validation-routines.md)

- [mensajes AFX](afx-messages.md)

- [Estilos de control de Barra de Herramientas](toolbar-control-styles.md)

- [CMFCImagePaintArea::IMAGE_EDIT_MODE (Enumeración)](cmfcimagepaintarea-image-edit-mode-enumeration.md)

## <a name="database"></a>Base de datos

- Funciones de intercambio de campos de [registros (RFX)](record-field-exchange-functions.md) y funciones de intercambio de campos de registros [masivos (RFX masivo)](record-field-exchange-functions.md) para las clases ODBC de MFC

- Funciones de intercambio de campos de [registros (DFX)](record-field-exchange-functions.md) para las clases DAO de MFC

- Funciones de intercambio de datos de cuadro de diálogo [(DDX) para CRecordView y CDaoRecordView](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md) (clases ODBC y DAO de MFC)

- [Funciones de intercambio de datos de cuadro de diálogo (DDX) para los controles OLE](dialog-data-exchange-functions-for-ole-controls.md)

- [Macros y funciones globales para ayudar a llamar directamente a las funciones de la API de ODBC](database-macros-and-globals.md)

- [Inicialización y terminación del motor de base de datos DAO](dao-database-engine-initialization-and-termination.md)

## <a name="internet"></a>Internet

- [Variables globales de análisis de direcciones URL de Internet](internet-url-parsing-globals.md)

## <a name="dhtml--dhtml-event-maps"></a>Mapas de eventos DHTML y DHTML

- [Macros del asistente de intercambio de datos de cuadro de diálogo DHTML (DDX)](ddx-dhtml-helper-macros.md)

- [Mapas de eventos DHTML](dhtml-event-maps.md)

## <a name="ole"></a>OLE

- [Inicialización de OLE](ole-initialization.md)

- [Control de aplicaciones](application-control.md)

- [Mapas de despacho](dispatch-maps.md)

Además, MFC proporciona una función denominada [AfxEnableControlContainer](ole-initialization.md#afxenablecontrolcontainer) que permite que cualquier contenedor OLE desarrollado con MFC 4.0 admita completamente los controles OLE incrustados.

## <a name="ole-controls"></a>Controles OLE

- [Constantes de tipo de parámetro de variante](variant-parameter-type-constants.md)

- [Acceso a la biblioteca de tipos](type-library-access.md)

- [Páginas de propiedades](property-pages-mfc.md)

- [Mapas de eventos](event-maps.md)

- [Mapas de sumideros de eventos](event-sink-maps.md)

- [Mapas de conexión](connection-maps.md)

- [Registro de controles OLE](registering-ole-controls.md)

- [Fábricas de clases y licencias](class-factories-and-licensing.md)

- [Persistencia de controles OLE](persistence-of-ole-controls.md)

En la primera parte de esta sección se explica brevemente cada una de las categorías anteriores y se enumera las funciones globales y macros de la categoría, junto con una descripción breve de la funcionalidad. A continuación se encuentran las descripciones de las funciones globales, las variables globales y las macros en la biblioteca MFC.

> [!NOTE]
> Muchas funciones globales comienzan con el prefijo “Afx”, pero algunas, por ejemplo, las funciones de intercambio de datos de cuadro de diálogo (DDX) y muchas de las funciones de base de datos, no siguen esta convención. Todas las variables globales comienzan con el prefijo "afx". Las macros no comienzan con ningún prefijo concreto, sino que se escriben en letras mayúsculas.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../mfc/class-library-overview.md)
