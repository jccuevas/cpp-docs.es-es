---
title: 'TN022: Implementación de comandos estándar | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.commands
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dea42f4bd33281e65696791677bdd81a921a59e6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="tn022-standard-commands-implementation"></a>TN022: Implementación de comandos estándar
> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe las implementaciones de comando estándar proporcionadas por MFC 2.0. Lectura [21 de nota técnica](../mfc/tn021-command-and-message-routing.md) primera porque describe los mecanismos utilizados para implementar muchos de los comandos estándares.  
  
 Esta descripción supone un conocimiento de las arquitecturas MFC, API y práctica de programación común. Documentado, así como sin documentar "implementación solo" API se describen. Esto no es un lugar para empezar a conocer las características de o cómo programar en MFC. Hacer referencia a Visual C++ para obtener más información y para obtener información detallada de las API documentadas.  
  
## <a name="the-problem"></a>El problema  
 MFC define muchos de los identificadores de comando estándar en el archivo de encabezado AFXRES. H. La compatibilidad con el marco de trabajo para estos comandos varía. Comprender dónde y cómo las clases de framework controlan estos comandos no solo mostrará cómo funciona internamente el marco de trabajo, pero proporcionará información útil acerca de cómo personalizar las implementaciones estándar y se explican algunas técnicas para implementar sus propios controladores de comandos.  
  
## <a name="contents-of-this-technical-note"></a>Contenido de esta nota técnica  
 Cada identificador de comando se describe en dos secciones:  
  
-   El título: nombre simbólico del identificador de comando (por ejemplo, **ID_FILE_SAVE**) seguido por el propósito del comando (por ejemplo, "se guarda el documento actual") separado por dos puntos.  
  
-   Uno o varios de los párrafos que describe las clases que implementan el comando y lo que hace la implementación predeterminada  
  
 Mayoría de las implementaciones de comandos de manera predeterminada se viene cableada en mapa de mensajes de clase base del marco de trabajo. Hay algunas implementaciones de comando que requieren conexión explícita en la clase derivada. Se describen en "Nota". Si opta por las opciones adecuadas en el Asistente para aplicaciones, estos controladores de manera predeterminada se conectará automáticamente en la aplicación esqueleto generada.  
  
## <a name="naming-convention"></a>Convención de nomenclatura  
 Comandos estándar siguen una convención de nomenclatura simple que se recomienda que utilice si es posible. Comandos más estándar se encuentran en lugares estándar en la barra de menús de la aplicación. El nombre simbólico del comando empieza por "ID_" seguido del nombre del menú emergente estándar, seguido del nombre de elemento de menú. El nombre simbólico es en mayúsculas con separaciones de palabras de carácter de subrayado. Para los comandos que no tienen nombres de elemento de menú estándar, se define un nombre de comando lógico a partir de "ID_" (por ejemplo, **ID_NEXT_PANE**).  
  
 El prefijo "ID_" se usa para indicar los comandos que están diseñados para enlazar a elementos de menú, botones de barra de herramientas u otros objetos de interfaz de usuario de comandos. Controladores de comandos controlar comandos "ID_" se deben utilizar el `ON_COMMAND` y `ON_UPDATE_COMMAND_UI` arquitectura de comandos de mecanismos de MFC.  
  
 Se recomienda que usar el prefijo "IDM_" estándar para los elementos de menú que no siguen la arquitectura de comandos y necesita un código específico del menú para activarlos y desactivarlos. Por supuesto el número de comandos específicos de menú debe ser pequeño porque después de la arquitectura de comandos MFC no solo aumenta la eficacia de los controladores de comandos (ya que trabajan con las barras de herramientas), pero hacen que el código de controlador de comandos reutilizable.  
  
## <a name="id-ranges"></a>Intervalos de Id.  
 Consulte [Nota técnica 20](../mfc/tn020-id-naming-and-numbering-conventions.md) para obtener más detalles sobre el uso de intervalos de identificadores de MFC.  
  
 Comandos estándar de MFC se encuentran dentro del rango 0xE000 a 0xEFFF. Por favor, no dependen de los valores específicos de estos identificadores puesto que están sujetos a cambios en versiones futuras de la biblioteca.  
  
 La aplicación debe definir sus comandos en el intervalo 0 x 8000 a 0xDFFF.  
  
## <a name="standard-command-ids"></a>Identificadores de comando estándar  
 Para cada identificador de comando, hay una cadena de mensaje de la línea de mensaje estándar que se pueden encontrar en los mensajes de archivo. RC. El identificador de cadena para ese mensaje de menú debe ser el mismo que el identificador del comando.  
  
