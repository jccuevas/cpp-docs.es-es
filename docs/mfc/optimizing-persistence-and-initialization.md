---
title: Optimizar la persistencia y la inicialización
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- optimizing performance, ActiveX controls
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
ms.openlocfilehash: 294d9c43f5f767329c04932c574485d7dca704e9
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342128"
---
# <a name="optimizing-persistence-and-initialization"></a>Optimizar la persistencia y la inicialización

De forma predeterminada, persistencia y la inicialización en un control se controlan mediante el `DoPropExchange` función miembro. En un control típico, esta función contiene llamadas a varios **PX_** funciones (`PX_Color`, `PX_Font`, etc.), uno para cada propiedad.

Este enfoque tiene la ventaja de que una sola `DoPropExchange` implementación se puede usar para la inicialización, persistencia en formato binario y persistencia en el formato del llamado "bolsa" utilizado por algunos contenedores. Esta uno función proporciona toda la información sobre las propiedades y sus valores predeterminados en un solo lugar.

Sin embargo, esta generalidad se obtiene a costa de la eficacia. El **PX_** funciones obtienen su flexibilidad a través de las implementaciones de varios niveles que son intrínsecamente menos eficaz que los enfoques más directos, pero es menos flexibles. Además, si un control pasa un valor predeterminado para un **PX_** funcione, que se debe proporcionar valor predeterminado cada vez, incluso en situaciones cuando es posible que no es necesario utilizar el valor predeterminado. Si genera el valor predeterminado es una tarea trivial (por ejemplo, cuando se obtiene el valor de una propiedad de ambiente), entonces adicional, se realiza trabajo innecesario en los casos donde no se utiliza el valor predeterminado.

Puede mejorar el rendimiento de persistencia binaria del control invalidando el control `Serialize` función. La implementación predeterminada de esta función miembro realiza una llamada a su `DoPropExchange` función. Si se reemplaza, puede proporcionar una implementación más directa para la persistencia binaria. Por ejemplo, tenga en cuenta esto `DoPropExchange` función:

[!code-cpp[NVC_MFC_AxOpt#1](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_1.cpp)]

Para mejorar el rendimiento de persistencia binaria de este control, puede invalidar el `Serialize` funcione como se indica a continuación:

[!code-cpp[NVC_MFC_AxOpt#2](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_2.cpp)]

El `dwVersion` variable local se puede utilizar para detectar la versión de estado persistente del control que se va a cargar o guardar. Puede usar esta variable en lugar de llamar [CPropExchange:: GetVersion](../mfc/reference/cpropexchange-class.md#getversion).

Para guardar un poco de espacio en el formato persistente para un **BOOL** propiedad (y hacer que sea compatible con el formato producido por `PX_Bool`), puede almacenar la propiedad como un **bytes**, como sigue:

[!code-cpp[NVC_MFC_AxOpt#3](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_3.cpp)]

Tenga en cuenta que en el caso de carga, se usa una variable temporal y, a continuación, su valor se asigna, en lugar de convertir *m_boolProp* a un **bytes** referencia. La técnica de conversión daría lugar a un solo byte de *m_boolProp* que se está modificando, dejando los bytes restantes sin inicializar.

Para el mismo control, puede optimizar la inicialización del control invalidando [COleControl:: OnResetState](../mfc/reference/colecontrol-class.md#onresetstate) como sigue:

[!code-cpp[NVC_MFC_AxOpt#4](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_4.cpp)]

Aunque `Serialize` y `OnResetState` se han invalidado, el `DoPropExchange` función debe mantenerse intacta porque aún se utiliza para la persistencia en el formato de contenedor de propiedades. Es importante mantener las tres de estas funciones para asegurarse de que el control administra sus propiedades de forma coherente, independientemente de persistencia que utiliza el mecanismo del contenedor.

## <a name="see-also"></a>Vea también

[Controles ActiveX de MFC: optimización](../mfc/mfc-activex-controls-optimization.md)
