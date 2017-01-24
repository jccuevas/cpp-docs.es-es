---
title: "Configuraci&#243;n del control, Asistente para controles ActiveX MFC | Microsoft Docs"
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
  - "vc.appwiz.mfc.ctl.settings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para controles ActiveX MFC, configuración del control"
ms.assetid: 2ccaa4fc-0d52-413e-afa3-ecd474c3f6f0
caps.latest.revision: 16
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Configuraci&#243;n del control, Asistente para controles ActiveX MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utilice esta página del asistente para especificar cómo desea que se comporte el control.  Por ejemplo, puede basar el control en los tipos estándar de controles de Windows, optimizar su comportamiento y apariencia o indicar que el control puede actuar como contenedor de otros controles.  
  
 Para obtener más información sobre cómo seleccionar las opciones de esta página para maximizar la eficacia de controles, vea [Controles ActiveX MFC: Optimización](../../mfc/mfc-activex-controls-optimization.md).  
  
## Lista de UIElement  
 **Crear control basado en**  
 En esta lista, puede seleccionar el tipo de control del que debe heredar el control.  La lista es un subconjunto de las clases control disponibles para `CreateWindowEx` y los controles comunes adicionales especificados en commctrl.h.  La selección determina el estilo del control en la función de `PreCreateWindow` en el archivo de *ProjName*Ctrl.cpp.  Para obtener más información, vea [Controles ActiveX MFC: Creación de subclases de un control de Windows](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md).  
  
|Control|Descripción|  
|-------------|-----------------|  
|**BUTTON**|Un control de botón de Windows.|  
|**COMBOBOX**|Un control de cuadro combinado de Windows.|  
|**EDIT**|Un control de cuadro de edición de Windows.|  
|**LISTBOX**|Un control de cuadro de lista de Windows.|  
|**SCROLLBAR**|Un control de barra de desplazamiento de Windows.|  
|**STATIC**|Un control estático de Windows.|  
|**msctls\_hotkey32**|Un control común de tecla de acceso rápido|  
|**msctls\_progress32**|Un control común de barra de progreso|  
|**msctls\_statusbar32**|Un control común de barra de estado|  
|**msctls\_trackbar32**|Un control común de barra de seguimiento|  
|**msctls\_updown32**|Control común de botón de número \(o de flechas\)|  
|**SysAnimate32**|Un control común de animación|  
|**SysHeader32**|Un control común de encabezado|  
|**SysListView32**|Un control común de vista de lista|  
|**SysTabControl32**|Un control común de pestaña|  
|**SysTreeView32**|Un control común de vista de árbol|  
  
 **Se activa cuando está visible**  
 Especifica que se crea una ventana para el control al obtener acceso al mismo.  De forma predeterminada, la opción **Se activa cuando está visible** está seleccionada.  Si desea aplazar la activación del control hasta que la requiera el contenedor\(por ejemplo, cuando un usuario hace clic con el mouse\), borre esta opción.  Cuando esta característica se desactiva, el control no incurre en el gasto de creación de la ventana hasta que se requiere.  Para obtener más información, vea [Desactivar la opción Activar cuando esté visible](../../mfc/turning-off-the-activate-when-visible-option.md).  
  
 **No visible en tiempo de ejecución**  
 Especifica que el control no tiene interfaz de usuario en tiempo de ejecución.  Un temporizador es un tipo de control que puede que desee que sea invisible.  
  
 **Tiene un cuadro de diálogo Acerca de**  
 Especifica que el control tiene el cuadro de diálogo **Acerca de** estándar de Windows, que muestra el número de versión y la información de copyright.  
  
