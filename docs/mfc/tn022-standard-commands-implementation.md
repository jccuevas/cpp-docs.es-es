---
title: "TN022: Implementaci&#243;n de comandos est&#225;ndar | Microsoft Docs"
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
  - "vc.commands"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "comandos, estándar"
  - "ID_APP_ABOUT (comando)"
  - "ID_APP_EXIT (comando)"
  - "ID_CONTEXT_HELP (comando)"
  - "ID_DEFAULT_HELP (comando)"
  - "ID_EDIT_CLEAR (comando)"
  - "ID_EDIT_CLEAR_ALL (comando)"
  - "ID_EDIT_COPY (comando)"
  - "ID_EDIT_CUT (comando)"
  - "ID_EDIT_FIND (comando)"
  - "ID_EDIT_PASTE (comando)"
  - "ID_EDIT_PASTE_LINK (comando)"
  - "ID_EDIT_PASTE_SPECIAL (comando)"
  - "ID_EDIT_REDO (comando)"
  - "ID_EDIT_REPEAT (comando)"
  - "ID_EDIT_REPLACE (comando)"
  - "ID_EDIT_SELECT_ALL (comando)"
  - "ID_EDIT_UNDO (comando)"
  - "ID_FILE_CLOSE (comando)"
  - "ID_FILE_NEW (comando)"
  - "ID_FILE_OPEN (comando)"
  - "ID_FILE_PAGE_SETUP (comando)"
  - "ID_FILE_PRINT (comando)"
  - "ID_FILE_PRINT_PREVIEW (comando)"
  - "ID_FILE_PRINT_SETUP (comando)"
  - "ID_FILE_SAVE (comando)"
  - "ID_FILE_SAVE_AS (comando)"
  - "ID_FILE_SAVE_COPY_AS (comando)"
  - "ID_FILE_UPDATE (comando)"
  - "ID_HELP (comando)"
  - "ID_HELP_INDEX (comando)"
  - "ID_HELP_USING (comando)"
  - "ID_INDICATOR_CAPS (comando)"
  - "ID_INDICATOR_EXT (comando)"
  - "ID_INDICATOR_KANA (comando)"
  - "ID_INDICATOR_NUM (comando)"
  - "ID_INDICATOR_OVR (comando)"
  - "ID_INDICATOR_REC (comando)"
  - "ID_INDICATOR_SCRL (comando)"
  - "ID_NEXT_PANE (comando)"
  - "ID_OLE_EDIT_LINKS (comando)"
  - "ID_OLE_INSERT_NEW (comando)"
  - "ID_OLE_VERB_FIRST (comando)"
  - "ID_PREV_PANE (comando)"
  - "ID_VIEW_STATUS_BAR (comando)"
  - "ID_VIEW_TOOLBAR (comando)"
  - "ID_WINDOW_ARRANGE (comando)"
  - "ID_WINDOW_CASCADE (comando)"
  - "ID_WINDOW_NEW (comando)"
  - "ID_WINDOW_SPLIT (comando)"
  - "ID_WINDOW_TILE_HORZ (comando)"
  - "ID_WINDOW_TILE_VERT (comando)"
  - "comandos estándar"
  - "TN022"
ms.assetid: a7883b46-23f7-4870-ac3a-804aed9258b5
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN022: Implementaci&#243;n de comandos est&#225;ndar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Esta nota describe las implementaciones de comando estándar proporcionadas por MFC 2,0.  Lea [Nota técnica 21](../mfc/tn021-command-and-message-routing.md) primero porque describe los mecanismos utilizados para implementar muchos de los comandos estándar.  
  
 Esta descripción se supone el conocimiento de las arquitecturas de MFC, de API, y el habitual de programación.  Documentado así como se describe en “implementación indocumentada sólo” API.  Esto no es un punto de partida para conocer el sobre las características de o cómo programar en MFC.  Consulte en Visual C\+\+ para obtener información general y para los detalles de las API documentadas.  
  
## El problema  
 MFC define muchos id. de comando estándar en el archivo de encabezado AFXRES.H.  La compatibilidad del marco de trabajo para estos comandos varía.  La comprensión de dónde y cómo las clases del marco de trabajo administran estos comandos no solo muestran cómo el marco funciona internamente pero proporcionan información útil sobre cómo personalizar las implementaciones estándar y enseñarle a algunas técnicas para implementar a poseer los controladores de comando.  
  
## Contenido de la nota técnica de Esta  
 Cada identificador de comando se describe en dos secciones:  
  
-   El título: el nombre simbólico del identificador de comando \(por ejemplo, **ID\_FILE\_SAVE**\) seguido del propósito de comando \(por ejemplo, “guarda el documento actual”\) separados por dos puntos.  
  
-   Uno o más párrafos que describen las clases que implementan el comando, y lo que hace la implementación predeterminada  
  
 La mayoría de las implementaciones predeterminadas de comando son prealambradas en el mapa de mensajes de la clase base del marco.  Hay algunas implementaciones de comando que requieren la conexión explícito en la clase derivada.  Éstos se describen en “notas”.  Si eligió las opciones correctas en AppWizard, estos controladores predeterminados estarán conectados en la aplicación esqueleto generada.  
  
