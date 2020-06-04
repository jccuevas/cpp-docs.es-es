---
title: Opciones, Asistente para páginas de propiedades ATL
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.options
helpviewer_keywords:
- ATL Property Page Wizard, options
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
ms.openlocfilehash: a46a55cca221293e83a72bf0c2670e2343c744b0
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076210"
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
   |**Único**|La página de propiedades se ejecuta solo en el subproceso COM principal.|
   |**Apartment**|La página de propiedades se puede crear en cualquier apartamento de un único subproceso. El valor predeterminado.|

- **Agregación**

   Agrega compatibilidad con la agregación para la página de propiedades que está creando. Consulte [Agregación](../../atl/aggregation.md) para obtener más información.

   |Opción|Descripción|
   |------------|-----------------|
   |**Sí**|Cree una página de propiedades que se pueda agregar.|
   |**No**|Cree una página de propiedades que no se pueda agregar.|
   |**Solo**|Cree una página de propiedades de la que se puedan crear instancias a través de la agregación.|

::: moniker-end

## <a name="see-also"></a>Consulte también

[Asistente para páginas de propiedades ATL](../../atl/reference/atl-property-page-wizard.md)<br/>
[Cadenas, Asistente para páginas de propiedades ATL](../../atl/reference/strings-atl-property-page-wizard.md)