-   ID_FILE_NEW crea un documento nuevo o está vacío.  
  
    > [!NOTE]
    >  Debe conectarse a su `CWinApp`-derivados de mapa de mensajes de la clase para habilitar esta funcionalidad.  
  
     `CWinApp::OnFileNew` Este comando de forma diferente dependiendo del número de plantillas de documento se implementa en la aplicación. Si solo hay un `CDocTemplate`, `CWinApp::OnFileNew` creará un nuevo documento de ese tipo, así como la clase de marco y vista apropiada.  
  
     Si hay más de un `CDocTemplate`, `CWinApp::OnFileNew` pedirá al usuario un cuadro de diálogo (**AFX_IDD_NEWTYPEDLG**) lo que permite seleccionar qué tipo de documento que se usará. Seleccionado `CDocTemplate` se utiliza para crear el documento.  
  
     Una personalización común de `ID_FILE_NEW` es proporcionar una diferente y más opciones gráfico de tipos de documentos. En este caso puede implementar su propia **CMyApp::OnFileNew** y lo coloca en el mapa de mensajes en lugar de `CWinApp::OnFileNew`. No hay ninguna necesidad de llamar a la implementación de la clase base.  
  
     Otra personalización común de `ID_FILE_NEW` es proporcionar un comando independiente para la creación de un documento de cada tipo. En este caso debe definir nuevos identificadores de comando, por ejemplo ID_FILE_NEW_CHART y ID_FILE_NEW_SHEET.  
  
-   ID_FILE_OPEN abre un documento existente.  
  
    > [!NOTE]
    >  Debe conectarse a su `CWinApp`-derivados de mapa de mensajes de la clase para habilitar esta funcionalidad.  
  
     `CWinApp::OnFileOpen` tiene una implementación muy sencilla de llamar al método **CWinApp::DoPromptFileName** seguido `CWinApp::OpenDocumentFile` con el nombre de archivo o ruta de acceso del archivo que se abre. El `CWinApp` rutina de implementación **DoPromptFileName** , se abrirá el cuadro de diálogo FileOpen estándar y se rellena con las extensiones de archivo que se obtienen de las plantillas de documento actual.  
  
     Una personalización común de `ID_FILE_OPEN` es para personalizar el cuadro de diálogo FileOpen o agregar filtros de archivo adicionales. Es la manera recomendada para personalizarlo reemplazar la implementación predeterminada con su propio cuadro de diálogo FileOpen y llamada `CWinApp::OpenDocumentFile` con el nombre de archivo o ruta de acceso del documento. No hay ninguna necesidad de llamar a la clase base.  
  
-   ID_FILE_CLOSE cierra el documento abierto actualmente.  
  
     **CDocument::OnFileClose** llamadas `CDocument::SaveModified` para pedir al usuario que guarde el documento si se ha modificado y, a continuación, llama a `OnCloseDocument`. Toda la lógica de cierre, incluidos destruir el documento, se realiza en el `OnCloseDocument` rutina.  
  
    > [!NOTE]
    >  **ID_FILE_CLOSE** actúa de forma diferente de un `WM_CLOSE` mensaje o un **SC_CLOSE** comando del sistema enviado a la ventana de marco de documentos. Cerrar la ventana se cerrará el documento solo si la última ventana de marco que muestra el documento. Cerrar el documento con **ID_FILE_CLOSE** sólo no cerrará el documento pero se cerrará todas las ventanas de marco que muestra el documento.  
  
-   ID_FILE_SAVE guarda el documento actual.  
  
     La implementación utiliza una rutina auxiliar **CDocument::DoSave** que se usa para **OnFileSave** y **OnFileSaveAs**. Si guarda un documento que no se ha guardado antes (es decir, no tiene un nombre de ruta de acceso, como en el caso de FileNew) o que se han leído desde un documento de sólo lectura, el **OnFileSave** lógica actuará como el **ID_FILE_SAVE_AS** comando y pedir al usuario que especifique un nuevo nombre de archivo. El proceso de abrir el archivo y realizar el almacenamiento real se realiza a través de la función virtual `OnSaveDocument`.  
  
     Hay dos razones comunes para personalizar **ID_FILE_SAVE**. Para los documentos que no guardan, basta con quitar el **ID_FILE_SAVE** elementos de menú y botones de barra de herramientas de la interfaz de usuario. Además, asegúrese de que nunca desfasadas del documento (es decir, no llamar nunca a `CDocument::SetModifiedFlag`) y el marco de trabajo nunca hará que el documento se guarde. Para los documentos que guarde en algún lugar que no sea un archivo de disco, definir un nuevo comando para esa operación.  
  
     En el caso de un `COleServerDoc`, **ID_FILE_SAVE** se usa para guardar archivos (para documentos normales) y la actualización del archivo (para documentos incrustados).  
  
     Si los datos del documento se almacenan en archivos de disco individuales, pero no desea usar el valor predeterminado **CDocument** serializar la implementación, debe invalidar `CDocument::OnSaveDocument` en lugar de **OnFileSave**.  
  
