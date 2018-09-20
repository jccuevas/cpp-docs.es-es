---
title: Filosofía general de diseño de clase | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8fe64ee4d9e6fc678d97c3e9fe37a85e53807541
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416648"
---
# <a name="general-class-design-philosophy"></a>Filosofía general de diseño de clases

Microsoft Windows se diseñaron mucho antes de que se hizo popular el lenguaje C++. Dado que miles de aplicaciones utilizan la interfaz de programación de aplicaciones (API) de Windows del lenguaje C, esa interfaz se mantendrá en el futuro inmediato. Cualquier interfaz de Windows de C++, por tanto, debe compilarse sobre la API del lenguaje C procedimientos. Esto garantiza que las aplicaciones de C++ podrán coexistir con aplicaciones de C.

La biblioteca Microsoft Foundation Class es una interfaz orientada a objetos para Windows que cumpla los objetivos de diseño siguientes:

- Reducción significativa en el esfuerzo necesario para escribir una aplicación para Windows.

- Velocidad de ejecución es comparable a la de la API del lenguaje C.

- Sobrecarga de tamaño mínimo de código.

- Capacidad de llamar directamente a cualquier función de C de Windows.

- Conversión más fácil de las aplicaciones existentes de C a C++.

- Capacidad de aprovechar de la base de la experiencia de programación de Windows de lenguaje C existente.

- Simplificar su uso de la API de Windows con C++ que con C.

- Más fácil de utilizar pero eficaz abstracciones de complicadas funciones como controles ActiveX, compatibilidad con la base de datos, impresión, las barras de herramientas y barras de estado.

- API de Windows es True para C++ que utiliza características del lenguaje C++ de forma eficaz.

Para obtener más información sobre el diseño de la biblioteca MFC, vea:

- [El marco de aplicación](../mfc/application-framework.md)

- [Relación con la API del lenguaje C](../mfc/relationship-to-the-c-language-api.md)

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)

