---
title: "Activación: Verbos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- verbs [MFC]
- OLE [MFC], activation
- edit verb [MFC]
- activation [MFC], verbs
- OLE [MFC], editing
- Primary verb [MFC]
- OLE activation {MFC]
ms.assetid: eb56ff23-1de8-43ad-abeb-dc7346ba7b70
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c2a443f4ce65dcc7e9460bd016638aa5069e7e6d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="activation-verbs"></a>Activación: Verbos
Este artículo explica el rol que desempeñan los verbos principal y secundaria en OLE [activación](../mfc/activation-cpp.md).  
  
 Por lo general, al hacer doble clic en un elemento incrustado, se permite al usuario editarlo. Sin embargo, algunos elementos de comportamiento no sea así. Por ejemplo, haga doble clic en un elemento creado con la aplicación de la grabadora de sonidos no se abre el servidor en una ventana independiente; en su lugar, reproduce el sonido.  
  
 La razón de esta diferencia de comportamiento es que los elementos de la grabadora de sonidos tienen diferentes "verbo principal". El verbo principal es la acción realizada cuando el usuario hace doble clic en un elemento OLE. Para la mayoría de los tipos de elementos OLE, el verbo principal es editar, que inicia el servidor que creó el elemento. Para algunos tipos de elementos, como los elementos de la grabadora de sonidos, el verbo principal es reproducir.  
  
 Muchos tipos de elementos OLE admiten un solo verbo, y editar es el más común. Sin embargo, algunos tipos de elementos admiten varios verbos. Por ejemplo, la grabadora de sonidos admiten elementos Editar como verbo secundario.  
  
 Otro verbo que se usan con frecuencia está abierta. El verbo Open es idéntico a editar, excepto la aplicación de servidor se inicia en una ventana independiente. Este verbo debe utilizarse cuando la aplicación contenedora o la aplicación de servidor no admite la activación en contexto.  
  
 Los verbos distintos del principal deben invocarse a través de un comando de submenú cuando se selecciona el elemento. Este submenú contiene todos los verbos admitidos por el elemento y normalmente alcanza el *typename* **objeto** comando el **editar** menú. Para obtener información sobre la *typename* **objeto** command, consulte el artículo [menús y recursos: adiciones de contenedor](../mfc/menus-and-resources-container-additions.md).  
  
 Los verbos que admite una aplicación de servidor se muestran en la base de datos de registro de Windows. Si la aplicación de servidor está escrita con la biblioteca Microsoft Foundation Class, registrará automáticamente todos los verbos cuando se inicia el servidor. Si no es así, debe registrarlos durante la fase de inicialización de la aplicación de servidor. Para obtener más información, vea el artículo [registro](../mfc/registration.md).  
  
## <a name="see-also"></a>Vea también  
 [Activación](../mfc/activation-cpp.md)   
 [Contenedores](../mfc/containers.md)   
 [Servidores](../mfc/servers.md)