-   ID_FILE_SAVE_AS guarda el documento actual con un nombre de archivo diferente.  
  
     El **CDocument::OnFileSaveAs** implementación utiliza la misma **CDocument::DoSave** rutina auxiliar como **OnFileSave**. El **OnFileSaveAs** comandos se administran igual que **ID_FILE_SAVE** si los documentos no tenían ningún nombre de archivo antes de guardar. **COleServerDoc::OnFileSaveAs** implementa la lógica para guardar un archivo de datos de documento normal o para guardar un documento de servidor que representa un objeto OLE se incrusta en otra aplicación como un archivo independiente.  
  
     Si personaliza la lógica de **ID_FILE_SAVE**, probablemente deseará personalizar **ID_FILE_SAVE_AS** de un modo similar o a la operación de "Guardar como" no puede aplicarse al documento. Puede quitar el elemento de menú de la barra de menús si no es necesario.  
  
-   ID_FILE_SAVE_COPY_AS guarda un documento de copia actual con un nombre nuevo.  
  
     El **COleServerDoc::OnFileSaveCopyAs** implementación es muy similar a **CDocument::OnFileSaveAs**, excepto en que el objeto de documento no está "conectado" en el archivo subyacente después de la operación de guardar. Es decir, si el documento en memoria se ha "modificado" antes de guardar, que se sigue "modificar". Además, este comando no tiene ningún efecto en el nombre de ruta de acceso o el título almacenado en el documento.  
  
-   ID_FILE_UPDATE notifica el contenedor para guardar un documento incrustado.  
  
     El `COleServerDoc::OnUpdateDocument` implementación simplemente notifiies el contenedor que se debe guardar la incrustación. El contenedor, a continuación, llama a las API OLE adecuadas para guardar el objeto incrustado.  
  
-   ID_FILE_PAGE_SETUP, se invoca un cuadro de diálogo del programa de instalación y diseño de página específica de la aplicación.  
  
     Actualmente no hay ningún estándar para este cuadro de diálogo y el marco de trabajo no tiene ninguna implementación predeterminada de este comando.  
  
     Si decide implementar este comando, se recomienda que usar este identificador de comando.  
  
-   ID_FILE_PRINT_SETUP invocar el cuadro de diálogo de instalación de impresión estándar.  
  
    > [!NOTE]
    >  Debe conectarse a su `CWinApp`-derivados de mapa de mensajes de la clase para habilitar esta funcionalidad.  
  
     Este comando, invoca el cuadro de diálogo de configuración de impresión estándar que permite al usuario personalizar la impresora y la configuración de impresión para al menos en este documento o a lo sumo todos los documentos en esta aplicación. Debe usar el Panel de Control para cambiar la configuración de impresora predeterminada para todo el sistema.  
  
     `CWinApp::OnFilePrintSetup` tiene una implementación muy sencilla de crear un `CPrintDialog` objeto y llamar a la **CWinApp::DoPrintDialog** función de la implementación. Esto establece la configuración de impresora de aplicación predeterminada.  
  
     La necesidad común para personalizar este comando es permitir la configuración de la impresora de cada documento, que se debe almacenar con el documento cuando se guarda. Para ello debe agregar un controlador de mapa de mensajes en su **CDocument** clase que crea una `CPrintDialog` de objetos, lo inicializa con los atributos de impresora adecuada (normalmente **hDevMode** y **hDevNames**), llame a la **CPrintDialog::DoModal,** y guardar la configuración de impresora modificada. Para una implementación sólida, debe considerar la implementación de **CWinApp::DoPrintDialog** para detectar errores y **CWinApp::UpdatePrinterSelection** para tratar los valores predeterminados razonables y seguimiento de cambios de la impresora de todo el sistema.  
  
-   Impresión ID_FILE_PRINT estándar del documento actual  
  
    > [!NOTE]
    >  Debe conectarse a su `CView`-derivados de mapa de mensajes de la clase para habilitar esta funcionalidad.  
  
     Este comando imprime el documento actual, o más correctamente, inicia el proceso de impresión, lo que implica invocar el cuadro de diálogo de impresión estándar y ejecuta el motor de impresión.  
  
     **CView::OnFilePrint** implementa este comando y el bucle de impresión principal. Lo llama el virtual `CView::OnPreparePrinting` al símbolo del sistema del usuario con el cuadro de diálogo de impresión. A continuación, se prepara la salida del controlador de dominio para ir a la impresora, se abrirá el cuadro de diálogo de progreso de la impresión (**AFX_IDD_PRINTDLG**) y envía el `StartDoc` escape a la impresora. **CView::OnFilePrint** también contiene el bucle de impresión y orientada a la página principal. Para cada página, llama a virtual `CView::OnPrepareDC` seguido por un `StartPage` escape y llamar a virtual `CView::OnPrint` para esa página. Cuando haya terminado, el virtual `CView::OnEndPrinting` se llama, y se cierra el cuadro de diálogo de progreso de la impresión.  
  
     La arquitectura de impresión de MFC está diseñada para enlazar de muchas maneras diferentes para la impresión y vista previa. Normalmente, encontrará los distintos `CView` funciones reemplazables adecuadas para las tareas de impresión orientada a páginas. Sólo en el caso de una aplicación que usa la impresora para distintos de páginas orientada a servicios de salida, debe buscar la necesidad de reemplazar el **ID_FILE_PRINT** implementación.  
  
