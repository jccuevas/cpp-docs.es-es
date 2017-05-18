---
title: "Configuración del control, Asistente para controles ActiveX MFC | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.ctl.settings
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX Control Wizard, control settings
ms.assetid: 2ccaa4fc-0d52-413e-afa3-ecd474c3f6f0
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 35ec579e6f777a3dffd87adc5a86af2ea38b30f4
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="control-settings-mfc-activex-control-wizard"></a>Configuración del control, Asistente para controles ActiveX MFC
Utilice esta página del Asistente para especificar cómo desea que el control se comporte. Por ejemplo, puede basar el control en tipos de control estándar de Windows, optimizar su comportamiento y apariencia o indicar que el control puede actuar como un contenedor para otros controles.  
  
 Para obtener más información acerca de cómo seleccionar opciones en esta página para maximizar la eficacia del control, vea [controles ActiveX MFC: optimización](../../mfc/mfc-activex-controls-optimization.md).  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Crear un control basado en**  
 En esta lista, puede seleccionar el tipo de control del que debe heredar su control. La lista es un subconjunto de las clases de controles que están disponibles para `CreateWindowEx` y controles comunes adicionales que se especifican en commctrl.h. La selección determina el estilo del control en el `PreCreateWindow` funcionan en el *Nombre_proyecto*archivo Ctrl.cpp. Para obtener más información, consulte [controles ActiveX MFC: crear subclases de un Control de Windows](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md).  
  
|Control|Descripción|  
|-------------|-----------------|  
|**BOTÓN**|Un control de botón de Windows|  
|**CUADRO COMBINADO**|Un control de cuadro combinado de Windows|  
|**EDITAR**|Un control de cuadro de edición de Windows|  
|**CUADRO DE LISTA**|Un control de cuadro de lista de Windows|  
|**BARRA DE DESPLAZAMIENTO**|Un control de barra de desplazamiento de Windows|  
|**ESTÁTICO**|Un control estático de Windows|  
|**msctls_hotkey32**|Un control común de tecla activo|  
|**msctls_progress32**|Una control común de barra de progreso|  
|**msctls_statusbar32**|Un control común de la barra de estado|  
|**msctls_trackbar32**|Una pista de control común de barra|  
|**msctls_updown32**|Un botón de número (o arriba-abajo) control común|  
|**SysAnimate32**|Un control común de animación|  
|**SysHeader32**|Un control común de encabezado|  
|**SysListView32**|Un control común de vista de lista|  
|**SysTabControl32**|Un control común de ficha|  
|**SysTreeView32**|Un control común de vista de árbol|  
  
 **Se activa cuando está visible**  
 Especifica que se crea una ventana para el control cuando se tiene acceso. De forma predeterminada, el **se activa cuando está visible** está seleccionada. Si desea aplazar la activación del control hasta que el contenedor lo requiere (por ejemplo, cuando un usuario hace clic en el mouse), desactive esta opción. Cuando esta característica está desactivada, el control no incurre en el gasto de creación de ventana hasta que sea necesario. Para obtener más información, consulte [al desactivar la opción Activar cuando Visible](../../mfc/turning-off-the-activate-when-visible-option.md).  
  
 **Invisible en tiempo de ejecución**  
 Especifica que el control no tiene ninguna interfaz de usuario en tiempo de ejecución. Un temporizador es un tipo de control que desea ser invisible.  
  
 **Tiene un cuadro de diálogo acerca de**  
 Especifica que el control tiene el estándar de Windows **sobre** cuadro de diálogo que muestra el número de versión e información de copyright.  
  
