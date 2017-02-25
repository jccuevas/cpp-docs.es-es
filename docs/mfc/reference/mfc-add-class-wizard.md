---
title: "Asistente para agregar clases MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.class.mfc.simple.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para agregar clases MFC"
  - "asistentes [MFC]"
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# Asistente para agregar clases MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utilice este asistente de código para agregar una clase a un proyecto MFC existente, o para agregar una clase a un proyecto ATL compatible con MFC.  También se pueden agregar clases MFC a proyectos Win32 que sean compatibles con MFC.  Las características que especificara al crear el proyecto determinarán las opciones disponibles en este cuadro de diálogo.  
  
## Nombres  
 En esta página, especifique el nombre de clase, la clase base y los nombres de archivo para la nueva clase.  
  
 **Nombre de clase**  
 Especifica el nombre de la nueva clase y facilita la base predeterminada para los nombres de ids. y los archivos en esta página.  Las clases de C\+\+ suelen comenzar con "C", así que, por ejemplo, "CMiClase" se convierte en "MiClase.h", etc.  
  
 **Clase base**  
 Especifica el nombre de la clase base para la nueva clase.  De manera predeterminada, la clase base es [CWnd](../../mfc/reference/cwnd-class.md).  La clase base que seleccione determina si otros cuadros de esta página están activos.  
  
 El tipo de clase que establece cuando la clase base determina si la clase tiene un id. de cuadro de diálogo o un id. de recurso.  Los tipos generales de clases son los siguientes:  
  
-   Clases como [CButton](../../mfc/reference/cbutton-class.md), [CWnd](../../mfc/reference/cwnd-class.md) o [CDocument](../../mfc/reference/cdocument-class.md), que no requieren ningún id. de cuadro de diálogo ni id. de recurso.  Estas clases no utilizan ningún id. de cuadro de diálogo ni id. de recurso.  Si selecciona una de estas clases para su clase base, se atenúan el cuadro **Id. del cuadro de diálogo** y el cuadro **Id. del recurso DHTML**.  
  
-   Las clases como [CDialog](../../mfc/reference/cdialog-class.md), [CFormView](../../mfc/reference/cformview-class.md) o [CPropertyPage](../../mfc/reference/cpropertypage-class.md), que requieren un id. de cuadro de diálogo.  
  
-   La clase [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md), que requiere un id. de cuadro de diálogo, un id. de recurso DHTML y un nombre de archivo HTML.  
  
 Para las clases que requieren un id. de cuadro de diálogo, podría resultar más eficaz utilizar el [editor de recursos](../../mfc/resource-editors.md) para crear el recurso de cuadro de diálogo, asignar su identificador en la [ventana Propiedades](../Topic/Properties%20Window.md) y, a continuación, crear una clase asociada a ese id. de recurso.  Vea [Crear un nuevo cuadro de diálogo](../../mfc/creating-a-new-dialog-box.md) para obtener más información sobre cómo crear un cuadro de diálogo de Windows estándar.  
  