## Convención de nomenclatura  
 Los comandos estándar utilizan una convención de nomenclatura simple que le recomendamos uso si es posible.  La mayoría de los comandos estándar se encuentran en lugares estándar en la barra de menús de una aplicación.  El nombre simbólico de comando comienza con “ID\_” seguido por el nombre del elemento emergente estándar, seguido por el nombre del elemento de menú.  El nombre simbólico está en mayúscula con divisiones de palabras de subrayado.  Para los comandos que no tienen nombres estándar del elemento de menú, un nombre de comando lógico es el iniciar definido con “ID\_” \(por ejemplo, **ID\_NEXT\_PANE**\).  
  
 Utilizamos el prefijo “ID\_” para indicar los comandos que están diseñados para ser enlazados a los elementos de menú, los botones de la barra de herramientas, u otros objetos de la interfaz de usuario del comando.  Controladores de comandos que administran comandos de “ID\_” deben utilizar mecanismos de `ON_COMMAND` y de `ON_UPDATE_COMMAND_UI` de la arquitectura de comando de MFC.  
  
 Le recomendamos utilizamos el prefijo del estándar “IDM\_” para los elementos de menú que no siguen la arquitectura del comando y no necesitan código menú\- concreto habilitarlos y deshabilitar.  Por supuesto el número de comandos específicos del menú debe ser pequeño desde el siguiente de comando de MFC que la arquitectura no solo crea controladores de comandos más eficaces \(dado que ejecutarán las barras de herramientas\) pero que hace el código de controlador de comandos reutilizable.  
  
## Intervalos de identificador  
 Hace referencia a [Nota técnica 20](../mfc/tn020-id-naming-and-numbering-conventions.md) para obtener más detalles sobre el uso de los intervalos de identificador en MFC.  
  
 Los comandos estándar de MFC se encuentran en el intervalo 0xE000 a 0xEFFF.  No confíe en los valores específicos de estos id. ya que están sujetas a cambios en versiones futuras de biblioteca.  
  
 La aplicación debe definir los comandos en el intervalo 0x8000 a 0xDFFF.  
  
## Id. de comando estándar  
 Para cada identificador de comando, hay una cadena de solicitud estándar de línea de mensajes que se puede encontrar en el archivo PROMPTS.RC.  El identificador de cadena del indicador de menú debe ser igual que para el identificador de comando  
  
-   ID\_FILE\_NEW crea un nuevo y vacío documento.  
  
    > [!NOTE]
    >  Debe conectarse esto a `CWinApp`\- mapa derivado del mensaje de la clase para habilitar esta funcionalidad.  
  
     `CWinApp::OnFileNew` implementa este comando de manera diferente dependiendo del número de plantillas de documento en la aplicación.  Si solo hay un `CDocTemplate`, `CWinApp::OnFileNew` creará un nuevo documento de ese tipo, así como la clase correspondiente del cuadro y vistas.  
  
     Si hay más de un `CDocTemplate`, `CWinApp::OnFileNew` pedirá al usuario un diálogo \(**AFX\_IDD\_NEWTYPEDLG**\) que les permite seleccionar qué tipo de documento a utilizar.  `CDocTemplate` seleccionado se utiliza para crear el documento.  
  
     Una personalización común de `ID_FILE_NEW` es proporcionar una opción diferente y más gráfica de tipos de documento.  En este caso puede implementar dispone **CMyApp::OnFileNew** y colocarlo en el mapa de mensajes en lugar de `CWinApp::OnFileNew`.  No hay necesidad de llamar a la implementación de la clase base.  
  
     Otra personalización común de `ID_FILE_NEW` es proporcionar un comando independiente para crear un documento de cada tipo.  En este caso debe definir nuevos id. de comando, por ejemplo ID\_FILE\_NEW\_CHART e ID\_FILE\_NEW\_SHEET.  
  
-   ID\_FILE\_OPEN abre un documento existente.  
  
    > [!NOTE]
    >  Debe conectarse esto a `CWinApp`\- mapa derivado del mensaje de la clase para habilitar esta funcionalidad.  
  
     `CWinApp::OnFileOpen` tiene mismo una implementación sencilla de llamar a **CWinApp::DoPromptFileName** seguido de `CWinApp::OpenDocumentFile` con el nombre de archivo o de ruta de acceso del archivo para abrirlo.  La implementación **DoPromptFileName** rutinario de `CWinApp` extrae para abrir el cuadro de diálogo estándar FileOpen y lo rellena con las extensiones de archivo obtenidas de plantillas de documento actuales.  
  
     Una personalización común de `ID_FILE_OPEN` es personalizar el diálogo FileOpen o agregar filtros de archivo adicionales.  La manera recomendada de personalizar esto es reemplazar la implementación predeterminada con dispone del diálogo FileOpen; la llamada `CWinApp::OpenDocumentFile` con el nombre del archivo o la ruta de documento.  No hay necesidad de llamar a la clase base.  
  
