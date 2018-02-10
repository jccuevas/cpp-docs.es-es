---
title: "Ventajas de carácter portabilidad de los juegos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7ce02fa834c39f629990d4f3c9785de94bd02196
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="benefits-of-character-set-portability"></a>Ventajas de la portabilidad de los juegos de caracteres
Puede beneficiarse del uso de funciones de portabilidad de tiempo de ejecución de C y MFC incluso aunque no piense actualmente a internacionalizar la aplicación:  
  
-   Código portable hace que el código base flexible. Más adelante se puede mover fácilmente a Unicode o MBCS.  
  
-   El uso de Unicode hace que las aplicaciones para Windows sean más eficaces. Dado que Windows utiliza Unicode, deben convertirse cadenas no Unicode que se pasan a y desde el sistema operativo, lo que produce la sobrecarga.  

  
## <a name="see-also"></a>Vea también  
 [Unicode y MBCS](../text/unicode-and-mbcs.md)   
 [Compatibilidad con Unicode](../text/support-for-unicode.md)