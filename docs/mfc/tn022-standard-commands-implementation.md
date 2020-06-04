---
title: 'TN022: Implementación de comandos estándar'
ms.date: 11/04/2016
f1_keywords:
- vc.commands
helpviewer_keywords:
- ID_PREV_PANE command [MFC]
- ID_APP_EXIT command [MFC]
- ID_NEXT_PANE command [MFC]
- ID_INDICATOR_REC command [MFC]
- ID_WINDOW_SPLIT command [MFC]
- ID_FILE_PRINT_PREVIEW command [MFC]
- ID_WINDOW_CASCADE command [MFC]
- ID_FILE_CLOSE command [MFC]
- ID_FILE_SAVE_COPY_AS command [MFC]
- ID_WINDOW_ARRANGE command [MFC]
- ID_EDIT_FIND command [MFC]
- ID_FILE_OPEN command [MFC]
- ID_FILE_PAGE_SETUP command [MFC]
- ID_OLE_VERB_FIRST command [MFC]
- ID_EDIT_UNDO command [MFC]
- ID_EDIT_CLEAR command [MFC]
- ID_INDICATOR_CAPS command [MFC]
- ID_HELP_INDEX command [MFC]
- commands [MFC], standard
- ID_FILE_PRINT_SETUP command [MFC]
- ID_DEFAULT_HELP command [MFC]
- ID_INDICATOR_SCRL command [MFC]
- ID_FILE_PRINT command [MFC]
- ID_INDICATOR_OVR command [MFC]
- ID_INDICATOR_KANA command [MFC]
- ID_EDIT_COPY command [MFC]
- ID_EDIT_REDO command [MFC]
- ID_EDIT_PASTE command [MFC]
- ID_OLE_INSERT_NEW command [MFC]
- ID_OLE_EDIT_LINKS command [MFC]
- ID_EDIT_PASTE_SPECIAL command [MFC]
- ID_INDICATOR_EXT command [MFC]
- ID_HELP_USING command [MFC]
- standard commands
- ID_VIEW_STATUS_BAR command [MFC]
- ID_FILE_SAVE_AS command [MFC]
- ID_EDIT_CLEAR_ALL command [MFC]
- ID_WINDOW_NEW command [MFC]
- ID_CONTEXT_HELP command [MFC]
- ID_EDIT_REPLACE command [MFC]
- ID_WINDOW_TILE_HORZ command [MFC]
- ID_APP_ABOUT command [MFC]
- TN022
- ID_VIEW_TOOLBAR command [MFC]
- ID_HELP command [MFC]
- ID_WINDOW_TILE_VERT command [MFC]
- ID_EDIT_CUT command [MFC]
- ID_FILE_UPDATE command [MFC]
- ID_EDIT_REPEAT command [MFC]
- ID_FILE_SAVE command [MFC]
- ID_EDIT_PASTE_LINK command [MFC]
- ID_EDIT_SELECT_ALL command [MFC]
- ID_FILE_NEW command [MFC]
- ID_INDICATOR_NUM command
ms.assetid: a7883b46-23f7-4870-ac3a-804aed9258b5
ms.openlocfilehash: 5c7041f40c7e30592f642d29d9d02812a9596864
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370398"
---
# <a name="tn022-standard-commands-implementation"></a>TN022: Implementación de comandos estándar

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota describe las implementaciones de comandos estándar proporcionadas por MFC 2.0. Lea [primero la Nota técnica 21](../mfc/tn021-command-and-message-routing.md) porque describe los mecanismos utilizados para implementar muchos de los comandos estándar.

Esta descripción supone el conocimiento de las arquitecturas MFC, las API y la práctica de programación común. Se describen las API documentadas y no documentadas de "solo implementación". Este no es un lugar para empezar a aprender acerca de las características de o cómo programar en MFC. Consulte Visual C++ para obtener más información general y detalles de las API documentadas.

## <a name="the-problem"></a>El problema

MFC define muchos iDE de comandos estándar en el archivo de encabezado AFXRES. H. La compatibilidad con Framework para estos comandos varía. Comprender dónde y cómo las clases de marco de trabajo controlan estos comandos no solo le mostrará cómo funciona el marco de trabajo internamente, sino que proporcionará información útil sobre cómo personalizar las implementaciones estándar y le enseñará algunas técnicas para implementar sus propios controladores de comandos.

## <a name="contents-of-this-technical-note"></a>Contenido de esta nota técnica

Cada ID de comando se describe en dos secciones:

- El título: el nombre simbólico del identificador de comando (por ejemplo, ID_FILE_SAVE) seguido del propósito del comando (por ejemplo, "guarda el documento actual") separado por dos puntos.

- Uno o más párrafos que describen qué clases implementan el comando y qué hace la implementación predeterminada

La mayoría de las implementaciones de comandos predeterminadas están precableadas en el mapa de mensajes de clase base del marco de trabajo. Hay algunas implementaciones de comandos que requieren cableado explícito en la clase derivada. Estos se describen en "Nota". Si elige las opciones correctas en AppWizard, estos controladores predeterminados se conectarán automáticamente en la aplicación de esqueleto generada.

