---
title: "Función miembro ExitInstance | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: 
dev_langs: C++
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 99898a5e80c3f487c7f53fe81d13d3d1eb55ebd5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="exitinstance-member-function"></a>ExitInstance Member (Función)
El [ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) función miembro de clase [CWinApp](../mfc/reference/cwinapp-class.md) se llama cada vez que finaliza una copia de la aplicación, normalmente porque el usuario salir de la aplicación.  
  
 Invalidar `ExitInstance` si necesita procesamiento de la operación de limpieza especial, como liberar recursos de interfaz (GDI) de dispositivo de gráficos o desasignar memoria utilizada durante la ejecución del programa. Limpieza de los elementos estándar, como documentos y vistas, sin embargo, se proporciona mediante el marco de trabajo, con otras funciones reemplazables para realizar labores de limpieza específicas a esos objetos.  
  
## <a name="see-also"></a>Vea también  
 [CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)
