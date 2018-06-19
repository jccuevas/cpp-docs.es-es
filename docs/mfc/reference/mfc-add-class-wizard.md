---
title: Agregar Asistente para clases MFC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.class.mfc.simple.overview
dev_langs:
- C++
helpviewer_keywords:
- MFC Add Class Wizard
- wizards [MFC]
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9560dec12a7710076f752d5329269c844f0d3a8b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373416"
---
# <a name="mfc-add-class-wizard"></a>Asistente para agregar clases MFC
Use este asistente de código para agregar una clase a un proyecto MFC existente, o para agregar una clase a un proyecto ATL compatible con MFC. También puede agregar clases MFC a proyectos de Win32 que tengan compatibilidad con MFC. Las características que se especificó cuando creó el proyecto determinan las opciones disponibles en este cuadro de diálogo.  
  
## <a name="names"></a>Nombres  
 En esta página, especifique el nombre de clase, la clase base y los nombres de archivo para la nueva clase.  
  
 **Nombre de clase**  
 Especifica el nombre de la nueva clase y proporciona la base predeterminada para los nombres de identificadores y archivos en esta página. Las clases de C++ suelen comenzar con "C", por ejemplo, "CMiClase" se convierte en "MiClase.h", y así sucesivamente.  
  
 **Clase base**  
 Especifica el nombre de la clase base para la nueva clase. De forma predeterminada, es la clase base [CWnd](../../mfc/reference/cwnd-class.md). La clase base que seleccione determina si otros cuadros de esta página están activos.  
  
 El tipo de clase que se establece como la clase base determina si la clase tiene un identificador de diálogo o un identificador de recurso. Los tipos generales de clases son los siguientes:  
  
-   Las clases como [CButton](../../mfc/reference/cbutton-class.md), [CWnd](../../mfc/reference/cwnd-class.md), o [CDocument](../../mfc/reference/cdocument-class.md), que no requieren un cuadro de diálogo identificador o identificador de recurso. Estas clases no usan un identificador de recurso o el cuadro de diálogo. Si selecciona una de estas clases para la clase base, el **Id. del cuadro de diálogo** cuadro y **Id. de recurso DHTML** cuadro aparecen atenuados.  
  
-   Las clases como [CDialog](../../mfc/reference/cdialog-class.md), [CFormView](../../mfc/reference/cformview-class.md), o [CPropertyPage](../../mfc/reference/cpropertypage-class.md), que requieren un Id.  
  
-   La clase [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md), lo que requiere un Id. de cuadro de diálogo, un identificador de recurso DHTML y el nombre del archivo HTML.  
  
 Para las clases que requieren un Id. de cuadro de diálogo, le resultará más eficaz utilizar la [editor de recursos](../../windows/resource-editors.md) para crear el recurso de cuadro de diálogo, asignar su identificador en el [ventana propiedades](/visualstudio/ide/reference/properties-window)y, a continuación, cree una clase asociada con ese identificador de recurso. Vea [crear un nuevo cuadro de diálogo](../../windows/creating-a-new-dialog-box.md) para obtener más información acerca de cómo crear un cuadro de diálogo estándar de Windows.  
  
