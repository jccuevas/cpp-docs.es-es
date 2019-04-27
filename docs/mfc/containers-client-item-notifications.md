---
title: 'Contenedores: Notificaciones de elementos de cliente'
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], container client item
- OLE containers [MFC], client-item notifications
- client items and OLE containers
ms.assetid: e1f1c427-01f5-45f2-b496-c5bce3d76340
ms.openlocfilehash: 583c438820c002a4c192d15358ca98424d02889a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153430"
---
# <a name="containers-client-item-notifications"></a>Contenedores: Notificaciones de elementos de cliente

En este artículo se describe las funciones reemplazables que llama el marco MFC cuando las aplicaciones de servidor modifican elementos en el documento de la aplicación cliente.

[COleClientItem](../mfc/reference/coleclientitem-class.md) define varias funciones reemplazables que se llaman en respuesta a solicitudes de la aplicación de componente, que también se denomina la aplicación de servidor. Estas funciones reemplazables suelen actúan como notificaciones. Informarán de la aplicación contenedora de diversos eventos, como el desplazamiento, la activación o un cambio de posición y de los cambios que realice el usuario al editar o manipular el elemento.

El marco de trabajo notifica a la aplicación de contenedor de los cambios a través de una llamada a `COleClientItem::OnChange`, una función reemplazable cuya implementación se requiere. Esta función protegida recibe dos argumentos. El primero especifica el motivo por que el servidor puede cambiar el elemento:

|notificación|Significado|
|------------------|-------------|
|**OLE_CHANGED**|Apariencia del elemento OLE ha cambiado.|
|**OLE_SAVED**|Se ha guardado el elemento OLE.|
|**OLE_CLOSED**|Se cerró el elemento OLE.|
|**OLE_RENAMED**|Se ha cambiado el documento del servidor que contiene el elemento OLE.|
|**OLE_CHANGED_STATE**|El elemento OLE ha cambiado de un estado a otro.|
|**OLE_CHANGED_ASPECT**|Aspecto de dibujo del elemento OLE se cambió el marco de trabajo.|

Estos valores están comprendidos entre el **OLE_NOTIFICATION** enumeración, que se define en el archivo AFXOLE. H.

El segundo argumento a esta función especifica cómo ha cambiado el elemento o qué estado que ha entrado en:

|Cuando el primer argumento es|Segundo argumento|
|----------------------------|---------------------|
|**OLE_SAVED** o **OLE_CLOSED**|No se utiliza.|
|**OLE_CHANGED**|Especifica el aspecto del elemento OLE que ha cambiado.|
|**OLE_CHANGED_STATE**|Describe el estado que se escribió (*emptyState*, *loadedState*, *openState*, *activeState*, o  *activeUIState*).|

Para obtener más información acerca de los Estados que puede suponer un elemento de cliente, consulte [contenedores: Estados de elementos de cliente](../mfc/containers-client-item-states.md).

Las llamadas de framework `COleClientItem::OnGetItemPosition` cuando se está activando un elemento para su edición en contexto. Implementación es necesaria para las aplicaciones que admiten la edición en contexto. El Asistente para aplicaciones MFC proporciona una implementación básica, que asigna las coordenadas del elemento en el `CRect` objeto que se pasa como argumento a `OnGetItemPosition`.

Si cambia el tamaño o posición de un elemento OLE durante la edición en contexto, se debe actualizar la información del contenedor sobre rectángulos de recorte y la posición del elemento y el servidor debe recibir información sobre los cambios. Las llamadas de framework `COleClientItem::OnChangeItemPosition` para este propósito. El Asistente para aplicaciones MFC proporciona una invalidación que llama a la función de la clase base. Debe editar la función que escribe el Asistente para aplicaciones para su `COleClientItem`-clase derivada para que la función actualiza cualquier información retenida por el objeto de elementos de cliente.

## <a name="see-also"></a>Vea también

[Contenedores](../mfc/containers.md)<br/>
[Contenedores: estados de elementos de cliente](../mfc/containers-client-item-states.md)<br/>
[COleClientItem::OnChangeItemPosition](../mfc/reference/coleclientitem-class.md#onchangeitemposition)
