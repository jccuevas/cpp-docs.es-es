---
title: Apariencia, Asistente para controles ATL
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.control.misc
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
ms.openlocfilehash: 3484fb5d0f919af0dfd18b584e96d4675e2baea8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319405"
---
# <a name="appearance-atl-control-wizard"></a>Apariencia, Asistente para controles ATL

Utilice esta página del asistente para identificar opciones de elementos de usuario adicionales para el control. Esta página está disponible para los controles identificados como **controles estándar** en **Tipo** de control en la página [Opciones, Asistente para controles ATL.](../../atl/reference/options-atl-control-wizard.md)

## <a name="uielement-list"></a>Lista de UIElement

- **Ver estado**

   Establece la apariencia del control dentro del contenedor.

  - **Opaque**: Establece el VIEWSTATUS_OPAQUE bit en el [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) enumeración y dibuja todo el rectángulo de control pasado a la [CComControlBase::OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw) método. El control parece completamente opaco y ninguno de los contenedores se muestra detrás de los límites del control.

      Esta configuración ayuda al contenedor a dibujar el control más rápidamente. Si esta opción no está seleccionada, el control puede contener piezas transparentes.

      Solo un control opaco puede tener un fondo sólido.

  - **Fondo sólido**: Establece el VIEWSTATUS_SOLIDBKGND bit en la enumeración VIEWSTATUS. El fondo del control aparece como un color sólido sin patrón.

      Esta opción solo está disponible si la opción **Opaque** también está seleccionada.

- **Añadir control basado en**

   Establece el control que se basará en un tipo de control de Windows agregando un [CContainedWindow](ccontainedwindowt-class.md) miembro de datos a la clase que implementa el control. También agrega un mapa de mensajes y funciones de controlador de mensajes para controlar los mensajes de Windows para el control. Elija en la lista el tipo de control de Windows que desea crear, si existe.

  - **Botón**

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

  - **Estática**

  - **SysIPAddress32**

  - **SysTreeView32**

- **Estado misc**

   Establece opciones adicionales de apariencia y comportamiento para el control.

  - **Invisible en tiempo de ejecución:** establece el control para que sea invisible en tiempo de ejecución. Puede utilizar controles invisibles para realizar operaciones en segundo plano, como desencadenar eventos a intervalos de tiempo.

  - **Actúa como botón**: Establece el OLEMISC_ACTSLIKEBUTTON bit de la enumeración [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) para permitir que un control actúe como un botón. Si el contenedor ha marcado el sitio cliente del control como un botón predeterminado, al seleccionar esta opción se permite que el control de botón se muestre como un botón predeterminado dibujándose con un marco más grueso. Vea [CComControlBase::GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault) para obtener más información.

  - **Actúa como etiqueta:** establece el OLEMISC_ACTSLIKELABEL bit de la enumeración OLEMISC para permitir que un control reemplace la etiqueta nativa del contenedor. El contenedor determina qué hacer con esta marca, si acaso.

- **Otros**

   Establece opciones de comportamiento adicionales para el control.

  - **DC normalizado:** establece el control para crear un contexto de dispositivo normalizado cuando se llama para dibujarse a sí mismo. Esta acción estandariza la apariencia del control, pero hace que el dibujo sea menos eficiente.

  - **Solo ventana:** especifica que el control no puede estar sin ventanas. Si no selecciona esta opción, el control no tiene ventanas automáticamente en contenedores que admiten objetos sin ventanas y se muestra automáticamente en contenedores que no admiten objetos sin ventanas. La selección de esta opción obliga a que se ventana el control, incluso en contenedores que admiten objetos sin ventanas.

  - **Insertable:** seleccione esta opción para que el control aparezca en el cuadro de diálogo **Insertar objeto** de aplicaciones como Word y Excel. A continuación, cualquier aplicación que admita objetos incrustados a través de este cuadro de diálogo puede insertar el control.

## <a name="see-also"></a>Consulte también

[Asistente para controles ATL](../../atl/reference/atl-control-wizard.md)<br/>
[Ejemplo de SUBEDIT: Superclases de un control estándar de Windows](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)