> [!NOTE]
>  Si primero crea un recurso de cuadro de diálogo y deriva su nueva clase de `CDHtmlDialog`, eliminar el estándar de Windows **Aceptar** y **cancelar** botones que aparecen en el cuadro de diálogo de forma predeterminada. El cuadro de diálogo estándar de Windows hospeda el formulario DHTML, que contiene sus propias **Aceptar** y **cancelar** botones.  
  
 Mientras que el cuadro de diálogo puede contener controles de Windows y controles DHTML, no se recomienda.  
  
 **Id. del cuadro de diálogo**  
 Especifica el identificador del cuadro de diálogo, si seleccionó `CDialog`, `CFormView`, `CPropertyPage`, o `CDHtmlDialog` como el **clase Base**.  
  
 **archivo .h**  
 Establece el nombre del archivo de encabezado para la nueva clase del objeto. De forma predeterminada, este nombre se basa en el nombre que proporcione en **nombre de la clase**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación de su elección, o para anexar la declaración de clase a un archivo existente. Si elige un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **finalizar** en el asistente.  
  
 El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **finalizar**, el asistente le preguntará si para indicar si se debe anexar la declaración de clase para el contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **n** para volver al asistente y especificar otro nombre de archivo.  
  
 **archivo .cpp**  
 Establece el nombre del archivo de implementación para la nueva clase del objeto. De forma predeterminada, este nombre se basa en el nombre que proporcione en **nombre de la clase**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación de su elección. El archivo no se guarda en la ubicación seleccionada hasta que haga clic **finalizar** en el asistente.  
  
 El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **finalizar**, el asistente le preguntará si para indicar si se debe anexar a la implementación de la clase para el contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **n** para volver al asistente y especificar otro nombre de archivo.  
  
 **Active accessibility**  
 Habilita la compatibilidad con de MFC Active Accessibility llamando [EnableActiveAccessibility](../../mfc/reference/cwnd-class.md#enableactiveaccessibility) en el constructor. Esta opción está disponible para las clases derivadas de [CWnd](../../mfc/reference/cwnd-class.md).  
  
 **Id. de recurso DHTML**  
 Se aplica a las clases derivadas de `CDHtmlDialog` solo. Especifica el identificador de recurso del cuadro de diálogo DHTML. El identificador de recurso aparece en la sección HTML del archivo de .rc del proyecto, junto con el nombre de archivo del cuadro de diálogo HTML. El recurso DHTML, identificado por este Id., se hospeda en el cuadro de diálogo, identificado por **Id. del cuadro de diálogo**.  
  
 **. Archivo en formato HTM**  
 Se aplica a las clases derivadas de `CDHtmlDialog` solo. Establece el nombre del archivo HTML para el cuadro de diálogo DHTML. De forma predeterminada, este nombre de archivo se basa en el nombre de clase. El nombre de archivo aparece en la sección HTML del archivo de .rc del proyecto, junto con el identificador de recurso de cuadro de diálogo DHTML.  
  
 **Automatización**  
 Establece el nivel de clase de compatibilidad para [automatización](../../mfc/automation.md). Automatización en el nivel de clase está disponible para todas las clases que admiten la automatización. También está disponible para los proyectos creados con compatibilidad para la automatización. Es decir, un proyecto MFC que [es compatible con ATL](../../atl/reference/mfc-support-in-atl-projects.md), o un proyecto MFC para el que ha seleccionado la **automatización** casilla de verificación en la [características avanzadas](../../mfc/reference/advanced-features-mfc-application-wizard.md) página de MFC Asistente para aplicaciones.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Ninguno**|Indica que la clase no tiene se admite la automatización.|  
|**Automatización**|Indica que la clase admite la automatización. Si selecciona esta opción, la clase recién creada está disponible como un objeto programable por las aplicaciones de cliente de automatización, como Microsoft Visual Basic y Microsoft Excel. Esta opción no está disponible para las clases base enumeradas después de esta tabla.|  
|**Puede crear con el identificador de tipo**|Indica que la clase y el proyecto compatible con otras aplicaciones que crean objetos de esta clase mediante la automatización. Con esta opción, los clientes de automatización pueden crear directamente un objeto de automatización. El identificador de tipo en el cuadro de texto se utiliza la aplicación cliente para especificar el objeto que se va a crear; es todo el sistema y debe ser único. Esta opción no está disponible para las clases base enumeradas después de esta tabla.|  
  
 Compatibilidad de automatización no está disponible para las clases base siguientes:  
  
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
  
 **Id. de tipo**  
 Establece el identificador de tipo de la clase. El **Type_id** cuadro concatena el nombre del proyecto y el nuevo nombre de clase como sigue: *ProyectoMFC.ClaseMFC*. Este identificador es modificable sólo si seleccionó la **automatización** opción **se puede crear por Id. de tipo**.  
  
 **Generar recursos DocTemplate**  
 Indica que los documentos creados por la aplicación tienen recursos de plantilla de documento. Para activar esta casilla de verificación, el proyecto debe admitir la arquitectura documento/vista MFC, y la clase base de esta clase debe ser [CFormView](../../mfc/reference/cformview-class.md).  
  
 Vea [plantillas de documento y el proceso de creación de documento/vista](../../mfc/document-templates-and-the-document-view-creation-process.md) para obtener más información.  
  
## <a name="see-also"></a>Vea también  
 [MFC (clase)](../../mfc/reference/adding-an-mfc-class.md)   
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)
