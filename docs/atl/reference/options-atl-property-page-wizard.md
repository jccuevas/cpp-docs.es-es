---
title: Opciones, Asistente para páginas de propiedades ATL
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.options
helpviewer_keywords:
- ATL Property Page Wizard, options
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
ms.openlocfilehash: 205f6d3debafe22373355af12ef88c83d6a01911
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707001"
---
# <a name="options-atl-property-page-wizard"></a>Opciones, Asistente para páginas de propiedades ATL


::: moniker range="vs-2019"

El Asistente para páginas de propiedades ATL no está disponible en Visual Studio 2019 ni en versiones posteriores.

::: moniker-end

::: moniker range="<=vs-2017"

Use esta página del asistente para definir el modelo de subprocesos y el nivel de agregación de la página de propiedades que está creando.

- **Modelo de subprocesos**

   Especifica el modelo de subprocesos que usa la página de propiedades.

   Consulte el artículo sobre [cómo especificar el modelo de subprocesos del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md) para obtener más información.

   |Opción|Descripción|
   |------------|-----------------|
   |**Single**|La página de propiedades se ejecuta solo en el subproceso COM principal.|
   |**Apartment**|La página de propiedades se puede crear en cualquier apartamento de un único subproceso. El valor predeterminado.|

- **Agregación**

   Agrega compatibilidad con la agregación para la página de propiedades que está creando. Consulte [Agregación](../../atl/aggregation.md) para obtener más información.

   |Opción|Descripción|
   |------------|-----------------|
   |**Sí**|Cree una página de propiedades que se pueda agregar.|
   |**No**|Cree una página de propiedades que no se pueda agregar.|
   |**Solo**|Cree una página de propiedades de la que se puedan crear instancias a través de la agregación.|

::: moniker-end

## <a name="see-also"></a>Vea también

[Asistente para páginas de propiedades ATL](../../atl/reference/atl-property-page-wizard.md)<br/>
[Cadenas, Asistente para páginas de propiedades ATL](../../atl/reference/strings-atl-property-page-wizard.md)
