---
title: "Clases de cuadro de di&#225;logo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.dialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases de cuadros de diálogo comunes"
  - "clases de cuadro de diálogo"
  - "clases de cuadros de diálogo comunes OLE"
  - "clases de hoja de propiedades"
  - "cuadros de diálogo con fichas"
ms.assetid: db75da23-4eff-4c6c-beae-79cf046fbce9
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases de cuadro de di&#225;logo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase `CDialog` y sus clases derivadas encapsulan la funcionalidad del cuadro de diálogo.  Puesto que un cuadro de diálogo es un tipo especial de ventana, `CDialog` se deriva de `CWnd`.  Derive las clases de diálogo de `CDialog` o utilice una de las clases comunes de cuadro de diálogo para los cuadros de diálogo estándar, como abrir o guardar un archivo, la impresión, seleccionando una fuente o el color, inicia una operación de Buscar\-y\- reemplazar, o realizando operaciones OLE\- relacionadas.  
  
 [CDialog](../mfc/reference/cdialog-class.md)  
 La clase base para todos los cuadros de diálogo, modales y no modales.  
  
 [CDataExchange](../mfc/reference/cdataexchange-class.md)  
 Proporciona información de intercambio de datos y validación para los cuadros de diálogo.  
  
## Cuadros de diálogo comunes  
 Estas clases de cuadro de diálogo encapsulan los cuadros de diálogo comunes de Windows.  Proporcionan implementaciones fáciles de usar de cuadros de diálogo complicados.  
  
 [CCommonDialog](../mfc/reference/ccommondialog-class.md)  
 Clase base para todos los cuadros de diálogo comunes.  
  
 [CFileDialog](../mfc/reference/cfiledialog-class.md)  
 Proporciona un cuadro de diálogo estándar para abrir o guardar un archivo.  
  
 [CColorDialog](../mfc/reference/ccolordialog-class.md)  
 Proporciona un cuadro de diálogo estándar para seleccionar color.  
  
 [CFontDialog](../mfc/reference/cfontdialog-class.md)  
 Proporciona un cuadro de diálogo estándar para seleccionar una fuente.  
  
 [CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)  
 Proporciona un cuadro de diálogo estándar para una operación de Buscar\-y\- reemplazar.  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 Proporciona un cuadro de diálogo estándar para imprimir un archivo.  
  
 [CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)  
 Proporciona una hoja de propiedades de impresión de Windows 2000.  
  
 [CPageSetupDialog](../mfc/reference/cpagesetupdialog-class.md)  
 Encapsula los servicios proporcionados por el cuadro de diálogo común de la configuración de página de Windows de compatibilidad adicional para los márgenes de impresión que establecen y modificar.  
  
## Cuadros de diálogo comunes de OLE  
 OLE agrega varios cuadros de diálogo comunes en Windows.  Estas clases encapsulan los cuadros de diálogo comunes de OLE.  
  
 [COleDialog](../mfc/reference/coledialog-class.md)  
 Utiliza el marco para contener las implementaciones comunes para todos los cuadros de diálogo de OLE.  Todas las clases de cuadro de diálogo en la categoría de la interfaz de usuario se derivan de esta clase base.  `COleDialog` no se puede utilizar directamente.  
  
 [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)  
 Muestra el cuadro de diálogo del objeto INSERT, la interfaz de usuario estándar para insertar los nuevos elementos vinculados o insertados OLE.  
  
 [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)  
 Muestra el cuadro de diálogo de pegar especial, la interfaz de usuario estándar para implementar el comando de pegar especial de edición.  
  
 [COleLinksDialog](../mfc/reference/colelinksdialog-class.md)  
 Muestra el cuadro de diálogo de los vínculos de edición, la interfaz de usuario estándar para la información de modificación sobre elementos vinculados.  
  
 [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)  
 Muestra el cuadro de diálogo del icono de cambio, la interfaz de usuario estándar para cambiar el icono asociado a un elemento incrustado o vinculado OLE.  
  
 [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)  
 Muestra el cuadro de diálogo convert, la interfaz de usuario estándar para convertir elementos de OLE a partir de un tipo a otro.  
  
 [COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)  
 Encapsula el cuadro de diálogo Propiedades OLE común de Windows.  Los cuadros de diálogo de Propiedades de OLE comunes proporcionan una manera fácil de mostrar y modificar las propiedades de un elemento OLE de una manera coherente con los estándares de Windows.  
  
 [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)  
 Muestra el cuadro de diálogo de la actualización, la interfaz de usuario estándar para actualizar todos los vínculos en un documento.  El cuadro de diálogo contiene un indicador de progreso para indicar cómo el cierre el procedimiento de actualización está completamente.  
  
 [COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)  
 Muestra el cuadro de diálogo del origen del cambio, la interfaz de usuario estándar para cambiar el destino o el origen de un vínculo.  
  
 [COleBusyDialog](../mfc/reference/colebusydialog-class.md)  
 Muestra el Servidor No disponibles y los cuadros de diálogo No Responder de Servidor, la interfaz de usuario estándar para administrar las llamadas a las aplicaciones No disponibles.  Mostrado normalmente automáticamente por la implementación de [COleMessageFilter](../mfc/reference/colemessagefilter-class.md) .  
  
