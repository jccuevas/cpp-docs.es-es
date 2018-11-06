---
title: 'Contenedores de controles ActiveX: Programar controles ActiveX en un contenedor de controles ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- Confirm Classes dialog box
- wrapper classes [MFC], ActiveX controls
- ActiveX control containers [MFC], wrapper classes
- ActiveX controls [MFC], accessing
- MFC ActiveX controls [MFC], accessing in containers
- header files [MFC], for ActiveX control wrapper class
- wrapper classes [MFC], using
- ActiveX controls [MFC], wrapper classes
ms.assetid: ef9b2480-92d6-4191-b16e-8055c4fd7b73
ms.openlocfilehash: c9a0c51d090b1c62309f27bf6587ea02e0fe1152
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636896"
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>Contenedores de controles ActiveX: Programar controles ActiveX en un contenedor de controles ActiveX

En este artículo se describe el proceso para tener acceso a la expuesta [métodos](../mfc/mfc-activex-controls-methods.md) y [propiedades](../mfc/mfc-activex-controls-properties.md) de controles ActiveX incrustados.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no se recomienda para nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que sustituyen a ActiveX, vea [controles ActiveX](activex-controls.md).

Básicamente, se siguen estos pasos:

1. [Inserte un control ActiveX en el proyecto de contenedor de ActiveX](../mfc/inserting-a-control-into-a-control-container-application.md) con la galería.

1. [Definir una variable miembro](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) (u otra forma de acceso) del mismo tipo como el ActiveX clase contenedora del control.

1. [Programar el control ActiveX](#_core_programming_the_activex_control) utilizando funciones de miembro de la clase contenedora predefinidas.

Para este análisis, suponga que ha creado un proyecto basado en el cuadro de diálogo (denominado contenedor) con compatibilidad con controles ActiveX. El control del ejemplo, Circ, se agregará al proyecto resultante.

Una vez que el control Circ se inserta en el proyecto (paso 1), inserte una instancia del control Circ en el cuadro de diálogo principal de la aplicación.

## <a name="procedures"></a>Procedimientos

#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>Para agregar el control Circ a la plantilla de cuadro de diálogo

1. Cargar el proyecto de contenedor de controles ActiveX. En este ejemplo, utilice el `Container` proyecto.

1. Haga clic en la pestaña de vista de recursos.

1. Abra el **diálogo** carpeta.

1. Haga doble clic en la plantilla de cuadro de diálogo principal. En este ejemplo, utilice **IDD_CONTAINER_DIALOG**.

1. Haga clic en el icono del control Circ en el cuadro de herramientas.

1. Haga clic en una zona en el cuadro de diálogo para insertar el control Circ.

1. Desde el **archivo** menú, elija **guardar todo** para guardar todas las modificaciones en la plantilla de cuadro de diálogo.

## <a name="modifications-to-the-project"></a>Modificaciones en el proyecto

Para habilitar la aplicación tenga acceso al control Circ, Visual C++ agrega automáticamente la clase contenedora (`CCirc`) archivo de implementación (. (CPP) para el proyecto de contenedor y el archivo de encabezado (. H) archivo de en el archivo de encabezado del cuadro de diálogo:

[!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]

##  <a name="_core_the_wrapper_class_header_28h29_file"></a> El archivo de encabezado (. H) archivo de

Para obtener y establecer las propiedades (e invocar métodos) para el control Circ, la `CCirc` clase contenedora proporciona una declaración de todas se exponen métodos y propiedades. En el ejemplo, estas declaraciones se encuentran en CIRC. H. El ejemplo siguiente es la parte de la clase `CCirc` que define las interfaces expuestas del control ActiveX:

[!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]

Estas funciones, a continuación, se pueden llamar desde otro de los procedimientos de la aplicación utilizando la sintaxis de C++ normal. Para obtener más información sobre el uso de esta función miembro establecida para tener acceso a los métodos y propiedades del control, vea la sección [programación del control ActiveX](#_core_programming_the_activex_control).

##  <a name="_core_member_variable_modifications_to_the_project"></a> Modificaciones de Variable de miembro para el proyecto

Una vez que el control ActiveX tiene se han agregado al proyecto e incrustado en un contenedor de cuadro de diálogo, puede tener acceso otras partes del proyecto. La manera más fácil para el control de acceso es [cree una variable miembro](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) de la clase de cuadro de diálogo, `CContainerDlg` (paso 2), que es del mismo tipo que la clase contenedora que agregó al proyecto de Visual c++. A continuación, puede usar la variable miembro para tener acceso al control incrustado en cualquier momento.

Cuando el **agregar variables miembro** cuadro de diálogo agrega la *m_circctl* miembro variable al proyecto, también agrega las siguientes líneas al archivo de encabezado (. (H) de la `CContainerDlg` clase:

[!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]

Además, una llamada a **DDX_Control** se agrega automáticamente a la `CContainerDlg`de implementación de `DoDataExchange`:

[!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]

##  <a name="_core_programming_the_activex_control"></a> Programación del Control ActiveX

En este punto, tiene Insertar control ActiveX en la plantilla de cuadro de diálogo y crear una variable miembro para él. Ahora puede usar la sintaxis común de C++ para tener acceso a las propiedades y métodos del control insertado.

Como se indica (en [el archivo de encabezado (. Archivo de H)](#_core_the_wrapper_class_header_28h29_file)), el archivo de encabezado (. (H) para el `CCirc` clase contenedora, en este caso CIRC. H, contiene una lista de funciones miembro que puede usar para obtener y establecer cualquier valor de propiedad expuesta. También están disponibles las funciones de miembro para los métodos expuestos.

Es un lugar común para modificar las propiedades del control en el `OnInitDialog` la función miembro de la clase de cuadro de diálogo principal. Esta función se llama justo antes de que el cuadro de diálogo aparece y se usa para inicializar su contenido, las de sus controles incluidas.

El siguiente ejemplo de código utiliza el *m_circctl* variable miembro para modificar las propiedades de título y CircleShape del control Circ incrustado:

[!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]

## <a name="see-also"></a>Vea también

[Contenedores de controles ActiveX](../mfc/activex-control-containers.md)

