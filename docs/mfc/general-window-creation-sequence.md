---
title: Secuencia de creación de ventanas general | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9336e5fa19b373f07c54e758a6f939bbc63e50ec
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432794"
---
# <a name="general-window-creation-sequence"></a>Secuencia de creación de ventanas general

Cuando se crea una ventana de la ventana de su elección, como un elemento secundario, el marco usa casi el mismo proceso que se ha descrito en [creación de documento/vista](../mfc/document-view-creation.md).

Todas las clases de ventana proporcionadas por emplear MFC [construcción en dos fases](../mfc/one-stage-and-two-stage-construction-of-objects.md). Es decir, durante una llamada de C++ **nuevo** operador, el constructor asigna y se inicializa un objeto de C++ pero no crea una ventana de Windows correspondiente. Que se realiza más adelante mediante una llamada a la [crear](../mfc/reference/cwnd-class.md#create) función de miembro del objeto de ventana.

El `Create` función miembro hace que la ventana de Windows y almacena su `HWND` en miembro de datos públicos del objeto de C++ [m_hWnd](../mfc/reference/cwnd-class.md#m_hwnd). `Create` le ofrece completos flexibilidad a través de los parámetros de creación. Antes de llamar a `Create`, que es posible que desee registrar una clase de ventana con la función global [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) con el fin de establecer los estilos de icono y de clase para el marco.

Ventanas de marco, puede usar el [LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) función miembro en lugar de `Create`. `LoadFrame` hace que la ventana de Windows con menos parámetros. Obtiene muchos valores predeterminados de recursos, incluido el título del marco, icono, tabla de aceleradores y menús.

> [!NOTE]
>  El icono, tabla de aceleradores y recursos de menú deben tener un identificador de recursos comunes, como **IDR_MAINFRAME**, para que se puedan cargar mediante LoadFrame.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Window (objetos)](../mfc/window-objects.md)

- [Registrar clases de ventana""](../mfc/registering-window-classes.md)

- [Destruir objetos window](../mfc/destroying-window-objects.md)

- [Crear ventanas de marco de documento](../mfc/creating-document-frame-windows.md)

## <a name="see-also"></a>Vea también

[Creación de ventanas](../mfc/creating-windows.md)

