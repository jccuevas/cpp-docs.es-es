---
title: 'Controles ActiveX MFC: Métodos | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93a8d3f9840afd88a9ce0ae7cbaf661babc13647
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46406053"
---
# <a name="mfc-activex-controls-methods"></a>Controles ActiveX MFC: Métodos

Un control ActiveX desencadena eventos para comunicarse entre sí y su contenedor. Un contenedor también puede comunicarse con un control por medio de métodos y propiedades. Los métodos también se denominan funciones.

Métodos y propiedades proporcionan una interfaz exportada para su uso por otras aplicaciones, como los clientes de automatización y contenedores de controles ActiveX. Para obtener más información sobre las propiedades de controles ActiveX, vea el artículo [controles ActiveX MFC: propiedades](../mfc/mfc-activex-controls-properties.md).

Los métodos son similares en uso y propósito a las funciones miembro de una clase de C++. Hay dos tipos de métodos que puede implementar el control: estándar y personalizados. Similares a los eventos estándar, los métodos estándar son aquellos métodos que [COleControl](../mfc/reference/colecontrol-class.md) proporciona una implementación. Para obtener más información sobre métodos estándar, vea el artículo [controles ActiveX MFC: agregar métodos estándar](../mfc/mfc-activex-controls-adding-stock-methods.md). Los métodos personalizados definidos por el programador, permiten una mayor personalización del control. Para obtener más información, vea el artículo [controles ActiveX MFC: agregar métodos personalizados](../mfc/mfc-activex-controls-adding-custom-methods.md).

La biblioteca de clases (MFC) de Microsoft Foundation implementa un mecanismo que permite el control admitir métodos estándar y personalizados. La primera parte es la clase `COleControl`. Deriva `CWnd`, `COleControl` las funciones miembro admiten métodos estándar que son comunes a todos los controles ActiveX. La segunda parte de este mecanismo es el mapa de envíos. Un mapa de envíos es similar a un mapa de mensajes; Sin embargo, en lugar de una función de asignación a un identificador de mensaje de Windows, un mapa de envíos asigna las funciones miembro virtuales a identificadores IDispatch.

Para que un control admitir varios métodos correctamente, su clase debe declarar un mapa de envíos. Esto se consigue mediante la siguiente línea de código que se encuentra en archivos de encabezado (. H) archivo de:

[!code-cpp[NVC_MFC_AxUI#13](../mfc/codesnippet/cpp/mfc-activex-controls-methods_1.h)]

El propósito principal del mapa de envíos es establecer la relación entre los nombres de método utilizados por un llamador externo (por ejemplo, el contenedor) y las funciones miembro de clase del control que implementan los métodos. Después de que se ha declarado el mapa de envíos, debe definirse en la implementación del control (. Archivo CPP). Las líneas de código siguientes definen el mapa de envíos:

[!code-cpp[NVC_MFC_AxUI#14](../mfc/codesnippet/cpp/mfc-activex-controls-methods_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#15](../mfc/codesnippet/cpp/mfc-activex-controls-methods_3.cpp)]

Si ha usado el [Asistente para controles ActiveX de MFC](../mfc/reference/mfc-activex-control-wizard.md) para crear el proyecto, estas líneas se agregaron automáticamente. Si no se utilizó el Asistente para controles de ActiveX de MFC, debe agregarlas manualmente.

Los siguientes artículos describen métodos con detalle:

- [Controles ActiveX MFC: Agregar métodos estándar](../mfc/mfc-activex-controls-adding-stock-methods.md)

- [Controles ActiveX MFC: Agregar métodos personalizados](../mfc/mfc-activex-controls-adding-custom-methods.md)

- [Controles ActiveX MFC: Devolver códigos de error desde un método](../mfc/mfc-activex-controls-returning-error-codes-from-a-method.md)

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

