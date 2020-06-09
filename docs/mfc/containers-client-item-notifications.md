---
title: 'Contenedores: Notificaciones de elementos de cliente'
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], container client item
- OLE containers [MFC], client-item notifications
- client items and OLE containers
ms.assetid: e1f1c427-01f5-45f2-b496-c5bce3d76340
ms.openlocfilehash: 54b1b2a64685b00fb265e0f80c1f6ad878a7da85
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623020"
---
# <a name="containers-client-item-notifications"></a>Contenedores: Notificaciones de elementos de cliente

En este artículo se describen las funciones reemplazables a las que llama el marco de trabajo de MFC cuando las aplicaciones de servidor modifican elementos en el documento de la aplicación cliente.

[COleClientItem](reference/coleclientitem-class.md) define varias funciones reemplazables a las que se llama en respuesta a las solicitudes de la aplicación de componentes, que también se denomina aplicación de servidor. Estos reemplazables suelen actuar como notificaciones. Informan a la aplicación contenedora de diversos eventos, como el desplazamiento, la activación o un cambio de posición, y de los cambios que el usuario realiza al editar o manipular el elemento de otra manera.

El marco de trabajo notifica a la aplicación de contenedor los cambios a través de una llamada a `COleClientItem::OnChange` , una función reemplazable cuya implementación es necesaria. Esta función protegida recibe dos argumentos. El primero especifica la razón por la que el servidor cambió el elemento:

|Notificación|Significado|
|------------------|-------------|
|**OLE_CHANGED**|La apariencia del elemento OLE ha cambiado.|
|**OLE_SAVED**|Se ha guardado el elemento OLE.|
|**OLE_CLOSED**|El elemento OLE se ha cerrado.|
|**OLE_RENAMED**|Se ha cambiado el nombre del documento de servidor que contiene el elemento OLE.|
|**OLE_CHANGED_STATE**|El elemento OLE ha cambiado de un estado a otro.|
|**OLE_CHANGED_ASPECT**|El marco ha cambiado el aspecto de dibujo del elemento OLE.|

Estos valores proceden de la enumeración **OLE_NOTIFICATION** , que se define en AFXOLE. C.

El segundo argumento de esta función especifica el modo en que el elemento ha cambiado o el estado que ha escrito:

|Cuando el primer argumento es|Segundo argumento|
|----------------------------|---------------------|
|**OLE_SAVED** o **OLE_CLOSED**|No se utiliza.|
|**OLE_CHANGED**|Especifica el aspecto del elemento OLE que ha cambiado.|
|**OLE_CHANGED_STATE**|Describe el estado que se va a especificar (*emptyState*, *loadedState*, *openState*, *activeState*o *activeUIState*).|

Para obtener más información sobre los Estados que un elemento de cliente puede asumir, consulte [contenedores: Estados de elementos de cliente](containers-client-item-states.md).

El marco de trabajo llama `COleClientItem::OnGetItemPosition` cuando un elemento se activa para la edición en contexto. La implementación es necesaria para las aplicaciones que admiten la edición en contexto. El Asistente para aplicaciones MFC proporciona una implementación básica, que asigna las coordenadas del elemento al `CRect` objeto que se pasa como argumento a `OnGetItemPosition` .

Si cambia la posición o el tamaño de un elemento OLE durante la edición en contexto, se debe actualizar la información del contenedor sobre la posición del elemento y los rectángulos de recorte, y el servidor debe recibir información acerca de los cambios. El marco de trabajo llama a `COleClientItem::OnChangeItemPosition` para este propósito. El Asistente para aplicaciones MFC proporciona una invalidación que llama a la función de la clase base. Debe editar la función que el Asistente para aplicaciones escribe en la `COleClientItem` clase derivada de para que la función actualice cualquier información retenida por el objeto de elemento de cliente.

## <a name="see-also"></a>Consulte también

[Contenedores](containers.md)<br/>
[Contenedores: Estados de elementos de cliente](containers-client-item-states.md)<br/>
[COleClientItem:: OnChangeItemPosition](reference/coleclientitem-class.md#onchangeitemposition)
