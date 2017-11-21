---
title: "Opciones, Asistente para componentes de páginas de Active Server ATL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.asp.options
dev_langs: C++
helpviewer_keywords: ATL Active Server Page Component Wizard, options
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8bba50b9d9859039c34532ed2a4fba189db48374
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="options-atl-active-server-page-component-wizard"></a>Opciones, Asistente para componentes de páginas Active Server ATL
Use esta página del Asistente para componentes de páginas Active Server ATL para diseñar para una mayor eficiencia y soporte técnico de error para el objeto.  
  
 Para obtener más información sobre ATL (proyectos) y las clases COM de ATL, vea [componentes de escritorio ATL COM](../../atl/atl-com-desktop-components.md).  
  
 **Modelo de subprocesos**  
 Indica el método de administración de subprocesos. De forma predeterminada, el proyecto utiliza **apartamento** subprocesamiento.  
  
 Vea [especificar el modelo de subprocesamiento del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md) para obtener más información.  
  
|Opción|Descripción|  
|------------|-----------------|  
|`Single`|Especifica que el objeto utiliza el modelo de subprocesamiento único. En el modelo de subprocesamiento único, un objeto siempre se ejecuta en el subproceso COM principal. Vea [los contenedores uniproceso](http://msdn.microsoft.com/library/windows/desktop/ms680112) y [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) para obtener más información.|  
|**Apartamento**|Especifica que el objeto utiliza apartamento de subproceso. Apartamento de subproceso equivalente al único. Cada objeto de un componente de subprocesamiento controlado se le asigna un apartamento para su subproceso, durante la vida del objeto; Sin embargo, varios subprocesos pueden utilizarse para varios objetos. Cada contenedor está asociado a un subproceso concreto y tiene un suministro de mensajes de Windows (valor predeterminado).<br /><br /> Vea [los contenedores uniproceso](http://msdn.microsoft.com/library/windows/desktop/ms680112) para obtener más información.|  
|**Ambos**|Especifica que el objeto puede usar apartamento o subprocesamiento libre, dependiendo de qué tipo de un subproceso se crea.|  
|**Libre**|Especifica que el objeto utiliza subprocesamiento libre. Subprocesamiento libre equivale a un modelo de apartamento multiproceso. Vea [apartamentos multiproceso](http://msdn.microsoft.com/library/windows/desktop/ms693421) para obtener más información.|  
|**Neutral** (sólo Windows 2000)|Especifica que el objeto sigue las directrices para apartamentos multiproceso, pero pueden ejecutar en cualquier tipo de subproceso.|  
  
 **Agregación**  
 Indica si el objeto utiliza [agregaciones](http://msdn.microsoft.com/library/windows/desktop/ms686558). El objeto agregado elige qué interfaces se expondrán a los clientes y las interfaces se exponen como si el objeto agregado implementarlos. Los clientes del objeto agregado se comunican con el objeto agregado.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Sí**|Especifica que se puede agregar el objeto. El valor predeterminado.|  
|**No**|Especifica que no se agrega el objeto.|  
|**Solo**|Especifica que debe agregarse el objeto.|  
  
 **Soporte técnico**  
 (Se agrega una descripción del elemento)  
  
|Opción|Descripción|  
|------------|-----------------|  
|**ISupportErrorInfo**|¡Crea compatibilidad con la [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) interfaz para el objeto pueda devolver información de error al cliente.|  
|**Puntos de conexión**|Habilita puntos de conexión para el objeto mediante la realización de la clase del objeto deriva [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|  
|**Contador de referencias de subprocesamiento libre**|Crea un objeto de contador de referencias de subprocesamiento libre para calcular las referencias de punteros de interfaz eficazmente entre subprocesos en el mismo proceso. Disponibles para especificar el objeto **ambos** o **libre** como el modelo de subprocesos.|  
  
## <a name="see-also"></a>Vea también  
 [Asistente para componentes de páginas de Active Server ATL](../../atl/reference/atl-active-server-page-component-wizard.md)   
 [Componentes de páginas Active Server ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)