-   ID_FILE_PRINT_PREVIEW especificar el modo de vista previa de impresión del documento actual.  
  
    > [!NOTE]
    >  Debe conectarse a su `CView`-derivados de mapa de mensajes de la clase para habilitar esta funcionalidad.  
  
     **CView::OnFilePrintPreview** inicia el modo de vista previa de impresión mediante una llamada a la función auxiliar documentado **CView::DoPrintPreview**. **CView::DoPrintPreview** es el motor principal para el bucle de vista previa de impresión, al igual que **OnFilePrint** es el motor principal para el bucle de impresión.  
  
     La operación de vista previa de impresión se puede personalizar de varias maneras al pasar parámetros distintos a **DoPrintPreview**. Consulte [30 de nota técnica](../mfc/tn030-customizing-printing-and-print-preview.md), que describen algunos de los detalles de la vista previa de impresión y cómo personalizarlo.  
  
-   **ID_FILE_MRU_FILE1**... **FILE16** un intervalo de identificadores de comandos para el archivo de elementos utilizados Recientemente `list`.  
  
     **CWinApp::OnUpdateRecentFileMenu** es un controlador de interfaz de usuario de comandos de actualización que es uno de los usos más avanzados de la `ON_UPDATE_COMMAND_UI` mecanismo. En el recurso de menú, sólo necesita definir un solo elemento de menú con el identificador **ID_FILE_MRU_FILE1**. Ese elemento de menú permanece inicialmente deshabilitado.  
  
     Como el MRU lista crece, menú más elementos se agregan a la lista. El estándar `CWinApp` implementación tiene como valor predeterminado del límite estándar de los cuatro archivos usados más recientemente. Puede cambiar el valor predeterminado mediante una llamada a `CWinApp::LoadStdProfileSettings` con un valor mayor o menor. La lista de elementos utilizados Recientemente se almacena en la aplicación. Archivo INI. La lista se carga en la aplicación `InitInstance` funcionando si se llama a `LoadStdProfileSettings`y se guarda cuando se cierre la aplicación. El controlador de interfaz de usuario de comandos de actualización MRU también convertirá rutas de acceso absolutas en las rutas de acceso relativas para su presentación en el menú archivo.  
  
     **CWinApp::OnOpenRecentFile** es el `ON_COMMAND` controlador que ejecutará el comando real. Obtiene simplemente el nombre de archivo en la lista de elementos utilizados Recientemente y llamadas `CWinApp::OpenDocumentFile`, que hace todo el trabajo de abrir el archivo y actualizar la lista de elementos utilizados Recientemente.  
  
     No se recomienda la personalización de este controlador de comandos.  
  
-   ID_EDIT_CLEAR borra la selección actual  
  
     Actualmente no hay ninguna implementación estándar de este comando. Debe hacerlo para cada `CView`-clase derivada.  
  
     `CEditView` Proporciona una implementación de este comando mediante `CEdit::Clear`. El comando está deshabilitado si no hay ninguna selección actual.  
  
     Si decide implementar este comando, se recomienda que usar este identificador de comando.  
  
-   ID_EDIT_CLEAR_ALL borra todo el documento.  
  
     Actualmente no hay ninguna implementación estándar de este comando. Debe hacerlo para cada `CView`-clase derivada.  
  
     Si decide implementar este comando, se recomienda que usar este identificador de comando. Vea el ejemplo de Tutorial de MFC [SCRIBBLE](../visual-cpp-samples.md) para una implementación de ejemplo.  
  
-   ID_EDIT_COPY copia la selección actual en el Portapapeles.  
  
     Actualmente no hay ninguna implementación estándar de este comando. Debe hacerlo para cada `CView`-clase derivada.  
  
     `CEditView` Proporciona una implementación de este comando, que copia el texto seleccionado actualmente en el Portapapeles como CF_TEXT mediante `CEdit::Copy`. El comando está deshabilitado si no hay ninguna selección actual.  
  
     Si decide implementar este comando, se recomienda que usar este identificador de comando.  
  
-   ID_EDIT_CUT corta la selección actual en el Portapapeles.  
  
     Actualmente no hay ninguna implementación estándar de este comando. Debe hacerlo para cada `CView`-clase derivada.  
  
     `CEditView` Proporciona una implementación de este comando, que corta el texto seleccionado actualmente en el Portapapeles como CF_TEXT mediante `CEdit::Cut`. El comando está deshabilitado si no hay ninguna selección actual.  
  
     Si decide implementar este comando, se recomienda que usar este identificador de comando.  
  
