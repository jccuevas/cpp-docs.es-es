---
title: Clases de cuadro de diálogo
ms.date: 11/04/2016
f1_keywords:
- vc.classes.dialog
helpviewer_keywords:
- property sheet classes
- dialog box classes
- OLE common dialog classes
- common dialog classes [MFC]
- tab dialog boxes
ms.assetid: db75da23-4eff-4c6c-beae-79cf046fbce9
ms.openlocfilehash: 2399b27fc081dcc810277079729b0e62ef80d603
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616949"
---
# <a name="dialog-box-classes"></a>Clases de cuadro de diálogo

`CDialog`La clase y sus clases derivadas encapsulan la funcionalidad del cuadro de diálogo. Dado que un cuadro de diálogo es un tipo especial de ventana, `CDialog` se deriva de `CWnd` . Derive las clases de cuadro de diálogo de `CDialog` o use una de las clases de cuadro de diálogo comunes para los cuadros de diálogo estándar, como abrir o guardar un archivo, imprimir, seleccionar una fuente o un color, iniciar una operación de búsqueda y reemplazo, o realizar varias operaciones relacionadas con OLE.

[CDialog](reference/cdialog-class.md)<br/>
La clase base para todos los cuadros de diálogo, tanto modal como no modal.

[CDataExchange](reference/cdataexchange-class.md)<br/>
Proporciona información de validación e intercambio de datos para los cuadros de diálogo.

## <a name="common-dialogs"></a>Cuadros de diálogo comunes

Estas clases de cuadro de diálogo encapsulan los cuadros de diálogo comunes de Windows. Proporcionan implementaciones fáciles de usar de cuadros de diálogo complicados.

[CCommonDialog](reference/ccommondialog-class.md)<br/>
Clase base para todos los cuadros de diálogo comunes.

[CFileDialog](reference/cfiledialog-class.md)<br/>
Proporciona un cuadro de diálogo estándar para abrir o guardar un archivo.

[CColorDialog](reference/ccolordialog-class.md)<br/>
Proporciona un cuadro de diálogo estándar para seleccionar un color.

[CFontDialog](reference/cfontdialog-class.md)<br/>
Proporciona un cuadro de diálogo estándar para seleccionar una fuente.

[CFindReplaceDialog](reference/cfindreplacedialog-class.md)<br/>
Proporciona un cuadro de diálogo estándar para una operación de búsqueda y reemplazo.

[CPrintDialog](reference/cprintdialog-class.md)<br/>
Proporciona un cuadro de diálogo estándar para imprimir un archivo.

[CPrintDialogEx](reference/cprintdialogex-class.md)<br/>
Proporciona una hoja de propiedades de impresión de Windows.

[CPageSetupDialog](reference/cpagesetupdialog-class.md)<br/>
Encapsula los servicios proporcionados por el cuadro de diálogo de configuración de página común de Windows con compatibilidad adicional para configurar y modificar los márgenes de impresión.

## <a name="ole-common-dialogs"></a>Cuadros de diálogo comunes de OLE

OLE agrega varios cuadros de diálogo comunes a Windows. Estas clases encapsulan los cuadros de diálogo comunes de OLE.

[COleDialog](reference/coledialog-class.md)<br/>
Lo usa el marco de trabajo para contener implementaciones comunes para todos los cuadros de diálogo de OLE. Todas las clases de cuadro de diálogo de la categoría interfaz de usuario se derivan de esta clase base. `COleDialog`no se puede usar directamente.

[COleInsertDialog](reference/coleinsertdialog-class.md)<br/>
Muestra el cuadro de diálogo Insertar objeto, la interfaz de usuario estándar para insertar nuevos elementos vinculados OLE o incrustados.

[COlePasteSpecialDialog](reference/colepastespecialdialog-class.md)<br/>
Muestra el cuadro de diálogo Pegar especial, la interfaz de usuario estándar para implementar el comando Editar pegado especial.

[COleLinksDialog](reference/colelinksdialog-class.md)<br/>
Muestra el cuadro de diálogo Editar vínculos, la interfaz de usuario estándar para modificar información sobre los elementos vinculados.

[COleChangeIconDialog](reference/colechangeicondialog-class.md)<br/>
Muestra el cuadro de diálogo Cambiar icono, la interfaz de usuario estándar para cambiar el icono asociado a un elemento OLE incrustado o vinculado.

