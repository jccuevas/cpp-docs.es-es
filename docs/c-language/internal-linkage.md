---
title: "Vinculación interna | Microsoft Docs"
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
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e6ca8a9e9804aa6c14077b023d0014062067f324
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="internal-linkage"></a>Vinculación interna
Si la declaración de un identificador de ámbito de archivo para un objeto o una función contiene el *storage-class-specifier* **static**, el identificador tiene vinculación interna. De lo contrario, el identificador tiene vinculación externa. Vea [Clases de almacenamiento](../c-language/c-storage-classes.md) si desea una descripción del elemento no terminal *storage-class-specifier*.  
  
 Dentro de una unidad de traducción, cada instancia de un identificador con vinculación interna denota el mismo identificador o función. Los identificadores vinculados internamente son exclusivos para una unidad de traducción.  
  
## <a name="see-also"></a>Vea también  
 [Usar extern para especificar la vinculación](../cpp/using-extern-to-specify-linkage.md)