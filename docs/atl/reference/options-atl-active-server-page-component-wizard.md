---
title: Opciones, Asistente para componentes de páginas Active Server ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.asp.options
helpviewer_keywords:
- ATL Active Server Page Component Wizard, options
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
ms.openlocfilehash: c76ab7730256b007b66d54ca6753409926f7ae89
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495300"
---
# <a name="options-atl-active-server-page-component-wizard"></a>Opciones, Asistente para componentes de páginas Active Server ATL

Use esta página del Asistente para componentes de páginas de Active Server ATL para diseñar una mayor eficiencia y compatibilidad con errores para el objeto.

Para obtener más información sobre los proyectos ATL y las clases COM de ATL, vea [Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md).

- **Modelo de subprocesos**

   Indica el método para administrar los subprocesos. De forma predeterminada, el proyecto utiliza el subprocesamiento **controlado** .

   Consulte el artículo sobre [cómo especificar el modelo de subprocesos del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md) para obtener más información.

   |Opción|DESCRIPCIÓN|
   |------------|-----------------|
   |**Single**|Especifica que el objeto utiliza el modelo de subprocesos único. En el modelo de subproceso único, un objeto siempre se ejecuta en el subproceso COM principal. Consulte [apartamentos de un solo subproceso](/windows/win32/com/single-threaded-apartments) y [InProcServer32](/windows/win32/com/inprocserver32) para obtener más información.|
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

- **Soporte técnico**

   Opciones de soporte técnico adicionales:

   |Opción|DESCRIPCIÓN|
   |------------|-----------------|
   |**ISupportErrorInfo**|Crea compatibilidad con la interfaz [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) para que el objeto pueda devolver información de error al cliente.|
   |**Puntos de conexión**|Habilita los puntos de conexión para el objeto haciendo que la clase del objeto se derive de [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|
   |**Contador de referencias de subprocesamiento libre**|Crea un objeto de cálculo de referencias de subprocesamiento libre para calcular las referencias de los punteros de interfaz de forma eficaz entre los subprocesos del mismo proceso. Disponible para el objeto que especifica **tanto** como el modelo de subprocesos como **gratuito** .|

## <a name="see-also"></a>Vea también

[Asistente para componentes de páginas Active Server ATL](../../atl/reference/atl-active-server-page-component-wizard.md)<br/>
[Componente de páginas Active Server ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)
