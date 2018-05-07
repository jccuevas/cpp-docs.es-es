---
title: Clases de cuadro de diálogo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.dialog
dev_langs:
- C++
helpviewer_keywords:
- property sheet classes
- dialog box classes
- OLE common dialog classes
- common dialog classes [MFC]
- tab dialog boxes
ms.assetid: db75da23-4eff-4c6c-beae-79cf046fbce9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60d33289d8025d7cdcaf4f6f69062230730b958c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="dialog-box-classes"></a>Clases de cuadro de diálogo
Clase `CDialog` y sus clases derivadas encapsulan la funcionalidad de cuadro de diálogo. Puesto que un cuadro de diálogo es un tipo especial de ventana, `CDialog` se deriva de `CWnd`. Derivar las clases de cuadro de diálogo de `CDialog` o use una de las clases de cuadro de diálogo comunes para los cuadros de diálogo estándar, como abrir o guardar un archivo, impresión, seleccionando una fuente o un color, iniciar una operación de búsqueda y reemplazo, o bien realizar diversas relacionadas con OLE operaciones.  
  
 [CDialog](../mfc/reference/cdialog-class.md)  
 La clase base para todos los cuadros de diálogo, modales y no modales.  
  
 [CDataExchange](../mfc/reference/cdataexchange-class.md)  
 Proporciona información de intercambio y validación de datos de cuadros de diálogo.  
  
## <a name="common-dialogs"></a>Cuadros de diálogo comunes  
 Estas clases de cuadro de diálogo encapsulan los cuadros de diálogo comunes de Windows. Proporcionan implementaciones fácil de usar los cuadros de diálogo complicados.  
  
 [CCommonDialog](../mfc/reference/ccommondialog-class.md)  
 Clase base para todos los cuadros de diálogo comunes.  
  
 [CFileDialog](../mfc/reference/cfiledialog-class.md)  
 Proporciona un cuadro de diálogo estándar para abrir o guardar un archivo.  
  
 [CColorDialog](../mfc/reference/ccolordialog-class.md)  
 Proporciona un cuadro de diálogo para seleccionar un color.  
  
 [CFontDialog](../mfc/reference/cfontdialog-class.md)  
 Proporciona un cuadro de diálogo para seleccionar una fuente.  
  
 [CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)  
 Proporciona un cuadro de diálogo estándar para una operación de búsqueda y reemplazo.  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 Proporciona un cuadro de diálogo estándar para imprimir un archivo.  
  
 [CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)  
 Proporciona una hoja de propiedades de impresión de Windows.  
  
 [CPageSetupDialog](../mfc/reference/cpagesetupdialog-class.md)  
 Encapsula los servicios proporcionados por el cuadro de diálogo Configurar página común de Windows con compatibilidad adicional para configurar y modificar los márgenes de impresión.  
  
## <a name="ole-common-dialogs"></a>Cuadros de diálogo comunes OLE  
 OLE agrega varios cuadros de diálogo comunes en Windows. Estas clases encapsulan los cuadros de diálogo comunes OLE.  
  
 [COleDialog](../mfc/reference/coledialog-class.md)  
 Utiliza el marco de trabajo para contener las implementaciones comunes para todos los cuadros de diálogo OLE. Todas las clases de cuadro de diálogo de la categoría de la interfaz de usuario se derivan de esta clase base. `COleDialog` no se puede usar directamente.  
  
 [Clase COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)  
 Muestra el cuadro de diálogo Insertar objeto, la interfaz de usuario estándar para insertar nuevo OLE elementos vinculados o incrustados.  
  
 [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)  
 Muestra el cuadro de diálogo Pegado especial, la interfaz de usuario estándar para implementar el comando Editar Pegado especial.  
  
 [COleLinksDialog](../mfc/reference/colelinksdialog-class.md)  
 Muestra el cuadro de diálogo Editar vínculos, la interfaz de usuario estándar para modificar información sobre los elementos vinculados.  
  
 [Clase COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)  
 Muestra el cuadro de diálogo Cambiar icono, la interfaz de usuario estándar para cambiar el icono asociado a un OLE incrustado o el elemento vinculado.  
  
 [Clase COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)  
 Muestra el cuadro de diálogo de Convert, la interfaz de usuario estándar para convertir los elementos OLE de un tipo a otro.  
  
 [COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)  
 Encapsula el cuadro de diálogo de propiedades de OLE común de Windows. Cuadros de diálogo comunes OLE propiedades proporcionan una manera sencilla de mostrar y modificar las propiedades de un elemento de documento OLE de manera coherente con los estándares de Windows.  
  
 [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)  
 Muestra el cuadro de diálogo de actualización, la interfaz de usuario estándar para actualizar todos los vínculos en un documento. El cuadro de diálogo contiene un indicador de progreso para indicar la distancia es el procedimiento de actualización hasta su finalización.  
  
 [COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)  
 Muestra el cuadro de diálogo Cambiar origen, la interfaz de usuario estándar para cambiar el destino o el origen de un vínculo.  
  
 [Clase COleBusyDialog](../mfc/reference/colebusydialog-class.md)  
 Muestra los cuadros de diálogo servidor ocupado y el servidor no responde, la interfaz de usuario estándar para controlar las llamadas a las aplicaciones ocupadas. Habitualmente se muestra automáticamente el [COleMessageFilter](../mfc/reference/colemessagefilter-class.md) implementación.  
  
