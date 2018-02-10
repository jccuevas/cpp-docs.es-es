---
title: Opciones, Asistente para objetos simples ATL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.simple.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Simple Object Wizard, options
ms.assetid: 125fe179-942d-4181-8b82-33e92e1fd779
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 37341dc23f95e1863aeae4a1b57c01d24d6ad365
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="options-atl-simple-object-wizard"></a>Opciones, Asistente para objetos simples ATL
Use esta página del Asistente para objetos simples ATL para diseñar para una mayor eficiencia y soporte técnico de error para el objeto.  
  
 Para obtener más información sobre ATL (proyectos) y las clases COM de ATL, vea [componentes de escritorio ATL COM](../../atl/atl-com-desktop-components.md).  
  
 **Modelo de subprocesos**  
 Indica el método de administración de subprocesos. De forma predeterminada, el proyecto utiliza **apartamento** subprocesamiento.  
  
 Vea [especificar el modelo de subprocesamiento del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md) para obtener más información.  
  
|Opción|Descripción|  
|------------|-----------------|  
|`Single`|Especifica que el objeto siempre se ejecuta en el subproceso COM principal. Vea [los contenedores uniproceso](http://msdn.microsoft.com/library/windows/desktop/ms680112) y [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) para obtener más información.|  
|**Apartment**|Especifica que el objeto utiliza apartamento de subproceso. Apartamento de subproceso equivalente al único. Cada objeto de un componente de subprocesamiento controlado se le asigna un apartamento para su subproceso, durante la vida del objeto; Sin embargo, varios subprocesos pueden utilizarse para varios objetos. Cada contenedor está asociado a un subproceso concreto y tiene un suministro de mensajes de Windows (valor predeterminado).<br /><br /> Vea [los contenedores uniproceso](http://msdn.microsoft.com/library/windows/desktop/ms680112) para obtener más información.|  
|**Both**|Especifica que el objeto puede usar apartamento o subprocesamiento libre, dependiendo de qué tipo de un subproceso se crea.|  
|**Libre**|Especifica que el objeto utiliza subprocesamiento libre. Subprocesamiento libre equivale a un modelo de apartamento multiproceso. Vea [apartamentos multiproceso](http://msdn.microsoft.com/library/windows/desktop/ms693421) para obtener más información.|  
|**Neutral**|Especifica que el objeto sigue las directrices para apartamentos multiproceso, pero pueden ejecutar en cualquier tipo de subproceso.|  
  
 **Agregación**  
 Indica si el objeto utiliza [agregaciones](http://msdn.microsoft.com/library/windows/desktop/ms686558). El objeto agregado elige qué interfaces se expondrán a los clientes y las interfaces se exponen como si el objeto agregado implementarlos. Los clientes del objeto agregado se comunican con el objeto agregado.  
  
|Opción|Descripción|  
|------------|-----------------|  
|Sí|Especifica que se puede agregar el objeto. El valor predeterminado.|  
|No|Especifica que no se agrega el objeto.|  
|Únicamente|Especifica que debe agregarse el objeto.|  
  
 **Interface**  
 Indica el tipo de interfaz sea compatible con el objeto. De forma predeterminada, el objeto admite una interfaz dual.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Dual**|Especifica que el objeto admite una interfaz dual (su tabla vtable posee funciones de interfaz personalizada y enlace tardío `IDispatch` métodos). Permite a los clientes COM y [controladores de automatización](../../mfc/automation-clients.md) para tener acceso al objeto. El valor predeterminado.|  
|**Custom**|Especifica que el objeto admite una interfaz personalizada (su tabla vtable posee funciones de interfaz personalizada). Una interfaz personalizada puede ser más rápida que una interfaz dual, especialmente en los límites de proceso.<br /><br /> -   **Compatible con automatización** controladores de automatización permite tener acceso a un objeto que tiene la compatibilidad de la interfaz personalizada.|  
  
 **Support**  
 Indica compatibilidad adicional para el objeto.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**ISupportErrorInfo**|¡Crea compatibilidad con la [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) interfaz para el objeto pueda devolver información de error al cliente.|  
|**Puntos de conexión**|Habilita puntos de conexión para el objeto mediante la realización de la clase del objeto deriva [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|  
|**Contador de referencias de subprocesamiento libre**|Crea un objeto de contador de referencias de subprocesamiento libre para calcular las referencias de punteros de interfaz eficazmente entre subprocesos en el mismo proceso. Disponible para especificar el objeto **tanto** como el modelo de subprocesos.|  
|**IObjectWithSite (compatibilidad con objetos de Internet Explorer)**|Implementa [IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md), que proporciona una manera sencilla para admitir la comunicación entre un objeto y su sitio en un contenedor.|  
  
## <a name="see-also"></a>Vea también  
 [Asistente para objetos simples ATL](../../atl/reference/atl-simple-object-wizard.md)   
 [Objeto Simple ATL](../../atl/reference/adding-an-atl-simple-object.md)   
 [Problemas de subprocesamiento de servidor en proceso](http://msdn.microsoft.com/library/windows/desktop/ms687205)