-   ID\_FILE\_CLOSE cierre actualmente el documento abierto.  
  
     **CDocument::OnFileClose** llama `CDocument::SaveModified` para solicitar al usuario guardar el documento si se ha modificado y después llama `OnCloseDocument`.  Toda la lógica cerrada, incluida la destrucción del documento, se hace en la rutina de `OnCloseDocument` .  
  
    > [!NOTE]
    >  **ID\_FILE\_CLOSE** actúa de manera diferente de un mensaje de `WM_CLOSE` o un comando del sistema de **SC\_CLOSE** enviado a la ventana cuadro de documentos.  Al cerrar una ventana se cierra el documento sólo si es la última ventana de marco que muestra el documento.  Al cerrar el documento con **ID\_FILE\_CLOSE** no solo se cerrará el documento pero se cerrará abajo todas las ventanas de marco que muestran el documento.  
  
-   ID\_FILE\_SAVE guarda el documento actual.  
  
     La implementación utiliza una aplicación auxiliar **CDocument::DoSave** tiene que se utiliza para **OnFileSave** y **OnFileSaveAs**.  Si guarda un documento de que no se ha guardado antes \(es decir, no tiene un nombre de ruta, como en el caso de FileNew\) o de que se ha leído de un documento de sólo lectura, la lógica de **OnFileSave** actuará como el comando de **ID\_FILE\_SAVE\_AS** y pedirá al usuario proporcione un nombre de archivo nuevo.  El proceso real de abrir el archivo y haga un nombre se hace con la función virtual `OnSaveDocument`.  
  
     Hay dos razones comunes para personalizar **ID\_FILE\_SAVE**.  Para los documentos que no se guardan, quitar los elementos de menú y los botones de la barra de herramientas de **ID\_FILE\_SAVE** de la interfaz de usuario.  Asegúrese también de que nunca modificado el documento \(es decir, nunca llame a `CDocument::SetModifiedFlag`\) y el marco nunca producirá el documento que se va a guardar.  Para los documentos que guardan a en un lugar distinto de un archivo de disco, defina un nuevo comando de esa operación.  
  
     En el caso de `COleServerDoc`, **ID\_FILE\_SAVE** se utiliza para el almacenamiento de archivo \(para los documentos normales\) y la actualización del archivo \(para los documentos incrustados\).  
  
     Si los datos del documento se almacena en archivos de disco individuales, pero no desea utilizar **CDocument** predeterminado serializa la implementación, debe invalidar `CDocument::OnSaveDocument` en lugar de **OnFileSave**.  
  
-   ID\_FILE\_SAVE\_AS guarda el documento actual en nombre de archivo diferente.  
  
     La implementación de **CDocument::OnFileSaveAs** utiliza la misma rutina auxiliar de **CDocument::DoSave** que **OnFileSave**.  Controlan el comando de **OnFileSaveAs** como **ID\_FILE\_SAVE** si los documentos no tienen ningún nombre de archivo antes de guardar.  **COleServerDoc::OnFileSaveAs** implementa la lógica para guardar un archivo de datos normal de documento o guardar un documento de servidor que representa un objeto OLE incrustado en otra aplicación como un archivo independiente.  
  
     Si personaliza la lógica de **ID\_FILE\_SAVE**, es posible que desee personalizar **ID\_FILE\_SAVE\_AS** de manera similar o la operación de “Guardar como” no se puede aplicar al documento.  Puede quitar el elemento de menú de la barra de menús si no es necesaria.  
  
-   ID\_FILE\_SAVE\_COPY\_AS guarda en copia el documento actual bajo el nuevo nombre.  
  
     La implementación de **COleServerDoc::OnFileSaveCopyAs** es muy similar a **CDocument::OnFileSaveAs**, salvo que el objeto de documento “no está adjunto” en el archivo subyacente después de guardar.  Es decir, si el documento de en\- memoria “se modificó” antes de que se guarde, continúa “se modifica”.  Además, este comando no tiene efecto en el nombre o el título de ruta almacenado en el documento.  
  
-   ID\_FILE\_UPDATE Notifies el contenedor para guardar un documento incrustado.  
  
     De `COleServerDoc::OnUpdateDocument` de implementación los notifiies simplemente el contenedor que la incrustación debe guardarse.  El contenedor llama a las API OLE adecuado para guardar el objeto incrustado.  
  
-   ID\_FILE\_PAGE\_SETUP invoca un diálogo específico de la aplicación de la configuración de página y de diseño.  
  
     Actualmente no hay un estándar para este diálogo, y el marco no tiene ninguna implementación predeterminada de este comando.  
  
     Si decide implementar este comando, le recomendamos utilizamos este identificador de comando  
  
-   ID\_FILE\_PRINT\_SETUP invocan el diálogo estándar de la configuración de impresión.  
  
    > [!NOTE]
    >  Debe conectarse esto a `CWinApp`\- mapa derivado del mensaje de la clase para habilitar esta funcionalidad.  
  
     Este comando invoca el diálogo estándar de la configuración de impresión que permite al usuario personalizar la configuración de la impresora y la impresión para al menos este documento o a lo sumo todos los documentos de esta aplicación.  Debe utilizar el Panel de control para cambiar la configuración de impresora predeterminada del sistema completo.  
  
     `CWinApp::OnFilePrintSetup` tiene mismo una implementación simple que crea un objeto de `CPrintDialog` y que llama a la función de la implementación de **CWinApp::DoPrintDialog** .  Esto establece la configuración de impresora predeterminada de la aplicación.  
  
     La necesidad frecuente para personalizar este comando es tener en cuenta la configuración de impresora de por\- documento, que se deben almacenar con el documento cuando se guardan.  Para ello que debe agregar un controlador de mensaje\- mapa en la clase de **CDocument** que crea un objeto de `CPrintDialog` , se inicializa con los atributos adecuados de la impresora \(normalmente **hDevMode** y **hDevNames**\), llame **CPrintDialog::DoModal,** y guardar la configuración de impresora modificadas.  Para una implementación más robusta, debe considerar la implementación de **CWinApp::DoPrintDialog** para detectar errores y **CWinApp::UpdatePrinterSelection** para tratar con valores predeterminados razonables y realizar cambios sistema\- anchos de impresora.  
  
