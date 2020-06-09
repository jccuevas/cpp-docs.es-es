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
ms.openlocfilehash: cfad635c2a826c6f57e2e1513d753a4083494dee
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618782"
---
# <a name="general-class-design-philosophy"></a>Filosofía general de diseño de clases

Microsoft Windows se diseñó durante mucho tiempo antes de que se convirtiera en el lenguaje C++. Dado que miles de aplicaciones usan la interfaz de programación de aplicaciones (API) de Windows en lenguaje C, esa interfaz se mantendrá para el futuro previsible. Por lo tanto, cualquier interfaz de Windows de C++ se debe crear sobre la API del lenguaje C de procedimientos. Esto garantiza que las aplicaciones de C++ podrán coexistir con aplicaciones de C.

El biblioteca MFC es una interfaz orientada a objetos a Windows que cumple los siguientes objetivos de diseño:

- Reducción significativa en el esfuerzo de escribir una aplicación para Windows.

- Velocidad de ejecución comparable a la de la API del lenguaje C.

- Sobrecarga mínima de tamaño de código.

- Capacidad de llamar directamente a cualquier función de Windows C.

- Conversión más sencilla de aplicaciones de C existentes a C++.

- Capacidad de aprovecharse de la base existente de la experiencia de programación de Windows en lenguaje C.

- Uso más sencillo de la API de Windows con C++ que con C.

- Más fáciles de usar, pero eficaces abstracciones de características complicadas, como controles ActiveX, compatibilidad con bases de datos, impresión, barras de herramientas y barras de estado.

- Verdadera API de Windows para C++ que usa eficazmente las características del lenguaje C++.

Para obtener más información sobre el diseño de la biblioteca MFC, vea:

- [Marco de trabajo de la aplicación](application-framework.md)

- [Relación con la API del lenguaje C](relationship-to-the-c-language-api.md)

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)
