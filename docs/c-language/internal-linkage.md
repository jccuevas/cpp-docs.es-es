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
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 6d693f4d12fcfe048ef16d9eb8e8806a58d62030
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="internal-linkage"></a>Vinculación interna
Si la declaración de un identificador de ámbito de archivo para un objeto o una función contiene el *storage-class-specifier* **static**, el identificador tiene vinculación interna. De lo contrario, el identificador tiene vinculación externa. Vea [Clases de almacenamiento](../c-language/c-storage-classes.md) si desea una descripción del elemento no terminal *storage-class-specifier*.  
  
 Dentro de una unidad de traducción, cada instancia de un identificador con vinculación interna denota el mismo identificador o función. Los identificadores vinculados internamente son exclusivos para una unidad de traducción.  
  
## <a name="see-also"></a>Vea también  
 [Usar extern para especificar la vinculación](../cpp/using-extern-to-specify-linkage.md)
