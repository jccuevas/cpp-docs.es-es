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
ms.openlocfilehash: 0f79aaaf59f12e226220e51681f64d0bf1131303
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504343"
---
# <a name="tn022-standard-commands-implementation"></a>TN022: Implementación de comandos estándar

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota describe las implementaciones de comando estándar proporcionadas por MFC 2.0. Lectura [21 de nota técnica](../mfc/tn021-command-and-message-routing.md) primera porque describe los mecanismos utilizados para implementar muchos de los comandos estándares.

Esta descripción supone un conocimiento de las arquitecturas, API y práctica de programación comunes de MFC. Documentado como sin documentar "implementación sólo" API se describen. Esto no es un lugar para empezar a aprender acerca de cómo programar en MFC o de las características de. Hacer referencia a Visual C++ para obtener información general y detalles de las API documentadas.

## <a name="the-problem"></a>El problema

MFC define muchos de los identificadores de comando estándar en el archivo de encabezado AFXRES. H. La compatibilidad con el marco de trabajo para estos comandos varía. Descripción de dónde y cómo las clases de framework controlan estos comandos no sólo le mostrará cómo funciona internamente el marco de trabajo, pero proporcionará información útil sobre cómo personalizar las implementaciones estándar y mostrarle algunas técnicas para implementar sus propios controladores de comandos.

## <a name="contents-of-this-technical-note"></a>Contenido de esta nota técnica

Cada identificador de comando se describe en dos secciones:

- El título: el nombre simbólico del Id. de comando (por ejemplo, ID_FILE_SAVE) seguido por el propósito del comando (por ejemplo, "guarda el documento actual") separados por dos puntos.

- Uno o varios de los párrafos que describe las clases que implementan el comando y lo que hace la implementación predeterminada

Mayoría de las implementaciones de comando de forma predeterminada se viene cableada en mapa de mensajes de la clase base de .NET framework. Hay algunas implementaciones de comando que requieren conexión explícita en la clase derivada. Estos métodos se describen en "Nota". Si ha elegido las opciones adecuadas en el Asistente para aplicaciones, estos controladores predeterminados se conectará automáticamente en la aplicación de esqueleto generada.

## <a name="naming-convention"></a>Convención de nomenclatura

Comandos estándares siguen una convención de nomenclatura simple que se recomienda que utilizar si es posible. Mayoría de los comandos se encuentran en lugares estándar en la barra de menús de la aplicación. El nombre simbólico del comando comienza con "ID_" seguido del nombre del menú emergente estándar, seguido del nombre de elemento de menú. El nombre simbólico es en mayúsculas con separaciones de palabras de un carácter de subrayado. Para los comandos que no tienen nombres de elemento de menú estándar, un nombre de comando lógico se define a partir de "ID_" (por ejemplo, ID_NEXT_PANE).

El prefijo "ID_" se usa para indicar los comandos que están diseñados para enlazarse a los elementos de menú, botones de barra de herramientas u otros objetos de interfaz de usuario de comandos. Los controladores de comandos para controlar los comandos de "ID_" deben usar los mecanismos de ON_COMMAND y ON_UPDATE_COMMAND_UI de la arquitectura de comandos MFC.

Se recomienda que usar el prefijo "IDM_" estándar para los elementos de menú que no siguen la arquitectura de comandos y necesita código específico de menú para habilitarlas y deshabilitarlas. Por supuesto el número de comandos de menú específicos debe ser pequeño, ya que sigue la arquitectura de comandos MFC no sólo aumenta la eficacia de los controladores de comandos (ya que funcionan con las barras de herramientas), pero hace que el código de controlador de comando reutilizables.

## <a name="id-ranges"></a>Intervalos de Id.

Consulte [Nota técnica 20](../mfc/tn020-id-naming-and-numbering-conventions.md) para obtener más detalles sobre el uso de intervalos de identificadores de MFC.

Comandos estándar de MFC se encuentran en el intervalo de 0xE000 a 0xEFFF. Por favor, no confíe en los valores específicos de estos Id. Dado que están sujetos a cambios en versiones futuras de la biblioteca.

La aplicación debe definir sus comandos en el intervalo 0 x 8000 a 0xDFFF.

## <a name="standard-command-ids"></a>Identificadores de comando estándar

Para cada identificador de comando, hay una cadena de mensaje de la línea de mensaje estándar que puede encontrarse en los mensajes de archivo. RC. El identificador de cadena para ese mensaje de menú debe ser el mismo que para el identificador de comando.

