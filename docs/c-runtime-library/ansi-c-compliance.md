---
title: Conformidad con ANSI C | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Ansi
dev_langs:
- C++
helpviewer_keywords:
- underscores, leading
- compatibility [C++], ANSI C
- compliance with ANSI C
- conventions [C++], Microsoft extensions
- underscores
- naming conventions [C++], Microsoft library
- ANSI [C++], C standard
- Microsoft extensions naming conventions
ms.assetid: 6be271bf-eecf-491a-a928-0ee2dd60e3b9
caps.latest.revision: 6
author: corob-msft
ms.author: corob
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
ms.openlocfilehash: 7e6c5d4045f0b71890a34d845b898844ca550ca8
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="ansi-c-compliance"></a>Conformidad con ANSI C
La convención de nomenclatura de todos los identificadores específicos de Microsoft en el sistema en tiempo de ejecución (por ejemplo, funciones, macros, constantes, variables y definiciones de tipo) cumple la norma ANSI. En esta documentación, cualquier función de tiempo de ejecución que sigue las normas ANSI/ISO C se indica como conforme con ANSI. Las aplicaciones conformes con ANSI solo deben usar estas funciones compatible con ANSI.  
  
 Los nombres de funciones específicas de Microsoft y las variables globales comienzan con un único guión bajo. Estos nombres se pueden invalidar solo localmente, dentro del ámbito de su código. Por ejemplo, cuando se incluyen los archivos de encabezado de tiempo de ejecución de Microsoft, puede invalidar localmente la función específica de Microsoft denominada `_open` al declarar una variable local del mismo nombre. Sin embargo, no se puede utilizar este nombre para su propia función o variable globales.  
  
 Los nombres de macros y constantes de manifiesto específicas de Microsoft empiezan con dos guiones bajos o con un único guión bajo inicial seguido inmediatamente por una letra mayúscula. El ámbito de estos identificadores es absoluto. Por ejemplo, no se puede usar el identificador específico de Microsoft **_UPPER** por esta razón.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad](../c-runtime-library/compatibility.md)
