---
title: Opciones, Asistente para componentes de páginas de Active Server ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.asp.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Active Server Page Component Wizard, options
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cdd3e62915b81311450cf4d798b04f8df30492ff
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884605"
---
# <a name="options-atl-active-server-page-component-wizard"></a>Opciones, Asistente para componentes de páginas Active Server ATL
Use esta página del Asistente para componentes de páginas Active Server ATL para el diseño para una mayor eficiencia y soporte técnico de error para el objeto.  
  
 Para obtener más información sobre los proyectos ATL y clases COM de ATL, vea [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md).  
  
 **Modelo de subprocesos**  
 Indica el método de administración de subprocesos. De forma predeterminada, el proyecto usa **apartamento** subprocesamiento.  
  
 Consulte [especificar el modelo de subprocesamiento del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md) para obtener más información.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Single**|Especifica que el objeto utiliza el modelo de subprocesamiento único. En el modelo de subprocesamiento único, un objeto siempre se ejecuta en el subproceso COM principal. Consulte [contenedores uniproceso](http://msdn.microsoft.com/library/windows/desktop/ms680112) y [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) para obtener más información.|  
|**Apartamento**|Especifica que el objeto utiliza el apartamento de subproceso. Apartamento de subproceso equivalente al único. Se asigna a cada objeto de un componente de subprocesamiento controlado un apartamento de subproceso, durante la vida del objeto; Sin embargo, varios subprocesos pueden usarse para varios objetos. Cada contenedor está asociado a un subproceso concreto y tiene un bombeo de mensajes de Windows (valor predeterminado).<br /><br /> Consulte [contenedores uniproceso](http://msdn.microsoft.com/library/windows/desktop/ms680112) para obtener más información.|  
|**Ambos**|Especifica que el objeto puede usar apartamento o subprocesamiento libre, dependiendo del tipo de un subproceso creado.|  
|**gratis**|Especifica que el objeto usa el subprocesamiento libre. Subprocesamiento libre es equivalente a un modelo de apartamento multiproceso. Consulte [apartamentos multiproceso](http://msdn.microsoft.com/library/windows/desktop/ms693421) para obtener más información.|  
|**Neutral**|Especifica que el objeto sigue las directrices para apartamentos multiproceso, pero pueden ejecutar en cualquier tipo de subproceso.|  
  
 **Agregación**  
 Indica si el objeto usa [agregación](http://msdn.microsoft.com/library/windows/desktop/ms686558). El objeto agregado elige qué interfaces se expondrán a los clientes y las interfaces se exponen como si el objeto agregado implementarlos. Los clientes del objeto agregado comunicarse solo con el objeto agregado.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Sí**|Especifica que se puede agregar el objeto. El valor predeterminado.|  
|**No**|Especifica que no se agrega el objeto.|  
|**Solo**|Especifica que debe agregarse el objeto.|  
  
 **Soporte técnico**  
 (Se puede agregar una descripción del elemento)  
  
|Opción|Descripción|  
|------------|-----------------|  
|`ISupportErrorInfo`|Crea la compatibilidad con la [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) interfaz para que el objeto puede devolver información de error al cliente.|  
|**Puntos de conexión**|Permite a los puntos de conexión para el objeto mediante la realización de derivar de la clase del objeto [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|  
|**Contador de referencias de subprocesamiento libre**|Crea un objeto de contador de referencias de subprocesamiento libre para calcular referencias de punteros de interfaz eficazmente entre los subprocesos en el mismo proceso. Disponible para el objeto que especifica ya sea **ambos** o **gratis** como el modelo de subprocesos.|  
  
## <a name="see-also"></a>Vea también  
 [Asistente para componentes de páginas de Active Server ATL](../../atl/reference/atl-active-server-page-component-wizard.md)   
 [Componente de páginas Active Server ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)

