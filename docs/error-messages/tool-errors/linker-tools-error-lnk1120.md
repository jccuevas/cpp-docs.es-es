---
title: Las herramientas del vinculador LNK1120 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 05/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1120
dev_langs:
- C++
helpviewer_keywords:
- LNK1120
ms.assetid: 56aa7d36-921f-4daf-b44d-cca0d4fb1b51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fab2b937f8bf941219c678c638e9757903ee7698
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298517"
---
# <a name="linker-tools-error-lnk1120"></a>Error de las herramientas del vinculador LNK1120
*número* externos sin resolver  
  
El error LNK1120 notifica el recuento (*número*) de errores de símbolo externo sin resolver de esta operación de enlace. La mayoría no resuelta se notifican los errores de símbolo externo individualmente por [Error de las herramientas del vinculador LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md) y [Error de las herramientas del vinculador LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md), que preceden a este mensaje de error, una vez por cada externo sin resolver error de símbolo.  
  
Para corregir este error, corrija todos los demás errores externos sin resolver u otros errores del vinculador que lo preceden en la salida de compilación. Este error no se produce cuando no permanecen errores externos sin resolver.  
