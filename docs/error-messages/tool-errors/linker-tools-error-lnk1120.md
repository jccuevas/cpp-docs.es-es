---
title: Error de las herramientas del vinculador LNK1120
ms.date: 05/17/2017
f1_keywords:
- LNK1120
helpviewer_keywords:
- LNK1120
ms.assetid: 56aa7d36-921f-4daf-b44d-cca0d4fb1b51
ms.openlocfilehash: b11318dcffb665d3b422fffcbd7e6275f35984dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255110"
---
# <a name="linker-tools-error-lnk1120"></a>Error de las herramientas del vinculador LNK1120

> *número* externos sin resolver

El error LNK1120 notifica el recuento (*número*) de los errores de símbolo externo sin resolver de esta operación de enlace. La mayoría sin resolver errores de símbolo externo se notifican individualmente por [Error de las herramientas del vinculador LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md) y [Error de las herramientas del vinculador LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md), que preceden a este mensaje de error, una vez para cada externo sin resolver error de símbolo.

Para corregir este error, corrija todos los demás errores externos sin resolver o de otros errores del vinculador que lo preceden en la salida de compilación. No se notifica este error cuando no hay errores externos sin resolver permanecen.
