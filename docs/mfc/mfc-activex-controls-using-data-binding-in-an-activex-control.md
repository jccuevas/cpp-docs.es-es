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
ms.openlocfilehash: 41ac0180242aea3143a1df2c32dc81fb18cd7dca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370783"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>Controles ActiveX de MFC: utilizar enlace de datos en un control ActiveX

Uno de los usos más eficaces de los controles ActiveX es el enlace de datos, que permite que una propiedad del control se enlace con un campo específico de una base de datos. Cuando un usuario modifica los datos de esta propiedad enlazada, el control notifica a la base de datos y solicita que se actualice el campo de registro. A continuación, la base de datos notifica al control del éxito o error de la solicitud.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe utilizarse para el nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que reemplazan a ActiveX, vea [Controles ActiveX](activex-controls.md).

En este artículo se trata el lado de control de la tarea. Implementar las interacciones de enlace de datos con la base de datos es responsabilidad del contenedor de control. La forma de administrar las interacciones de la base de datos en el contenedor está fuera del ámbito de esta documentación. La forma de preparar el control para el enlace de datos se explica en el resto de este artículo.

![Diagrama conceptual de un control enlazado de&#45;de datos](../mfc/media/vc374v1.gif "Diagrama conceptual de un control enlazado de&#45;de datos") <br/>
Diagrama conceptual de un control enlazado a datos

La `COleControl` clase proporciona dos funciones miembro que hacen que el enlace de datos sea un proceso fácil de implementar. La primera función, [BoundPropertyRequestEdit](../mfc/reference/colecontrol-class.md#boundpropertyrequestedit), se utiliza para solicitar permiso para cambiar el valor de la propiedad. [BoundPropertyChanged](../mfc/reference/colecontrol-class.md#boundpropertychanged), se llama a la segunda función después de que el valor de la propiedad se ha cambiado correctamente.

En este artículo se tratan los temas siguientes:

- [Creación de una propiedad de stock enlazable](#vchowcreatingbindablestockproperty)

- [Creación de un método Get/Set enlazable](#vchowcreatingbindablegetsetmethod)

## <a name="creating-a-bindable-stock-property"></a><a name="vchowcreatingbindablestockproperty"></a>Creación de una propiedad de stock enlazable

Es posible crear una propiedad de stock enlazada a datos, aunque es más probable que desee un [método get/set enlazable.](#vchowcreatingbindablegetsetmethod)

> [!NOTE]
> Las propiedades `bindable` de `requestedit` stock tienen los atributos y de forma predeterminada.

#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>Para agregar una propiedad de stock enlazable mediante el Asistente para agregar propiedades

1. Comience un proyecto mediante el [Asistente para controles ActiveX](../mfc/reference/mfc-activex-control-wizard.md)de MFC.

1. Haga clic con el botón derecho en el nodo de interfaz del control.

   Se abrirá el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, haga clic en **Agregar propiedad**.

1. Seleccione una de las entradas de la lista desplegable Nombre de **propiedad.** Por ejemplo, puede seleccionar **Texto**.

   Dado que **Text** es una propiedad de stock, los atributos **bindable** y **requestedit** ya están comprobados.

1. Seleccione las siguientes casillas de verificación de la pestaña **Atributos IDL:** **displaybind** y **defaultbind** para agregar los atributos a la definición de propiedad en el proyecto. IDL. Estos atributos hacen que el control sea visible para el usuario y hacen que la propiedad stock sea la propiedad enlazable predeterminada.

En este punto, el control puede mostrar datos de un origen de datos, pero el usuario no podrá actualizar los campos de datos. Si desea que el control también pueda actualizar `OnOcmCommand` los datos, cambie la función [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) para que tenga el siguiente aspecto:

[!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

Ahora puede compilar el proyecto, que registrará el control. Al insertar el control en un cuadro de diálogo, se habrán agregado las propiedades **Campo** de datos y **Origen** de datos y ahora puede seleccionar un origen de datos y un campo para mostrar en el control.

## <a name="creating-a-bindable-getset-method"></a><a name="vchowcreatingbindablegetsetmethod"></a>Creación de un método Get/Set enlazable

Además de un método get/set enlazado a datos, también puede crear una propiedad de [stock enlazable.](#vchowcreatingbindablestockproperty)

> [!NOTE]
> En este procedimiento se supone que tiene un proyecto de control ActiveX que subclase un control de Windows.

#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>Para agregar un método get/set enlazable mediante el Asistente para agregar propiedades

1. Cargue el proyecto del control.

1. En la página Configuración de **control,** seleccione una clase de ventana para que el control subclase. Por ejemplo, es posible que desee subclase un EDIT control.

1. Cargue el proyecto del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control.

   Se abrirá el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, haga clic en **Agregar propiedad**.

1. Escriba el nombre de la propiedad en el cuadro Nombre de **propiedad.** Utilícelo `MyProp` para este ejemplo.

1. Seleccione un tipo de datos en el cuadro de lista desplegable Tipo de **propiedad.** Utilice **short** para este ejemplo.

1. Para **Tipo de implementación**, haga clic en **Métodos Get/Set**.

1. Active las siguientes casillas de verificación de la pestaña Atributos IDL: **bindable**, **requestedit**, **displaybind**y **defaultbind** para agregar los atributos a la definición de propiedad en el proyecto. IDL. Estos atributos hacen que el control sea visible para el usuario y hacen que la propiedad stock sea la propiedad enlazable predeterminada.

1. Haga clic en **Finalizar**

1. Modifique el cuerpo `SetMyProp` de la función para que contenga el código siguiente:

   [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]

1. El parámetro pasado `BoundPropertyChanged` `BoundPropertyRequestEdit` a las funciones y es el dispid de la propiedad, que es el parámetro pasado al atributo id() de la propiedad en el archivo . IDL.

1. Modifique la función [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) para que contenga el código siguiente:

   [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

1. Modifique `OnDraw` la función para que contenga el código siguiente:

   [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]

1. A la sección pública del archivo de encabezado, el archivo de encabezado de la clase de control, agregue las siguientes definiciones (constructores) para las variables miembro:

   [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]

1. Haga que la siguiente línea `DoPropExchange` sea la última línea de la función:

   [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]

1. Modifique `OnResetState` la función para que contenga el código siguiente:

   [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]

1. Modifique `GetMyProp` la función para que contenga el código siguiente:

   [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]

Ahora puede compilar el proyecto, que registrará el control. Al insertar el control en un cuadro de diálogo, se habrán agregado las propiedades **Campo** de datos y **Origen** de datos y ahora puede seleccionar un origen de datos y un campo para mostrar en el control.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)
