---
title: "Diagnóstico impreso por la función assert | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d6e5ea4e5f8bae3fda190ac7a7136035aea0c948
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnóstico impreso por la función assert
**ANSI 4.2** El diagnóstico impreso por la función **assert** y su comportamiento de finalización  
  
 La función **assert** imprime un mensaje de diagnóstico y llama a la rutina **abort** si la expresión es false (0). El mensaje de diagnóstico tiene la forma  
  
 **Error de aserción**: *expression***, archivo** *filename***, línea** *linenumber*  
  
 donde filename es el nombre del archivo de código fuente y linenumber es el número de línea de la aserción que produjo un error en el archivo de código fuente. No se realiza ninguna acción si la expresión es true (distinto de cero).  
  
## <a name="see-also"></a>Vea también  
 [Funciones de la biblioteca](../c-language/library-functions.md)