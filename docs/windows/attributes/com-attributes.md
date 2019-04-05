---
title: Atributos COM
ms.date: 10/03/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
ms.openlocfilehash: eb87d3861c6b3066cf482108e2ce2243c8196093
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038934"
---
# <a name="com-attributes"></a>Atributos COM

Los atributos COM insertan código para admitir numerosas áreas de desarrollo de COM y el desarrollo de .NET Framework common language runtime. Estas van de áreas de implementación de interfaz personalizada y soporte técnico de las interfaces existentes para admitir los eventos, métodos y propiedades estándar. Además, se puede buscar soporte para la composición y la implementación del control ActiveX.

|Atributo|Descripción|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Indica que se puede agregar un control por otro control.|
|[agregados](aggregates.md)|Indica que un control agrega la clase de destino.|
|[coclase](coclass.md)|Crea un objeto COM, que puede implementar una interfaz COM.|
|[com_interface_entry](com-interface-entry-cpp.md)|Agrega una entrada de la interfaz a un mapa COM.|
|[implements_category](implements-category.md)|Especifica las categorías de componentes implementados para la clase.|
|[progid](progid.md)|Define el ProgID de un control.|
|[rdx](rdx.md)|Crea o modifica una clave del registro.|
|[registration_script](registration-script.md)|Ejecuta el script de registro especificado.|
|[requires_category](requires-category.md)|Especifica las categorías de los componentes necesarios para la clase.|
|[support_error_info](support-error-info.md)|Admite informes de errores para el objeto de destino.|
|[synchronize](synchronize.md)|Sincroniza el acceso a un método.|
|[subprocesamiento](threading-cpp.md)|Especifica el modelo de subprocesos para un objeto COM.|
|[vi_progid](vi-progid.md)|Define un ProgID independientes de la versión de un control.|

## <a name="see-also"></a>Vea también

[Atributos por grupo](attributes-by-group.md)