- ID_FILE_NEW crea un documento nuevo o está vacía.

    > [!NOTE]
    >  Debe conectarse para su `CWinApp`-derivados de mapa de mensajes de la clase para habilitar esta funcionalidad.

   `CWinApp::OnFileNew` Este comando de manera diferente dependiendo del número de plantillas de documento se implementa en la aplicación. Si solo hay un `CDocTemplate`, `CWinApp::OnFileNew` creará un nuevo documento de ese tipo, así como la clase de marco y la vista adecuada.

   Si hay más de un `CDocTemplate`, `CWinApp::OnFileNew` solicitará al usuario un cuadro de diálogo (AFX_IDD_NEWTYPEDLG) que les permite seleccionar qué tipo usar de documento. Seleccionado `CDocTemplate` se usa para crear el documento.

   Una personalización común de ID_FILE_NEW es proporcionar una diferente y más opciones gráfico de tipos de documento. En este caso puede implementar su propia `CMyApp::OnFileNew` y colóquelo en el mapa de mensajes en lugar de `CWinApp::OnFileNew`. No hay ninguna necesidad de llamar a la implementación de la clase base.

   Otra personalización común de ID_FILE_NEW es proporcionar un comando independiente para la creación de un documento de cada tipo. En este caso debe definir nuevos identificadores de comando, por ejemplo ID_FILE_NEW_CHART y ID_FILE_NEW_SHEET.

- ID_FILE_OPEN abre un documento existente.

    > [!NOTE]
    >  Debe conectarse para su `CWinApp`-derivados de mapa de mensajes de la clase para habilitar esta funcionalidad.

   `CWinApp::OnFileOpen` tiene una implementación muy sencilla de llamar a `CWinApp::DoPromptFileName` seguido `CWinApp::OpenDocumentFile` con el nombre de archivo o ruta de acceso del archivo que se abra. El `CWinApp` rutina implementación `DoPromptFileName` , se abrirá el cuadro de diálogo FileOpen estándar y lo rellena con las extensiones de archivo obtenidas de las plantillas de documento actual.

   Es una personalización común de ID_FILE_OPEN personalizar el cuadro de diálogo FileOpen o agregar más filtros de archivo. La manera recomendada para personalizar esto es reemplazar la implementación predeterminada con su propio cuadro de diálogo FileOpen y llamada `CWinApp::OpenDocumentFile` con el nombre de archivo o ruta de acceso del documento. No hay ninguna necesidad de llamar a la clase base.

- ID_FILE_CLOSE cierra el documento abierto.

   `CDocument::OnFileClose` las llamadas `CDocument::SaveModified` para preguntar al usuario para guardar el documento si se ha modificado y, a continuación, llama a `OnCloseDocument`. Toda la lógica de cierre, incluyendo destruir el documento, se realiza en el `OnCloseDocument` rutina.

    > [!NOTE]
    >  ID_FILE_CLOSE actúa de manera diferente a un mensaje WM_CLOSE o un comando del sistema SC_CLOSE enviados a la ventana de marco de documentos. Cerrar la ventana se cerrará el documento solo si es la última ventana de marco que muestra el documento. Cerrar el documento con ID_FILE_CLOSE no sólo se cerrará el documento, pero se cerrará todas las ventanas de marco que muestra el documento.

- ID_FILE_SAVE guarda el documento actual.

   La implementación usa una rutina auxiliar `CDocument::DoSave` que se usa para ambos `OnFileSave` y `OnFileSaveAs`. Si se guarda un documento que no se ha guardado antes (es decir, no tiene un nombre de ruta de acceso, como en el caso de FileNew) o que ha leído un documento de solo lectura, el `OnFileSave` lógica, que actuará como el ID_FILE_SAVE_AS comando y pedir al usuario que proporcione un nuevo nombre de archivo . El proceso de abrir el archivo y hacer el ahorro real se realiza a través de la función virtual `OnSaveDocument`.

   Hay dos razones comunes para personalizar ID_FILE_SAVE. Para los documentos que no guardan, basta con quitar los botones de barra de herramientas y elementos de menú ID_FILE_SAVE desde la interfaz de usuario. Además, asegúrese de que nunca desfasadas del documento (es decir, nunca llaman a `CDocument::SetModifiedFlag`) y el marco de trabajo nunca hará que el documento se guarde. Para los documentos que guardar en cualquier lugar que no sea un archivo de disco, defina un nuevo comando para esa operación.

   En el caso de un `COleServerDoc`, ID_FILE_SAVE se utiliza para guardar archivos (para documentos normales) y la actualización del archivo (para documentos incrustados).

   Si los datos del documento se almacenan en archivos de disco individuales, pero no desea usar el valor predeterminado `CDocument` serializar la implementación, debe reemplazar `CDocument::OnSaveDocument` en lugar de `OnFileSave`.

