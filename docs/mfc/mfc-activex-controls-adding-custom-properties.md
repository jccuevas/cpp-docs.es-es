---
title: 'Controles ActiveX MFC: Agregar propiedades personalizadas'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
ms.openlocfilehash: 00f7a879582bca562ce626fe224206094fd19bc7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364701"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>Controles ActiveX MFC: Agregar propiedades personalizadas

Las propiedades personalizadas difieren de las propiedades de `COleControl` stock en que las propiedades personalizadas no están implementadas por la clase. Una propiedad personalizada se utiliza para exponer un determinado estado o apariencia de un control ActiveX a un programador mediante el control.

En este artículo se describe cómo agregar una propiedad personalizada al control ActiveX mediante el Asistente para agregar propiedades y se explican las modificaciones de código resultantes. Contenido de los temas:

- [Uso del Asistente para agregar propiedades para agregar una propiedad personalizada](#_core_using_classwizard_to_add_a_custom_property)

- [Agregar cambios en el Asistente para propiedades personalizadas](#_core_classwizard_changes_for_custom_properties)

Las propiedades personalizadas vienen en cuatro variedades de implementación: Variable miembro, Variable miembro con notificación, Métodos Get/Set y Parametrizado.

- Implementación de variables miembro

   Esta implementación representa el estado de la propiedad como una variable miembro en la clase de control. Utilice la implementación de la variable miembro cuando no es importante saber cuándo cambia el valor de propiedad. De los tres tipos, esta implementación crea la menor cantidad de código de soporte técnico para la propiedad. La macro de entrada de asignación de distribución para la implementación de la variable miembro es [DISP_PROPERTY](../mfc/reference/dispatch-maps.md#disp_property).

- Variable miembro con implementación de notificaciones

   Esta implementación consta de una variable miembro y una función de notificación creada por el Asistente para agregar propiedades. El marco de trabajo llama automáticamente a la función de notificación después de que cambie el valor de propiedad. Utilice la variable miembro con implementación de notificación cuando necesite recibir una notificación después de que un valor de propiedad haya cambiado. Esta implementación requiere más tiempo porque requiere una llamada de función. La macro de entrada de mapa de distribución para esta implementación es [DISP_PROPERTY_NOTIFY](../mfc/reference/dispatch-maps.md#disp_property_notify).

- Implementación de métodos Get/Set

   Esta implementación consta de un par de funciones miembro en la clase de control. El Get/Set Methods implementación llama automáticamente a la Get función miembro cuando el usuario del control solicita el valor actual de la propiedad y el Set función miembro cuando el usuario del control solicita que se cambie la propiedad. Utilice esta implementación cuando necesite calcular el valor de una propiedad durante el tiempo de ejecución, validar un valor pasado por el usuario del control antes de cambiar la propiedad real o implementar un tipo de propiedad de solo lectura o escritura. La macro de entrada de mapa de distribución para esta implementación se [DISP_PROPERTY_EX.](../mfc/reference/dispatch-maps.md#disp_property_ex) En la sección siguiente, [Uso del Asistente para agregar propiedades para agregar una propiedad personalizada](#_core_using_classwizard_to_add_a_custom_property), se usa la propiedad personalizada CircleOffset para demostrar esta implementación.

- Implementación parametrizada

   La implementación parametrizada es compatible con el Asistente para agregar propiedades. Una propiedad parametrizada (a veces denominada matriz de propiedades) se puede utilizar para tener acceso a un conjunto de valores a través de una sola propiedad del control. La macro de entrada de mapa de distribución para esta implementación se DISP_PROPERTY_PARAM. Para obtener más información sobre cómo implementar este tipo, vea [Implementar una propiedad parametrizada](../mfc/mfc-activex-controls-advanced-topics.md) en el artículo Controles ActiveX: temas avanzados.

## <a name="using-the-add-property-wizard-to-add-a-custom-property"></a><a name="_core_using_classwizard_to_add_a_custom_property"></a>Uso del Asistente para agregar propiedades para agregar una propiedad personalizada

El siguiente procedimiento muestra cómo agregar una propiedad personalizada, CircleOffset, que usa el Get/Set Methods implementación. El CircleOffset propiedad personalizada permite al usuario del control para desplazar el círculo desde el centro del rectángulo delimitador del control. El procedimiento para agregar propiedades personalizadas con una implementación distinta de Get/Set Methods es muy similar.

Este mismo procedimiento también se puede usar para agregar otras propiedades personalizadas que desee. Sustituya el nombre de la propiedad personalizada por el nombre y los parámetros de la propiedad CircleOffset.

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>Para agregar la propiedad personalizada CircleOffset mediante el Asistente para agregar propiedades

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, haga clic en **Agregar propiedad**.

   Se abrirá el [Asistente para agregar propiedades](../ide/names-add-property-wizard.md).

1. En el cuadro Nombre de **propiedad** , escriba *CircleOffset*.

1. Para **Tipo de implementación**, haga clic en **Métodos Get/Set**.

1. En el cuadro **Tipo de propiedad,** seleccione **short**.

1. Escriba nombres únicos para las funciones Get y Set o acepte los nombres predeterminados.

1. Haga clic en **Finalizar**

## <a name="add-property-wizard-changes-for-custom-properties"></a><a name="_core_classwizard_changes_for_custom_properties"></a>Agregar cambios del Asistente para propiedades personalizadas

Al agregar la propiedad personalizada CircleOffset, el Asistente para agregar propiedades realiza cambios en el encabezado (. H) y la implementación (. CPP) de la clase de control.

Las siguientes líneas se agregan al archivo . H para declarar dos `GetCircleOffset` `SetCircleOffset`funciones llamadas y:

[!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

La siguiente línea se agrega a la de su control. Archivo IDL:

[!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

Esta línea asigna a la propiedad CircleOffset un número de identificador específico, tomado de la posición del método en la lista de métodos y propiedades del Asistente para agregar propiedades.

Además, la siguiente línea se agrega al mapa de distribución (en el archivo . CPP de la clase de control) para asignar la propiedad CircleOffset a las dos funciones de controlador del control:

[!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

Por último, las `GetCircleOffset` implementaciones de las funciones y `SetCircleOffset` se agregan al final del control. Archivo CPP. En la mayoría de los casos, modificará la función Get para devolver el valor de la propiedad. La función Set normalmente contendrá código que se debe ejecutar antes o después de que cambie la propiedad.

[!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

Tenga en cuenta que el Asistente para agregar propiedades agrega automáticamente una llamada, a [SetModifiedFlag](../mfc/reference/colecontrol-class.md#setmodifiedflag), al cuerpo de la Set función. Llamar a esta función marca el control como modificado. Si se ha modificado un control, su nuevo estado se guardará cuando se guarde el contenedor. Esta función debe llamarse cada vez que una propiedad, guardada como parte del estado persistente del control, cambia el valor.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Controles ActiveX MFC: Propiedades](../mfc/mfc-activex-controls-properties.md)<br/>
[Controles ActiveX MFC: Métodos](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl (clase)](../mfc/reference/colecontrol-class.md)
