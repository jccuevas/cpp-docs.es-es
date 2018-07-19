---
title: Optimizar la persistencia y la inicialización | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- optimizing performance, ActiveX controls
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d03966cb61e1ccab3f8f3886638efdf95a534a73
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930318"
---
# <a name="optimizing-persistence-and-initialization"></a>Optimizar la persistencia y la inicialización
De forma predeterminada, persistencia y la inicialización en un control se controlan mediante la `DoPropExchange` función miembro. En un control típico, esta función contiene llamadas a varios **PX_** funciones (`PX_Color`, `PX_Font`, etc.), uno para cada propiedad.  
  
 Este enfoque tiene la ventaja de que una sola `DoPropExchange` implementación puede utilizarse para la inicialización, persistencia en formato binario y persistencia en el formato denominado "bolsa de propiedades", utilizado por algunos contenedores. Esta única función proporciona toda la información sobre las propiedades y sus valores predeterminados en un lugar cómodo.  
  
 Sin embargo, esta generalidad se obtiene a costa de la eficacia. El **PX_** funciones obtienen su flexibilidad a través de implementaciones de varios niveles que son intrínsecamente menos eficaz que los enfoques más directos, pero es menos flexibles. Además, si un control pasa un valor predeterminado para un **PX_** funcione, que se debe proporcionar el valor de forma predeterminada cada vez, incluso en situaciones en que no es necesario utilizar el valor predeterminado. Si genera el valor predeterminado es una tarea trivial (por ejemplo, cuando se obtiene el valor de una propiedad de ambiente), entonces adicional, se realiza trabajo innecesario en casos donde no se utiliza el valor predeterminado.  
  
 Puede mejorar el rendimiento de persistencia binaria del control invalidando el control `Serialize` (función). La implementación predeterminada de esta función miembro realiza una llamada a su `DoPropExchange` función. Si se reemplaza, puede proporcionar una implementación más directa para la persistencia binaria. Por ejemplo, considere lo siguiente `DoPropExchange` función:  
  
 [!code-cpp[NVC_MFC_AxOpt#1](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_1.cpp)]  
  
 Para mejorar el rendimiento de persistencia binaria del control, puede invalidar el `Serialize` funcione como se indica a continuación:  
  
 [!code-cpp[NVC_MFC_AxOpt#2](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_2.cpp)]  
  
 El `dwVersion` variable local se puede utilizar para detectar la versión del estado persistente del control que se cargan o se guardan. Puede usar esta variable en lugar de llamar [CPropExchange:: GetVersion](../mfc/reference/cpropexchange-class.md#getversion).  
  
 Para guardar un poco de espacio en el formato persistente para una **BOOL** propiedad (y hacer que sea compatible con el formato producido por `PX_Bool`), se puede almacenar la propiedad como un **bytes**, como se indica a continuación:  
  
 [!code-cpp[NVC_MFC_AxOpt#3](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_3.cpp)]  
  
 Tenga en cuenta que en el caso de carga, se usa una variable temporal y, a continuación, se asigna su valor, en lugar de convertir *m_boolProp* a una **bytes** referencia. La técnica de conversión, se crearán en solo un byte de *m_boolProp* que se está modificando, dejando los bytes restantes no se ha inicializado.  
  
 Para el mismo control, puede optimizar la inicialización del control invalidando [COleControl:: OnResetState](../mfc/reference/colecontrol-class.md#onresetstate) como se indica a continuación:  
  
 [!code-cpp[NVC_MFC_AxOpt#4](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_4.cpp)]  
  
 Aunque `Serialize` y `OnResetState` se han reemplazado, el `DoPropExchange` función se debe mantener intacta porque aún se utiliza para la persistencia en el formato de contenedor de propiedades. Es importante mantener las tres de estas funciones para asegurarse de que el control administra sus propiedades de forma coherente, independientemente de qué persistencia utiliza el mecanismo del contenedor.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC: Optimización](../mfc/mfc-activex-controls-optimization.md)

