---
title: Opciones, Asistente para páginas de propiedades ATL
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.options
helpviewer_keywords:
- ATL Property Page Wizard, options
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
ms.openlocfilehash: c883b3e79bd857bb457da0a1bd540a08ddddf017
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524540"
---
# <a name="options-atl-property-page-wizard"></a>Opciones, Asistente para páginas de propiedades ATL


::: moniker range="vs-2019"

El Asistente para páginas de propiedades ATL no está disponible en Visual Studio 2019 ni en versiones posteriores.

::: moniker-end

::: moniker range="vs-2017"

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