-   Impresión estándar de ID\_FILE\_PRINT del documento actual  
  
    > [!NOTE]
    >  Debe conectarse esto a `CView`\- mapa derivado del mensaje de la clase para habilitar esta funcionalidad.  
  
     Este comando imprime el documento actual, o más correctamente, inicia el proceso de impresión, que consiste en invocar el diálogo y ejecutar estándar de impresión del motor de impresión.  
  
     **CView::OnFilePrint** implementa este comando y el bucle principal de impresión.  Llama a `CView::OnPreparePrinting` virtual al marcador del usuario con el cuadro de diálogo de impresión.  Se prepara para generar elementos TITLE. para ir a la impresora, extrae para abrir el cuadro de diálogo de progreso de impresión \(**AFX\_IDD\_PRINTDLG**\), y envía el escape de `StartDoc` a la impresora.  **CView::OnFilePrint** también contiene el bucle página\- orientado principal de impresión.  Para cada página, llame a `CView::OnPrepareDC` virtual seguido un escape de `StartPage` y llamando `CView::OnPrint` virtual para esa página.  Cuando haya finalizado, se llama a `CView::OnEndPrinting` virtual, y el cuadro de diálogo de progreso de impresión se cierra.  
  
     MFC que imprime la arquitectura está diseñado para enlace de muchas maneras diferentes para imprimir y vista previa de impresión.  Encontrará normalmente las diversas funciones reemplazable de `CView` adecuadas para cualquier tarea que imprime página\- orientada.  Sólo en el caso de una aplicación que utiliza la impresora para que la página orientó la salida, si se encuentra la necesidad de reemplazar la implementación de **ID\_FILE\_PRINT** .  
  
-   Modo vista previa de impresión enter de ID\_FILE\_PRINT\_PREVIEW en el documento actual.  
  
    > [!NOTE]
    >  Debe conectarse esto a `CView`\- mapa derivado del mensaje de la clase para habilitar esta funcionalidad.  
  
     **CView::OnFilePrintPreview** inicia el modo de vista previa de impresión llamando a la función documentada **CView::DoPrintPreview**auxiliares.  **CView::DoPrintPreview** es el motor principal para el bucle de la vista previa de impresión, tal como **OnFilePrint** es el motor principal para el bucle de impresión.  
  
     La operación de la vista previa de impresión se puede personalizar de diversas maneras pasando distintos parámetros a **DoPrintPreview**.  Hace referencia a [Nota técnica 30](../mfc/tn030-customizing-printing-and-print-preview.md), que se describen algunos detalles de la vista previa de impresión y cómo personalizarlo.  
  
-   Intervalo de**ID\_FILE\_MRU\_FILE1**…**FILE16** A de los id. de comando para el archivo MRU `list`.  
  
     **CWinApp::OnUpdateRecentFileMenu** es el de la interfaz de usuario de comandos de actualización que es una de las más avanzadas utiliza el mecanismo de `ON_UPDATE_COMMAND_UI` .  En el recurso de menú, solo es necesario definir un elemento de menú único con el identificador **ID\_FILE\_MRU\_FILE1**.  Que queda el elemento de menú inicialmente deshabilitado.  
  
     Mientras la lista de archivos usados recientemente crece, varios elementos de menú se agregan a la lista.  Los valores predeterminados de la implementación de `CWinApp` estándar del límite estándar de los cuatro archivos usados recientemente.  Puede cambiar el valor predeterminado llamando a `CWinApp::LoadStdProfileSettings` con un valor mayor o menor.  La lista de archivos usados recientemente se almacena en el archivo de .INI de la aplicación.  La lista se carga en la función de `InitInstance` de la aplicación si llama a `LoadStdProfileSettings`, y guardada cuando finaliza.  El controlador de la interfaz de usuario de comandos de actualización MRU también convierte las rutas de acceso absolutas a las rutas de acceso relativas para la presentación en el menú archivo.  
  
     **CWinApp::OnOpenRecentFile** es el controlador de `ON_COMMAND` que ejecuta el comando real.  Obtiene simplemente el nombre de archivo de la lista de archivos usados recientemente y llama a `CWinApp::OpenDocumentFile`, que realiza el trabajo para abrir el archivo y actualizar la lista de archivos usados recientemente.  
  
     La personalización de este controlador de comandos no se recomienda.  
  
-   ID\_EDIT\_CLEAR borra la selección actual  
  
     Actualmente no hay implementación estándar para este comando.  Debe implementar esto para cada `CView`\- clase derivada.  
  
     `CEditView` proporciona una implementación de este comando mediante `CEdit::Clear`.  Deshabilite el comando si no hay ninguna selección actual.  
  
     Si decide implementar este comando, le recomendamos utilizamos este identificador de comando  
  