[COleConvertDialog](reference/coleconvertdialog-class.md)<br/>
Muestra el cuadro de diálogo convertir, la interfaz de usuario estándar para convertir elementos OLE de un tipo a otro.

[COlePropertiesDialog](reference/colepropertiesdialog-class.md)<br/>
Encapsula el cuadro de diálogo Propiedades comunes de OLE de Windows. Los cuadros de diálogo Propiedades comunes de OLE proporcionan una manera sencilla de mostrar y modificar las propiedades de un elemento de documento OLE de una manera coherente con los estándares de Windows.

[COleUpdateDialog](reference/coleupdatedialog-class.md)<br/>
Muestra el cuadro de diálogo actualizar, la interfaz de usuario estándar para actualizar todos los vínculos de un documento. El cuadro de diálogo contiene un indicador de progreso para indicar cómo se completa el procedimiento de actualización.

[COleChangeSourceDialog](reference/colechangesourcedialog-class.md)<br/>
Muestra el cuadro de diálogo cambiar origen, la interfaz de usuario estándar para cambiar el destino o el origen de un vínculo.

[COleBusyDialog](reference/colebusydialog-class.md)<br/>
Muestra los cuadros de diálogo servidor ocupado y servidor que no responde, la interfaz de usuario estándar para administrar las llamadas a aplicaciones ocupadas. Normalmente se muestra automáticamente mediante la implementación de [COleMessageFilter](reference/colemessagefilter-class.md) .

## <a name="property-sheet-classes"></a>Clases de hoja de propiedades

Las clases de hoja de propiedades permiten a las aplicaciones utilizar hojas de propiedades, también conocidas como cuadros de diálogo con pestañas. Las hojas de propiedades son una manera eficaz de organizar un gran número de controles en un solo cuadro de diálogo.

[CPropertyPage](reference/cpropertypage-class.md)<br/>
Proporciona las páginas individuales dentro de una hoja de propiedades. Derive una clase de `CPropertyPage` por cada página que se va a agregar a la hoja de propiedades.

[CPropertySheet](reference/cpropertysheet-class.md)<br/>
Proporciona el marco para varias páginas de propiedades. Derive la clase de hoja de propiedades de `CPropertySheet` para implementar rápidamente sus hojas de propiedades.

[COlePropertyPage](reference/colepropertypage-class.md)<br/>
Muestra las propiedades de un control OLE en una interfaz gráfica, similar a un cuadro de diálogo.

## <a name="html-based-dialog-classes"></a>Clases de cuadro de diálogo basadas en HTML

[CDHtmlDialog](reference/cdhtmldialog-class.md)<br/>
Se utiliza para crear cuadros de diálogo que implementan su interfaz de usuario con HTML en lugar de recursos de cuadro de diálogo.

[CMultiPageDHtmlDialog](reference/cmultipagedhtmldialog-class.md)<br/>
Muestra varias páginas HTML secuencialmente y controla los eventos de cada página.

## <a name="related-classes"></a>Clases relacionadas

Estas clases no son cuadros de diálogo por se, pero usan plantillas de cuadro de diálogo y tienen gran parte del comportamiento de los cuadros de diálogo.

[CDialogBar](reference/cdialogbar-class.md)<br/>
Barra de control que se basa en una plantilla de cuadro de diálogo.

[CFormView](reference/cformview-class.md)<br/>
Vista de desplazamiento cuyo diseño se define en una plantilla de cuadro de diálogo. Derive una clase de `CFormView` para implementar una interfaz de usuario basada en una plantilla de cuadro de diálogo.

[CDaoRecordView](reference/cdaorecordview-class.md)<br/>
Proporciona una vista de formulario conectada directamente a un objeto de conjunto de registros de objetos de acceso a datos (DAO). Al igual que todas las vistas de formulario, `CDaoRecordView` se basa en una plantilla de cuadro de diálogo.

[CRecordView](reference/crecordview-class.md)<br/>
Proporciona una vista de formulario conectada directamente a un objeto de conjunto de registros ODBC (Conectividad abierta de bases de datos). Al igual que todas las vistas de formulario, `CRecordView` se basa en una plantilla de cuadro de diálogo.

[CPrintInfo](reference/cprintinfo-structure.md)<br/>
Estructura que contiene información sobre un trabajo de impresión o de vista previa de impresión. Lo utiliza la arquitectura de impresión de [CView](reference/cview-class.md).

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)
