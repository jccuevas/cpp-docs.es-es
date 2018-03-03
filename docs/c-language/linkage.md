---
title: "Vinculación | Microsoft Docs"
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
- linkage [C++]
- linkage [C++], identifier names and scope
ms.assetid: 986ee549-2d6c-487a-9e3b-a1f643bc5bdc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e7d2522169588aa285c91c535eb31360679d8136
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linkage"></a>Vinculación
Los nombres de identificador pueden hacer referencia a identificadores diferentes en ámbitos diferentes. Un identificador declarado en ámbitos diferentes o en el mismo ámbito más de una vez puede establecerse para que haga referencia al mismo identificador o a la misma función mediante un proceso denominado "vinculación". La vinculación determina las partes del programa en las que se puede hacer referencia a un identificador (su "visibilidad"). Hay tres tipos de vinculación: [interna](../c-language/internal-linkage.md), [externa](../c-language/external-linkage.md) y [sin vinculación](../c-language/no-linkage.md).  
  
## <a name="see-also"></a>Vea también  
 [Usar extern para especificar la vinculación](../cpp/using-extern-to-specify-linkage.md)