---
title: 'Controles ActiveX MFC: Agregar métodos personalizados'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
ms.openlocfilehash: 88d486248eab5d980463764db34bf40b05b830dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364711"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>Controles ActiveX MFC: Agregar métodos personalizados

Los métodos personalizados difieren de los `COleControl`métodos de stock en que no están ya implementados por . Debe proporcionar la implementación para cada método personalizado que agregue al control.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe utilizarse para el nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que reemplazan a ActiveX, vea [Controles ActiveX](activex-controls.md).

Un usuario de control ActiveX puede llamar a un método personalizado en cualquier momento para realizar acciones específicas del control. La entrada de mapa de envío para métodos personalizados tiene el formato DISP_FUNCTION.

## <a name="adding-a-custom-method-with-the-add-method-wizard"></a><a name="_core_adding_a_custom_method_with_classwizard"></a>Agregar un método personalizado con el Asistente para agregar métodos

En el siguiente procedimiento se muestra cómo agregar el método personalizado PtInCircle al código de esqueleto de un control ActiveX. PtInCircle determina si las coordenadas pasadas al control están dentro o fuera del círculo. Este mismo procedimiento también se puede utilizar para agregar otros métodos personalizados. Sustituya el nombre del método personalizado y sus parámetros por el nombre y los parámetros del método PtInCircle.

> [!NOTE]
> En este `InCircle` ejemplo se utiliza la función del artículo Eventos. Para obtener más información sobre esta función, vea el artículo [Controles ActiveX de MFC: Agregar eventos personalizados a un control ActiveX](../mfc/mfc-activex-controls-adding-custom-events.md).

#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>Para agregar el método personalizado PtInCircle mediante el Asistente para agregar métodos

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, haga clic en **Agregar método**.

   Se abrirá el Asistente para agregar métodos.

1. En el cuadro Nombre del **método** , escriba *PtInCircle*.

1. En el cuadro **Nombre interno,** escriba el nombre de la función interna del método o utilice el valor predeterminado (en este caso, *PtInCircle*).

1. En el cuadro Tipo de **valor devuelto,** haga clic en **VARIANT_BOOL** para el tipo de valor devuelto del método.

1. Mediante los controles Tipo de **parámetro** y Nombre de **parámetro,** agregue un parámetro denominado *xCoord* (tipo *OLE_XPOS_PIXELS*).

1. Mediante los controles Tipo de **parámetro** y Nombre de **parámetro,** agregue un parámetro denominado *yCoord* (tipo *OLE_YPOS_PIXELS*).

1. Haga clic en **Finalizar**

## <a name="add-method-wizard-changes-for-custom-methods"></a><a name="_core_classwizard_changes_for_custom_methods"></a>Agregar cambios del Asistente para métodos personalizados

Al agregar un método personalizado, el Asistente para agregar métodos realiza algunos cambios en el encabezado de la clase de control (. H) e implementación (. CPP). La línea siguiente se agrega a la declaración de mapa de distribución en el encabezado de clase de control (. H) archivo:

[!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]

Este código declara un controlador `PtInCircle`de método de envío denominado . El usuario del control puede llamar a `PtInCircle`esta función utilizando el nombre externo.

La siguiente línea se agrega al control . Archivo IDL:

[!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]

Esta línea asigna `PtInCircle` al método un número de identificador específico, la posición del método en la lista de propiedades y métodos del Asistente para agregar métodos. Dado que se usó el Asistente para agregar métodos para agregar el método personalizado, la entrada para él se agregó automáticamente al proyecto. IDL.

Además, la siguiente línea, ubicada en la implementación (. CPP) de la clase de control, se agrega al mapa de distribución del control:

[!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]

La DISP_FUNCTION macro `PtInCircle` asigna el método a `PtInCircle`la función de controlador del control, , declara que el tipo `PtInCircle`de valor devuelto es **VARIANT_BOOL**y declara dos parámetros de tipo **VTS_XPOS_PIXELS** y **VTS_YPOSPIXELS** que se va a pasar a .

Por último, el Asistente para agregar `CSampleCtrl::PtInCircle` métodos agrega la función de código auxiliar a la parte inferior de la implementación del control (. CPP). Para `PtInCircle` que funcione como se ha indicado anteriormente, debe modificarse de la siguiente manera:

[!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Iconos de la vista de clases y del explorador de objetos](/visualstudio/ide/class-view-and-object-browser-icons)
