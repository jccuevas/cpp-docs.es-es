---
title: Nombres, Asistente para agregar propiedades
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.prop.overview
ms.assetid: 0453b7ea-89cb-41a1-80a2-d45f61589c0a
ms.openlocfilehash: 1cb37b2e8f3efd9ff9789a315e6bf32add730708
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636922"
---
# <a name="names-add-property-wizard"></a>Nombres, Asistente para agregar propiedades

Use este asistente para agregar una propiedad a una interfaz.

- **Tipo de propiedad**

   Establece el tipo de propiedad que se va a agregar. Para las interfaces dispinterface de MFC, proporcione un tipo propio o seleccione en la lista predefinida. Si se proporciona una implementación estándar de una propiedad, **Tipo de propiedad** se establece en el tipo estándar y no está disponible para el cambio.

- **Nombre de propiedad**

   Establece el nombre de la propiedad. Para las interfaces dispinterface de MFC asociadas a controles ActiveX, puede proporcionar un nombre propio o seleccionar un nombre de propiedad estándar en la lista predefinida. Si proporciona un nombre de propiedad propio, el tipo de implementación **Estándar** no está disponible. Vea [Propiedades estándar](../ide/stock-properties.md) para obtener una descripción de las propiedades de la lista.

   |Tipo de interfaz|Descripción|
   |--------------------|-----------------|
   |Interfaz dual de ATL, interfaz personalizada e interfaz personalizada local|Se proporciona un nombre de propiedad.|
   |Interfaz dispinterface de MFC, interfaz dispinterface de control ActiveX MFC|Se proporciona un nombre de propiedad o se selecciona una propiedad estándar de la lista. Si se selecciona una propiedad de la lista, el valor apropiado aparecerá en el cuadro **Tipo de propiedad**. Este tipo se puede cambiar, según la selección en **Tipo de implementación**.|

- **Tipo de valor devuelto**

   Solo interfaces de ATL. Establece el tipo de devolución para la propiedad. Para las interfaces duales `HRESULT` siempre es el tipo de valor devuelto, y este cuadro no está disponible. Para las interfaces personalizadas, puede seleccionar un tipo de valor devuelto de la lista. Se sigue recomendando `HRESULT`, ya que proporciona una manera estándar de devolver errores.

- **Nombre de variable**

   Solo para interfaces dispinterface de MFC. Disponible únicamente si se especifica **Variable miembro** en **Tipo de implementación**. Establece el nombre de la variable miembro con el que se asocia la propiedad. De forma predeterminada, el nombre de la variable se establece en m_*NombreDePropiedad*. Este nombre se puede modificar.

- **Función de notificación**

   Solo para interfaces dispinterface de MFC. Disponible únicamente si se especifica **Variable miembro** en **Tipo de implementación**. Establece el nombre de la función de notificación que se llama si cambia la propiedad. De forma predeterminada, el nombre de la función de notificación se establece en On*NombreDePropiedad*Changed. Este nombre se puede modificar.

- **Get (función)**

   Para interfaces dispinterface de MFC. Disponible únicamente si se especifica **Métodos Get/Set** en **Tipo de implementación**. Establece el nombre de la función para obtener la propiedad. De forma predeterminada, el nombre de la función Get se establece en Get*NombreDePropiedad*. Este nombre se puede modificar. Si se elimina el nombre, la función [GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported) se inserta en el mapa de envíos de interfaz. La función Get*NombreDePropiedad* especifica que la propiedad se puede leer.

- **Set (función)**

   Solo para interfaces dispinterface de MFC. Disponible únicamente si se especifica **Métodos Get/Set** en **Tipo de implementación**. Establece el nombre de la función para establecer la propiedad. De forma predeterminada, el nombre de la función Set se establece en Set*NombreDePropiedad*. Este nombre se puede modificar. Si se elimina el nombre, la función [SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported) se inserta en el mapa de envíos de interfaz. La función Set*NombreDePropiedad* indica que la propiedad se puede escribir.