- ID_FILE_SAVE_AS guarda el documento actual con un nombre de archivo diferente.

   El `CDocument::OnFileSaveAs` implementación usa el mismo `CDocument::DoSave` rutina auxiliar como `OnFileSave`. El `OnFileSaveAs` comando trata igual que ID_FILE_SAVE si los documentos no tenían ningún nombre de archivo antes de guardar. `COleServerDoc::OnFileSaveAs` implementa la lógica para guardar un archivo de datos de documento normal o guardar un documento de servidor que representa un objeto OLE incrustado en alguna otra aplicación como un archivo independiente.

   Si personaliza la lógica de ID_FILE_SAVE, probablemente deseará personalizar ID_FILE_SAVE_AS de manera similar, o la operación de "Guardar como" no es posible que se aplican al documento. Puede quitar el elemento de menú en la barra de menús si no es necesario.

- ID_FILE_SAVE_COPY_AS guarda un documento de copia actual con un nombre nuevo.

   El `COleServerDoc::OnFileSaveCopyAs` implementación es muy similar a `CDocument::OnFileSaveAs`, salvo que el objeto de documento no está "asociado" en el archivo subyacente después de guardar. Es decir, si el documento en memoria se "modificó" antes de guardar, se sigue "modifica". Además, este comando tiene ningún efecto en el nombre de ruta de acceso o el título almacenado en el documento.

- ID_FILE_UPDATE notifica al contenedor para guardar un documento incrustado.

   El `COleServerDoc::OnUpdateDocument` implementación simplemente notifiies el contenedor que se debe guardar la incrustación. El contenedor, a continuación, llama a las API OLE adecuadas con el fin de guardar el objeto incrustado.

- ID_FILE_PAGE_SETUP invoca un cuadro de diálogo del programa de instalación y diseño de página específica de la aplicación.

   Actualmente no hay ningún estándar para este cuadro de diálogo y el marco de trabajo no tiene ninguna implementación predeterminada de este comando.

   Si decide implementar este comando, se recomienda que usar este identificador de comando.

- ID_FILE_PRINT_SETUP invocar el cuadro de diálogo de instalación de impresión estándar.

    > [!NOTE]
    >  Debe conectarse para su `CWinApp`-derivados de mapa de mensajes de la clase para habilitar esta funcionalidad.

   Este comando invoca el cuadro de diálogo de configuración de impresión estándar que permite al usuario personalizar la impresora y la configuración de impresión para al menos en este documento o a lo sumo todos los documentos de esta aplicación. Debe usar el Panel de Control para cambiar la configuración de impresora predeterminada para todo el sistema.

   `CWinApp::OnFilePrintSetup` tiene una implementación muy sencilla de crear un `CPrintDialog` objeto y llamar a la `CWinApp::DoPrintDialog` función de la implementación. Esto establece la configuración de impresora de aplicación predeterminada.

   La necesidad común para personalizar este comando es permitir la configuración de impresora por documento, que debe almacenarse con el documento cuando se guarda. Para ello debe agregar un controlador de mapa de mensajes en su `CDocument` clase que crea un `CPrintDialog` de objetos, lo inicializa con los atributos de impresora adecuada (normalmente *hDevMode* y *hDevNames*), llame a la `CPrintDialog::DoModal`y guarde la configuración de impresora modificada. Para una implementación sólida, debe mirar la implementación de `CWinApp::DoPrintDialog` para detectar errores y `CWinApp::UpdatePrinterSelection` para tratar con valores predeterminados razonables y seguimiento de cambios de la impresora de todo el sistema.

- Impresión ID_FILE_PRINT estándar del documento actual

    > [!NOTE]
    >  Debe conectarse para su `CView`-derivados de mapa de mensajes de la clase para habilitar esta funcionalidad.

   Este comando imprime el documento actual o, más bien, inicia el proceso de impresión, lo que implica invocar el cuadro de diálogo de impresión estándar y ejecuta el motor de impresión.

   `CView::OnFilePrint` Implemente este comando y el bucle de impresión principal. Lo llama el virtual `CView::OnPreparePrinting` al símbolo del sistema del usuario con el cuadro de diálogo de impresión. A continuación, prepara la salida del controlador de dominio para ir a la impresora, abre el cuadro de diálogo Progreso de la impresión (AFX_IDD_PRINTDLG) y envía el `StartDoc` escape a la impresora. `CView::OnFilePrint` También contiene el bucle de impresión orientada a la página principal. Para cada página, llamadas virtual `CView::OnPrepareDC` seguido por un `StartPage` escape y una llamada virtual `CView::OnPrint` para esa página. Cuando haya terminado, el virtual `CView::OnEndPrinting` se llama a, y se cierra el cuadro de diálogo de progreso de la impresión.

   La arquitectura de impresión de MFC está diseñada para enlazar de muchas maneras diferentes de impresión y vista previa. Normalmente, encontrará los diversos `CView` funciones reemplazables adecuadas para las tareas de impresión orientada a páginas. Solo en el caso de una aplicación que usa la impresora para la salida orientada a distintos de páginas, debería encontrar la necesidad de reemplazar la implementación ID_FILE_PRINT.

