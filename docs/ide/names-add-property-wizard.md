---
title: Nombres, Asistente para agregar propiedades | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.prop.overview
dev_langs: C++
ms.assetid: 0453b7ea-89cb-41a1-80a2-d45f61589c0a
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 310ac33fa4e34e75273732f715472114bab9650f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="names-add-property-wizard"></a>Nombres, Asistente para agregar propiedades
Use este asistente para agregar una propiedad a una interfaz.  
  
 **Tipo de propiedad**  
 Establece el tipo de propiedad que se va a agregar. Para interfaces dispinterface MFC, proporcionar su propio tipo o seleccione en la lista predefinida. Si se proporciona una implementación estándar de una propiedad, **tipo de propiedad** se establece en el tipo estándar y no está disponible para el cambio.  
  
 **Nombre de propiedad**  
 Establece el nombre de la propiedad. Para interfaces dispinterface MFC asociada a controles ActiveX, puede proporcionar su propio nombre o puede seleccionar un nombre de propiedad estándar de la lista predefinida. Si proporciona su propio nombre de propiedad, el **existencias** tipo de implementación no está disponible. Vea [propiedades estándar](../ide/stock-properties.md) para obtener una descripción de las propiedades de la lista.  
  
|Tipo de interfaz|Descripción|  
|--------------------|-----------------|  
|Interfaz dual ATL, interfaz personalizada e interfaz personalizada local|Proporcione un nombre de propiedad.|  
|Dispinterface MFC, dispinterface de controles ActiveX en MFC|Proporcione un nombre de propiedad o seleccione una propiedad estándar de la lista. Si selecciona una propiedad de la lista, el valor apropiado aparecerá en el **tipo de propiedad** cuadro. Puede cambiar este tipo, según su selección en **tipo de implementación**.|  
  
 **Tipo de valor devuelto**  
 Interfaces ATL. Establece el tipo de valor devuelto para la propiedad. Para interfaces duales `HRESULT` siempre es el tipo de valor devuelto, y este cuadro no está disponible. Para las interfaces personalizadas, puede seleccionar un tipo de valor devuelto de la lista. `HRESULT`todavía se se recomienda, ya que proporciona una manera estándar de devolver errores.  
  
 **Nombre de variable**  
 MFC interfaces dispinterface solo. Disponible únicamente si se especifica **variable miembro** en **tipo de implementación**. Establece el nombre de la variable de miembro con el que se asocia la propiedad. De forma predeterminada, se establece el nombre de variable toma el valor m_*PropertyName*. Puede modificar este nombre.  
  
 **Función de notificación**  
 MFC interfaces dispinterface solo. Disponible únicamente si se especifica **variable miembro** en **tipo de implementación**. Establece el nombre de la función de notificación llama si los cambios de propiedad. De forma predeterminada, el nombre de la función de notificación se establece en*PropertyName*Changed. Puede modificar este nombre.  
  
 **Get (función)**  
 Para interfaces dispinterface MFC. Disponible únicamente si se especifica **métodos Get/Set** en **tipo de implementación**. Establece el nombre de la función que se va a obtener la propiedad. De forma predeterminada, el nombre de la función Get se establece en Get*PropertyName*. Puede modificar este nombre. Si elimina el nombre, la función [GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported) se inserta en el mapa de envíos de interfaz. Get*PropertyName* función especifica que la propiedad se puede leer.  
  
 **Función de conjunto**  
 MFC interfaces dispinterface solo. Disponible únicamente si se especifica **métodos Get/Set** en **tipo de implementación**. Establece el nombre de la función para establecer la propiedad. De forma predeterminada, se establece el nombre de la función de conjunto a conjunto*PropertyName*. Puede modificar este nombre. Si elimina el nombre, la función [SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported) se inserta en el mapa de envíos de interfaz. El conjunto de*PropertyName* función indica que la propiedad se puede escribir.  
  
 **Tipo de implementación**  
 MFC interfaces dispinterface solo. Especifica cómo implementar la propiedad que se va a agregar.  
  
