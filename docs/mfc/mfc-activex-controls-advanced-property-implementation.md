---
title: "Controles ActiveX MFC: Implementaci&#243;n de propiedades avanzada | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX en MFC, códigos de error"
  - "controles ActiveX en MFC, propiedades"
  - "propiedades [MFC], controles ActiveX"
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Controles ActiveX MFC: Implementaci&#243;n de propiedades avanzada
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe los temas relacionados con implementar propiedades avanzadas en un control ActiveX:  
  
-   [Readonly y propiedades de solo escritura](#_core_read2donly_and_write2donly_properties)  
  
-   [Devolver códigos de error de una propiedad](#_core_returning_error_codes_from_a_property)  
  
##  <a name="_core_read2donly_and_write2donly_properties"></a> Readonly y propiedades de solo escritura  
 El asistente para agregar proporciona un método rápido y fácil implementar readonly o propiedades de solo escritura para el control.  
  
#### Para implementar un solo lectura o una propiedad de sólo escritura  
  
1.  Cargue el proyecto de control.  
  
2.  En la vista de clases, expanda el nodo de biblioteca de controles.  
  
3.  Haga clic con el botón secundario en el nodo de la interfaz del control \(el segundo nodo el nodo de biblioteca\) para abrir el menú contextual.  
  
4.  En el menú contextual, haga clic en **Add** y haga clic en **Agregar propiedad**.  
  
     Esto abre [Asistente para agregar propiedades](../ide/names-add-property-wizard.md).  
  
5.  En el cuadro de **Nombre de propiedad** , escriba el nombre de la propiedad.  
  
6.  Para **Tipo de implementación**, haga clic en **Get\/Set Methods**.  
  
7.  En el cuadro de **Tipo de propiedad** , seleccione el tipo adecuado para la propiedad.  
  
8.  Si desea que una propiedad de sólo lectura, borre el nombre de función determinado.  Si desea que una propiedad de sólo escritura, borre el nombre de función get.  
  
9. Haga clic en **Finalizar**.  
  
 Al hacer esto, el asistente para agregar inserta la función `SetNotSupported` o `GetNotSupported` sobre cómo asigna entrada en lugar de un conjunto normal o función get.  
  
 Si desea cambiar una propiedad existente para que sea de sólo lectura o de sólo escritura, puede modificar el envío asignado manualmente y quitar el conjunto innecesario u obtener la función de la clase del control.  
  
 Si desea una propiedad sea condicional de sólo lectura o de sólo escritura \(por ejemplo, sólo cuando el control está trabajando en un modo determinado\), puede proporcionar el conjunto o obtener la función, como normal, y llama a la función de `SetNotSupported` o de `GetNotSupported` en su caso.  Por ejemplo:  
  
 [!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/CPP/mfc-activex-controls-advanced-property-implementation_1.cpp)]  
  
 Este ejemplo de código llama a `SetNotSupported` si el miembro de datos de `m_bReadOnlyMode` es **VERDADERO**.  Si **FALSE**, la propiedad se establece en el nuevo valor.  
  
##  <a name="_core_returning_error_codes_from_a_property"></a> Devuelve los códigos de error De una propiedad  
 Para indicar que se ha producido un error al intentar obtener o establecer una propiedad, utilice la función de `COleControl::ThrowError` , que toma `SCODE` \(código de estado\) como parámetro.  Puede utilizar `SCODE` predefinido o definir uno de sea propietario.  Para obtener una lista de s predefinida de `SCODE`e instrucciones para definir s personalizada de `SCODE`, vea [Controlar errores en el control ActiveX se](../mfc/mfc-activex-controls-advanced-topics.md) en los controles ActiveX de caso: Temas avanzados.  
  
 Las funciones auxiliares existen para la mayoría de s predefinida común de `SCODE`, como [COleControl::SetNotSupported](../Topic/COleControl::SetNotSupported.md), [COleControl::GetNotSupported](../Topic/COleControl::GetNotSupported.md), y [COleControl::SetNotPermitted](../Topic/COleControl::SetNotPermitted.md).  
  
> [!NOTE]
>  `ThrowError` está diseñado para usarse sólo como medio para devolver un error dentro de una propiedad obtiene o establece la función o método de automatización.  Estos son los únicos veces que el controlador de excepciones adecuado aparecerá en la pila.  
  
 Para obtener más información sobre excepciones de informe en otras áreas de código, vea [COleControl::FireError](../Topic/COleControl::FireError.md) y la sección [Controlar errores en el control ActiveX se](../mfc/mfc-activex-controls-advanced-topics.md) en Controles ActiveX de caso: Temas avanzados.  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Controles ActiveX MFC: Propiedades](../mfc/mfc-activex-controls-properties.md)   
 [Controles ActiveX MFC: Métodos](../mfc/mfc-activex-controls-methods.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)