---
title: Opciones, Asistente para objetos simples ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.simple.options
helpviewer_keywords:
- ATL Simple Object Wizard, options
ms.assetid: 125fe179-942d-4181-8b82-33e92e1fd779
ms.openlocfilehash: e92f4909907645fc317590fbcc3601887346c642
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495156"
---
# <a name="options-atl-simple-object-wizard"></a>Opciones, Asistente para objetos simples ATL

Utilice esta página del Asistente para objetos simples ATL para diseñar una mayor eficiencia y compatibilidad con errores para el objeto.

Para obtener más información sobre los proyectos ATL y las clases COM de ATL, vea [Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md).

- **Modelo de subprocesos**

   Indica el método para administrar los subprocesos. De forma predeterminada, el proyecto utiliza el subprocesamiento **controlado** .

   Consulte el artículo sobre [cómo especificar el modelo de subprocesos del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md) para obtener más información.

   |Opción|DESCRIPCIÓN|
   |------------|-----------------|
   |**Single**|Especifica que el objeto siempre se ejecuta en el subproceso COM principal. Consulte [apartamentos de un solo subproceso](/windows/win32/com/single-threaded-apartments) y [InProcServer32](/windows/win32/com/inprocserver32) para obtener más información.|
   |**Apartment**|Especifica que el objeto utiliza el subprocesamiento de apartamento. Equivalente al apartamento de un solo subproceso. A cada objeto de un componente de subproceso controlado se le asigna un apartamento para su subproceso, mientras dure el objeto; sin embargo, se pueden utilizar varios subprocesos para varios objetos. Cada apartamento está ligada a un subproceso específico y tiene un bombeo de mensajes de Windows (valor predeterminado).<br /><br /> Consulte [apartamentos de un solo subproceso](/windows/win32/com/single-threaded-apartments) para obtener más información.|
   |**Ambos**|Especifica que el objeto puede utilizar el subprocesamiento controlado o libre, en función del tipo de un subproceso que se cree.|
   |**Gratis**|Especifica que el objeto utiliza el subprocesamiento libre. El subprocesamiento libre es equivalente a un modelo de Apartamento multiproceso. Para obtener más información, consulte [apartamentos multiproceso](/windows/win32/com/multithreaded-apartments) .|
   |**Neutral**|Especifica que el objeto sigue las instrucciones para apartamentos multiproceso, pero puede ejecutarse en cualquier tipo de subproceso.|

- **Agregación**

   Indica si el objeto utiliza la [agregación](/windows/win32/com/aggregation). El objeto agregado elige qué interfaces se exponen a los clientes, y las interfaces se exponen como si el objeto agregado las implementa. Los clientes del objeto agregado solo se comunican con el objeto agregado.

   |Opción|DESCRIPCIÓN|
   |------------|-----------------|
   |**Sí**|Especifica que el objeto se puede Agregar. El valor predeterminado.|
   |**No**|Especifica que el objeto no se agrega.|
   |**Solo**|Especifica que debe agregarse el objeto.|

- **Interface**

   Indica el tipo de interfaz que admite el objeto. De forma predeterminada, el objeto admite una interfaz dual.

   |Opción|DESCRIPCIÓN|
   |------------|-----------------|
   |**Dual**|Especifica que el objeto admite una interfaz dual (su vtable tiene funciones de interfaz personalizadas más métodos de `IDispatch` enlace en tiempo de ejecución). Permite a los clientes COM y a los [controladores de automatización](../../mfc/automation-clients.md) tener acceso al objeto. El valor predeterminado.|
   |**Personalizada**|Especifica que el objeto admite una interfaz personalizada (su tabla virtual tiene funciones de interfaz personalizadas). Una interfaz personalizada puede ser más rápida que una interfaz dual, especialmente entre los límites de procesos.<br /><br /> - **Compatible con Automation** Permite a los controladores de automatización tener acceso a un objeto que tiene la compatibilidad con la interfaz personalizada.|

- **Soporte técnico**

   Indica compatibilidad adicional para el objeto.

   |Opción|DESCRIPCIÓN|
   |------------|-----------------|
   |**ISupportErrorInfo**|Crea compatibilidad con la interfaz [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) para que el objeto pueda devolver información de error al cliente.|
   |**Puntos de conexión**|Habilita los puntos de conexión para el objeto haciendo que la clase del objeto se derive de [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|
   |**Contador de referencias de subprocesamiento libre**|Crea un objeto de cálculo de referencias de subprocesamiento libre para calcular las referencias de los punteros de interfaz de forma eficaz entre los subprocesos del mismo proceso. Disponible para el **objeto que especifica como modelo** de subprocesos.|
   |**IObjectWithSite** (Compatibilidad con objetos de IE)|Implementa [IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md), que proporciona una manera sencilla de admitir la comunicación entre un objeto y su sitio en un contenedor.|

## <a name="see-also"></a>Vea también

[Asistente para objetos simples ATL](../../atl/reference/atl-simple-object-wizard.md)<br/>
[Objeto simple ATL](../../atl/reference/adding-an-atl-simple-object.md)<br/>
[Problemas de subprocesos de servidor en proceso](/windows/win32/com/in-process-server-threading-issues)