- Escriba ID_FILE_PRINT_PREVIEW el modo de vista previa de impresión del documento actual.

    > [!NOTE]
    >  Debe conectarse para su `CView`-derivados de mapa de mensajes de la clase para habilitar esta funcionalidad.

   `CView::OnFilePrintPreview` se inicia el modo de vista previa de impresión mediante una llamada a la función auxiliar documentado `CView::DoPrintPreview`. `CView::DoPrintPreview` es el principal motor para el bucle de vista previa de impresión, al igual que `OnFilePrint` es el motor principal para el bucle de impresión.

   La operación de vista previa de impresión puede personalizarse en una variedad de formas al pasar parámetros distintos a `DoPrintPreview`. Consulte [30 de nota técnica](../mfc/tn030-customizing-printing-and-print-preview.md), donde explican algunos de los detalles de la vista previa de impresión y cómo personalizarlo.

- ID_FILE_MRU_FILE1... FILE16 Un intervalo de identificadores de comando para los elementos utilizados Recientemente del archivo **lista**.

   `CWinApp::OnUpdateRecentFileMenu` es un controlador de interfaz de usuario de comandos de actualización que es uno de los usos más avanzados del mecanismo ON_UPDATE_COMMAND_UI. En el recurso de menú, sólo debe definir un elemento de menú único con el Id. de ID_FILE_MRU_FILE1. Ese elemento de menú permanece deshabilitado inicialmente.

   Como los elementos utilizados Recientemente lista crece, menú más elementos se agregan a la lista. El estándar `CWinApp` implementación el valor predeterminado es el límite de estándar de los cuatro archivos usados más recientemente. Puede cambiar el valor predeterminado mediante una llamada a `CWinApp::LoadStdProfileSettings` con un valor mayor o menor. La lista MRU se almacena en la aplicación. Archivo INI. La lista se carga en la aplicación `InitInstance` funcionar si se llama a `LoadStdProfileSettings`y se guarda cuando se cierra la aplicación. El controlador de interfaz de usuario de comandos de actualización MRU también convertirá las rutas de acceso absolutas para rutas de acceso relativas para su presentación en el menú archivo.

   `CWinApp::OnOpenRecentFile` es el controlador ON_COMMAND que realiza el comando real. Simplemente obtiene el nombre de archivo en la lista de elementos utilizados Recientemente y llamadas `CWinApp::OpenDocumentFile`, que hace todo el trabajo de abrir el archivo y actualizar la lista MRU.

   No se recomienda la personalización de este controlador de comandos.

- ID_EDIT_CLEAR borra la selección actual

   Actualmente no hay ninguna implementación estándar para este comando. Esto debe implementar para cada `CView`-clase derivada.

   `CEditView` Proporciona una implementación de este comando mediante `CEdit::Clear`. El comando está deshabilitado si no hay ninguna selección actual.

   Si decide implementar este comando, se recomienda que usar este identificador de comando.

- ID_EDIT_CLEAR_ALL borra todo el documento.

   Actualmente no hay ninguna implementación estándar para este comando. Esto debe implementar para cada `CView`-clase derivada.

   Si decide implementar este comando, se recomienda que usar este identificador de comando. Vea el ejemplo de Tutorial de MFC [SCRIBBLE](../visual-cpp-samples.md) para una implementación de ejemplo.

- ID_EDIT_COPY copia la selección actual en el Portapapeles.

   Actualmente no hay ninguna implementación estándar para este comando. Esto debe implementar para cada `CView`-clase derivada.

   `CEditView` Proporciona una implementación de este comando, que copia el texto seleccionado actualmente en el Portapapeles como CF_TEXT mediante `CEdit::Copy`. El comando está deshabilitado si no hay ninguna selección actual.

   Si decide implementar este comando, se recomienda que usar este identificador de comando.

- ID_EDIT_CUT corta la selección actual en el Portapapeles.

   Actualmente no hay ninguna implementación estándar para este comando. Esto debe implementar para cada `CView`-clase derivada.

   `CEditView` Proporciona una implementación de este comando, que corta el texto seleccionado actualmente en el Portapapeles como CF_TEXT mediante `CEdit::Cut`. El comando está deshabilitado si no hay ninguna selección actual.

   Si decide implementar este comando, se recomienda que usar este identificador de comando.

