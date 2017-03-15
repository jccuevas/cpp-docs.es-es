---
title: "Nombres, Asistente para agregar propiedades | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.prop.overview"
dev_langs: 
  - "C++"
ms.assetid: 0453b7ea-89cb-41a1-80a2-d45f61589c0a
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Nombres, Asistente para agregar propiedades
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este asistente se utiliza para agregar una propiedad a una interfaz.  
  
 **Tipo de propiedad**  
 Permite definir el tipo de propiedad que se va a agregar.  Con interfaces dispinterfaces de MFC, deberá especificar un tipo propio o seleccionarlo de la lista predefinida.  Si especifica una implementación estándar de una propiedad, **Tipo de propiedad** se definirá como tipo estándar y no se podrá cambiar.  
  
 **Nombre de la propiedad**  
 Permite especificar el nombre de la propiedad.  Con interfaces dispinterfaces de MFC asociadas a controles ActiveX, podrá especificar su propio nombre o elegir de la lista predefinida un nombre de propiedad estándar.  Si especifica su propio nombre de propiedad, no podrá utilizar el tipo de implementación **Estándar**.  Vea [Propiedades estándar](../ide/stock-properties.md) para obtener una descripción de las propiedades de la lista.  
  
|Tipo de interfaz|Descripción|  
|----------------------|-----------------|  
|Interfaz dual ATL, interfaz personalizada e interfaz personalizada local|Especifique un nombre de propiedad.|  
|Dispinterface MFC, dispinterface de control ActiveX MFC|Especifique un nombre de propiedad o seleccione una propiedad estándar de la lista.  Si selecciona una propiedad de la lista, el valor apropiado aparecerá en el cuadro **Tipo de propiedad**.  Podrá cambiar este tipo según la selección efectuada en **Tipo de implementación**.|  
  
 **Tipo de valor devuelto**  
 Sólo para interfaces ATL.  Establece el tipo de valor devuelto para la propiedad.  Con interfaces duales, el tipo de valor devuelto será siempre `HRESULT` y este cuadro no estará disponible.  En las interfaces personalizadas, puede seleccionar un tipo de valor devuelto en la lista.  Todavía se sigue recomendando `HRESULT`, ya que proporciona una manera estándar de devolver errores.  
  
 **Nombre de variable**  
 Sólo para dispinterfaces de MFC.  Sólo está disponible si se especifica **Variable miembro** bajo **Tipo de implementación**.  Permite establecer el nombre de la variable miembro con la que se asocia la propiedad.  De forma predeterminada, el nombre de variable toma el valor m\_*NombreDePropiedad*.  Este nombre se puede modificar.  
  
 **Función de notificación**  
 Sólo para dispinterfaces de MFC.  Sólo está disponible si se especifica **Variable miembro** bajo **Tipo de implementación**.  Permite especificar el nombre de la función de notificación a la que se llamará si cambia la propiedad.  De forma predeterminada, el nombre de la función de notificación toma el valor On*NombreDePropiedad*Changed.  Este nombre se puede modificar.  
  
 **Función Get**  
 Para dispinterfaces de MFC.  Sólo está disponible si se especifica **Métodos Get\/Set** bajo **Tipo de implementación**.  Permite asignar un nombre a la función utilizada para obtener la propiedad.  De forma predeterminada, el nombre de la función Get toma el valor Get*NombreDePropiedad*.  Este nombre se puede modificar.  Si elimina el nombre, se insertará la función [GetNotSupported](../Topic/COleControl::GetNotSupported.md) en el mapa de envíos de la interfaz.  La función Get*NombreDePropiedad* indica que la propiedad se puede leer.  
  
 **Función Set**  
 Sólo para dispinterfaces de MFC.  Sólo está disponible si se especifica **Métodos Get\/Set** bajo **Tipo de implementación**.  Permite dar un nombre a la función utilizada para establecer la propiedad.  De forma predeterminada, el nombre dado a la función Set es Set*NombreDePropiedad*.  Este nombre se puede modificar.  Si elimina el nombre, se insertará la función [SetNotSupported](../Topic/COleControl::SetNotSupported.md) en el mapa de envíos de la interfaz.  La función Set*NombreDePropiedad* indica que se trata de una propiedad que permite escritura.  
  
 **Tipo de implementación**  
 Sólo para dispinterfaces de MFC.  Especifica cómo implementar la propiedad que se está agregando.  
  