## <a name="naming-convention"></a>Convención de nomenclatura

Los comandos estándar siguen una convención de nomenclatura simple que le recomendamos que utilice si es posible. La mayoría de los comandos estándar se encuentran en lugares estándar en la barra de menús de una aplicación. El nombre simbólico del comando comienza con "ID_" seguido del nombre del menú emergente estándar, seguido del nombre del elemento de menú. El nombre simbólico está en mayúsculas con saltos de palabras de subrayado. Para los comandos que no tienen nombres de elemento de menú estándar, se define un nombre de comando lógico a partir de "ID_" (por ejemplo, ID_NEXT_PANE).

Usamos el prefijo "ID_" para indicar comandos que están diseñados para enlazarse a elementos de menú, botones de barra de herramientas u otros objetos de interfaz de usuario de comandos. Los controladores de comandos que controlan comandos "ID_" deben usar los mecanismos ON_COMMAND y ON_UPDATE_COMMAND_UI de la arquitectura de comandos MFC.

Le recomendamos que utilice el prefijo estándar "IDM_" para los elementos de menú que no siguen la arquitectura de comandos y necesitan código específico del menú para habilitarlos y deshabilitarlos. Por supuesto, el número de comandos específicos del menú debe ser pequeño, ya que seguir la arquitectura de comandos MFC no solo hace que los controladores de comandos sean más eficaces (ya que funcionarán con barras de herramientas), sino que hace que el código del controlador de comandos sea reutilizable.

## <a name="id-ranges"></a>Rangos de identificación

Consulte [la Nota técnica 20](../mfc/tn020-id-naming-and-numbering-conventions.md) para obtener más detalles sobre el uso de intervalos de ID en MFC.

Los comandos estándar de MFC entran en el intervalo 0xE000 a 0xEFFF. Por favor, no confíe en los valores específicos de estos iDE, ya que están sujetos a cambios en futuras versiones de la biblioteca.

La aplicación debe definir sus comandos en el intervalo 0x8000 a 0xDFFF.

## <a name="standard-command-ids"></a>IDs de comando estándar

Para cada identificador de comando, hay una cadena de solicitud de línea de mensaje estándar que se puede encontrar en el archivo PROMPTS. Rc. El identificador de cadena para ese símbolo del sistema de menú debe ser el mismo que para el identificador de comando.

- ID_FILE_NEW Crea un documento nuevo o vacío.

    > [!NOTE]
    >  Debe conectar esto `CWinApp`al mapa de mensajes de la clase derivada para habilitar esta funcionalidad.

   `CWinApp::OnFileNew`implementa este comando de forma diferente en función del número de plantillas de documento en la aplicación. Si solo hay `CDocTemplate` `CWinApp::OnFileNew` uno , creará un nuevo documento de ese tipo, así como el marco adecuado y la clase de vista.

   Si hay más `CDocTemplate`de `CWinApp::OnFileNew` uno , solicitará al usuario un cuadro de diálogo (AFX_IDD_NEWTYPEDLG) que le permitirá seleccionar qué tipo de documento utilizar. El `CDocTemplate` seleccionado se utiliza para crear el documento.

   Una personalización común de ID_FILE_NEW es proporcionar una selección diferente y más gráfica de los tipos de documento. En este caso, puede `CMyApp::OnFileNew` implementar el suyo propio `CWinApp::OnFileNew`y colocarlo en su mapa de mensajes en lugar de . No es necesario llamar a la implementación de la clase base.

   Otra personalización común de ID_FILE_NEW es proporcionar un comando independiente para crear un documento de cada tipo. En este caso, debe definir nuevos iDE de comando, por ejemplo, ID_FILE_NEW_CHART y ID_FILE_NEW_SHEET.

- ID_FILE_OPEN Abre un documento existente.

    > [!NOTE]
    >  Debe conectar esto `CWinApp`al mapa de mensajes de la clase derivada para habilitar esta funcionalidad.

   `CWinApp::OnFileOpen`tiene una implementación `CWinApp::DoPromptFileName` muy `CWinApp::OpenDocumentFile` simple de la llamada seguida de con el nombre de archivo o ruta de acceso del archivo que se va a abrir. La `CWinApp` rutina `DoPromptFileName` de implementación abre el cuadro de diálogo FileOpen estándar y lo rellena con las extensiones de archivo obtenidas de las plantillas de documento actuales.

   Una personalización común de ID_FILE_OPEN es personalizar el cuadro de diálogo FileOpen o agregar filtros de archivo adicionales. La forma recomendada de personalizar esto es reemplazar la implementación `CWinApp::OpenDocumentFile` predeterminada con su propio cuadro de diálogo FileOpen y llamar con el nombre de archivo o ruta de acceso del documento. No es necesario llamar a la clase base.

