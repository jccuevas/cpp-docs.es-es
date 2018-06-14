---
title: Atributos IDL, Asistente para agregar propiedades | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.prop.idlattributes
dev_langs:
- C++
ms.assetid: 356ed666-79d0-4bd9-a5e7-cda679cbadbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77931296d8d33337c4e630b7327a1ec8fd0a458f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340195"
---
# <a name="idl-attributes-add-property-wizard"></a>Atributos IDL, Asistente para agregar propiedades
Use esta página del Asistente para agregar propiedades para especificar la configuración de lenguaje de definición de interfaz (IDL) para la propiedad.  
  
 **identificador**  
 Establece el id. numérico que identifica la propiedad. Esta opción no está disponible para las propiedades de interfaces personalizadas. Vea [id](http://msdn.microsoft.com/library/windows/desktop/aa367040) en la *Referencia de MIDL*.  
  
 **helpcontext**  
 Especifica un id. de contexto que permite al usuario ver información sobre esta propiedad en el archivo de ayuda. Vea [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851) en la *Referencia de MIDL*.  
  
 **helpstring**  
 Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica. De forma predeterminada, se establece en "property *Nombre de la propiedad*". Vea [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856) en la *Referencia de MIDL*.  
  
## <a name="other-options"></a>Otras opciones  
 No todas las opciones están disponibles para todos los tipos de propiedad.  
  
|Opción|Description|  
|------------|-----------------|  
|**bindable**|Indica que la propiedad admite enlace de datos. Vea [bindable](http://msdn.microsoft.com/library/windows/desktop/aa366738) en la *Referencia de MIDL*. Para la implementación estándar de la propiedad, esta opción se establece de forma predeterminada y no se puede cambiar.|  
|**defaultbind**|Indica que es la única propiedad enlazable que representa mejor el objeto. Vea [defaultbind](http://msdn.microsoft.com/library/windows/desktop/aa366790) en la *Referencia de MIDL*.|  
|**displaybind**|Indica que esta propiedad se debe mostrar al usuario como enlazable. Vea [displaybind](http://msdn.microsoft.com/library/windows/desktop/aa366804) en la *Referencia de MIDL*.|  
|**immediatebind**|Indica que todos los cambios en esta propiedad de un objeto enlazado a datos se notificarán inmediatamente a la base de datos. Vea [immediatebind](http://msdn.microsoft.com/library/windows/desktop/aa367045) en la *Referencia de MIDL*.|  
|**defaultcollelem**|Indica que la propiedad es una función de descriptor de acceso para un elemento de la colección predeterminada. Vea [defaultcollelem](http://msdn.microsoft.com/library/windows/desktop/aa366792) en la *Referencia de MIDL*.|  
|**nonbrowsable**|Etiqueta un miembro de interfaz o interfaz dispinterface que no se debe mostrar en un explorador de propiedades. Vea [nonbrowsable](http://msdn.microsoft.com/library/windows/desktop/aa367117) en la *Referencia de MIDL*.|  
|**requestedit**|Indica que la propiedad admite la notificación **OnRequestEdit**. Vea [requestedit](http://msdn.microsoft.com/library/windows/desktop/aa367155) en la *Referencia de MIDL*. Para la implementación estándar de la propiedad, esta opción se establece de forma predeterminada y no se puede cambiar.|  
|**source**|Indica que un miembro de la propiedad es un origen de eventos. Vea [source](http://msdn.microsoft.com/library/windows/desktop/aa367166) en la *Referencia de MIDL*.|  
|**hidden**|Indica que la propiedad existe pero que no se debe mostrar en un explorador orientado al usuario. Vea [hidden](http://msdn.microsoft.com/library/windows/desktop/aa366861) en la *Referencia de MIDL*.|  
|**restricted**|Especifica que la propiedad no se puede llamar de forma arbitraria. Vea [restricted](http://msdn.microsoft.com/library/windows/desktop/aa367157) en la *Referencia de MIDL*.|  
|`local`|Especifica al compilador MIDL que la propiedad no es remota. Vea [local](http://msdn.microsoft.com/library/windows/desktop/aa367071) en la *Referencia de MIDL*.|  
  
## <a name="see-also"></a>Vea también  
 [Agregar una propiedad](../ide/adding-a-property-visual-cpp.md)   
 [Nombres, Asistente para agregar propiedades](../ide/names-add-property-wizard.md)   
 [Implementar una interfaz](../ide/implementing-an-interface-visual-cpp.md)   
 [Propiedades estándar](../ide/stock-properties.md)