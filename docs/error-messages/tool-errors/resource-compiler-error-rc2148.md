---
title: Error del compilador de recursos RC2148 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2148
dev_langs:
- C++
helpviewer_keywords:
- RC2148
ms.assetid: 0290065c-35d3-4815-80c5-40bf7132ae1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d10e18eef4691c0a018feb583ffb93499e86ccb6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320211"
---
# <a name="resource-compiler-error-rc2148"></a>Error del compilador de recursos RC2148
Identificador de SUBIDIOMA demasiado grande  
  
 El valor de identificador de SUBIDIOMA estaba fuera del intervalo.  
  
 La instrucción **LANGUAGE** debe usar la sintaxis siguiente:  
  
 **LANGUAGE** *Id_idioma_primario*,*Id_idioma_secundario*  
  
 Identificadores de SUBIDIOMA válidos se definen como **sublang dentro** constantes en el archivo WINNT.h.