|Tipo de implementación|Descripción|  
|----------------------------|-----------------|  
|**Estándar**|Especifica una implementación estándar para la propiedad seleccionada en **Nombre de propiedad**.  Es el formato predeterminado.  Vea [Propiedades estándar](../ide/stock-properties.md) para obtener más información.<br /><br /> Si se especifica **Estándar**, las opciones **Tipo de propiedad**, **Tipo de parámetro** y **Nombre de parámetro** aparecerán atenuadas.|  
|**Variable miembro**|Especifica que la propiedad se agrega como variable miembro.  Las propiedades personalizadas y la mayoría de las propiedades estándar pueden agregarse como variables miembro.  No es posible especificar **Variable miembro** para las propiedades **Caption**, **hWnd** y **Text**.<br /><br /> Proporciona nombres predeterminados bajo **Nombre de variable** y **Función de notificación**.  Este nombre se puede modificar.|  
|**Métodos Get\/Set**|Especifica que la propiedad se agrega, de forma predeterminada, como función Get*NombreDePropiedad* y Set*NombreDePropiedad*.  Estos nombres aparecen en **Función Get** y **Función Set**.<br /><br /> Se puede cambiar la opción **Tipo de propiedad** predeterminada, que pasa un valor a la función Get.  Se pueden especificar parámetros para las funciones **Get** y `Set`.|  
  
 **Función Get**  
 Para interfaces ATL.  Define la propiedad como de lectura, es decir, crea el método **Get** para recuperar la propiedad a partir del objeto.  Deberá seleccionar **Get**, `Put` o ambos.  
  
 **Función Put**  
 Sólo para interfaces ATL.  Hace que la propiedad sea de escritura, es decir, crea el método `Put` para establecer o "colocar" esta propiedad en el objeto.  Deberá seleccionar **Get**, `Put` o ambos.  Si selecciona esta opción, podrá elegir entre las dos formas siguientes de implementar el método:  
  
|Opción|Descripción|  
|------------|-----------------|  
|**PropPut**|La función [PropPut](../windows/propput.md) devuelve una copia del objeto.  Es la forma predeterminada y más usual para hacer que la propiedad pueda aceptar valores \(escritura\).|  
|**PropPutRef**|La función [PropPutRef](../windows/propputref.md) devuelve una referencia al objeto en lugar de devolver la copia del propio objeto.  Esta opción es útil para objetos cuya inicialización supone una sobrecarga, como structs o matrices grandes.|  
  
 **Atributos del parámetro**  
 Sólo para interfaces ATL.  Indica si el parámetro especificado en **Nombre de parámetro** es **in**, **out**, ambos o ninguno.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**in**|Indica que el parámetro se pasa del procedimiento de llamada al procedimiento llamado.|  
|**out**|Indica que el parámetro de puntero se devuelve desde el procedimiento llamado al procedimiento de llamada \(del servidor al cliente\).|  
  
 **Tipo de parámetro**  
 Permite definir el tipo de datos del parámetro.  Selecciónelo en la lista.  
  
 **Nombre de parámetro**  
 Define el nombre de los parámetros que se agregarán, en su caso, a la propiedad.  Después de hacer clic en **Agregar**, el nombre de parámetro aparece en la **Lista de parámetros**.  
  
 **Lista de parámetros**  
 Muestra la lista de atributos que se van a agregar a la propiedad.  Cada elemento de la lista consta de: nombre de parámetro, tipo de parámetro y atributos.  Utilice **Agregar** y **Quitar** para modificar la lista.  
  
 **Agregar**  
 Agrega a la **Lista de parámetros** el parámetro especificado en **Nombre de parámetro** y **Tipo de parámetro**.  Debe hacer clic en **Agregar** para agregar un parámetro a la lista.  
  
 **Remove**  
 Quita de la **Lista de parámetros** el parámetro seleccionado.  
  
 **Propiedad predeterminada**  
 Sólo para dispinterfaces de MFC.  Define esta propiedad como propiedad predeterminada para la interfaz.  Una interfaz sólo podrá tener una propiedad predeterminada; una vez especificada, la casilla quedará deshabilitada para cualquier otra propiedad que se agregue a la interfaz.  
  
## Vea también  
 [Agregar una propiedad](../ide/adding-a-property-visual-cpp.md)   
 [Atributos IDL, Asistente para agregar propiedades](../ide/idl-attributes-add-property-wizard.md)   
 [Implementar una interfaz](../ide/implementing-an-interface-visual-cpp.md)