---
title: 'How to: Create a Message Map for a Template (Clase)'
ms.date: 11/04/2016
helpviewer_keywords:
- template classes [MFC], creating message maps
- message maps [MFC], template classes
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
ms.openlocfilehash: 65ddc77b4e8fd466c7d651e54e93a504b4858da1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620071"
---
# <a name="how-to-create-a-message-map-for-a-template-class"></a>How to: Create a Message Map for a Template (Clase)

La asignación de mensajes en MFC proporciona una manera eficaz de dirigir los mensajes de Windows a una instancia de objeto de C++ adecuada. Algunos ejemplos de destinos de mapa de mensajes de MFC son las clases de aplicación, las clases de documento y de vista, las clases de control, etc.

Los mapas de mensajes de MFC tradicionales se declaran mediante la macro [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) para declarar el inicio del mapa de mensajes, una entrada de macro para cada método de clase de controlador de mensajes y, por último, la macro [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map) para declarar el final del mapa de mensajes.

Una limitación con la macro [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) se produce cuando se utiliza junto con una clase que contiene argumentos de plantilla. Cuando se usa con una clase de plantilla, esta macro producirá un error en tiempo de compilación debido a que faltan parámetros de plantilla durante la expansión de la macro. La macro de [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map) se ha diseñado para permitir que las clases que contienen un único argumento de plantilla declaren sus propios mapas de mensajes.

## <a name="example"></a>Ejemplo

Considere un ejemplo en el que la clase [CListBox](reference/clistbox-class.md) de MFC se extiende para proporcionar la sincronización con un origen de datos externo. La `CSyncListBox` clase ficticia se declara de la siguiente manera:

[!code-cpp[NVC_MFC_CListBox#42](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_1.h)]

La `CSyncListBox` clase tiene una plantilla en un tipo único que describe el origen de datos con el que se sincronizará. También declara tres métodos que participarán en el mapa de mensajes de la clase: `OnPaint` , `OnDestroy` y `OnSynchronize` . El `OnSynchronize` método se implementa de la siguiente manera:

[!code-cpp[NVC_MFC_CListBox#43](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_2.cpp)]

La implementación anterior permite que la `CSyncListBox` clase se especializa en cualquier tipo de clase que implementa el `GetCount` método, como `CArray` , `CList` y `CMap` . La `StringizeElement` función es una función de plantilla con prototipos de lo siguiente:

[!code-cpp[NVC_MFC_CListBox#44](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_3.cpp)]

Normalmente, el mapa de mensajes para esta clase se definiría como:

```cpp
BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)
  ON_WM_PAINT()
  ON_WM_DESTROY()
  ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)
END_MESSAGE_MAP()
```

donde **LBN_SYNCHRONIZE** es un mensaje de usuario personalizado definido por la aplicación, como:

[!code-cpp[NVC_MFC_CListBox#45](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_4.cpp)]

El mapa de macros anterior no se compilará, debido a que la especificación de la plantilla para la clase no estará `CSyncListBox` disponible durante la expansión de la macro. La macro **BEGIN_TEMPLATE_MESSAGE_MAP** resuelve este paso mediante la incorporación del parámetro de plantilla especificado en el mapa de macros expandido. El mapa de mensajes de esta clase se convierte en:

[!code-cpp[NVC_MFC_CListBox#46](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_5.cpp)]

A continuación se muestra el uso de ejemplo de la `CSyncListBox` clase mediante un `CStringList` objeto:

[!code-cpp[NVC_MFC_CListBox#47](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_6.cpp)]

Para completar la prueba, la `StringizeElement` función debe estar especializada para trabajar con la `CStringList` clase:

[!code-cpp[NVC_MFC_CListBox#48](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_7.cpp)]

## <a name="see-also"></a>Consulte también

[BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)<br/>
[Control y asignación de mensajes](message-handling-and-mapping.md)
