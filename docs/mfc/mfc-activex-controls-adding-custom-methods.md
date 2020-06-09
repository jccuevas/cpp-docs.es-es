---
title: 'Controles ActiveX MFC: Agregar métodos personalizados'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
ms.openlocfilehash: e32a1c372d89fc4ade414b20a0f77fa162807250
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626156"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>Controles ActiveX MFC: Agregar métodos personalizados

Los métodos personalizados se diferencian de los métodos estándar en que todavía no se han implementado `COleControl` . Debe proporcionar la implementación para cada método personalizado que agregue al control.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información sobre las tecnologías modernas que reemplazan a ActiveX, vea [controles ActiveX](activex-controls.md).

Un usuario de control ActiveX puede llamar a un método personalizado en cualquier momento para realizar acciones específicas del control. La entrada de mapa de envío para los métodos personalizados tiene el formato DISP_FUNCTION.

## <a name="adding-a-custom-method-with-the-add-method-wizard"></a><a name="_core_adding_a_custom_method_with_classwizard"></a>Agregar un método personalizado con el Asistente para agregar métodos

En el procedimiento siguiente se muestra cómo agregar el método personalizado PtInCircle al código esqueleto de un control ActiveX. PtInCircle determina si las coordenadas pasadas al control están dentro o fuera del círculo. Este mismo procedimiento también se puede utilizar para agregar otros métodos personalizados. Sustituya el nombre del método personalizado y sus parámetros por el nombre del método PtInCircle y los parámetros.

> [!NOTE]
> En este ejemplo se usa la `InCircle` función de los eventos de artículo. Para obtener más información sobre esta función, vea el artículo [controles ActiveX de MFC: agregar eventos personalizados a un control ActiveX](mfc-activex-controls-adding-custom-events.md).

#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>Para agregar el método personalizado PtInCircle mediante el Asistente para agregar métodos

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar método**.

   Se abrirá el Asistente para agregar métodos.

1. En el cuadro **nombre del método** , escriba *PtInCircle*.

1. En el cuadro **nombre interno** , escriba el nombre de la función interna del método o use el valor predeterminado (en este caso, *PtInCircle*).

1. En el cuadro **tipo de valor devuelto** , haga clic en **VARIANT_BOOL** para el tipo de valor devuelto del método.

1. Mediante los controles **tipo de parámetro** y nombre de **parámetro** , agregue un parámetro denominado *xCoord* (de tipo *OLE_XPOS_PIXELS*).

1. Mediante los controles **tipo de parámetro** y nombre de **parámetro** , agregue un parámetro denominado *yCoord* (de tipo *OLE_YPOS_PIXELS*).

1. Haga clic en **Finalizar**

## <a name="add-method-wizard-changes-for-custom-methods"></a><a name="_core_classwizard_changes_for_custom_methods"></a>Cambios del Asistente para agregar métodos para métodos personalizados

Cuando se agrega un método personalizado, el Asistente para agregar métodos realiza algunos cambios en el encabezado de clase de control (. H) y la implementación (. CPP). La línea siguiente se agrega a la declaración de mapa de envío del encabezado de clase de control (. H):

[!code-cpp[NVC_MFC_AxUI#18](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]

Este código declara un controlador de método de envío denominado `PtInCircle` . El usuario del control puede llamar a esta función mediante el nombre externo `PtInCircle` .

La línea siguiente se agrega al del control. Archivo IDL:

[!code-cpp[NVC_MFC_AxUI#19](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]

Esta línea asigna el `PtInCircle` método a un número de identificador concreto, la posición del método en la lista de métodos y propiedades del Asistente para agregar métodos. Dado que se usó el Asistente para agregar métodos para agregar el método personalizado, la entrada para este se agregó automáticamente al del proyecto. Archivo IDL.

Además, la siguiente línea, ubicada en la implementación (. CPP) de la clase del control, se agrega al mapa de envío del control:

[!code-cpp[NVC_MFC_AxUI#20](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]

La macro DISP_FUNCTION asigna el método `PtInCircle` a la función de controlador del control, `PtInCircle` , declara el tipo de valor devuelto que se va a **VARIANT_BOOL**y declara dos parámetros de tipo **VTS_XPOS_PIXELS** y **VTS_YPOSPIXELS** que se van a pasar a `PtInCircle` .

Por último, el Asistente para agregar métodos agrega la función de código auxiliar `CSampleCtrl::PtInCircle` a la parte inferior de la implementación del control (. CPP). Para `PtInCircle` que funcione como se indicó anteriormente, debe modificarse de la siguiente manera:

[!code-cpp[NVC_MFC_AxUI#21](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)<br/>
[Iconos de Vista de clases y Examinador de objetos](/visualstudio/ide/class-view-and-object-browser-icons)
