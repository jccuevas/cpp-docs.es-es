---
title: Compilar en el marco | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- application-specific classes [MFC]
- application framework [MFC], building applications
- applications [MFC]
- MFC, application development
ms.assetid: 883f0f19-866f-4221-8a3d-5607941dc8d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ca0ebd9bf03df8725c14df8d2aca1f7858b7b65
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396186"
---
# <a name="building-on-the-framework"></a>Compilar en el marco

Su rol en la configuración de una aplicación con el marco de trabajo MFC es proporcionar el código fuente específica de la aplicación y para conectar los componentes definiendo qué mensajes y comandos a la que responden. Usar el lenguaje C++ y las técnicas estándar de C++ para derivar sus propias clases específicas de la aplicación de las proporcionadas por la biblioteca de clases y para invalidar y aumentar el comportamiento de la clase base.

En otros temas relacionados, las tablas siguientes describen la secuencia general de las operaciones que normalmente se siguen y sus responsabilidades frente a las responsabilidades de .NET framework:

- [Secuencia para la creación de una aplicación con el marco de trabajo](../mfc/sequence-of-operations-for-building-mfc-applications.md)

- [Secuencia de operaciones para crear aplicaciones OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)

- [Secuencia de operaciones para crear controles ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)

- [Secuencia de operaciones para crear aplicaciones de base de datos](../mfc/sequence-of-operations-for-creating-database-applications.md)

En su mayor parte, puede seguir estas tablas como una secuencia de pasos para crear una aplicación MFC, aunque algunos de los pasos son opciones alternativas. Por ejemplo, la mayoría de las aplicaciones usa un tipo de clase de vista de los diferentes tipos disponibles.

## <a name="see-also"></a>Vea también

[Temas generales de MFC](../mfc/general-mfc-topics.md)

