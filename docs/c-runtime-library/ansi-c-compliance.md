---
title: Conformidad con ANSI C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 452c6803ea05f051727a1417aee49c3a56759141
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387904"
---
# <a name="ansi-c-compliance"></a>Conformidad con ANSI C
La convención de nomenclatura de todos los identificadores específicos de Microsoft en el sistema en tiempo de ejecución (por ejemplo, funciones, macros, constantes, variables y definiciones de tipo) cumple la norma ANSI. En esta documentación, cualquier función de tiempo de ejecución que sigue las normas ANSI/ISO C se indica como conforme con ANSI. Las aplicaciones conformes con ANSI solo deben usar estas funciones compatible con ANSI.  
  
 Los nombres de funciones específicas de Microsoft y las variables globales comienzan con un único guión bajo. Estos nombres se pueden invalidar solo localmente, dentro del ámbito de su código. Por ejemplo, cuando se incluyen los archivos de encabezado de tiempo de ejecución de Microsoft, puede invalidar localmente la función específica de Microsoft denominada `_open` al declarar una variable local del mismo nombre. Sin embargo, no se puede utilizar este nombre para su propia función o variable globales.  
  
 Los nombres de macros y constantes de manifiesto específicas de Microsoft empiezan con dos guiones bajos o con un único guión bajo inicial seguido inmediatamente por una letra mayúscula. El ámbito de estos identificadores es absoluto. Por ejemplo, no se puede usar el identificador específico de Microsoft **_UPPER** por esta razón.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad](../c-runtime-library/compatibility.md)