- ID_FILE_CLOSE Cierra el documento abierto actualmente.

   `CDocument::OnFileClose`llama `CDocument::SaveModified` para solicitar al usuario que guarde el documento `OnCloseDocument`si se ha modificado y, a continuación, llama a . Toda la lógica de cierre, incluida la `OnCloseDocument` destrucción del documento, se realiza en la rutina.

    > [!NOTE]
    >  ID_FILE_CLOSE actúa de forma diferente a un mensaje WM_CLOSE o a un comando SC_CLOSE sistema enviado a la ventana de marco de documentos. Al cerrar una ventana, se cerrará el documento solo si es la última ventana de marco que muestra el documento. Cerrar el documento con ID_FILE_CLOSE no solo cerrará el documento, sino que cerrará todas las ventanas de marco que muestran el documento.

- ID_FILE_SAVE Guarda el documento actual.

   La implementación utiliza `CDocument::DoSave` una rutina `OnFileSave` auxiliar `OnFileSaveAs`que se utiliza para ambos y . Si guarda un documento que no se ha guardado antes (es decir, no tiene un nombre de ruta de acceso, `OnFileSave` como en el caso de FileNew) o que se leyó desde un documento de solo lectura, la lógica actuará como el comando ID_FILE_SAVE_AS y pedirá al usuario que proporcione un nuevo nombre de archivo. El proceso real de abrir el archivo y realizar `OnSaveDocument`el guardado se realiza a través de la función virtual.

   Hay dos razones comunes para personalizar ID_FILE_SAVE. Para los documentos que no se guardan, simplemente quite los elementos de menú de ID_FILE_SAVE y los botones de la barra de herramientas de la interfaz de usuario. Asegúrese también de que nunca ensucie `CDocument::SetModifiedFlag`el documento (es decir, nunca llame) y el marco de trabajo nunca hará que el documento se guarde. Para los documentos que se guardan en otro lugar que no sea un archivo de disco, defina un nuevo comando para esa operación.

   En el caso `COleServerDoc`de un , ID_FILE_SAVE se utiliza tanto para guardar archivos (para documentos normales) como para la actualización de archivos (para documentos incrustados).

   Si los datos del documento se almacenan en archivos de disco `CDocument` individuales, pero `CDocument::OnSaveDocument` no `OnFileSave`desea usar la implementación de serialización predeterminada, debe invalidar en lugar de .

- ID_FILE_SAVE_AS Guarda el documento actual con un nombre de archivo diferente.

   La `CDocument::OnFileSaveAs` implementación `CDocument::DoSave` utiliza la `OnFileSave`misma rutina auxiliar que . El `OnFileSaveAs` comando se controla igual que ID_FILE_SAVE si los documentos no tenían ningún nombre de archivo antes de guardar. `COleServerDoc::OnFileSaveAs`implementa la lógica para guardar un archivo de datos de documento normal o para guardar un documento de servidor que representa un objeto OLE incrustado en alguna otra aplicación como un archivo independiente.

   Si personaliza la lógica de ID_FILE_SAVE, es probable que desee personalizar ID_FILE_SAVE_AS de forma similar o la operación de "Guardar como" puede no aplicarse a su documento. Puede eliminar el elemento de menú de la barra de menús si no es necesario.

- ID_FILE_SAVE_COPY_AS Guarda una copia del documento actual con un nuevo nombre.

   La `COleServerDoc::OnFileSaveCopyAs` implementación es `CDocument::OnFileSaveAs`muy similar a , excepto que el objeto de documento no está "adjunto" al archivo subyacente después de guardar. Es decir, si el documento en memoria se "modificó" antes de guardar, sigue siendo "modificado". Además, este comando no tiene ningún efecto en el nombre de la ruta de acceso o el título almacenados en el documento.

- ID_FILE_UPDATE Notifica al contenedor que guarde un documento incrustado.

   La `COleServerDoc::OnUpdateDocument` implementación simplemente notifica el contenedor que la incrustación debe ser guardada. A continuación, el contenedor llama a las API OLE adecuadas para guardar el objeto incrustado.

- ID_FILE_PAGE_SETUP Invoca un cuadro de diálogo de configuración/diseño de página específico de la aplicación.

   Actualmente no hay ningún estándar para este cuadro de diálogo y el marco de trabajo no tiene ninguna implementación predeterminada de este comando.

   Si decide implementar este comando, le recomendamos que utilice este identificador de comando.