-   ID_EDIT_FIND comienza la operación de búsqueda, se abrirá el cuadro de diálogo no modal de búsqueda.  
  
     Actualmente no hay ninguna implementación estándar de este comando. Debe hacerlo para cada `CView`-clase derivada.  
  
     `CEditView` Proporciona una implementación de este comando, que llama a la función de aplicación auxiliar de implementación **OnEditFindReplace** para utilizar y almacenar la configuración de búsqueda y reemplazo anterior en variables de implementación privada. La `CFindReplaceDialog` clase se utiliza para administrar el cuadro de diálogo no modal para preguntar al usuario.  
  
     Si decide implementar este comando, se recomienda que usar este identificador de comando.  
  
-   ID_EDIT_PASTE inserta el contenido actual del Portapapeles.  
  
     Actualmente no hay ninguna implementación estándar de este comando. Debe hacerlo para cada `CView`-clase derivada.  
  
     `CEditView` Proporciona una implementación de este comando, que copia los datos del Portapapeles actuales reemplazando el texto seleccionado con `CEdit::Paste`. El comando está deshabilitado si no hay ningún **CF_TEXT** en el Portapapeles.  
  
     **COleClientDoc** simplemente proporciona un controlador de interfaz de usuario de comando de actualización para este comando. Si el Portapapeles no contiene un elemento OLE incrustable/objeto, se deshabilitará el comando. Usted es responsable de escribir el controlador para el comando real para realizar el pegado real. Si una aplicación OLE también puede pegar a otros formatos, debe proporcionar su propio controlador de interfaz de usuario de comando de actualización en la vista o el documento (es decir, en algún lugar antes de **COleClientDoc** en la ruta de destino de comando).  
  
     Si decide implementar este comando, se recomienda que usar este identificador de comando.  
  
     Para reemplazar la implementación estándar de OLE, utilice `COleClientItem::CanPaste`.  
  
-   ID_EDIT_PASTE_LINK inserta un vínculo de contenido actual del Portapapeles.  
  
     Actualmente no hay ninguna implementación estándar de este comando. Debe hacerlo para cada `CView`-clase derivada.  
  
     `COleDocument` simplemente proporciona un controlador de interfaz de usuario de comando de actualización para este comando. Si el Portapapeles no contiene linkable elemento/objeto OLE, se deshabilitará el comando. Usted es responsable de escribir el controlador para el comando real para realizar el pegado real. Si una aplicación OLE también puede pegar a otros formatos, debe proporcionar su propio controlador de interfaz de usuario de comando de actualización en la vista o el documento (es decir, en algún lugar antes de `COleDocument` en la ruta de destino de comando).  
  
     Si decide implementar este comando, se recomienda que usar este identificador de comando.  
  
     Para reemplazar la implementación estándar de OLE, utilice `COleClientItem::CanPasteLink`.  
  
-   ID_EDIT_PASTE_SPECIAL inserta el contenido actual del Portapapeles con opciones.  
  
     Actualmente no hay ninguna implementación estándar de este comando. Debe hacerlo para cada `CView`-clase derivada. MFC no proporciona este cuadro de diálogo.  
  
     Si decide implementar este comando, se recomienda que usar este identificador de comando.  
  
-   ID_EDIT_REPEAT se repite la última operación.  
  
     Actualmente no hay ninguna implementación estándar de este comando. Debe hacerlo para cada `CView`-clase derivada.  
  
     `CEditView` Proporciona una implementación de este comando para repetir la última operación de búsqueda. Se utilizan las variables de implementación privada de la última búsqueda. El comando está deshabilitado si no se puede intentar una operación de búsqueda.  
  
     Si decide implementar este comando, se recomienda que usar este identificador de comando.  
  
-   ID_EDIT_REPLACE comienza la operación de reemplazo, aparece el cuadro de diálogo no modal de reemplazo.  
  
     Actualmente no hay ninguna implementación estándar de este comando. Debe hacerlo para cada `CView`-clase derivada.  
  
     `CEditView` Proporciona una implementación de este comando, que llama a la función de aplicación auxiliar de implementación **OnEditFindReplace** para utilizar y almacenar la configuración de búsqueda y reemplazo anterior en variables de implementación privada. La `CFindReplaceDialog` clase se utiliza para administrar el cuadro de diálogo no modal que pide al usuario.  
  
     Si decide implementar este comando, se recomienda que usar este identificador de comando.  
  
-   ID_EDIT_SELECT_ALL selecciona todo el documento.  
  
     Actualmente no hay ninguna implementación estándar de este comando. Debe hacerlo para cada `CView`-clase derivada.  
  
     `CEditView` Proporciona una implementación de este comando, que selecciona todo el texto del documento. El comando está deshabilitado si no hay ningún texto que desea seleccionar.  
  
     Si decide implementar este comando, se recomienda que usar este identificador de comando.  
  
