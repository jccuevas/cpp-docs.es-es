---
title: 'Controles ActiveX MFC: Propiedades'
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
- properties [MFC]
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
ms.openlocfilehash: 5e01854e7ae7acdc33275351d0d26a76dfeabc9b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326418"
---
# <a name="mfc-activex-controls-properties"></a>Controles ActiveX MFC: Propiedades

Un control ActiveX activa eventos para comunicarse con su contenedor. El contenedor, en cambio, utiliza los métodos y propiedades para comunicarse con el control. Propiedades y métodos son similares en uso y propósito, respectivamente, para las funciones miembro y variables de miembro de una clase de C++. Las propiedades son miembros de datos del control ActiveX que se exponen a cualquier contenedor. Las propiedades proporcionan una interfaz para las aplicaciones que contienen controles ActiveX, como los clientes de automatización y contenedores de controles ActiveX.

Las propiedades también se denominan atributos.

Para obtener más información sobre los métodos del control ActiveX, vea el artículo [controles ActiveX MFC: Métodos](../mfc/mfc-activex-controls-methods.md).

Controles ActiveX pueden implementar las existencias y métodos y propiedades personalizados. Clase `COleControl` proporciona una implementación de propiedades estándar. (Para obtener una lista completa de propiedades estándar, vea el artículo [controles ActiveX MFC: Agregar propiedades estándar](../mfc/mfc-activex-controls-adding-stock-properties.md).) Propiedades personalizadas, definidas por el desarrollador, agregar capacidades especializadas a un control ActiveX. Para obtener más información, consulte [controles ActiveX MFC: Agregar propiedades personalizadas](../mfc/mfc-activex-controls-adding-custom-properties.md).

Se admiten las propiedades estándar y personalizadas, como los métodos, mediante un mecanismo que consta de un mapa de envíos que controla las propiedades y métodos y funciones de miembro existente de la `COleControl` clase. Además, estas propiedades pueden tener parámetros que el programador usa para pasar información adicional al control.

Los siguientes artículos describen las propiedades del control ActiveX con más detalle:

- [Controles ActiveX MFC: Agregar propiedades estándar](../mfc/mfc-activex-controls-adding-stock-properties.md)

- [Controles ActiveX MFC: Agregar propiedades personalizadas](../mfc/mfc-activex-controls-adding-custom-properties.md)

- [Controles ActiveX MFC: Implementación de propiedades avanzadas](../mfc/mfc-activex-controls-advanced-property-implementation.md)

- [Controles ActiveX MFC: Obtener acceso a las propiedades de ambiente](../mfc/mfc-activex-controls-accessing-ambient-properties.md)

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)
