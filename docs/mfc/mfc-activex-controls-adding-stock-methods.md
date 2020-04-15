---
title: 'Controles ActiveX MFC: Agregar métodos estándar'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
ms.openlocfilehash: ec59ccc0cbd48fc3114eb2dc0833dd3dd65691de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364669"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>Controles ActiveX MFC: Agregar métodos estándar

Un método stock difiere de un método personalizado en que ya está implementado por la clase [COleControl](../mfc/reference/colecontrol-class.md). Por ejemplo, `COleControl` contiene una función miembro predefinida que admite el método Refresh para el control. La entrada de mapa de envío para este método de stock es DISP_STOCKFUNC_REFRESH.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe utilizarse para el nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que reemplazan a ActiveX, vea [Controles ActiveX](activex-controls.md).

`COleControl`admite dos métodos de stock: DoClick y Refresh. El usuario del control invoca la actualización para actualizar inmediatamente la apariencia del control; DoClick se invoca para desencadenar el control Click eventos.

|Método|Entrada de mapa de despacho|Comentario|
|------------|------------------------|-------------|
|`DoClick`|**DISP_STOCKPROP_DOCLICK( )**|Activa un evento Click.|
|`Refresh`|**DISP_STOCKPROP_REFRESH( )**|Actualiza inmediatamente la apariencia del control.|

## <a name="adding-a-stock-method-using-the-add-method-wizard"></a><a name="_core_adding_a_stock_method_using_classwizard"></a>Adición de un método de stock mediante el Asistente para agregar métodos

Agregar un método de stock es sencillo mediante el [Asistente para agregar métodos](../ide/add-method-wizard.md). En el siguiente procedimiento se muestra cómo agregar el método Refresh a un control creado mediante el Asistente para controles ActiveX de MFC.

#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>Para agregar el método Refresh de stock mediante el Asistente para agregar métodos

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, haga clic en **Agregar método**.

   Se abrirá el Asistente para agregar métodos.

1. En el cuadro Nombre del **método** , haga clic en **Actualizar**.

1. Haga clic en **Finalizar**

## <a name="add-method-wizard-changes-for-stock-methods"></a><a name="_core_classwizard_changes_for_stock_methods"></a>Agregar cambios del Asistente para métodos de stock

Dado que el método Refresh de stock es compatible con la clase base del control, el **Asistente para agregar métodos** no cambia la declaración de clase del control de ninguna manera. Agrega una entrada para el método al mapa de distribución del control y a su archivo . IDL. La siguiente línea se agrega al mapa de distribución del control, ubicado en su implementación (. CPP) archivo:

[!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]

Esto hace que el Refresh método disponible para los usuarios del control.

La siguiente línea se agrega al control . Archivo IDL:

[!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]

Esta línea asigna al método Refresh un número de ID específico.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)
