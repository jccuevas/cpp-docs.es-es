---
title: Filosofía general de diseño de clases
ms.date: 11/04/2016
helpviewer_keywords:
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
ms.openlocfilehash: 34a173802e3fa43615c05da4ce747592f851228f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441190"
---
# <a name="general-class-design-philosophy"></a>Filosofía general de diseño de clases

Microsoft Windows se diseñó durante mucho tiempo C++ antes de que el lenguaje se convirtiera en popular. Dado que miles de aplicaciones usan la interfaz de programación de aplicaciones (API) de Windows en lenguaje C, esa interfaz se mantendrá para el futuro previsible. Por C++ lo tanto, cualquier interfaz de Windows se debe crear sobre la API del lenguaje C de procedimientos. Esto garantiza que C++ las aplicaciones puedan coexistir con aplicaciones de C.

El biblioteca MFC es una interfaz orientada a objetos a Windows que cumple los siguientes objetivos de diseño:

- Reducción significativa en el esfuerzo de escribir una aplicación para Windows.

- Velocidad de ejecución comparable a la de la API del lenguaje C.

- Sobrecarga mínima de tamaño de código.

- Capacidad de llamar directamente a cualquier función de Windows C.

- Conversión más sencilla de aplicaciones de C C++existentes en.

- Capacidad de aprovecharse de la base existente de la experiencia de programación de Windows en lenguaje C.

- Uso más sencillo de la API de C++ Windows con que con C.

- Más fáciles de usar, pero eficaces abstracciones de características complicadas, como controles ActiveX, compatibilidad con bases de datos, impresión, barras de herramientas y barras de estado.

- Verdadera API de Windows C++ para que utiliza C++ de forma eficaz las características del lenguaje.

Para obtener más información sobre el diseño de la biblioteca MFC, vea:

- [Marco de trabajo de la aplicación](../mfc/application-framework.md)

- [Relación con la API del lenguaje C](../mfc/relationship-to-the-c-language-api.md)

## <a name="see-also"></a>Consulte también

[Información general sobre clases](../mfc/class-library-overview.md)
