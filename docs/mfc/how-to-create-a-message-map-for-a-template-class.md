---
title: "How to: Create a Message Map for a Template (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mapas de mensajes, clases de plantillas"
  - "clases de plantillas, crear mapas de mensajes"
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# How to: Create a Message Map for a Template (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Asignación de mensajes en MFC proporciona una manera eficaz de tratar los mensajes de Windows en una instancia de objeto adecuada de C\+\+.  Los ejemplos de mapa de mensajes MFC incluyen clases de la aplicación, el documento y las clases de vista, clases de control, y así sucesivamente.  
  
 Los mapas tradicionales de mensajes MFC se declaran con la macro de [BEGIN\_MESSAGE\_MAP](../Topic/BEGIN_MESSAGE_MAP.md) para declarar el inicio del mapa de mensajes, entrada de macro para cada método de la clase de controlador de mensajes, y por último de la macro de [END\_MESSAGE\_MAP](../Topic/END_MESSAGE_MAP.md) de declarar el final del mapa de mensajes.  
  
 Una limitación con la macro de [BEGIN\_MESSAGE\_MAP](../Topic/BEGIN_MESSAGE_MAP.md) aparece cuando se utiliza junto con una clase que contiene los argumentos de plantilla.  Cuando se utiliza con una clase de plantilla, esta macro producirá un error en tiempo de compilación debido a los parámetros que faltan de plantilla durante la expansión de macro.  La macro de [BEGIN\_TEMPLATE\_MESSAGE\_MAP](../Topic/BEGIN_TEMPLATE_MESSAGE_MAP.md) está diseñada para permitir las clases que contienen un solo argumento de plantilla para declarar mapas de mensajes.  
  
## Ejemplo  
 Considere un ejemplo donde la clase MFC [CListBox](../mfc/reference/clistbox-class.md) se extiende para proporcionar la sincronización con un origen de datos externo.  Se declara la clase ficticia de **CSyncListBox** como sigue:  
  
 [!code-cpp[NVC_MFC_CListBox#42](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_1.h)]  
  
 La clase de **CSyncListBox** plantilla en un tipo único que describe el origen de datos que se sincronizará con.  También declara tres métodos que participan en el mapa de mensajes de la clase: **OnPaint**, **OnDestroy**, y **OnSynchronize**.  Se implementa el método de **OnSynchronize** como sigue:  
  
 [!code-cpp[NVC_MFC_CListBox#43](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_2.cpp)]  
  
 La implementación anterior permite que la clase de **CSyncListBox** sea especializada en cualquier tipo de clase que implemente el método de **GetCount** , como **CArray**, **CList**, y **CMap**.  La función de **StringizeElement** es una función de plantilla prototipo mediante:  
  
 [!code-cpp[NVC_MFC_CListBox#44](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_3.cpp)]  
  
 Normalmente, el mapa de mensajes para esta clase se definiría como:  
  
 `BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)`  
  
 `ON_WM_PAINT()`  
  
 `ON_WM_DESTROY()`  
  
 `ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)`  
  
 `END_MESSAGE_MAP()`  
  
 donde es un mensaje **LBN\_SYNCHRONIZE** de usuario personalizado definido por la aplicación, por ejemplo:  
  
 [!code-cpp[NVC_MFC_CListBox#45](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_4.cpp)]  
  
 El mapa anterior de la macro no se compilará, debido al hecho de que la especificación de plantilla para la clase de **CSyncListBox** faltará durante la expansión de macro.  La macro de **BEGIN\_TEMPLATE\_MESSAGE\_MAP** soluciona esto especificando el parámetro de plantilla especificado en el mapa expandida de la macro.  El mapa de mensajes para esta clase se convierte en:  
  
 [!code-cpp[NVC_MFC_CListBox#46](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_5.cpp)]  
  
 A continuación se muestra el ejemplo del uso de la clase de **CSyncListBox** utilizando un objeto de **CStringList** :  
  
 [!code-cpp[NVC_MFC_CListBox#47](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_6.cpp)]  
  
 Para completar la prueba, la función de **StringizeElement** debe especializar para trabajar con la clase de **CStringList** :  
  
 [!code-cpp[NVC_MFC_CListBox#48](../mfc/codesnippet/CPP/how-to-create-a-message-map-for-a-template-class_7.cpp)]  
  
## Vea también  
 [BEGIN\_TEMPLATE\_MESSAGE\_MAP](../Topic/BEGIN_TEMPLATE_MESSAGE_MAP.md)   
 [Controlar y asignar mensajes](../mfc/message-handling-and-mapping.md)