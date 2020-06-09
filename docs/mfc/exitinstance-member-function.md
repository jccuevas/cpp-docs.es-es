---
title: ExitInstance Member (Función)
ms.date: 11/04/2016
f1_keywords: []
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
ms.openlocfilehash: 58546d26293ad48a39a36b98ba4bfdabb68385ee
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622698"
---
# <a name="exitinstance-member-function"></a>ExitInstance Member (Función)

Se llama a la función miembro [ExitInstance](reference/cwinapp-class.md#exitinstance) de la clase [CWinApp](reference/cwinapp-class.md) cada vez que finaliza una copia de la aplicación, normalmente como resultado de que el usuario salga de la aplicación.

Reemplace `ExitInstance` si necesita un procesamiento de limpieza especial, como la liberación de recursos de la interfaz de dispositivo gráfico (GDI) o la desasignación de memoria que se usa durante la ejecución del programa. La limpieza de elementos estándar, como documentos y vistas, se proporciona mediante el marco de trabajo, con otras funciones reemplazables para realizar una limpieza especial específica de esos objetos.

## <a name="see-also"></a>Consulte también

[CWinApp: la clase Application](cwinapp-the-application-class.md)