-   ID\_EDIT\_CLEAR\_ALL borra todo el documento.  
  
     Actualmente no hay implementación estándar para este comando.  Debe implementar esto para cada `CView`\- clase derivada.  
  
     Si decide implementar este comando, le recomendamos utilizamos este identificador de comando  Vea a MFC el ejemplo paso [SCRIBBLE](../top/visual-cpp-samples.md) para una aplicación de ejemplo.  
  
-   ID\_EDIT\_COPY copia la selección actual en el portapapeles.  
  
     Actualmente no hay implementación estándar para este comando.  Debe implementar esto para cada `CView`\- clase derivada.  
  
     `CEditView` proporciona una implementación de este comando, que copia el texto seleccionado en el portapapeles como CF\_TEXT mediante `CEdit::Copy`.  Deshabilite el comando si no hay ninguna selección actual.  
  
     Si decide implementar este comando, le recomendamos utilizamos este identificador de comando  
  
-   ID\_EDIT\_CUT corta la selección actual en el portapapeles.  
  
     Actualmente no hay implementación estándar para este comando.  Debe implementar esto para cada `CView`\- clase derivada.  
  
     `CEditView` proporciona una implementación de este comando, cortar el texto seleccionado en el portapapeles como CF\_TEXT mediante `CEdit::Cut`.  Deshabilite el comando si no hay ninguna selección actual.  
  
     Si decide implementar este comando, le recomendamos utilizamos este identificador de comando  
  
-   ID\_EDIT\_FIND inicia la operación de búsqueda, extrae para abrir el cuadro de diálogo no modal de búsqueda.  
  
     Actualmente no hay implementación estándar para este comando.  Debe implementar esto para cada `CView`\- clase derivada.  
  
     `CEditView` proporciona una implementación de este comando, que llama a la función **OnEditFindReplace** auxiliares de implementación para utilizar y almacenar la búsqueda anterior y reemplace las variables de implementación de los valores en privado.  La clase de `CFindReplaceDialog` se utiliza para administrar el diálogo no modal para solicitar al usuario.  
  
     Si decide implementar este comando, le recomendamos utilizamos este identificador de comando  
  
-   ID\_EDIT\_PASTE inserta el contenido del Portapapeles actuales.  
  
     Actualmente no hay implementación estándar para este comando.  Debe implementar esto para cada `CView`\- clase derivada.  
  
     `CEditView` proporciona una implementación de este comando, que copia los datos actuales del portapapeles que reemplazar texto seleccionado utilizando `CEdit::Paste`.  Deshabilite el comando si no hay **CF\_TEXT** en el portapapeles.  
  
     **COleClientDoc** simplemente proporciona un controlador de interfaz de usuario de comandos de actualización para este comando.  Si el portapapeles no contiene un elemento o un objeto de OLE integrables, se deshabilitará el comando.  Es responsable de escribir el controlador para que el comando real haga el pegado real.  Si la aplicación OLE también puede pegar otros formatos, debe proporcionar el propio controlador de interfaz de usuario de comandos de actualización en la vista o el documento \(es decir, en algún lugar antes de **COleClientDoc** en el enrutamiento del destino de comando\).  
  
     Si decide implementar este comando, le recomendamos utilizamos este identificador de comando  
  
     Para reemplazar la implementación OLE estándar, utilice `COleClientItem::CanPaste`.  
  
-   ID\_EDIT\_PASTE\_LINK inserta un vínculo del contenido del Portapapeles actuales.  
  
     Actualmente no hay implementación estándar para este comando.  Debe implementar esto para cada `CView`\- clase derivada.  
  
     `COleDocument` simplemente proporciona un controlador de interfaz de usuario de comandos de actualización para este comando.  Si el portapapeles no contiene el elemento del objeto de OLE enlazables, se deshabilitará el comando.  Es responsable de escribir el controlador para que el comando real haga el pegado real.  Si la aplicación OLE también puede pegar otros formatos, debe proporcionar el propio controlador de interfaz de usuario de comandos de actualización en la vista o el documento \(es decir, en algún lugar antes de `COleDocument` en el enrutamiento del destino de comando\).  
  
     Si decide implementar este comando, le recomendamos utilizamos este identificador de comando  
  
     Para reemplazar la implementación OLE estándar, utilice `COleClientItem::CanPasteLink`.  
  
-   ID\_EDIT\_PASTE\_SPECIAL inserta el contenido del Portapapeles actuales con opciones.  
  
     Actualmente no hay implementación estándar para este comando.  Debe implementar esto para cada `CView`\- clase derivada.  MFC no proporciona este diálogo.  
  
     Si decide implementar este comando, le recomendamos utilizamos este identificador de comando  
  
-   ID\_EDIT\_REPEAT repite la última operación.  
  
     Actualmente no hay implementación estándar para este comando.  Debe implementar esto para cada `CView`\- clase derivada.  
  
     `CEditView` proporciona una implementación de este comando de repetir la última operación de búsqueda.  Las variables privadas de implementación para la búsqueda última se utilizan.  Deshabilite el comando si una búsqueda no se probó.  
  
     Si decide implementar este comando, le recomendamos utilizamos este identificador de comando  
  