|Tipo de implementación|Descripción|  
|-------------------------|-----------------|  
|**Existencias**|Especifica una implementación estándar para la propiedad seleccionada en **nombre de la propiedad**. El valor predeterminado. Vea [propiedades estándar](../ide/stock-properties.md) para obtener más información.<br /><br /> Si especifica **existencias**, a continuación, **tipo de propiedad**, **tipo de parámetro**, y **nombre de parámetro** aparecen atenuados.|  
|**Variable de miembro**|Especifica que la propiedad se agrega como una variable de miembro. Puede agregar propiedades personalizadas o la mayoría de las propiedades estándar como variables de miembro. No se puede especificar **variable miembro** para **título**, **hWnd**, y **texto** propiedades.<br /><br /> Proporciona nombres predeterminados bajo **nombre de Variable** y **función de notificación**. Puede modificar este nombre.|  
|**Métodos Get/Set.**|Especifica la propiedad se agrega como Get*PropertyName* y establezca*PropertyName* funciones, de forma predeterminada. Estos nombres aparecen en **Get (función)** y **Set (función)**.<br /><br /> Puede cambiar el valor predeterminado **tipo de propiedad**, que pasa un valor para la función Get. Puede especificar parámetros para el **obtener** y `Set` funciones.|  
  
 **Get (función)**  
 Con las interfaces ATL. Establece la propiedad como legible; es decir, crea el **obtener** método para recuperar esta propiedad del objeto. Debe seleccionar **obtener**, `Put`, o ambos.  
  
 **Función Put**  
 Interfaces ATL. Establece la propiedad de escritura; es decir, crea el `Put` método para establecer o "poner", esta propiedad del objeto. Debe seleccionar **obtener**, `Put`, o ambos. Si selecciona esta opción, se puede elegir entre las dos maneras siguientes para implementar el método:  
  
|Opción|Descripción|  
|------------|-----------------|  
|**PropPut**|El [PropPut](../windows/propput.md) función devuelve una copia del objeto. Este es el valor predeterminado y la manera más común para convertir la propiedad grabable.|  
|**PropPutRef**|El [PropPutRef](../windows/propputref.md) función devuelve una referencia al objeto, en lugar de devolver la copia del propio objeto. Considere el uso de esta opción para los objetos, como grandes estructuras o matrices, que pueden tener la sobrecarga de inicialización.|  
  
 **Atributos de parámetro**  
 Interfaces ATL. Establece si el parámetro especificado por **nombre de parámetro** es **en**, **out**, ambos o ninguno.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**in**|Indica que el parámetro se pasa desde el procedimiento que realiza la llamada al procedimiento llamado.|  
|**out**|Indica que el parámetro de puntero se devuelve desde el procedimiento llamado al procedimiento que realiza la llamada (desde el servidor al cliente).|  
  
 **Tipo de parámetro**  
 Establece el tipo de datos del parámetro. Seleccione el tipo de la lista.  
  
 **Nombre de parámetro**  
 Establece el nombre de un parámetro que se va a agregar para la propiedad, si la propiedad tiene parámetros. Una vez que pulses **agregar**, el nombre del parámetro aparece en **lista de parámetros**.  
  
 **Lista de parámetros**  
 Muestra la lista de atributos que se agregarán a la propiedad. Cada elemento de la lista está formada por el nombre del parámetro, el tipo de parámetro y los atributos. Use **agregar** y **quitar** para actualizar la lista.  
  
 **Add**  
 Agrega el parámetro especificado en **nombre de parámetro** y **tipo de parámetro** a la **lista de parámetros**. Debe hacer clic en **agregar** para agregar un parámetro a la lista.  
  
 **Remove**  
 Quita el parámetro seleccionado en **lista de parámetros**.  
  
 **Propiedad predeterminada**  
 Solo dispinterface MFC. Esta propiedad se establece como el valor predeterminado de la interfaz. Una interfaz puede tener sólo una propiedad predeterminada; una vez que se especifica la propiedad predeterminada, para cualquier otra propiedad que se agregue a la interfaz, esta casilla no está disponible.  
  
## <a name="see-also"></a>Vea también  
 [Agregar una propiedad](../ide/adding-a-property-visual-cpp.md)   
 [Atributos IDL, Asistente para agregar propiedades](../ide/idl-attributes-add-property-wizard.md)   
 [Implementar una interfaz](../ide/implementing-an-interface-visual-cpp.md)