- ID_FILE_PRINT_SETUP Invocar el cuadro de diálogo Configuración de impresión estándar.

    > [!NOTE]
    >  Debe conectar esto `CWinApp`al mapa de mensajes de la clase derivada para habilitar esta funcionalidad.

   Este comando invoca el cuadro de diálogo de configuración de impresión estándar que permite al usuario personalizar la impresora y la configuración de impresión para al menos este documento o, como máximo, todos los documentos de esta aplicación. Debe utilizar el Panel de control para cambiar la configuración predeterminada de la impresora para todo el sistema.

   `CWinApp::OnFilePrintSetup`tiene una implementación `CPrintDialog` muy simple `CWinApp::DoPrintDialog` creando un objeto y llamando a la función de implementación. Esto establece la configuración predeterminada de la impresora de la aplicación.

   La necesidad común de personalizar este comando es permitir la configuración de la impresora por documento, que debe almacenarse con el documento cuando se guarda. Para ello, debe agregar un controlador `CDocument` de mapa `CPrintDialog` de mensajes en la clase que cree un objeto, lo inicializa con `CPrintDialog::DoModal`los atributos de impresora adecuados (normalmente *hDevMode* y *hDevNames*), llame a la , y guarde la configuración de impresora modificada. Para una implementación sólida, debe `CWinApp::DoPrintDialog` examinar la `CWinApp::UpdatePrinterSelection` implementación de la detección de errores y para tratar los valores predeterminados razonables y el seguimiento de los cambios de impresora en todo el sistema.

- ID_FILE_PRINT Impresión estándar del documento actual

    > [!NOTE]
    >  Debe conectar esto `CView`al mapa de mensajes de la clase derivada para habilitar esta funcionalidad.

   Este comando imprime el documento actual, o más correctamente, inicia el proceso de impresión, lo que implica invocar el cuadro de diálogo de impresión estándar y ejecutar el motor de impresión.

   `CView::OnFilePrint`implementa este comando y el bucle de impresión principal. Llama al `CView::OnPreparePrinting` virtual para solicitar al usuario con el cuadro de diálogo de impresión. A continuación, prepara el controlador de dominio de salida para ir a `StartDoc` la impresora, abre el cuadro de diálogo de progreso de impresión (AFX_IDD_PRINTDLG) y envía el escape a la impresora. `CView::OnFilePrint`también contiene el bucle de impresión principal orientado a la página. Para cada página, llama `CView::OnPrepareDC` a `StartPage` la virtual seguida `CView::OnPrint` de un escape y llama a la virtual para esa página. Cuando se completa, se llama a la virtual `CView::OnEndPrinting` y se cierra el cuadro de diálogo de progreso de impresión.

   La arquitectura de impresión MFC está diseñada para enganchar de muchas maneras diferentes para imprimir y obtener una vista previa de impresión. Normalmente encontrará las `CView` diversas funciones reemplazables adecuadas para cualquier tarea de impresión orientada a páginas. Sólo en el caso de una aplicación que utiliza la impresora para la salida no orientada a la página, debe encontrar la necesidad de reemplazar la implementación de ID_FILE_PRINT.

- ID_FILE_PRINT_PREVIEW Entrar en el modo de vista previa de impresión para el documento actual.

    > [!NOTE]
    >  Debe conectar esto `CView`al mapa de mensajes de la clase derivada para habilitar esta funcionalidad.

   `CView::OnFilePrintPreview`inicia el modo de vista previa `CView::DoPrintPreview`de impresión llamando a la función auxiliar documentada. `CView::DoPrintPreview`es el motor principal para el `OnFilePrint` bucle de vista previa de impresión, al igual que el motor principal para el bucle de impresión.

   La operación de vista previa de impresión se `DoPrintPreview`puede personalizar de varias maneras pasando diferentes parámetros a . Consulte [la Nota técnica 30](../mfc/tn030-customizing-printing-and-print-preview.md), que analiza algunos de los detalles de la vista previa de impresión y cómo personalizarla.

- ID_FILE_MRU_FILE1... FILE16 Un rango de comandos para la **lista**MRU de archivo .

   `CWinApp::OnUpdateRecentFileMenu`es un controlador de interfaz de usuario de comandos de actualización que es uno de los usos más avanzados del mecanismo de ON_UPDATE_COMMAND_UI. En el recurso de menú, solo necesita definir un único elemento de menú con id ID_FILE_MRU_FILE1. Ese elemento de menú permanece deshabilitado inicialmente.

   A medida que crece la lista MRU, se agregan más elementos de menú a la lista. El `CWinApp` valor predeterminado de la implementación estándar es el límite estándar de los cuatro archivos utilizados más recientemente. Puede cambiar el valor `CWinApp::LoadStdProfileSettings` predeterminado llamando con un valor mayor o menor. La lista MRU se almacena en el archivo . Archivo INI. La lista se carga en `InitInstance` la función de la aplicación si se llama a `LoadStdProfileSettings`, y se guarda cuando se cierra la aplicación. El controlador de interfaz de usuario de comandos de actualización de MRU también convertirá rutas absolutas en rutas relativas para mostrarlas en el menú de archivos.

   `CWinApp::OnOpenRecentFile`es el controlador de ON_COMMAND que realiza el comando real. Simplemente obtiene el nombre de archivo de `CWinApp::OpenDocumentFile`la lista MRU y llama, lo que hace todo el trabajo de abrir el archivo y actualizar la lista MRU.

   No se recomienda la personalización de este controlador de comandos.

