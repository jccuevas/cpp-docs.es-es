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
ms.openlocfilehash: 9620f4d47197147db4972c9f2024f6018a705902
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371184"
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>Contenedores de controles ActiveX: Programar controles ActiveX en un contenedor de controles ActiveX

En este artículo se describe el proceso para tener acceso a los [métodos expuestos](../mfc/mfc-activex-controls-methods.md) y [propiedades](../mfc/mfc-activex-controls-properties.md) de controles ActiveX incrustados.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe utilizarse para el nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que reemplazan a ActiveX, vea [Controles ActiveX](activex-controls.md).

Básicamente, seguirá estos pasos:

1. [Inserte un control ActiveX en el proyecto contenedor ActiveX](../mfc/inserting-a-control-into-a-control-container-application.md) mediante Galería.

1. [Defina una variable miembro](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) (u otra forma de acceso) del mismo tipo que la clase contenedora de control ActiveX.

1. [Programe el control ActiveX](#_core_programming_the_activex_control) mediante funciones miembro predefinidas de la clase contenedora.

Para esta discusión, supongamos que ha creado un proyecto basado en cuadros de diálogo (denominado Contenedor) con compatibilidad con controles ActiveX. El control de muestra Circ, Circ, se agregará al proyecto resultante.

Una vez insertado el control Circ en el proyecto (paso 1), inserte una instancia del control Circ en el cuadro de diálogo principal de la aplicación.

## <a name="procedures"></a>Procedimientos

#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>Para agregar el control Circ a la plantilla de cuadro de diálogo

1. Cargue el proyecto de contenedor de controles ActiveX. Para este ejemplo, `Container` utilice el proyecto.

1. Haga clic en la pestaña Vista de recursos.

1. Abra la carpeta **Diálogo.**

1. Haga doble clic en la plantilla del cuadro de diálogo principal. Para este ejemplo, utilice **IDD_CONTAINER_DIALOG**.

1. Haga clic en el icono de control Circ en el cuadro de herramientas.

1. Haga clic en un punto dentro del cuadro de diálogo para insertar el control Circ.

1. En el menú **Archivo,** elija **Guardar todo** para guardar todas las modificaciones en la plantilla del cuadro de diálogo.

## <a name="modifications-to-the-project"></a>Modificaciones al proyecto

Para permitir que la aplicación Container acceda al control Circ, Visual`CCirc`C++ agrega automáticamente el archivo de implementación de la clase contenedora ( ) (. CPP) al proyecto Container y al encabezado de clase contenedor (. H) al archivo de encabezado del cuadro de diálogo:

[!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]

## <a name="the-wrapper-class-header-h-file"></a><a name="_core_the_wrapper_class_header_28h29_file"></a>El encabezado de clase Wrapper (. H) Archivo

Para obtener y establecer propiedades (e invocar métodos) para el Circ control, la `CCirc` clase contenedora proporciona una declaración de todos los métodos y propiedades expuestas. En el ejemplo, estas declaraciones se encuentran en circunvalación. H. El ejemplo siguiente es `CCirc` la parte de la clase que define las interfaces expuestas del control ActiveX:

[!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]

A continuación, se puede llamar a estas funciones desde otros procedimientos de la aplicación mediante la sintaxis Normal de C++. Para obtener más información sobre el uso de esta función miembro establecida para tener acceso a los métodos y propiedades del control, vea la sección [Programación del control ActiveX](#_core_programming_the_activex_control).

## <a name="member-variable-modifications-to-the-project"></a><a name="_core_member_variable_modifications_to_the_project"></a>Modificaciones de variables miembro al proyecto

Una vez que el control ActiveX se ha agregado al proyecto e incrustado en un contenedor de cuadro de diálogo, se puede tener acceso a él por otras partes del proyecto. La forma más fácil de tener acceso al control es `CContainerDlg` crear una variable [miembro](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) de la clase de cuadro de diálogo, (paso 2), que es del mismo tipo que la clase contenedora agregada al proyecto por Visual C++. A continuación, puede usar la variable miembro para tener acceso al control incrustado en cualquier momento.

Cuando el cuadro de diálogo **Agregar variable miembro** agrega la variable miembro *m_circctl* al proyecto, también agrega las siguientes líneas al archivo de encabezado (. H) de `CContainerDlg` la clase:

[!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]

Además, una **DDX_Control** llamada a DDX_Control `CContainerDlg`se añade `DoDataExchange`automáticamente a la implementación de:

[!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]

## <a name="programming-the-activex-control"></a><a name="_core_programming_the_activex_control"></a>Programación del control ActiveX

En este punto, ha insertado el control ActiveX en la plantilla de cuadro de diálogo y ha creado una variable miembro para él. Ahora puede usar la sintaxis común de C++ para tener acceso a las propiedades y métodos del control incrustado.

Como se indica (en el encabezado de [clase Wrapper (. H) Archivo](#_core_the_wrapper_class_header_28h29_file)), el archivo de encabezado (. H) para `CCirc` la clase contenedora, en este caso CIRC. H, contiene una lista de funciones miembro que puede usar para obtener y establecer cualquier valor de propiedad expuesto. Las funciones miembro para los métodos expuestos también están disponibles.

Un lugar común para modificar las propiedades `OnInitDialog` del control está en la función miembro de la clase de cuadro de diálogo principal. Esta función se llama justo antes de que aparezca el cuadro de diálogo y se utiliza para inicializar su contenido, incluidos cualquiera de sus controles.

En el ejemplo de código siguiente se utiliza la *m_circctl* variable miembro para modificar el Caption y CircleShape propiedades del incrustado Circ control:

[!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]

## <a name="see-also"></a>Consulte también

[Contenedores de controles ActiveX](../mfc/activex-control-containers.md)
