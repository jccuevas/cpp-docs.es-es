---
title: Opciones, Asistente para páginas de propiedades ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.ppg.options
helpviewer_keywords:
- ATL Property Page Wizard, options
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
ms.openlocfilehash: c92c7a3f03c3ddedbea02647e2317d77a7655609
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298989"
---
# <a name="options-atl-property-page-wizard"></a>Opciones, Asistente para páginas de propiedades ATL

Utilice esta página del Asistente para definir el nivel de agregación y de modelo de subprocesamiento de página de propiedades que se va a crear.

- **Modelo de subprocesos**

   Especifica el modelo de subprocesos utilizado por la página de propiedades.

   Consulte [especificar el modelo de subprocesamiento del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md) para obtener más información.

   |Opción|Descripción|
   |------------|-----------------|
   |**Single**|La página de propiedades solo se ejecuta en el subproceso COM principal.|
   |**Apartment**|La página de propiedades puede crearse en cualquier apartamento de subproceso único. El valor predeterminado.|

- **Agregación**

   Agrega compatibilidad con la agregación para la página de propiedades que se va a crear. Consulte [agregación](../../atl/aggregation.md) para obtener más información.

   |Opción|Descripción|
   |------------|-----------------|
   |**Sí**|Crear una página de propiedades que se puede agregar.|
   |**No**|Crear una página de propiedades que no se puede agregar.|
   |**Solo**|Crear una página de propiedades que solo se puede crear instancias mediante agregación.|

## <a name="see-also"></a>Vea también

[Asistente para páginas de propiedades ATL](../../atl/reference/atl-property-page-wizard.md)<br/>
[Cadenas, Asistente para páginas de propiedades ATL](../../atl/reference/strings-atl-property-page-wizard.md)
