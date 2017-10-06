---
title: "Vinculación externa | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: f04fe738a5c045eeb955742e9947e420ab50de6f
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="external-linkage"></a>Vinculación externa
Si la primera declaración en el nivel de ámbito de archivo para un identificador no usa el especificador de clase de almacenamiento **static**, el objeto tiene una vinculación externa.  
  
 Si la declaración de un identificador para una función no tiene ningún especificador de clase de almacenamiento (*storage-class-specifier*), su vinculación se determina exactamente como si se declarara con *storage-class-specifier* `extern`. Si la declaración de un identificador de un objeto tiene ámbito de archivo y no tiene *storage-class-specifier*, su vinculación es externa.  
  
 El nombre de un identificador con vinculación externa designa la misma función u objeto de datos que realiza cualquier otra declaración para el mismo nombre con vinculación externa. Las dos declaraciones pueden estar en la misma unidad de traducción o en unidades de traducción diferentes. Si el objeto o la función también tienen una duración global, el programa completo comparte el objeto o la función.  
  
## <a name="see-also"></a>Vea también  
 [Usar extern para especificar la vinculación](../cpp/using-extern-to-specify-linkage.md)
