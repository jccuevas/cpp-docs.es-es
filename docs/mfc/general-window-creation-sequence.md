---
title: Secuencia de creación de ventanas general
ms.date: 11/04/2016
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
ms.openlocfilehash: 0b09543d659448454bbc7c2cca6abee5de3013e5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618752"
---
# <a name="general-window-creation-sequence"></a>Secuencia de creación de ventanas general

Cuando se crea una ventana propia, como una ventana secundaria, el marco de trabajo usa mucho el mismo proceso que el que se describe en [creación de documentos y vistas](document-view-creation.md).

Todas las clases de ventana proporcionadas por MFC emplean la [construcción en dos fases](one-stage-and-two-stage-construction-of-objects.md). Es decir, durante una invocación del operador **New** de c++, el constructor asigna e inicializa un objeto de c++, pero no crea una ventana de Windows correspondiente. Esto se hace después mediante una llamada a la función miembro [Create](reference/cwnd-class.md#create) del objeto Window.

La `Create` función miembro hace que la ventana de Windows y almacene su `HWND` en el miembro de datos público del objeto de C++ [m_hWnd](reference/cwnd-class.md#m_hwnd). `Create`proporciona una flexibilidad completa sobre los parámetros de creación. Antes de llamar a `Create` , es posible que desee registrar una clase de ventana con la función global [AfxRegisterWndClass (](reference/application-information-and-management.md#afxregisterwndclass) para establecer el icono y los estilos de clase para el marco.

En el caso de las ventanas de marco, puede usar la función miembro [LoadFrame](reference/cframewnd-class.md#loadframe) en lugar de `Create` . `LoadFrame`hace que la ventana de Windows use menos parámetros. Obtiene muchos valores predeterminados de los recursos, como el título, el icono, la tabla de aceleradores y el menú del marco.

> [!NOTE]
> El icono, la tabla de aceleradores y los recursos de menú deben tener un identificador de recurso común, como **IDR_MAINFRAME**, para que los cargue LoadFrame.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Objetos de ventana](window-objects.md)

- [Registrando "clases" de ventana](registering-window-classes.md)

- [Destruir objetos Window](destroying-window-objects.md)

- [Crear ventanas de marco de documento](creating-document-frame-windows.md)

## <a name="see-also"></a>Consulte también

[Crear ventanas](creating-windows.md)
