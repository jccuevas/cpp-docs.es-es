---
title: Configuración del control, Asistente para controles ActiveX MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.settings
helpviewer_keywords:
- MFC ActiveX Control Wizard, control settings
ms.assetid: 2ccaa4fc-0d52-413e-afa3-ecd474c3f6f0
ms.openlocfilehash: 3eedf24fa4b0bb527b374dbc9f538408f20de953
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548244"
---
# <a name="control-settings-mfc-activex-control-wizard"></a>Configuración del control, Asistente para controles ActiveX MFC

Utilice esta página del Asistente para especificar cómo desea que el control se comporte. Por ejemplo, puede basar el control en los tipos de control de Windows estándar, optimizar su comportamiento y apariencia o indicar que el control puede actuar como un contenedor para otros controles.

Para obtener más información sobre cómo seleccionar las opciones de esta página para maximizar la eficacia del control, vea [controles ActiveX MFC: optimización](../../mfc/mfc-activex-controls-optimization.md).

## <a name="uielement-list"></a>Lista de UIElement

- **Crear un control basado en**

   En esta lista, puede seleccionar el tipo de control del que debe heredar su control. La lista es un subconjunto de las clases de controles que están disponibles para `CreateWindowEx` y controles comunes adicionales que se especifican en commctrl.h. La selección determina el estilo del control en el `PreCreateWindow` funcionando en el *Nombre_proyecto*archivo Ctrl.cpp. Para obtener más información, consulte [controles ActiveX MFC: creación de subclases de un Control de Windows](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md).

   |Control|Descripción|
   |-------------|-----------------|
   |**BOTÓN**|Un control de botón de Windows|
   |**CUADRO COMBINADO**|Un control de cuadro combinado de Windows|
   |**EDITAR**|Un control de cuadro de edición de Windows|
   |**CUADRO DE LISTA**|Un control de cuadro de lista de Windows|
   |**BARRA DE DESPLAZAMIENTO**|Un control de barra de desplazamiento de Windows|
   |**ESTÁTICO**|Un control estático de Windows|
   |**msctls_hotkey32**|Un control común hot key|
   |**msctls_progress32**|Una barra de control común de progreso|
   |**msctls_statusbar32**|Un control común de la barra de estado|
   |**msctls_trackbar32**|Una pista de barra de control comunes|
   |**msctls_updown32**|Un botón de número (o arriba-abajo) control común|
   |**SysAnimate32**|Un control común de animación|
   |**SysHeader32**|Un control común de encabezado|
   |**SysListView32**|Un control común de vista de lista|
   |**SysTabControl32**|Un control común de pestaña|
   |**SysTreeView32**|Un control común de vista de árbol|

- **Se activa cuando está visible**

   Especifica que se crea una ventana para el control cuando se tiene acceso a. De forma predeterminada, el **activa cuando está visible** está seleccionada. Si desea aplazar la activación del control hasta que lo requiera el contenedor (por ejemplo, cuando un usuario hace clic con el mouse), desactive esta opción. Cuando esta característica está desactivada, el control no incurre en el gasto que supone la creación de ventana hasta que sea necesario. Para obtener más información, consulte [al desactivar la opción Activar cuando Visible](../../mfc/turning-off-the-activate-when-visible-option.md).

- **Invisible en tiempo de ejecución**

   Especifica que el control no tiene ninguna interfaz de usuario en tiempo de ejecución. Un temporizador es un tipo de control que desea ser invisible.

