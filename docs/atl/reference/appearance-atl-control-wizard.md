---
title: Apariencia, Asistente para controles ATL
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.control.misc
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
ms.openlocfilehash: e07dc017241848f1a670c17b12c2254de6d1b8e1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492181"
---
# <a name="appearance-atl-control-wizard"></a>Apariencia, Asistente para controles ATL

Utilice esta página del Asistente para identificar las opciones adicionales del elemento de usuario para el control. Esta página está disponible para los controles identificados como **controles estándar** en **tipo de control** en la página [Opciones, Asistente para controles ATL](../../atl/reference/options-atl-control-wizard.md) .

## <a name="uielement-list"></a>Lista de UIElement

- **Ver estado**

   Establece la apariencia del control dentro del contenedor.

   - **Opaco**: Establece el bit VIEWSTATUS_OPAQUE en la enumeración [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) y dibuja el rectángulo de control completo que se pasa al método [CComControlBase:: OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw) . El control aparece completamente opaco y ninguno de los contenedores se muestra detrás de los límites del control.

      Esta configuración ayuda al contenedor a dibujar el control más rápidamente. Si no se selecciona esta opción, el control puede contener partes transparentes.

      Solo un control opaco puede tener un fondo sólido.

   - **Fondo sólido**: Establece el bit VIEWSTATUS_SOLIDBKGND en la enumeración VIEWSTATUS. El fondo del control aparece como un color sólido sin ningún patrón.

      Esta opción solo está disponible si la opción **opaca** también está seleccionada.

- **Agregar control basado en**

   Establece el control que se va a basar en un tipo de control de Windows agregando un miembro de datos [CContainedWindow](ccontainedwindowt-class.md) a la clase que implementa el control. También agrega un mapa de mensajes y las funciones del controlador de mensajes para controlar los mensajes de Windows para el control. Elija en la lista el tipo de control de Windows que desea crear, si existe.

   - **Button**

   - **ListBox**

   - **SysAnimate32**

   - **SysListView32**

   - **ComboBox**

   - **RichEdit**

   - **SysDateTimePick32**

   - **SysMonthCal32**

   - **ComboBoxEx32**

   - **ScrollBar**

   - **SysHeader32**

   - **SysTabControl32**

   - **Editar**

   - **Static**

   - **SysIPAddress32**

   - **SysTreeView32**

- **Estado varios**

   Establece opciones de apariencia y comportamiento adicionales para el control.

   - **Invisible en tiempo de ejecución**: Establece que el control sea invisible en tiempo de ejecución. Puede usar controles invisibles para realizar operaciones en segundo plano, como la activación de eventos a intervalos de tiempo.

   - **Actúa como botón**: Establece el bit OLEMISC_ACTSLIKEBUTTON en la enumeración [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) para permitir que un control actúe como un botón. Si el contenedor ha marcado el sitio de cliente del control como un botón predeterminado, al seleccionar esta opción se habilita el control de botón para que se muestre como un botón predeterminado; para ello, debe dibujarse con un marco más grueso. Vea [CComControlBase:: GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault) para obtener más información.

   - **Actúa como etiqueta**: Establece el bit OLEMISC_ACTSLIKELABEL en la enumeración OLEMISC para permitir que un control Reemplace la etiqueta nativa del contenedor. El contenedor determina qué hacer con esta marca, en caso de que haya algo.

- **Otros problemas**

   Establece opciones de comportamiento adicionales para el control.

   - **Controlador de dominio normalizado**: Establece el control para crear un contexto de dispositivo normalizado cuando se llama para dibujarse a sí mismo. Esta acción normaliza la apariencia del control, pero hace que el dibujo sea menos eficaz.

   - **Solo ventana**: Especifica que el control no puede tener ventanas. Si no selecciona esta opción, el control no tiene ventanas en los contenedores que admiten objetos sin ventanas y se activa automáticamente en contenedores que no admiten objetos sin ventanas. Al seleccionar esta opción, se fuerza el control en ventanas, incluso en contenedores que admiten objetos sin ventanas.

   - **Insertable**: Seleccione esta opción para que el control aparezca en el cuadro de diálogo **Insertar objeto** de aplicaciones como Word y Excel. Después, el control puede ser insertado por cualquier aplicación que admita objetos incrustados a través de este cuadro de diálogo.

## <a name="see-also"></a>Vea también

[Asistente para controles ATL](../../atl/reference/atl-control-wizard.md)<br/>
[Ejemplo de SubEdit: Superclases de un control estándar de Windows](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)
