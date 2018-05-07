---
title: 'Cómo: crear un mapa de mensajes para una clase de plantilla | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- template classes [MFC], creating message maps
- message maps [MFC], template classes
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6781ca14b174608a815a0300750dd6a3d9aa96bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-message-map-for-a-template-class"></a>How to: Create a Message Map for a Template (Clase)
Asignación de mensajes en MFC proporciona una manera eficaz para dirigir los mensajes de Windows a una instancia de objeto de C++ adecuada. Algunos ejemplos de destinos de mapa de mensajes MFC son las clases de aplicación, clases de documento y vista, clases de controles y así sucesivamente.  
  
 Mapas de mensajes MFC tradicionales se declaran mediante la [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) macro para declarar el inicio del mapa de mensajes, una entrada de macro de cada método de clase de controlador de mensajes y, finalmente, la [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)macro para declarar el final de la asignación de mensaje.  
  
 Una limitación con la [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) macro se produce cuando se utiliza junto con una clase que contiene los argumentos de plantilla. Cuando se utiliza con una clase de plantilla, esta macro provocará un error en tiempo de compilación debido a los parámetros de plantilla que faltan durante la expansión de macro. El [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map) macro se ha diseñado para permitir que asigna las clases que contienen un argumento de plantilla único para declarar su propio mensaje.  
  
## <a name="example"></a>Ejemplo  
 Considere un ejemplo donde la MFC [CListBox](../mfc/reference/clistbox-class.md) clase se ha ampliado para proporcionar una sincronización con un origen de datos externo. El ficticio **CSyncListBox** clase se declara como sigue:  
  
 [!code-cpp[NVC_MFC_CListBox#42](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_1.h)]  
  
 El **CSyncListBox** tiene asignada una plantilla en un único tipo que describe el origen de datos se sincronizarán con la clase. También declara tres métodos que vaya a participar en el mapa de mensajes de la clase: **OnPaint**, **OnDestroy**, y **OnSynchronize**. El **OnSynchronize** método se implementa como sigue:  
  
 [!code-cpp[NVC_MFC_CListBox#43](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_2.cpp)]  
  
 La implementación anterior permite la **CSyncListBox** clase especializadas en cualquier tipo de clase que implementa el **GetCount** método, como **CArray**, **CList**, y **CMap**. El **StringizeElement** es una función de plantilla prototipo por el texto siguiente:  
  
 [!code-cpp[NVC_MFC_CListBox#44](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_3.cpp)]  
  
 Normalmente, el mapa de mensajes para esta clase se definiría como:  
  
 `BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)`  
  
 `ON_WM_PAINT()`  
  
 `ON_WM_DESTROY()`  
  
 `ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)`  
  
 `END_MESSAGE_MAP()`  
  
 donde **LBN_SYNCHRONIZE** es un mensaje de usuario personalizado definido por la aplicación, como:  
  
 [!code-cpp[NVC_MFC_CListBox#45](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_4.cpp)]  
  
 El mapa de macro anterior no se compilará, debido al hecho de que la especificación de la plantilla para la **CSyncListBox** clase se perderá durante la expansión de macro. El **BEGIN_TEMPLATE_MESSAGE_MAP** macro se resuelve este problema si se incorpora el parámetro de plantilla especificada en el mapa de la macro expandida. El mapa de mensajes para esta clase se convierte en:  
  
 [!code-cpp[NVC_MFC_CListBox#46](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_5.cpp)]  
  
 El siguiente ejemplo muestra el uso del ejemplo de la **CSyncListBox** clase mediante un **objeto CStringList** objeto:  
  
 [!code-cpp[NVC_MFC_CListBox#47](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_6.cpp)]  
  
 Para completar la prueba, el **StringizeElement** función debe haberse especializada para trabajar con la **objeto CStringList** clase:  
  
 [!code-cpp[NVC_MFC_CListBox#48](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_7.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)   
 [Control y asignación de mensajes](../mfc/message-handling-and-mapping.md)