-   ID_EDIT_UNDO deshace la última operación.  
  
     Actualmente no hay ninguna implementación estándar de este comando. Debe hacerlo para cada `CView`-clase derivada.  
  
     `CEditView` Proporciona una implementación de este comando, mediante `CEdit::Undo`. El comando está deshabilitado si `CEdit::CanUndo` devuelve FALSE.  
  
     Si decide implementar este comando, se recomienda que usar este identificador de comando.  
  
-   ID_EDIT_REDO Rehace la última operación.  
  
     Actualmente no hay ninguna implementación estándar de este comando. Debe hacerlo para cada `CView`-clase derivada.  
  
     Si decide implementar este comando, se recomienda que usar este identificador de comando.  
  
-   ID_WINDOW_NEW abre otra ventana en el documento activo.  
  
     **CMDIFrameWnd::OnWindowNew** implementa esta eficaz característica mediante la plantilla de documento del documento actual para crear otro marco que contiene otra vista del documento actual.  
  
     Al igual que la mayoría varios documentos (MDI) de la interfaz ventana comandos de menú, el comando está deshabilitado si no hay ninguna ventana secundaria MDI activa.  
  
     No se recomienda la personalización de este controlador de comandos. Si desea proporcionar un comando que crea vistas adicionales o ventanas de marco, probablemente será mejor inventar su propio comando. Se puede clonar el código de **CMDIFrameWnd::OnWindowNew** y modifíquelo para las clases concretas de marco y vista de su gusto.  
  
-   ID_WINDOW_ARRANGE organiza los iconos en la parte inferior de una ventana MDI.  
  
     `CMDIFrameWnd` implementa este comando estándar de MDI en una función de aplicación auxiliar de implementación **OnMDIWindowCmd**. Esta aplicación auxiliar asigna identificadores de comando a los mensajes de ventanas MDI y, por tanto, puede compartir una gran cantidad de código.  
  
     Al igual que la mayoría de los comandos de menú de ventana MDI, el comando está deshabilitado si no hay ninguna ventana secundaria MDI activa.  
  
     No se recomienda la personalización de este controlador de comandos.  
  
-   Ventanas en cascada ID_WINDOW_CASCADE para que se superpongan.  
  
     `CMDIFrameWnd` implementa este comando estándar de MDI en una función de aplicación auxiliar de implementación **OnMDIWindowCmd**. Esta aplicación auxiliar asigna identificadores de comando a los mensajes de ventanas MDI y, por tanto, puede compartir una gran cantidad de código.  
  
     Al igual que la mayoría de los comandos de menú de ventana MDI, el comando está deshabilitado si no hay ninguna ventana secundaria MDI activa.  
  
     No se recomienda la personalización de este controlador de comandos.  
  
-   Windows ID_WINDOW_TILE_HORZ mosaicos horizontalmente.  
  
     Este comando se implementa en `CMDIFrameWnd` igual que **ID_WINDOW_CASCADE**, excepto en que se usa un mensaje de ventanas MDI diferente para la operación.  
  
     Debe elegir la orientación de mosaico predeterminado para la aplicación. Puede hacerlo cambiando el identificador para el elemento de menú "Icono" de ventana como **ID_WINDOW_TILE_HORZ** o **ID_WINDOW_TILE_VERT**.  
  
-   Windows ID_WINDOW_TILE_VERT iconos verticalmente.  
  
     Este comando se implementa en `CMDIFrameWnd` igual que **ID_WINDOW_CASCADE**, excepto en que se usa un mensaje de ventanas MDI diferente para la operación.  
  
     Debe elegir la orientación de mosaico predeterminado para la aplicación. Puede hacerlo cambiando el identificador para el elemento de menú "Icono" de ventana como **ID_WINDOW_TILE_HORZ** o **ID_WINDOW_TILE_VERT**.  
  
-   Interfaz de teclado ID_WINDOW_SPLIT al divisor.  
  
     `CView` controla este comando para el `CSplitterWnd` implementación. Si la vista es parte de una ventana divisora, este comando va a delegar a la función de la implementación `CSplitterWnd::DoKeyboardSplit`. Esto colocará el divisor en un modo que permitirá a los usuarios de teclado dividir o eliminar las divisiones de una ventana divisora.  
  
     Este comando está deshabilitado si la vista no está en un divisor.  
  
     No se recomienda la personalización de este controlador de comandos.  
  
-   ID_APP_ABOUT, se invoca el cuadro de diálogo acerca de.  
  
     No hay ninguna implementación estándar para el cuadro de diálogo acerca de la aplicación. La aplicación creada mediante AppWizard predeterminada creará una clase de cuadro de diálogo personalizado para su aplicación y usarlo como el cuadro de diálogo acerca. AppWizard también escribirá el controlador de comandos trivial que controla este comando e invoca el cuadro de diálogo.  
  
     Casi siempre implementará este comando.  
  
