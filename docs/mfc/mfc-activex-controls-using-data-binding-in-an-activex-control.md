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
ms.openlocfilehash: a5cb73496cd6678e3f45500d9d53c2127b0fb17c
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175814"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>Controles ActiveX de MFC: utilizar enlace de datos en un control ActiveX

Uno de los usos más eficaces de controles ActiveX es el enlace de datos, lo que permite una propiedad del control para enlazar con un campo específico en una base de datos. Cuando un usuario modifica los datos en la propiedad enlazada, el control notifica a la base de datos y las solicitudes que se actualiza el campo de registro. La base de datos, a continuación, notifica el control del éxito o fracaso de la solicitud.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no se recomienda para nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que sustituyen a ActiveX, vea [controles ActiveX](activex-controls.md).

Este artículo trata sobre el lado del control de la tarea. Implementación de las interacciones de enlace de datos con la base de datos es responsabilidad del contenedor del control. Cómo administrar las interacciones de la base de datos en el contenedor queda fuera del ámbito de esta documentación. En el resto de este artículo, se explica cómo preparar el control de enlace de datos.

![Diagrama conceptual de los datos&#45;control enlazado a](../mfc/media/vc374v1.gif "diagrama Conceptual de los datos&#45;control enlazado a") <br/>
Diagrama conceptual de un Control enlazado a datos

La `COleControl` clase proporciona dos funciones miembro que hacen que un proceso sencillo para implementar de enlace de datos. La primera función, [BoundPropertyRequestEdit](../mfc/reference/colecontrol-class.md#boundpropertyrequestedit), se usa para solicitar permiso para cambiar el valor de propiedad. [BoundPropertyChanged](../mfc/reference/colecontrol-class.md#boundpropertychanged), la segunda función, se llama después de que el valor de propiedad ha cambiado correctamente.

En este artículo se tratan los siguientes temas:

- [Creación de una propiedad enlazable estándar](#vchowcreatingbindablestockproperty)

- [Creación de un método Get/Set enlazable](#vchowcreatingbindablegetsetmethod)

##  <a name="vchowcreatingbindablestockproperty"></a> Creación de una propiedad enlazable estándar

Es posible crear una propiedad enlazada a datos estándar, aunque es más probable que desee un [método get/set enlazable](#vchowcreatingbindablegetsetmethod).

> [!NOTE]
> Las propiedades estándar tienen la `bindable` y `requestedit` atributos de forma predeterminada.

#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>Para agregar una propiedad estándar enlazable mediante el Asistente para agregar propiedades

1. Comenzar un proyecto mediante el [Asistente para controles ActiveX de MFC](../mfc/reference/mfc-activex-control-wizard.md).

1. Haga clic en el nodo de interfaz para el control.

   Se abrirá el menú contextual.

1. En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar propiedad**.

1. Seleccione una de las entradas de la **nombre de la propiedad** lista desplegable. Por ejemplo, puede seleccionar **texto**.

   Dado que **texto** es una propiedad estándar, el **enlazable** y **requestedit** atributos ya están seleccionados.

1. Active las casillas siguientes desde el **atributos IDL** ficha: **displaybind** y **defaultbind** para agregar los atributos a la definición de propiedad del proyecto. Archivo IDL. Estos atributos que el control sea visible para el usuario y que la propiedad enlazable predeterminada de la propiedad estándar.

En este momento, el control puede mostrar datos de un origen de datos, pero el usuario no podrá actualizar los campos de datos. Si desea que el control también puedan actualizar los datos, cambie el `OnOcmCommand` [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) función a tener el aspecto siguiente:

[!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

Ahora puede compilar el proyecto, que se registrará el control. Al insertar el control en un cuadro de diálogo el **Datové** y **origen de datos** se habrán agregadas las propiedades y ahora puede seleccionar un origen de datos y un campo para mostrar en el control.

##  <a name="vchowcreatingbindablegetsetmethod"></a> Creación de un método Get/Set enlazable

Además de un enlace de datos Obtiene o establece el método, también puede crear un [propiedad estándar enlazable](#vchowcreatingbindablestockproperty).

> [!NOTE]
> Este procedimiento se supone que un control ActiveX: proyecto que cree subclases de un control de Windows.

#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>Para agregar un método get/set enlazable mediante el Asistente para agregar propiedades

1. Cargue el proyecto del control.

1. En el **configuración del Control** , seleccione una clase de ventana para el control para crear una subclase. Por ejemplo, es posible que desee para crear una subclase un control de edición.

1. Cargue el proyecto del control.

1. Haga clic en el nodo de interfaz para el control.

   Se abrirá el menú contextual.

1. En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar propiedad**.

1. Escriba el nombre de propiedad en el **nombre de la propiedad** cuadro. Use `MyProp` para este ejemplo.

1. Seleccione un tipo de datos en el **tipo de propiedad** cuadro de lista desplegable. Use **breve** en este ejemplo.

1. Para **Tipo de implementación**, haga clic en **Métodos Get/Set**.

1. Seleccione las casillas siguientes en la ficha atributos IDL: **enlazable**, **requestedit**, **displaybind**, y **defaultbind** para agregar los atributos a la definición de propiedad del proyecto. Archivo IDL. Estos atributos que el control sea visible para el usuario y que la propiedad enlazable predeterminada de la propiedad estándar.

1. Haga clic en **Finalizar**.

1. Modificar el cuerpo de la `SetMyProp` función para que contenga el código siguiente:

   [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]

1. El parámetro pasado a la `BoundPropertyChanged` y `BoundPropertyRequestEdit` funciones es el dispid de la propiedad, que es el parámetro pasado al atributo ID para la propiedad en el. Archivo IDL.

1. Modificar el [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) funcione de manera que contenga el código siguiente:

   [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

1. Modificar el `OnDraw` función para que contenga el código siguiente:

   [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]

1. En la sección pública del archivo de encabezado del archivo de encabezado de la clase del control, agregue las siguientes definiciones (constructores) para las variables de miembro:

   [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]

1. Hacer que la línea siguiente de la última línea en el `DoPropExchange` función:

   [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]

1. Modificar el `OnResetState` función para que contenga el código siguiente:

   [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]

1. Modificar el `GetMyProp` función para que contenga el código siguiente:

   [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]

Ahora puede compilar el proyecto, que se registrará el control. Al insertar el control en un cuadro de diálogo el **Datové** y **origen de datos** se habrán agregadas las propiedades y ahora puede seleccionar un origen de datos y un campo para mostrar en el control.

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