- ID_EDIT_FIND comienza la operación de búsqueda, aparece el cuadro de diálogo no modal de búsqueda.

   Actualmente no hay ninguna implementación estándar para este comando. Esto debe implementar para cada `CView`-clase derivada.

   `CEditView` Proporciona una implementación de este comando, que llama a la función auxiliar implementación `OnEditFindReplace` para usar y almacenar la configuración anterior de buscar y reemplazar en las variables de implementación privada. La `CFindReplaceDialog` clase se utiliza para administrar el cuadro de diálogo no modal para preguntar al usuario.

   Si decide implementar este comando, se recomienda que usar este identificador de comando.

- ID_EDIT_PASTE inserta el contenido actual del Portapapeles.

   Actualmente no hay ninguna implementación estándar para este comando. Esto debe implementar para cada `CView`-clase derivada.

   `CEditView` Proporciona una implementación de este comando, que copia los datos del Portapapeles actuales reemplazando el texto seleccionado con `CEdit::Paste`. El comando está deshabilitado si no hay ningún **CF_TEXT** en el Portapapeles.

   `COleClientDoc` simplemente proporciona un controlador de interfaz de usuario de comandos de actualización para este comando. Si el Portapapeles no contiene un elemento OLE incrustable/objeto, se deshabilitará el comando. Usted es responsable de escribir el controlador para el comando real para realizar el pegado real. Si una aplicación OLE también puede pegar a otros formatos, debe proporcionar su propio controlador de interfaz de usuario del comando update en la vista o el documento (es decir, en algún punto antes de `COleClientDoc` en la ruta de destino de comando).

   Si decide implementar este comando, se recomienda que usar este identificador de comando.

   Para reemplazar la implementación estándar de OLE, utilice `COleClientItem::CanPaste`.

- ID_EDIT_PASTE_LINK inserta un vínculo de contenido actual del Portapapeles.

   Actualmente no hay ninguna implementación estándar para este comando. Esto debe implementar para cada `CView`-clase derivada.

   `COleDocument` simplemente proporciona un controlador de interfaz de usuario de comandos de actualización para este comando. Si el Portapapeles no contiene vinculable OLE/objeto de elemento, se deshabilitará el comando. Usted es responsable de escribir el controlador para el comando real para realizar el pegado real. Si una aplicación OLE también puede pegar a otros formatos, debe proporcionar su propio controlador de interfaz de usuario del comando update en la vista o el documento (es decir, en algún punto antes de `COleDocument` en la ruta de destino de comando).

   Si decide implementar este comando, se recomienda que usar este identificador de comando.

   Para reemplazar la implementación estándar de OLE, utilice `COleClientItem::CanPasteLink`.

- ID_EDIT_PASTE_SPECIAL inserta el contenido actual del Portapapeles con opciones.

   Actualmente no hay ninguna implementación estándar para este comando. Esto debe implementar para cada `CView`-clase derivada. MFC no proporciona este cuadro de diálogo.

   Si decide implementar este comando, se recomienda que usar este identificador de comando.

- ID_EDIT_REPEAT se repite la última operación.

   Actualmente no hay ninguna implementación estándar para este comando. Esto debe implementar para cada `CView`-clase derivada.

   `CEditView` Proporciona una implementación de este comando para repetir la última operación de búsqueda. Se usan las variables de la implementación privada de la última búsqueda. El comando está deshabilitado si no se puede intentar una operación de búsqueda.

   Si decide implementar este comando, se recomienda que usar este identificador de comando.

- ID_EDIT_REPLACE comienza la operación de reemplazo, aparece el cuadro de diálogo no modal de reemplazo.

   Actualmente no hay ninguna implementación estándar para este comando. Esto debe implementar para cada `CView`-clase derivada.

   `CEditView` Proporciona una implementación de este comando, que llama a la función auxiliar implementación `OnEditFindReplace` para usar y almacenar la configuración anterior de buscar y reemplazar en las variables de implementación privada. La `CFindReplaceDialog` clase se utiliza para administrar el cuadro de diálogo no modal que solicita al usuario.

   Si decide implementar este comando, se recomienda que usar este identificador de comando.

- ID_EDIT_SELECT_ALL selecciona todo el documento.

   Actualmente no hay ninguna implementación estándar para este comando. Esto debe implementar para cada `CView`-clase derivada.

   `CEditView` Proporciona una implementación de este comando, que selecciona todo el texto del documento. El comando está deshabilitado si no hay ningún texto para seleccionar.

   Si decide implementar este comando, se recomienda que usar este identificador de comando.