- ID_EDIT_CLEAR Borra la selección actual

   Actualmente no hay ninguna implementación estándar para este comando. Debe implementar esto `CView`para cada clase derivada.

   `CEditView`proporciona una implementación `CEdit::Clear`de este comando mediante . El comando está deshabilitado si no hay ninguna selección actual.

   Si decide implementar este comando, le recomendamos que utilice este identificador de comando.

- ID_EDIT_CLEAR_ALL Borra todo el documento.

   Actualmente no hay ninguna implementación estándar para este comando. Debe implementar esto `CView`para cada clase derivada.

   Si decide implementar este comando, le recomendamos que utilice este identificador de comando. Vea el Tutorial de MFC ejemplo [SCRIBBLE](../overview/visual-cpp-samples.md) para obtener una implementación de ejemplo.

- ID_EDIT_COPY Copia la selección actual en el Portapapeles.

   Actualmente no hay ninguna implementación estándar para este comando. Debe implementar esto `CView`para cada clase derivada.

   `CEditView`proporciona una implementación de este comando, que copia el `CEdit::Copy`texto seleccionado actualmente en el Portapapeles como CF_TEXT mediante . El comando está deshabilitado si no hay ninguna selección actual.

   Si decide implementar este comando, le recomendamos que utilice este identificador de comando.

- ID_EDIT_CUT Corta la selección actual en el Portapapeles.

   Actualmente no hay ninguna implementación estándar para este comando. Debe implementar esto `CView`para cada clase derivada.

   `CEditView`proporciona una implementación de este comando, que corta el `CEdit::Cut`texto seleccionado actualmente en el Portapapeles como CF_TEXT mediante . El comando está deshabilitado si no hay ninguna selección actual.

   Si decide implementar este comando, le recomendamos que utilice este identificador de comando.

- ID_EDIT_FIND Comienza la operación de búsqueda, abre el cuadro de diálogo de búsqueda no esmimoso.

   Actualmente no hay ninguna implementación estándar para este comando. Debe implementar esto `CView`para cada clase derivada.

   `CEditView`proporciona una implementación de este comando, `OnEditFindReplace` que llama a la función auxiliar de implementación para usar y almacenar la configuración de búsqueda/reemplazo anterior en variables de implementación privadas. La `CFindReplaceDialog` clase se utiliza para administrar el cuadro de diálogo no quese debe solicitar al usuario.

   Si decide implementar este comando, le recomendamos que utilice este identificador de comando.

- ID_EDIT_PASTE Inserta el contenido actual del Portapapeles.

   Actualmente no hay ninguna implementación estándar para este comando. Debe implementar esto `CView`para cada clase derivada.

   `CEditView`proporciona una implementación de este comando, que copia los `CEdit::Paste`datos actuales del Portapapeles reemplazando el texto seleccionado mediante . El comando está deshabilitado si no hay **ninguna CF_TEXT** en el Portapapeles.

   `COleClientDoc`simplemente proporciona un controlador de interfaz de usuario de comandos de actualización para este comando. Si el Portapapeles no contiene un elemento/objeto OLE incrustable, el comando se deshabilitará. Usted es responsable de escribir el controlador para el comando real para realizar el pegado real. Si la aplicación OLE también puede pegar otros formatos, debe proporcionar su propio controlador `COleClientDoc` de interfaz de usuario de comandos de actualización en la vista o documento (es decir, en algún lugar antes en el enrutamiento de destino de comando).

   Si decide implementar este comando, le recomendamos que utilice este identificador de comando.

   Para reemplazar la implementación `COleClientItem::CanPaste`OLE estándar, utilice .

- ID_EDIT_PASTE_LINK Inserta un vínculo desde el contenido actual del Portapapeles.

   Actualmente no hay ninguna implementación estándar para este comando. Debe implementar esto `CView`para cada clase derivada.

   `COleDocument`simplemente proporciona un controlador de interfaz de usuario de comandos de actualización para este comando. Si el Portapapeles no contiene elemento/objeto OLE enlazable, el comando se deshabilitará. Usted es responsable de escribir el controlador para el comando real para realizar el pegado real. Si la aplicación OLE también puede pegar otros formatos, debe proporcionar su propio controlador `COleDocument` de interfaz de usuario de comandos de actualización en la vista o documento (es decir, en algún lugar antes en el enrutamiento de destino de comando).

   Si decide implementar este comando, le recomendamos que utilice este identificador de comando.

   Para reemplazar la implementación `COleClientItem::CanPasteLink`OLE estándar, utilice .

- ID_EDIT_PASTE_SPECIAL Inserta el contenido actual del Portapapeles con opciones.

   Actualmente no hay ninguna implementación estándar para este comando. Debe implementar esto `CView`para cada clase derivada. MFC no proporciona este cuadro de diálogo.

   Si decide implementar este comando, le recomendamos que utilice este identificador de comando.