> [!NOTE]
>  Si crea en primer lugar un recurso de cuadro de diálogo y deriva su nueva clase de `CDHtmlDialog`, elimine los botones **Aceptar** y **Cancelar** estándar de Windows que aparecen en el cuadro de diálogo predeterminado.  El cuadro de diálogo estándar de Windows hospeda el formulario DHTML, que agrega sus propios botones **Aceptar** y **Cancelar**.  
  
 Si bien un cuadro de diálogo puede contener tanto controles Windows como controles DHTML, no se recomienda.  
  
 **Id. del cuadro de diálogo**  
 Especifica el identificador del cuadro de diálogo, si se seleccionó `CDialog`, `CFormView`, `CPropertyPage` o `CDHtmlDialog` como **Clase base**.  
  
 **Archivo .h**  
 Establece el nombre del archivo de encabezado para la clase del nuevo objeto.  De forma predeterminada, este nombre está basado en el nombre proporcionado en **Nombre de clase**.  Haga clic en el botón de los puntos suspensivos para guardar el nombre de archivo en la ubicación que desee o para anexar la declaración de la clase a un archivo existente.  Si elige un archivo ya existente, el asistente no lo guardará en la ubicación seleccionada hasta que seleccione **Finalizar** en el asistente.  
  
 El asistente no sobrescribe ningún archivo.  Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar** el asistente le preguntará si desea anexar la declaración de la clase al contenido del archivo.  Haga clic en **Sí** para anexar el archivo; haga clic en **No** para regresar al asistente y especificar otro nombre de archivo.  
  
 **Archivo .cpp**  
 Establece el nombre del archivo de implementación para la clase del nuevo objeto.  De forma predeterminada, este nombre está basado en el nombre proporcionado en **Nombre de clase**.  Haga clic en el botón de los puntos suspensivos para guardar el nombre de archivo en la ubicación que desee.  El archivo no quedará guardado en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.  
  
 El asistente no sobrescribe ningún archivo.  Si selecciona el nombre de un archivo que ya existe, al hacer clic en **Finalizar**, el asistente solicitará que especifique si la implementación de la clase debe anexarse al contenido del archivo.  Haga clic en **Sí** para anexar el archivo; haga clic en **No** para regresar al asistente y especificar otro nombre de archivo.  
  
 **Active accessibility**  
 Habilita la compatibilidad de MFC con Active Accessibility llamando a [EnableActiveAccessibility](../Topic/CWnd::EnableActiveAccessibility.md) en el constructor.  Esta opción está disponible para las clases derivadas de [CWnd](../../mfc/reference/cwnd-class.md).  
  
 **Id. del recurso DHTML**  
 Se aplica únicamente a las clases derivadas de `CDHtmlDialog`.  Especifica el id. de recurso del cuadro de diálogo DHTML.  El identificador de recurso aparece en la sección HTML del archivo .rc del proyecto, junto con el nombre de archivo del cuadro de diálogo DHTML.  El recurso DHTML, identificado por este Id., está hospedado en el cuadro de diálogo, identificado mediante el **Id. del cuadro de diálogo**.  
  
 **Archivo .HTM**  
 Se aplica únicamente a las clases derivadas de `CDHtmlDialog`.  Establece el nombre del archivo HTML para el cuadro de diálogo DHTML.  De forma predeterminada, el nombre de archivo se basa en el nombre de clase.  El nombre de archivo aparece en la sección HTML del archivo .rc del proyecto, junto con el id. de recurso del cuadro de diálogo DHTML.  
  
 **Automatización**  
 Establece el nivel de clases de soporte con la [automatización](../../mfc/automation.md).  La automatización en el nivel de clase está disponible para todas las clases que admiten la automatización.  También está disponible para los proyectos creados con compatibilidad de automatización.  Es decir, un proyecto MFC que es [compatible con ATL](../../atl/reference/mfc-support-in-atl-projects.md) o un proyecto MFC para el que activó la casilla **Automatización** en la página [Características avanzadas](../../mfc/reference/advanced-features-mfc-application-wizard.md) del Asistente para aplicaciones MFC.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**None**|Indica que la clase no es compatible con automatización.|  
|**Automatización**|Indica que la clase admite automatización.  Si selecciona esta opción, la clase recién creada está disponible como objeto programable por las aplicaciones de cliente de automatización, como Microsoft Visual Basic y Microsoft Excel.  Esta opción no está disponible para las clases base enumeradas a continuación de esta tabla.|  
|**Se puede crear por el id. del tipo**|Indica que tanto la clase como el proyecto admiten otras aplicaciones que crean objetos de esta clase mediante automatización.  Con esta opción, los clientes de automatización pueden crear directamente un objeto Automation.  El id. de tipo del cuadro de texto es utilizado por la aplicación de cliente para especificar el objeto que se va a crear; afecta a todo el sistema y debe ser único.  Esta opción no está disponible para las clases base enumeradas a continuación de esta tabla.|  
  
 La compatibilidad con automatización no está disponible para las siguientes clases base:  
  
-   `CAsyncMonitorFile`  
  
-   `CAsyncSocket`  
  
-   `CCachedDataPathProperty`  
  
-   `CConnectionPoint`  
  
-   `CDatabase`  
  
-   `CDataPathProperty`  
  
-   `CHttpFilter`  
  
-   `CHttpServer`  
  
-   `CInternetSession`  
  
-   `CObject`  
  
-   `CSocket`  
  
 **Id. del tipo**  
 Establece el id. de tipo de la clase.  El cuadro de **Id. de tipo** concatena el nombre del proyecto y el nuevo nombre de clase como sigue: *MFCProj.MFCClass*.  Este identificador es modificable sólo si se seleccionó la opción **Se puede crear por Id. de tipo** en **Automatización**.  
  
 **Generar recursos DocTemplate**  
 Indica que los documentos creados por la aplicación contienen recursos de plantilla de documento.  Para activar esta casilla, el proyecto debe admitir la arquitectura documento\/vista de MFC, y la clase base de esta clase debe ser [CFormView](../../mfc/reference/cformview-class.md).  
  
 Vea [Plantillas de documento y el proceso de creación de documentos y vistas](../../mfc/document-templates-and-the-document-view-creation-process.md) para obtener más información.  
  
## Vea también  
 [MFC \(clase\)](../../mfc/reference/adding-an-mfc-class.md)   
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)