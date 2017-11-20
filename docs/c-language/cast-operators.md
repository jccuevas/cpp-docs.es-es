---
title: "Operadores de conversión | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- cast operators
- type casts, operators
- operators [C++], cast
- type conversion, cast operators
ms.assetid: 43b90bbd-39ef-43e6-ae5d-e8a67a01de40
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8e607d3e1d02a985225f1ae41be66200ecf754ff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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