- ID_EDIT_REPEAT Repite la última operación.

   Actualmente no hay ninguna implementación estándar para este comando. Debe implementar esto `CView`para cada clase derivada.

   `CEditView`proporciona una implementación de este comando para repetir la última operación de búsqueda. Se utilizan las variables de implementación privadas para la última búsqueda. El comando se inhabilita si no se puede intentar una búsqueda.

   Si decide implementar este comando, le recomendamos que utilice este identificador de comando.

- ID_EDIT_REPLACE Comienza la operación de reemplazo, abre el cuadro de diálogo de reemplazo no esmimoso.

   Actualmente no hay ninguna implementación estándar para este comando. Debe implementar esto `CView`para cada clase derivada.

   `CEditView`proporciona una implementación de este comando, `OnEditFindReplace` que llama a la función auxiliar de implementación para usar y almacenar la configuración de búsqueda/reemplazo anterior en variables de implementación privadas. La `CFindReplaceDialog` clase se utiliza para administrar el cuadro de diálogo no que se encuentra y solicita al usuario.

   Si decide implementar este comando, le recomendamos que utilice este identificador de comando.

- ID_EDIT_SELECT_ALL Selecciona todo el documento.

   Actualmente no hay ninguna implementación estándar para este comando. Debe implementar esto `CView`para cada clase derivada.

   `CEditView`proporciona una implementación de este comando, que selecciona todo el texto del documento. El comando está deshabilitado si no hay texto que seleccionar.

   Si decide implementar este comando, le recomendamos que utilice este identificador de comando.

- ID_EDIT_UNDO Deshace la última operación.

   Actualmente no hay ninguna implementación estándar para este comando. Debe implementar esto `CView`para cada clase derivada.

   `CEditView`proporciona una implementación de `CEdit::Undo`este comando, utilizando . El comando está `CEdit::CanUndo` deshabilitado si devuelve FALSE.

   Si decide implementar este comando, le recomendamos que utilice este identificador de comando.

- ID_EDIT_REDO Rehace la última operación.

   Actualmente no hay ninguna implementación estándar para este comando. Debe implementar esto `CView`para cada clase derivada.

   Si decide implementar este comando, le recomendamos que utilice este identificador de comando.

- ID_WINDOW_NEW Abre otra ventana del documento activo.

   `CMDIFrameWnd::OnWindowNew`implementa esta poderosa característica mediante el uso de la plantilla de documento del documento actual para crear otro marco que contiene otra vista del documento actual.

   Al igual que la mayoría de los comandos de menú de ventana de la interfaz de documentos múltiples (MDI), el comando se deshabilita si no hay ninguna ventana secundaria MDI activa.

   No se recomienda la personalización de este controlador de comandos. Si desea proporcionar un comando que cree vistas adicionales o ventanas de marco, probablemente será mejor inventar su propio comando. Puede clonar el `CMDIFrameWnd::OnWindowNew` código y modificarlo al marco específico y ver las clases de su gusto.

- ID_WINDOW_ARRANGE Organiza los iconos en la parte inferior de una ventana MDI.

   `CMDIFrameWnd`implementa este comando MDI estándar en `OnMDIWindowCmd`una función auxiliar de implementación. Este comando de mapas auxiliares idea los mensajes de Windows MDI y, por lo tanto, puede compartir una gran cantidad de código.

   Al igual que la mayoría de los comandos de menú de la ventana MDI, el comando se inhabilita si no hay ninguna ventana secundaria MDI activa.

   No se recomienda la personalización de este controlador de comandos.

- ID_WINDOW_CASCADE ventanas Cascades para que se superpongan.

   `CMDIFrameWnd`implementa este comando MDI estándar en `OnMDIWindowCmd`una función auxiliar de implementación. Este comando de mapas auxiliares idea los mensajes de Windows MDI y, por lo tanto, puede compartir una gran cantidad de código.

   Al igual que la mayoría de los comandos de menú de la ventana MDI, el comando se inhabilita si no hay ninguna ventana secundaria MDI activa.

   No se recomienda la personalización de este controlador de comandos.

- ID_WINDOW_TILE_HORZ ventanas de azulejos horizontalmente.

   Este comando se `CMDIFrameWnd` implementa al igual que ID_WINDOW_CASCADE, excepto que se utiliza un mensaje MDI de Windows diferente para la operación.

   Debe elegir la orientación de teselas predeterminada para la aplicación. Puede hacerlo cambiando el identificador del elemento de menú "Tile" de la ventana a ID_WINDOW_TILE_HORZ o ID_WINDOW_TILE_VERT.

- ID_WINDOW_TILE_VERT ventanas de azulejos verticalmente.

   Este comando se `CMDIFrameWnd` implementa al igual que ID_WINDOW_CASCADE, excepto que se utiliza un mensaje MDI de Windows diferente para la operación.

   Debe elegir la orientación de teselas predeterminada para la aplicación. Puede hacerlo cambiando el identificador del elemento de menú "Tile" de la ventana a ID_WINDOW_TILE_HORZ o ID_WINDOW_TILE_VERT.

