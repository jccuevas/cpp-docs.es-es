---
title: Error del compilador de recursos RC2148 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC2148
dev_langs: C++
helpviewer_keywords: RC2148
ms.assetid: 0290065c-35d3-4815-80c5-40bf7132ae1d
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ee5add7bae569e08849ec7d3cb4f737c70ac97bb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-error-rc2148"></a>Error del compilador de recursos RC2148
Identificador de SUBIDIOMA demasiado grande  
  
 El valor de identificador de SUBIDIOMA estaba fuera del intervalo.  
  
 La instrucción **LANGUAGE** debe usar la sintaxis siguiente:  
  
 **LANGUAGE** *Id_idioma_primario*,*Id_idioma_secundario*  
  
 Identificadores de SUBIDIOMA válidos se definen como **sublang dentro** constantes en el archivo WINNT.h.