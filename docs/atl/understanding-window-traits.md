---
title: Rasgos de las ventanas ATL | Microsoft Docs
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
ms.openlocfilehash: 91ea30c79712ced6c86da0b030882fe6a88359ed
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764048"
---
# <a name="understanding-window-traits"></a>Descripción de rasgos de las ventanas

Clases de rasgos de ventana proporcionan un método sencillo para estandarizar los estilos utilizados para la creación de un objeto de ventana ATL. Se aceptan los rasgos de las ventanas como parámetros de plantilla por [CWindowImpl](../atl/reference/cwindowimpl-class.md) y otras clases de ventana ATL como una manera de proporcionar de forma predeterminada los estilos de ventana en el nivel de clase.

Si el creador de una instancia de la ventana no proporciona estilos explícitamente en la llamada a [crear](../atl/reference/cwindowimpl-class.md#create), puede usar una clase de rasgos para asegurarse de que la ventana se ha creado con los estilos correctos. Incluso puede garantizar que determinados estilos se establecen para todas las instancias de esa clase de ventana al tiempo que permite a otros estilos debe establecerse en una base por instancia.

## <a name="atl-window-traits-templates"></a>Plantillas de rasgos de ventana ATL

ATL proporciona dos plantillas de rasgos de ventana que permiten establecer los estilos predeterminados en tiempo de compilación mediante sus parámetros de plantilla.

|Clase|Descripción|
|-----------|-----------------|
|[CWinTraits](../atl/reference/cwintraits-class.md)|Use esta plantilla cuando desee proporcionar predeterminado estilos de ventana que se usará sólo cuando ningún otro estilo se especifica en la llamada a `Create`. Los estilos proporcionados en tienen prioridad de tiempo de ejecución a través de los estilos establecidos en tiempo de compilación.|
|[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)|Utilice esta clase cuando desee especificar estilos que siempre deben estar establecidos para la clase de ventana. Los estilos proporcionados en tiempo de ejecución se combinan con los estilos establecidos en tiempo de compilación mediante el operador OR bit a bit.|

Además de estas plantillas, ATL proporciona una serie de especializaciones predefinidas de la `CWinTraits` plantilla para las combinaciones de estilos de ventana comúnmente usadas. Consulte la [CWinTraits](../atl/reference/cwintraits-class.md) documentación para obtener detalles completos de referencia.

## <a name="custom-window-traits"></a>Rasgos de ventana personalizado

En el caso poco probable que una de las plantillas proporcionadas por ATL especializada no es suficiente y necesita crear su propia clase de rasgos, basta con crear una clase que implementa dos funciones estáticas: `GetWndStyle` y `GetWndStyleEx`:

[!code-cpp[NVC_ATL_Windowing#68](../atl/codesnippet/cpp/understanding-window-traits_1.h)]

Cada una de estas funciones se pasará algún valor de estilo en tiempo de ejecución que puede utilizar para generar un nuevo valor de estilo. Si la clase de rasgos de ventana que se va a se usa como argumento de plantilla para una clase de ventana ATL, los valores de estilo pasados a estas funciones estáticas será lo que se pasó como argumentos de estilo a [crear](../atl/reference/cwindowimpl-class.md#create).

## <a name="see-also"></a>Vea también

[Clases de ventana](../atl/atl-window-classes.md)