- ID_WINDOW_SPLIT Interfaz del teclado a la divisora.

   `CView`controla este `CSplitterWnd` comando para la implementación. Si la vista forma parte de una ventana divisora, este comando delegará en la función `CSplitterWnd::DoKeyboardSplit`de implementación. Esto colocará el divisor en un modo que permitirá a los usuarios de teclado dividir o desdividir una ventana divisora.

   Este comando está deshabilitado si la vista no está en un divisor.

   No se recomienda la personalización de este controlador de comandos.

- ID_APP_ABOUT Invoca el cuadro de diálogo Acerca de.

   No hay ninguna implementación estándar para el cuadro Acerca de de una aplicación. La aplicación predeterminada creada por AppWizard creará una clase de cuadro de diálogo personalizada para la aplicación y la usará como cuadro Acerca de. AppWizard también escribirá el controlador de comandos trivial que controla este comando e invoca el cuadro de diálogo.

   Casi siempre implementará este comando.

- ID_APP_EXIT Salir de la aplicación.

   `CWinApp::OnAppExit`controla este comando enviando un mensaje WM_CLOSE a la ventana principal de la aplicación. La `CFrameWnd` implementación controla el cierre estándar de la aplicación (solicitud de archivos sucios, etc.).

   No se recomienda la personalización de este controlador de comandos. Se `CWinApp::SaveAllModified` recomienda `CFrameWnd` reemplazar o cerrar la lógica.

   Si decide implementar este comando, le recomendamos que utilice este identificador de comando.

- ID_HELP_INDEX listas de temas de ayuda de . HlP.

    > [!NOTE]
    >  Debe conectar esto `CWinApp`al mapa de mensajes de la clase derivada para habilitar esta funcionalidad.

   `CWinApp::OnHelpIndex`controla este comando `CWinApp::WinHelp`llamando trivialmente .

   No se recomienda la personalización de este controlador de comandos.

- ID_HELP_USING Muestra ayuda sobre cómo usar la Ayuda.

    > [!NOTE]
    >  Debe conectar esto `CWinApp`al mapa de mensajes de la clase derivada para habilitar esta funcionalidad.

   `CWinApp::OnHelpUsing`controla este comando `CWinApp::WinHelp`llamando trivialmente .

   No se recomienda la personalización de este controlador de comandos.

- ID_CONTEXT_HELP Entra en el modo de ayuda SHIFT-F1.

    > [!NOTE]
    >  Debe conectar esto `CWinApp`al mapa de mensajes de la clase derivada para habilitar esta funcionalidad.

   `CWinApp::OnContextHelp`controla este comando estableciendo el cursor del modo de ayuda, introduciendo un bucle modal y esperando a que el usuario seleccione una ventana para obtener ayuda. Consulte [la Nota técnica 28](../mfc/tn028-context-sensitive-help-support.md) para obtener más detalles sobre la implementación de la Ayuda de MFC.

   No se recomienda la personalización de este controlador de comandos.

- ID_HELP Ayuda en el contexto actual

    > [!NOTE]
    >  Debe conectar esto `CWinApp`al mapa de mensajes de la clase derivada para habilitar esta funcionalidad.

   `CWinApp::OnHelp`controla este comando obteniendo el contexto de ayuda adecuado para el contexto de aplicación actual. Esto maneja la ayuda simple de F1, la ayuda en los cuadros de mensaje y así sucesivamente. Consulte [la Nota técnica 28](../mfc/tn028-context-sensitive-help-support.md) para obtener más detalles sobre la implementación de la ayuda de MFC.

   No se recomienda la personalización de este controlador de comandos.

- ID_DEFAULT_HELP Muestra la ayuda predeterminada para el contexto

    > [!NOTE]
    >  Debe conectar esto `CWinApp`al mapa de mensajes de la clase derivada para habilitar esta funcionalidad.

   Este comando se `CWinApp::OnHelpIndex`asigna generalmente a .

   Se puede proporcionar un controlador de comandos diferente si se desea una distinción entre la Ayuda predeterminada y el índice de Ayuda.

- ID_NEXT_PANE Va al siguiente panel

   `CView`controla este `CSplitterWnd` comando para la implementación. Si la vista forma parte de una ventana divisora, este comando delegará en la función `CSplitterWnd::OnNextPaneCmd`de implementación. Esto moverá la vista activa al siguiente panel del divisor.

   Este comando está deshabilitado si la vista no está en un divisor o no hay ningún panel siguiente al que ir.

   No se recomienda la personalización de este controlador de comandos.

- ID_PREV_PANE Va al panel anterior

   `CView`controla este `CSplitterWnd` comando para la implementación. Si la vista forma parte de una ventana divisora, este comando delegará en la función `CSplitterWnd::OnNextPaneCmd`de implementación. Esto moverá la vista activa al panel anterior en el divisor.

   Este comando está deshabilitado si la vista no está en un divisor o no hay ningún panel anterior al que ir.

   No se recomienda la personalización de este controlador de comandos.