- **Tiene un cuadro de diálogo About**

   Especifica que el control tiene el estándar Windows **sobre** cuadro de diálogo que muestra el número de versión e información de copyright.

   > [!NOTE]
   > Cómo el usuario accede a la Ayuda del control depende de cómo haya implementado la Ayuda y si ha integrado la Ayuda del control con la Ayuda del contenedor. Para obtener más información sobre cómo integrar la Ayuda, en la [MSDN Library](http://go.microsoft.com/fwlink/p/?linkid=150542) sitio Web, busque "Agregar contextuales ayuda a un Control ActiveX MFC".

   Cuando se selecciona esta opción, se inserta el `AboutBox` controlar el método de la clase de control del proyecto (C*Nombre_proyecto*Ctrl.cpp) y se agregará AboutBox al mapa de envíos del proyecto. Esta opción se encuentra activada de forma predeterminada.

- **Código de dibujo optimizado**

   Especifica que el contenedor restaura los objetos GDI originales automáticamente después de todo los controles de contenedor, que se dibujan en el mismo contexto de dispositivo, se hayan dibujado. Para obtener más información sobre esta característica, consulte [optimizar el dibujo de controles](../../mfc/optimizing-control-drawing.md).

- **Activación sin ventana**

   Especifica que el control no genera una ventana cuando se activa. Activación sin ventana permite controles no rectangulares o transparentes, y requiere de un control sin ventanas requiere menos sobrecarga del sistema que un control que tenga una ventana. No se permite un control sin ventanas para un contexto de dispositivo no recortado o activación sin parpadeo. Los contenedores que se crearon antes de 1996 no admiten la activación sin ventana. Para obtener más información sobre cómo usar esta opción, consulte [proporcionar activación sin ventana](../../mfc/providing-windowless-activation.md).

- **Contexto de dispositivo no recortado**

   Invalida [COleControl:: GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags) en el encabezado de control (*Nombre_proyecto*ctrl.h) para deshabilitar la llamada a `IntersectClipRect` realizadas por `COleControl`. Cuando se selecciona esta opción, proporciona una ventaja de velocidad. Si selecciona **activación sin ventana**, esta característica no está disponible. Para obtener más información, consulte [utilizando un contexto de dispositivo no recortado](../../mfc/using-an-unclipped-device-context.md).

- **Activación sin parpadeo**

   Elimina las operaciones de dibujo y el parpadeo visual que se producen entre los estados activos e inactivos del control. Si selecciona **activación sin ventana**, esta característica no está disponible. Al establecer esta opción, el `noFlickerActivate` indicador es una de las marcas que se devuelven por [COleControl:: GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags). Para obtener más información, consulte [proporcionar activación sin parpadeo](../../mfc/providing-flicker-free-activation.md).

- **Disponible en el cuadro de diálogo Insertar objeto**

   Especifica que el control estará disponible en el **Insertar objeto** cuadro de diálogo para contenedores habilitados. Cuando se selecciona esta opción, el `afxRegInsertable` indicador es una de las marcas que se devuelven por `AfxOleRegisterControlClass`. Mediante el uso de la **Insertar objeto** cuadro de diálogo, un usuario puede insertar recién creado u objetos existentes en un documento compuesto.

- **Notificaciones con el puntero del mouse cuando está inactivo**

   Habilita el control al proceso de notificaciones del puntero del mouse, si el control está activo o no. Cuando se selecciona esta opción, el `pointerInactive` indicador es una de las marcas que se devuelven por [COleControl:: GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags). Para obtener más información sobre cómo usar esta opción, consulte [proporcionar Mouse interacción inactivo](../../mfc/providing-mouse-interaction-while-inactive.md).

- **Actúa como un control de marco sencillo**

   Especifica que el control es un contenedor para otros controles estableciendo el bit OLEMISC_SIMPLEFRAME para el control. Para obtener más información sobre la [MSDN Library](http://go.microsoft.com/fwlink/p/?linkid=150542) sitio Web, busque "Contención de sitio de marco Simple".

- **Carga las propiedades de forma asincrónica**

   Permite restablecer datos asincrónicos anteriores e inicia una nueva carga de la propiedad asincrónica del control.

## <a name="see-also"></a>Vea también

[Asistente para controles ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[Configuración de la aplicación, Asistente para controles ActiveX MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)<br/>
[Nombres del control, Asistente para controles ActiveX MFC](../../mfc/reference/control-names-mfc-activex-control-wizard.md)

