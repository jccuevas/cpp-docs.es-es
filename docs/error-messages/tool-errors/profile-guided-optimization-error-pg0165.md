---
title: "PG0165 de Error de optimización guiada por perfiles | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PG0165
dev_langs: C++
helpviewer_keywords: PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 32b9f5f3ee335aac0a8382377aa850c3b91a27a0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="profile-guided-optimization-error-pg0165"></a>Error de la optimización guiada por perfiles PG0165
Leer 'Filename.pgd': ' no se admite la versión PGD (error de coincidencia de versión)'.  
  
 Los archivos PGD son específicos de un conjunto de herramientas del compilador determinado. Este error se genera cuando se usa un compilador diferente a la utilizada para *Filename*pgd. Este error indica que este conjunto de herramientas del compilador no puede usar los datos de *Filename*.pgd para optimizar el programa actual.  
  
 Para resolver este problema, vuelva a generar *Filename*.pgd mediante el conjunto de herramientas de compilador actual.