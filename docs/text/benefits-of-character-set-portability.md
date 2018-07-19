---
title: Ventajas de carácter portabilidad de los juegos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d1b78048baebfd89aed0ccc898c2bb9e3612525
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33853822"
---
# <a name="benefits-of-character-set-portability"></a>Ventajas de la portabilidad de los juegos de caracteres
Puede beneficiarse del uso de funciones de portabilidad de tiempo de ejecución de C y MFC incluso aunque no piense actualmente a internacionalizar la aplicación:  
  
-   Código portable hace que el código base flexible. Más adelante se puede mover fácilmente a Unicode o MBCS.  
  
-   El uso de Unicode hace que las aplicaciones para Windows sean más eficaces. Dado que Windows utiliza Unicode, deben convertirse cadenas no Unicode que se pasan a y desde el sistema operativo, lo que produce la sobrecarga.  

  
## <a name="see-also"></a>Vea también  
 [Unicode y MBCS](../text/unicode-and-mbcs.md)   
 [Compatibilidad con Unicode](../text/support-for-unicode.md)