> [!NOTE]
>  Cómo el usuario accede a la ayuda para el control depende de cómo haya implementado la Ayuda y si ha integrado la ayuda con la Ayuda del contenedor. Para obtener más información acerca de cómo integrar la Ayuda, en la [MSDN Library](http://go.microsoft.com/fwlink/linkid=150542) sitio Web, busque "Agregar contextual ayuda a un Control ActiveX MFC".  
  
 Cuando se selecciona esta opción, se inserta el `AboutBox` controlar el método de la clase de control del proyecto (C*Nombre_proyecto*Ctrl.cpp) y se agregará AboutBox al mapa de envíos del proyecto. Esta opción se encuentra activada de forma predeterminada.  
  
 **Código de dibujo optimizado**  
 Especifica que el contenedor restaura los objetos GDI originales automáticamente después de todos los controles contenedor, que se dibujan en el mismo contexto de dispositivo, se han trazado. Para obtener más información sobre esta característica, consulte [optimizar el dibujo de controles](../../mfc/optimizing-control-drawing.md).  
  
 **Activación sin ventana**  
 Especifica que el control no genera una ventana cuando se activa. Activación sin ventana permite controles no rectangulares o transparentes y requiere de un control sin ventana requiere menos sobrecarga del sistema que un control que tenga una ventana. No se permite un control sin ventana para un contexto de dispositivo no recortado o activación sin parpadeo. Los contenedores creados antes de 1996 no admiten la activación sin ventana. Para obtener más información acerca de cómo usar esta opción, consulte [proporcionar activación sin ventana](../../mfc/providing-windowless-activation.md).  
  
 **Contexto de dispositivo no recortado**  
 Reemplaza [COleControl:: GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags) en el encabezado de control (*Nombre_proyecto*ctrl.h) para deshabilitar la llamada a `IntersectClipRect` realizados por `COleControl`. Cuando se selecciona esta opción, proporciona una ventaja de velocidad. Si selecciona **activación sin ventana**, esta característica no está disponible. Para obtener más información, consulte [mediante un contexto de dispositivo no recortado](../../mfc/using-an-unclipped-device-context.md).  
  
 **Activación sin parpadeo**  
 Elimina las operaciones de dibujo y el parpadeo visual que se producen entre los estados activos e inactivos del control. Si selecciona **activación sin ventana**, esta característica no está disponible. Cuando se establece esta opción, el `noFlickerActivate` marca es uno de los indicadores devueltos por [COleControl:: GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags). Para obtener más información, consulte [proporcionar activación sin parpadeo](../../mfc/providing-flicker-free-activation.md).  
  
 **Disponible en el cuadro de diálogo Insertar objeto**  
 Especifica que el control estará disponible en la **Insertar objeto** cuadro de diálogo para contenedores habilitados. Cuando se selecciona esta opción, el `afxRegInsertable` marca es uno de los indicadores devueltos por `AfxOleRegisterControlClass`. Mediante el uso de la **Insertar objeto** cuadro de diálogo, un usuario puede insertar recién creado u objetos existentes en un documento compuesto.  
  
 **Notificaciones con el puntero del mouse cuando está inactivo**  
 Habilita el control para procesamiento de notificaciones del puntero del mouse, si el control está activo o no. Cuando se selecciona esta opción, el `pointerInactive` marca es uno de los indicadores devueltos por [COleControl:: GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags). Para obtener más información acerca de cómo usar esta opción, consulte [proporcionar Mouse Interaction While Inactive](../../mfc/providing-mouse-interaction-while-inactive.md).  
  
 **Actúa como un control de marco sencillo**  
 Especifica que el control es un contenedor para otros controles estableciendo la `OLEMISC_SIMPLEFRAME` de bits para el control. Para obtener más información, en la [MSDN Library](http://go.microsoft.com/fwlink/linkid=150542) sitio Web, busque "Contención de sitio de marco Simple".  
  
 **Carga de propiedades de forma asincrónica**  
 Permite restablecer datos asincrónicos anteriores e inicia una nueva carga de la propiedad asincrónica del control.  
  
## <a name="see-also"></a>Vea también  
 [Asistente para controles ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)   
 [Configuración de la aplicación, Asistente para controles ActiveX MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [Nombres del control, Asistente para controles ActiveX MFC](../../mfc/reference/control-names-mfc-activex-control-wizard.md)