## Clases de hoja de propiedades  
 Las clases de hoja de propiedades permiten las aplicaciones para utilizar las hojas de propiedades, también conocidas como cuadros de diálogo con fichas.  Las hojas de propiedades es una manera eficaz de organizar un gran número de controles en un único cuadro de diálogo.  
  
 [CPropertyPage](../mfc/reference/cpropertypage-class.md)  
 Proporciona páginas individuales dentro de una hoja de propiedades.  Derive una clase de `CPropertyPage` para cada página que se agregue a la hoja de propiedades.  
  
 [CPropertySheet](../mfc/reference/cpropertysheet-class.md)  
 Proporciona el marco para páginas de varias propiedades.  Derive la clase de hojas de propiedades de `CPropertySheet` para implementar las hojas de propiedades rápidamente.  
  
 [COlePropertyPage](../mfc/reference/colepropertypage-class.md)  
 Muestra las propiedades de un control OLE en una interfaz gráfica, a un cuadro de diálogo.  
  
## Clases basado en HTML del cuadro de diálogo  
 [CDHtmlDialog](../mfc/reference/cdhtmldialog-class.md)  
 Se utiliza para crear cuadros de diálogo que implementan la interfaz de usuario con HTML en lugar de recursos de cuadro de diálogo.  
  
 [CMultiPageDHtmlDialog](../mfc/reference/cmultipagedhtmldialog-class.md)  
 Muestra las páginas HTML varias secuencialmente y administra los eventos de cada página.  
  
## Clases relacionadas  
 Estas clases no son cuadros de diálogo por sí mismo, pero que utilizan plantillas de cuadro de diálogo y tienen gran parte del comportamiento de cuadros de diálogo.  
  
 [CDialogBar](../mfc/reference/cdialogbar-class.md)  
 Una barra de control basado en una plantilla de cuadro de diálogo.  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 Una vista de desplazamiento cuyo diseño se define en una plantilla de cuadro de diálogo.  Derive una clase de `CFormView` para implementar una interfaz de usuario basada en una plantilla de cuadro de diálogo.  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 Proporciona una vista de formulario directamente conectada a un objeto de conjunto de registros de \(DAO\) del Objeto de acceso a datos.  Como todas las vistas de formulario, `CDaoRecordView` se basa en una plantilla de cuadro de diálogo.  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 Proporciona una vista de formulario directamente conectada a un objeto de conjunto de registros de ODBC.  Como todas las vistas de formulario, `CRecordView` se basa en una plantilla de cuadro de diálogo.  
  
 [CPrintInfo](../mfc/reference/cprintinfo-structure.md)  
 Una estructura que contiene información sobre un trabajo de impresión o de la vista previa de impresión.  Utilizado por la arquitectura de impresión de [CView](../mfc/reference/cview-class.md).  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)