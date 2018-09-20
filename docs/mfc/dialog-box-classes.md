---
title: Clases de cuadro de diálogo | Microsoft Docs
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
ms.openlocfilehash: 177e6f7ab0787ba3eccfe963f08963697747145e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399514"
---
# <a name="dialog-box-classes"></a>Clases de cuadro de diálogo

Clase `CDialog` y sus clases derivadas encapsulan la funcionalidad de cuadro de diálogo. Puesto que un cuadro de diálogo es un tipo especial de ventana, `CDialog` se deriva de `CWnd`. Derivar clases de cuadro de diálogo `CDialog` o use una de las clases de cuadro de diálogo comunes de cuadros de diálogo estándar, por ejemplo, al abrir o guardar un archivo, impresión, seleccionar una fuente o color, iniciar una operación de búsqueda y reemplazo, o realizan diversas relacionadas con OLE operaciones.

[CDialog](../mfc/reference/cdialog-class.md)<br/>
La clase base para todos los cuadros de diálogo modales y no modales.

[CDataExchange](../mfc/reference/cdataexchange-class.md)<br/>
Proporciona información de intercambio y validación de datos de cuadros de diálogo.

## <a name="common-dialogs"></a>Cuadros de diálogo comunes

Estas clases de cuadro de diálogo encapsulan los cuadros de diálogo comunes de Windows. Proporcionan implementaciones para uso de cuadros de diálogo complicada.

[CCommonDialog](../mfc/reference/ccommondialog-class.md)<br/>
Clase base para todos los cuadros de diálogo comunes.

[CFileDialog](../mfc/reference/cfiledialog-class.md)<br/>
Proporciona un cuadro de diálogo estándar para abrir o guardar un archivo.

[CColorDialog](../mfc/reference/ccolordialog-class.md)<br/>
Proporciona un cuadro de diálogo estándar para seleccionar un color.

[CFontDialog](../mfc/reference/cfontdialog-class.md)<br/>
Proporciona un cuadro de diálogo estándar para seleccionar una fuente.

[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)<br/>
Proporciona un cuadro de diálogo estándar para una operación de búsqueda y reemplazo.

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
Proporciona un cuadro de diálogo estándar para imprimir un archivo.

[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)<br/>
Proporciona una hoja de propiedades de impresión de Windows.

[CPageSetupDialog](../mfc/reference/cpagesetupdialog-class.md)<br/>
Encapsula los servicios proporcionados por el cuadro de diálogo Configurar página común de Windows con compatibilidad adicional para configurar y modificar los márgenes de impresión.

## <a name="ole-common-dialogs"></a>Cuadros de diálogo comunes OLE

OLE agrega varios cuadros de diálogo comunes en Windows. Estas clases encapsulan los cuadros de diálogo comunes OLE.

[COleDialog](../mfc/reference/coledialog-class.md)<br/>
Usa el marco de trabajo para contener las implementaciones comunes para todos los cuadros de diálogo OLE. Todas las clases de cuadro de diálogo en la categoría de la interfaz de usuario se derivan de esta clase base. `COleDialog` no se puede usar directamente.

[COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)<br/>
Muestra el cuadro de diálogo Insertar objeto la interfaz de usuario estándar para insertar nuevo OLE elementos vinculados o incrustados.

[COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)<br/>
Muestra el cuadro de diálogo Pegado especial, la interfaz de usuario estándar para implementar el comando Editar Pegado especial.

[COleLinksDialog](../mfc/reference/colelinksdialog-class.md)<br/>
Muestra el cuadro de diálogo Editar vínculos, la interfaz de usuario estándar para modificar la información sobre los elementos vinculados.

[COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)<br/>
Muestra el cuadro de diálogo Cambiar icono, la interfaz de usuario estándar para cambiar el icono asociado a un OLE incrustado o el elemento vinculado.

[COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)<br/>
Muestra el cuadro de diálogo Convertir, la interfaz de usuario estándar para convertir los elementos OLE.

[COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)<br/>
Encapsula el cuadro de diálogo Propiedades de OLE común de Windows. Cuadros de diálogo comunes OLE propiedades proporcionan una manera fácil para mostrar y modificar las propiedades de un elemento de documento OLE de manera coherente con los estándares de Windows.

[COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)<br/>
Muestra el cuadro de diálogo de actualización, la interfaz de usuario estándar para actualizar todos los vínculos en un documento. El cuadro de diálogo contiene un indicador de progreso para indicar cómo cerrar el procedimiento de actualización es hasta su finalización.

[COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)<br/>
Muestra el cuadro de diálogo Cambiar origen, la interfaz de usuario estándar para cambiar el destino o el origen de un vínculo.

[COleBusyDialog](../mfc/reference/colebusydialog-class.md)<br/>
Muestra los cuadros de diálogo servidor ocupado y el servidor no responde, la interfaz de usuario estándar para controlar las llamadas a las aplicaciones ocupadas. Normalmente, se muestra automáticamente el [COleMessageFilter](../mfc/reference/colemessagefilter-class.md) implementación.

## <a name="property-sheet-classes"></a>Clases de hoja de propiedades

Las clases de hoja de propiedades permiten que las aplicaciones usar las hojas de propiedades, los cuadros de diálogo también se denomina con pestañas. Hojas de propiedades son una manera eficaz para organizar un gran número de controles en un cuadro de diálogo.

[CPropertyPage](../mfc/reference/cpropertypage-class.md)<br/>
Proporciona las páginas individuales dentro de una hoja de propiedades. Derive una clase de `CPropertyPage` para cada página que se agregarán a la hoja de propiedades.

[CPropertySheet](../mfc/reference/cpropertysheet-class.md)<br/>
Proporciona el marco para varias páginas de propiedades. Derive la clase de hoja de propiedades de `CPropertySheet` para implementar rápidamente sus hojas de propiedades.

[COlePropertyPage](../mfc/reference/colepropertypage-class.md)<br/>
Muestra las propiedades de OLE controlan en una interfaz gráfica, similar a un cuadro de diálogo.

## <a name="html-based-dialog-classes"></a>Clases de cuadro de diálogo basado en HTML

[CDHtmlDialog](../mfc/reference/cdhtmldialog-class.md)<br/>
Se usa para crear cuadros de diálogo que implementan la interfaz de usuario con los recursos HTML en lugar de cuadro de diálogo.

[CMultiPageDHtmlDialog](../mfc/reference/cmultipagedhtmldialog-class.md)<br/>
Muestra varias páginas HTML secuencialmente y administra los eventos de cada página.

## <a name="related-classes"></a>Clases relacionadas

Estas clases no son cuadros de diálogo Sí, pero usan plantillas de cuadro de diálogo y tiene gran parte del comportamiento de los cuadros de diálogo.

[CDialogBar](../mfc/reference/cdialogbar-class.md)<br/>
Una barra de controles que se basa en una plantilla de cuadro de diálogo.

[CFormView](../mfc/reference/cformview-class.md)<br/>
Una vista de desplazamiento cuyo diseño se define en una plantilla de cuadro de diálogo. Derive una clase de `CFormView` para implementar una interfaz de usuario basada en una plantilla de cuadro de diálogo.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Proporciona un formulario de vista directamente conectada a un objeto de conjunto de registros de objeto de acceso a datos (DAO). Al igual que todas las vistas de formulario, un `CDaoRecordView` se basa en una plantilla de cuadro de diálogo.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Proporciona un formulario de vista directamente conectada a un objeto de conjunto de registros de Open Database Connectivity (ODBC). Al igual que todas las vistas de formulario, un `CRecordView` se basa en una plantilla de cuadro de diálogo.

[CPrintInfo](../mfc/reference/cprintinfo-structure.md)<br/>
Una estructura que contiene información acerca de un trabajo de impresión o vista preliminar. Utilizado por la arquitectura de impresión de [CView](../mfc/reference/cview-class.md).

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)

