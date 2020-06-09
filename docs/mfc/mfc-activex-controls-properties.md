---
title: 'Controles ActiveX MFC: Propiedades'
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
- properties [MFC]
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
ms.openlocfilehash: c7ed0fddea660409f5089159b71d39a29b01d538
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618179"
---
# <a name="mfc-activex-controls-properties"></a>Controles ActiveX MFC: Propiedades

Un control ActiveX desencadena eventos para comunicarse con el contenedor de control. El contenedor, a su vez, usa métodos y propiedades para comunicarse con el control. Los métodos y las propiedades son similares en uso y propósito, respectivamente, a las funciones miembro y a las variables miembro de una clase de C++. Las propiedades son miembros de datos del control ActiveX que se exponen a cualquier contenedor. Las propiedades proporcionan una interfaz para las aplicaciones que contienen controles ActiveX, como los clientes de automatización y los contenedores de controles ActiveX.

Las propiedades también se denominan atributos.

Para obtener más información sobre los métodos de control ActiveX, vea el artículo [controles ActiveX MFC: métodos](mfc-activex-controls-methods.md).

Los controles ActiveX pueden implementar métodos y propiedades estándar y personalizados. La clase `COleControl` proporciona una implementación de propiedades estándar. (Para obtener una lista completa de las propiedades estándar, vea el artículo [controles ActiveX MFC: agregar propiedades estándar](mfc-activex-controls-adding-stock-properties.md)). Las propiedades personalizadas, definidas por el desarrollador, agregan funciones especializadas a un control ActiveX. Para obtener más información, vea [controles ActiveX MFC: agregar propiedades personalizadas](mfc-activex-controls-adding-custom-properties.md).

Tanto las propiedades personalizadas como las estándar, como los métodos, se admiten en un mecanismo que consta de un mapa de envíos que controla las propiedades y los métodos y las funciones miembro existentes de la `COleControl` clase. Además, estas propiedades pueden tener parámetros que el desarrollador utiliza para pasar información adicional al control.

En los siguientes artículos se describen con más detalle las propiedades de los controles ActiveX:

- [Controles ActiveX MFC: Agregar propiedades estándar](mfc-activex-controls-adding-stock-properties.md)

- [Controles ActiveX MFC: Agregar propiedades personalizadas](mfc-activex-controls-adding-custom-properties.md)

- [Controles ActiveX MFC: Implementación de propiedades avanzadas](mfc-activex-controls-advanced-property-implementation.md)

- [Controles ActiveX MFC: Acceso a las propiedades de ambiente](mfc-activex-controls-accessing-ambient-properties.md)

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)
