---
title: Apariencia, Asistente para controles ATL
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.control.misc
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
ms.openlocfilehash: 4d3b0519951636fad4175dc35261ba35b3694ffa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62248958"
---
# <a name="appearance-atl-control-wizard"></a>Apariencia, Asistente para controles ATL

Utilice esta página del Asistente para identificar las opciones de elemento de usuario adicionales para el control. Esta página está disponible para los controles identificados como **controles estándar** en **tipo de Control** en el [opciones, Asistente para controles ATL](../../atl/reference/options-atl-control-wizard.md) página.

## <a name="uielement-list"></a>Lista de UIElement

- **Estado de vista**

   Establece la apariencia del control dentro del contenedor.

   - **Opaque**: Establece el bit VIEWSTATUS_OPAQUE en el [VIEWSTATUS](/windows/desktop/api/ocidl/ne-ocidl-tagviewstatus) enumeración y dibuja el rectángulo de todo el control pasa a la [CComControlBase:: OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw) método. El control aparece completamente opaco y ninguno de sus contenedores muestra detrás de los límites del control.

      Esta configuración permite que el contenedor de dibujar el control más rápidamente. Si no se selecciona esta opción, el control puede contener las partes transparentes.

      Sólo un control opaco puede tener un fondo sólido.

   - **Fondo sólido**: Establece el bit VIEWSTATUS_SOLIDBKGND en la enumeración VIEWSTATUS. El fondo del control aparece como un color sólido con ningún patrón.

      Esta opción está disponible solo si el **opaco** también se selecciona la opción.

- **Agregar control basado en**

   Establece el control debe basarse en un tipo de control de Windows mediante la adición de un [CContainedWindow](ccontainedwindowt-class.md) miembro de datos a la clase que implementa el control. También agrega un mapa de mensajes y funciones de controlador de mensajes para controlar los mensajes de Windows para el control. En la lista, elija el tipo de control de Windows que desea crear, si existe.

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

- **Estado de varios**

   Establece las opciones de apariencia y comportamiento adicionales para el control.

   - **Invisible en tiempo de ejecución**: Establece el control sea invisible en tiempo de ejecución. Puede usar controles invisibles para realizar operaciones en segundo plano, como la activación de eventos a intervalos de tiempo.

   - **Actúa como botón**: Establece el bit OLEMISC_ACTSLIKEBUTTON en el [OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc) enumeración para permitir que un control para que actúe como un botón. Si el contenedor ha marcado el sitio de cliente del control como un botón predeterminado, al seleccionar esta opción permite que el control de botón para que se muestre como un botón predeterminado mediante el dibujo de sí mismo con un marco más grueso. Consulte [CComControlBase:: GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault) para obtener más información.

   - **Actúa como etiqueta**: Establece el bit OLEMISC_ACTSLIKELABEL en la enumeración OLEMISC para permitir que un control reemplazar la etiqueta del contenedor nativo. El contenedor determina qué hacer con esta marca, caso en todo.

- **Otros problemas**

   Establece las opciones de comportamiento adicional para el control.

   - **Normaliza DC**: Establece el control para crear un contexto de dispositivo normalizado cuando se llama a dibujarse a sí mismo. Esta acción normaliza la apariencia del control, pero resulta que dibujo menos eficiente.

   - **Ventana solo**: Especifica que el control no puede ser sin ventanas. Si no selecciona esta opción, el control no tiene ventana automáticamente en los contenedores que admiten objetos sin ventana y con ventana en contenedores que no admiten objetos sin ventana. Al seleccionar esta opción fuerza el control de ventana, incluso en los contenedores que admiten objetos sin ventana.

   - **Insertable**: Seleccione esta opción para que el control aparezca en el **Insertar objeto** cuadro de diálogo de las aplicaciones como Word y Excel. El control, a continuación, se puede insertar en cualquier aplicación que admite objetos incrustados mediante este cuadro de diálogo.

## <a name="see-also"></a>Vea también

[Asistente para controles ATL](../../atl/reference/atl-control-wizard.md)<br/>
[Ejemplo SUBEDIT: Convierte en superclase un Control estándar de Windows](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)
