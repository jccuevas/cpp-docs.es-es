---
title: "Operadores de conversión | Microsoft Docs"
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
- cast operators
- type casts, operators
- operators [C++], cast
- type conversion, cast operators
ms.assetid: 43b90bbd-39ef-43e6-ae5d-e8a67a01de40
caps.latest.revision: 8
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
ms.openlocfilehash: c1d8315270f6b69629eca55e7aa1c6198f414117
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="cast-operators"></a>Operadores de conversión
Una conversión de tipo proporciona un método para la conversión explícita del tipo de un objeto en una situación concreta.  
  
## <a name="syntax"></a>Sintaxis  
 *cast-expression*:  
 *unary-expression*  
  
 **(**  *type-name*  **)**  *cast-expression*  
  
 El compilador trata *cast-expression* como tipo *type-name* una vez realizada una conversión de tipo. Las conversiones se pueden utilizar para convertir objetos de cualquier tipo escalar en cualquier otro tipo escalar. Las conversiones de tipos explícitas están restringidas por las mismas reglas que determinan los efectos de las conversiones implícitas, que se describen en [Conversiones de asignación](../c-language/assignment-conversions.md). Se pueden aplicar otras restricciones derivadas de los tamaños reales o de la representación de tipos específicos. Vea [Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md) para obtener información sobre los tamaños reales de los tipos enteros. Para obtener más información sobre la conversión de tipos, vea [Conversiones de tipos](../c-language/type-cast-conversions.md).  
  
## <a name="see-also"></a>Vea también  
 [Operador de conversión: ()](../cpp/cast-operator-parens.md)
