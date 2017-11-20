---
title: "Sin vinculación | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 278325c1ad1b31ce20b6a17034be5e4731f6da78
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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