-   ID\_EDIT\_REPLACE inicia la operación de reemplazo, aporta para buscar el no modal reemplaza diálogo.  
  
     Actualmente no hay implementación estándar para este comando.  Debe implementar esto para cada `CView`\- clase derivada.  
  
     `CEditView` proporciona una implementación de este comando, que llama a la función **OnEditFindReplace** auxiliares de implementación para utilizar y almacenar la búsqueda anterior y reemplace las variables de implementación de los valores en privado.  La clase de `CFindReplaceDialog` se utiliza para administrar el diálogo no modal que solicita al usuario.  
  
     Si decide implementar este comando, le recomendamos utilizamos este identificador de comando  
  
-   ID\_EDIT\_SELECT\_ALL Selects todo el documento.  
  
     Actualmente no hay implementación estándar para este comando.  Debe implementar esto para cada `CView`\- clase derivada.  
  
     `CEditView` proporciona una implementación de este comando, que selecciona todo el texto del documento.  Deshabilite el comando si no hay texto que desea seleccionar.  
  
     Si decide implementar este comando, le recomendamos utilizamos este identificador de comando  
  
-   ID\_EDIT\_UNDO Undoes la última operación.  
  
     Actualmente no hay implementación estándar para este comando.  Debe implementar esto para cada `CView`\- clase derivada.  
  
     `CEditView` proporciona una implementación de este comando, mediante `CEdit::Undo`.  Deshabilite el comando si `CEdit::CanUndo` devuelve FALSE.  
  
     Si decide implementar este comando, le recomendamos utilizamos este identificador de comando  
  
-   ID\_EDIT\_REDO rehace la última operación.  
  
     Actualmente no hay implementación estándar para este comando.  Debe implementar esto para cada `CView`\- clase derivada.  
  
     Si decide implementar este comando, le recomendamos utilizamos este identificador de comando  
  
-   ID\_WINDOW\_NEW abre otra ventana del documento activo.  
  
     **CMDIFrameWnd::OnWindowNew** implementa esta característica eficaz mediante la plantilla de documento del documento actual para crear otro cuadro que contiene otra vista del documento actual.  
  
     Como la mayoría de los comandos del menú Ventana de \(MDI\) de interfaz de múltiples documentos, deshabilite el comando si no hay ninguna ventana secundaria de MDI activa.  
  
     La personalización de este controlador de comandos no se recomienda.  Si desea proporcionar un comando que cree vistas adicionales o las ventanas de marco, será probablemente mejor la invención poseer el comando.  Puede clonar el código de **CMDIFrameWnd::OnWindowNew** y modificarlo a las clases específicas de cuadro y ver de tener como.  
  
-   ID\_WINDOW\_ARRANGE organiza iconos en la parte inferior de una ventana MDI.  
  
     `CMDIFrameWnd` implementa este comando estándar de MDI en una función **OnMDIWindowCmd**auxiliares de implementación.  Esta aplicación auxiliar asigna id. de comando a los mensajes de MDI Windows y por lo que puede compartir mucho código.  
  
     Como la mayoría de los comandos de menú Ventana MDI, deshabilite el comando si no hay ninguna ventana secundaria de MDI activa.  
  
     La personalización de este controlador de comandos no se recomienda.  
  
-   ID\_WINDOW\_CASCADE coloca en cascada las ventanas para que se solapa.  
  
     `CMDIFrameWnd` implementa este comando estándar de MDI en una función **OnMDIWindowCmd**auxiliares de implementación.  Esta aplicación auxiliar asigna id. de comando a los mensajes de MDI Windows y por lo que puede compartir mucho código.  
  
     Como la mayoría de los comandos de menú Ventana MDI, deshabilite el comando si no hay ninguna ventana secundaria de MDI activa.  
  
     La personalización de este controlador de comandos no se recomienda.  
  
-   Ventanas de mosaicos de ID\_WINDOW\_TILE\_HORZ horizontalmente.  
  
     Implementan este comando en `CMDIFrameWnd` como **ID\_WINDOW\_CASCADE**, a menos que otro mensaje MDI Windows se utiliza para la operación.  
  
     Debe elegir la orientación predeterminada de mosaico para la aplicación.  Puede hacer esto cambiando el identificador del elemento de menú “colocar la ventana” a **ID\_WINDOW\_TILE\_HORZ** o a **ID\_WINDOW\_TILE\_VERT**.  
  
-   Ventanas de mosaicos de ID\_WINDOW\_TILE\_VERT verticalmente.  
  
     Implementan este comando en `CMDIFrameWnd` como **ID\_WINDOW\_CASCADE**, a menos que otro mensaje MDI Windows se utiliza para la operación.  
  
     Debe elegir la orientación predeterminada de mosaico para la aplicación.  Puede hacer esto cambiando el identificador del elemento de menú “colocar la ventana” a **ID\_WINDOW\_TILE\_HORZ** o a **ID\_WINDOW\_TILE\_VERT**.  
  
-   Interfaz de teclado de ID\_WINDOW\_SPLIT el divisor.  
  
     `CView` controla este comando para la implementación de `CSplitterWnd` .  Si es parte de una ventana divisora, este comando delegará a la función `CSplitterWnd::DoKeyboardSplit`de implementación.  Esto iniciará el divisor en un modo que permite a los usuarios de teclado dividan o el unsplit una ventana divisora.  
  
     Deshabilitan a este comando si la vista no está en un divisor.  
  
     La personalización de este controlador de comandos no se recomienda.  
  
