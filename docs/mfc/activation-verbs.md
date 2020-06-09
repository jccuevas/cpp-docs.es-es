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
ms.openlocfilehash: 03edba0a4336fdc147ef6dd10c7a8154aca19d3a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616644"
---
# <a name="activation-verbs"></a>Activación: Verbos

En este artículo se explican los verbos principales y secundarios de rol que se reproducen en la [activación](activation-cpp.md)OLE.

Normalmente, al hacer doble clic en un elemento incrustado, el usuario puede editarlo. Sin embargo, algunos elementos no se comportan de esta manera. Por ejemplo, al hacer doble clic en un elemento creado con la aplicación grabadora de sonidos no se abre el servidor en una ventana independiente. en su lugar, reproduce el sonido.

La razón de esta diferencia de comportamiento es que los elementos de la grabadora de sonidos tienen un "verbo principal" diferente. El verbo principal es la acción que se realiza cuando el usuario hace doble clic en un elemento OLE. Para la mayoría de los tipos de elementos OLE, el verbo principal es Edit, que inicia el servidor que creó el elemento. En algunos tipos de elementos, como los elementos de la grabadora de sonidos, el verbo principal es Play.

Muchos tipos de elementos OLE solo admiten un verbo y Edit es el más común. Sin embargo, algunos tipos de elementos admiten varios verbos. Por ejemplo, los elementos de la grabadora de sonidos admiten editar como verbo secundario.

Otro verbo utilizado con frecuencia es Open. El verbo Open es idéntico a Edit, excepto que la aplicación de servidor se inicia en una ventana independiente. Este verbo debe usarse cuando la aplicación contenedora o la aplicación de servidor no admiten la activación en contexto.

Los verbos distintos del verbo principal deben invocarse a través de un comando de submenú cuando se selecciona el elemento. Este submenú contiene todos los verbos admitidos por el elemento y normalmente se alcanza mediante el comando *TypeName* **Object** en el menú **Editar** . Para obtener información sobre el comando *TypeName* **Object** , vea el artículo [menús y recursos: adiciones de contenedor](menus-and-resources-container-additions.md).

Los verbos que admite una aplicación de servidor se muestran en la base de datos de registro de Windows. Si la aplicación de servidor se escribe con el biblioteca MFC, se registrarán automáticamente todos los verbos cuando se inicie el servidor. Si no es así, debe registrarlos durante la fase de inicialización de la aplicación de servidor. Para obtener más información, consulte el artículo [registro](registration.md).

## <a name="see-also"></a>Consulte también

[Activación](activation-cpp.md)<br/>
[Contenedores](containers.md)<br/>
[Servidores](servers.md)
