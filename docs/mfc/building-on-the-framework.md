---
title: Compilar en el marco
ms.date: 11/04/2016
helpviewer_keywords:
- application-specific classes [MFC]
- application framework [MFC], building applications
- applications [MFC]
- MFC, application development
ms.assetid: 883f0f19-866f-4221-8a3d-5607941dc8d0
ms.openlocfilehash: 2c171b223892c8bca1b32e18c57c09027558c192
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619734"
---
# <a name="building-on-the-framework"></a>Compilar en el marco

El rol en la configuración de una aplicación con el marco de trabajo de MFC es proporcionar el código fuente específico de la aplicación y conectar los componentes definiendo los mensajes y los comandos a los que responden. Utilice el lenguaje C++ y las técnicas estándar de C++ para derivar sus propias clases específicas de la aplicación de las proporcionadas por la biblioteca de clases y para reemplazar y aumentar el comportamiento de la clase base.

En los temas relacionados, en las tablas siguientes se describe la secuencia general de operaciones que suele seguir y sus responsabilidades frente a las responsabilidades del marco:

- [Secuencia para compilar una aplicación con el marco de trabajo](sequence-of-operations-for-building-mfc-applications.md)

- [Secuencia de operaciones para crear aplicaciones OLE](sequence-of-operations-for-creating-ole-applications.md)

- [Secuencia de operaciones para crear controles ActiveX](sequence-of-operations-for-creating-activex-controls.md)

- [Secuencia de operaciones para crear aplicaciones de base de datos](sequence-of-operations-for-creating-database-applications.md)

En su mayor parte, puede seguir estas tablas como una secuencia de pasos para crear una aplicación MFC, aunque algunos de los pasos son opciones alternativas. Por ejemplo, la mayoría de las aplicaciones usan un tipo de clase de vista de los diversos tipos disponibles.

## <a name="see-also"></a>Consulte también

[Temas generales de MFC](general-mfc-topics.md)
