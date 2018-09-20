---
title: Atributos COM | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 71ff4e3fdb80b48e306e543bdb683c3dd2b26ec3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443337"
---
# <a name="com-attributes"></a>Atributos COM
Los atributos COM insertan código para admitir numerosas áreas de desarrollo de COM y el desarrollo de .NET Framework common language runtime. Estas van de áreas de implementación de interfaz personalizada y soporte técnico de las interfaces existentes para admitir los eventos, métodos y propiedades estándar. Además, se puede buscar soporte para la composición y la implementación del control ActiveX.
  
|Atributo|Descripción|
|---------------|-----------------|
|[aggregatable](../windows/aggregatable.md)|Indica que se puede agregar un control por otro control.|
|[aggregates](../windows/aggregates.md)|Indica que un control agrega la clase de destino.|
|[coclass](../windows/coclass.md)|Crea un objeto COM, que puede implementar una interfaz COM.|
|[COM_INTERFACE_ENTRY](../windows/com-interface-entry-cpp.md)|Agrega una entrada de la interfaz a un mapa COM.|
|[implements_category](../windows/implements-category.md)|Especifica las categorías de componentes implementados para la clase.|
|[progid](../windows/progid.md)|Define el ProgID de un control.|
|[rdx](../windows/rdx.md)|Crea o modifica una clave del registro.|
|[registration_script](../windows/registration-script.md)|Ejecuta el script de registro especificado.|
|[requires_category](../windows/requires-category.md)|Especifica las categorías de los componentes necesarios para la clase.|
|[support_error_info](../windows/support-error-info.md)|Admite informes de errores para el objeto de destino.|
|[synchronize](../windows/synchronize.md)|Sincroniza el acceso a un método.|
|[Subprocesamiento](../windows/threading-cpp.md)|Especifica el modelo de subprocesos para un objeto COM.|
|[vi_progid](../windows/vi-progid.md)|Define un ProgID independientes de la versión de un control.|
  
## <a name="see-also"></a>Vea también

[Atributos por grupo](../windows/attributes-by-group.md)