-   ID_APP_EXIT salir de la aplicación.  
  
     **CWinApp::OnAppExit** controla este comando mediante el envío de un `WM_CLOSE` mensaje en la ventana principal de la aplicación. El estándar de cierre de la aplicación (pedir archivos modificados y así sucesivamente) se controla mediante el `CFrameWnd` implementación.  
  
     No se recomienda la personalización de este controlador de comandos. Reemplazar `CWinApp::SaveAllModified` o `CFrameWnd` se recomienda la lógica de cierre.  
  
     Si decide implementar este comando, se recomienda que usar este identificador de comando.  
  
-   ID_HELP_INDEX se enumeran temas de la Ayuda de. Archivo HLP.  
  
    > [!NOTE]
    >  Debe conectarse a su `CWinApp`-derivados de mapa de mensajes de la clase para habilitar esta funcionalidad.  
  
     `CWinApp::OnHelpIndex` controla este comando llamando trivial `CWinApp::WinHelp`.  
  
     No se recomienda la personalización de este controlador de comandos.  
  
-   ID_HELP_USING muestra la ayuda acerca de cómo usar la Ayuda.  
  
    > [!NOTE]
    >  Debe conectarse a su `CWinApp`-derivados de mapa de mensajes de la clase para habilitar esta funcionalidad.  
  
     `CWinApp::OnHelpUsing` controla este comando llamando trivial `CWinApp::WinHelp`.  
  
     No se recomienda la personalización de este controlador de comandos.  
  
-   MAYÚS-F1 de ID_CONTEXT_HELP entra en modo de ayuda.  
  
    > [!NOTE]
    >  Debe conectarse a su `CWinApp`-derivados de mapa de mensajes de la clase para habilitar esta funcionalidad.  
  
     `CWinApp::OnContextHelp` Este comando se controla estableciendo el cursor del modo de ayuda, escribir un bucle modal y esperando al usuario seleccionar una ventana para obtener ayuda sobre. Consulte [28 de nota técnica](../mfc/tn028-context-sensitive-help-support.md) para obtener más detalles sobre la implementación de la Ayuda de MFC.  
  
     No se recomienda la personalización de este controlador de comandos.  
  
-   ID_HELP proporciona ayuda en el contexto actual  
  
    > [!NOTE]
    >  Debe conectarse a su `CWinApp`-derivados de mapa de mensajes de la clase para habilitar esta funcionalidad.  
  
     `CWinApp::OnHelp` gestiona este comando al obtener el contexto de ayuda adecuada para el contexto de aplicación actual. Esto controla simple ayuda de F1, ayuda en cuadros de mensaje y así sucesivamente. Consulte [28 de nota técnica](../mfc/tn028-context-sensitive-help-support.md) para obtener más detalles sobre la MFC de implementación de la Ayuda.  
  
     No se recomienda la personalización de este controlador de comandos.  
  
-   ID_DEFAULT_HELP muestra la Ayuda de forma predeterminada para el contexto  
  
    > [!NOTE]
    >  Debe conectarse a su `CWinApp`-derivados de mapa de mensajes de la clase para habilitar esta funcionalidad.  
  
     Este comando normalmente se asigna a `CWinApp::OnHelpIndex`.  
  
     Si se desea una diferencia entre la Ayuda predeterminada y el índice de la Ayuda, puede proporcionarse un controlador de comandos diferente.  
  
-   ID_NEXT_PANE va al siguiente panel  
  
     `CView` controla este comando para el `CSplitterWnd` implementación. Si la vista es parte de una ventana divisora, este comando va a delegar a la función de la implementación **CSplitterWnd::OnNextPaneCmd**. Este proceso moverá la vista activa al siguiente panel en el divisor.  
  
     Este comando está deshabilitado si la vista no está en un divisor o no hay ningún panel siguiente para ir a.  
  
     No se recomienda la personalización de este controlador de comandos.  
  
-   ID_PREV_PANE va al panel anterior  
  
     `CView` controla este comando para el `CSplitterWnd` implementación. Si la vista es parte de una ventana divisora, este comando va a delegar a la función de la implementación **CSplitterWnd::OnNextPaneCmd**. Este proceso moverá la vista activa al panel anterior en el divisor.  
  
     Este comando está deshabilitado si la vista no está en un divisor o no hay ningún panel anterior para ir a.  
  
     No se recomienda la personalización de este controlador de comandos.  
  
-   ID_OLE_INSERT_NEW inserta un nuevo objeto OLE  
  
     Actualmente no hay ninguna implementación estándar de este comando. Debe hacerlo para su `CView`-clase derivada para insertar un nuevo elemento/objeto OLE en la selección actual.  
  
     Todas las aplicaciones de cliente OLE deben implementar este comando. El Asistente para aplicaciones, con la opción OLE, creará una implementación esqueleto de **OnInsertObject** en la clase de vista que se deben completar.  
  
     Vea el ejemplo de MFC OLE [OCLIENT](../visual-cpp-samples.md) ejemplo para una implementación completa de este comando.  
  
