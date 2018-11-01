---
title: Asistente para agregar métodos | Microsoft Docs
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
ms.openlocfilehash: 45c3b0ca9a3e6c88e4ae40a5eb52aeb3223d2860
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397309"
---
# <a name="add-method-wizard"></a>Asistente para agregar métodos

Use este asistente para agregar un método a una interfaz. Según el tipo de proyecto o de interfaz a la que se va a agregar un método, el asistente mostrará otras opciones.

## <a name="names"></a>Nombres

- **Tipo de valor devuelto**

   El tipo de datos devuelto por el método. Se recomienda `HRESULT` para todos los tipos de interfaz, ya que proporciona una manera estándar de devolver errores.

   |Tipo de interfaz|Descripción|
   |--------------------|-----------------|
   |Interfaz dual|`HRESULT`. No se puede cambiar.|
   |Interfaz personalizada|`HRESULT`. No se puede cambiar.|
   |Interfaz personalizada local|Proporcione un tipo de valor devuelto propio o seleccione uno de la lista.|
   |Interfaz dispinterface|Proporcione un tipo de valor devuelto propio o seleccione uno de la lista.|
   |Interfaz dispinterface de control ActiveX MFC|Si implementa un método de reserva, el tipo de valor devuelto se establece en el valor adecuado y no se podrá cambiar. Si selecciona un método en la lista **Nombre del método** y hace clic en **Personalizado** en **Seleccionar tipo de método**, seleccione un tipo de valor devuelto de la lista.|

- **Nombre del método**

   Establece el nombre del método.

   |Tipo de interfaz|Descripción|
   |--------------------|-----------------|
   |Interfaz dual de ATL, interfaz personalizada e interfaz personalizada local|Proporcione un nombre de método propio.|
   |Interfaz dispinterface de MFC|Proporcione un nombre de método propio o seleccione un nombre de método sugerido de la lista. Si selecciona un nombre de la lista, el valor apropiado aparecerá en el cuadro **Tipo de valor devuelto** y no se podrá cambiar.|
   |Interfaz dispinterface de control ActiveX MFC|Proporcione un método de reserva propio o seleccione [DoClick](../mfc/reference/colecontrol-class.md#doclick) o [Refresh](../mfc/reference/colecontrol-class.md#refresh). Vea [Controles ActiveX MFC: agregar métodos de reserva](../mfc/mfc-activex-controls-adding-stock-methods.md) para obtener más información.|

- **Tipo de método**

   Solo disponible para controles ActiveX MFC. Si proporciona un nombre de método en el cuadro **Nombre del método**, en lugar de seleccionar un método de la lista, este cuadro no está disponible.

   Si selecciona uno de los métodos de la lista **Nombre del método**, seleccione la implementación estándar o una implementación personalizada.

   |Tipo de método|Descripción|
   |-----------------|-----------------|
   |**Estándar**|El valor predeterminado. Inserta la implementación estándar del método que seleccione en la lista **Nombre del método**. **Tipo de valor devuelto** no se podrá cambiar si selecciona **Estándar**.|
   |**Custom**|Inserta una implementación de código auxiliar del método que seleccione en la lista **Nombre del método**. Para los tipos de métodos personalizados, puede proporcionar un tipo de valor devuelto propio, o bien puede seleccionar uno en la lista **Tipo de valor devuelto**.|

- **Nombre interno**

   Disponible únicamente para los métodos personalizados agregados a una interfaz dispinterface de MFC. Establece el nombre que se usa en el mapa de envíos, el archivo de encabezado (.h) y el archivo de implementación (.cpp). De forma predeterminada, este nombre es el mismo que **Nombre del método**. Puede cambiar el nombre del método si está trabajando con una interfaz dispinterface de MFC o si va a agregar un método personalizado a una interfaz dispinterface de control ActiveX MFC.

   |Tipo de interfaz|Descripción|
   |--------------------|-----------------|
   |Interfaz dual de ATL, interfaz personalizada e interfaz personalizada local|No disponible|
   |Interfaz dispinterface de MFC|De forma predeterminada, se establece en el nombre del método. El nombre interno se puede modificar.|
   |Interfaz dispinterface de control ActiveX MFC|Solo se puede establecer el nombre interno para los métodos personalizados. En los métodos de reserva no se usa un nombre interno.|

- **Atributos de parámetro**

   Establece los atributos adicionales para los parámetros especificados en **Nombre del parámetro**.

   |Atributo de parámetro|Descripción|Combinaciones permitidas|
   |-------------------------|-----------------|--------------------------|
   |**In**|Indica que el parámetro se pasa del procedimiento que realiza la llamada al procedimiento que se llama.|Solo **in**<br /><br /> **in** y **out**|
   |**Out**|Indica que el parámetro de puntero se devuelve desde el procedimiento llamado al procedimiento que realiza la llamada (desde el servidor al cliente).|Solo **out**<br /><br /> **in** y **out**<br /><br /> **out** y **retval**|
   |**Retval**|Indica que el parámetro recibe el valor devuelto del miembro.|**retval** y out|

- **Tipo de parámetro**

   Establece el tipo de datos del parámetro. Seleccione el tipo de la lista.

- **Nombre del parámetro**

   Establece el nombre de un parámetro que se va a pasar a través del método. Después de escribir el nombre, debe hacer clic en **Agregar** para agregarlo a la lista de parámetros que se van a pasar a través del método. Si no proporciona un nombre de parámetro, el asistente ignora los atributos de parámetro (solo en ATL) o las selecciones de **Tipo de parámetro**.

   Después de hacer clic en **Agregar**, el nombre del parámetro aparece en la **Lista de parámetros**.

   > [!Note]
   > Si proporciona un nombre de parámetro y después hace clic en **Finalizar** antes de hacer clic en **Agregar**, el parámetro no se agrega al método. Debe buscar el método e insertar el parámetro de forma manual.

- **Add**

   Agrega el parámetro especificado en **Nombre del parámetro** y sus atributos de tipo y parámetro a **Lista de parámetros**. Debe hacer clic en **Agregar** para agregar un parámetro a la lista.

- **Remove**

   Quita de la lista el parámetro seleccionado en **Lista de parámetros**.

- **Lista de parámetros**

   Muestra todos los parámetros y sus modificadores y tipos agregados actualmente al método. A medida que se agregan los parámetros, el asistente actualiza la **Lista de parámetros** para mostrar cada uno con su modificador y tipo.

## <a name="see-also"></a>Vea también

[Agregar un método](../ide/adding-a-method-visual-cpp.md)<br/>
[Atributos IDL, Asistente para agregar métodos](../ide/idl-attributes-add-method-wizard.md)