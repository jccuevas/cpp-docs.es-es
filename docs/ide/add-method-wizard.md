---
title: Asistente para agregar métodos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.method.overview
dev_langs:
- C++
helpviewer_keywords:
- Add Method Wizard [C++]
- methods [C++], adding using wizards
ms.assetid: b9a71b0e-9ecf-40fa-9f86-4200cb23d671
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cc2ebd18640f0ab778cb45252691e63206861d53
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="add-method-wizard"></a>Asistente para agregar métodos
Use este asistente para agregar un método a una interfaz. Según el tipo de proyecto o tipo de interfaz a la que va a agregar un método, el asistente mostrará opciones diferentes.  
  
## <a name="names"></a>Nombres  
 **Tipo de valor devuelto**  
 El tipo de datos devuelto por el método. `HRESULT` se recomienda para todos los tipos de interfaz, ya que proporciona una manera estándar de devolver errores.  
  
|Tipo de interfaz|Descripción|  
|--------------------|-----------------|  
|Interfaz dual|`HRESULT`. Puede cambiar.|  
|Interfaz personalizada|`HRESULT`. Puede cambiar.|  
|Interfaz personalizada local|Proporcionar su propio tipo de valor devuelto o seleccione en la lista.|  
|Dispinterface|Proporcionar su propio tipo de valor devuelto o seleccione en la lista.|  
|Dispinterface de controles ActiveX en MFC|Si implementa un método estándar, el tipo de valor devuelto se establece en el valor adecuado y se podrá cambiar. Si selecciona un método de la **nombre del método** lista y haga clic en **personalizado** en **Seleccionar tipo de método**, seleccione un tipo de valor devuelto de la lista.|  
  
 **Nombre del método**  
 Establece el nombre del método.  
  
|Tipo de interfaz|Descripción|  
|--------------------|-----------------|  
|Interfaz dual ATL, interfaz personalizada e interfaz personalizada local|Especifique su propio nombre de método.|  
|Dispinterface MFC|Especifique su propio nombre de método o seleccione un nombre de método sugerido de la lista. Si selecciona un nombre de la lista, el valor apropiado aparecerá en el **tipo de valor devuelto** cuadro y no es invariable.|  
|Dispinterface de controles ActiveX en MFC|Proporcionar su propio o seleccione cualquiera de los métodos estándar [DoClick](../mfc/reference/colecontrol-class.md#doclick) y [actualizar](../mfc/reference/colecontrol-class.md#refresh). Vea [controles ActiveX de MFC: agregar métodos estándar](../mfc/mfc-activex-controls-adding-stock-methods.md) para obtener más información.|  
  
 **Tipo de método**  
 Disponible únicamente para controles ActiveX en MFC. Si proporciona un nombre de método en el **nombre del método** cuadro, en lugar de seleccionar un método de la lista, este cuadro no está disponible.  
  
 Si selecciona uno de los métodos en el **nombre del método** , seleccione la implementación estándar o una implementación personalizada.  
  
|Tipo de método|Descripción|  
|-----------------|-----------------|  
|**Existencias**|El valor predeterminado. Inserta la implementación estándar del método que seleccione en la **nombre del método** lista. **Tipo de valor devuelto** si selecciona, no podrá cambiar **existencias**.|  
|**Custom**|Inserta una implementación de código auxiliar del método seleccionado en el **nombre del método** lista. Para tipos de métodos personalizados, puede proporcionar su propio tipo de valor devuelto, o puede seleccionar uno de los **tipo de valor devuelto** lista.|  
  
 **Nombre interno**  
 Disponible únicamente para métodos personalizados agregados a una interfaz dispinterface MFC. Establece el nombre utilizado en el mapa de envíos, el archivo de encabezado (. h) y el archivo de implementación (.cpp). De forma predeterminada, este nombre es el mismo que **nombre del método**. Puede cambiar el nombre del método si está trabajando con una interfaz dispinterface de MFC o si va a agregar un método personalizado a una interfaz dispinterface de control de ActiveX de MFC.  
  
|Tipo de interfaz|Descripción|  
|--------------------|-----------------|  
|Interfaz dual ATL, interfaz personalizada e interfaz personalizada local|No disponible|  
|Dispinterface MFC|De forma predeterminada, establezca el nombre del método. Puede editar el nombre interno.|  
|Dispinterface de controles ActiveX en MFC|Puede establecer el nombre interno solo para métodos personalizados. Métodos estándar no utilizan un nombre interno.|  
  
 **Atributos de parámetro**  
 Establece los atributos adicionales para los parámetros especificados en **nombre de parámetro**.  
  
|Atributo de parámetro|Descripción|Combinaciones permitidas|  
|-------------------------|-----------------|--------------------------|  
|**In**|Indica que el parámetro se pasa desde el procedimiento que realiza la llamada al procedimiento llamado.|**en** sólo<br /><br /> **en** y **out**|  
|**Out**|Indica que el parámetro de puntero se devuelve desde el procedimiento llamado al procedimiento que realiza la llamada (desde el servidor al cliente).|**out** solo<br /><br /> **en** y **out**<br /><br /> **out** y **retval**|  
|**retval**|Indica que el parámetro recibe el valor devuelto del miembro.|**retval** y out|  
  
 **Tipo de parámetro**  
 Establece el tipo de datos del parámetro. Seleccione el tipo de la lista.  
  
 **Nombre de parámetro**  
 Establece el nombre de un parámetro que se pasa a través del método. Después de escribir el nombre, debe hacer clic en **agregar** para agregarlo a la lista de parámetros que se pasen a través de su método. Si no proporciona un nombre de parámetro, el asistente pasa por alto los atributos de parámetro (sólo ATL) o **tipo de parámetro** selecciones.  
  
 Una vez que pulses **agregar**, el nombre del parámetro aparece en **lista de parámetros**.  
  
 **Tenga en cuenta** si especifica un nombre de parámetro y, a continuación, haga clic en **finalizar** antes de hacer clic **agregar**, el parámetro no se agrega al método. Debe buscar el método e insertar el parámetro manualmente.  
  
 **Add**  
 Agrega el parámetro especificado en **nombre de parámetro**y sus atributos de tipo y un parámetro para **lista de parámetros**. Debe hacer clic en **agregar** para agregar un parámetro a la lista.  
  
 **Remove**  
 Quita el parámetro seleccionado en **lista de parámetros** en la lista.  
  
 **Lista de parámetros**  
 Muestra todos los parámetros y sus modificadores y tipos agregados actualmente al método. A medida que agregue parámetros, el asistente actualiza **lista de parámetros** para mostrar cada parámetro con su modificador y tipo.  
  
## <a name="see-also"></a>Vea también  
 [Agregar un método](../ide/adding-a-method-visual-cpp.md)   
 [Atributos IDL, Asistente para agregar métodos](../ide/idl-attributes-add-method-wizard.md)