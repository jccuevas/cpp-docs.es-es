---
title: 'Activación: Verbos'
ms.date: 11/04/2016
helpviewer_keywords:
- verbs [MFC]
- OLE [MFC], activation
- edit verb [MFC]
- activation [MFC], verbs
- OLE [MFC], editing
- Primary verb [MFC]
- OLE activation {MFC]
ms.assetid: eb56ff23-1de8-43ad-abeb-dc7346ba7b70
ms.openlocfilehash: baf8e0ac3527407b2e5ba77dfdf3921419217fd7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267919"
---
# <a name="activation-verbs"></a>Activación: Verbos

En este artículo se explica el rol que desempeñan los verbos principal y secundaria en OLE [activación](../mfc/activation-cpp.md).

Por lo general, haga doble clic en un elemento incrustado permite que el usuario editarlo. Sin embargo, algunos elementos no se comportan así. Por ejemplo, haga doble clic en un elemento creado con la aplicación de la grabadora de sonidos no se abre el servidor en una ventana independiente; en su lugar, reproduce el sonido.

La razón de esta diferencia de comportamiento es que los elementos de la grabadora de sonidos tienen diferentes "verbo principal". El verbo principal es la acción realizada cuando el usuario hace doble clic en un elemento OLE. Para la mayoría de los tipos de elementos OLE, el verbo principal es editar, que inicia el servidor que creó el elemento. Para algunos tipos de elementos, como los elementos de la grabadora de sonidos, el verbo principal es reproducir.

Muchos tipos de elementos OLE admiten un solo verbo y edición es la más común. Sin embargo, algunos tipos de elementos admiten varios verbos. Por ejemplo, los elementos admiten la grabadora de sonidos editar como verbo secundario.

Otro verbo que se usan con frecuencia es abierto. El verbo Open es idéntico al editar, salvo que se inicia la aplicación de servidor en una ventana independiente. Este verbo debe usarse cuando la aplicación de contenedor o la aplicación de servidor no admite la activación en contexto.

Los verbos distintos del principal se deben invocar a través de un comando de submenú cuando se selecciona el elemento. Este menú contiene todos los verbos admitidos por el elemento y suele alcanzarse por la *typename* **objeto** comando el **editar** menú. Para obtener información sobre la *typename* **objeto** de comandos, consulte el artículo [menús y recursos: Adiciones de contenedor](../mfc/menus-and-resources-container-additions.md).

Los verbos que admite una aplicación de servidor se muestran en la base de datos de registro de Windows. Si se escribe la aplicación de servidor con la biblioteca Microsoft Foundation Class, se registrarán automáticamente todos los verbos cuando se inicia el servidor. Si no es así, debe registrarlos durante la fase de inicialización de la aplicación de servidor. Para obtener más información, vea el artículo [registro](../mfc/registration.md).

## <a name="see-also"></a>Vea también

[Activación](../mfc/activation-cpp.md)<br/>
[Contenedores](../mfc/containers.md)<br/>
[Servidores](../mfc/servers.md)