-   ID_OLE_EDIT_LINKS edita vínculos OLE  
  
     `COleDocument` Este comando se controla mediante la implementación proporcionada por MFC del cuadro de diálogo estándar de vínculos OLE. La implementación de este cuadro de diálogo se tiene acceso a través de la `COleLinksDialog` clase. Si el documento actual no contiene ningún vínculo, se deshabilita el comando.  
  
     No se recomienda la personalización de este controlador de comandos.  
  
-   ID_OLE_VERB_FIRST... ÚLTIMO intervalo de un identificador para los verbos OLE  
  
     `COleDocument` usa este intervalo de Id. de comando para los verbos admitidos por el elemento/objeto OLE actualmente seleccionado. Esto debe ser un intervalo como un tipo de elemento u objeto OLE determinado puede admitir verbos personalizados de cero o más. En el menú de la aplicación, debe tener un elemento de menú con el Id. de **ID_OLE_VERB_FIRST**. Cuando se ejecuta el programa, el menú se actualizará con la descripción del verbo de menú correspondiente (o menú emergente con muchos verbos). La administración del menú OLE se controla mediante `AfxOleSetEditMenu`hecho en el controlador de interfaz de usuario de comandos de actualización para este comando.  
  
     No hay ningún controlador de comando explícito para controlar cada uno de identificador del comando en este intervalo. **COleDocument::OnCmdMsg** se invalida para interceptar todos los identificadores de comando de este intervalo, convertirlas en números de verbo basado en cero e iniciar el servidor para ese verbo (mediante `COleClientItem::DoVerb`).  
  
     No se recomienda personalización u otros usos de este intervalo de Id. de comando.  
  
-   ID_VIEW_TOOLBAR alterna la barra de herramientas, activar y desactivar  
  
     `CFrameWnd` controla este comando y el controlador de interfaz de usuario de comandos de actualización para alternar el estado de visibilidad de la barra de herramientas. La barra de herramientas debe ser una ventana secundaria del marco con el identificador de ventana secundaria de `AFX_IDW_TOOLBAR`. El controlador de comandos realmente alterna la visibilidad de la ventana de la barra de herramientas. `CFrameWnd::RecalcLayout` se utiliza para volver a dibujar la ventana de marco con la barra de herramientas en su nuevo estado. El controlador de interfaz de usuario de comando de actualización comprueba el elemento de menú cuando la barra de herramientas está visible.  
  
     No se recomienda la personalización de este controlador de comandos. Si desea agregar barras de herramientas adicionales, desea clonar y modificar el controlador de comandos y el controlador de interfaz de usuario de comando de actualización para este comando.  
  
-   ID_VIEW_STATUS_BAR activa o desactiva la barra de estado activar y desactivar  
  
     Este comando se implementa en `CFrameWnd` igual que **ID_VIEW_TOOLBAR**, excepto un identificador de ventana secundaria diferentes (**AFX_IDW_STATUS_BAR**) se utiliza.  
  
## <a name="update-only-command-handlers"></a>Controladores de comandos sólo actualización  
 Se utilizan varios identificadores de comando estándar como indicadores en barras de estado. Estos usan el mismo mecanismo de control de interfaz de usuario de comando de actualización para mostrar su estado visual actual durante el tiempo de inactividad de la aplicación. Puesto que no se pueden seleccionar por el usuario (es decir, no puede insertar un panel de barra de estado), a continuación, no tiene sentido tener un `ON_COMMAND` controlador para estos identificadores de comando.  
  
-   **ID_INDICATOR_CAPS** : indicador de bloqueo de extremo.  
  
-   **ID_INDICATOR_NUM** : indicador de BLOQ NUM.  
  
-   **ID_INDICATOR_SCRL** : indicador de bloqueo Bloq Despl.  
  
-   **ID_INDICATOR_KANA** : indicador de bloqueo KANA (se aplica sólo a los sistemas japonés).  
  
 Estas tres cosas se implementan en **CFrameWnd::OnUpdateKeyIndicator**, una aplicación auxiliar de implementación que utiliza el identificador de comando para asignar a la clave Virtual adecuada. Una implementación común habilita o deshabilita (para los paneles de estado deshabilitados = no hay texto) la `CCmdUI` objeto dependiendo de si la tecla Virtual correspondiente está bloqueada actualmente.  
  
 No se recomienda la personalización de este controlador de comandos.  
  
-   **ID_INDICATOR_EXT: EXT**indicador seleccione finaliza.  
  
-   **ID_INDICATOR_OVR: OV**e**R**strike indicador.  
  
-   **ID_INDICATOR_REC: REC**indicador ording.  
  
 Actualmente no hay ninguna implementación estándar para estos indicadores.  
  
 Si decide implementar estos indicadores, se recomienda utilizar estos identificadores de indicador y mantener el orden de los indicadores en la barra de estado (es decir, en este orden: EXT, CAP, NUM, Bloq Despl, SOB, REC).  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