> [!NOTE]
>  El modo de acceso del usuario a la ayuda del control depende de cómo se haya implementado la ayuda y de si se ha integrado la ayuda del control con la ayuda del contenedor.  Para obtener más información sobre cómo integrar la ayuda, en [MSDN Library](http://go.microsoft.com/fwlink/?linkID=150542) el sitio Web, busque “agregar ayuda contextual a un control ActiveX de MFC”.  
  
 Al seleccionar esta opción, inserta el método de control de `AboutBox` en la clase de control del proyecto \(C*ProjName*Ctrl.cpp\) y agregue AboutBox a la asignación de envío del proyecto.  Esta opción se encuentra activada de forma predeterminada.  
  
 **Código de dibujo optimizado**  
 Especifica que el contenedor restaura automáticamente los objetos GDI originales una vez dibujados todos los controles contenedor, que se dibujan en el mismo contexto de dispositivo.  Para obtener más información acerca de esta característica, vea [Optimizar el dibujo de controles](../../mfc/optimizing-control-drawing.md).  
  
 **Activación sin ventana**  
 Especifica que el control no genera una ventana al activarse.  La activación sin ventana permite los controles no rectangulares o transparentes, y un control sin ventana requiere una menor sobrecarga del sistema que un control que tiene una ventana.  Un control sin ventana no permite la activación de un contexto de dispositivo no recortado o sin parpadeo.  Los contenedores creados antes de 1996 no admiten la activación sin ventana.  Para obtener más información sobre cómo utilizar esta opción, vea [Proporcionar activación sin ventana](../../mfc/providing-windowless-activation.md).  
  
 **Contexto de dispositivo no recortado**  
 Reemplaza [COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md) en el encabezado del control \(*projname*ctrl.h\) para deshabilitar la llamada a `IntersectClipRect` creados por `COleControl`.  Cuando se selecciona esta opción, proporciona una pequeña ventaja de la velocidad.  Si selecciona **Activación sin ventana**, esta característica no estará disponible.  Para obtener más información, vea [Usar un contexto de dispositivo no recortado](../../mfc/using-an-unclipped-device-context.md).  
  
 **Activación sin parpadeo**  
 Elimina las operaciones de dibujo y el parpadeo visual presente que se produce entre los estados activo e inactivo del control.  Si selecciona **Activación sin ventana**, esta característica no estará disponible.  Cuando se establece esta opción, la marca `noFlickerActivate` es una de las marcas devueltas por [COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md).  Para obtener más información, vea [Proporcionar activación sin parpadeo](../../mfc/providing-flicker-free-activation.md).  
  
 **Disponible en el cuadro de diálogo Insertar objeto**  
 Especifica que el control estará disponible en el cuadro de diálogo **Insertar objeto** para contenedores habilitados.  Cuando se selecciona esta opción, la marca `afxRegInsertable` es una de las marcas devueltas por `AfxOleRegisterControlClass`.  Con el cuadro de diálogo **Insertar objeto**, un usuario puede insertar objetos recién creados o ya existentes en un documento compuesto.  
  
 **Notificaciones con el puntero del mouse cuando está inactivo**  
 Habilita el control para procesar notificaciones con el puntero del mouse, independientemente de que el control esté activo o no.  Cuando se selecciona esta opción, la marca `pointerInactive` es una de las marcas devueltas por [COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md).  Para obtener más información sobre cómo utilizar esta opción, vea [Proporcionar interacción con el mouse mientras está inactivo](../../mfc/providing-mouse-interaction-while-inactive.md).  
  
 **Actúa como un control de marco sencillo**  
 Especifica que el control es un contenedor para otros controles estableciendo el bit `OLEMISC_SIMPLEFRAME` para el control.  Para obtener más información, en [MSDN Library](http://go.microsoft.com/fwlink/?linkID=150542) el sitio Web, busque “contención de sitio frame sencillo”.  
  
 **Cargar propiedades de forma asincrónica**  
 Habilita el restablecimiento de cualquier dato asincrónico anterior e inicia una nueva carga de la propiedad asynchronous del control.  
  
## Vea también  
 [Asistente para controles ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)   
 [Configuración de la aplicación, Asistente para controles ActiveX MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [Nombres del control, Asistente para controles ActiveX MFC](../../mfc/reference/control-names-mfc-activex-control-wizard.md)