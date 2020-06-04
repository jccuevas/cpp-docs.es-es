---
title: Activación (C++)
ms.date: 11/04/2016
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
ms.openlocfilehash: 9f3fba71002a19a0be0e3429a0faeeefb7c65197
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354170"
---
# <a name="activation-c"></a>Activación (C++)

En este artículo se explica el rol de activación en la edición visual de elementos OLE. Después de que un usuario ha incrustado un elemento OLE en un documento contenedor, es posible que deba usarse. Para ello, el usuario hace doble clic en el elemento, lo que activa ese elemento. La actividad más frecuente para la activación es la edición. Muchos elementos OLE actuales, cuando se activan para la edición, hacen que los menús y barras de herramientas de la ventana de marco actual cambien para reflejar los que pertenecen a la aplicación de servidor que creó el elemento. Este comportamiento, conocido como activación en contexto, permite al usuario editar cualquier elemento incrustado en un documento compuesto sin salir de la ventana del documento contenedor.

También es posible editar elementos OLE incrustados en una ventana independiente. Esto sucederá si la aplicación contenedora o de servidor no admite la activación en contexto. En este caso, cuando el usuario hace doble clic en un elemento incrustado, la aplicación de servidor se inicia en una ventana independiente y el elemento incrustado aparece como su propio documento. El usuario edita el elemento en esta ventana. Una vez completada la edición, el usuario cierra la aplicación de servidor y vuelve a la aplicación contenedora.

Como alternativa, el usuario puede elegir "editar abierto" con el ** \<objeto> comando Abrir** en el menú **Edición.** Esto abre el objeto en una ventana independiente.

> [!NOTE]
> La edición de elementos incrustados en una ventana independiente era un comportamiento estándar en la versión 1 de OLE y algunas aplicaciones OLE pueden admitir solo este estilo de edición.

La activación in situ promueve un enfoque centrado en documentos para la creación de documentos. El usuario puede tratar un documento compuesto como una sola entidad, trabajando en él sin cambiar entre aplicaciones. Sin embargo, la activación in situ solo se utiliza para elementos incrustados, no para elementos vinculados: deben editarse en una ventana independiente. Esto se debe a que un elemento vinculado se almacena realmente en un lugar diferente. La edición de un elemento vinculado tiene lugar en el contexto real de los datos, es decir, donde se almacenan los datos. La edición de un elemento vinculado en una ventana independiente recuerda al usuario que los datos pertenecen a otro documento.

MFC no admite la activación en contexto anidada. Si crea una aplicación contenedora/servidor y ese contenedor/servidor está incrustado en otro contenedor y activado in situ, no puede activar en contexto los objetos incrustados en él.

Lo que sucede con un elemento incrustado cuando el usuario hace doble clic en él depende de los verbos definidos para el elemento. Para obtener más información, consulte [Activación: Verbos](../mfc/activation-verbs.md).

## <a name="see-also"></a>Consulte también

[OLE](../mfc/ole-in-mfc.md)<br/>
[Contenedores](../mfc/containers.md)<br/>
[Servidores](../mfc/servers.md)