- **Tipo de implementación**

   Solo para interfaces dispinterface de MFC. Especifica cómo implementar la propiedad que se va a agregar.

   |Tipo de implementación|Descripción|
   |-------------------------|-----------------|
   |**Estándar**|Especifica una implementación estándar para la propiedad seleccionada en **Nombre de la propiedad**. El valor predeterminado. Vea [Propiedades estándar](../ide/stock-properties.md) para obtener más información.<br /><br /> Si especifica **Estándar**, aparecen atenuados **Tipo de propiedad**, **Tipo de parámetro** y **Nombre de parámetro**.|
   |**Variable miembro**|Especifica que la propiedad se agrega como una variable miembro. Se pueden agregar propiedades personalizadas o la mayoría de las propiedades estándar como variables miembro. No se puede especificar **Variable miembro** para las propiedades **Título**, **hWnd**, y **Texto**.<br /><br /> Proporciona nombres predeterminados bajo **Nombre de variable** y **Función de notificación**. Este nombre se puede modificar.|
   |**Get/Set (métodos)**|Especifica que la propiedad se agrega como las funciones Get*NombrePropiedad* y Set*NombrePropiedad*, de forma predeterminada. Estos nombres aparecen en **Get (función)** y **Set (función)**.<br /><br /> Puede cambiar el valor predeterminado **Tipo de propiedad**, que pasa un valor para la función Get. Puede especificar parámetros para las funciones **Get** y `Set`.|

- **Get (función)**

   Para las interfaces de ATL. Establece la propiedad como legible; es decir, crea el método **Get** para recuperar esta propiedad del objeto. Debe seleccionar **Get**, `Put` o las dos.

- **Put (función)**

   Solo interfaces de ATL. Establece la propiedad como grabable; es decir, crea el método `Put` para establecer o "poner", esta propiedad del objeto. Debe seleccionar **Get**, `Put` o las dos. Si se selecciona esta opción, se puede elegir entre las dos maneras siguientes de implementar el método:

   |Opción|Descripción|
   |------------|-----------------|
   |**PropPut**|La función [PropPut](../windows/propput.md) devuelve una copia del objeto. Este es el valor predeterminado y la manera más común de convertir la propiedad en grabable.|
   |**PropPutRef**|La función [PropPutRef](../windows/propputref.md) devuelve una referencia al objeto, en lugar de devolver la copia del propio objeto. Considere el uso de esta opción para los objetos, como estructuras o matrices grandes, que puedan tener sobrecarga de inicialización.|

- **Atributos de parámetro**

   Solo interfaces de ATL. Establece si el parámetro especificado por **Nombre de parámetro** es **in**, **out**, ambos o ninguno.

   |Opción|Descripción|
   |------------|-----------------|
   |**in**|Indica que el parámetro se pasa del procedimiento que realiza la llamada al procedimiento que se llama.|
   |**out**|Indica que el parámetro de puntero se devuelve desde el procedimiento llamado al procedimiento que realiza la llamada (desde el servidor al cliente).|

- **Tipo de parámetro**

   Establece el tipo de datos del parámetro. Seleccione el tipo de la lista.

- **Nombre del parámetro**

   Establece el nombre de un parámetro que se va a agregar para la propiedad, si la propiedad tiene parámetros. Después de hacer clic en **Agregar**, el nombre del parámetro aparece en la **Lista de parámetros**.

- **Lista de parámetros**

   Muestra la lista de atributos que se van a agregar a la propiedad. Cada elemento de la lista está formado por el nombre del parámetro, el tipo y los atributos. Haga clic en **Agregar** y **Quitar** para actualizar la lista.

- **Add**

   Agrega el parámetro especificado en **Nombre del parámetro** y **Tipo de parámetro** a la **Lista de parámetros**. Debe hacer clic en **Agregar** para agregar un parámetro a la lista.

- **Remove**

   Quita de la lista el parámetro seleccionado en **Lista de parámetros**.

- **Propiedad predeterminada**

   Solo para la interfaz dispinterface de MFC. Establece esta propiedad como el valor predeterminado de la interfaz. Una interfaz solo puede tener una propiedad predeterminada; una vez que se especifica la propiedad predeterminada, para cualquier otra propiedad que se agregue a la interfaz, esta casilla no está disponible.

## <a name="see-also"></a>Vea también

[Agregar una propiedad](../ide/adding-a-property-visual-cpp.md)<br>
[Atributos IDL, Asistente para agregar propiedades](../ide/idl-attributes-add-property-wizard.md)<br>
[Implementar una interfaz](../ide/implementing-an-interface-visual-cpp.md)