---
title: 'Controles ActiveX MFC: Métodos'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
ms.openlocfilehash: 9f9ec06852ed0376583363df7649331a0be02105
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621234"
---
# <a name="mfc-activex-controls-methods"></a>Controles ActiveX MFC: Métodos

Un control ActiveX desencadena eventos para comunicarse entre sí mismo y su contenedor de control. Un contenedor también puede comunicarse con un control por medio de métodos y propiedades. Los métodos también se denominan funciones.

Los métodos y las propiedades proporcionan una interfaz exportada para su uso por parte de otras aplicaciones, como los clientes de automatización y los contenedores de controles ActiveX. Para obtener más información sobre las propiedades de los controles ActiveX, vea el artículo [controles ActiveX MFC: propiedades](mfc-activex-controls-properties.md).

Los métodos tienen un uso similar y el propósito de las funciones miembro de una clase de C++. Hay dos tipos de métodos que el control puede implementar: material y personalizado. De forma similar a los eventos estándar, los métodos estándar son aquellos para los que [COleControl](reference/colecontrol-class.md) proporciona una implementación. Para obtener más información sobre los métodos estándar, vea el artículo [controles ActiveX MFC: agregar métodos estándar](mfc-activex-controls-adding-stock-methods.md). Los métodos personalizados, definidos por el desarrollador, permiten la personalización adicional del control. Para obtener más información, vea el artículo [controles ActiveX MFC: agregar métodos personalizados](mfc-activex-controls-adding-custom-methods.md).

El biblioteca MFC (MFC) implementa un mecanismo que permite que el control admita los métodos estándar y de existencias. La primera parte es la clase `COleControl` . Derivada de `CWnd` , `COleControl` las funciones miembro admiten métodos estándar que son comunes a todos los controles ActiveX. La segunda parte de este mecanismo es el mapa de envío. Un mapa de envío es similar a un mapa de mensajes; sin embargo, en lugar de asignar una función a un identificador de mensaje de Windows, un mapa de envío asigna las funciones miembro virtuales a los IDENTIFICADOres IDispatch.

Para que un control admita varios métodos correctamente, su clase debe declarar un mapa de envío. Esto se logra mediante la siguiente línea de código ubicada en el encabezado de clase de control (. H):

[!code-cpp[NVC_MFC_AxUI#13](codesnippet/cpp/mfc-activex-controls-methods_1.h)]

El propósito principal del mapa de envío es establecer la relación entre los nombres de método utilizados por un llamador externo (como el contenedor) y las funciones miembro de la clase del control que implementan los métodos. Una vez declarado el mapa de envío, debe definirse en la implementación del control (. CPP). Las siguientes líneas de código definen el mapa de envío:

[!code-cpp[NVC_MFC_AxUI#14](codesnippet/cpp/mfc-activex-controls-methods_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#15](codesnippet/cpp/mfc-activex-controls-methods_3.cpp)]

Si utilizó el [Asistente para controles ActiveX de MFC](reference/mfc-activex-control-wizard.md) para crear el proyecto, estas líneas se agregaron automáticamente. Si no se ha utilizado el Asistente para controles ActiveX MFC, debe agregar estas líneas manualmente.

En los siguientes artículos se describen los métodos en detalle:

- [Controles ActiveX MFC: Agregar métodos estándar](mfc-activex-controls-adding-stock-methods.md)

- [Controles ActiveX MFC: Agregar métodos personalizados](mfc-activex-controls-adding-custom-methods.md)

- [MFC ActiveX Controls: Returning Error Codes From a (Método)](mfc-activex-controls-returning-error-codes-from-a-method.md)

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)
