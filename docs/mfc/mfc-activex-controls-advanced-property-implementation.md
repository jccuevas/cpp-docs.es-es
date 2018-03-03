---
title: "Controles ActiveX MFC: Implementación de propiedades de avanzadas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5ac8b2cb1a9c8de43ecfbd2f4712d19750bb143a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>Controles ActiveX MFC: Implementación de propiedades avanzada
Este artículo describe temas relacionados con la implementación de propiedades en un control ActiveX avanzadas:  
  
-   [Propiedades de solo lectura y de solo escritura](#_core_read2donly_and_write2donly_properties)  
  
-   [Devolver códigos de error de una propiedad](#_core_returning_error_codes_from_a_property)  
  
##  <a name="_core_read2donly_and_write2donly_properties"></a>Propiedades de solo lectura y de solo escritura  
 El Asistente para agregar propiedades proporciona un método rápido y sencillo para implementar propiedades de solo lectura o de solo escritura para el control.  
  
#### <a name="to-implement-a-read-only-or-write-only-property"></a>Para implementar una propiedad de solo lectura o de solo escritura  
  
1.  Cargue el proyecto del control.  
  
2.  En la vista de clases, expanda el nodo de biblioteca del control.  
  
3.  Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.  
  
4.  En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar propiedad**.  
  
     Se abrirá la [Asistente para agregar propiedades](../ide/names-add-property-wizard.md).  
  
5.  En el **nombre de la propiedad** , escriba el nombre de la propiedad.  
  
6.  Para **Tipo de implementación**, haga clic en **Métodos Get/Set**.  
  
7.  En el **tipo de propiedad** , seleccione el tipo adecuado para la propiedad.  
  
8.  Si desea que una propiedad de solo lectura, desactive el nombre de la función de conjunto. Si desea que una propiedad de solo escritura, desactive el nombre de la función Get.  
  
9. Haga clic en **Finalizar**.  
  
 Al hacerlo, el Asistente para agregar propiedades inserta la función `SetNotSupported` o `GetNotSupported` en la entrada de mapa de envíos en lugar del valor normal de un conjunto o Get (función).  
  
 Si desea cambiar una propiedad existente para que sea de solo lectura o de solo escritura, puede editar el mapa de envíos manualmente y quitar la función Set o Get innecesaria de la clase de control.  
  
 Si desea que una propiedad que se va a ser condicionalmente de solo lectura o de solo escritura (por ejemplo, cuando el control está funcionando en un modo determinado), puede proporcionar la función Set o Get, como es habitual y llamar a la `SetNotSupported` o `GetNotSupported` funcione en su caso. Por ejemplo:  
  
 [!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]  
  
 Este ejemplo de código llama `SetNotSupported` si la `m_bReadOnlyMode` miembro de datos es **TRUE**. Si **FALSE**, la propiedad se establece en el nuevo valor.  
  
##  <a name="_core_returning_error_codes_from_a_property"></a>Devolver códigos de Error de una propiedad  
 Para indicar que se ha producido un error al intentar obtener o establecer una propiedad, utilice la `COleControl::ThrowError` función, que toma un `SCODE` (código de estado) como parámetro. Puede usar predefinido `SCODE` o definir uno propio. Para obtener una lista de predefinidos `SCODE`s e instrucciones para definir personalizado `SCODE`s, consulte [controlar los errores en el ActiveX Control](../mfc/mfc-activex-controls-advanced-topics.md) en el artículo controles ActiveX: temas avanzados.  
  
 Funciones auxiliares que permiten la más común predefinida `SCODE`s, como [COleControl:: SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), y [COleControl:: SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).  
  
> [!NOTE]
>  `ThrowError`está pensado para usarse únicamente como un medio para devolver un error desde dentro Get de una propiedad o Set función o un método de automatización. Éstas son las únicas veces que el controlador de excepción apropiado estará presenten en la pila.  
  
 Para obtener más información sobre cómo informar de excepciones en otras áreas del código, consulte [COleControl:: FireError](../mfc/reference/colecontrol-class.md#fireerror) y la sección [controlar los errores en el ActiveX Control](../mfc/mfc-activex-controls-advanced-topics.md) en el artículo controles ActiveX: avanzadas Temas.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md)   
 [Controles ActiveX de MFC: propiedades](../mfc/mfc-activex-controls-properties.md)   
 [Controles ActiveX de MFC: métodos](../mfc/mfc-activex-controls-methods.md)   
 [COleControl (clase)](../mfc/reference/colecontrol-class.md)
