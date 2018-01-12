---
title: "Tipos de vinculación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- no linkage
- linkage [C++], none
- linkage [C++], types of
- types [C++], linkage
- internal linkage, types of linkage
- external linkage, linkage types
ms.assetid: 41326c7f-4602-4bad-a648-697604858ba0
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f71fc6e0d0251db38cd1c3dc1032ba6c71ba3ba4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="types-of-linkage"></a>Tipos de vinculación
La manera en que se comparten los nombres de objetos y funciones entre las unidades de traducción se denomina vinculación. Estos nombres pueden tener:  
  
-   Vinculación interna, en cuyo caso solo hacen referencia a elementos del programa incluidos dentro de sus propias unidades de traducción; no se comparten con otras unidades de traducción.  
  
     El mismo nombre en otra unidad de traducción puede hacer referencia a un objeto diferente o a una clase diferente. De los nombres con vinculación interna se suele decir que son locales con respecto a sus unidades de traducción.  
  
     Una declaración de ejemplo de un nombre con vinculación interna es:  
  
    ```  
    static int i;   // The static keyword ensures internal linkage.  
    ```  
  
-   Vinculación externa, en cuyo caso pueden hacer referencia a elementos de programa en cualquier unidad de traducción del programa: el elemento de programa se comparte entre las unidades de traducción.  
  
     Puede estar seguro de que el mismo nombre en otra unidad de traducción hará referencia al mismo objeto o clase. De los nombres con vinculación externa se suele decir que son globales.  
  
     Una declaración de ejemplo de un nombre con vinculación externa es:  
  
    ```  
    extern int i;  
    ```  
  
-   Ninguna vinculación, en cuyo caso harán referencia a entidades únicas. El mismo nombre en otro ámbito no puede hacer referencia al mismo objeto. Un ejemplo es una enumeración. (Tenga en cuenta, sin embargo, que puede pasar un puntero a un objeto sin vinculación. Esto hace que el objeto esté accesible en otras unidades de traducción).  
  
## <a name="see-also"></a>Vea también  
 [Programa y vinculación](../cpp/program-and-linkage-cpp.md)