---
title: ExitInstance Member (Función)
ms.date: 11/04/2016
f1_keywords: []
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
ms.openlocfilehash: c76f588b22ad8ffd1d3dae954c5113feffb62a3f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405825"
---
# <a name="exitinstance-member-function"></a>ExitInstance Member (Función)

El [ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) función miembro de clase [CWinApp](../mfc/reference/cwinapp-class.md) se llama cada vez que finaliza una copia de la aplicación, normalmente como resultado el usuario salga de la aplicación.

Invalidar `ExitInstance` si necesita procesamiento de limpieza especial, como liberar recursos de interfaz (GDI) de dispositivo de gráficos o desasignar memoria utilizada durante la ejecución del programa. Sin embargo, la limpieza de los elementos estándar, como documentos y vistas, se proporciona el marco de trabajo, con otras funciones reemplazables para realizar labores de limpieza específicas a esos objetos.

## <a name="see-also"></a>Vea también

[CWinApp: La clase Application](../mfc/cwinapp-the-application-class.md)
