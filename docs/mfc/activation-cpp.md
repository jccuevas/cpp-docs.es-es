---
title: "Activación (C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE server applications [MFC], activation
- OLE items [MFC], visual editing
- activation [MFC]
- OLE [MFC], in-place activation
- OLE [MFC], activation
- in-place activation, embedded and linked items
- activating objects
- visual editing, activation
- visual editing
- documents [MFC], OLE
- embedded objects [MFC]
- OLE [MFC], editing
- in-place activation
- activation [MFC], embedded OLE items
- OLE activation [MFC]
ms.assetid: ed8357d9-e487-4aaa-aa6b-2edc4de25dfa
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 70017721fb59fa0c6d18d568546d9618257328b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="activation-c"></a>Activación (C++)
En este artículo se explica el rol de activación en la edición visual de elementos OLE. Después de que un usuario ha incorporado un elemento OLE en un documento de contenedor, tendrá que se usará. Para ello, el usuario hace doble clic en el elemento, que activa ese elemento. Está editando la actividad más frecuente para la activación. Muchos elementos OLE actuales, cuando se activan para la edición, hacer que los menús y barras de herramientas en la ventana de marco actual cambian para reflejarlos que pertenecen a la aplicación de servidor que creó el elemento. Este comportamiento, conocido como en el contexto de activación, permite al usuario editar cualquier elemento incrustado en un documento compuesto sin salir de la ventana del documento contenedor.  
  
 También es posible editar elementos OLE incrustados en una ventana independiente. Esto sucederá si el contenedor o el servidor de aplicaciones no es compatible con la activación en contexto. En este caso, cuando el usuario hace doble clic en un elemento incrustado, se inicia la aplicación de servidor en una ventana independiente y el elemento incrustado aparece como su propio documento. El usuario edita el elemento en esta ventana. Cuando se completa la edición, el usuario cierra la aplicación de servidor y se devuelve a la aplicación contenedora.  
  
 Como alternativa, el usuario puede elegir "abrir edición" con el  **\<objeto > Abrir** comando el **editar** menú. Se abre el objeto en una ventana independiente.  
  
> [!NOTE]
>  Editar elementos incrustados en una ventana independiente era el comportamiento estándar en la versión 1 de OLE y algunas aplicaciones OLE pueden admitir solo este estilo de edición.  
  
 Activación en contexto promueve un enfoque centrado en documentos para la creación de documentos. El usuario puede tratar un documento compuesto como una entidad única, trabajar en él sin tener que cambiar entre las aplicaciones. Sin embargo, la activación en contexto solo se utiliza para los elementos incrustados, no para los elementos vinculados: éstos deben editarse en una ventana independiente. Esto es porque un elemento vinculado se almacena realmente en un lugar diferente. La edición de un elemento vinculado tiene lugar dentro del contexto real de los datos, es decir, donde se almacenan los datos. Editar un elemento vinculado en una ventana independiente recuerda al usuario que pertenecen los datos a otro documento.  
  
 MFC no admite la activación en contexto anidada. Si se crea una aplicación de contenedor y servidor y que contenedor/servidor está incrustado en otro contenedor y activado en contexto, no se en contexto activar objetos incrustados dentro de él.  
  
 ¿Qué ocurre cuando el usuario hace doble clic en un elemento incrustado depende de los verbos definidos para el elemento. Para obtener información, consulte [activación: verbos](../mfc/activation-verbs.md).  
  
## <a name="see-also"></a>Vea también  
 [OLE](../mfc/ole-in-mfc.md)   
 [Contenedores](../mfc/containers.md)   
 [Servidores](../mfc/servers.md)

