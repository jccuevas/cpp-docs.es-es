---
title: "Atributos IDL, Asistente para agregar propiedades | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.prop.idlattributes"
dev_langs: 
  - "C++"
ms.assetid: 356ed666-79d0-4bd9-a5e7-cda679cbadbd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Atributos IDL, Asistente para agregar propiedades
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta página del asistente se utiliza para especificar la configuración de lenguaje de definición de interfaz \(IDL\) de la propiedad.  
  
 **id**  
 Permite especificar el identificador numérico de la propiedad.  Esta opción no está disponible con propiedades de interfaces personalizadas.  Vea [id](http://msdn.microsoft.com/library/windows/desktop/aa367040) en *MIDL Reference \(*Referencia del lenguaje MIDL*\)*.  
  
 **helpcontext**  
 Especifica un identificador de contexto que permite al usuario ver información sobre esta propiedad en el archivo de Ayuda.  Vea [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851) en *MIDL Reference \(*Referencia del lenguaje MIDL*\)*.  
  
 **helpstring**  
 Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.  De forma predeterminada, toma el valor "property *Nombre de propiedad*". Vea [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856) en *MIDL Reference \(*Referencia del lenguaje MIDL*\)*.  
  
## Otras opciones  
 No todas las opciones están disponibles para todos los tipos de propiedades:  
  
|Opción|Descripción|  
|------------|-----------------|  
|**bindable**|Indica que la propiedad admite enlace de datos.  Vea [bindable](http://msdn.microsoft.com/library/windows/desktop/aa366738) en *MIDL Reference \(*Referencia del lenguaje MIDL*\)*.  Esta opción está activada de forma predeterminada para la implementación estándar de la propiedad y no se puede cambiar.|  
|**defaultbind**|Indica que ésta es la única propiedad enlazable que representa óptimamente al objeto.  Vea [defaultbind](http://msdn.microsoft.com/library/windows/desktop/aa366790) en *MIDL Reference* \(Referencia del lenguaje MIDL*\)*.|  
|**displaybind**|Indica que esta propiedad se le deberá mostrar al usuario como enlazable.  Vea [displaybind](http://msdn.microsoft.com/library/windows/desktop/aa366804) en *MIDL Reference* \(Referencia del lenguaje MIDL\).|  
|**immediatebind**|Indica que la base de datos recibirá notificación inmediata de cualquier cambio en esta propiedad de un objeto enlazado a datos.  Vea [immediatebind](http://msdn.microsoft.com/library/windows/desktop/aa367045) en *MIDL Reference* \(Referencia del lenguaje MIDL\).|  
|**defaultcollelem**|Indica que la propiedad es una función de descriptor de acceso de un elemento de la colección predeterminada.  Vea [defaultcollelem](http://msdn.microsoft.com/library/windows/desktop/aa366792) en *MIDL Reference* \(Referencia del lenguaje MIDL\).|  
|**nonbrowsable**|Etiqueta un miembro de interfaz o dispinterface para que no se muestre en un explorador de propiedades.  Vea [nonbrowsable](http://msdn.microsoft.com/library/windows/desktop/aa367117) en *MIDL Reference* \(Referencia del lenguaje MIDL\).|  
|**requestedit**|Indica que la propiedad admite la notificación **OnRequestEdit**. Vea [requestedit](http://msdn.microsoft.com/library/windows/desktop/aa367155) en *MIDL Reference \(*Referencia del lenguaje MIDL*\)*.  Esta opción está activada de forma predeterminada para la implementación estándar de la propiedad y no se puede cambiar.|  
|**source**|Indica que un miembro de la propiedad es un origen de eventos.  Vea [source](http://msdn.microsoft.com/library/windows/desktop/aa367166) en *MIDL Reference* \(Referencia del lenguaje MIDL\).|  
|**hidden**|Indica que, aunque la propiedad existe, no deberá mostrarse en exploradores orientados al usuario.  Vea [hidden](http://msdn.microsoft.com/library/windows/desktop/aa366861) en *MIDL Reference* \(Referencia del lenguaje MIDL\).|  
|**restricted**|Especifica que no se puede llamar a la propiedad arbitrariamente.  Vea [restricted](http://msdn.microsoft.com/library/windows/desktop/aa367157) en *MIDL Reference* \(Referencia del lenguaje MIDL\).|  
|`local`|Especifica al compilador MIDL que la propiedad no es remota.  Vea [local](http://msdn.microsoft.com/library/windows/desktop/aa367071) en *MIDL Reference* \(Referencia del lenguaje MIDL\).|  
  
## Vea también  
 [Agregar una propiedad](../ide/adding-a-property-visual-cpp.md)   
 [Nombres, Asistente para agregar propiedades](../ide/names-add-property-wizard.md)   
 [Implementar una interfaz](../ide/implementing-an-interface-visual-cpp.md)   
 [Propiedades estándar](../ide/stock-properties.md)