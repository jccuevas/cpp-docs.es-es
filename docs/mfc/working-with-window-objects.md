---
title: Trabajar con objetos Window | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- child windows [MFC], working with
- window objects [MFC], working with
ms.assetid: f73aa254-90e3-46a9-8e9b-d78b7054a331
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 55f3eae10954ee2da1386907f88ae8b594dc8e53
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413638"
---
# <a name="working-with-window-objects"></a>Trabajar con objetos Window

Trabajo con ventanas requiere dos tipos de actividad:

- Mensajes de control de Windows

- En la ventana de dibujo

Para controlar los mensajes de Windows en cualquier ventana, incluidas sus propias ventanas secundarias, consulte [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md) para asignar los mensajes a la clase de C++. A continuación, escriba al controlador de mensajes funciones miembro en la clase.

La mayoría de dibujo en una aplicación de framework se produce en la vista, cuyo [OnDraw](../mfc/reference/cview-class.md#ondraw) función miembro se llama cada vez que se debe dibujar el contenido de la ventana. Si la ventana es un elemento secundario de la vista, puede delegar algunas de dibujo de la vista en la ventana secundaria al tener `OnDraw` llamar a una de las funciones de miembro de la ventana.

En cualquier caso, necesitará un contexto de dispositivo para dibujar. Puede usar el lápiz de cotizaciones, pincel y otros objetos gráficos incluidos en el contexto de dispositivo asociado a la ventana. O bien, puede modificar estos objetos para obtener los efectos de dibujo que necesita. Con el contexto de dispositivo configurado como desee, llamar a funciones miembro de clase [CDC](../mfc/reference/cdc-class.md) (clase de contexto de dispositivo) para dibujar líneas, formas y texto; utilice colores; y para trabajar con un sistema de coordenadas.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Controlar y asignar mensajes](../mfc/message-handling-and-mapping.md)

- [Dibujar en una vista](../mfc/drawing-in-a-view.md)

- [Contextos de dispositivo](../mfc/device-contexts.md)

- [Objetos gráficos](../mfc/graphic-objects.md)

## <a name="see-also"></a>Vea también

[Objetos de ventana](../mfc/window-objects.md)