- ID_EDIT_UNDO deshace la última operación.

   Actualmente no hay ninguna implementación estándar para este comando. Esto debe implementar para cada `CView`-clase derivada.

   `CEditView` Proporciona una implementación de este comando, use `CEdit::Undo`. El comando está deshabilitado si `CEdit::CanUndo` devuelve FALSE.

   Si decide implementar este comando, se recomienda que usar este identificador de comando.

- ID_EDIT_REDO Rehace la última operación.

   Actualmente no hay ninguna implementación estándar para este comando. Esto debe implementar para cada `CView`-clase derivada.

   Si decide implementar este comando, se recomienda que usar este identificador de comando.

- ID_WINDOW_NEW abre otra ventana del documento activo.

   `CMDIFrameWnd::OnWindowNew` Esta eficaz característica se implementa mediante la plantilla de documento del documento actual para crear otro marco que contiene otra vista del documento actual.

   Al igual que la mayoría múltiples documentos (MDI) de la interfaz comandos del menú Ventana, el comando está deshabilitado si no hay ninguna ventana secundaria MDI activa.

   No se recomienda la personalización de este controlador de comandos. Si desea proporcionar un comando que crea vistas adicionales o ventanas de marco, probablemente será mejor que tener que inventar su propio comando. Puede clonar el código de `CMDIFrameWnd::OnWindowNew` y modificarlo para las clases de marco y la vista específicas de su agrado.

- ID_WINDOW_ARRANGE organiza los iconos en la parte inferior de una ventana MDI.

   `CMDIFrameWnd` Implemente este comando estándar de MDI en una función auxiliar de implementación `OnMDIWindowCmd`. Esta aplicación auxiliar de identificadores de comando asigna a los mensajes de Windows de MDI y, por tanto, puede compartir una gran cantidad de código.

   Al igual que la mayoría de los comandos de menú ventana MDI, el comando está deshabilitado si no hay ninguna ventana secundaria MDI activa.

   No se recomienda la personalización de este controlador de comandos.

- Windows ID_WINDOW_CASCADE cascadas para que se superpongan.

   `CMDIFrameWnd` Implemente este comando estándar de MDI en una función auxiliar de implementación `OnMDIWindowCmd`. Esta aplicación auxiliar de identificadores de comando asigna a los mensajes de Windows de MDI y, por tanto, puede compartir una gran cantidad de código.

   Al igual que la mayoría de los comandos de menú ventana MDI, el comando está deshabilitado si no hay ninguna ventana secundaria MDI activa.

   No se recomienda la personalización de este controlador de comandos.

- Windows ID_WINDOW_TILE_HORZ mosaicos horizontalmente.

   Este comando se implementa en `CMDIFrameWnd` al igual que ID_WINDOW_CASCADE, salvo que se usa un mensaje de Windows de MDI diferente para la operación.

   Debe elegir la orientación de mosaico predeterminado para la aplicación. Para ello, cambie el identificador para el elemento de menú de ventana "Mosaico" ID_WINDOW_TILE_HORZ o ID_WINDOW_TILE_VERT.

- Windows ID_WINDOW_TILE_VERT iconos verticalmente.

   Este comando se implementa en `CMDIFrameWnd` al igual que ID_WINDOW_CASCADE, salvo que se usa un mensaje de Windows de MDI diferente para la operación.

   Debe elegir la orientación de mosaico predeterminado para la aplicación. Para ello, cambie el identificador para el elemento de menú de ventana "Mosaico" ID_WINDOW_TILE_HORZ o ID_WINDOW_TILE_VERT.

- Interfaz de teclado ID_WINDOW_SPLIT al divisor.

   `CView` controla este comando para el `CSplitterWnd` implementación. Si la vista es parte de una ventana divisora, va a delegar este comando a la función de la implementación `CSplitterWnd::DoKeyboardSplit`. Esto colocará el divisor en un modo que permitirá a los usuarios de teclado dividir o quitar la división de una ventana divisora.

   Este comando está deshabilitado si la vista no está en un divisor.

   No se recomienda la personalización de este controlador de comandos.

- ID_APP_ABOUT invoca el cuadro de diálogo About.

   No hay ninguna implementación estándar para el cuadro de diálogo acerca de la aplicación. La aplicación creada mediante AppWizard predeterminada creará una clase de cuadro de diálogo personalizado para su aplicación y usarlo como el cuadro acerca de. AppWizard también escribirá el controlador de comandos trivial que controla este comando e invoca el cuadro de diálogo.

   Casi siempre implementará este comando.

