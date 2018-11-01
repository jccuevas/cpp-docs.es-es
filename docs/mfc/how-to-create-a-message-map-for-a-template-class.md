---
title: 'How to: Create a Message Map for a Template (Clase)'
ms.date: 11/04/2016
helpviewer_keywords:
- template classes [MFC], creating message maps
- message maps [MFC], template classes
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
ms.openlocfilehash: 437fdf59ae9c9d3428654fc412fd78bf1348a701
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586243"
---
# <a name="how-to-create-a-message-map-for-a-template-class"></a>How to: Create a Message Map for a Template (Clase)

Asignación de mensajes en MFC proporciona una manera eficaz para dirigir los mensajes de Windows a una instancia de objeto de C++ correspondiente. Algunos ejemplos de destinos de mapa de mensajes MFC son las clases de aplicación, clases de documento y vista, las clases de control y así sucesivamente.

Mapas de mensajes MFC tradicionales se declaran mediante la [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) macro para declarar el inicio del mapa de mensajes, una entrada de macro para cada método de clase de controlador de mensajes y, finalmente, el [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)macro para declarar el final del mapa de mensajes.

Una limitación con la [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) macro se produce cuando se utiliza junto con una clase que contiene los argumentos de plantilla. Cuando se usa con una clase de plantilla, esta macro producirá un error de tiempo de compilación debido a que faltan parámetros de plantilla durante la expansión de macro. El [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map) macro se ha diseñado para permitir que asigna las clases que contienen un argumento de plantilla único para declarar su propio mensaje.

## <a name="example"></a>Ejemplo

Considere un ejemplo donde la MFC [CListBox](../mfc/reference/clistbox-class.md) clase se extiende para proporcionar una sincronización con un origen de datos externo. El texto ficticio `CSyncListBox` clase se declara como sigue:

[!code-cpp[NVC_MFC_CListBox#42](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_1.h)]

El `CSyncListBox` es plantilla en un único tipo que describe el origen de datos, se sincronizará con la clase. También declara tres métodos que participarán en el mapa de mensajes de la clase: `OnPaint`, `OnDestroy`, y `OnSynchronize`. El `OnSynchronize` método se implementa como sigue:

[!code-cpp[NVC_MFC_CListBox#43](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_2.cpp)]

La implementación anterior permite el `CSyncListBox` clase especializarse en cualquier tipo de clase que implementa el `GetCount` método, como `CArray`, `CList`, y `CMap`. El `StringizeElement` es una función de plantilla prototipo a lo siguiente:

[!code-cpp[NVC_MFC_CListBox#44](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_3.cpp)]

Normalmente, el mapa de mensajes para esta clase se definiría como:

```cpp
BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)
  ON_WM_PAINT()
  ON_WM_DESTROY()
  ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)
END_MESSAGE_MAP()
```

donde **LBN_SYNCHRONIZE** es un mensaje de usuario personalizado definido por la aplicación, como:

[!code-cpp[NVC_MFC_CListBox#45](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_4.cpp)]

No se compilará el mapa de la macro anterior, debido al hecho de que la especificación de la plantilla para el `CSyncListBox` clase faltará durante la expansión de macro. El **BEGIN_TEMPLATE_MESSAGE_MAP** macro solucionan este problema mediante la incorporación del parámetro de plantilla especificada en el mapa de la macro expandida. El mapa de mensajes para esta clase se convierte en:

[!code-cpp[NVC_MFC_CListBox#46](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_5.cpp)]

El siguiente ejemplo muestra el ejemplo de uso de la `CSyncListBox` clase mediante un `CStringList` objeto:

[!code-cpp[NVC_MFC_CListBox#47](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_6.cpp)]

Para completar la prueba, el `StringizeElement` función debe ser especializada para trabajar con el `CStringList` clase:

[!code-cpp[NVC_MFC_CListBox#48](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_7.cpp)]

## <a name="see-also"></a>Vea también

[BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)<br/>
[Control y asignación de mensajes](../mfc/message-handling-and-mapping.md)

