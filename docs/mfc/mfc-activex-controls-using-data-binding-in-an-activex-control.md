---
title: 'Controles ActiveX de MFC: utilizar enlace de datos en un control ActiveX'
ms.date: 11/19/2018
f1_keywords:
- bindable
- requestedit
- defaultbind
- displaybind
- dispid
helpviewer_keywords:
- MFC ActiveX controls [MFC], data binding
- data binding [MFC], MFC ActiveX controls
- data-bound controls [MFC], MFC ActiveX controls
- controls [MFC], data binding
- bound controls [MFC], MFC ActiveX
ms.assetid: 476b590a-bf2a-498a-81b7-dd476bd346f1
ms.openlocfilehash: 3f16ea3ad77c676695a9d5ca6e2deb10637de455
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621181"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>Controles ActiveX de MFC: utilizar enlace de datos en un control ActiveX

Uno de los usos más eficaces de los controles ActiveX es el enlace de datos, que permite enlazar una propiedad del control con un campo específico en una base de datos. Cuando un usuario modifica los datos de esta propiedad enlazada, el control notifica a la base de datos y solicita que se actualice el campo de registro. A continuación, la base de datos notifica al control si la solicitud se ha realizado correctamente o no.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información sobre las tecnologías modernas que reemplazan a ActiveX, vea [controles ActiveX](activex-controls.md).

En este artículo se trata el lado del control de la tarea. La implementación de las interacciones de enlace de datos con la base de datos es responsabilidad del contenedor de controles. La forma de administrar las interacciones de la base de datos en el contenedor queda fuera del ámbito de esta documentación. En el resto de este artículo se explica cómo preparar el control para el enlace de datos.

![Diagrama conceptual de un control enlazado de&#45;de datos](../mfc/media/vc374v1.gif "Diagrama conceptual de un control enlazado de&#45;de datos") <br/>
Diagrama conceptual de un control enlazado a datos

La `COleControl` clase proporciona dos funciones miembro que hacen que el enlace de datos sea un proceso fácil de implementar. La primera función, [BoundPropertyRequestEdit](reference/colecontrol-class.md#boundpropertyrequestedit), se usa para solicitar permiso para cambiar el valor de propiedad. [BoundPropertyChanged](reference/colecontrol-class.md#boundpropertychanged), la segunda función, se llama después de que el valor de la propiedad se haya cambiado correctamente.

En este artículo se tratan los temas siguientes:

- [Crear una propiedad estándar enlazable](#vchowcreatingbindablestockproperty)

- [Crear un método get/set enlazable](#vchowcreatingbindablegetsetmethod)

## <a name="creating-a-bindable-stock-property"></a><a name="vchowcreatingbindablestockproperty"></a>Crear una propiedad estándar enlazable

Es posible crear una propiedad estándar enlazada a datos, aunque es más probable que desee un [método get/set enlazable](#vchowcreatingbindablegetsetmethod).

> [!NOTE]
> Las propiedades estándar tienen `bindable` los `requestedit` atributos y de forma predeterminada.

#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>Para agregar una propiedad estándar enlazable mediante el Asistente para agregar propiedades

1. Iniciar un proyecto mediante el [Asistente para controles ActiveX MFC](reference/mfc-activex-control-wizard.md).

1. Haga clic con el botón secundario en el nodo de interfaz del control.

   Se abrirá el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar propiedad**.

1. Seleccione una de las entradas de la lista desplegable **nombre de propiedad** . Por ejemplo, puede seleccionar **texto**.

   Dado que el **texto** es una propiedad estándar, los atributos **Bindable** y **requestedit** ya están comprobados.

1. Active las siguientes casillas en la pestaña **atributos IDL** : **displaybind** y **defaultbind** para agregar los atributos a la definición de propiedad en el del proyecto. Archivo IDL. Estos atributos hacen que el control sea visible para el usuario y convierta la propiedad estándar en la propiedad enlazable predeterminada.

En este momento, el control puede mostrar los datos de un origen de datos, pero el usuario no podrá actualizar los campos de datos. Si desea que el control también pueda actualizar los datos, cambie la `OnOcmCommand` función [OnOcmCommand](mfc-activex-controls-subclassing-a-windows-control.md) para que tenga el siguiente aspecto:

[!code-cpp[NVC_MFC_AxData#1](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

Ahora puede compilar el proyecto, que registrará el control. Al insertar el control en un cuadro de diálogo, se agregan las propiedades de los **campos** de datos y del **origen de datos** , y ahora puede seleccionar un origen de datos y un campo para mostrar en el control.

## <a name="creating-a-bindable-getset-method"></a><a name="vchowcreatingbindablegetsetmethod"></a>Crear un método get/set enlazable

Además de un método get/set enlazado a datos, también puede crear una [propiedad estándar enlazable](#vchowcreatingbindablestockproperty).

> [!NOTE]
> En este procedimiento se supone que tiene un proyecto de control ActiveX que subclase un control de Windows.

#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>Para agregar un método get/set enlazable mediante el Asistente para agregar propiedades

1. Cargue el proyecto del control.

1. En la página **configuración del control** , seleccione una clase de ventana para el control que se va a subclase. Por ejemplo, puede que desee subclase de un control de edición.

1. Cargue el proyecto del control.

1. Haga clic con el botón secundario en el nodo de interfaz del control.

   Se abrirá el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar propiedad**.

1. Escriba el nombre de la propiedad en el cuadro **nombre de propiedad** . Use `MyProp` en este ejemplo.

1. Seleccione un tipo de datos en el cuadro de lista desplegable **tipo de propiedad** . Utilice **Short** en este ejemplo.

1. Para **Tipo de implementación**, haga clic en **Métodos Get/Set**.

1. Active las siguientes casillas en la pestaña atributos IDL: **Bindable**, **requestedit**, **displaybind**y **defaultbind** para agregar los atributos a la definición de propiedad en el del proyecto. Archivo IDL. Estos atributos hacen que el control sea visible para el usuario y convierta la propiedad estándar en la propiedad enlazable predeterminada.

1. Haga clic en **Finalizar**

1. Modifique el cuerpo de la `SetMyProp` función para que contenga el código siguiente:

   [!code-cpp[NVC_MFC_AxData#2](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]

1. El parámetro pasado a las `BoundPropertyChanged` `BoundPropertyRequestEdit` funciones y es el DISPID de la propiedad, que es el parámetro pasado al atributo ID () de la propiedad en. Archivo IDL.

1. Modifique la función [OnOcmCommand](mfc-activex-controls-subclassing-a-windows-control.md) para que contenga el código siguiente:

   [!code-cpp[NVC_MFC_AxData#1](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

1. Modifique la `OnDraw` función para que contenga el código siguiente:

   [!code-cpp[NVC_MFC_AxData#3](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]

1. En la sección Public del archivo de encabezado del archivo de encabezado de la clase de control, agregue las siguientes definiciones (constructores) para las variables de miembro:

   [!code-cpp[NVC_MFC_AxData#4](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]

1. Convertir la línea siguiente en la última línea de la `DoPropExchange` función:

   [!code-cpp[NVC_MFC_AxData#5](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]

1. Modifique la `OnResetState` función para que contenga el código siguiente:

   [!code-cpp[NVC_MFC_AxData#6](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]

1. Modifique la `GetMyProp` función para que contenga el código siguiente:

   [!code-cpp[NVC_MFC_AxData#7](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]

Ahora puede compilar el proyecto, que registrará el control. Al insertar el control en un cuadro de diálogo, se agregan las propiedades de los **campos** de datos y del **origen de datos** , y ahora puede seleccionar un origen de datos y un campo para mostrar en el control.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)
