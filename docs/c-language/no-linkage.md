---
title: Sin vinculación | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7dc6515020272d19a9b9efca7341293be4983a56
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="no-linkage"></a>Sin vinculación
Si una declaración de un identificador dentro de un bloque no incluye el especificador de clase de almacenamiento `extern`, el identificador no tiene ninguna vinculación y es exclusivo de la función.  
  
 Los identificadores siguientes no tienen vinculación:  
  
-   Un identificador declarado como algo distinto de un objeto o función  
  
-   Un identificador declarado como un parámetro de función  
  
-   Un identificador de ámbito de bloque para un objeto declarado sin el especificador de clase de almacenamiento `extern`  
  
 Si un identificador no tiene vinculación, al volver a declararse el mismo nombre (en un especificador de declarador o tipo) en el mismo nivel de ámbito, se genera un error de redefinición de símbolo.  
  
## <a name="see-also"></a>Vea también  
 [Usar extern para especificar la vinculación](../cpp/using-extern-to-specify-linkage.md)