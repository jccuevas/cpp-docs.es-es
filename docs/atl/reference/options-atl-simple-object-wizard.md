---
title: Opciones, Asistente para objetos simples ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.simple.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Simple Object Wizard, options
ms.assetid: 125fe179-942d-4181-8b82-33e92e1fd779
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36aab0177eaa62e5ec9601d9258c7de1a6ce7b59
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205695"
---
# <a name="options-atl-simple-object-wizard"></a>Opciones, Asistente para objetos simples ATL
Use esta página del Asistente para objetos simples ATL para el diseño para una mayor eficiencia y soporte técnico de error para el objeto.  
  
 Para obtener más información sobre los proyectos ATL y clases COM de ATL, vea [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md).  
  
 **Modelo de subprocesos**  
 Indica el método de administración de subprocesos. De forma predeterminada, el proyecto usa **apartamento** subprocesamiento.  
  
 Consulte [especificar el modelo de subprocesamiento del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md) para obtener más información.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Single**|Especifica que el objeto siempre se ejecuta en el subproceso COM principal. Consulte [contenedores uniproceso](/windows/desktop/com/single-threaded-apartments) y [InprocServer32](/windows/desktop/com/inprocserver32) para obtener más información.|  
|**Apartamento**|Especifica que el objeto utiliza el apartamento de subproceso. Apartamento de subproceso equivalente al único. Se asigna a cada objeto de un componente de subprocesamiento controlado un apartamento de subproceso, durante la vida del objeto; Sin embargo, varios subprocesos pueden usarse para varios objetos. Cada contenedor está asociado a un subproceso concreto y tiene un bombeo de mensajes de Windows (valor predeterminado).<br /><br /> Consulte [contenedores uniproceso](/windows/desktop/com/single-threaded-apartments) para obtener más información.|  
|**Ambos**|Especifica que el objeto puede usar apartamento o subprocesamiento libre, dependiendo del tipo de un subproceso creado.|  
|**gratis**|Especifica que el objeto usa el subprocesamiento libre. Subprocesamiento libre es equivalente a un modelo de apartamento multiproceso. Consulte [apartamentos multiproceso](/windows/desktop/com/multithreaded-apartments) para obtener más información.|  
|**Neutral**|Especifica que el objeto sigue las directrices para apartamentos multiproceso, pero pueden ejecutar en cualquier tipo de subproceso.|  
  
 **Agregación**  
 Indica si el objeto usa [agregación](/windows/desktop/com/aggregation). El objeto agregado elige qué interfaces se expondrán a los clientes y las interfaces se exponen como si el objeto agregado implementarlos. Los clientes del objeto agregado comunicarse solo con el objeto agregado.  
  
|Opción|Descripción|  
|------------|-----------------|  
|Sí|Especifica que se puede agregar el objeto. El valor predeterminado.|  
|No|Especifica que no se agrega el objeto.|  
|Únicamente|Especifica que debe agregarse el objeto.|  
  
 **Interface**  
 Indica el tipo de interfaz es compatible con el objeto. De forma predeterminada, el objeto admite una interfaz dual.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Dual**|Especifica que el objeto admite una interfaz dual (su tabla vtable posee funciones de interfaz personalizado y enlace tardío `IDispatch` métodos). Permite que los clientes COM y [controladores de automatización](../../mfc/automation-clients.md) para tener acceso al objeto. El valor predeterminado.|  
|**Custom**|Especifica que el objeto admite una interfaz personalizada (su tabla vtable tiene funciones de interfaz personalizada). Una interfaz personalizada puede ser más rápida que una interfaz dual, especialmente entre los límites del proceso.<br /><br /> -   **Compatible con automatización** controladores de automatización permite tener acceso a un objeto que tiene la compatibilidad de interfaz personalizado.|  
  
 **Soporte técnico**  
 Indica compatibilidad adicional para el objeto.  
  
|Opción|Descripción|  
|------------|-----------------|  
|`ISupportErrorInfo`|Crea la compatibilidad con la [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) interfaz para que el objeto puede devolver información de error al cliente.|  
|**Puntos de conexión**|Permite a los puntos de conexión para el objeto mediante la realización de derivar de la clase del objeto [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|  
|**Contador de referencias de subprocesamiento libre**|Crea un objeto de contador de referencias de subprocesamiento libre para calcular referencias de punteros de interfaz eficazmente entre los subprocesos en el mismo proceso. Disponible para especificar el objeto **ambos** como el modelo de subprocesos.|  
|`IObjectWithSite` **(Compatibilidad con objetos de Internet Explorer)**|Implementa [IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md), que proporciona una manera sencilla para admitir la comunicación entre un objeto y su sitio en un contenedor.|  
  
## <a name="see-also"></a>Vea también  
 [Asistente para objetos simples ATL](../../atl/reference/atl-simple-object-wizard.md)   
 [Objeto Simple ATL](../../atl/reference/adding-an-atl-simple-object.md)   
 [Problemas de subprocesamiento de servidor en proceso](/windows/desktop/com/in-process-server-threading-issues)