- ID_APP_EXIT salir de la aplicación.

   `CWinApp::OnAppExit` Este comando se controla mediante el envío de un mensaje WM_CLOSE a la ventana principal de la aplicación. El estándar de cierre de la aplicación (solicitar archivos modificados y así sucesivamente) se controla mediante el `CFrameWnd` implementación.

   No se recomienda la personalización de este controlador de comandos. Reemplazar `CWinApp::SaveAllModified` o `CFrameWnd` se recomienda la lógica de cierre.

   Si decide implementar este comando, se recomienda que usar este identificador de comando.

- ID_HELP_INDEX se enumeran temas de la Ayuda de. Archivo HLP.

    > [!NOTE]
    >  Debe conectarse para su `CWinApp`-derivados de mapa de mensajes de la clase para habilitar esta funcionalidad.

   `CWinApp::OnHelpIndex` controla este comando llamando trivialmente `CWinApp::WinHelp`.

   No se recomienda la personalización de este controlador de comandos.

- ID_HELP_USING muestra la ayuda sobre cómo usar la Ayuda.

    > [!NOTE]
    >  Debe conectarse para su `CWinApp`-derivados de mapa de mensajes de la clase para habilitar esta funcionalidad.

   `CWinApp::OnHelpUsing` controla este comando llamando trivialmente `CWinApp::WinHelp`.

   No se recomienda la personalización de este controlador de comandos.

- MAYÚS-F1 de ID_CONTEXT_HELP entra en modo de ayuda.

    > [!NOTE]
    >  Debe conectarse para su `CWinApp`-derivados de mapa de mensajes de la clase para habilitar esta funcionalidad.

   `CWinApp::OnContextHelp` Este comando se controla estableciendo el cursor del modo de ayuda, escribir un bucle modal y espera a que el usuario seleccionar una ventana para obtener ayuda sobre. Consulte [Nota técnica 28](../mfc/tn028-context-sensitive-help-support.md) para obtener más detalles sobre la implementación de la Ayuda de MFC.

   No se recomienda la personalización de este controlador de comandos.

- ID_HELP proporciona ayuda en el contexto actual

    > [!NOTE]
    >  Debe conectarse para su `CWinApp`-derivados de mapa de mensajes de la clase para habilitar esta funcionalidad.

   `CWinApp::OnHelp` Este comando se controla al obtener el contexto de ayuda adecuada para el contexto de la aplicación actual. Esto controla la Ayuda de F1 simple, ayuda en cuadros de mensaje y así sucesivamente. Consulte [Nota técnica 28](../mfc/tn028-context-sensitive-help-support.md) para obtener más detalles sobre la MFC ayudan a la implementación.

   No se recomienda la personalización de este controlador de comandos.

- ID_DEFAULT_HELP muestra la Ayuda de forma predeterminada para el contexto

    > [!NOTE]
    >  Debe conectarse para su `CWinApp`-derivados de mapa de mensajes de la clase para habilitar esta funcionalidad.

   Este comando normalmente se asigna a `CWinApp::OnHelpIndex`.

   Si se desea una distinción entre ayuda predeterminada y el índice, se puede proporcionar un controlador de comandos diferente.

- ID_NEXT_PANE va al panel siguiente

   `CView` controla este comando para el `CSplitterWnd` implementación. Si la vista es parte de una ventana divisora, va a delegar este comando a la función de la implementación `CSplitterWnd::OnNextPaneCmd`. La vista activa esto pasará al siguiente panel en el divisor.

   Este comando está deshabilitado si la vista no está en un divisor o no hay ningún panel para ir al siguiente.

   No se recomienda la personalización de este controlador de comandos.

- ID_PREV_PANE va al panel anterior

   `CView` controla este comando para el `CSplitterWnd` implementación. Si la vista es parte de una ventana divisora, va a delegar este comando a la función de la implementación `CSplitterWnd::OnNextPaneCmd`. Esto moverá la vista activa al panel anterior en el divisor.

   Este comando está deshabilitado si la vista no está en un divisor o no hay ningún panel para ir al anterior.

   No se recomienda la personalización de este controlador de comandos.

- ID_OLE_INSERT_NEW inserta un nuevo objeto OLE

   Actualmente no hay ninguna implementación estándar para este comando. Debe implementar esto para su `CView`-clase derivada para insertar un nuevo elemento/objeto OLE en la selección actual.

   Todas las aplicaciones de cliente OLE deben implementar este comando. Asistente para aplicaciones, con la opción OLE, creará una implementación de esqueleto `OnInsertObject` en la clase de vista que debe completar.

   Vea el ejemplo OLE de MFC [OCLIENT](../visual-cpp-samples.md) ejemplo para una implementación completa de este comando.