## <a name="property-sheet-classes"></a>Clases de hoja de propiedades  
 Las clases de hoja de propiedades permiten que las aplicaciones usar hojas de propiedades, los cuadros de diálogo también se denomina con pestañas. Hojas de propiedades son una manera eficaz para organizar un gran número de controles en un único cuadro de diálogo.  
  
 [CPropertyPage](../mfc/reference/cpropertypage-class.md)  
 Proporciona las páginas individuales dentro de una hoja de propiedades. Derivar una clase de `CPropertyPage` para cada página que se va a agregar a la hoja de propiedades.  
  
 [CPropertySheet](../mfc/reference/cpropertysheet-class.md)  
 Proporciona el marco para varias páginas de propiedades. Derive la clase de hoja de propiedades de `CPropertySheet` para implementar rápidamente sus hojas de propiedades.  
  
 [COlePropertyPage](../mfc/reference/colepropertypage-class.md)  
 Muestra las propiedades de una OLE controlan en una interfaz gráfica, similar a un cuadro de diálogo.  
  
## <a name="html-based-dialog-classes"></a>Clases de cuadro de diálogo basado en HTML  
 [CDHtmlDialog](../mfc/reference/cdhtmldialog-class.md)  
 Se utiliza para crear cuadros de diálogo que implementan la interfaz de usuario con recursos HTML en lugar de cuadro de diálogo.  
  
 [CMultiPageDHtmlDialog](../mfc/reference/cmultipagedhtmldialog-class.md)  
 Muestra varias páginas HTML secuencialmente y administra los eventos de cada página.  
  
## <a name="related-classes"></a>Clases relacionadas  
 Estas clases no son cuadros de diálogo de sí mismo, pero usan plantillas de cuadro de diálogo y tienen gran parte del comportamiento de los cuadros de diálogo.  
  
 [CDialogBar](../mfc/reference/cdialogbar-class.md)  
 Una barra de controles que se basa en una plantilla de cuadro de diálogo.  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 Una vista de desplazamiento cuyo diseño está definido en una plantilla de cuadro de diálogo. Derivar una clase de `CFormView` para implementar una interfaz de usuario basada en una plantilla de cuadro de diálogo.  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 Proporciona una forma Vista conectada directamente a un objeto de conjunto de registros de objetos de acceso a datos (DAO). Al igual que todas las vistas de formulario y un `CDaoRecordView` se basa en una plantilla de cuadro de diálogo.  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 Proporciona una forma Vista conectada directamente a un objeto de conjunto de registros de Open Database Connectivity (ODBC). Al igual que todas las vistas de formulario y un `CRecordView` se basa en una plantilla de cuadro de diálogo.  
  
 [CPrintInfo](../mfc/reference/cprintinfo-structure.md)  
 Una estructura que contiene información acerca de un trabajo de impresión o vista preliminar. Utilizado por la arquitectura de impresión de [CView](../mfc/reference/cview-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

