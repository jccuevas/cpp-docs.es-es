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
ms.openlocfilehash: 47640a59180348bd3513013b65029a775545e211
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619181"
---
# <a name="activation-c"></a>Activación (C++)

En este artículo se explica el rol de activación en la edición visual de elementos OLE. Una vez que un usuario ha incrustado un elemento OLE en un documento de contenedor, puede que sea necesario utilizarlo. Para ello, el usuario hace doble clic en el elemento, que activa ese elemento. La actividad más frecuente de la activación es la edición. Muchos elementos OLE actuales, cuando se activan para su edición, hacen que los menús y las barras de herramientas de la ventana de marco actual cambien para reflejar los que pertenecen a la aplicación de servidor que creó el elemento. Este comportamiento, conocido como activación en contexto, permite al usuario editar cualquier elemento incrustado en un documento compuesto sin mantener la ventana del documento contenedor.

También es posible editar elementos OLE incrustados en una ventana independiente. Esto ocurrirá si el contenedor o la aplicación de servidor no admiten la activación en contexto. En este caso, cuando el usuario hace doble clic en un elemento incrustado, la aplicación de servidor se inicia en una ventana independiente y el elemento incrustado aparece como su propio documento. El usuario edita el elemento en esta ventana. Cuando se completa la edición, el usuario cierra la aplicación de servidor y vuelve a la aplicación contenedora.

Como alternativa, el usuario puede elegir "abrir edición" con el comando ** \<object> abrir** en el menú **edición** . Se abrirá el objeto en una ventana independiente.

> [!NOTE]
> La edición de elementos incrustados en una ventana independiente era un comportamiento estándar en la versión 1 de OLE y algunas aplicaciones OLE solo pueden admitir este estilo de edición.

La activación en contexto promueve un enfoque centrado en documentos para la creación de documentos. El usuario puede tratar un documento compuesto como una entidad única, trabajando en él sin cambiar de aplicación. Sin embargo, la activación en contexto solo se usa para los elementos incrustados, no para los elementos vinculados: deben editarse en una ventana independiente. Esto se debe a que un elemento vinculado está realmente almacenado en un lugar diferente. La edición de un elemento vinculado tiene lugar dentro del contexto real de los datos, es decir, donde se almacenan los datos. Al editar un elemento vinculado en una ventana independiente, se recuerda al usuario que los datos pertenecen a otro documento.

MFC no admite la activación en contexto anidada. Si compila una aplicación de contenedor/servidor y ese contenedor o servidor está incrustado en otro contenedor y activado en contexto, no puede activar objetos incrustados dentro de él.

Lo que ocurre en un elemento incrustado cuando el usuario hace doble clic en él depende de los verbos definidos para el elemento. Para obtener más información, consulte [activación: verbos](activation-verbs.md).

## <a name="see-also"></a>Consulte también

[OLE](ole-in-mfc.md)<br/>
[Contenedores](containers.md)<br/>
[Servidores](servers.md)
