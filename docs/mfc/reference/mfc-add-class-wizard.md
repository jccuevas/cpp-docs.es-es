---
title: Asistente para agregar clases MFC
ms.date: 09/06/2019
f1_keywords:
- vc.codewiz.class.mfc.simple.overview
helpviewer_keywords:
- MFC Add Class Wizard
- wizards [MFC]
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
ms.openlocfilehash: 2c82e084de2123c579299ca6490bdfcfdac5d255
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908030"
---
# <a name="mfc-add-class-wizard"></a>Asistente para agregar clases MFC

Utilice este asistente para código para agregar una clase a un proyecto de MFC existente o para agregar una clase a un proyecto ATL que admita MFC. También puede Agregar clases MFC a proyectos Win32 que tengan compatibilidad con MFC. Las características que especificó al crear el proyecto determinan las opciones disponibles en este cuadro de diálogo. Para obtener acceso al asistente, haga clic en **Agregar clase** en el [Asistente para clases](mfc-class-wizard.md).

![Asistente para agregar clases MFC](media/add-mfc-class-wizard.png "Asistente para agregar clases MFC")

## <a name="names"></a>Nombres

En esta página, especifique el nombre de clase, la clase base y los nombres de archivo de la nueva clase.

- **Nombre de la clase**

  Especifica el nombre de la nueva clase y proporciona la base predeterminada de los nombres de los identificadores y archivos de esta página. C++las clases normalmente comienzan con "C", por lo que, por ejemplo, "CMyClass" se convierte en "MyClass. h", etc.

- **Clase base**

  Especifica el nombre de la clase base para la nueva clase. De forma predeterminada, la clase base es [CWnd](../../mfc/reference/cwnd-class.md). La clase base que seleccione determina si otros cuadros de esta página están activos.

  El tipo de clase que se establece como clase base determina si la clase tiene un identificador de cuadro de diálogo o un identificador de recurso. Los tipos generales de clases son los siguientes:

  - Clases como [CButton](../../mfc/reference/cbutton-class.md), [CWnd](../../mfc/reference/cwnd-class.md)o [CDocument](../../mfc/reference/cdocument-class.md), que no requieren un identificador de cuadro de diálogo o un identificador de recurso. Estas clases no usan un cuadro de diálogo o un identificador de recurso. Si selecciona una de estas clases para la clase base, el cuadro **ID** . de diálogo y el cuadro ID. de **recurso DHTML** aparecen atenuados.

  - Clases como [CDialog](../../mfc/reference/cdialog-class.md), [CFormView](../../mfc/reference/cformview-class.md)o [CPROPERTYPAGE](../../mfc/reference/cpropertypage-class.md), que requieren un identificador de cuadro de diálogo.

  - La clase [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md), que requiere un identificador de cuadro de diálogo, un identificador de recurso DHTML y un nombre de archivo HTML.

  En el caso de las clases que requieren un identificador de cuadro de diálogo, puede que le resulte más eficaz usar el [Editor de recursos](../../windows/resource-editors.md) para crear el recurso de cuadro de diálogo, asignar su identificador en el [Asistente para clases](mfc-class-wizard.md)y, a continuación, crear una clase asociada a ese identificador de recurso. Consulte [crear un nuevo cuadro de diálogo](../../windows/creating-a-new-dialog-box.md) para obtener más información sobre cómo crear un cuadro de diálogo estándar de Windows.

  > [!NOTE]
  > Si crea primero un recurso de diálogo y deriva su nueva clase de `CDHtmlDialog`, elimine los botones estándar **Aceptar** y **Cancelar** de Windows que aparecen en el cuadro de diálogo predeterminado. El cuadro de diálogo estándar de Windows hospeda el formulario DHTML, que contiene sus propios botones **Aceptar** y **Cancelar** .

  Aunque el cuadro de diálogo puede contener controles de Windows y controles DHTML, no se recomienda.

- **ID. de cuadro de diálogo**

  Especifica el identificador del cuadro de diálogo, `CDialog`si seleccionó `CFormView` `CPropertyPage`,, o `CDHtmlDialog` como la **clase base**.

- **Archivo .h**

  Establece el nombre del archivo de encabezado para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el que se proporcione en **Nombre de la clase**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija, o bien para anexar la declaración de clase a un archivo existente. Si elige un archivo existente, el asistente no lo guardará en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.

  El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la declaración de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.

- **Archivo .cpp**

  Establece el nombre del archivo de implementación para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el que se proporcione en **Nombre de la clase**. Haga clic en el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que elija. El archivo no se guarda en la ubicación seleccionada hasta que haga clic en **Finalizar** en el asistente.

  El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente, al hacer clic en **Finalizar**, el asistente le pedirá que indique si se debe anexar la implementación de clase al contenido del archivo. Haga clic en **Sí** para anexar el archivo; haga clic en **No** para volver al asistente y especificar otro nombre de archivo.

- **Accesibilidad activa**

  Habilita la compatibilidad de MFC con Active Accessibility llamando a [EnableActiveAccessibility](../../mfc/reference/cwnd-class.md#enableactiveaccessibility) en el constructor. Esta opción está disponible para las clases derivadas de [CWnd](../../mfc/reference/cwnd-class.md).

- **Automatización**

  Establece el nivel de clase de compatibilidad para la [automatización](../../mfc/automation.md). La automatización en el nivel de clase está disponible para todas las clases que admiten la automatización. También está disponible para los proyectos creados con compatibilidad con Automation. Es decir, un proyecto MFC que [admita ATL](../../atl/reference/mfc-support-in-atl-projects.md)o un proyecto MFC para el que se haya activado la casilla **automatización** en la página [características avanzadas](../../mfc/reference/advanced-features-mfc-application-wizard.md) del Asistente para aplicaciones MFC.

   La compatibilidad con automatización no está disponible para las clases base siguientes:

  - `CAsyncMonitorFile`

  - `CAsyncSocket`

  - `CCachedDataPathProperty`

  - `CConnectionPoint`

  - `CDatabase`

  - `CDataPathProperty`

  - `CHttpFilter`

  - `CHttpServer`

  - `CInternetSession`

  - `CObject`

  - `CSocket`

## <a name="see-also"></a>Vea también

[Clase MFC](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Agregar una clase](../../ide/adding-a-class-visual-cpp.md)
