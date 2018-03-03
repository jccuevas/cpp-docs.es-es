---
title: Atributos IDL, Asistente para agregar propiedades | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.prop.idlattributes
dev_langs:
- C++
ms.assetid: 356ed666-79d0-4bd9-a5e7-cda679cbadbd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8ec158c117161c5a5c2ffd23cef0d5c79c312ae7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="idl-attributes-add-property-wizard"></a>Atributos IDL, Asistente para agregar propiedades
Utilice esta página del Asistente para agregar propiedades para especificar la configuración de idioma (IDL) de definición de interfaz para la propiedad.  
  
 **identificador**  
 Establece el identificador numérico que identifica la propiedad. Esta opción no está disponible para las propiedades de interfaces personalizadas. Vea [identificador](http://msdn.microsoft.com/library/windows/desktop/aa367040) en el *MIDL referencia*.  
  
 **helpcontext**  
 Especifica un identificador de contexto que permite al usuario ver información acerca de esta propiedad en el archivo de ayuda. Vea [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851) en el *MIDL referencia*.  
  
 **helpstring**  
 Especifica una cadena de caracteres que se utiliza para describir el elemento al que se aplica. De forma predeterminada, se establece en "propiedad *nombre de la propiedad*." Vea [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856) en el *MIDL referencia*.  
  
## <a name="other-options"></a>Otras opciones  
 No todas las opciones están disponibles para todos los tipos de propiedad.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**bindable**|Indica que la propiedad admite enlace de datos. Vea [enlazables](http://msdn.microsoft.com/library/windows/desktop/aa366738) en el *MIDL referencia*. La implementación estándar de la propiedad, esta opción se establece de forma predeterminada y se podrá cambiar.|  
|**defaultbind**|Indica que la única propiedad enlazable mejor representa el objeto. Vea [defaultbind](http://msdn.microsoft.com/library/windows/desktop/aa366790) en el *MIDL referencia*.|  
|**displaybind**|Indica que esta propiedad se debería mostrar al usuario como enlazable. Vea [displaybind](http://msdn.microsoft.com/library/windows/desktop/aa366804) en el *MIDL referencia*.|  
|**immediatebind**|Indica que se notificará inmediatamente a la base de datos de todos los cambios a esta propiedad de un objeto enlazado a datos. Vea [immediatebind](http://msdn.microsoft.com/library/windows/desktop/aa367045) en el *MIDL referencia*.|  
|**defaultcollelem**|Indica que la propiedad es una función de descriptor de acceso de un elemento de la colección predeterminada. Vea [defaultcollelem](http://msdn.microsoft.com/library/windows/desktop/aa366792) en el *MIDL referencia*.|  
|**nonbrowsable**|Etiqueta a un miembro de interfaz o dispinterface que no se debe mostrar en un explorador de propiedades. Vea [nonbrowsable](http://msdn.microsoft.com/library/windows/desktop/aa367117) en el *MIDL referencia*.|  
|**requestedit**|Indica que la propiedad admite la **OnRequestEdit** notificación vea [requestedit](http://msdn.microsoft.com/library/windows/desktop/aa367155) en el *MIDL referencia*. La implementación estándar de la propiedad, esta opción se establece de forma predeterminada y se podrá cambiar.|  
|**origen**|Indica que un miembro de la propiedad es un origen de eventos. Vea [origen](http://msdn.microsoft.com/library/windows/desktop/aa367166) en el *MIDL referencia*.|  
|**hidden**|Indica que la propiedad existe pero no se debe mostrar en un explorador orientado al usuario. Vea [oculto](http://msdn.microsoft.com/library/windows/desktop/aa366861) en el *MIDL referencia*.|  
|**restricted**|Especifica que la propiedad no se puede llamar arbitrariamente. Vea [restringido](http://msdn.microsoft.com/library/windows/desktop/aa367157) en el *MIDL referencia*.|  
|`local`|Especifica que el compilador MIDL que la propiedad no es remota. Vea [local](http://msdn.microsoft.com/library/windows/desktop/aa367071) en el *MIDL referencia*.|  
  
## <a name="see-also"></a>Vea también  
 [Agregar una propiedad](../ide/adding-a-property-visual-cpp.md)   
 [Nombres, Asistente para agregar propiedades](../ide/names-add-property-wizard.md)   
 [Implementar una interfaz](../ide/implementing-an-interface-visual-cpp.md)   
 [Propiedades estándar](../ide/stock-properties.md)