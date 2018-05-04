---
title: Rasgos de ventana ATL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window traits
ms.assetid: c90cf850-9e91-49da-9cf3-ad4efb30347d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71fbf5b3c4c3f1aa95070cbc0d30beb9e1321348
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="understanding-window-traits"></a>Descripción de los rasgos de las ventanas
Clases de ventana de rasgos proporcionan un método sencillo para estandarizar los estilos utilizados para la creación de un objeto de ventana ATL. Rasgos de las ventanas se aceptan como parámetros de plantilla por [CWindowImpl](../atl/reference/cwindowimpl-class.md) y otras clases de ventana ATL como una manera de ofrecer predeterminado estilos de ventana en el nivel de clase.  
  
 Si no le proporciona el creador de una instancia de la ventana Estilos de forma explícita en la llamada a [crear](../atl/reference/cwindowimpl-class.md#create), puede usar una clase de rasgos para asegurarse de que la ventana se ha creado con los estilos correctos. Incluso puede asegurarse de que ciertos estilos se establecen para todas las instancias de esa clase de ventana al permitir otros estilos que se establecerá en por instancia.  
  
## <a name="atl-window-traits-templates"></a>Plantillas de rasgos de ventana ATL  
 ATL proporciona dos plantillas de rasgos de ventana que le permiten establecer estilos predeterminados en tiempo de compilación mediante sus parámetros de plantilla.  
  
|Clase|Descripción|  
|-----------|-----------------|  
|[CWinTraits](../atl/reference/cwintraits-class.md)|Utilice esta plantilla cuando desee proporcionar predeterminado estilos de ventana que se utilizará sólo cuando no hay otros estilos se especifican en la llamada a **crear**. Los estilos proporcionados en prevalecen de tiempo de ejecución sobre los estilos establecidos en tiempo de compilación.|  
|[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)|Utilice esta clase cuando desee especificar estilos que siempre se deben establecer para la clase de ventana. Los estilos proporcionados en tiempo de ejecución se combinan con los estilos establecidos en tiempo de compilación mediante el operador OR bit a bit.|  
  
 Además de estas plantillas, ATL proporciona un número de especializaciones predefinidas de la `CWinTraits` plantilla para combinaciones usadas con frecuencia de estilos de ventana. Consulte la [CWinTraits](../atl/reference/cwintraits-class.md) hacen referencia a documentación para obtener detalles completos.  
  
## <a name="custom-window-traits"></a>Rasgos de ventana personalizados  
 En el caso poco probable que una de las plantillas proporcionadas por ATL especializada no es suficiente y necesita crear su propia clase de rasgos, necesitará crear una clase que implemente dos funciones estáticas: `GetWndStyle` y **GetWndStyleEx** :  
  
 [!code-cpp[NVC_ATL_Windowing#68](../atl/codesnippet/cpp/understanding-window-traits_1.h)]  
  
 Cada una de estas funciones se pasará algún valor de estilo en tiempo de ejecución que puede utilizar para generar un nuevo valor de estilo. Si se utiliza la clase de rasgos de ventana como argumento de plantilla a una clase de ventana ATL, los valores de estilo pasados a estas funciones estáticas serán lo que se pasó como argumentos de estilo a [crear](../atl/reference/cwindowimpl-class.md#create).  
  
## <a name="see-also"></a>Vea también  
 [Clases de ventana](../atl/atl-window-classes.md)

