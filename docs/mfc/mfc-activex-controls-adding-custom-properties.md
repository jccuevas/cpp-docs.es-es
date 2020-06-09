---
title: 'Controles ActiveX MFC: Agregar propiedades personalizadas'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
ms.openlocfilehash: 5014a32386a0a140f0fdc00b23a0ac24a54afcee
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626149"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>Controles ActiveX MFC: Agregar propiedades personalizadas

Las propiedades personalizadas se diferencian de las propiedades estándar en que las propiedades personalizadas todavía no están implementadas por la `COleControl` clase. Una propiedad personalizada se utiliza para exponer un determinado Estado o apariencia de un control ActiveX a un programador mediante el control.

En este artículo se describe cómo agregar una propiedad personalizada al control ActiveX mediante el Asistente para agregar propiedades y se explican las modificaciones de código resultantes. Contenido de los temas:

- [Usar el Asistente para agregar propiedades para agregar una propiedad personalizada](#_core_using_classwizard_to_add_a_custom_property)

- [Cambios del Asistente para agregar propiedades para las propiedades personalizadas](#_core_classwizard_changes_for_custom_properties)

Las propiedades personalizadas tienen cuatro variedades de implementación: variable miembro, variable miembro con la notificación, métodos Get/Set y parametrizados.

- Implementación de variables miembro

   Esta implementación representa el estado de la propiedad como una variable miembro en la clase del control. Utilice la implementación de variables miembro cuando no sea importante saber cuándo cambia el valor de la propiedad. De los tres tipos, esta implementación crea la cantidad mínima de código de compatibilidad para la propiedad. La macro de entrada de mapa de envío para la implementación de variables miembro es [DISP_PROPERTY](reference/dispatch-maps.md#disp_property).

- Variable miembro con implementación de notificación

   Esta implementación consta de una variable miembro y una función de notificación creada por el Asistente para agregar propiedades. El marco de trabajo llama automáticamente a la función de notificación después de que cambie el valor de la propiedad. Use la variable miembro con la implementación de notificaciones cuando necesite recibir una notificación cuando haya cambiado un valor de propiedad. Esta implementación requiere más tiempo porque requiere una llamada de función. La macro de entrada de mapa de envío para esta implementación es [DISP_PROPERTY_NOTIFY](reference/dispatch-maps.md#disp_property_notify).

- Implementación de métodos Get/Set

   Esta implementación consta de un par de funciones miembro en la clase control. La implementación de los métodos Get/Set llama automáticamente a la función miembro Get cuando el usuario del control solicita el valor actual de la propiedad y la función miembro SET cuando el usuario del control solicita que se cambie la propiedad. Utilice esta implementación cuando necesite calcular el valor de una propiedad durante el tiempo de ejecución, validar un valor pasado por el usuario del control antes de cambiar la propiedad real o implementar un tipo de propiedad de solo lectura o de solo escritura. La macro de entrada de mapa de envío para esta implementación es [DISP_PROPERTY_EX](reference/dispatch-maps.md#disp_property_ex). En la siguiente sección, el [uso del Asistente para agregar propiedades para agregar una propiedad personalizada](#_core_using_classwizard_to_add_a_custom_property), se usa la propiedad personalizada CircleOffset para mostrar esta implementación.

- Implementación parametrizada

   La implementación parametrizada es compatible con el Asistente para agregar propiedades. Una propiedad parametrizada (a veces denominada matriz de propiedades) se puede usar para tener acceso a un conjunto de valores a través de una única propiedad del control. La macro de entrada de mapa de envío para esta implementación es DISP_PROPERTY_PARAM. Para obtener más información sobre la implementación de este tipo, vea [implementar una propiedad parametrizada](mfc-activex-controls-advanced-topics.md) en el artículo controles ActiveX: temas avanzados.

## <a name="using-the-add-property-wizard-to-add-a-custom-property"></a><a name="_core_using_classwizard_to_add_a_custom_property"></a>Usar el Asistente para agregar propiedades para agregar una propiedad personalizada

En el procedimiento siguiente se muestra cómo agregar una propiedad personalizada, CircleOffset, que usa la implementación de los métodos Get/Set. La propiedad personalizada CircleOffset permite al usuario del control desplazar el círculo desde el centro del rectángulo delimitador del control. El procedimiento para agregar propiedades personalizadas con una implementación distinta de los métodos Get/Set es muy similar.

Este mismo procedimiento también se puede usar para agregar otras propiedades personalizadas que desee. Sustituya el nombre de la propiedad personalizada por el nombre de la propiedad CircleOffset y los parámetros.

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>Para agregar la propiedad personalizada CircleOffset mediante el Asistente para agregar propiedades

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar propiedad**.

   Se abrirá el [Asistente para agregar propiedades](../ide/names-add-property-wizard.md).

1. En el cuadro **nombre de propiedad** , escriba *CircleOffset*.

1. Para **Tipo de implementación**, haga clic en **Métodos Get/Set**.

1. En el cuadro **tipo de propiedad** , seleccione **Short**.

1. Escriba nombres únicos para las funciones Get y set o acepte los nombres predeterminados.

1. Haga clic en **Finalizar**

## <a name="add-property-wizard-changes-for-custom-properties"></a><a name="_core_classwizard_changes_for_custom_properties"></a>Cambios del Asistente para agregar propiedades para las propiedades personalizadas

Al agregar la propiedad personalizada CircleOffset, el Asistente para agregar propiedades realiza cambios en el encabezado (. H) y la implementación (. CPP) de la clase control.

Las líneas siguientes se agregan a. H para declarar dos funciones llamadas `GetCircleOffset` y `SetCircleOffset` :

[!code-cpp[NVC_MFC_AxUI#25](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

La línea siguiente se agrega al del control. Archivo IDL:

[!code-cpp[NVC_MFC_AxUI#26](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

Esta línea asigna a la propiedad CircleOffset un número de identificador específico, tomado de la posición del método en la lista métodos y propiedades del Asistente para agregar propiedades.

Además, se agrega la línea siguiente al mapa de envío (en. Archivo CPP de la clase del control) para asignar la propiedad CircleOffset a las dos funciones de controlador del control:

[!code-cpp[NVC_MFC_AxUI#27](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

Por último, las implementaciones de `GetCircleOffset` las `SetCircleOffset` funciones y se agregan al final de la del control. Archivo CPP. En la mayoría de los casos, modificará la función get para devolver el valor de la propiedad. La función set normalmente contendrá código que debe ejecutarse antes o después de la modificación de la propiedad.

[!code-cpp[NVC_MFC_AxUI#28](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

Tenga en cuenta que el Asistente para agregar propiedades agrega automáticamente una llamada a [SetModifiedFlag](reference/colecontrol-class.md#setmodifiedflag)para el cuerpo de la función set. La llamada a esta función marca el control como modificado. Si se ha modificado un control, su nuevo estado se guardará cuando se guarde el contenedor. Se debe llamar a esta función siempre que una propiedad, guardada como parte del estado persistente del control, cambie el valor.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)<br/>
[Controles ActiveX MFC: Propiedades](mfc-activex-controls-properties.md)<br/>
[Controles ActiveX MFC: Métodos](mfc-activex-controls-methods.md)<br/>
[COleControl (clase)](reference/colecontrol-class.md)
