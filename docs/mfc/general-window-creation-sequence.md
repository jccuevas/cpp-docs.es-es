---
title: Secuencia de creación de ventanas general
ms.date: 11/04/2016
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
ms.openlocfilehash: fb10ced78e230316a6e2982f24c1fb6e2e52ed8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364273"
---
# <a name="general-window-creation-sequence"></a>Secuencia de creación de ventanas general

Cuando se crea una ventana propia, como una ventana secundaria, el marco de trabajo utiliza el mismo proceso que el descrito en Creación de [documento/vista](../mfc/document-view-creation.md).

Todas las clases de ventana proporcionadas por MFC emplean [la construcción en dos etapas.](../mfc/one-stage-and-two-stage-construction-of-objects.md) Es decir, durante una invocación del **operador new** C++, el constructor asigna e inicializa un objeto C++, pero no crea una ventana de Windows correspondiente. Esto se hace después mediante una llamada a la [Create](../mfc/reference/cwnd-class.md#create) función miembro del objeto de ventana.

La `Create` función miembro hace que `HWND` la ventana de Windows y almacena su en el miembro de datos públicos del objeto C++ [m_hWnd](../mfc/reference/cwnd-class.md#m_hwnd). `Create`proporciona una flexibilidad completa sobre los parámetros de creación. Antes `Create`de llamar a , es posible que desee registrar una clase de ventana con la función global [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) para establecer el icono y los estilos de clase para el marco.

Para las ventanas de marco, puede `Create`utilizar la función miembro [LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) en lugar de . `LoadFrame`hace que la ventana de Windows con menos parámetros. Obtiene muchos valores predeterminados de los recursos, incluidos el título, el icono, la tabla de aceleradores y el menú del marco.

> [!NOTE]
> El icono, la tabla de aceleradores y los recursos de menú deben tener un identificador de recurso común, como **IDR_MAINFRAME**, para que LoadFrame los cargue.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué quieres saber más sobre

- [Objetos de ventana](../mfc/window-objects.md)

- [Registro de la ventana "clases"](../mfc/registering-window-classes.md)

- [Destruir objetos de ventana](../mfc/destroying-window-objects.md)

- [Creación de ventanas de marco de documento](../mfc/creating-document-frame-windows.md)

## <a name="see-also"></a>Consulte también

[Crear ventanas](../mfc/creating-windows.md)
