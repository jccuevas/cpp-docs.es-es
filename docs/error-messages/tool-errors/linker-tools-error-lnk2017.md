---
title: Las herramientas del vinculador LNK2017 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2017
dev_langs:
- C++
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 095423b5f2d86cef309ed4316ff72d195b11eb26
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk2017"></a>Error de las herramientas del vinculador LNK2017
reubicación de 'símbolo' a 'segmento' no válido sin/LARGEADDRESSAWARE: no  
  
 Está intentando crear una imagen de 64 bits con direcciones de 32 bits. Para ello, debe:  
  
-   Usar una dirección de carga fija.  
  
-   Restringir la imagen a 3 GB.  
  
-   Especifique [/LARGEADDRESSAWARE: no](../../build/reference/largeaddressaware-handle-large-addresses.md).