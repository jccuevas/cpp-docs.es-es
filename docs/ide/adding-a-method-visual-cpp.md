---
title: Agregar un método
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.method.overview
- vc.codewiz.method.idlattrib
helpviewer_keywords:
- add method wizard [C++]
- methods [C++], adding
- methods [C++], adding using wizards
- IDL attributes, add method wizard
ms.assetid: 4ba4e45f-fa38-4d5e-af44-cbec0a7ab558
ms.openlocfilehash: b0c8ddabc4ed08fd217545bad269f0b2e48dd49e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509542"
---
# <a name="add-a-method"></a>Agregar un método

Se puede usar el [Asistente para agregar métodos](#add-method-wizard) para agregar un método a una interfaz del proyecto. Si el proyecto contiene una clase asociada a la interfaz, el asistente también modifica la clase.

**Para agregar un método al objeto:**

1. En la **Vista de clases**, expanda el nodo del proyecto para mostrar la interfaz a la que quiere agregar el método.

   > [!NOTE]
   > También puede agregar métodos a interfaces dispinterface que, a menos que el proyecto tenga atributos, se encuentran bajo el nodo de biblioteca.

1. Haga clic con el botón derecho en el nombre de la interfaz.

1. En el menú contextual, elija **Agregar** y luego **Agregar método**.

1. En el Asistente para agregar métodos, proporcione la información para crear el método.

1. Especifique cualquier configuración de lenguaje de definición de interfaz para este método en la página [Atributos IDL](#idl-attributes-add-method-wizard) del asistente.

1. Seleccione **Finalizar** para agregar el método.

## <a name="in-this-section"></a>En esta sección

- [Asistente para agregar métodos](#add-method-wizard)
- [Atributos IDL, Asistente para agregar métodos](#idl-attributes-add-method-wizard)

## <a name="add-method-wizard"></a>Asistente para agregar métodos

Use este asistente para agregar un método a una interfaz. Según el tipo de proyecto o de interfaz al que se vaya a agregar un método, el asistente muestra diferentes opciones.

### <a name="names"></a>Nombres

- **Tipo de valor devuelto**

  El tipo de datos devuelto por el método. Se recomienda `HRESULT` para todos los tipos de interfaz, ya que proporciona una manera estándar de devolver errores.

  |Tipo de interfaz|DESCRIPCIÓN|
  |--------------------|-----------------|
  |Interfaz dual|`HRESULT`. No se puede cambiar.|
  |Interfaz personalizada|`HRESULT`. No se puede cambiar.|
  |Interfaz personalizada local|Proporcione un tipo de valor devuelto propio o seleccione uno de la lista.|
  |Interfaz dispinterface|Proporcione un tipo de valor devuelto propio o seleccione uno de la lista.|
  |Interfaz dispinterface de control ActiveX MFC|Si implementa un método de reserva, el tipo de valor devuelto se establece en el valor adecuado y no se podrá cambiar. Si selecciona un método en la lista **Nombre de método** y luego selecciona **Personalizado** en **Seleccionar tipo de método**, seleccione un tipo de valor devuelto de la lista.|

- **Nombre del método**

  Establece el nombre del método.

  |Tipo de interfaz|DESCRIPCIÓN|
  |--------------------|-----------------|
  |Interfaz dual de ATL, interfaz personalizada e interfaz personalizada local|Proporcione un nombre de método propio.|
  |Interfaz dispinterface de MFC|Proporcione un nombre de método propio o seleccione un nombre de método sugerido de la lista. Si selecciona un nombre de la lista, aparece el valor correcto en el cuadro **Tipo de valor devuelto** y no se puede cambiar.|
  |Interfaz dispinterface de control ActiveX MFC|Proporcione un método de reserva propio o seleccione [DoClick](../mfc/reference/colecontrol-class.md#doclick) o [Refresh](../mfc/reference/colecontrol-class.md#refresh). Para obtener más información, vea [Controles ActiveX MFC: Adición de métodos estándar](../mfc/mfc-activex-controls-adding-stock-methods.md).|

- **Tipo de método**

  Solo disponible para controles ActiveX MFC. Si proporciona un nombre de método en el cuadro **Nombre del método**, en lugar de seleccionar un método de la lista, este cuadro no está disponible.

  Si selecciona uno de los métodos de la lista **Nombre del método**, seleccione la implementación estándar o una implementación personalizada.

  |Tipo de método|DESCRIPCIÓN|
  |-----------------|-----------------|
  |**Estándar**|El valor predeterminado. Inserta la implementación estándar del método que seleccione en la lista **Nombre del método**. **Tipo de valor devuelto** no se podrá cambiar si selecciona **Estándar**.|
  |**Custom**|Inserta una implementación de código auxiliar del método que seleccione en la lista **Nombre del método**. Para los tipos de métodos personalizados, puede proporcionar un tipo de valor devuelto propio, o bien puede seleccionar uno en la lista **Tipo de valor devuelto**.|

- **Nombre interno**

  Disponible únicamente para los métodos personalizados agregados a una interfaz dispinterface de MFC. Establece el nombre que se usa en el mapa de envíos, el archivo de encabezado (.h) y el archivo de implementación (.cpp). De forma predeterminada, este nombre es el mismo que **Nombre del método**. Puede cambiar el nombre del método si está trabajando con una interfaz dispinterface de MFC o si va a agregar un método personalizado a una interfaz dispinterface de control ActiveX MFC.

  |Tipo de interfaz|DESCRIPCIÓN|
  |--------------------|-----------------|
  |Interfaz dual de ATL, interfaz personalizada e interfaz personalizada local|No está disponible.|
  |Interfaz dispinterface de MFC|De forma predeterminada, se establece en el nombre del método. El nombre interno se puede modificar.|
  |Interfaz dispinterface de control ActiveX MFC|Solo se puede establecer el nombre interno para los métodos personalizados. En los métodos estándar no se usa un nombre interno.|

- **Atributos de parámetro**

  Establece atributos adicionales para el parámetro especificado en **Nombre del parámetro**.

  |Atributo de parámetro|DESCRIPCIÓN|Combinaciones permitidas|
  |-------------------------|-----------------|--------------------------|
  |**In**|Indica que el parámetro se pasa del procedimiento que realiza la llamada al procedimiento que se llama.|Solo `in`<br /><br /> `in` y `out`|
  |**Out**|Indica que el parámetro de puntero se devuelve desde el procedimiento llamado al procedimiento que realiza la llamada (desde el servidor al cliente).|Solo `out`<br /><br /> `in` y `out`<br /><br /> `out` y `retval`|
  |**Retval**|Indica que el parámetro recibe el valor devuelto del miembro.|`retval` y `out`|

- **Tipo de parámetro**

  Establece el tipo de datos del parámetro. Seleccione el tipo de la lista.

- **Nombre del parámetro**

  Establece el nombre de un parámetro que se va a pasar a través del método. Después de escribir el nombre, seleccione **Agregar** para agregarlo a la lista de parámetros que se van a pasar a través del método. Si no proporciona un nombre de parámetro, el asistente pasa por alto los atributos de parámetro (solo en ATL) o las selecciones de **Tipo de parámetro**.

  Después de seleccionar **Agregar**, el nombre del parámetro aparece en **Lista de parámetros**.

  > [!NOTE]
  > Si proporciona un nombre de parámetro y después selecciona **Finalizar** antes de seleccionar **Agregar**, el parámetro no se agrega al método. Debe buscar el método e insertar el parámetro de forma manual.

- **Add**

  Agrega el parámetro especificado en **Nombre del parámetro** y sus atributos de tipo y parámetro a **Lista de parámetros**. Seleccione **Agregar** para agregar un parámetro a la lista.

- **Remove**

  Quita de la lista el parámetro seleccionado en **Lista de parámetros**.

- **Lista de parámetros**

  Muestra todos los parámetros y sus modificadores y tipos agregados actualmente al método. A medida que se agregan los parámetros, el asistente actualiza la **Lista de parámetros** para mostrar cada uno con su modificador y tipo.

## <a name="idl-attributes-add-method-wizard"></a>Atributos IDL, Asistente para agregar métodos

Use esta página del Asistente para agregar métodos para especificar la configuración de lenguaje de definición de interfaz (IDL) para el método.

- `id`

  Establece el id. numérico que identifica el método. Para obtener más información, vea [id](/windows/win32/Midl/id) en la *Referencia de MIDL*.

  Este cuadro no está disponible para las interfaces personalizadas ni para las interfaces dispinterface de MFC.

- `call_as`

  Especifica el nombre de un método remoto al que se puede asignar este método local. Para obtener más información, vea [call_as](/windows/win32/Midl/call-as) en la *Referencia de MIDL*.

  No está disponible para interfaces dispinterface de MFC.

- `helpcontext`

  Especifica un id. contextual que permite al usuario ver información sobre este método en el archivo de ayuda. Para obtener más información, vea [helpcontext](/windows/win32/Midl/helpcontext) en la *Referencia de MIDL*.

  No está disponible para interfaces dispinterface de MFC.

- `helpstring`

  Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica. De forma predeterminada, se establece en "method *Method name*". Para obtener más información, vea [helpstring](/windows/win32/Midl/helpstring) en la *Referencia de MIDL*.

  No está disponible para interfaces dispinterface de MFC.

- **Atributos adicionales**

  No está disponible para interfaces dispinterface de MFC.

  |Atributo|DESCRIPCIÓN|
  |---------------|-----------------|
  |`hidden`|Indica que el método existe, pero que no se debe mostrar en un explorador orientado al usuario. Para obtener más información, vea [hidden](/windows/win32/Midl/hidden) en la *Referencia de MIDL*.|
  |`source`|Indica que un miembro del método es un origen de eventos. Para obtener más información, vea [source](/windows/win32/Midl/source) en la *Referencia de MIDL*.|
  |`local`|Especifica al compilador de MIDL que el método no es remoto. Para obtener más información, vea [local](/windows/win32/Midl/local) en la *Referencia de MIDL*.|
  |`restricted`|Especifica que no se puede llamar al método de manera arbitraria. Para obtener más información, vea [restricted](/windows/win32/Midl/restricted) en la *Referencia de MIDL*.|
  |`vararg`|Especifica que el método toma un número variable de argumentos. Para conseguirlo, el último argumento debe ser una matriz segura de tipo `VARIANT` que contenga el resto de los argumentos. Para obtener más información, vea [vararg](/windows/win32/Midl/vararg) en la *Referencia de MIDL*.|