-   ID\_APP\_ABOUT invoca el cuadro de diálogo Acerca de.  
  
     No hay ninguna implementación estándar para el cuadro Acerca de una aplicación.  La aplicación AppWizard\- creada predeterminada creará una clase de diálogo para la aplicación y utilizarla como el cuadro Acerca de.  AppWizard también escribirá el controlador trivial de comando que controla este comando e invoca el diálogo.  
  
     Implementará casi siempre este comando.  
  
-   Salida de ID\_APP\_EXIT la aplicación.  
  
     **CWinApp::OnAppExit** controla este comando enviando un mensaje de `WM_CLOSE` a la ventana principal de la aplicación.  El cierre estándar de la aplicación \(que solicita los archivos modificados etc.\) controla la implementación de `CFrameWnd` .  
  
     La personalización de este controlador de comandos no se recomienda.  Se recomienda reemplazar `CWinApp::SaveAllModified` o la lógica cerrada de `CFrameWnd` .  
  
     Si decide implementar este comando, le recomendamos utilizamos este identificador de comando  
  
-   ID\_HELP\_INDEX enumera temas de Ayuda del archivo de .HLP.  
  
    > [!NOTE]
    >  Debe conectarse esto a `CWinApp`\- mapa derivado del mensaje de la clase para habilitar esta funcionalidad.  
  
     `CWinApp::OnHelpIndex` controla este comando trivial llamando a `CWinApp::WinHelp`.  
  
     La personalización de este controlador de comandos no se recomienda.  
  
-   Muestra la ayuda de ID\_HELP\_USING en cómo usarla.  
  
    > [!NOTE]
    >  Debe conectarse esto a `CWinApp`\- mapa derivado del mensaje de la clase para habilitar esta funcionalidad.  
  
     `CWinApp::OnHelpUsing` controla este comando trivial llamando a `CWinApp::WinHelp`.  
  
     La personalización de este controlador de comandos no se recomienda.  
  
-   Modo de ayuda de las ENTRAR SHIFT\-F1 de ID\_CONTEXT\_HELP.  
  
    > [!NOTE]
    >  Debe conectarse esto a `CWinApp`\- mapa derivado del mensaje de la clase para habilitar esta funcionalidad.  
  
     `CWinApp::OnContextHelp` controla este comando estableciendo el modo cursor de ayuda, escribiendo un bucle modal y esperando al usuario seleccionar una ventana para obtener ayuda en.  Hace referencia a [Nota técnica 28](../mfc/tn028-context-sensitive-help-support.md) para obtener información más detallada sobre la implementación de la Ayuda de MFC.  
  
     La personalización de este controlador de comandos no se recomienda.  
  
-   ID\_HELP proporciona ayuda en el contexto actual  
  
    > [!NOTE]
    >  Debe conectarse esto a `CWinApp`\- mapa derivado del mensaje de la clase para habilitar esta funcionalidad.  
  
     `CWinApp::OnHelp` controla este comando obteniendo el contexto correcto de ayuda para el contexto de la aplicación.  Esto controla la ayuda simple de F1, ayuda sobre los cuadros de mensaje y así sucesivamente.  Hace referencia a [Nota técnica 28](../mfc/tn028-context-sensitive-help-support.md) para obtener información más detallada sobre la implementación de la ayuda de MFC.  
  
     La personalización de este controlador de comandos no se recomienda.  
  
-   Ayuda de las pantallas de ID\_DEFAULT\_HELP para el contexto  
  
    > [!NOTE]
    >  Debe conectarse esto a `CWinApp`\- mapa derivado del mensaje de la clase para habilitar esta funcionalidad.  
  
     Asignados a este comando normalmente a `CWinApp::OnHelpIndex`.  
  
     Un controlador distinto de comando puede proporcionarse si una distinción entre la Ayuda predeterminada y el índice de la Ayuda se desea.  
  
-   ID\_NEXT\_PANE Goes al siguiente panel  
  
     `CView` controla este comando para la implementación de `CSplitterWnd` .  Si es parte de una ventana divisora, este comando delegará a la función **CSplitterWnd::OnNextPaneCmd**de implementación.  Esto moverá la vista activa el panel siguiente del divisor.  
  
     Deshabilitan a este comando si la vista no está en un divisor o no hay panel siguiente a ir.  
  
     La personalización de este controlador de comandos no se recomienda.  
  
-   ID\_PREV\_PANE Goes al panel anterior  
  
     `CView` controla este comando para la implementación de `CSplitterWnd` .  Si es parte de una ventana divisora, este comando delegará a la función **CSplitterWnd::OnNextPaneCmd**de implementación.  Esto moverá la vista activa al panel anterior del divisor.  
  
     Deshabilitan a este comando si la vista no está en un divisor o no hay panel anterior a ir.  
  
     La personalización de este controlador de comandos no se recomienda.  
  
-   ID\_OLE\_INSERT\_NEW inserta un nuevo objeto OLE  
  
     Actualmente no hay implementación estándar para este comando.  Debe implementar esto para `CView`\- clase derivada para insertar un nuevo elemento\/objeto de OLE en la selección actual.  
  
     Todas las aplicaciones cliente OLE deben implementar este comando.  AppWizard, con la opción OLE, creará una implementación básica de **OnInsertObject** en la clase de vista que tendrá que completar.  
  
     Vea a MFC el ejemplo OLE de [OCLIENT](../top/visual-cpp-samples.md) de ejemplo para una implementación completa de este comando.  
  
