---
title: Apariencia, Asistente para controles ATL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.control.misc
dev_langs:
- C++
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8869df577dfbc541b989beb4b4f3117d7d12feea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="appearance-atl-control-wizard"></a>Apariencia, Asistente para controles ATL
Inserte aquí "Búsqueda de resumen de los resultados".  
  
 Utilice esta página del Asistente para identificar las opciones de elemento de usuario adicionales para el control. Esta página está disponible para los controles identificados como **controles estándar** en **tipo de Control** en el [opciones, Asistente para controles ATL](../../atl/reference/options-atl-control-wizard.md) página.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Estado de vista**  
 Establece la apariencia del control dentro del contenedor.  
  
-   **Opaco**: conjuntos de la `VIEWSTATUS_OPAQUE` de bits en el [VIEWSTATUS](http://msdn.microsoft.com/library/windows/desktop/ms687201) enumeración y dibuja el rectángulo entero del control se pasa a la [CComControlBase:: OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw) método. El control aparece completamente opaco y ninguno de sus contenedores visible más allá de los límites del control.  
  
     Esta configuración ayuda al contenedor a dibujar el control más rápidamente. Si no se selecciona esta opción, el control puede contener partes transparentes.  
  
     Sólo un control opaco puede tener un fondo sólido.  
  
-   Establece el `VIEWSTATUS_SOLIDBKGND` de bits en el `VIEWSTATUS` enumeración. El fondo del control aparece como un color sólido con ningún patrón.  
  
     Esta opción está disponible solo si el **opaco** también se selecciona la opción.  
  
 **Agregar control basado en**  
 Establece el control debe basarse en un tipo de control de Windows mediante la adición de un [CContainedWindow](ccontainedwindowt-class.md) miembro de datos a la clase que implementa el control. También agrega un mapa de mensajes y funciones de controlador de mensajes para controlar los mensajes de Windows para el control. En la lista, elija el tipo de control de Windows que desea crear, si existe.  

  
-   `Button`  
  
-   `ListBox`  
  
-   `SysAnimate32`  
  
-   `SysListView32`  
  
-   `ComboBox`  
  
-   `RichEdit`  
  
-   `SysDateTimePick32`  
  
-   `SysMonthCal32`  
  
-   `ComboBoxEx32`  
  
-   `ScrollBar`  
  
-   `SysHeader32`  
  
-   `SysTabControl32`  
  
-   `Edit`  
  
-   `Static`  
  
-   `SysIPAddress32`  
  
-   `SysTreeView32`  
  
 **Estado de varios**  
 Establece opciones adicionales de apariencia y el comportamiento del control.  
  
-   **Invisible en tiempo de ejecución**: establece el control sea invisible en tiempo de ejecución. Puede usar controles invisibles para realizar operaciones en segundo plano, como activar eventos a intervalos regulares.  
  
-   **Actúa como botón**: establece el `OLEMISC_ACTSLIKEBUTTON` bit en el [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) enumeración para permitir que un control actúe como un botón. Si el contenedor marcó el sitio de cliente del control como un botón predeterminado, al seleccionar esta opción permite que el control de botón para que aparezca como un botón predeterminado por el propio diseño con un marco más grueso. Vea [CComControlBase:: GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault) para obtener más información.  
  
-   **Actúa como etiqueta**: establece el `OLEMISC_ACTSLIKELABEL` de bits en el `OLEMISC` enumeración para permitir que un control reemplace la etiqueta nativa del contenedor. El contenedor determina qué hacer con esta marca, si hay alguna.  
  
 **Otros problemas**  
 Establece las opciones de comportamiento adicional para el control.  
  
-   **Normaliza el controlador de dominio**: establece el control que desee crear un contexto de dispositivo normalizado cuando se llama a dibujarse a sí mismo. Esta acción normaliza la apariencia del control, pero lo hace dibujo menos eficiente.  
  
-   **Solo la ventana**: Especifica que el control no puede ser sin ventana. Si no selecciona esta opción, el control no tiene ventana automáticamente en contenedores que admitan objetos sin ventana, y es automáticamente con ventanas en contenedores que no admitan objetos sin ventana. Si selecciona esta opción, fuerza el control tenga ventana, incluso en contenedores que admiten objetos sin ventana.  
  
-   **Insertable**: seleccione esta opción para que el control aparezca en el **Insertar objeto** cuadro de diálogo de aplicaciones como Word y Excel. El control, a continuación, se puede insertar en cualquier aplicación que admita objetos incrustados a través de este cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Asistente para controles ATL](../../atl/reference/atl-control-wizard.md)   
 [Ejemplo SUBEDIT: Superclase un Control estándar de Windows](http://msdn.microsoft.com/en-us/30e46bdc-ed92-417c-b6b8-359017265a7b)