- ID_OLE_INSERT_NEW Inserta un nuevo objeto OLE

   Actualmente no hay ninguna implementación estándar para este comando. Debe implementar esto `CView`para que la clase derivada inserte un nuevo elemento/objeto OLE en la selección actual.

   Todas las aplicaciones cliente OLE deben implementar este comando. AppWizard, con la opción OLE, creará `OnInsertObject` una implementación de esqueleto de en la clase de vista que tendrá que completar.

   Vea el ejemplo OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md) ejemplo para una implementación completa de este comando.

- ID_OLE_EDIT_LINKS Edita vínculos OLE

   `COleDocument`controla este comando mediante la implementación proporcionada por MFC del cuadro de diálogo de vínculos OLE estándar. Se accede a la implementación de este cuadro de diálogo a través de la `COleLinksDialog` clase. Si el documento actual no contiene ningún vínculo, el comando se inhabilita.

   No se recomienda la personalización de este controlador de comandos.

- ID_OLE_VERB_FIRST... LAST Un intervalo de ID para verbos OLE

   `COleDocument`utiliza este intervalo de identificador de comando para los verbos admitidos por el elemento/objeto OLE seleccionado actualmente. Debe ser un intervalo, ya que un determinado elemento OLE/tipo de objeto puede admitir cero o más verbos personalizados. En el menú de la aplicación, debe tener un elemento de menú con el identificador de ID_OLE_VERB_FIRST. Cuando se ejecuta el programa, el menú se actualizará con la descripción del verbo de menú adecuado (o menú emergente con muchos verbos). La administración del menú OLE `AfxOleSetEditMenu`se controla mediante , realizada en el controlador de interfaz de usuario de comandos de actualización para este comando.

   No hay controladores de comandos explícitos para controlar cada uno de los identificadores de comando en este intervalo. `COleDocument::OnCmdMsg`se invalida para atrapar todos los ides de comando en este rango, convertirlos en `COleClientItem::DoVerb`números de verbo de base cero e iniciar el servidor para ese verbo (usando ).

   No se recomienda la personalización u otro uso de este intervalo de ID de comando.

- ID_VIEW_TOOLBAR Activa y desactiva la barra de herramientas

   `CFrameWnd`controla este comando y el controlador de interfaz de usuario update-command para alternar el estado visible de la barra de herramientas. La barra de herramientas debe ser una ventana secundaria del marco con el identificador de ventana secundaria de AFX_IDW_TOOLBAR. El controlador de comandos realmente alterna la visibilidad de la ventana de la barra de herramientas. `CFrameWnd::RecalcLayout`se utiliza para volver a dibujar la ventana de marco con la barra de herramientas en su nuevo estado. El controlador de interfaz de usuario update-command comprueba el elemento de menú cuando la barra de herramientas está visible.

   No se recomienda la personalización de este controlador de comandos. Si desea agregar barras de herramientas adicionales, querrá clonar y modificar el controlador de comandos y el controlador de interfaz de usuario update-command para este comando.

- ID_VIEW_STATUS_BAR Activa y desactiva la barra de estado

   Este comando se `CFrameWnd` implementa al igual que ID_VIEW_TOOLBAR, excepto que se utiliza un identificador de ventana secundario (AFX_IDW_STATUS_BAR) diferente.

## <a name="update-only-command-handlers"></a>Controladores de comandos de solo actualización

Varios IDs de comando estándar se utilizan como indicadores en las barras de estado. Estos usan el mismo mecanismo de control de la interfaz de usuario de comando de actualización para mostrar su estado visual actual durante el tiempo de inactividad de la aplicación. Puesto que el usuario no puede seleccionarlos (es decir, no puede insertar un panel de barra de estado), no tiene sentido tener un controlador de ON_COMMAND para estos id de comando.

- ID_INDICATOR_CAPS : Indicador de bloqueo CAP.

- ID_INDICATOR_NUM : Indicador de bloqueo NUM.

- ID_INDICATOR_SCRL : Indicador de bloqueo SCRL.

- ID_INDICATOR_KANA : Indicador de bloqueo KANA (aplicable sólo a sistemas japoneses).

Los tres se implementan `CFrameWnd::OnUpdateKeyIndicator`en , una aplicación auxiliar de implementación que utiliza el identificador de comando para asignar a la clave virtual adecuada. Una implementación común habilita o deshabilita (para los `CCmdUI` paneles de estado deshabilitados - sin texto) el objeto en función de si la clave virtual adecuada está bloqueada actualmente.

No se recomienda la personalización de este controlador de comandos.

- ID_INDICATOR_EXT : Indicador de selección EXTended.

- ID_INDICATOR_OVR : Indicador OVeRstrike.

- ID_INDICATOR_REC : Indicador RECording.

Actualmente no existe una implementación estándar para estos indicadores.

Si decide implementar estos indicadores, le recomendamos que utilice estos indicadores ID y que mantenga el orden de los indicadores en su barra de estado (es decir, en este orden: EXT, CAP, NUM, SCRL, OVR, REC).

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
