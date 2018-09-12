---
title: Diagnóstico impreso por la función assert | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e824e94f79aa01ab3a82675fb3e8f76059c567d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195557"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnóstico impreso por la función assert
**ANSI 4.2** El diagnóstico impreso por la función **assert** y su comportamiento de finalización  
  
La función **assert** imprime un mensaje de diagnóstico y llama a la rutina **abort** si la expresión es false (0). El mensaje de diagnóstico tiene la forma  

> **Error de aserción**: <em>expression</em>**, archivo** <em>filename</em>**, línea** *linenumber*  

donde *filename* es el nombre del archivo de código fuente y *linenumber* es el número de línea de la aserción que produjo un error en el archivo de código fuente. No se realiza ninguna acción si la *expresión* es true (distinto de cero).  
  
## <a name="see-also"></a>Vea también  
 [Funciones de la biblioteca](../c-language/library-functions.md)