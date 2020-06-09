---
title: Optimizar la persistencia y la inicialización
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- optimizing performance, ActiveX controls
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
ms.openlocfilehash: 57b98f7e2e4f9e23175b8b01c2e37ff49c499949
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623997"
---
# <a name="optimizing-persistence-and-initialization"></a>Optimizar la persistencia y la inicialización

De forma predeterminada, la función miembro controla la persistencia y la inicialización en un control `DoPropExchange` . En un control típico, esta función contiene llamadas a varias funciones de **PX_** ( `PX_Color` , `PX_Font` , etc.), una para cada propiedad.

Este enfoque tiene la ventaja de que `DoPropExchange` se puede usar una sola implementación para la inicialización, para la persistencia en formato binario y para la persistencia en el formato denominado "contenedor de propiedades" que usan algunos contenedores. Esta función proporciona toda la información sobre las propiedades y sus valores predeterminados en un lugar cómodo.

Sin embargo, esta generalidad se refiere a la eficacia. Las funciones de **PX_** obtienen su flexibilidad a través de implementaciones de varias capas que son intrínsecamente menos eficientes que los enfoques más directos, pero menos flexibles. Además, si un control pasa un valor predeterminado a una función **PX_** , se debe proporcionar ese valor predeterminado cada vez, incluso en situaciones en las que no sea necesario usar el valor predeterminado. Si la generación del valor predeterminado es una tarea no trivial (por ejemplo, cuando el valor se obtiene de una propiedad de ambiente), se realiza un trabajo adicional innecesario en los casos en los que no se usa el valor predeterminado.

Puede mejorar el rendimiento de la persistencia binaria del control invalidando la `Serialize` función del control. La implementación predeterminada de esta función miembro realiza una llamada a la `DoPropExchange` función. Al invalidarlo, puede proporcionar una implementación más directa para la persistencia binaria. Por ejemplo, considere esta `DoPropExchange` función:

[!code-cpp[NVC_MFC_AxOpt#1](codesnippet/cpp/optimizing-persistence-and-initialization_1.cpp)]

Para mejorar el rendimiento de la persistencia binaria de este control, puede invalidar la función de la `Serialize` siguiente manera:

[!code-cpp[NVC_MFC_AxOpt#2](codesnippet/cpp/optimizing-persistence-and-initialization_2.cpp)]

La `dwVersion` variable local se puede usar para detectar la versión del estado persistente del control que se carga o se guarda. Puede usar esta variable en lugar de llamar a [CPropExchange:: GetVersion](reference/cpropexchange-class.md#getversion).

Para guardar un poco espacio en el formato persistente para una propiedad **bool** (y para mantenerlo compatible con el formato generado por `PX_Bool` ), puede almacenar la propiedad como un **byte**, como se indica a continuación:

[!code-cpp[NVC_MFC_AxOpt#3](codesnippet/cpp/optimizing-persistence-and-initialization_3.cpp)]

Tenga en cuenta que, en el caso de carga, se usa una variable temporal y, a continuación, se asigna su valor, en lugar de convertir *m_boolProp* en una referencia de **bytes** . La técnica de conversión daría como resultado que solo se modificara un byte de *m_boolProp* , lo que dejaría los bytes restantes sin inicializar.

En el mismo control, puede optimizar la inicialización del control invalidando [COleControl:: OnResetState](reference/colecontrol-class.md#onresetstate) como se indica a continuación:

[!code-cpp[NVC_MFC_AxOpt#4](codesnippet/cpp/optimizing-persistence-and-initialization_4.cpp)]

Aunque `Serialize` y `OnResetState` se han reemplazado, la `DoPropExchange` función debe mantenerse intacta porque todavía se usa para la persistencia en el formato de contenedor de propiedades. Es importante mantener las tres funciones para asegurarse de que el control administre sus propiedades de forma coherente, independientemente del mecanismo de persistencia que use el contenedor.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC: Optimización](mfc-activex-controls-optimization.md)
