---
title: Atributos IDL, Asistente para agregar propiedades
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.prop.idlattributes
ms.assetid: 356ed666-79d0-4bd9-a5e7-cda679cbadbd
ms.openlocfilehash: d2a7448675be6a9d8cfc290d648413643aa4681c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514288"
---
# <a name="idl-attributes-add-property-wizard"></a>Atributos IDL, Asistente para agregar propiedades

Use esta página del Asistente para agregar propiedades para especificar la configuración de lenguaje de definición de interfaz (IDL) para la propiedad.

- **identificador**

   Establece el id. numérico que identifica la propiedad. Esta opción no está disponible para las propiedades de interfaces personalizadas. Vea [id](/windows/desktop/Midl/id) en la *Referencia de MIDL*.

- **helpcontext**

   Especifica un id. de contexto que permite al usuario ver información sobre esta propiedad en el archivo de ayuda. Vea [helpcontext](/windows/desktop/Midl/helpcontext) en la *Referencia de MIDL*.

- **helpstring**

   Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica. De forma predeterminada, se establece en "property *Nombre de la propiedad*". Vea [helpstring](/windows/desktop/Midl/helpstring) en la *Referencia de MIDL*.

## <a name="other-options"></a>Otras opciones

No todas las opciones están disponibles para todos los tipos de propiedad.

|Opción|Descripción|
|------------|-----------------|
|**bindable**|Indica que la propiedad admite enlace de datos. Vea [bindable](/windows/desktop/Midl/bindable) en la *Referencia de MIDL*. Para la implementación estándar de la propiedad, esta opción se establece de forma predeterminada y no se puede cambiar.|
|**defaultbind**|Indica que es la única propiedad enlazable que representa mejor el objeto. Vea [defaultbind](/windows/desktop/Midl/defaultbind) en la *Referencia de MIDL*.|
|**displaybind**|Indica que esta propiedad se debe mostrar al usuario como enlazable. Vea [displaybind](/windows/desktop/Midl/displaybind) en la *Referencia de MIDL*.|
|**immediatebind**|Indica que todos los cambios en esta propiedad de un objeto enlazado a datos se notificarán inmediatamente a la base de datos. Vea [immediatebind](/windows/desktop/Midl/immediatebind) en la *Referencia de MIDL*.|
|**defaultcollelem**|Indica que la propiedad es una función de descriptor de acceso para un elemento de la colección predeterminada. Vea [defaultcollelem](/windows/desktop/Midl/defaultcollelem) en la *Referencia de MIDL*.|
|**nonbrowsable**|Etiqueta un miembro de interfaz o interfaz dispinterface que no se debe mostrar en un explorador de propiedades. Vea [nonbrowsable](/windows/desktop/Midl/nonbrowsable) en la *Referencia de MIDL*.|
|**requestedit**|Indica que la propiedad admite la notificación **OnRequestEdit**. Vea [requestedit](/windows/desktop/Midl/requestedit) en la *Referencia de MIDL*. Para la implementación estándar de la propiedad, esta opción se establece de forma predeterminada y no se puede cambiar.|
|**source**|Indica que un miembro de la propiedad es un origen de eventos. Vea [source](/windows/desktop/Midl/source) en la *Referencia de MIDL*.|
|**hidden**|Indica que la propiedad existe pero que no se debe mostrar en un explorador orientado al usuario. Vea [hidden](/windows/desktop/Midl/hidden) en la *Referencia de MIDL*.|
|**restricted**|Especifica que la propiedad no se puede llamar de forma arbitraria. Vea [restricted](/windows/desktop/Midl/restricted) en la *Referencia de MIDL*.|
|`local`|Especifica al compilador MIDL que la propiedad no es remota. Vea [local](/windows/desktop/Midl/local) en la *Referencia de MIDL*.|

## <a name="see-also"></a>Vea también

[Agregar una propiedad](../ide/adding-a-property-visual-cpp.md)<br>
[Nombres, Asistente para agregar propiedades](../ide/names-add-property-wizard.md)<br>
[Implementar una interfaz](../ide/implementing-an-interface-visual-cpp.md)<br>
[Propiedades estándar](../ide/stock-properties.md)