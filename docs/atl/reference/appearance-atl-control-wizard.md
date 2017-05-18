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
caps.latest.revision: 12
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
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: dde27a7b62f3ee3b5fe8fcacd8141e9f89ed3c98
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="appearance-atl-control-wizard"></a>Apariencia, Asistente para controles ATL
Inserte aquí "Resultados de búsqueda" resumen.  
  
 Utilice esta página del Asistente para identificar opciones de elemento de usuario adicionales para el control. Esta página está disponible para los controles identificados como **controles estándar** en **tipo de Control** en el [opciones, Asistente para controles ATL](../../atl/reference/options-atl-control-wizard.md) página.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Estado de vista**  
 Establece la apariencia del control dentro del contenedor.  
  
-   **Opaco**: establece el `VIEWSTATUS_OPAQUE` bit en la [VIEWSTATUS](http://msdn.microsoft.com/library/windows/desktop/ms687201) enumeración y dibuja el rectángulo entero del control que se pasa a la [CComControlBase:: OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw) (método). El control aparece completamente opaco, y ninguno de sus contenedores muestra detrás de los límites del control.  
  
     Esta configuración ayuda al contenedor a dibujar el control más rápidamente. Si no se selecciona esta opción, el control puede contener partes transparentes.  
  
     Sólo un control opaco puede tener un fondo sólido.  
  
-   Establece la `VIEWSTATUS_SOLIDBKGND` de bits en el `VIEWSTATUS` (enumeración). El fondo del control aparece como un color sólido con ningún patrón.  
  
     Esta opción está disponible sólo si la **opaco** también se selecciona la opción.  
  
 **Agregar control basado en**  
 Establece el control que basarse en un tipo de control de Windows mediante la adición de un [CContainedWindow](ccontainedwindowt-class.md) miembro de datos a la clase que implementa el control. También agrega un mapa de mensajes y funciones de controlador de mensajes para controlar los mensajes de Windows para el control. En la lista, elija el tipo de control de Windows que desea crear, si existe.  

  
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
  
 **Estados varios**  
 Establece opciones adicionales de aspecto y el comportamiento del control.  
  
-   **Invisible en tiempo de ejecución**: establece el control sea invisible en tiempo de ejecución. Puede usar controles invisibles para realizar operaciones en segundo plano, como activar eventos a intervalos de tiempo.  
  
-   **Actúa como botón**: establece el `OLEMISC_ACTSLIKEBUTTON` de bits en el [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) enumeración para permitir que un control para que actúe como un botón. Si el contenedor marcó el sitio de cliente del control como un botón predeterminado, al seleccionar esta opción permite que el control de botón para que se muestre como un botón predeterminado mediante el dibujo de sí mismo con un marco más grueso. Consulte [CComControlBase:: GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault) para obtener más información.  
  
-   **Actúa como etiqueta**: establece el `OLEMISC_ACTSLIKELABEL` de bits en el `OLEMISC` (enumeración) para permitir que un control reemplace la etiqueta nativa del contenedor. El contenedor determina qué hacer con este indicador, si hay alguna.  
  
 **Otros problemas**  
 Establece opciones de comportamiento adicional para el control.  
  
-   **Normaliza DC**: establece el control para crear un contexto de dispositivo normalizado cuando se llama a dibujarse a sí mismo. Esta acción estandariza la apariencia del control, pero hace dibujo menos eficiente.  
  
-   **Solo la ventana**: Especifica que el control no puede carecer de ventana. Si no selecciona esta opción, el control no tiene automáticamente ventana en contenedores que admitan objetos sin ventana, y con ventana en contenedores que admitan objetos sin ventana. Esta opción obliga al control tenga ventana, incluso en contenedores que admitan objetos sin ventana.  
  
-   **Insertable**: seleccione esta opción para que el control aparezca en el **Insertar objeto** cuadro de diálogo de aplicaciones como Word y Excel. A continuación, se puede insertar el control de cualquier aplicación que admita objetos incrustados mediante este cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Asistente para controles ATL](../../atl/reference/atl-control-wizard.md)   
 [Ejemplo SUBEDIT: Convierte en superclase un Control estándar de Windows](http://msdn.microsoft.com/en-us/30e46bdc-ed92-417c-b6b8-359017265a7b)


