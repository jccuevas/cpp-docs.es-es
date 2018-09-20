---
title: Función miembro ExitInstance | Microsoft Docs
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
ms.openlocfilehash: da411fbecdea0a1e7b8976ca119057204693a9bd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387866"
---
# <a name="exitinstance-member-function"></a>ExitInstance Member (Función)

El [ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) función miembro de clase [CWinApp](../mfc/reference/cwinapp-class.md) se llama cada vez que finaliza una copia de la aplicación, normalmente como resultado el usuario salga de la aplicación.

Invalidar `ExitInstance` si necesita procesamiento de limpieza especial, como liberar recursos de interfaz (GDI) de dispositivo de gráficos o desasignar memoria utilizada durante la ejecución del programa. Sin embargo, la limpieza de los elementos estándar, como documentos y vistas, se proporciona el marco de trabajo, con otras funciones reemplazables para realizar labores de limpieza específicas a esos objetos.

## <a name="see-also"></a>Vea también

[CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)