- ID_OLE_EDIT_LINKS edita vínculos OLE

   `COleDocument` Este comando se controla mediante la implementación proporcionada por MFC del cuadro de diálogo vínculos OLE estándar. Se tiene acceso a la implementación de este cuadro de diálogo a través de la `COleLinksDialog` clase. Si el documento actual no contiene los vínculos, se deshabilita el comando.

   No se recomienda la personalización de este controlador de comandos.

- ID_OLE_VERB_FIRST... ÚLTIMO intervalo de un identificador para los verbos OLE

   `COleDocument` usa este intervalo de Id. de comando para los verbos admitidos por el elemento OLE actualmente seleccionado/objeto. Esto debe ser un intervalo como un tipo de elemento u objeto determinado de OLE puede admitir verbos personalizados de cero o más. En el menú de la aplicación, debe tener un elemento de menú con el Id. de ID_OLE_VERB_FIRST. Cuando se ejecuta el programa, el menú se actualizará con la descripción de verbo del menú correspondiente (o menú emergente con muchos de los verbos). La administración del menú OLE se controla mediante `AfxOleSetEditMenu`hecho en el controlador de interfaz de usuario de comandos de actualización para este comando.

   No hay ningún controlador de comando explícito para controlar cada uno de identificador del comando en este intervalo. `COleDocument::OnCmdMsg` se reemplaza para interceptar todos los identificadores de comando en este intervalo, convertirlos en números de base cero del verbo e iniciar el servidor para ese verbo (mediante `COleClientItem::DoVerb`).

   No se recomienda personalización u otros usos de este intervalo de Id. de comando.

- ID_VIEW_TOOLBAR alterna la barra de herramientas activar y desactivar

   `CFrameWnd` controla este comando y el controlador de interfaz de usuario de comando de actualización para alternar el estado de visibilidad de la barra de herramientas. La barra de herramientas debe ser una ventana secundaria del marco con la ventana secundaria de la Id. de AFX_IDW_TOOLBAR. El controlador de comandos alterna la visibilidad de la ventana de la barra de herramientas. `CFrameWnd::RecalcLayout` se usa para dibujar la ventana de marco con la barra de herramientas en su nuevo estado. El controlador de interfaz de usuario de comando de actualización comprueba el elemento de menú cuando la barra de herramientas está visible.

   No se recomienda la personalización de este controlador de comandos. Si desea agregar barras de herramientas adicionales, desea clonar y modificar el controlador de comandos y el controlador de interfaz de usuario de comando de actualización para este comando.

- ID_VIEW_STATUS_BAR la barra de estado en activa y desactiva

   Este comando se implementa en `CFrameWnd` igual que ID_VIEW_TOOLBAR, excepto una ventana de otro elemento secundario ID (AFX_IDW_STATUS_BAR) se utiliza.

## <a name="update-only-command-handlers"></a>Controladores de comandos sólo actualizar

Se utilizan varios identificadores de comando estándar como indicadores en barras de estado. Estos usan el mismo mecanismo de control de interfaz de usuario de comando de actualización para mostrar su estado actual de visual durante el tiempo de inactividad de la aplicación. Puesto que no se pueden seleccionar por el usuario (es decir, no se puede insertar un panel de barra de estado), entonces no tiene sentido tener un controlador ON_COMMAND para estos identificadores de comando.

- ID_INDICATOR_CAPS: Indicador de bloqueo de CAP.

- ID_INDICATOR_NUM: Indicador NUM lock.

- ID_INDICATOR_SCRL: Indicador de bloqueo Bloq Despl.

- ID_INDICATOR_KANA: KANA indicador de bloqueo (se aplica sólo a los sistemas japonés).

Tres de estos se implementan en `CFrameWnd::OnUpdateKeyIndicator`, una aplicación auxiliar de implementación que usa el identificador de comando para asignar a la clave Virtual adecuada. Una implementación común habilita o deshabilita (para los paneles de estado deshabilitados = no hay texto) la `CCmdUI` objeto dependiendo de si la tecla Virtual correspondiente está bloqueada actualmente.

No se recomienda la personalización de este controlador de comandos.

- ID_INDICATOR_EXT: Indicador de select extendido.

- ID_INDICATOR_OVR: Indicador de sobrescritura.

- ID_INDICATOR_REC: Indicador de grabación.

Actualmente no hay ninguna implementación estándar para estos indicadores.

Si decide implementar estos indicadores, se recomienda utilizar estos identificadores de indicador y mantener el orden de los indicadores de la barra de estado (es decir, en este orden: EXT, CAP, NUM, Bloq Despl, SOB, REC).

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

