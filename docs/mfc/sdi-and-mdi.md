---
title: SDI y MDI
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], SDI applications
- frame windows [MFC], MDI applications
- MFC, windows
- single document interface (SDI) [MFC], applications
- MDI [MFC], vs. SDI
ms.assetid: bb7239d9-4759-4f63-bfff-44a04b48c067
ms.openlocfilehash: 9730e7baf9589c4b05a60703c619aae2e941bdec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372755"
---
# <a name="sdi-and-mdi"></a>SDI y MDI

MFC facilita el trabajo con aplicaciones de interfaz de documento único (SDI) e interfaz de varios documentos (MDI).

Las aplicaciones SDI solo permiten una ventana de marco de documento abierta a la vez. Las aplicaciones MDI permiten que se abran varias ventanas de marco de documento en la misma instancia de una aplicación. Una aplicación MDI tiene una ventana dentro de la cual se pueden abrir varias ventanas secundarias MDI, que son ventanas de marco, cada una con un documento independiente. En algunas aplicaciones, las ventanas secundarias pueden ser de diferentes tipos, como ventanas de gráficos y ventanas de hoja de cálculo. En ese caso, la barra de menús puede cambiar a medida que se activan las ventanas secundarias MDI de diferentes tipos.

> [!NOTE]
> En Windows 95 y versiones posteriores, las aplicaciones suelen ser SDI porque el sistema operativo ha adoptado una vista "centrada en documentos".

Para obtener más información, vea [Documentos, vistas y marco de trabajo](../mfc/documents-views-and-the-framework.md).

## <a name="see-also"></a>Consulte también

[Uso de las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
