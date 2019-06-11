---
title: Agregar una propiedad
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.prop.overview
- vc.codewiz.prop.idlattributes
helpviewer_keywords:
- interfaces, adding properties
- properties [C++], adding to interfaces
- names, add property wizard
- IDL attributes, add property wizard
- stock properties, about stock properties
- stock properties
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
ms.openlocfilehash: 79938cb5c762292c5e1802832477c3a568ae2fdb
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504469"
---
# <a name="add-a-property"></a>Agregar una propiedad

Se puede usar el [Asistente para agregar propiedades](#names-add-property-wizard) para agregar un método a una interfaz del proyecto.

**Para agregar una propiedad al objeto:**

1. En la [Vista de clases](/visualstudio/ide/viewing-the-structure-of-code), haga clic con el botón derecho en la interfaz a la que quiera agregar la propiedad.

   > [!NOTE]
   > También puede agregar propiedades a interfaces dispinterface que, a menos que el proyecto tenga atributos, se anidan bajo el nodo de biblioteca.

1. En el menú contextual, elija **Agregar** y luego **Agregar propiedad**.

1. En el [Asistente para agregar propiedades](#names-add-property-wizard), proporcione la información para crear la propiedad.

1. Especifique cualquier configuración de lenguaje de definición de interfaz (IDL) para la propiedad en la página [Atributos IDL](#idl-attributes-add-property-wizard) del asistente.

1. Seleccione **Finalizar** para agregar la propiedad.

Los métodos `Get` y `Put` de la propiedad se muestran como dos iconos en la Vista de clases, en la interfaz donde se ha definido. Puede hacer doble clic en cualquiera de los iconos para ver la declaración de propiedad en el archivo .idl.

- En el caso de las interfaces ATL, las funciones `Get` y `Put` se agregan al archivo .cpp, mientras que las referencias a estas funciones se agregan al archivo .h.

- Para las interfaces dispinterface de MFC, si selecciona **Variable miembro** como el tipo de implementación, se agregan un método y una variable a la clase que lo implementa. Si selecciona **Métodos Get/Set** como el tipo de implementación, se agregan dos métodos a la clase que lo implementa.

## <a name="in-this-section"></a>En esta sección

- [Nombres, Asistente para agregar propiedades](#names-add-property-wizard)
- [Atributos IDL, Asistente para agregar propiedades](#idl-attributes-add-property-wizard)
- [Propiedades estándar](#stock-properties)

## <a name="names-add-property-wizard"></a>Nombres, Asistente para agregar propiedades

Use este asistente para agregar una propiedad a una interfaz.

- **Tipo de propiedad**

  Establece el tipo de propiedad que se va a agregar. Para las interfaces dispinterface de MFC, proporcione un tipo propio o seleccione en la lista predefinida. Si se proporciona una implementación estándar de una propiedad, **Tipo de propiedad** se establece en el tipo estándar y no está disponible para el cambio.

- **Nombre de propiedad**

  Establece el nombre de la propiedad. Para las interfaces dispinterface de MFC asociadas a controles ActiveX, puede proporcionar un nombre propio o seleccionar un nombre de propiedad estándar en la lista predefinida. Si proporciona un nombre de propiedad propio, el tipo de implementación **Estándar** no está disponible. Vea [Propiedades estándar](#stock-properties) para obtener una descripción de las propiedades de la lista.

  |Tipo de interfaz|Descripción|
  |--------------------|-----------------|
  |Interfaz dual de ATL, interfaz personalizada e interfaz personalizada local|Se proporciona un nombre de propiedad.|
  |Interfaz dispinterface de MFC, interfaz dispinterface de control ActiveX MFC|Se proporciona un nombre de propiedad o se selecciona una propiedad estándar de la lista. Si se selecciona una propiedad de la lista, el valor apropiado aparecerá en el cuadro **Tipo de propiedad**. Este tipo se puede cambiar, según la selección en **Tipo de implementación**.|

- **Tipo de valor devuelto**

  Solo interfaces de ATL. Establece el tipo de devolución para la propiedad. Para las interfaces duales `HRESULT` siempre es el tipo de valor devuelto, y este cuadro no está disponible. Para las interfaces personalizadas, puede seleccionar un tipo de valor devuelto de la lista. Se sigue recomendando `HRESULT`, ya que proporciona una manera estándar de devolver errores.

- **Nombre de variable**

  Solo para interfaces dispinterface de MFC. Disponible únicamente si se especifica **Variable miembro** en **Tipo de implementación**. Establece el nombre de la variable miembro con el que se asocia la propiedad. De forma predeterminada, el nombre de la variable se establece en `m_`*NombreDePropiedad*. Este nombre se puede modificar.

- **Función de notificación**

  Solo para interfaces dispinterface de MFC. Disponible únicamente si se especifica **Variable miembro** en **Tipo de implementación**. Establece el nombre de la función de notificación que se llama si cambia la propiedad. De forma predeterminada, el nombre de la función de notificación se establece en `On`*NombreDePropiedad*`Changed`. Este nombre se puede modificar.

- **Get (función)**

  Para interfaces dispinterface de MFC. Disponible únicamente si se especifica **Métodos Get/Set** en **Tipo de implementación**. Establece el nombre de la función para obtener la propiedad. De forma predeterminada, el nombre de la función `Get` se establece en `Get`*NombreDePropiedad*. Este nombre se puede modificar. Si se elimina el nombre, la función [GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported) se inserta en el mapa de envíos de interfaz. La función `Get`*NombreDePropiedad* especifica que la propiedad se puede leer.

- **Set (función)**

  Solo para interfaces dispinterface de MFC. Disponible únicamente si se especifica **Métodos Get/Set** en **Tipo de implementación**. Establece el nombre de la función para establecer la propiedad. De forma predeterminada, el nombre de la función `Set` se establece en `Set`*NombreDePropiedad*. Este nombre se puede modificar. Si se elimina el nombre, la función [SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported) se inserta en el mapa de envíos de interfaz. La función `Set`*NombreDePropiedad* especifica que la propiedad se puede escribir.

- **Tipo de implementación**

  Solo para interfaces dispinterface de MFC. Especifica cómo implementar la propiedad que se va a agregar.

  |Tipo de implementación|Descripción|
  |-------------------------|-----------------|
  |**Estándar**|Especifica una implementación estándar para la propiedad seleccionada en **Nombre de la propiedad**. El valor predeterminado. Para obtener más información, vea [Propiedades estándar](#stock-properties).<br /><br /> Si especifica **Estándar**, aparecen atenuados **Tipo de propiedad**, **Tipo de parámetro** y **Nombre de parámetro**.|
  |**Variable miembro**|Especifica que la propiedad se agrega como una variable miembro. Se pueden agregar propiedades personalizadas o la mayoría de las propiedades estándar como variables miembro. No puede especificar **Variable miembro** para las propiedades `Caption`, `hWnd` y `Text`.<br /><br /> Proporciona nombres predeterminados bajo **Nombre de variable** y **Función de notificación**. Este nombre se puede modificar.|
  |**Get/Set (métodos)**|Especifica que la propiedad se agrega como las funciones `Get`*NombreDePropiedad* y `Set`*NombreDePropiedad*, de forma predeterminada. Estos nombres aparecen en **Get (función)** y **Set (función)** .<br /><br /> Puede cambiar el valor predeterminado **Tipo de propiedad**, que pasa un valor para la función Get. Puede especificar parámetros para las funciones `Get` y `Set`.|

- **Get (función)**

  Para las interfaces de ATL. Establece la propiedad como legible; es decir, crea el método `Get` para recuperar esta propiedad del objeto. Seleccione **Get**, **Put** o ambas.

- **Put (función)**

  Solo interfaces de ATL. Establece la propiedad como grabable; es decir, crea el método `Put` para establecer o "poner", esta propiedad del objeto. Seleccione **Get**, **Put** o ambas. Si se selecciona esta opción, se puede elegir entre las dos maneras siguientes de implementar el método:

  |Opción|Descripción|
  |------------|-----------------|
  |**PropPut**|La función [PropPut](../windows/propput.md) devuelve una copia del objeto. Este es el valor predeterminado y la manera más común de convertir la propiedad en grabable.|
  |**PropPutRef**|La función [PropPutRef](../windows/propputref.md) devuelve una referencia al objeto, en lugar de devolver la copia del propio objeto. Considere el uso de esta opción para los objetos, como estructuras o matrices grandes, que puedan tener sobrecarga de inicialización.|

- **Atributos de parámetro**

  Solo interfaces de ATL. Establece si el parámetro especificado por **Nombre del parámetro** es `in`, `out`, ambos o ninguno.

  |Opción|Descripción|
  |------------|-----------------|
  |`in`|Indica que el parámetro se pasa del procedimiento que realiza la llamada al procedimiento que se llama.|
  |`out`|Indica que el parámetro de puntero se devuelve desde el procedimiento llamado al procedimiento que realiza la llamada (desde el servidor al cliente).|

- **Tipo de parámetro**

  Establece el tipo de datos del parámetro. Seleccione el tipo de la lista.

- **Nombre del parámetro**

  Establece el nombre de un parámetro que se va a agregar para la propiedad, si esta tiene parámetros. Después de seleccionar **Agregar**, el nombre del parámetro aparece en **Lista de parámetros**.

- **Lista de parámetros**

  Muestra la lista de atributos que se van a agregar a la propiedad. Cada elemento de la lista está formado por el nombre del parámetro, el tipo y los atributos. Haga clic en **Agregar** y **Quitar** para actualizar la lista.

- **Add**

  Agrega el parámetro especificado en **Nombre del parámetro** y **Tipo de parámetro** a la **Lista de parámetros**. Seleccione **Agregar** para agregar un parámetro a la lista.

- **Remove**

  Quita de la lista el parámetro seleccionado en **Lista de parámetros**.

- **Propiedad predeterminada**

  Solo para la interfaz dispinterface de MFC. Establece esta propiedad como el valor predeterminado de la interfaz. Una interfaz solo puede tener una propiedad predeterminada; una vez que se especifica la propiedad predeterminada, para cualquier otra propiedad que se agregue a la interfaz, esta casilla no está disponible.

## <a name="idl-attributes-add-property-wizard"></a>Atributos IDL, Asistente para agregar propiedades

Use esta página del Asistente para agregar propiedades para especificar la configuración de lenguaje de definición de interfaz (IDL) para la propiedad.

- `id`

  Establece el id. numérico que identifica la propiedad. Esta opción no está disponible para las propiedades de interfaces personalizadas. Vea [id](/windows/desktop/Midl/id) en la *Referencia de MIDL*.

- `helpcontext`

  Especifica un id. de contexto que permite al usuario ver información sobre esta propiedad en el archivo de ayuda. Vea [helpcontext](/windows/desktop/Midl/helpcontext) en la *Referencia de MIDL*.

- `helpstring`

  Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica. De forma predeterminada, se establece en `property`&nbsp;*Property&nbsp;name*. Vea [helpstring](/windows/desktop/Midl/helpstring) en la *Referencia de MIDL*.

### <a name="other-options"></a>Otras opciones

No todas las opciones están disponibles para todos los tipos de propiedad.

|Opción|Descripción|
|------------|-----------------|
|`bindable`|Indica que la propiedad admite enlace de datos. Vea [bindable](/windows/desktop/Midl/bindable) en la *Referencia de MIDL*. Para la implementación estándar de la propiedad, esta opción se establece de forma predeterminada y no se puede cambiar.|
|`defaultbind`|Indica que esta propiedad enlazable única representa mejor al objeto. Vea [defaultbind](/windows/desktop/Midl/defaultbind) en la *Referencia de MIDL*.|
|`displaybind`|Indica que esta propiedad se debe mostrar al usuario como enlazable. Vea [displaybind](/windows/desktop/Midl/displaybind) en la *Referencia de MIDL*.|
|`immediatebind`|Indica que todos los cambios en esta propiedad de un objeto enlazado a datos se notificarán inmediatamente a la base de datos. Vea [immediatebind](/windows/desktop/Midl/immediatebind) en la *Referencia de MIDL*.|
|`defaultcollelem`|Indica que la propiedad es una función de descriptor de acceso para un elemento de la colección predeterminada. Vea [defaultcollelem](/windows/desktop/Midl/defaultcollelem) en la *Referencia de MIDL*.|
|`nonbrowsable`|Etiqueta a un miembro de interfaz o de interfaz dispinterface que no se debe mostrar en un explorador de propiedades. Vea [nonbrowsable](/windows/desktop/Midl/nonbrowsable) en la *Referencia de MIDL*.|
|`requestedit`|Indica que la propiedad admite la notificación `OnRequestEdit`. Vea [requestedit](/windows/desktop/Midl/requestedit) en la *Referencia de MIDL*. Para la implementación estándar de la propiedad, esta opción se establece de forma predeterminada y no se puede cambiar.|
|`source`|Indica que un miembro de la propiedad es un origen de eventos. Vea [source](/windows/desktop/Midl/source) en la *Referencia de MIDL*.|
|`hidden`|Indica que la propiedad existe, pero que no se debe mostrar en un explorador orientado al usuario. Vea [hidden](/windows/desktop/Midl/hidden) en la *Referencia de MIDL*.|
|`restricted`|Especifica que no se puede llamar a la propiedad de forma arbitraria. Vea [restricted](/windows/desktop/Midl/restricted) en la *Referencia de MIDL*.|
|`local`|Especifica al compilador de MIDL que la propiedad no es remota. Vea [local](/windows/desktop/Midl/local) en la *Referencia de MIDL*.|

## <a name="stock-properties"></a>Propiedades estándar

Si va a agregar una propiedad a una interfaz dispinterface de MFC mediante el [Asistente para agregar propiedades](#idl-attributes-add-property-wizard), puede elegir una propiedad estándar de la lista **Nombre de la propiedad** en la página [Nombres](../ide/names-add-property-wizard.md) del asistente. Estas propiedades son las siguientes:

|Nombre de la propiedad|Descripción|
|-------------------|-----------------|
|`Appearance`|Devuelve o establece un valor que determina la apariencia del control. La propiedad `Appearance` del control puede incluir u omitir efectos de presentación tridimensionales. Se trata de una propiedad ambiente de lectura y escritura.|
|`BackColor`|Devuelve o establece la propiedad `BackColor` de ambiente del control en un color de paleta (RGB) o un color del sistema predefinido. De forma predeterminada, su valor se corresponde al color de primer plano del contenedor del control. Se trata de una propiedad ambiente de lectura y escritura.|
|`BorderStyle`|Devuelve o establece el estilo de borde para un control. Se trata de una propiedad de lectura y escritura.|
|`Caption`|Devuelve o establece la propiedad `Caption` del control. El título es el título de la ventana. `Caption` no tiene ningún tipo de implementación **Variable miembro**.|
|`Enabled`|Devuelve o establece la propiedad `Enabled` del control. Un control habilitado puede responder a eventos generados por el usuario.|
|`Font`|Devuelve o establece la fuente de ambiente del control. Es NULL si el control no tiene ninguna fuente.|
|`ForeColor`|Devuelve o establece la propiedad `ForeColor` de ambiente del control.|
|`hWnd`|Devuelve o establece la propiedad `hWnd` del control. `hWnd` no tiene ningún tipo de implementación **Variable miembro**.|
|`ReadyState`|Devuelve o establece la propiedad `ReadyState` del control. Un control puede estar no inicializado, inicializado, cargando, interactivo o completo. Para obtener más información, vea [READYSTATE](/previous-versions//aa768362\(v=vs.85\)) en el *SDK de Internet*.|
|`Text`|Devuelve o establece el texto contenido en un control. `Text` no tiene ningún tipo de implementación **Variable miembro**.|
