---
title: Atributos COM
ms.date: 10/03/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
ms.openlocfilehash: 15225d23abb66b8aadd5f82b8429334356bdaa8d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168322"
---
# <a name="com-attributes"></a>Atributos COM

Los atributos COM insertan código para admitir numerosas áreas de desarrollo COM y .NET Framework Common Language Runtime desarrollo. Estas áreas van desde la implementación de la interfaz personalizada y la compatibilidad con las interfaces existentes para admitir propiedades, métodos y eventos estándar. Además, se puede encontrar compatibilidad con la implementación de controles compuestos y ActiveX.

|Atributo|Descripción|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Indica que otro control puede Agregar un control.|
|[aggregates](aggregates.md)|Indica que un control agrega la clase de destino.|
|[coclass](coclass.md)|Crea un objeto COM, que puede implementar una interfaz COM.|
|[com_interface_entry](com-interface-entry-cpp.md)|Agrega una entrada de interfaz a un mapa COM.|
|[implements_category](implements-category.md)|Especifica las categorías de componentes implementados para la clase.|
|[progid](progid.md)|Define el identificador de programa (ProgID) para un control.|
|[rdx](rdx.md)|Crea o modifica una clave del registro.|
|[registration_script](registration-script.md)|Ejecuta el script de registro especificado.|
|[requires_category](requires-category.md)|Especifica las categorías de componentes necesarias para la clase.|
|[support_error_info](support-error-info.md)|Admite informes de errores para el objeto de destino.|
|[synchronize](synchronize.md)|Sincroniza el acceso a un método.|
|[threading](threading-cpp.md)|Especifica el modelo de subprocesos para un objeto COM.|
|[vi_progid](vi-progid.md)|Define un ProgID independiente de la versión para un control.|

## <a name="see-also"></a>Consulte también

[Atributos por grupo](attributes-by-group.md)
