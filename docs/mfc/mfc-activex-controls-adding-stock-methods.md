---
title: 'Controles ActiveX MFC: Agregar métodos estándar'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
ms.openlocfilehash: 42d8dfecd32b4aecd0daa4034497ec9abff6d11a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619932"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>Controles ActiveX MFC: Agregar métodos estándar

Un método estándar difiere de un método personalizado en que ya está implementado por la clase [COleControl](reference/colecontrol-class.md). Por ejemplo, `COleControl` contiene una función miembro predefinida que admite el método Refresh para el control. La entrada de mapa de envío para este método estándar es DISP_STOCKFUNC_REFRESH.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información sobre las tecnologías modernas que reemplazan a ActiveX, vea [controles ActiveX](activex-controls.md).

`COleControl`admite dos métodos estándar: hacer clic y actualizar. El usuario del control invoca la actualización para actualizar inmediatamente la apariencia del control; Al hacer clic se invoca para activar el evento click del control.

|Método|Entrada de mapa de envío|Comentario|
|------------|------------------------|-------------|
|`DoClick`|**DISP_STOCKPROP_DOCLICK ()**|Desencadena un evento de clic.|
|`Refresh`|**DISP_STOCKPROP_REFRESH ()**|Actualiza inmediatamente la apariencia del control.|

## <a name="adding-a-stock-method-using-the-add-method-wizard"></a><a name="_core_adding_a_stock_method_using_classwizard"></a>Agregar un método estándar mediante el Asistente para agregar métodos

Agregar un método estándar es sencillo mediante el [Asistente para agregar métodos](../ide/add-method-wizard.md). En el procedimiento siguiente se muestra cómo agregar el método Refresh a un control creado mediante el Asistente para controles ActiveX MFC.

#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>Para agregar el método de actualización de existencias mediante el Asistente para agregar métodos

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar método**.

   Se abrirá el Asistente para agregar métodos.

1. En el cuadro **nombre del método** , haga clic en **Actualizar**.

1. Haga clic en **Finalizar**

## <a name="add-method-wizard-changes-for-stock-methods"></a><a name="_core_classwizard_changes_for_stock_methods"></a>Cambios del Asistente para agregar métodos para los métodos estándar

Dado que el método de actualización de existencias es compatible con la clase base del control, el **Asistente para agregar métodos** no cambia la declaración de clase del control de ningún modo. Agrega una entrada para el método al mapa de envío del control y a su. Archivo IDL. La línea siguiente se agrega al mapa de envío del control, que se encuentra en su implementación (. CPP):

[!code-cpp[NVC_MFC_AxUI#16](codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]

Esto hace que el método Refresh esté disponible para los usuarios del control.

La línea siguiente se agrega al del control. Archivo IDL:

[!code-cpp[NVC_MFC_AxUI#17](codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]

Esta línea asigna al método Refresh un número de identificación específico.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)
