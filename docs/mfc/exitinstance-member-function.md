---
title: Función miembro ExitInstance | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords: []
dev_langs:
- C++
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 954d2248061ec571d9d2ba8804c1f7c97275cbfc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343504"
---
# <a name="exitinstance-member-function"></a>ExitInstance Member (Función)
El [ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) función miembro de clase [CWinApp](../mfc/reference/cwinapp-class.md) se llama cada vez que finaliza una copia de la aplicación, normalmente porque el usuario salir de la aplicación.  
  
 Invalidar `ExitInstance` si necesita procesamiento de la operación de limpieza especial, como liberar recursos de interfaz (GDI) de dispositivo de gráficos o desasignar memoria utilizada durante la ejecución del programa. Limpieza de los elementos estándar, como documentos y vistas, sin embargo, se proporciona mediante el marco de trabajo, con otras funciones reemplazables para realizar labores de limpieza específicas a esos objetos.  
  
## <a name="see-also"></a>Vea también  
 [CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)