-   ID\_OLE\_EDIT\_LINKS editar vínculos OLE  
  
     `COleDocument` controla este comando utilizando MFC\- proporcionado a la implementación de diálogo estándar de los vínculos OLE.  La implementación de este diálogo se tiene acceso a través de la clase de `COleLinksDialog` .  Si el documento actual no contiene vínculos, deshabilite el comando.  
  
     La personalización de este controlador de comandos no se recomienda.  
  
-   ID\_OLE\_VERB\_FIRST… LAST un intervalo de verbos OLE  
  
     `COleDocument` utiliza este intervalo de identificador de comando para verbos admitidos por el elemento del objeto seleccionado OLE.  Debe ser un intervalo puesto que un elemento o un tipo de objeto de OLE especificados puede admitir cero o más verbo personalizado.  En el menú de la aplicación, debe tener un elemento de menú con el identificador de **ID\_OLE\_VERB\_FIRST**.  Cuando se ejecuta el programa, el menú se actualizará con la descripción adecuada el verbo de menú \(o el menú emergente con muchos verbos\).  Administración de menú OLE controla `AfxOleSetEditMenu`, hecho en el controlador de la interfaz de usuario de comandos de actualización para este comando.  
  
     No hay controladores explícitos de comando para administrar cada uno del identificador de comando en este intervalo.  **COleDocument::OnCmdMsg** se invalida para interceptar todos los id. de comando en este intervalo, los convierte en números cero\- en función del verbo, y inicia el servidor para ese verbo \(mediante `COleClientItem::DoVerb`\).  
  
     La personalización u otro uso de este intervalo de identificadores de comando no se recomienda.  
  
-   ID\_VIEW\_TOOLBAR alterna la barra de herramientas por intervalos  
  
     `CFrameWnd` controla este comando y el controlador de interfaz de usuario de actualización\- comando de alternancia el estado de visibilidad de la barra de herramientas.  La barra de herramientas debe ser una ventana secundaria del marco con el identificador de ventana secundaria de `AFX_IDW_TOOLBAR`.  El controlador de comandos alterna realmente la visibilidad de la ventana de la barra de herramientas.  `CFrameWnd::RecalcLayout` se utiliza para actualizar la ventana de marco con la barra de herramientas en el nuevo estado.  El controlador de interfaz de usuario de actualización\- comando comprueba el elemento de menú a la barra de herramientas está visible.  
  
     La personalización de este controlador de comandos no se recomienda.  Si desea agregar barras de herramientas adicionales, deseará clonar y modificar el controlador de comandos y el controlador de la interfaz de usuario de actualización\- comando para este comando.  
  
-   ID\_VIEW\_STATUS\_BAR alterna la barra de estado por intervalos  
  
     Implementan este comando en `CFrameWnd` como **ID\_VIEW\_TOOLBAR**, a menos que se utilice un identificador diferente de la ventana secundaria \(**AFX\_IDW\_STATUS\_BAR**\).  
  
## Controladores de comandos de actualización \- solo  
 Varios id. de comando estándar se utilizan como marcadores de barras de estado.  Éstos utilizan la misma interfaz de usuario de actualización\- comando que administra el mecanismo para mostrar el estado visual actual durante el tiempo de inactividad de la aplicación.  Puesto que no pueden estar seleccionados por el usuario \(es decir, no puede insertar un panel de barra de estado\), no tiene sentido de tener un controlador de `ON_COMMAND` para estos id. del comando.  
  
-   **ID\_INDICATOR\_CAPS** : Indicador de bloqueo de LOCK.  
  
-   **ID\_INDICATOR\_NUM** : Indicador de BLOQ NUM.  
  
-   **ID\_INDICATOR\_SCRL** : Indicador de bloqueo de SCRL.  
  
-   **ID\_INDICATOR\_KANA** : Indicador de bloqueo de KANA \(aplicable sólo a los sistemas japonés\).  
  
 Los tres de ellos se implementan en **CFrameWnd::OnUpdateKeyIndicator**, aplicación auxiliar de implementación que utilice el identificador de comando para asignar a la clave adecuada de Virtual.  Una implementación común habilita o deshabilita \(para los paneles de estado deshabilitados \= ningún texto\) el objeto de `CCmdUI` dependiendo de si la clave adecuada de Virtual está bloqueada actualmente.  
  
 La personalización de este controlador de comandos no se recomienda.  
  
-   **ID\_INDICATOR\_EXT : EXT**terminó el marcador seleccione.  
  
-   La marca de strike \(**ID\_INDICATOR\_OVR : OV**e**R**.  
  
-   **ID\_INDICATOR\_REC : REC**ording el marcador.  
  
 Actualmente no hay implementación estándar para estos marcadores.  
  
 Si decide implementar estos marcadores, le recomendamos utilizamos estos id. de marcador y mantener el orden de los marcadores de la barra de estado \(es decir, en este orden: EXTENSIÓN, LOCK, NUM, SCRL, SOB, REC\).  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)